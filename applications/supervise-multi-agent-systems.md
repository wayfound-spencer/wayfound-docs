# Supervise Multi-Agent Systems

For supervising multi-agent systems, Wayfound has the concept of **Applications.**  One or more agents can be added to an application, and as sessions flow in to Wayfound, OpenTelemetry `trace` and `span` information is leveraged to create a holistic view of exactly what has occurred and when.  Additionally, the Wayfound Supervisor can reason across the actions of every agent that participated in the application `trace`.

To create an **Application**, go to the **Applications** section of Wayfound and click 'New Application'.

<figure><img src="../.gitbook/assets/Untitled (17).png" alt="" width="563"><figcaption></figcaption></figure>

Provide a name and role and select one or more agents for the **Application**.

<figure><img src="../.gitbook/assets/Untitled (18).png" alt="" width="375"><figcaption></figcaption></figure>

When viewing the list of Applications, simply click on the **Application** name to view `traces`.

<figure><img src="../.gitbook/assets/Untitled (19).png" alt=""><figcaption></figcaption></figure>

The **Application** detail screen provides a quick overview of all the `traces` collected.  For each `trace` you can see the number of sessions, the grades of each participating agent, the durations, and when each `trace` started and ended.

<figure><img src="../.gitbook/assets/Untitled (20).png" alt=""><figcaption></figcaption></figure>

Clicking on a `trace` id will display the `trace` details drawer where you can view key analysis and the multi-agent timeline.

<figure><img src="../.gitbook/assets/Untitled (21).png" alt="" width="563"><figcaption></figcaption></figure>

Click on an entry in the timeline to view the full agent analysis drawer.

<figure><img src="../.gitbook/assets/Untitled (22).png" alt="" width="563"><figcaption></figcaption></figure>



**Contextualize Session Data**

After an Application is created in Wayfound, the next step is to enhance your session data to include the `applicationId`, `trace_id`, and `span_id` .

It is important to use the same `trace_id` across sessions where multiple agents are involved so that Wayfound can properly correlate the multi-agent session data.

The required `span_id` and optional `parent_span_id` can be used to further group data within a trace.

Here is an example of a Wayfound session with these fields included:

```
{
 "agentId": "22198fc5-1056-4a9d-b455-440db1249539",
 "applicationId": "7cf54242-0898-4ac1-a09c-c0e4be3f000a",
 "firstMessageAt": "2025-15-08T10:51:00.000Z",
 "lastMessageAt": "2025-15-08T10:54:00.000Z",
    "messages": [
      {
        "timestamp": "2025-10-15T22:47:26.014Z",
        "event_type": "assistant_message",
        "attributes": {
          "content": "Hello, how can I help you today?"
        },
        "context": {
            "trace_id": "123",
            "span_id": "abc"
        }
      }
    ]
}

    
```

**Note:** The `context`, `trace_id`, and `span_id` are required fields when you add `applicationId` to a session.
