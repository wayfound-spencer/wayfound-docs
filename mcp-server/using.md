---
hidden: true
---

# Using

### MCP Server Address

The Wayfound MCP server can be accessed at:

```
https://app.wayfound.ai/sse
```

### Authentication

You can create an MCP API key in the Wayfound Settings/API screen

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

The MCP API key must be passed as an Authorization bearer token.

### Cursor Example

Add the following to your mcp.json file:

```
{
  "mcpServers": {
    "wayfound": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://app.wayfound.ai/sse",
        "--header",
        "Authorization:${AUTH_HEADER}"
      ],
      "env": {
        "AUTH_HEADER": "Bearer <YOUR_MCP_API_KEY>"
      }
    }
  }
}
```

### Claude Code Example

Run the following command line to add Wayfound MCP server to Claude Code:

```
claude mcp add --transport sse wayfound https://app.wayfound.ai/sse --header "Authorization: Bearer <YOUR_MCP_API_KEY>"
```

