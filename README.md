# AgentRouter Skill

AgentRouter is a generic bootstrap skill plus Claude Desktop extension for connecting AI clients to the Agent Native Data Network.

## Claude Desktop No-Command Install

Download `agentrouter.mcpb` from this repo and install it in Claude Desktop:

```text
Settings -> Extensions -> Install Extension -> choose agentrouter.mcpb
```

Use the default config:

```text
AgentRouter URL = https://agentrouter-markets-production.up.railway.app
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
