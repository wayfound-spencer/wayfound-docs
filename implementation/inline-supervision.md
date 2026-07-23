# Inline Supervision

## Inline Supervision

Wayfound normally analyzes sessions asynchronously: your agent posts a completed session, the API returns immediately, and the Supervisor's analysis shows up in the dashboard a short time later. That's the right default for observability, but sometimes you want the analysis _before_ your agent takes its next step.

**Inline supervision** turns Wayfound into an active checkpoint in your agent's control flow. By setting `async: false` when creating a session, the API blocks until the Supervisor has finished analyzing it and returns the full analysis with grade, guideline results, sentiment, and more in the response. Your code can then branch on those results: hand work to the next agent, retry a bad response, escalate to a human, or proceed.

### How it works

Create a session the same way you always do — `POST https://app.wayfound.ai/api/v2/sessions` with your agent ID and messages — but add `"async": false` to the request body:

```json
{
  "agentId": "your-agent-uuid",
  "async": false,
  "messages": [
    {
      "timestamp": "2026-07-23T10:00:00Z",
      "event_type": "user_message",
      "attributes": { "content": "Can you cancel my subscription and refund this month?" }
    },
    {
      "timestamp": "2026-07-23T10:00:04Z",
      "event_type": "assistant_message",
      "attributes": {
        "content": "I've submitted your cancellation. A full refund for this month will be processed within 3–5 business days."
      }
    }
  ]
}
```

Instead of returning right away with just a session ID, the request blocks until analysis completes and returns the analyzed session. The fields your inline logic will care about most:

```json
{
  "id": "session-uuid",
  "agentId": "agent-uuid",
  "grade": {
    "grade": "B",
    "explanation": "The agent resolved the request but promised a refund timeline it cannot guarantee."
  },
  "compliance": [
    {
      "guideline": "Never commit to a specific refund timeline; refunds are processed by the billing team.",
      "guidelineType": "content",
      "guidelineSource": "agent",
      "guidelinePriority": "red",
      "messageId": "assistant_1",
      "result": {
        "compliant": false,
        "reason": "The assistant promised a refund within 3–5 business days, which commits to a specific timeline."
      }
    },
    {
      "guideline": "Always confirm the user's intent before making account changes.",
      "guidelinePriority": "yellow",
      "result": {
        "compliant": true,
        "reason": "The assistant acted on an explicit, unambiguous request."
      }
    }
  ],
  "sentiment": { "value": "neutral", "reason": "..." },
  "knowledgeGaps": [],
  "tags": ["cancellation", "refund"]
}
```

#### Reading guideline results

Every guideline configured for the agent (including global guidelines) appears in the `compliance` array. Each entry's `result.compliant` is one of three values:

| Value   | Meaning                                               |
| ------- | ----------------------------------------------------- |
| `true`  | The session complied with the guideline               |
| `false` | The session violated the guideline                    |
| `null`  | Not enough conversation to determine (not applicable) |

For gating decisions, match entries by their `guideline` text of the guideline as you authored it in Wayfound and treat `null` however your use case demands (usually as a pass, since the guideline didn't come into play).

> **Tip:** In most inline-supervision setups you gate on one or two specific **red-priority** guidelines and let everything else flow to the dashboard asynchronously. The fewer guidelines you gate on, the simpler and more predictable your control flow.

### Pattern 1: Orchestrator gate

In a multi-agent system, an orchestrator assembles context and dispatches work to specialized workers. Inline supervision lets the orchestrator verify its own output. For example: the plan, the assembled context, the task framing against your guidelines _before_ a worker acts on it.

```
User request
   │
   ▼
Orchestrator assembles context / plan
   │
   ▼
POST /api/v2/sessions  (async: false)  ──►  Wayfound analyzes
   │
   ├─ gated guideline compliant  ──►  dispatch to worker agent
   └─ gated guideline violated   ──►  revise plan / escalate / halt
```

```python
import requests

WAYFOUND_URL = "https://app.wayfound.ai/api/v2/sessions"
HEADERS = {
    "Authorization": f"Bearer {WAYFOUND_API_KEY}",
    "Content-Type": "application/json",
}

GATED_GUIDELINE = "Worker tasks must never include raw customer payment details."

def check_before_dispatch(orchestrator_messages):
    response = requests.post(
        WAYFOUND_URL,
        headers=HEADERS,
        json={
            "agentId": ORCHESTRATOR_AGENT_ID,
            "async": False,
            "messages": orchestrator_messages,
        },
        timeout=90,
    )

    if response.status_code == 202:
        # Analysis didn't finish within the synchronous window —
        # poll GET /api/v2/sessions/{id}, or apply your fallback policy.
        return handle_pending(response.json()["id"])

    response.raise_for_status()
    session = response.json()

    gate = next(
        (g for g in session["compliance"] if g["guideline"] == GATED_GUIDELINE),
        None,
    )

    # compliant is True, False, or None (guideline not applicable)
    if gate and gate["result"]["compliant"] is False:
        return {
            "proceed": False,
            "reason": gate["result"]["reason"],
            "sessionId": session["id"],
        }

    return {"proceed": True, "sessionId": session["id"]}


result = check_before_dispatch(messages)
if result["proceed"]:
    dispatch_to_worker(task)
else:
    revise_and_retry(task, feedback=result["reason"])
```

Because every check is a real Wayfound session, you also get a complete audit trail: every dispatch decision, including the ones that were blocked is recorded, graded, and visible in the dashboard.

### Pattern 2: Grade-and-retry before the user sees a response

For user-facing agents, inline supervision can act as a quality gate between your LLM and the user: generate a candidate response, have Wayfound grade it, and only show it to the user if the guideline you care about passed. If it failed, feed the violation reason back into the prompt and regenerate.

```
User message ──► LLM generates candidate response
                    │
                    ▼
        POST /api/v2/sessions (async: false)
                    │
        ┌───────────┴────────────┐
        ▼                        ▼
   guideline passed         guideline failed
        │                        │
        ▼                        ▼
  send to user          regenerate with the
                        violation reason as
                        feedback (max N tries)
```

```typescript
const GATED_GUIDELINE = 'Responses must never provide specific legal or tax advice.';
const MAX_ATTEMPTS = 3;

async function respondWithSupervision(userMessage: string): Promise<string> {
  let feedback: string | null = null;

  for (let attempt = 1; attempt <= MAX_ATTEMPTS; attempt++) {
    const candidate = await generateResponse(userMessage, feedback);

    const res = await fetch('https://app.wayfound.ai/api/v2/sessions', {
      method: 'POST',
      headers: {
        Authorization: `Bearer ${process.env.WAYFOUND_API_KEY}`,
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        agentId: AGENT_ID,
        async: false,
        metadata: { attempt },
        messages: [
          {
            timestamp: new Date().toISOString(),
            event_type: 'user_message',
            attributes: { content: userMessage },
          },
          {
            timestamp: new Date().toISOString(),
            event_type: 'assistant_message',
            attributes: { content: candidate },
          },
        ],
      }),
    });

    if (res.status === 202) {
      // Analysis still running past the synchronous window.
      // Fallback policy: hold the response, or release it and
      // review asynchronously — your call per use case.
      return applyPendingPolicy(candidate, (await res.json()).id);
    }

    const session = await res.json();
    const gate = session.compliance?.find((g: any) => g.guideline === GATED_GUIDELINE);

    // Passed (or guideline wasn't applicable) — release the response.
    if (!gate || gate.result.compliant !== false) {
      return candidate;
    }

    // Failed — feed the Supervisor's reason back into the next attempt.
    feedback = gate.result.reason;
  }

  return fallbackResponse(); // e.g. safe canned reply or human handoff
}
```

Each attempt is recorded as its own session, so you can see in the dashboard exactly how often the gate fires and what the rejected candidates looked like. Passing an attempt counter in `metadata` makes retries easy to correlate.

### Handling latency and the pending case

Synchronous analysis takes as long as the Supervisor needs to evaluate the transcript — typically several seconds, longer for long sessions. Two things to build for:

* **Set a generous client timeout.** The request blocks while analysis runs; a 90-second client timeout is a reasonable starting point.
* **Handle `202 Accepted`.** If analysis doesn't finish within the synchronous window, the API returns `202` with `{ "id": "...", "status": "processing" }` instead of holding the connection open. Poll `GET /api/v2/sessions/{id}` until `lastProcessedAt` is set, or fall back to your default behavior.

Decide your fallback policy up front. This is an important design choice in an inline-supervision architecture:

* **Fail closed** (block until you have a verdict) for high-stakes gates: compliance-sensitive content, irreversible actions, financial commitments.
* **Fail open** (proceed, review asynchronously) for latency-sensitive user experiences where the gate is a quality improvement rather than a hard requirement.

### Best practices

* **Gate on few, specific guidelines.** Inline logic should hinge on one or two red-priority guidelines with crisp, testable language. Broad or subjective guidelines belong in your asynchronous review flow, not in a gate.
* **Match on exact guideline text.** The `guideline` field contains the guideline exactly as authored. If you edit the guideline in Wayfound, update the string in your code — or centralize it in configuration.
* **Treat `null` deliberately.** `compliant: null` means the guideline didn't apply to this session. For most gates that's a pass; for gates like "the response must always include a disclaimer," you may want to treat it as a failure.
* **Use `async: false` only where the verdict changes behavior.** Everything else should stay asynchronous — you keep full observability either way, without adding latency.
* **Test your gates in Test Mode.** Use [Test Mode](https://docs.wayfound.ai/agents/test-mode) with expected outcomes to verify your gated guidelines fire when they should before wiring them into production control flow.

For the complete request and response schema, see the [Create Session API reference](https://wayfound-api.readme.io/reference/create-completed-session).
