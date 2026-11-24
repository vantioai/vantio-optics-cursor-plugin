# VAN-93 and VAN-347: plugin copy

Branch `engineering/van-93-van-347-cursor-plugin-copy`, from `main` at `7ef8cf9`. Docs only. No publish, no marketplace change, no workflow dispatch.

Both tickets edit `README.md`, so they share one PR.

## Finding

The two sweeps (VAN-93 for present-tense enforcement claims, VAN-347 for the retired product name) did not list this repository.

- `README.md` line 5 and `skills/vantio-optics/SKILL.md` line 10 said "Phantom Engine is runtime protection on enrolled Linux", in the present tense. They also said "talk to sales", the retired call to action (open-core #369).
- `README.md` lines 62–73 had a section on the retired package `@vantio/gate-mcp`, with a `vantio-gate` MCP config.
- `rules/optics-observe.mdc` line 14 said "talk to sales".

## What changed

- The two "Phantom Engine is runtime protection" sentences now use the wording from vantio-optics #19 (VAN-93): "the Vantio product built for runtime protection on enrolled Linux. Its live enforcement is not yet proven." "talk to sales" became "Contact Vantio".
- The retired-package section is removed from `README.md`.
- `rules/optics-observe.mdc`: "talk to sales" became "contact Vantio".

## Commands

| Command | rc | Result |
| --- | --- | --- |
| `python3 scripts/ci/test_founder_approval_guard.py -v` | 0 | OK |
| `python3 -m detect_secrets scan` | 0 | 0 results |
| `git grep -niE "talk to sales\|is runtime protection\|\bgate\b"` outside `scripts/ci` and `.github` | 1 | no match |

## Gaps

- `README.md` is a founder-guard path. The guard job needs the `founder-approved` label, applied by an admin after the latest push.
- Public copy: needs council review, Kate's sign-off on the wording, and Zach's go.
- CI did not run: the org billing lock (VAN-129).
- Owner question, not changed: `mcp.json` and `.mcp.json` start `npx -y @vantio/optics-mcp` with no version, so each start can fetch a newer package. Keep it unpinned, or pin to `@vantio/optics-mcp@0.1.2`?
