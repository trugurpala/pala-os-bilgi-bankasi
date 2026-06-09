# Hafizalar v0.3.1 Full Real Project Sweep Implementation Report

Date: 2026-06-09

Source repo: `trugurpala/hafizalar`

Source commit: `fa43a0f7497cc086c2ce7d2df536e0cb5a83d24c`

GitHub commit: https://github.com/trugurpala/hafizalar/commit/fa43a0f7497cc086c2ce7d2df536e0cb5a83d24c

Phase: `PASS`

Status: implemented, pushed to `main`, CI green.

## Summary

Hafizalar v0.3.1 closes the remaining real-project dogfood gap.

The local sweep now includes the previously excluded dirty `pala-os-v4` folder as a dirty-inclusive temp copy. It also includes additional local Codex repos as install-only targets. The GitHub sweep now supports `--github-all --github-owner <owner>` so every non-archived owner repo can be cloned and install-verified without hardcoding every private project name in the public repo.

## Changed Files

- `CHANGELOG.md`
- `README.md`
- `docs/GITHUB-REPO-CHECKLIST.md`
- `docs/MAINTENANCE.md`
- `docs/REAL-PROJECT-DOGFOOD.md`
- `package.json`
- `scripts/dogfood-real-projects.mjs`
- `test/hafizalar.test.mjs`

New files:

- None in source repo.

## What Changed

- Bumped package version to `0.3.1`.
- Added local install-only coverage for `konusmalar`, `pala-os`, and `pala-os-bilgi-bankasi`.
- Added dirty-inclusive install-only temp-copy coverage for local `pala-os-v4`.
- Added curated GitHub coverage for `trugurpala/pala-os-v4`.
- Added `--github-all --github-owner <owner>` for dynamic install-only coverage across all non-archived owner repos.
- Updated README, maintenance checklist, GitHub checklist, dogfood docs, changelog, and tests.

## Evidence

Local commands:

- `node --check scripts\dogfood-real-projects.mjs` -> PASS
- `npm.cmd test` -> PASS, 13/13 tests
- `npm.cmd run dogfood -- --json` -> PASS
- `npm.cmd run dogfood:real -- --json` -> PASS
- `npm.cmd run dogfood:real -- --github-all --github-owner trugurpala --json` -> PASS
- `npm.cmd pack --dry-run` -> PASS, package `hafizalar-0.3.1.tgz`, 34 files listed
- `git diff --check` -> PASS
- secret-shaped text scan -> PASS, no matches
- GitHub fast install via `npm.cmd exec --yes --package github:trugurpala/hafizalar#main hafizalar-install -- --target <temp> --surface both` -> PASS

Default real-project dogfood:

- Local targets: 8/8 PASS.
- Curated GitHub targets: 5/5 PASS.
- Excluded local targets: none.
- Temp workspace cleanup: PASS.

Full GitHub owner sweep:

- Local targets: 8/8 PASS.
- Curated GitHub targets: 5/5 PASS.
- Dynamic owner inventory: 8 additional non-archived repos install-verified.
- Temp workspace cleanup: PASS.

CI:

- Workflow: `Hafizalar Test`
- Run: https://github.com/trugurpala/hafizalar/actions/runs/27204324905
- Conclusion: `success`
- Jobs passed:
  - `test (ubuntu-latest, 22)`
  - `test (ubuntu-latest, 24)`
  - `test (windows-2025, 22)`
  - `test (windows-2025, 24)`

## Important Boundary

`pala-os-v4` is install-only in this Hafizalar gate. A direct full test attempt in a temp local copy showed project-specific blockers unrelated to Hafizalar installation:

- the copied shape has no `.git`, while its release precheck expects git metadata,
- legacy tests require project dependencies such as `vitest` and `msw`.

The Hafizalar installer still passed for that target.

## Release Posture

- No npm publish.
- No release tag.
- No production deploy.
- No force push.
- Direct normal push to `main`: `60deee3..fa43a0f`.

## Rollback

Rollback path:

```powershell
git revert fa43a0f7497cc086c2ce7d2df536e0cb5a83d24c
git push origin main
```

## Remaining Risk

- `dogfood:real` and `--github-all` remain local/manual because GitHub Actions does not have the owner's local Codex folder or private GitHub access.
- Dynamic owner inventory targets are install-only by design; unknown private product tests are not run automatically.
