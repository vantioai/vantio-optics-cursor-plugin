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

| Path | Who | Mechanism | Not claimed |
|------|-----|-----------|-------------|
| **Client Cursor / Open Plugin (this MCP)** | Developer IDE | `npx @vantio/optics-mcp` reads local `~/.vantio/runs` from Node `vantio run` | Gate Latch BLOCK; PE DENY |
| **Python agents (local observe)** | Developer / agent host | Python `shield()` from `vantio-agent-sdk` writes the same local `~/.vantio/runs` metadata | Gate HTTP mediation of Cursor SaaS; PE path DENY (PE is stacked separately) |

This plugin reads local `~/.vantio/runs` from Node `vantio run` (`@vantio/cli` wraps fetch and Node http/https) or from Python `shield()` (`vantio-agent-sdk` wraps urllib, and requests/httpx when those libraries are already installed). It does not enforce policy and it does not see curl, raw sockets, or browser paths.

Optics is observe-only metadata. When you need Vantio to stop a host, redact a
payload, or enforce a spend ceiling on the wrapped path, upgrade to Vantio Gate.
When you need Control on enrolled Linux that still holds if an agent tries to go
around application rules, upgrade to Phantom Engine.
