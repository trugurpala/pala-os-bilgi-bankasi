# Hafizalar Community Project Changed Files Manifest

Date: 2026-06-09

Source repo: `trugurpala/hafizalar`

Local path: `C:\Users\Pala-Home-1\Desktop\Codex\hafizalar`

Phase: community GitHub project creation

## Included Source Files

| File | Status | Purpose |
| --- | --- | --- |
| `.github/workflows/test.yml` | new | Matrix CI for Ubuntu/Windows and Node 22/24. |
| `.gitignore` | new | Excludes local runtime/generated files and secrets. |
| `CONTRIBUTING.md` | new | Contribution rules for preserving contract safety. |
| `HAFIZALAR-CODEX-SHORT.md` | new | Compact Codex prompt for fast use. |
| `HAFIZALAR-CODEX.md` | new | Full reusable Codex product-builder contract. |
| `LICENSE` | new | MIT license. |
| `README.md` | new | Public project landing and usage guide with CI badge. |
| `package.json` | new | Test scripts and metadata. |
| `scripts/test-hafizalar.ps1` | new | Windows-friendly smoke wrapper. |
| `templates/GOLDEN-PATH.md` | new | Local runbook template. |
| `templates/HAFIZALAR.md` | new | Project operating contract template. |
| `templates/REVIEW.md` | new | Result/report template. |
| `templates/TASKS.md` | new | Task list template. |
| `test/hafizalar.test.mjs` | new | Contract, template, ASCII, secret-pattern, and sandbox tests. |

## Included Knowledge-Bank Files

| File | Status |
| --- | --- |
| `reports/hafizalar/2026-06-09-hafizalar-community-project-implementation-report.md` | new |
| `reports/hafizalar/2026-06-09-hafizalar-community-project-changed-files-manifest.md` | new |
| `reports/hafizalar/2026-06-09-hafizalar-community-project-repo-change-review.md` | new |
| `reports/hafizalar/2026-06-09-hafizalar-community-project-raw-patch-diff.patch` | new |

## Excluded Files

No unrelated local files were included in the `hafizalar` source repo.

Known unrelated Pala OS work not touched:

- `../pala-os-v6/docs/v6-vibe-coder-agent-host-plan.md`
- `../pala-os-v4/.pala/rules/evidence-battalions.json`
- `../pala-os-v4/.pala/rules/world-standards.json`

## Diff Stat

```text
.github/workflows/test.yml |  29 +++
.gitignore                 |  10 +
CONTRIBUTING.md            |  26 ++
HAFIZALAR-CODEX-SHORT.md   |  63 +++++
HAFIZALAR-CODEX.md         | 637 +++++++++++++++++++++++++++++++++++++++++++++
LICENSE                    |  21 ++
README.md                  |  91 +++++++
package.json               |  15 ++
scripts/test-hafizalar.ps1 |  17 ++
templates/GOLDEN-PATH.md   |  27 ++
templates/HAFIZALAR.md     |  26 ++
templates/REVIEW.md        |  24 ++
templates/TASKS.md         |  13 +
test/hafizalar.test.mjs    | 103 ++++++++
14 files changed, 1102 insertions(+)
```

## Verification Summary

| Check | Result |
| --- | --- |
| `npm.cmd test` | PASS, 7/7 |
| `scripts/test-hafizalar.ps1` | PASS, 7/7 |
| GitHub Actions matrix | PASS, 4/4 jobs |
| Public repo exists | PASS |
| Latest `main` is pushed | PASS |

## Release Posture

COMMUNITY_REPO_PUBLISHED_NOT_PACKAGE_RELEASED
