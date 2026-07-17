---
name: vantio-optics
description: Observe AI agent LLM egress with Vantio Optics MCP (Sight Loop). Read-only proofs and host discovery.
---

# Vantio Optics

Use the `vantio-optics` MCP server (`npx -y @vantio/optics-mcp`).

## Tools
- `optics_list_runs` / `optics_get_run` — local run metadata
- `optics_prove` — Markdown Sight Loop proof
- `optics_discover_local` — hosts from local logs
- `optics_explain` — privacy fence
- `optics_upgrade_path` — Optics → Gate → Phantom Engine

Fence: observe only. No prompts/completions retained.
