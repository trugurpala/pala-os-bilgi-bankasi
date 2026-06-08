# CI Source Court Audit Fix - Implementation Report

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

Source branch: `codex/v6-source-card-gate-radar`

Source PR: `#1 Strengthen V6 source-card gate radar`

Source fix commit: `32362b5626b7f3264c49f3676343389c009e407f`

Commit message: `fix: unblock source court audit ci gate`

Phase: CI red fix only - `source-court-audit`

Status: `SOURCE_COURT_AUDIT_FIXED_PR_TESTS_PENDING`

Release posture: `RELEASE_BLOCKED`

## Summary

The failing CI job was `source-court-audit`. The job failed in GitHub Actions because fresh CI checkout source audit returned `BLOCKED` with `blockedFiles=1`.

Local clean-clone reproduction identified the blocked file:

```text
docs/v6-dunya-standardi-karargah-tr.md
```

Reason:

```text
source chain incomplete for LEGACY_ADAPTED
missingRequirements: sourceCard
```

Root cause: local developer state had SQLite source-card records, but GitHub Actions fresh checkout did not. The adapted governance document had a source stamp and court decision, but no machine-readable source card available in clean checkout.

## Fix

The fix keeps source-court semantics strict:

- `BLOCKED` still fails CI.
- `blockedFiles > 0` still fails CI.
- `PARTIAL + blockedFiles=0` can pass CI while remaining visibly `PARTIAL`.
- Court remains `RELEASE_BLOCKED`.

Implementation:

- Added machine-readable source card data to `docs/inheritance-backlog.json`.
- Updated `src/source-court.js` to merge source cards supplied from local SQLite with default source cards from `docs/inheritance-backlog.json`.
- Updated `.github/workflows/pala.yml` to log source audit status and blocked file count, and to explicitly fail when `blockedFiles > 0`.
- Added regression coverage proving clean-checkout source audit can use inheritance backlog source cards without turning source audit into fake PASS.

## Changed Files

```text
.github/workflows/pala.yml
docs/inheritance-backlog.json
src/source-court.js
test/pala-v6.test.js
```

## New Files

```text
NONE
```

## Excluded / Pre-existing Dirty Files

The following source repo file remains outside the PR scope:

```text
docs/v6-vibe-coder-agent-host-plan.md
```

It remains untracked and was not staged, committed, or pushed.

## Evidence Commands

CI diagnosis:

```text
gh pr checks 1 --repo trugurpala/pala-os-v6
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,title,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url
gh run list --repo trugurpala/pala-os-v6 --branch codex/v6-source-card-gate-radar --limit 5
gh run view 27146595540 --repo trugurpala/pala-os-v6 --json jobs,conclusion,status,headSha,event,workflowName,url
gh run view 27146595540 --repo trugurpala/pala-os-v6 --log-failed
gh run view 27146590349 --repo trugurpala/pala-os-v6 --json jobs,conclusion,status,headSha,event,workflowName,url
gh run view 27146590349 --repo trugurpala/pala-os-v6 --log-failed
```

Local reproduce:

```text
node src/cli.js source audit --json
workflow inline PowerShell source-court-audit step in a clean temp clone
```

Verification:

```text
npm.cmd test
npm.cmd run github:audit
node src/cli.js source audit --json
node src/cli.js court
git status --short
git diff --stat
```

Push/readback:

```text
git push origin codex/v6-source-card-gate-radar
gh pr checks 1 --repo trugurpala/pala-os-v6
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url,headRefOid
node src/cli.js court
git status -sb
```

## Verification Results

```text
npm.cmd test: PASS, 38/38
npm.cmd run github:audit: PASS
source audit: PARTIAL, blockedFiles=0
clean temp clone workflow step: PARTIAL, blockedFiles=0
court: RELEASE_BLOCKED
```

## Post-Push PR Readback

Source branch push:

```text
0392a73..32362b5  codex/v6-source-card-gate-radar -> codex/v6-source-card-gate-radar
```

PR state at readback:

```text
headRefOid: 32362b5626b7f3264c49f3676343389c009e407f
isDraft: true
mergeStateStatus: BLOCKED
reviewDecision: REVIEW_REQUIRED
source-court-audit: PASS
legacy-boundary: PASS
test: PENDING
nightly-cron: SKIPPED
court: waiting on test
```

## Rollback Note

The source branch has been pushed. Any rollback, force push, PR merge, release, deployment, or main branch action requires explicit owner approval.

## Court Decision

Source-court-audit fix: `PASS`

Full PR checks: `PENDING_TESTS`

PR readiness: `BLOCKED_WITH_REASON`

Release: `RELEASE_BLOCKED`
