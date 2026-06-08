# Pala OS v6 Phase B Final Mutation Scope

Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`

GitHub repo: `trugurpala/pala-os-v6`

Date: 2026-06-08

Phase: B - GitHub Governance Hardening

Owner decision carried forward:

- Phase A accepted.
- Phase C accepted as `PARTIAL`.
- Phase C implementation passed local tests, but Docker daemon proof is `NOT_AVAILABLE_WITH_REASON`.
- Release remains `RELEASE_BLOCKED`.

This is a scope report only. No source repo code, files, commits, pushes, PRs, releases, or GitHub settings were changed.

## 1. Current GitHub State

| Item | Evidence | Status |
|---|---|---|
| Repository | `trugurpala/pala-os-v6` | `PRIVATE` |
| Default branch | `main` | PASS |
| Local branch | `codex/v6-source-card-gate-radar` | INFO |
| Local worktree | Dirty from Phase A/C local mutations | PARTIAL |
| `main` branch protection | `gh api repos/trugurpala/pala-os-v6/branches/main` returned `protected=false` | BLOCKED |
| `main` protection endpoint | `gh api repos/trugurpala/pala-os-v6/branches/main/protection` returned `Branch not protected (HTTP 404)` | BLOCKED |
| `codex/v6-source-card-gate-radar` protection | GitHub gate audit returned not protected | BLOCKED |
| Repository rulesets | `gh api repos/trugurpala/pala-os-v6/rulesets` returned no visible active rulesets | BLOCKED |
| Workflow | `Pala OS V6`, path `.github/workflows/pala.yml`, state `active` | PARTIAL |
| Required check candidate | Check run name `test`, workflow `Pala OS V6`, conclusion `success` on latest observed run | PARTIAL |
| Nightly job | `nightly-cron` skipped on push/PR, schedule-only | NOT_USED_WITH_REASON |
| Open PR | PR #1 draft, base `main`, head `codex/v6-source-card-gate-radar`, merge state `CLEAN`, review decision empty | PARTIAL |
| CODEOWNERS | `.github/CODEOWNERS` exists with `* @trugurpala` | PARTIAL |
| PR template | Evidence/test/rollback checkboxes exist | PARTIAL |

Current governance verdict: `BRANCH_PROTECTION_BLOCKED`.

## 2. Required Branch Protection Rules

Recommended implementation path: GitHub repository ruleset targeting `main`, with branch protection fallback if rulesets are unavailable.

| Rule | Required Setting | Why Needed | Risk If Missing |
|---|---|---|---|
| Target branch | `main` | `main` is default production record. | Direct commits can bypass court. |
| Require pull request | Enabled | All mutations must pass review package and evidence. | Agent/local changes can enter `main` without review. |
| Required approvals | At least 1 | Owner or approved reviewer must approve governance changes. | No human gate before merge. |
| Require CODEOWNERS review | Enabled | Governance/docs/workflows need owner-controlled review. | Critical files can change without owner visibility. |
| Dismiss stale approvals | Enabled | New commits invalidate old review. | Review can approve a different diff than the merge diff. |
| Require status checks | Enabled | Local claims need CI proof. | Broken code can merge. |
| Require branch up to date | Enabled if practical | Prevents stale green checks. | Old check result can merge over newer `main`. |
| Require conversation resolution | Enabled | Blocks unresolved review/court issues. | Known concerns can be ignored. |
| Require linear history | Enabled | Keeps provenance and rollback readable. | Merge graph becomes harder to audit. |
| Block force pushes | Enabled | Preserve ledger/source history. | History can be rewritten. |
| Block deletions | Enabled | Prevent accidental branch loss. | `main` can be deleted. |
| Restrict bypass | No bypass except explicit owner emergency path | Prevents silent admin override. | Governance can be bypassed by privileged token. |

Solo-owner warning: if all merges are authored by the same GitHub account and required review cannot be self-satisfied, strict review may deadlock. The clean governance answer is to use an approved second reviewer/team or keep owner-approval evidence outside the PR while still requiring PR/checks.

## 3. Required Status Checks

Initial required check set:

| Check | Source | Required? | Reason |
|---|---|---:|---|
| `test` | GitHub Actions workflow `Pala OS V6` | Yes | Current stable CI job; includes bootstrap, test, status, and Phase C legacy boundary scan. |
| `nightly-cron` | GitHub Actions workflow `Pala OS V6` schedule job | No | Skips on push/PR; making it required would block normal PRs. |

Recommended Phase B workflow hardening:

| Proposed Job | Purpose | Required? |
|---|---|---:|
| `legacy-boundary` | Prove `.dockerignore` and legacy quarantine boundary. | Yes |
| `source-court-audit` | Run `node src/cli.js source audit --json`. | Yes |
| `test` | Run `npm.cmd test` / `npm test`. | Yes |
| `court` | Run `node src/cli.js court` and prove release remains blocked without owner approval. | Yes |
| `github-gate-audit` | Run read-only branch protection/ruleset audit. | Advisory until protection exists, then required if token permissions allow. |

The current workflow has a single `test` job. For cleaner branch protection, Phase B should split governance checks into stable job names before requiring them.

## 4. Required CODEOWNERS / Review Policy

Current CODEOWNERS:

```text
* @trugurpala
```

Minimum acceptable Phase B policy:

```text
* @trugurpala
.github/** @trugurpala
docs/** @trugurpala
src/** @trugurpala
scripts/** @trugurpala
test/** @trugurpala
Dockerfile @trugurpala
compose.yaml @trugurpala
package.json @trugurpala
AGENTS.md @trugurpala
README.md @trugurpala
PALA_RULES.md @trugurpala
SECURITY.md @trugurpala
ARCHITECTURE.md @trugurpala
```

Review policy:

- Required PR before `main`.
- Required approving review.
- Required CODEOWNERS review for governance-sensitive files.
- Stale approvals dismissed on new commits.
- PR template must require the four artefacts for implementation phases:
  - Implementation Report.
  - Changed Files Manifest.
  - Repo Change Review.
  - Raw Patch/Diff.
- No review package means no court decision and no `PASS`.

## 5. Required Workflow Changes

Expected source files for Phase B implementation:

| File | Planned Change | Risk |
|---|---|---|
| `.github/workflows/pala.yml` | Split current monolithic `test` job into stable required check jobs or add governance jobs with stable names. | Changing job names before branch protection is applied can make required-check setup inconsistent if done in the wrong order. |
| `.github/CODEOWNERS` | Expand owner paths for governance-critical files. | Over-broad ownership can slow trivial PRs, but that is acceptable for current hardening. |
| `.github/PULL_REQUEST_TEMPLATE.md` | Add four-artefact review package checklist and `RELEASE_BLOCKED` confirmation. | Checklist is procedural unless enforced by CI. |
| `scripts/pala_github_gate_audit.ps1` | Add ruleset readback and stricter PASS/BLOCKED fields. | GitHub token permissions may differ locally vs Actions. |
| `docs/github-policy-pack.md` | Align policy text with actual ruleset/branch protection requirements. | Existing text is policy intent, not enforcement. |
| `test/pala-v6.test.js` | Add tests that local governance files contain required branch/ruleset policy markers. | Tests cannot prove GitHub remote settings by themselves. |

Expected GitHub setting changes for Phase B implementation:

| Surface | Planned Change |
|---|---|
| GitHub ruleset or branch protection | Protect `main`, require PR, review, CODEOWNERS review, required checks, no force push, no deletion. |
| Repository merge settings | Consider enabling delete branch on merge, disabling merge methods not desired by owner, and requiring linear history. |
| Actions permissions | Set minimum permissions for workflows; use `GH_TOKEN` only for read-back audits where needed. |

## 6. Release Gate Enforcement Plan

Phase B must not open release. It must make release harder to fake.

Required release posture after Phase B:

- `main` protected.
- PR required.
- Required checks enforced.
- CODEOWNERS review required.
- Force push blocked.
- Delete branch blocked.
- `node src/cli.js court` remains `RELEASE_BLOCKED` without owner approval.
- `npm run github:audit` reports branch protection/ruleset evidence instead of `Branch not protected`.
- Release issue/template remains owner-controlled.
- No automatic deploy/release workflow is introduced.

Phase B removes `BRANCH_PROTECTION_BLOCKED` only when GitHub read-back proves `main` protection or an active ruleset is enforcing the required policy.

## 7. gh api Evidence Commands

Read-only commands already run:

```powershell
gh auth status
gh repo view trugurpala/pala-os-v6 --json nameWithOwner,visibility,defaultBranchRef,isPrivate,url
powershell -NoProfile -ExecutionPolicy Bypass -File scripts\pala_github_gate_audit.ps1
gh api repos/trugurpala/pala-os-v6/branches/main --jq '{name,protected,protection_url}'
gh api repos/trugurpala/pala-os-v6/branches/main/protection --jq '{required_status_checks,enforce_admins,required_pull_request_reviews,restrictions,required_linear_history,allow_force_pushes,allow_deletions}'
gh api repos/trugurpala/pala-os-v6/rulesets --jq '.[] | {id,name,target,enforcement,conditions,rules}'
gh api repos/trugurpala/pala-os-v6/actions/workflows --jq '.workflows[] | {id,name,path,state}'
gh api repos/trugurpala/pala-os-v6/actions/runs/27123828415/jobs --jq '.jobs[] | {name,status,conclusion,html_url}'
gh api repos/trugurpala/pala-os-v6/commits/98bbf1f5827910fb00afd41ad4836060bcf55d0b/check-runs --jq '.check_runs[] | {name,status,conclusion,app:.app.slug,details_url}'
gh pr list --repo trugurpala/pala-os-v6 --state open --json number,title,headRefName,baseRefName,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url
```

Observed critical outputs:

```text
repo visibility: PRIVATE
default branch: main
main protected: false
main protection endpoint: Branch not protected (HTTP 404)
branches: codex/v6-source-card-gate-radar protected=false, main protected=false
workflow: Pala OS V6 active
required check candidate: test
open PR #1: draft, CLEAN, reviewDecision empty
github gate summary: gate=BLOCKED
```

Post-implementation proof commands:

```powershell
npm.cmd run github:audit
gh api repos/trugurpala/pala-os-v6/branches/main --jq '{name,protected}'
gh api repos/trugurpala/pala-os-v6/branches/main/protection --jq '{required_status_checks,required_pull_request_reviews,required_linear_history,allow_force_pushes,allow_deletions}'
gh api repos/trugurpala/pala-os-v6/rulesets --jq '.[] | {name,target,enforcement,conditions,rules}'
gh pr list --repo trugurpala/pala-os-v6 --state open --json number,isDraft,reviewDecision,mergeStateStatus,statusCheckRollup
node src/cli.js court
npm.cmd test
git status --short
```

## 8. Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Required review deadlock in solo-owner repo | PRs cannot merge if the only actor is also the author. | Add an approved second reviewer/team or keep an explicit owner emergency bypass with ledger evidence. |
| Required check name mismatch | Branch protection blocks all merges. | Freeze job names before enabling protection; verify check run names with `gh api check-runs`. |
| Ruleset vs branch protection duplication | Conflicting GitHub policy surfaces. | Prefer one enforcement path: ruleset first, branch protection fallback. |
| GitHub token permissions differ in Actions | `github-gate-audit` may fail in CI. | Make remote protection audit advisory until token permissions are proven, then require it. |
| CODEOWNERS too broad | Slower PRs. | Accept for hardening phase; reduce later only after governance evidence exists. |
| Owner bypass too loose | Governance can be bypassed. | Any bypass must require explicit owner evidence and stay visible in court/ledger. |
| PR template is not enforceable alone | Checkboxes can be ignored. | Add CI/lint later for required artefact links if needed. |

## 9. Rollback Plan

No source repo mutation was made in this scope step.

For the future Phase B implementation:

1. If workflow split breaks CI, revert `.github/workflows/pala.yml` to the previous single `test` job.
2. If required checks block merges due to wrong names, temporarily disable the specific required check and re-run check discovery.
3. If CODEOWNERS causes deadlock, reduce scope to `.github/**`, `src/**`, `scripts/**`, `docs/**`, and root governance docs while owner creates a second reviewer path.
4. If ruleset blocks emergency owner action, use documented owner emergency bypass and record it in court/evidence.
5. Do not delete Phase A/C local mutation evidence.
6. Keep release `RELEASE_BLOCKED` throughout rollback.

## 10. Phase B Final Mutation Scope

Phase B implementation package should include:

### Local Source Repo Mutations

- Update `.github/workflows/pala.yml` with stable governance job names.
- Update `.github/CODEOWNERS` with explicit governance ownership paths.
- Update `.github/PULL_REQUEST_TEMPLATE.md` with four-artefact review package checklist.
- Update `scripts/pala_github_gate_audit.ps1` to read branch protection and rulesets explicitly.
- Update `docs/github-policy-pack.md` to match actual enforcement.
- Add or update tests in `test/pala-v6.test.js` for local governance file expectations.

### GitHub Remote Mutations

- Enable branch protection or an active repository ruleset for `main`.
- Require PR before merge.
- Require at least one approval.
- Require CODEOWNERS review.
- Dismiss stale approvals.
- Require status checks.
- Block force pushes.
- Block branch deletion.
- Enforce linear history if selected by owner.

### Expected Phase B Result

| Area | Expected Result |
|---|---|
| `BRANCH_PROTECTION_BLOCKED` | Removed only after GitHub read-back proves protection/ruleset active. |
| CI required checks | Required and stable. |
| PR review | Required. |
| CODEOWNERS | Expanded and enforced. |
| Release | Still `RELEASE_BLOCKED`. |
| Court | Cannot PASS without review package and owner approval. |

Phase B scope status: `READY_FOR_OWNER_REVIEW`.

Current GitHub governance status: `BLOCKED`.

Kanıtlanan durum budur.
RELEASE_BLOCKED.
