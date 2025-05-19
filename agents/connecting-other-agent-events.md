# Connecting other Agent Events

In addition to [connecting-tool-calls.md](connecting-tool-calls.md "mention") and [connecting-user-ratings.md](connecting-user-ratings.md "mention") to your agents' session recordings in Wayfound, you can also connect other kinds of events under a general "event" message type. This could be any kind of data that is relevant to the agents' interactions with users. Some examples of this could be “user launches the bot” or “user clicks on a link”.

The AI Manager can make sense of this additional data in the recording session when analyzing your agents' activity. To help the AI Manager make the most of this data, the "event" message type comes with a description field that can contain more context about this particular datapoint. To this end, the description should be consistent with your agents' [guidelines.md](guidelines.md "mention").&#x20;

### Example Scenario

In this example, the AI agent provides a link to the user and the downstream system hosting the agent knows that the user clicked a particular link and that data is passed back to Wayfound. A high priority guideline is established saying “User clicks on a link that is different from what the agent provided them.” Session processing knows the user clicked on a different link by reading the event data and marks the session as “Needs Attention.”

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeWUhVyaIgBWcTAzYjqcTRvnBDF6Z9Zravm7_UF6W6AfQ-szdkw9dFvFTlsmUti64vNrrjoj4-tlnTj3RPa8UGHxcjkiJBr6Far6ZQ1geqE0s6y6vJvcS62J3lwpoi7NuKGnCPRDQ?key=BbI5-ChJZ9CMCTkcWQ8XCKeA" alt="" width="563"><figcaption></figcaption></figure>

The event is created as follows:

```
{
"agentId": "1d3348a5-dc4c-44d2-83b0-3e53acf74a76",
"firstMessageAt": "2025-04-11T10:51:00.000Z",
"lastMessageAt": "2025-04-11T10:54:00.000Z",
"messages": [
  
  {
    "role": "assistant",
    "content": "Hi, How may I help you?"
  },
  {
    "role": "user",
    "content": "I want help with creating agents."
  },
  {
    "role": "assistant",
    "content": "Go checkout Google's new agent builder: [Google AI Studio](https://aistudio.google.com/)"
  },
  {
    "role": "debug",
    "type": "event",
    "description": "User clicks on the link.",
    "data": { "category": "User Click Event",
              "detail": {"click": "https://www.crewai.com/"}}
  }
]
}

```
