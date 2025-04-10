# Connecting User Ratings

After [connecting-agents.md](connecting-agents.md "mention") to Wayfound, you can also track user feedback ratings. This allows Wayfound to generate satisfaction metrics in [performance.md](../manager/performance.md "mention") reports. You can do so by adding a "user.rating" type to "messages":

```python
{
 "agentId": "1d3348a5-dc4c-44d2-83b0-3e53acf74a76",
 "firstMessageAt": "2025-03-11T10:51:00.000Z",
 "lastMessageAt": "2025-03-11T10:54:00.000Z",
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
     "type": "user.rating",
     "data": { "value": 3}
   }
 ]
}
```

### Including Detailed Feedback

For more comprehensive feedback analysis, you can include user comments along with their ratings:

```python
{
 "role": "debug",
 "type": "user.rating",
 "data": { "value": 5, "detail": "Optional User Detailed Feedback" }
}
```

With this additional information, the feedback section in the transcript will display both the numerical rating and the user's comments.

Examples of feedback with and without user comments are shown here:

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Note that multiple feedback entries can be included for the same conversation, and feedback can be submitted at any point during or after the interaction.
