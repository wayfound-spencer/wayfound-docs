# Connecting Agents

The Wayfound Manager SDK provides a simple interface for connecting agents to Wayfound. It allows developers to seamlessly integrate Wayfound's AI agent management capabilities with their third-party agents using Python or JavaScript.

The **Connection** page provides instructions and information for connecting your third-party agent to Wayfound. It includes the agent's unique ID, which is required for use of the Wayfound SDK.

<figure><img src="../.gitbook/assets/Screenshot 2025-03-10 at 10.50.02 AM.png" alt=""><figcaption></figcaption></figure>



### Getting started

{% hint style="info" %}
First, you should have at least one third-party agent connected to the Wayfound platform. If you have not yet connected an agent, visit [the-agents-page.md](the-agents-page.md "mention") and connect an agent.
{% endhint %}

#### Connecting Agents with Python

You can install the Wayfound SDK using pip:

```python
pip install wayfound
```

To use the Wayfound Manager SDK, you'll need a Wayfound API key and an agent ID. The Agent ID is available on the agent's Connection page. API keys can be obtained by users with admin permissions from the [API page](../api.md).

The SDK provides methods to record new messages, update existing recordings, and add details like user ratings and handoffs. For example:

```python
from wayfound import Recording

recording = Recording(wayfound_api_key="<API KEY>", agent_id="f9380cc1-19ff-43d1-b933-9faba7adcb58")

# Record new messages
messages = [
    {"role": "assistant", "content": "Hello, how can I help you?"},
    {"role": "user", "content": "I need assistance with my account"}
]
recording.record_messages(messages)
```

#### Connecting Agents with JavaScript:

You can install the Wayfound SDK using npm:

```
npm install wayfound
```

To use the Wayfound Manager SDK, you'll need a Wayfound API key and an agent ID. The Agent ID is available on the agent's Connection page. API keys can be obtained by users with admin permissions from the [API page](../api.md).

The SDK provides methods to record new messages, update existing recordings, and add details like user ratings and handoffs. For example:

```javascript
import { Recording } from 'wayfound';

const recording = new Recording({
  wayfoundApiKey: '<API KEY>',
  agentId: 'f9380cc1-19ff-43d1-b933-9faba7adcb58'
});

// Record new messages
const messages = [
  { role: 'assistant', content: 'Hello, how can I help you?' },
  { role: 'user', content: 'I need assistance with my account' }
];
recording.recordMessages(messages);
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
* npm Package: [https://www.npmjs.com/package/wayfound](https://www.npmjs.com/package/wayfound)
* Source Code: [https://github.com/Wayfound-AI/wayfound-sdk-python](https://github.com/Wayfound-AI/wayfound-sdk-python)

