# Vantio Optics — Cursor / Open Plugin

Read-only **Vantio Optics** MCP for Cursor and Open Plugins hosts. Optics helps you see where agents go — host, size, process, time — without reading prompts or completions. It does not block, redact, or cap spend.

Vantio AI (Pittsburgh, 2026): Optics helps you see. Phantom Engine is runtime protection on enrolled Linux — Observe, Enforce, and Control in one purchase. Enterprise adds governance when you need proof and process on top — talk to sales.

Homepage: [vantio.ai/optics](https://vantio.ai/optics) · Pricing: [vantio.ai/pricing](https://vantio.ai/pricing)

## Install (manual)

Generate local run logs first (`npx @vantio/cli run node agent.js`, or Python `shield()` from `vantio-agent-sdk`), then add:

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

This MCP reads `~/.vantio/runs` on your machine. It is observe only.

## Marketplace submit

| Field | Value |
|-------|--------|
| Repository | `vantioai/vantio-optics-cursor-plugin` |
| **Logotype URL** | `https://vantio.ai/vantio-logo.png` |
| Alt logo | `https://raw.githubusercontent.com/vantioai/vantio-optics-cursor-plugin/main/assets/logo.png` |
| Homepage | https://vantio.ai/optics |

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

## Related: Phantom Engine dry-run MCP (legacy package name)

`@vantio/gate-mcp` is a legacy compatibility package for Phantom Engine application-path enforcement dry-run. Gate is not a separate Vantio product or subscription. Evaluate only — not live enforce:

```json
{
  "mcpServers": {
    "vantio-optics": { "command": "npx", "args": ["-y", "@vantio/optics-mcp"] },
    "vantio-gate": { "command": "npx", "args": ["-y", "@vantio/gate-mcp"] }
  }
}
```
