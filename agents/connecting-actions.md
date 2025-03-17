# Connecting Actions

After [connecting-agents.md](connecting-agents.md "mention") to Wayfound, you can also connect actions. This allows Wayfound to track action success rates in  [performance.md](../manager/performance.md "mention") reports. You can do so by adding an an "action.invocation" type to "messages":

```python
{
 "agentId": "1d3348a5-dc4c-44d2-83b0-3e53acf74a76",
 "firstMessageAt": "2025-03-11T11:51:00.000Z",
 "lastMessageAt": "2025-03-11T11:54:00.000Z",
 "messages": [
   {
     "role": "assistant",
     "content": "Test assistant response"
   },
   {
     "role": "user",
     "content": "This is a user response"
   },
   {
     "role": "debug",
     "type": "action.invocation",
     "data": { "actionName": "My DB Action"}
   }
 }
```

This will add the following information to the agent's Wayfound transcript whenever an action is called:

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

For more comprehensive monitoring, include additional metadata in your action.invocation message:

```python
     {
          "role": "debug",
          "type": "action.invocation",
          "data": { "actionName": "My DB Action",
                    "functionName": "call_db_for_data",
                    "functionArgs": "total record count",
                    "functionResponse": {"data": {"count": 2}}
                   }
     }
```

With this information, the action invocation window will now provide the added context:

<figure><img src="../.gitbook/assets/Screenshot 2025-03-17 at 4.27.15 PM.png" alt=""><figcaption></figcaption></figure>

You can also add error messages:

```python
   {
     "role": "debug",
     "type": "action.invocation",
     "data": { "actionName": "My DB Action",
               "functionName": "call_db_for_data",
               "functionArgs": "total record count",
               "functionStatus": {"errorType": "db", "errorReason": "authentication failed"}
              }
   }

```

When added, error messages appear in the transcript:

<figure><img src="../.gitbook/assets/Screenshot 2025-03-17 at 4.27.43 PM.png" alt=""><figcaption></figcaption></figure>

Note that action invocations should be logged regardless of success or failure for accurate performance tracking. In addition ,you can have multiple action invocations in a single transcript.
