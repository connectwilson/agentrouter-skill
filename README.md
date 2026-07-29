# AgentRouter Skill

Install AgentRouter once for supported AI agents:

```bash
npx @agentrouternetwork/agentrouter --full
```

The command installs the Skill, adds one AgentRouter MCP entry to one detected
supported AI client, and verifies that `agentrouter_fetch` is available. It
preserves unrelated MCP entries, creates a timestamped config backup, and does
not create a local wallet.

After installation, ask a normal data question, for example:

```text
What are real users complaining about Kimi K3 across social platforms?
```

AgentRouter's hosted capabilities, providers, routing logic, filtering, and MCP tools update server-side. Users do not reinstall the Skill for normal feature releases.

Public X status URLs route through the installed MCP bridge's fixed read-only
local connector. Browser credentials and cookies remain on the user's device.

Skill plus HTTP-only fallback:

```bash
npx @agentrouternetwork/agentrouter
```

Canonical live instructions:

```text
https://agentrouter.network/SKILL.md
```
