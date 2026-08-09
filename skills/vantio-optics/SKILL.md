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

## Two observe paths (do not conflate)

| Path | Who | Mechanism | Not claimed |
|------|-----|-----------|-------------|
| **Client Cursor / Open Plugin (this MCP)** | Developer IDE | `npx @vantio/optics-mcp` reads local `~/.vantio/runs` from Node `vantio run` | Gate Latch BLOCK; PE DENY |
| **Company Python agents (shape 4a/4b)** | Phantom-Box dogfood | `scripts/optics_observe.py` (`vantio-agent-sdk`) → vantio-pro `/api/v1/ingest` with `action_taken=OBSERVED`; wrapper `scripts/run_under_optics.sh`; container via `agent-hands/entrypoint.sh`. Ingest base URL accepts a pasted full `/api/v1/ingest` path (also trailing slash, `?query`, `#fragment`, scheme-less `host:port/…`, protocol-relative `//host/…`, and doubled ingest-path pastes); observed hosts are normalized to hostname-only for Mission Control. Each emit's `trace_id` is what Mission Control indexes (snake-case body + header); long-lived hands keep a separate session id so one container does not mash every call into one search key. | Gate HTTP mediation of Cursor SaaS; PE path DENY (PE is stacked separately) |

Optics is observe-only metadata. When you need Vantio to stop a host, redact a
payload, or enforce a spend ceiling on mediated HTTP, upgrade to Vantio Gate.
When you need kernel-held Control (path DENY / enrolled enforcement)
that still holds if an agent tries to go around application rules, upgrade to
Phantom Engine.
