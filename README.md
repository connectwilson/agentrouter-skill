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

## Safe Skill Install

Paste this into a shell-capable agent or run it in a terminal. It downloads the AgentRouter Skill markdown only and does not execute a remote shell script:

```bash
mkdir -p "$HOME/.agents/skills/agentrouter" "$HOME/.claude/skills/agentrouter" "$HOME/.codex/skills/agentrouter" && curl -fsSL https://agentrouter.network/skills/AgentRouter/SKILL.md -o "$HOME/.agents/skills/agentrouter/SKILL.md" && cp "$HOME/.agents/skills/agentrouter/SKILL.md" "$HOME/.claude/skills/agentrouter/SKILL.md" && cp "$HOME/.agents/skills/agentrouter/SKILL.md" "$HOME/.codex/skills/agentrouter/SKILL.md"
```

After installation, ask your agent a normal data/API question:

```text
Find BTC liquidation max pain right now.
```

If native MCP tools are not attached, the skill uses the hosted AgentRouter HTTP or CLI path:

```bash
AGENT_ROUTER_URL=https://agentrouter.network AGENT_ROUTER_MAX_PRICE=0.05 npx -y --package github:connectwilson/agentrouter-markets#main agent-router ask "BTC liquidation max pain"
```

For local terminals where you are comfortable auditing and running the installer script, this advanced installer is also available:

```bash
curl -fsSL https://agentrouter.network/install.sh | bash
```

This works for shell-capable agents such as Claude Code, Codex, OpenClaw, Hermes, Cursor, and Windsurf.

If your agent environment supports the `skills` CLI and GitHub cloning, this also works:

```bash
npx -y skills@latest add connectwilson/agentrouter-skill --skill AgentRouter -g -y --copy
```

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
