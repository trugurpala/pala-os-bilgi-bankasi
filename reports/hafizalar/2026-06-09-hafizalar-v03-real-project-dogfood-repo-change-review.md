# Hafizalar v0.3 Real Project Dogfood Repo Change Review

Date: 2026-06-09

Source repo: `trugurpala/hafizalar`

Source commit: `60deee3dfe325ab40f86eff105917a637ef69737`

Review decision: `PASS`

## Scope Reviewed

This review covers the Hafizalar v0.3 mutation package that adds real-project dogfood validation and publishes it to `main`.

Included mutation package:

- `CHANGELOG.md`
- `README.md`
- `docs/GITHUB-REPO-CHECKLIST.md`
- `docs/MAINTENANCE.md`
- `docs/REAL-PROJECT-DOGFOOD.md`
- `package.json`
- `scripts/dogfood-real-projects.mjs`
- `test/hafizalar.test.mjs`

Excluded from mutation package:

- Pre-existing dirty local state in `pala-os-v4`.
- Pre-existing untracked local file in `pala-os-v6`.
- Transient accidental files in `pala-os-v10`, removed before final verification.

## File-By-File Notes

`scripts/dogfood-real-projects.mjs`

- Adds a temp workspace based real-project validator.
- Clones local git repos with `git clone --quiet --no-hardlinks`.
- Copies non-git local targets with build/cache folders excluded.
- Clones GitHub repos with `gh repo clone ... -- --depth 1`.
- Installs Hafizalar with `--surface both --force` only inside temp copies/clones.
- Verifies required installed files and `INSTALL-REPORT.json`.
- Runs `npm test` for targets that are explicitly testable.
- Refuses to delete non-temp paths during cleanup.

`docs/REAL-PROJECT-DOGFOOD.md`

- Documents run commands, `--codex-root`, `--skip-github`, and `--keep`.
- Lists local and GitHub targets.
- Explains why `pala-os-v4` is excluded.
- States that active project folders are not modified.

`package.json`

- Bumps package version from `0.2.0` to `0.3.0`.
- Adds `dogfood:real`.

`test/hafizalar.test.mjs`

- Adds required file coverage for the new doc and script.
- Asserts version `0.3.0`.
- Asserts the new package script.

`README.md`, `CHANGELOG.md`, `docs/GITHUB-REPO-CHECKLIST.md`, `docs/MAINTENANCE.md`

- Update public documentation, release routine, and maintenance checklist for the v0.3 dogfood gate.

## Verification Results

Local verification:

| Command | Result |
| --- | --- |
| `node --check scripts\dogfood-real-projects.mjs` | PASS |
| `npm.cmd test` | PASS, 13/13 |
| `npm.cmd run dogfood -- --json` | PASS |
| `npm.cmd run dogfood:real -- --json` | PASS |
| `npm.cmd pack --dry-run` | PASS |
| `git diff --check` | PASS |
| secret-shaped text scan | PASS |

Real project dogfood:

| Target | Install | Test |
| --- | --- | --- |
| local `pala-os-v3` | PASS | PASS, 9/9 |
| local `pala-os-v5` | PASS | PASS, 1/1 |
| local `pala-os-v6` | PASS | PASS, 39/39 |
| local `pala-os-v10` | PASS | SKIPPED, no package test |
| GitHub `trugurpala/pala-os-v3` | PASS | PASS, 9/9 |
| GitHub `trugurpala/pala-os-v5` | PASS | SKIPPED, install-only default branch |
| GitHub `trugurpala/pala-os-v6` | PASS | PASS, 12/12 |
| GitHub `trugurpala/pinescriptv6` | PASS | SKIPPED, no package test |

CI verification:

- GitHub Actions run: https://github.com/trugurpala/hafizalar/actions/runs/27203591594
- Conclusion: `success`
- Ubuntu Node 22: PASS
- Ubuntu Node 24: PASS
- Windows 2025 Node 22: PASS
- Windows 2025 Node 24: PASS

## Risks And Boundaries

- `dogfood:real` is local/manual because CI does not have the owner's local Codex folder or private GitHub access.
- `pala-os-v4` remains untested in this gate until its dirty working tree is resolved.
- No release tag or npm publish was created.
- No production deploy was performed.
- No force push was performed.

## Rollback Note

Use a normal revert if this change must be backed out:

```powershell
git revert 60deee3dfe325ab40f86eff105917a637ef69737
git push origin main
```

## Raw Patch

Raw patch/diff artifact:

- `2026-06-09-hafizalar-v03-real-project-dogfood-raw-patch-diff.patch`
