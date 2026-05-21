# AgentRouter Skill

AgentRouter is a generic bootstrap skill plus Claude Desktop extension for connecting AI clients to the Agent Native Data Network.

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
用 AgentRouter 查 BTC 当前最大爆仓痛点是多少
```

## Skill Install Prompt

You can also ask an AI client to install the skill from this repo:

```text
请从这个 GitHub 链接安装 AgentRouter Skill：
https://github.com/connectwilson/agentrouter-skill

安装后，如果当前客户端支持 MCP，请优先帮我连接 AgentRouter MCP；如果是 Claude Desktop，请优先使用仓库里的 agentrouter.mcpb 扩展包。
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
