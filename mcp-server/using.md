# Using

### MCP Server Address

The Wayfound MCP server can be accessed at:

```
https://app.wayfound.ai/mcp
```

### Authentication

You can authenticate into Wayfound using either OAuth or an API key.  Both methods can be done on the Wayfound Settings/Connections screen

You can create an MCP API key in the Wayfound Settings/API screen

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

#### OAuth

An organization admin can enable OAuth for their organization by toggling the "Wayfound MCP Server OAuth" switch in the blue banner.

#### API Key

The MCP API key must be passed as an Authorization bearer token. Be sure to use Key Type: MCP

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

### Cursor Example

Add the following to your mcp.json file.  Choose the example that matches your authentication method:

#### API Key

```
{
  "mcpServers": {
    "wayfound": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://app.wayfound.ai/mcp",
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

#### OAuth

```
{
  "mcpServers": {
    "Wayfound": {
      "url": "https://app.wayfound.ai/mcp",
      "transport": "http"
    }
  }
}
```

### Claude Code Example

Run the following command line to add Wayfound MCP server to Claude Code:

#### API Key

```
claude mcp add --transport http wayfound https://app.wayfound.ai/mcp --header "Authorization: Bearer <YOUR_MCP_API_KEY>"
```

#### OAuth

```
claude mcp add --transport http wayfound https://app.wayfound.ai/mcp
```
