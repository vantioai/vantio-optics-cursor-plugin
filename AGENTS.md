# Cloud agents — vantio-optics-cursor-plugin

Public Cursor / Open Plugins bundle for **Vantio Optics** (read-only MCP). This repository ships manifests, rules, skills, and CI guards — not the `@vantio/optics-mcp` npm package itself.

## Repo map

| Path | Purpose |
|------|---------|
| `.cursor-plugin/plugin.json`, `.plugin/plugin.json` | Plugin metadata for Cursor Marketplace / Open Plugins |
| `mcp.json`, `.mcp.json` | MCP server install pin (`npx -y @vantio/optics-mcp`) — **founder-guard protected** |
| `README.md` | Install and marketplace fields — **founder-guard protected** |
| `rules/optics-observe.mdc` | Optional IDE rule: prefer Optics MCP; observe-only |
| `skills/vantio-optics/SKILL.md` | Agent skill for Optics tool usage |
| `assets/logo.svg`, `assets/logo.png` | Marketplace logos |
| `.github/workflows/ci.yml` | Runs Python guard unit tests on PR/push to `main` |
| `.github/workflows/founder-approval-guard.yml` | Blocks protected-path PRs without admin `founder-approved` label |
| `.github/founder-approval-paths.txt` | List of paths requiring founder approval |
| `scripts/ci/founder_approval_guard.py` | Guard implementation (runs on base branch in CI) |
| `scripts/ci/test_founder_approval_guard.py` | Unit tests for the guard |
| `.cursor/rules/*.mdc` | Cloud-agent policy (workflow, tests, evidence, safety, claims) |
| `evidence/*.md` | Verification notes from agent runs (commands, exit codes, SHAs) |

## Commands (verified in a clean checkout)

Run from repository root.

### Install

There is **no** `package.json` and no repo-local `npm install`. Clone the repository; no other install step is required to edit docs or CI fixtures.

```bash
git clone https://github.com/vantioai/vantio-optics-cursor-plugin.git
cd vantio-optics-cursor-plugin
```

Optional (not required for this repo): Python 3 for tests; `pip install detect-secrets` for local secret scanning (not run in GitHub Actions today).

### Test

```bash
python3 scripts/ci/test_founder_approval_guard.py -v
```

Expected: `Ran 10 tests` and `OK` (exit code `0`).

### Typecheck

**Not defined.** No TypeScript/JavaScript product sources and no typecheck script in CI.

### Lint

**Not defined.** No linter configured in CI or package scripts.

### Secret scan (local)

```bash
python3 -m pip install detect-secrets
python3 -m detect_secrets scan
```

Expected: JSON with `"results": {}` (exit code `0`). This scan is agent/local verification only; CI does not run it yet.

## Scope for cloud agents

- **Docs and config only** in this repo unless owners explicitly expand scope: manifests, README, rules, skills, `AGENTS.md`, `evidence/`, and `.cursor/rules/`.
- **One task per agent**, small diffs, **draft PR only** — never merge, never push to `main`, no tags, publishes, deploys, or dispatches.
- Touching **founder-guard protected paths** (see `.github/founder-approval-paths.txt`) requires a repository admin to apply the `founder-approved` label **after** the latest push; plan accordingly or avoid those paths.

## Observe-only product boundary

The Optics MCP configured here **reads local run metadata** (for example under `~/.vantio/runs`). It does **not** enforce policy, block egress, or operate Phantom Engine. Do not document or imply enforcement from this plugin.

## Definition of done

1. Change matches the assigned scope; diff stays small.
2. Existing tests pass: `python3 scripts/ci/test_founder_approval_guard.py -v` (exit `0`).
3. If behavior under `scripts/ci/` changes, unit tests are updated and include negative cases.
4. Local secret scan run when adding or editing tracked content: `python3 -m detect_secrets scan` with empty `results`.
5. `evidence/<topic>.md` updated with commands, exit codes, commit SHAs, and a **gap list** of what only a human can verify (marketplace publish, founder label, production MCP behavior).
6. **Draft PR** opened (never marked ready, never merged by the agent); PR text contains no secrets, tokens, or customer data.
7. Claims in docs match what tests or logs from **this run** prove; open **policy questions** for owners when unsure.

## Policy questions (for repository owners)

- Should `detect-secrets` (or another scanner) become a required CI job?
- Should cloud-agent rules in `.cursor/rules/` be duplicated or symlinked from a org-wide template repo?
- When may agents touch founder-guard protected install pins without a human founder review?
