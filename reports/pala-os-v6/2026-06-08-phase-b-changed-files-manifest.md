# Phase B Changed Files Manifest

Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`

Date: 2026-06-08

Phase: B - GitHub Governance Hardening

Release posture: `RELEASE_BLOCKED`

## Included Phase B Files

| Path | Type | Phase B Change |
|---|---|---|
| `.github/workflows/pala.yml` | GitHub Actions workflow | Added stable governance jobs: `source-court-audit`, `legacy-boundary`, `test`, `court`; kept `nightly-cron` schedule-only. |
| `.github/CODEOWNERS` | GitHub review policy | Expanded governance-critical path ownership. |
| `.github/PULL_REQUEST_TEMPLATE.md` | PR governance template | Added four-artefact review package, evidence commands, release posture, rollback. |
| `scripts/pala_github_gate_audit.ps1` | GitHub audit script | Added branch protection, ruleset, required checks, review gate, CODEOWNERS/template/workflow local policy readback. |
| `docs/github-policy-pack.md` | Governance documentation | Rewrote policy to match real enforcement and solo-owner deadlock handling. |
| `test/pala-v6.test.js` | Regression tests | Added Phase B tests for CODEOWNERS, PR template, workflow jobs, github audit gate, and release blocked court state. |

## New Source Repo Files

None.

## Remote GitHub Mutation

| Surface | Change | Status |
|---|---|---|
| `main` branch protection | Enabled | PASS |
| Required status check | `test` | PASS |
| Required PR review | 1 approval | PASS |
| CODEOWNERS review | Enabled | PASS |
| Dismiss stale reviews | Enabled | PASS |
| Enforce admins | Enabled | PASS |
| Linear history | Enabled | PASS |
| Conversation resolution | Enabled | PASS |
| Force pushes | Disabled | PASS |
| Branch deletion | Disabled | PASS |
| Rulesets | Not used | NOT_USED_WITH_REASON |

## Out-of-Scope Dirty Files Still Present

These files were already dirty from earlier local work and are not Phase B-specific:

- `README.md`
- `docs/inheritance-backlog.json`
- `docs/v6-dunya-standardi-karargah-tr.md`
- `src/bootstrap.js`
- `src/cli.js`
- `src/config.js`
- `src/dashboard.js`
- `src/policy.js`
- `src/server.js`
- `.dockerignore`
- `docs/source-stamp-contract.md`
- `docs/v6-vibe-coder-agent-host-plan.md`
- `src/core-foundation.js`
- `src/environment-limits.js`
- `src/operator-actions.js`
- `src/source-court.js`

Note: `test/pala-v6.test.js` already contained Phase A/C local test changes. The raw diff shows the full dirty-file delta from HEAD; this manifest identifies the Phase B-specific intent.

## Git Status Snapshot

```text
 M .github/CODEOWNERS
 M .github/PULL_REQUEST_TEMPLATE.md
 M .github/workflows/pala.yml
 M README.md
 M docs/github-policy-pack.md
 M docs/inheritance-backlog.json
 M docs/v6-dunya-standardi-karargah-tr.md
 M scripts/pala_github_gate_audit.ps1
 M src/bootstrap.js
 M src/cli.js
 M src/config.js
 M src/dashboard.js
 M src/policy.js
 M src/server.js
 M test/pala-v6.test.js
?? .dockerignore
?? docs/source-stamp-contract.md
?? docs/v6-vibe-coder-agent-host-plan.md
?? src/core-foundation.js
?? src/environment-limits.js
?? src/operator-actions.js
?? src/source-court.js
```

## Diff Stat

Command:

```powershell
git diff --stat -- .github/workflows/pala.yml .github/CODEOWNERS .github/PULL_REQUEST_TEMPLATE.md scripts/pala_github_gate_audit.ps1 docs/github-policy-pack.md test/pala-v6.test.js
```

Observed output:

```text
.github/CODEOWNERS                 |  15 ++
.github/PULL_REQUEST_TEMPLATE.md   |  14 ++
.github/workflows/pala.yml         |  83 ++++++++
docs/github-policy-pack.md         | 146 ++++++++++---
scripts/pala_github_gate_audit.ps1 | 272 +++++++++++++++++++++---
test/pala-v6.test.js               | 423 ++++++++++++++++++++++++++++++++++++-
6 files changed, 894 insertions(+), 59 deletions(-)
```

## Evidence Commands

```powershell
npm.cmd test
npm.cmd run github:audit
gh api repos/trugurpala/pala-os-v6/branches/main --jq "{name,protected}"
gh api repos/trugurpala/pala-os-v6/branches/main/protection --jq "{required_status_checks,required_pull_request_reviews,required_linear_history,allow_force_pushes,allow_deletions,required_conversation_resolution,enforce_admins}"
gh api repos/trugurpala/pala-os-v6/rulesets --jq ".[] | {name,target,enforcement,conditions,rules}"
gh pr list --repo trugurpala/pala-os-v6 --state open --json number,isDraft,reviewDecision,mergeStateStatus,statusCheckRollup
node src/cli.js court
git status --short
```

## Status

Changed-files manifest status: `PASS`

Phase B court status: `PARTIAL`

Kanıtlanan durum budur.
RELEASE_BLOCKED.
