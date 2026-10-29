# Installing the Serpier MCP server

Serpier is a hosted, remote MCP server. Do not clone, build or run anything.

1. Add this server to the client's MCP configuration:

   ```json
   {
     "mcpServers": {
       "serpier": {
         "type": "http",
         "url": "https://app.serpier.com/api/mcp"
       }
     }
   }
   ```

2. The server uses OAuth. On the first connection the client opens Serpier in the browser; the user signs in, chooses an organization and allows access. Do not ask the user for an API key.
3. A user can also connect with a personal access token: it starts with `srpr_` and is sent as the `x-api-key` header. Personal access tokens need the Enterprise plan.
4. Verify the connection by listing the server's tools.

The user needs a Serpier account: https://serpier.com
