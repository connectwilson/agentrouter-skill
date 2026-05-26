# AgentRouter Skill

AgentRouter is a generic bootstrap skill plus a universal MCP server for connecting AI clients to the Agent Native Data Network. A Claude Desktop extension is also available as an optional no-command install path.

## Claude Desktop No-Command Install

Download `agentrouter.mcpb` from this repo and install it in Claude Desktop:

```text
Settings -> Extensions -> Install Extension -> choose agentrouter.mcpb
```

Use the default config:

```text
AgentRouter URL = https://agentrouter.network
Default Max Price = 0.05
```

Then ask a normal data question:

```text
Find BTC liquidation max pain right now.
```

## Skill Install

For paid data calls, paste this into a shell-capable agent or run it in a terminal:

```bash
npx -y agentrouter
```

Before the npm package is published, run the same installer from GitHub:

```bash
npx -y github:connectwilson/agentrouter-markets#main
```

The installer adds the AgentRouter Skill, configures supported local MCP clients when their config directories are present, creates a local encrypted AgentRouter wallet, and prints the Arc Testnet USDC funding address. After install, restart or reload the AI client. For the first paid data request, AgentRouter checks the quote/payment path first and shows wallet funding instructions if the local Arc wallet needs USDC. The agent should not bypass that prompt with web search or a provider-specific MCP tool.

After installation, ask your agent a normal data/API question:

```text
Find BTC liquidation max pain right now.
```

For quote-only Skill behavior, the standard Skills CLI still works:

```bash
npx skills add connectwilson/agentrouter-skill --skill AgentRouter
```

Manual fallback if npm/npx is unavailable:

```bash
curl -fsSL https://agentrouter.network/install.sh | bash
```

This works for shell-capable agents such as Claude Code, Codex, OpenClaw, Hermes, Cursor, and Windsurf.

## Remote MCP Connector

For Claude web, Claude Managed Agents, and any product that supports URL-based Remote MCP, add this connector URL:

```text
https://agentrouter.network/mcp
```

## Skill Install Prompt

You can also ask an AI client to install the skill from this repo:

```text
Install the AgentRouter Skill from this GitHub repo:
https://github.com/connectwilson/agentrouter-skill

After installation, if the current client supports MCP, connect the AgentRouter MCP router. If this is Claude Desktop, prefer the bundled agentrouter.mcpb extension package.
```

## Universal MCP via npm/npx

For Cursor, Windsurf, Cline, Continue, VS Code, and other MCP-capable clients, use the npm package path after publication:

```json
{
  "mcpServers": {
    "AgentRouter": {
      "command": "npx",
      "args": ["-y", "@agentrouter/mcp"],
      "env": {
        "AGENT_ROUTER_URL": "https://agentrouter.network",
        "AGENT_ROUTER_MAX_PRICE": "0.05"
      }
    }
  }
}
```

Package source is included in:

```text
packages/agentrouter-mcp
```

Before npm publication, local development clients can point directly to:

```text
packages/agentrouter-mcp/bin/agentrouter-mcp.js
```
