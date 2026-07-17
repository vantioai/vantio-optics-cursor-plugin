# Vantio Optics — Cursor / Open Plugin

Read-only **Vantio Optics** MCP for Cursor and Open Plugins hosts.

## Install (manual)

```json
{
  "mcpServers": {
    "vantio-optics": {
      "command": "npx",
      "args": ["-y", "@vantio/optics-mcp"]
    }
  }
}
```

## Marketplace submit

| Field | Value |
|-------|--------|
| Repository | `vantioai/vantio-optics-cursor-plugin` |
| **Logotype URL** | `https://vantio.ai/vantio-logo.png` |
| Alt logo | `https://raw.githubusercontent.com/vantioai/vantio-optics-cursor-plugin/main/assets/logo.png` |
| Homepage | https://vantio.ai/platform |

### Cursor Marketplace
https://cursor.com/marketplace/publish → this repo → Logotype URL above

### cursor.directory
https://cursor.directory/mcp/new → this repo (needs root `mcp.json` / `.mcp.json`)

## Layout (Open Plugins + Cursor)

```
.cursor-plugin/plugin.json
.plugin/plugin.json
mcp.json
.mcp.json
rules/optics-observe.mdc
skills/vantio-optics/SKILL.md
assets/logo.svg
assets/logo.png
```

## Smithery note

Smithery’s publish form expects a **hosted HTTP MCP URL**, not a GitHub repo.
Optics is a **local stdio** server (`npx @vantio/optics-mcp`) reading `~/.vantio/runs`.
It is not a fit for Smithery’s remote URL flow unless we later ship a hosted gateway.

MIT · Vantio AI, Inc.


## Related: Gate dry-run MCP

```json
{
  "mcpServers": {
    "vantio-optics": { "command": "npx", "args": ["-y", "@vantio/optics-mcp"] },
    "vantio-gate": { "command": "npx", "args": ["-y", "@vantio/gate-mcp"] }
  }
}
```
