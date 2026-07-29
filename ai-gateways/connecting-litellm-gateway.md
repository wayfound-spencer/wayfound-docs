# Connecting LiteLLM Gateway

## Supervising Agents Through Your LiteLLM Gateway

If your LLM traffic flows through a LiteLLM proxy, the gateway can be your entire Wayfound integration — no SDK, no application code changes. Point the gateway's OpenTelemetry callback at Wayfound and every virtual key that sends traffic appears in **Settings → AI Gateway**, with its alias, team, and traffic stats. Flip **Supervise** on a key and Wayfound creates its Supervisor, connects it, and backfills roughly the last week of that key's traffic — analyzed sessions appear within minutes.

### Prerequisites

1. A LiteLLM proxy you operate (the standard deployment with `config.yaml`).
2. A Wayfound **API key** (Settings → API Keys).

You do **not** need to create agents in Wayfound first — the Supervise toggle creates and publishes the agent for you.

### 1. Point the gateway at Wayfound

In the proxy's `config.yaml`:

```yaml
litellm_settings:
  callbacks: ["otel"]
```

And in the gateway's environment:

```bash
OTEL_EXPORTER="otlp_http"
OTEL_ENDPOINT="https://app.wayfound.ai/api/otel/v1/traces"
OTEL_HEADERS="Authorization=Bearer <YOUR_API_KEY>"
```

Note the literal space in `Bearer <YOUR_API_KEY>` — LiteLLM parses its header env vars itself without URL-decoding, so the `%20` encoding used with standard OTel SDK exporters would be sent verbatim and fail authentication.

Restart the proxy after the change. This is a one-time setup by whoever operates the gateway.

### 2. Supervise your keys

Most teams already issue one virtual key per application for cost tracking — if that's you, the key _is_ the agent's identity. Once traffic flows, open **Settings → AI Gateway** in Wayfound:

* Every key seen in gateway traffic is listed with its alias, team, first/last seen, and traffic volume.
* Toggle **Supervise** on a key to create its Supervisor and backfill recent traffic. New traffic routes to it automatically — no per-request metadata needed.
* Key rotation and alias renames are detected and handled automatically.

### 3. Group multi-turn conversations

One request is one trace. To make a multi-turn conversation appear as a single Wayfound session, pass LiteLLM's session metadata on each completion request:

```json
{
  "model": "...",
  "metadata": { "session_id": "chat-123" },
  "messages": [...]
}
```

Requests sharing a `session_id` merge into one ordered session; requests without one become single-turn sessions. (The LiteLLM dashboard playground sends no metadata, so playground messages always land as separate single-turn sessions.)

### 4. Multiple agents behind one key

If several agents share a single virtual key, add per-request metadata to route each request to its own Supervisor — it overrides the key's default agent:

```json
{ "metadata": { "wayfound_agent_id": "<AGENT_UUID_OR_SHORT_ID>" } }
```

### What you get — and what needs instrumentation

Gateway-only supervision captures every LLM call's user and assistant messages, model, token counts, latency, and errors, grouped into per-agent sessions with full Supervisor analysis.

What it can't see: tool _executions_ as structured events, or agent/handoff structure inside your application (tool calls appear only as text within messages). For that, add framework instrumentation — see Sending OpenTelemetry Traces to Wayfound. Instrumented apps and the gateway work together: Wayfound de-duplicates automatically, with the framework's spans as the source of truth and the gateway's filling in token and cost details.

### Troubleshooting

* **No keys appearing in Settings → AI Gateway** — confirm the `otel` callback is in `config.yaml`, the `OTEL_*` variables are set in the gateway's environment (not just your shell), and the proxy was restarted. Check the header uses a literal space, not `%20`.
* **HTTP 403 from the endpoint** — the Wayfound API key is missing or invalid, or OTLP ingestion isn't enabled for your organization.
* **Every request is its own session** — requests aren't sending `metadata.session_id` (see above).
* **Sessions on the wrong agent** — a shared key without `metadata.wayfound_agent_id` routes everything to the key's default agent.

### Notes and limits

* Endpoint: OTLP/HTTP only (protobuf or JSON, gzip OK). gRPC is not supported.
* Metrics and logs are accepted and discarded — only traces are processed.
* Max request size: 4.5 MB per export batch.
* Sessions appear shortly after a trace goes quiet (roughly a minute), not instantly — spans are assembled asynchronously.
* Backfill on Supervise covers roughly the last 7 days of staged traffic.
