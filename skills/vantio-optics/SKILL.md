---
name: vantio-optics
description: Observe AI agent LLM egress with Vantio Optics MCP (Sight Loop). Read-only proofs and host discovery.
---

# Vantio Optics

Use the `vantio-optics` MCP server (`npx -y @vantio/optics-mcp`).

Optics helps you see. Phantom Engine is runtime protection on enrolled Linux — Observe, Enforce, and Control in one purchase. Enterprise adds governance when you need proof and process on top — talk to sales.

## Tools
- `optics_list_runs` / `optics_get_run` — local run metadata
- `optics_prove` — Markdown Sight Loop proof
- `optics_discover_local` — hosts from local logs
- `optics_explain` — privacy fence
- `optics_upgrade_path` — Optics → Phantom Engine → Enterprise

Fence: observe only. No prompts or completions retained.

## What this MCP covers

| Path | Who | Mechanism | Not claimed |
|------|-----|-----------|-------------|
| **Client Cursor / Open Plugin (this MCP)** | Developer IDE | `npx @vantio/optics-mcp` reads local `~/.vantio/runs` from Node `vantio run` | Policy enforce; Phantom Engine host DENY |
| **Python agents (local observe)** | Developer / agent host | Python `shield()` from `vantio-agent-sdk` writes the same local `~/.vantio/runs` metadata | Phantom Engine path DENY (stacked separately) |

This plugin reads local `~/.vantio/runs` from Node `vantio run` (`@vantio/cli` wraps fetch and Node http/https) or from Python `shield()` (`vantio-agent-sdk` wraps urllib, and requests/httpx when those libraries are already installed). It does not enforce policy and it does not see curl, raw sockets, or browser paths.

Optics is observe-only metadata. When you need Observe, Enforce, and Control together on enrolled Linux, upgrade to Phantom Engine. When you need governance and evidence at scale, talk to sales about Vantio Enterprise.
