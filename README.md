# Serpier MCP server

[![Serpier on Glama](https://glama.ai/mcp/connectors/com.serpier/serpier/badges/score.svg)](https://glama.ai/mcp/connectors/com.serpier/serpier)

<img src="assets/logo.png" alt="Serpier" width="96" align="right">

[Serpier](https://serpier.com) is an SEO platform for marketing teams and agencies. The Serpier MCP server lets an AI assistant work in your Serpier account: monitor your brand's AI Visibility, track published articles, and find publishers and manage link-building orders.

This is a hosted, remote MCP server. There is nothing to install or run. This repository holds the connection details and the metadata that MCP registries and directories read.

| | |
|---|---|
| Server URL | `https://app.serpier.com/api/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE. Dynamic Client Registration and Client ID Metadata Documents are supported. |
| Registry name | [`com.serpier/serpier`](https://registry.modelcontextprotocol.io/v0.1/servers?search=com.serpier/serpier) |
| Docs | [docs.serpier.com/mcp](https://docs.serpier.com/mcp) |

## What the assistant can do

- **AI Visibility**: see how often your brand is mentioned and cited in AI answers for the prompts you track, add or remove prompts, and start new analysis runs.
- **Publication tracking**: check whether published articles are live, indexed and still linking to you, and add new articles to monitor.
- **Marketplace**: search Serpier's catalog of vetted publishers by country, topic, price and authority.
- **Cart and orders**: add publishers to your cart, place orders, follow order status and fill in the brief for each publication.
- **Projects**: list and create the website projects in your organization.

Actions that change data are marked as such, so your assistant can ask you before running them. Placing an order is a real purchase, paid by card or invoice.

## Connect

You need a Serpier account. [Sign up at serpier.com](https://serpier.com). When your client connects for the first time, it opens Serpier in your browser. Sign in, choose the organization and team, and allow access. You never paste a key.

### Claude

In **Settings > Connectors**, select **Add custom connector**, name it Serpier, and paste the server URL.

### ChatGPT

Add a custom app with the server URL, then select **Authenticate** and sign in to Serpier.

### Claude Code

```bash
claude mcp add --transport http serpier https://app.serpier.com/api/mcp
```

Then run `/mcp` in Claude Code, select **serpier**, and sign in.

### Cursor, VS Code and other clients

Add the server to your client's MCP configuration ([`mcp.json`](mcp.json)):

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

VS Code uses `servers` as the top-level key instead of `mcpServers`.

### Gemini CLI

```bash
gemini extensions install https://github.com/Serpier/serpier-mcp
```

### Personal access token

You can also connect with a personal access token, sent in the `x-api-key` header. Personal access tokens need the Enterprise plan; see [Create a personal access token](https://docs.serpier.com/account-settings#create-a-personal-access-token).

## Privacy and support

- Privacy policy: [serpier.com/privacy-policy](https://serpier.com/privacy-policy)
- Terms: [serpier.com/terms-conditions](https://serpier.com/terms-conditions)
- Support: [hello@serpier.com](mailto:hello@serpier.com)

## Files in this repository

| File | Read by |
|---|---|
| [`server.json`](server.json) | The [Official MCP Registry](https://registry.modelcontextprotocol.io) and the directories that import from it, such as the GitHub MCP Registry |
| [`mcp.json`](mcp.json) | MCP clients that take a JSON server configuration |
| [`gemini-extension.json`](gemini-extension.json) | Gemini CLI |
| [`llms-install.md`](llms-install.md) | AI agents that install MCP servers for you, such as Cline |

## Releasing

1. Raise `version` in `server.json` and `gemini-extension.json` to the same value.
2. Merge to `main`, then push a tag `v<version>`.
3. The [publish workflow](.github/workflows/publish.yml) publishes `server.json` to the Official MCP Registry. It signs in with the `serpier.com` DNS key stored in the `MCP_REGISTRY_PRIVATE_KEY` secret.

## License

[MIT](LICENSE). The license covers the files in this repository. The Serpier service is covered by the [Serpier terms](https://serpier.com/terms-conditions).
