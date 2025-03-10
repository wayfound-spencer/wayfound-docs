# Wayfound Manager SDK

The Wayfound Manager SDK provides a simple interface for interacting with the Wayfound Manager API. It allows developers to seamlessly integrate Wayfound's AI agent management capabilities with their third-party agents using Python.

### Getting started

{% hint style="info" %}
First, you should have at least one third-party agent connected to the Wayfound platform. If you have not yet connected an agent, visit [the-agents-page.md](agents/the-agents-page.md "mention") and connect an agent.
{% endhint %}

You can install the Wayfound SDK using pip:

```python
pip install wayfound
```

To use the Wayfound Manager SDK, you'll need a Wayfound API key and an agent ID. The Agent ID is available on the agent's corresponding page in [the-agents-page.md](agents/the-agents-page.md "mention"). API keys can be obtained by users with admin permissions from the [API page](settings/api.md).

The API key and agent ID can be set as environment variables or passed directly to the Recording class:

<pre class="language-python"><code class="lang-python"><strong>from wayfound import Recording
</strong>
recording = Recording(wayfound_api_key="your_api_key", agent_id="your_agent_id")
</code></pre>

The SDK provides methods to record new messages, update existing recordings, and add details like user ratings and handoffs. For example:

```python
# Record new messages
messages = [
    {"role": "assistant", "content": "Hello, how can I help you?"},
    {"role": "user", "content": "I need assistance with my account"}
    
    # Add user ratings
    {
      "role": "debug",
      "type": "user.rating",
      "data": { "value": 3, "detail": "Optional User Detailed Feedback" }
    },
    
    #AI agent to human handoff
    {
      "role": "debug",
      "type": "agent.handoff",
      "data": { "content": "Jane Doe joined the conversation" }
    }
]
recording.record_messages(messages)
```

### LangChain Integration

The Wayfound Manager SDK also supports recording messages directly from Langchain memory objects. This allows you to use Wayfound to monitor and manage agents built with LangChain. For example:

```python
from wayfound import Recording
from langchain.memory import ConversationBufferMemory

recording = Recording(wayfound_api_key="your_api_key", agent_id="your_agent_id")

memory = ConversationBufferMemory(return_messages=True)
# ... after some conversation with Langchain ...
recording.record_messages_from_langchain_memory(memory)
```

### Resources

* PyPI Project: [https://pypi.org/project/wayfound/](https://pypi.org/project/wayfound/)
* Source Code: [https://github.com/Wayfound-AI/wayfound-sdk-python](https://github.com/Wayfound-AI/wayfound-sdk-python)

{% hint style="info" %}
Note: The Wayfound SDK is currently available only in python. A javascript&#x20;
{% endhint %}

