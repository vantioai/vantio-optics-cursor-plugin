---
name: vantio-optics
description: Observe AI agent LLM egress with Vantio Optics MCP (Sight Loop). Read-only proofs and host discovery.
---

# Vantio Optics

Use the `vantio-optics` MCP server (`npx -y @vantio/optics-mcp`).

Optics helps you see. Gate applies the rules you set. Phantom Engine protects the machines you own.

## Tools
- `optics_list_runs` / `optics_get_run` — local run metadata
- `optics_prove` — Markdown Sight Loop proof
- `optics_discover_local` — hosts from local logs
- `optics_explain` — privacy fence
- `optics_upgrade_path` — Optics → Gate → Phantom Engine

Fence: observe only. No prompts or completions retained.

## What this MCP covers

This plugin reads local `~/.vantio/runs` from Node `vantio run` (`@vantio/cli` 0.3.2 wraps fetch and Node http/https) or from Python `shield()` (`vantio-agent-sdk` 3.0.2 wraps urllib, and requests/httpx when those libraries are already installed). It does not enforce policy and it does not see curl, raw sockets, or browser paths.

Optics is observe-only metadata. When you need Vantio to stop a host, redact a payload, or enforce a spend ceiling on the wrapped path, upgrade to Vantio Gate. When you need protection on Linux machines you own that still holds if an agent tries to go around application rules, upgrade to Phantom Engine.
