# Connecting other Agent Events

In addition to [connecting-tool-calls.md](connecting-tool-calls.md "mention") and [connecting-user-feedback.md](connecting-user-feedback.md "mention") to your agents' session recordings in Wayfound, you can also connect other kinds of events. These can be any kind of data that is relevant to the agents' interactions.  The AI Manager can make sense of this additional data in the session when analyzing your agents' activity.

### Event Types

There are 14 supported event types (including the stop-gap "custom\_event"):

* assistant\_message
* user\_message
* system\_message
* developer\_message
* structured\_message
* reasoning\_step
* tool\_call
* agent\_call
* user\_feedback
* button\_click
* link\_click
* agent\_handoff
* human\_review
* custom\_event

### Example events with descriptions

Below is an example session transcript that uses all the event types along with brief explanations of why they are being used:

#### 1. `user_message`

Records the user’s request for Project Alpha status.

```json
{
  "timestamp": "2025-05-07T10:00:00Z",
  "event_type": "user_message",
  "label": "User Message",
  "description": "User asks for project Alpha status",
  "attributes": {
    "content": "What’s the current status of Project Alpha?"
  }
}
```

***

#### 2. `reasoning_step`

Logs the internal thought about which service to call first.

```json
{
  "timestamp": "2025-05-07T10:00:01Z",
  "event_type": "reasoning_step",
  "label": "Reasoning Step",
  "description": "Determine which service to call first",
  "attributes": {
    "thought": "Fetch high-level project data, then drill into trends."
  }
}
```

***

#### 3. `developer_message`

Shows how you parsed the user’s intent.

```json
{
  "timestamp": "2025-05-07T10:00:02Z",
  "event_type": "developer_message",
  "label": "Dev Log",
  "description": "Parsed user intent",
  "attributes": {
    "content": "Intent identified: get_project_status, projectId=Alpha"
  }
}
```

***

#### 4. `tool_call` (PMService.getProjectData)

Fetches the high-level summary for Project Alpha.

```json
{
  "timestamp": "2025-05-07T10:00:03Z",
  "event_type": "tool_call",
  "label": "Tool Call: PMService.getProjectData",
  "description": "Fetched summary for Project Alpha",
  "attributes": {
    "tool_name": "PMService",
    "tool_input": { "projectId": "Alpha" },
    "tool_output": { "status": "On Track", "completion": 80 },
    "success": true,
    "latency_ms": 95
  }
}
```

***

#### 5. `assistant_message`

Delivers the summary back to the user.

```json
{
  "timestamp": "2025-05-07T10:00:04Z",
  "event_type": "assistant_message",
  "label": "Assistant Summary",
  "description": "Reported high-level status",
  "attributes": {
    "content": "Project Alpha is On Track with 80% completion to date.",
    "model_name": "gpt-4",
    "tokens_total": 18,
    "latency_ms": 60
  }
}
```

***

#### 6. `structured_message`

Offers the user structured next-step options.

```json
{
  "timestamp": "2025-05-07T10:00:05Z",
  "event_type": "structured_message",
  "label": "Options Presented",
  "description": "Offered next steps",
  "attributes": {
    "options": [
      { "title": "Show trend chart", "value": "trend" },
      { "title": "Get risk assessment", "value": "risk" }
    ]
  }
}
```

***

#### 7. `button_click`

Records the user choosing “trend.”

```json
{
  "timestamp": "2025-05-07T10:00:06Z",
  "event_type": "button_click",
  "label": "Button Click",
  "description": "User chose to view trend",
  "attributes": {
    "button_id": "trend"
  }
}
```

***

#### 8. `tool_call` (AnalyticsService.getCompletionTrend)

Fetches week-by-week completion data.

```json
{
  "timestamp": "2025-05-07T10:00:07Z",
  "event_type": "tool_call",
  "label": "Tool Call: AnalyticsService.getCompletionTrend",
  "description": "Fetched completion trend data",
  "attributes": {
    "tool_name": "AnalyticsService",
    "tool_input": { "projectId": "Alpha" },
    "tool_output": [
      { "week": 1, "completion": 50 },
      { "week": 2, "completion": 60 },
      { "week": 3, "completion": 75 },
      { "week": 4, "completion": 80 }
    ],
    "success": true,
    "latency_ms": 110
  }
}
```

***

#### 9. `reasoning_step`

Decides whether to invoke the risk-evaluation agent.

```json
{
  "timestamp": "2025-05-07T10:00:08Z",
  "event_type": "reasoning_step",
  "label": "Reasoning Step",
  "description": "Decide whether to call risk agent",
  "attributes": {
    "thought": "Trend looks healthy—next get risk score."
  }
}
```

***

#### 10. `agent_call` (RiskAgent)

Requests a detailed risk assessment from your RiskAgent.

```json
{
  "timestamp": "2025-05-07T10:00:09Z",
  "event_type": "agent_call",
  "label": "Agent Call: RiskAgent",
  "description": "Requested project risk evaluation",
  "attributes": {
    "external_id": "agent-42",
    "input": { "projectId": "Alpha" }
  }
}
```

***

#### 11. `assistant_message`

Presents the risk score to the user.

```json
{
  "timestamp": "2025-05-07T10:00:10Z",
  "event_type": "assistant_message",
  "label": "Assistant Risk Report",
  "description": "Delivered risk assessment",
  "attributes": {
    "content": "Risk score for Project Alpha is 2.1/5 (Low), with schedule variance at 5%.",
    "model_name": "gpt-4",
    "tokens_total": 22,
    "latency_ms": 70
  }
}
```

***

#### 12. `link_click`

Logs the user clicking through to the web dashboard.

```json
{
  "timestamp": "2025-05-07T10:00:11Z",
  "event_type": "link_click",
  "label": "Link Click",
  "description": "User clicked through to dashboard",
  "attributes": {
    "url": "https://dashboard.example.com/projects/Alpha"
  }
}
```

***

#### 13. `system_message`

Notes a background system action (scheduling a report).

```json
{
  "timestamp": "2025-05-07T10:00:12Z",
  "event_type": "system_message",
  "label": "System Message",
  "description": "Scheduled weekly status email",
  "attributes": {
    "content": "Weekly report for Project Alpha will be sent every Monday at 09:00."
  }
}
```

***

#### 14. `custom_event`

Tracks a domain-specific audit entry.

```json
{
  "timestamp": "2025-05-07T10:00:13Z",
  "event_type": "custom_event",
  "label": "Custom Event",
  "description": "Audit log entry",
  "attributes": {
    "event_name": "audit_log",
    "details": { "action": "view_status", "user": "user-007" }
  }
}
```

***

#### 15. `agent_handoff`

Marks the transfer to a human agent.

```json
{
  "timestamp": "2025-05-07T10:00:14Z",
  "event_type": "agent_handoff",
  "label": "Agent Handoff",
  "description": "Transferred to human for budget questions",
  "attributes": {
    "reason": "budget_inquiry"
  }
}
```

***

#### 16. `human_review`

Captures a supervisor’s follow-up on that handoff.

```json
{
  "timestamp": "2025-05-07T10:05:00Z",
  "event_type": "human_review",
  "label": "Human Review",
  "description": "Supervisor added budget commentary",
  "attributes": {
    "approver_id": "supervisor-99",
    "status": "note_added"
  }
}
```

***

#### 17. `user_feedback` (Thumbs)

Logs a thumbs-up/down on the risk report.

```json
{
  "timestamp": "2025-05-07T10:05:05Z",
  "event_type": "user_feedback",
  "label": "User Feedback (Thumbs)",
  "description": "User gave a thumbs-up on risk report",
  "attributes": {
    "feedback_type": "thumbs_up_down",
    "rating": "thumbs_up",
    "related_span_id": "span-10"
  }
}
```

***

#### 18. `user_feedback` (Stars)

Captures an overall star rating for the session.

```json
{
  "timestamp": "2025-05-07T10:05:10Z",
  "event_type": "user_feedback",
  "label": "User Feedback (Stars)",
  "description": "User rated overall experience",
  "attributes": {
    "feedback_type": "stars",
    "rating": 5
  }
}
```

***

You can copy and adapt each block to instrument your own agent’s session logging for Wayfound—just plug in your timestamps, labels, descriptions, and attribute data as you go.
