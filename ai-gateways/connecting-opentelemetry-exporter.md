# Connecting OpenTelemetry Exporter

## Connecting Any AI Gateway via OpenTelemetry

> **Status:** Preview — this integration is under active development and not yet generally available.

If your LLM traffic flows through an AI gateway, the gateway can be your entire Wayfound integration — no SDK, no application code changes. Any gateway that lets you configure its OpenTelemetry export (an OTLP/HTTP endpoint plus request headers) can send its traces to Wayfound, and sessions appear in your dashboard with full Supervisor analysis.

**Using LiteLLM?** It has first-class support — automatic virtual-key discovery, one-click supervision, and traffic backfill. Follow Supervising Agents Through Your LiteLLM Gateway instead. This page is the generic contract for every other OTel-capable gateway, and for applications exporting their own traces.

### Prerequisites

1. A gateway whose OpenTelemetry trace export you can configure: the OTLP endpoint, the protocol (OTLP/HTTP), and custom request headers. Consult your gateway's documentation for where these are set.
2. A Wayfound **agent**, created and **published** (each agent gets its 1:1 Supervisor). Automatic agent creation is LiteLLM-only — on the generic path, create the agent first.
3. A Wayfound **API key** (Settings → API Keys).

### 1. Point the gateway's exporter at Wayfound

Configure the gateway's OTel export with:

```bash
OTEL_EXPORTER_OTLP_TRACES_ENDPOINT="https://app.wayfound.ai/api/otel/v1/traces"
OTEL_EXPORTER_OTLP_PROTOCOL="http/protobuf"
OTEL_EXPORTER_OTLP_HEADERS="Authorization=Bearer%20<YOUR_API_KEY>,x-wayfound-agent=<AGENT_UUID>"
```

The `%20` is required by the OTel spec's env-var header encoding — header values containing spaces must be URL-encoded, and some SDKs silently drop entries with raw spaces. (Gateways that parse header variables themselves may expect a literal space instead — LiteLLM does. When in doubt, try `%20` first if your gateway uses a standard OTel SDK exporter.)

`x-wayfound-agent` is the default Wayfound agent for every trace this exporter sends. A gateway fronting a single application needs nothing more; for multiple applications behind one gateway, see routing below.

### 2. What Wayfound reads from the spans

Wayfound reconstructs sessions from the **OTel GenAI semantic conventions** (`gen_ai.*`) and the **OpenInference** conventions — user and assistant messages, model, token counts, latency, and errors. Spans in other formats are preserved as generic events in the session timeline but carry no message content.

This is the assumption behind "any gateway": the gateway's spans must carry conversation content in one of those vocabularies. If your gateway emits something else, sessions will appear but read as structural traces rather than conversations — reach out and we'll look at supporting its dialect.

### 3. Route traffic to your agents

When one gateway carries traffic for several Wayfound agents, tag spans so each lands with the right Supervisor:

*   Set the resource attribute `wayfound.agent.id=<AGENT_UUID>` per agent process, or on individual spans for in-process multi-agent apps:

    ```bash
    OTEL_RESOURCE_ATTRIBUTES="wayfound.agent.id=<AGENT_UUID>"
    ```
* Or set each agent's **External ID** in Wayfound to match the agent name emitted in the spans (`gen_ai.agent.name` / the OpenInference agent span name) — Wayfound routes by name, no configuration changes.

Untagged child spans inherit their nearest tagged ancestor's agent; anything else falls back to the `x-wayfound-agent` header. Handoffs between agents are detected from the span tree: the handing-off agent's session records an `agent_handoff` event, and the receiving agent's session picks up from there.

Optionally set `x-wayfound-application=<APPLICATION_UUID>` in the exporter headers to group agents under an existing Wayfound Application; otherwise one is created automatically from your `service.name`.

### 4. Group multi-turn conversations

One OTel trace normally covers a single request. To make a multi-turn conversation appear as one Wayfound session, put a stable conversation ID on the spans — any one of:

* `session.id` (OpenInference — e.g. `using_session("chat-123")`)
* `gen_ai.conversation.id` (OTel GenAI conventions)
* `wayfound.session.id` (works anywhere)

Traces sharing an ID merge into a single session; traces without one become single-turn sessions. (On LiteLLM, callers pass `metadata.session_id` per request instead — see the LiteLLM guide.)

### 5. Optional: richer structure with app instrumentation

Gateway export captures every LLM call. What it can't see is your application's internal structure — tool _executions_ as structured events, agent steps, handoffs inside the app. For that, add a framework instrumentor and export from the app with the same endpoint and headers from section 1:

| Framework                                 | Instrumentation package                       | What Wayfound sees                           |
| ----------------------------------------- | --------------------------------------------- | -------------------------------------------- |
| OpenAI Agents SDK                         | `openinference-instrumentation-openai-agents` | Agent turns, LLM calls, tool calls, handoffs |
| LangChain / LangGraph                     | `openinference-instrumentation-langchain`     | Chains, LLM calls, tool calls                |
| CrewAI                                    | `openinference-instrumentation-crewai`        | Crew/agent structure, LLM + tool calls       |
| LlamaIndex                                | `openinference-instrumentation-llama-index`   | Query/retrieval structure, LLM calls         |
| smolagents                                | `openinference-instrumentation-smolagents`    | Agent steps, LLM + tool calls                |
| OpenAI SDK (direct)                       | `openinference-instrumentation-openai`        | LLM calls                                    |
| Anthropic SDK (direct)                    | `openinference-instrumentation-anthropic`     | LLM calls                                    |
| Anything using the OTel GenAI conventions | your framework's native OTel support          | LLM calls, tool/agent spans where emitted    |

Python example (OpenAI Agents SDK):

```python
from openinference.instrumentation.openai_agents import OpenAIAgentsInstrumentor
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import BatchSpanProcessor
from opentelemetry.exporter.otlp.proto.http.trace_exporter import OTLPSpanExporter

provider = TracerProvider()
provider.add_span_processor(BatchSpanProcessor(OTLPSpanExporter()))
OpenAIAgentsInstrumentor().instrument(tracer_provider=provider)
# endpoint + auth come from the OTEL_* env vars above
```

App instrumentation and gateway export work together: your app propagates trace context (W3C `traceparent`) on requests to the gateway, so gateway spans join the same trace. Wayfound automatically de-duplicates — the framework span is the source of truth for each LLM call, and gateway spans fill in token and cost details.

### Notes and limits

* Endpoint: OTLP/HTTP only (protobuf or JSON, gzip OK). gRPC is not supported.
* Metrics and logs are accepted and discarded — only traces are processed today.
* Max request size: 4.5 MB per export batch (platform request limit; bodies are additionally capped at 5 MB after gzip decompression).
* Spans that can't be matched to any Wayfound agent are dropped (the trace hierarchy is still recorded). Check exporter tagging if sessions are missing.
* Sessions appear shortly after a trace goes quiet (roughly a minute), not instantly — spans are assembled asynchronously.
