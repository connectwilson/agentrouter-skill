# @agentrouter/mcp

Universal MCP server for AgentRouter.

AgentRouter routes AI agents to paid API/data services, supports quote-before-pay, invokes providers, verifies returned data, and returns an evidence envelope with trace hashes.

## Usage

Run with npx:

```bash
npx -y @agentrouter/mcp
```

Most AI clients configure MCP like this:

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

For a local AgentRouter server:

```json
{
  "mcpServers": {
    "AgentRouter": {
      "command": "npx",
      "args": ["-y", "@agentrouter/mcp"],
      "env": {
        "AGENT_ROUTER_URL": "http://127.0.0.1:8800",
        "AGENT_ROUTER_MAX_PRICE": "0.05"
      }
    }
  }
}
```

## Tools

- `agentrouter_request`: preferred structured capability request path for specialized, real-time, paid, or verifiable external data/API needs.
- `agentrouter_quote`: route and quote without invoking a provider.
- `agentrouter_capabilities`: list capability schemas when the main agent has a data/API need and needs to discover what AgentRouter can route.
- `agentrouter_ask`: natural-language routing helper when a structured capability request cannot be produced.

## Protocol Boundary

The main agent should parse user language into a structured capability request whenever possible. AgentRouter handles routing, quote, provider invocation, verification, payment metadata, and evidence.
