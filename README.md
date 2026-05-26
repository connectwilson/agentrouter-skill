# AgentRouter Skill

AgentRouter is a generic bootstrap skill plus a universal MCP server for connecting AI clients to the Agent Native Data Network. A Claude Desktop extension is also available as an optional no-command install path.

## Claude Desktop No-Command Install

Download `agentrouter.mcpb` from this repo and install it in Claude Desktop:

```text
Settings -> Extensions -> Install Extension -> choose agentrouter.mcpb
```

Use the default config:

```text
AgentRouter URL = https://agentrouter-markets.onrender.com
Default Max Price = 0.05
```

Then ask Claude:

```text
Use AgentRouter to find BTC liquidation max pain right now.
```

## One-Line Skill Install

Paste this into Claude Code chat or run it in a terminal:

```bash
npx -y skills@latest add connectwilson/agentrouter-skill --skill AgentRouter --agent claude-code -g -y --copy
```

After installation, ask your agent:

```text
Use AgentRouter to find BTC liquidation max pain right now.
```

If native MCP tools are not attached, the skill uses the hosted AgentRouter CLI fallback:

```bash
AGENT_ROUTER_URL=https://agentrouter-markets.onrender.com AGENT_ROUTER_MAX_PRICE=0.05 npx -y --package github:connectwilson/agentrouter-markets#main agent-router ask "BTC liquidation max pain"
```

This works for shell-capable agents such as Claude Code, Codex, OpenClaw, Hermes, Cursor, and Windsurf.

## Remote MCP Connector

For Claude web, Claude Managed Agents, and any product that supports URL-based Remote MCP, add this connector URL:

```text
https://agentrouter-markets.onrender.com/mcp
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
        "AGENT_ROUTER_URL": "https://agentrouter-markets.onrender.com",
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
