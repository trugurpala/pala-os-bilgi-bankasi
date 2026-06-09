# Hafizalar v0.2 Dogfood Proof Repo Change Review

Date: 2026-06-09

Source repo: https://github.com/trugurpala/hafizalar

Source commit: 331b149fd3fdc04686e179bd98cbb3d7926f8abe

Phase: v0.2 dogfood proof

Status: PASS

## Review Result

No blocking issues found.

## File-by-File Notes

`scripts/dogfood-hafizalar.mjs`

- Creates a temporary project under the OS temp directory.
- Runs installer dry-run and real install.
- Verifies Codex contract, ChatGPT contract, agentic pattern map, install report, and project setup template.
- Simulates a small product request.
- Implements a deterministic greeting module in the temp project.
- Runs `node --test test/greeting.test.mjs`.
- Writes and verifies a dogfood `REVIEW.md`.
- Removes the temp project by default.
- Supports `--json` and `--keep`.

`docs/DOGFOOD.md`

- Documents dogfood purpose, commands, checks, and limits.
- Clarifies that the scenario is synthetic and does not prove every stack.

`.github/workflows/test.yml`

- Runs dogfood after `npm test`.
- CI now proves both contract tests and end-to-end temporary-project loop.

`package.json`

- Bumps version to `0.2.0`.
- Adds `dogfood` script.
- No npm publish was performed.

`CHANGELOG.md`

- Adds `0.2.0 Dogfood Proof`.
- Keeps `0.1.0 Community Starter` history.

`README.md`, `docs/GITHUB-REPO-CHECKLIST.md`, `docs/MAINTENANCE.md`

- Add dogfood visibility and maintenance expectations.

`test/hafizalar.test.mjs`

- Adds file and metadata assertions for dogfood.

## Dogfood Failure Found And Fixed

During local dogfood, the initial implementation attempted to spawn `npm.cmd` from Node and hit `spawnSync npm.cmd EINVAL` on Windows.

Fix:

- target project verification now runs through `node --test test/greeting.test.mjs`;
- this is more deterministic and cross-platform.

## Risks Left

- Dogfood is synthetic; it verifies the operating loop, not a full production app.
- No npm package publish or GitHub release tag exists yet.
- The dogfood module is intentionally small; future versions should add stack-specific dogfood profiles.

## Evidence Commands

```text
npm.cmd test
npm.cmd run dogfood -- --json
npm.cmd pack --dry-run
git diff --check
npm.cmd exec --yes --package github:trugurpala/hafizalar#331b149fd3fdc04686e179bd98cbb3d7926f8abe hafizalar-install -- --target <temp> --surface both
gh run watch 27202581251 --repo trugurpala/hafizalar --exit-status
```

## CI Result

GitHub Actions run:

https://github.com/trugurpala/hafizalar/actions/runs/27202581251

Result: PASS.

Matrix:

- Ubuntu latest, Node 22
- Ubuntu latest, Node 24
- Windows 2025, Node 22
- Windows 2025, Node 24

## Rollback

```powershell
git revert 331b149fd3fdc04686e179bd98cbb3d7926f8abe
git push origin main
```

Knowledge-bank publication is not release approval.
