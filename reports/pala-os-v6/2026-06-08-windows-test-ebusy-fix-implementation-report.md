# Windows Test EBUSY Fix - Implementation Report

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

Source branch: `codex/v6-source-card-gate-radar`

Source PR: `#1 Strengthen V6 source-card gate radar`

Source fix commit: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

Commit message: `fix: stabilize windows test cleanup`

Phase: CI red fix only - Windows test EBUSY cleanup

Status: `PASS`

Release posture: `RELEASE_BLOCKED`

## Summary

The remaining CI blocker was the Windows `test` job failing during teardown, not during the tested Docker smoke behavior.

Failing CI:

```text
run id: 27147614431
job id: 80129882120
event: push
job: test
step: Run tests
test: docker smoke writes evidence without requiring container startup
error: EBUSY: resource busy or locked, rmdir 'C:\Users\RUNNER~1\AppData\Local\Temp\pala-os-v6-2I5YMU'
exit code: 1
```

The same commit's pull request workflow passed, while the push workflow failed on Windows temp cleanup.

## Root Cause

The test body passed, but `t.after()` attempted to recursively remove the temp workspace immediately after child-process and filesystem activity. Windows can keep short-lived handles on files or folders briefly after process exit, causing `fs.rm(..., { recursive: true, force: true })` to fail with `EBUSY`, `EPERM`, or `ENOTEMPTY`.

This is a CI cleanup race, not a product/runtime failure.

## Fix

Implemented a test-only cleanup wrapper in `test/pala-v6.test.js`:

- uses `fs.rm` for real cleanup
- retries only `EBUSY`, `EPERM`, and `ENOTEMPTY`
- uses bounded backoff
- does not swallow real test failures
- still throws after final retry

No test was skipped. No production code was changed.

## Changed Files

```text
test/pala-v6.test.js
```

## New Files

```text
NONE
```

## Excluded / Pre-existing Dirty Files

The following file remains outside the PR scope:

```text
docs/v6-vibe-coder-agent-host-plan.md
```

It remains untracked and was not staged, committed, or pushed.

## Evidence Commands

Diagnosis:

```text
gh pr checks 1 --repo trugurpala/pala-os-v6
gh run list --repo trugurpala/pala-os-v6 --branch codex/v6-source-card-gate-radar --limit 10
gh run view 27147614431 --repo trugurpala/pala-os-v6 --json jobs,conclusion,status,headSha,event,workflowName,url
gh run view 27147614431 --repo trugurpala/pala-os-v6 --log-failed
```

Local reproduce and verification:

```text
npm.cmd test
node --test test/pala-v6.test.js
node --test --test-name-pattern "docker smoke writes evidence without requiring container startup" test/pala-v6.test.js
npm.cmd run github:audit
node src/cli.js source audit --json
node src/cli.js court
git status --short
git diff --stat
```

Post-push:

```text
git push origin codex/v6-source-card-gate-radar
gh pr checks 1 --repo trugurpala/pala-os-v6
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url,headRefOid
node src/cli.js court
git status -sb
```

## Verification Results

```text
targeted docker smoke test: PASS
npm.cmd test: PASS, 38/38
node --test test/pala-v6.test.js: PASS, 38/38
npm.cmd run github:audit: PASS
source audit: PARTIAL, blockedFiles=0
court: RELEASE_BLOCKED
```

## Post-Push PR Readback

```text
headRefOid: 61b5962f639baa61f497fdac3ba8b3e35863ed75
isDraft: true
mergeStateStatus: BLOCKED
reviewDecision: REVIEW_REQUIRED
source-court-audit: PASS x2
legacy-boundary: PASS x2
test: PASS x2
court: PASS x2
nightly-cron: SKIPPED x2
```

## Rollback Note

The fix was pushed to the existing PR branch. Any rollback, force push, PR merge, release, deploy, or main branch operation requires explicit owner approval.

## Court Decision

Windows EBUSY test fix: `PASS`

CI: `PASS`

PR readiness: `BLOCKED_WITH_REASON`

Release: `RELEASE_BLOCKED`
