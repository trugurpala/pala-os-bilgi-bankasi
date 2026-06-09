# Hafizalar v0.2 Dogfood Proof Changed Files Manifest

Date: 2026-06-09

Source repo: https://github.com/trugurpala/hafizalar

Source commit: 331b149fd3fdc04686e179bd98cbb3d7926f8abe

Phase: v0.2 dogfood proof

Status: PASS

## Included Files

| File | Status | Phase Note |
| --- | --- | --- |
| `.github/workflows/test.yml` | Modified | Adds CI dogfood step after tests. |
| `CHANGELOG.md` | New | Documents `0.2.0 Dogfood Proof`. |
| `README.md` | Modified | Adds v0.2 milestone, dogfood doc link, and dogfood command. |
| `docs/DOGFOOD.md` | New | Documents dogfood scenario, commands, and limits. |
| `docs/GITHUB-REPO-CHECKLIST.md` | Modified | Adds dogfood status row. |
| `docs/MAINTENANCE.md` | Modified | Adds dogfood to weekly/release checks and updates current version. |
| `package.json` | Modified | Bumps version to `0.2.0` and adds `dogfood` script. |
| `scripts/dogfood-hafizalar.mjs` | New | Runs isolated temporary-project dogfood proof. |
| `test/hafizalar.test.mjs` | Modified | Adds dogfood files and package metadata assertions. |

## New Files

- `CHANGELOG.md`
- `docs/DOGFOOD.md`
- `scripts/dogfood-hafizalar.mjs`

## Modified Files

- `.github/workflows/test.yml`
- `README.md`
- `docs/GITHUB-REPO-CHECKLIST.md`
- `docs/MAINTENANCE.md`
- `package.json`
- `test/hafizalar.test.mjs`

## Excluded Dirty Files

None.

## Tracked Diff Stat

```text
.github/workflows/test.yml    |   3 +++
CHANGELOG.md                  |  13 ++++++
README.md                     |  11 +++++
docs/DOGFOOD.md               |  42 ++++++++++++++++++
docs/GITHUB-REPO-CHECKLIST.md |   1 +
docs/MAINTENANCE.md           |  18 ++++----
package.json                  |   3 +-
scripts/dogfood-hafizalar.mjs | 192 +++++++++++++++++++++++++++++++++++++++++
test/hafizalar.test.mjs       |   6 +++
9 files changed, 289 insertions(+), 9 deletions(-)
```

## Evidence

- Local tests: `npm.cmd test` PASS, 13/13.
- Local dogfood: `npm.cmd run dogfood -- --json` PASS.
- Package dry-run: `npm.cmd pack --dry-run` PASS.
- Final GitHub quick install: PASS.
- CI: https://github.com/trugurpala/hafizalar/actions/runs/27202581251 PASS.
