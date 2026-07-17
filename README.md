# Vantio Optics — Cursor plugin

Read-only **Vantio Optics** MCP for Cursor. Sight Loop observe: list runs, export proofs, discover hosts. Cannot enforce — upgrade to Gate / Phantom Engine when needed.

## Install

From Cursor Marketplace (after listing), or add manually:

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

## Links

- Platform: https://vantio.ai/platform
- npm: https://www.npmjs.com/package/@vantio/optics-mcp
- Source: https://github.com/vantioai/vantio-open-core/tree/main/packages/vantio-optics-mcp

MIT · Vantio AI, Inc.

## Marketplace listings

| Surface | Status / link |
|---------|----------------|
| Official MCP Registry | Live — `io.github.vantioai/vantio-optics` |
| npm | `@vantio/optics-mcp` |
| Cursor Marketplace | Submit: https://cursor.com/marketplace/publish |
| cursor.directory | https://cursor.directory/mcp/new |
| mcp.so | https://mcp.so/submit?type=server |
| Smithery | https://smithery.ai/new |
| PulseMCP | Auto from registry; expedite hello@pulsemcp.com |
| Glama | Auto-index from GitHub `mcp` topic |
| awesome-mcp-servers | https://github.com/punkpeye/awesome-mcp-servers/pull/10326 |

### Cursor Marketplace submit (manual review)

1. Open https://cursor.com/marketplace/publish
2. Point at this repository: `vantioai/vantio-optics-cursor-plugin`
3. Wait for Cursor security review
