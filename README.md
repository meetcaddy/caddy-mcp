# caddy-mcp

Caddy graph MCP server, packaged as a Claude Code plugin. Gives a Claude Code session access to your org's knowledge graphs: portal login, graph pull/query, account maps, and packages.

## Install

```
/plugin marketplace add meetcaddy/caddy-mcp
/plugin install caddy-mcp@caddy
```

Restart Claude Code when prompted.

## First run

1. Ask Claude to run `graph_login`.
2. Open the authorize URL it returns, log in to the portal, and grant your orgs.
3. Claude polls `graph_auth_status` until it reports authenticated.

Credentials land in `~/.caddy/credentials.json`, graphs cache to `~/.caddy/graphs` (override with `GRAPH_DIR`).

## Requirements

Node 18+ on PATH. No other dependencies — the server ships as a single bundled file.
