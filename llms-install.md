# Installing the IndiaCos MCP server

The IndiaCos MCP server is hosted. Do not clone or build anything.

1. Add this remote server to the MCP settings (Streamable HTTP):

```json
{
  "mcpServers": {
    "indiacos": {
      "type": "streamableHttp",
      "url": "https://indiacos.com/mcp"
    }
  }
}
```

2. OAuth 2.1: sign in with your IndiaCos account when your client asks. Or send an API key as a header: `Authorization: Bearer YOUR_KEY` (one key works for the REST API and MCP).

3. Test it by asking: "Verify GSTIN 27AAOCM9194L2ZF: legal name, status, directors and other GST registrations under the same PAN."
