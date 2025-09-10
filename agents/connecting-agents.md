# Connecting Agents

The Wayfound Manager SDK provides a simple interface for connecting agents to Wayfound. It allows developers to seamlessly integrate Wayfound's AI agent supervision capabilities with their third-party agents using Python, JavaScript or simple REST API endpoints directly.

The **Connection** page provides instructions and information for connecting your third-party agent to Wayfound. It includes the agent's unique ID, which is required for use of the Wayfound SDK.

<figure><img src="../.gitbook/assets/Untitled (1).png" alt=""><figcaption></figcaption></figure>



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
from wayfound import Session

wayfound_api_key = "<API KEY>"
wayfound_agent_id = "<AGENT_ID>"

wayfound_session = Session(wayfound_api_key=wayfound_api_key, agent_id=wayfound_agent_id)

messages = []

messages.append({
    "timestamp": "2025-05-07T10:00:00Z",
    "event_type": "assistant_message",
    "attributes": {
      "content": "Hello, how can I help you today?",
    }
  })

messages.append({
    "timestamp": "2025-05-07T10:00:04Z",
    "event_type": "user_message",
    "attributes": {
      "content": "What's the current status of Project Alpha?"
    }
  })

result = wayfound_session.complete_session(messages=messages)
```

#### Connecting Agents with JavaScript:

You can install the Wayfound SDK using npm:

```
npm install wayfound
```

To use the Wayfound Manager SDK, you'll need a Wayfound API key and an agent ID. The Agent ID is available on the agent's Connection page. API keys can be obtained by users with admin permissions from the [API page](../api.md).

The SDK provides methods to record new messages, update existing recordings, and add details like user ratings and handoffs. For example:

```javascript
import { Session } from "wayfound";

const wayfoundApiKey = "<API KEY>";
const agentId = "<AGENT_ID>";

const session = new Session({ wayfoundApiKey, agentId });

const messages = [
  {
    timestamp: "2025-05-07T10:00:00Z",
    event_type: "assistant_message",
    attributes: {
      content: "Hello, how can I help you today?",
    },
  },
  {
    timestamp: "2025-05-07T10:00:10Z",
    event_type: "user_message",
    attributes: {
      content: "What's the current status of Project Alpha?",
    },
  },
];

const response = await session.completeSession({ messages });
```

### Resources

* PyPI Project: [https://pypi.org/project/wayfound/](https://pypi.org/project/wayfound/)
* npm Package: [https://www.npmjs.com/package/wayfound](https://www.npmjs.com/package/wayfound)
* Python Source Code: [https://github.com/Wayfound-AI/wayfound-sdk-python](https://github.com/Wayfound-AI/wayfound-sdk-python)
* Javascript Source Code: [https://github.com/Wayfound-AI/wayfound-sdk-javascript](https://github.com/Wayfound-AI/wayfound-sdk-javascript)

