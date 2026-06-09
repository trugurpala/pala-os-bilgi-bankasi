# Hafizalar v0.3 Real Project Dogfood Changed Files Manifest

Date: 2026-06-09

Source repo: `trugurpala/hafizalar`

Source commit: `60deee3dfe325ab40f86eff105917a637ef69737`

Phase: `PASS`

## Mutation Package

Included files:

| Status | File | Purpose |
| --- | --- | --- |
| M | `CHANGELOG.md` | Added v0.3 release note. |
| M | `README.md` | Added real-project dogfood surface, docs link, command, and status. |
| M | `docs/GITHUB-REPO-CHECKLIST.md` | Added real-project dogfood release/checklist gate. |
| M | `docs/MAINTENANCE.md` | Added real-project dogfood to weekly and release routines; bumped current version. |
| A | `docs/REAL-PROJECT-DOGFOOD.md` | New user-facing guide for local/GitHub temp dogfood validation. |
| M | `package.json` | Bumped to `0.3.0`; added `dogfood:real` script. |
| A | `scripts/dogfood-real-projects.mjs` | New temp-copy/temp-clone real project dogfood runner. |
| M | `test/hafizalar.test.mjs` | Added required file coverage and package/script assertions. |

New files:

- `docs/REAL-PROJECT-DOGFOOD.md`
- `scripts/dogfood-real-projects.mjs`

Tracked diff stat:

```text
8 files changed, 556 insertions(+), 11 deletions(-)
```

## Excluded Files And Dirty State

Excluded local project:

- `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v4`
  - Reason: pre-existing dirty files during audit.
  - Dirty files observed:
    - `M .pala/rules/evidence-battalions.json`
    - `M .pala/rules/world-standards.json`

Excluded untracked local file:

- `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6\docs\v6-vibe-coder-agent-host-plan.md`
  - Reason: pre-existing untracked file; local temp git clone used committed content only.

Transient operator correction:

- `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v10\scripts\dogfood-real-projects.mjs`
- `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v10\docs\REAL-PROJECT-DOGFOOD.md`
- Reason: accidentally created by `apply_patch` cwd mismatch, then removed before verification.
- Final state: both paths absent from `pala-os-v10`.

## Evidence Commands

- `git show --stat --oneline --decorate 60deee3`
- `git show --name-status --format=fuller --no-renames 60deee3`
- `npm.cmd test`
- `npm.cmd run dogfood -- --json`
- `npm.cmd run dogfood:real -- --json`
- `npm.cmd pack --dry-run`
- `git diff --check`
- secret-shaped text scan
- `gh run watch 27203591594 --repo trugurpala/hafizalar --exit-status`

## Artifact Set

- Implementation report: `2026-06-09-hafizalar-v03-real-project-dogfood-implementation-report.md`
- Changed files manifest: `2026-06-09-hafizalar-v03-real-project-dogfood-changed-files-manifest.md`
- Repo change review: `2026-06-09-hafizalar-v03-real-project-dogfood-repo-change-review.md`
- Raw patch/diff: `2026-06-09-hafizalar-v03-real-project-dogfood-raw-patch-diff.patch`
