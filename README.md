# caddy-mcp

Caddy graph MCP server. Gives Claude access to your org's knowledge graphs: portal login, graph pull and query, account maps, and packages. Ships as a single bundled file with zero runtime dependencies.

## Install: Claude Desktop / Cowork (recommended)

Download `dist/caddy-mcp.mcpb` and open it. Claude Desktop installs it as an extension and runs the server on its own bundled Node runtime, so nothing else needs to be installed on the machine.

Team rollout: an org owner uploads `caddy-mcp.mcpb` once under Organization settings > Connectors > Desktop. Every team member then installs it from the org's extension list in one click. The caddy-mcp tools are available in both chat and Cowork sessions.

## Install: Claude Code

The server ships inside the `caddy-agent` plugin:

```
claude plugin marketplace add meetcaddy/marketplace
claude plugin install caddy-agent@meetcaddy
```

## First run

1. Ask Claude to run `graph_login`.
2. Open the authorize URL it returns, log in to the portal, and grant your orgs.
3. Claude polls `graph_auth_status` until it reports authenticated.

Credentials land in `~/.caddy/credentials.json`, graphs cache to `~/.caddy/graphs` (override with `GRAPH_DIR`). Graph data stays on the machine: the portal streams it here and keeps no copy.

## Requirements

None for the desktop extension install. For manual or CLI use: Node 18+.

## Rebuilding the bundle

```
npx -y @anthropic-ai/mcpb validate manifest.json
npx -y @anthropic-ai/mcpb pack . dist/caddy-mcp.mcpb
```

`manifest.json` at the repo root describes the extension; `.mcpbignore` keeps the packed bundle to runtime files only.
