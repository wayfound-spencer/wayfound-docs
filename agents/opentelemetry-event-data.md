# OpenTelemetry Event Data

Wayfound supports sending optional [OpenTelemetry](https://opentelemetry.io/) fields along with each event in a session.  Here is an example that is using the supported fields (context, resource, and instrumentation) along with sub-fields.  Note that `resource` and `instrumentation` are optional fields:

```json
{
  "timestamp": "2025-05-08T17:00:00.000Z",
  "context": {
    "trace_id": "4bf92f3577b34da6a3ce929d0e0e4736",
    "span_id": "00f067aa0ba902b7",
    "parent_span_id": "3d7a2b8f9e1c4f2a"
  },
  "resource": {
    "service.name": "chat-interface-agent",
    "service.version": "3.2.1",
    "deployment.environment": "production",
    "hostname": "chat-frontend-02.example.com"
  },
  "instrumentation": {
    "name": "wayfound-otel-sdk",
    "version": "2.0.0"
  },
  "event_type": "user_message",
  "label": "User Message",
  "description": "User asks for account balance",
  "attributes": {
    "content": "What’s my current checking account balance?",
    "language": "en-US"
  }
}
```

This data will be returned whenever a session is retrieved through the Wayfound API. Additionally, Wayfound will leverage this data when used with multi-agent Wayfound Applications.

**Important**: the OpenTelemetry data is not included when Wayfound analyzes the session.
