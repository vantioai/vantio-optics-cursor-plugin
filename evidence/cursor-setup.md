# Cursor cloud agent setup — verification

**Date (UTC):** 2026-11-05  
**Agent run:** https://cursor.com/agents/bc-516605b8-9b2d-53bf-b28b-91d377757918  
**Base branch at start:** `main` @ `0c97c213acb07169b56e126597080af0e09244e5`  
**Branch:** `cursor/cursor-agent-setup-7918`

## What changed (this task)

- Added `AGENTS.md` (repo map, verified commands, definition of done).
- Added `.cursor/rules/` (`workflow`, `tests`, `evidence`, `safety`, `claims`).
- Added this evidence file.

No changes to protected install pins, CI workflows, or product MCP code.

## Commands run

| Command | Exit code | Notes |
|---------|-----------|--------|
| `python3 scripts/ci/test_founder_approval_guard.py -v` | 0 | 10 tests, all OK |
| `python3 -m detect_secrets scan` | 0 | `"results": {}` (after `pip install detect-secrets`) |

## Typecheck / lint

Not configured in this repository (no `package.json`, no CI lint/typecheck jobs). Documented as N/A in `AGENTS.md`.

## Install

No repo-local install step beyond clone; verified by inspection (no `package.json`).

## Commit SHAs

- **Pre-change `main`:** `0c97c213acb07169b56e126597080af0e09244e5`
- **Post-change branch tip:** use GitHub PR **head SHA** (local `git rev-parse HEAD` at push time; see agent report below)

## Gap list (human-only)

- GitHub Actions CI green on the draft PR (founder guard + unit tests on GitHub runners).
- Founder approval guard behavior on a real PR that touches protected paths (label workflow).
- Cursor Marketplace / cursor.directory listing correctness and logo URLs.
- End-to-end MCP observe behavior with `@vantio/optics-mcp` and local `~/.vantio/runs` on a developer machine.
- Whether `detect-secrets` should become a required CI check (policy decision).
