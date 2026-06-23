# API

Wayfound offers APIs to connect your agents to the platform. You can generate an API key on the **Connections tab** in the **Settings** page. Access to this page requires admin permissions on the Wayfound platform.

[Learn more about implementing Wayfound's APIs here](https://wayfound-api.readme.io/reference/get-agents).

For more information about connecting agents to Wayfound in order to leverage the API see here:

{% content-ref url="agents/connecting-agents.md" %}
[connecting-agents.md](agents/connecting-agents.md)
{% endcontent-ref %}

## Creating and Configuring Supervisor Agents

Examples for creating supervisor agents and setting their **role**, **goal**, and **guidelines** through the Wayfound public **v2** API.

### Authentication

All requests use a Bearer token in the `Authorization` header. The token is a Wayfound **API key** (a UUID), created under **Settings → Connections**.

```
Authorization: Bearer 550e8400-e29b-41d4-a716-446655440000
Content-Type: application/json
```

Notes:

* The key must be UUID-format or you get `401 Unauthorized: Invalid API key`.
* **MCP-type keys are rejected.** Use a standard API key.
* The key scopes every request to its organization automatically.

### Fields

| API field    | Type      | Required | Notes                                                        |
| ------------ | --------- | -------- | ------------------------------------------------------------ |
| `name`       | string    | yes      | Display name of the agent.                                   |
| `role`       | string    | no       | Who the agent is / its persona. Stored as the description.   |
| `goal`       | string    | no       | What the agent is trying to accomplish.                      |
| `guidelines` | object\[] | no       | Rules the supervisor evaluates sessions against (see below). |

### Guideline Object

| Field      | Type   | Required | Notes                                                |
| ---------- | ------ | -------- | ---------------------------------------------------- |
| `type`     | string | yes      | One of the guideline types below.                    |
| `content`  | string | yes      | The rule text. Cannot be empty / whitespace-only.    |
| `priority` | string | yes      | `"medium"` or `"high"`.                              |
| `context`  | string | no       | Optional extra context for the rule. Defaults to "". |

#### Valid Types

| `type`             | Meaning              |
| ------------------ | -------------------- |
| `prohibitedAction` | Prohibited actions   |
| `prohibitedWords`  | Prohibited words     |
| `preferredVoice`   | Preferred voice/tone |
| `formatting`       | Formatting rules     |
| `security`         | Security rules       |
| `bestPractices`    | Best practices       |
| `aiDisclosure`     | AI disclosure        |
| `otherEvaluation`  | Other evaluation     |

**Valid `priority` values:** `"medium"` or `"high"`.



### 1. Create a supervisor agent (role + goal + guidelines)

`POST /api/v2/agents`

```bash
curl -X POST https://app.wayfound.ai/api/v2/agents \
  -H "Authorization: Bearer $WAYFOUND_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Banking Assistant",
    "role": "Front-line virtual assistant for Atlas Bank retail customers.",
    "goal": "Answer everyday banking questions quickly and safely while verifying identity before sharing any account-specific details.",
    "guidelines": [
      {
        "type": "security",
        "content": "Verify the customer'\''s identity (name plus one security factor) before sharing any account-specific details such as balance, transactions, or card numbers.",
        "priority": "high"
      },
      {
        "type": "prohibitedAction",
        "content": "Never read back a full card number, full account number, or SSN. Only the last 4 digits.",
        "priority": "high"
      },
      {
        "type": "aiDisclosure",
        "content": "Always identify yourself as an AI assistant. Never imply or claim to be a human employee.",
        "priority": "high"
      },
      {
        "type": "bestPractices",
        "content": "For a disputed transaction, hand off to the Disputes & Transactions specialist.",
        "priority": "medium"
      }
    ]
  }'
```

**Response — `200 OK`**

```json
{
  "id": "8c0e89d0-2c7a-4c3e-9c6b-9f8a5d1e7c2a",
  "createdAt": "2026-06-23T14:32:15.123Z"
}
```

`id` is the agent's UUID — use it for all subsequent calls.

#### Minimal create (name only)

`name` is the only required field. Role, goal, and guidelines can be added later with a PUT.

```bash
curl -X POST https://app.wayfound.ai/api/v2/agents \
  -H "Authorization: Bearer $WAYFOUND_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{ "name": "Disputes & Transactions" }'
```

***

### 2. Update role, goal, or guidelines

`PUT /api/v2/agents/{agentId}`

Send only the fields you want to change. Each PUT republishes the agent.

**Update the goal only:**

```bash
curl -X PUT https://app.wayfound.ai/api/v2/agents/8c0e89d0-2c7a-4c3e-9c6b-9f8a5d1e7c2a \
  -H "Authorization: Bearer $WAYFOUND_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "goal": "Resolve account questions and money-movement requests within one session, escalating anything that fails identity verification."
  }'
```

**Replace the full guideline set:**

> `guidelines` is replaced wholesale, not merged. Always send the complete list you want the agent to have.

```bash
curl -X PUT https://app.wayfound.ai/api/v2/agents/8c0e89d0-2c7a-4c3e-9c6b-9f8a5d1e7c2a \
  -H "Authorization: Bearer $WAYFOUND_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "role": "Atlas Bank specialist for disputes and money movement.",
    "guidelines": [
      {
        "type": "security",
        "content": "Re-verify identity before opening a dispute or moving money.",
        "priority": "high"
      },
      {
        "type": "bestPractices",
        "content": "For a disputed transaction, open a dispute case and explain the timeline to the customer.",
        "priority": "medium"
      }
    ]
  }'
```

**Response — `200 OK`**

```json
{
  "id": "8c0e89d0-2c7a-4c3e-9c6b-9f8a5d1e7c2a",
  "createdAt": "2026-06-23T14:32:15.123Z",
  "updatedAt": "2026-06-23T15:04:51.880Z"
}
```

> **Archiving is exclusive.** `{ "archived": true }` (or `false`) must be sent on its own — combining it with any other field returns `400`.

### 3. Read agents back

**List all agents:**

```bash
curl https://app.wayfound.ai/api/v2/agents \
  -H "Authorization: Bearer $WAYFOUND_API_KEY"
```

**Get one agent (add `?detail=full` for sections/directives):**

```bash
curl https://app.wayfound.ai/api/v2/agents/8c0e89d0-2c7a-4c3e-9c6b-9f8a5d1e7c2a \
  -H "Authorization: Bearer $WAYFOUND_API_KEY"
```

**Response (shape):**

```json
{
  "id": "8c0e89d0-2c7a-4c3e-9c6b-9f8a5d1e7c2a",
  "createdAt": "2026-06-23T14:32:15.123Z",
  "updatedAt": "2026-06-23T15:04:51.880Z",
  "name": "Banking Assistant",
  "role": "Front-line virtual assistant for Atlas Bank retail customers.",
  "goal": "Answer everyday banking questions quickly and safely...",
  "guidelines": [
    {
      "uuid": "a1b2c3d4-e5f6-4a7b-8c9d-0e1f2a3b4c5d",
      "type": "security",
      "priority": "high",
      "content": "Verify the customer's identity..."
    }
  ]
}
```

Note that on read, `priority` comes back as `"medium"`/`"high"`.

### Validation & error reference

| Status | Body                                                                              | Cause                                         |
| ------ | --------------------------------------------------------------------------------- | --------------------------------------------- |
| `400`  | `{ "error": "Missing name field" }`                                               | `name` omitted on create.                     |
| `400`  | `{ "error": "Invalid guideline type: <type>. Valid types are: ..." }`             | `type` not in the allowed list.               |
| `400`  | `{ "error": "Invalid priority: <priority>. Valid priorities are: medium, high" }` | `priority` not `medium`/`high`.               |
| `400`  | `{ "error": "Guideline content cannot be empty for <label>..." }`                 | Empty/whitespace `content`.                   |
| `400`  | `{ "error": "Agent Id is invalid format" }`                                       | Path UUID malformed.                          |
| `400`  | `{ "error": "Cannot update archived status with other fields" }`                  | `archived` combined with other fields on PUT. |
| `400`  | `{ "error": "Invalid agent architecture" }`                                       | Agent wasn't created via the API (not `SDK`). |
| `401`  | `{ "message": "No authorization header provided" }`                               | Missing `Authorization` header.               |
| `401`  | `{ "message": "Unauthorized: Invalid API key" }`                                  | Bad/non-UUID/MCP-type key.                    |
| `404`  | (empty)                                                                           | Agent not found in your org.                  |

***

