# Hafizalar v0.3.1 Full Real Project Sweep Changed Files Manifest

Date: 2026-06-09

Source repo: `trugurpala/hafizalar`

Source commit: `fa43a0f7497cc086c2ce7d2df536e0cb5a83d24c`

Phase: `PASS`

## Mutation Package

Included files:

| Status | File | Purpose |
| --- | --- | --- |
| M | `CHANGELOG.md` | Added v0.3.1 release note. |
| M | `README.md` | Updated milestone and added full GitHub owner inventory command. |
| M | `docs/GITHUB-REPO-CHECKLIST.md` | Added full owner sweep gate. |
| M | `docs/MAINTENANCE.md` | Added full owner sweep to weekly and release routines; bumped current version. |
| M | `docs/REAL-PROJECT-DOGFOOD.md` | Added expanded local targets, `pala-os-v4`, and `--github-all` documentation. |
| M | `package.json` | Bumped to `0.3.1`. |
| M | `scripts/dogfood-real-projects.mjs` | Added expanded local coverage, `pala-os-v4`, and dynamic GitHub inventory support. |
| M | `test/hafizalar.test.mjs` | Added `--github-all` doc assertion and bumped expected version. |

New source files:

- None.

Tracked diff stat:

```text
8 files changed, 118 insertions(+), 18 deletions(-)
```

## Excluded Files And Dirty State

Excluded local targets:

- None.

Pre-existing dirty source state observed but not mutated:

- `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v4`
  - `M .pala/rules/evidence-battalions.json`
  - `M .pala/rules/world-standards.json`
- `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`
  - `?? docs/v6-vibe-coder-agent-host-plan.md`

The dogfood runner used temp clones/copies and did not clean, reset, normalize, or modify these active source folders.

## Evidence Commands

- `git show --stat --oneline --decorate fa43a0f`
- `git show --name-status --format=fuller --no-renames fa43a0f`
- `node --check scripts\dogfood-real-projects.mjs`
- `npm.cmd test`
- `npm.cmd run dogfood -- --json`
- `npm.cmd run dogfood:real -- --json`
- `npm.cmd run dogfood:real -- --github-all --github-owner trugurpala --json`
- `npm.cmd pack --dry-run`
- `git diff --check`
- secret-shaped text scan
- GitHub fast install via `npm.cmd exec --yes --package github:trugurpala/hafizalar#main hafizalar-install -- --target <temp> --surface both`
- `gh run watch 27204324905 --repo trugurpala/hafizalar --exit-status`

## Artifact Set

- Implementation report: `2026-06-09-hafizalar-v031-full-real-project-sweep-implementation-report.md`
- Changed files manifest: `2026-06-09-hafizalar-v031-full-real-project-sweep-changed-files-manifest.md`
- Repo change review: `2026-06-09-hafizalar-v031-full-real-project-sweep-repo-change-review.md`
- Raw patch/diff: `2026-06-09-hafizalar-v031-full-real-project-sweep-raw-patch-diff.patch`
