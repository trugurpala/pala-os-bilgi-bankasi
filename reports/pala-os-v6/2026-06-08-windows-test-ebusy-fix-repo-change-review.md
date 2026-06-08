# Windows Test EBUSY Fix - Repo Change Review

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

Source PR: `#1 Strengthen V6 source-card gate radar`

Source fix commit: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

Review status: `PASS_FOR_CI_STABILIZATION`

Release status: `RELEASE_BLOCKED`

## Finding

The failing push-event CI test did not fail on assertion logic. It failed during temp workspace cleanup:

```text
test: docker smoke writes evidence without requiring container startup
error: EBUSY: resource busy or locked, rmdir 'C:\Users\RUNNER~1\AppData\Local\Temp\pala-os-v6-2I5YMU'
```

The pull_request-event test job passed on the same commit before the fix, which supports the diagnosis that this was a Windows cleanup race.

## Fix Review

The change is scoped to test cleanup:

- no production code changed
- no test skipped
- no assertion weakened
- no source audit semantics changed
- no court/release behavior changed

The wrapper only retries transient Windows cleanup errors:

```text
EBUSY
EPERM
ENOTEMPTY
```

Non-retryable errors still fail immediately. Retryable errors still fail after the bounded retry limit.

## Verification Review

```text
targeted docker smoke test: PASS
npm.cmd test: PASS, 38/38
node --test test/pala-v6.test.js: PASS, 38/38
npm.cmd run github:audit: PASS
node src/cli.js source audit --json: PARTIAL, blockedFiles=0
node src/cli.js court: RELEASE_BLOCKED
post-push source-court-audit: PASS x2
post-push legacy-boundary: PASS x2
post-push test: PASS x2
post-push court: PASS x2
```

## Remaining Blockers

- PR is still draft.
- Review decision remains `REVIEW_REQUIRED`.
- Merge state remains `BLOCKED`.
- Docker daemon proof remains `NOT_AVAILABLE_WITH_REASON`.
- Release remains `RELEASE_BLOCKED`.

## Exclusions

```text
docs/v6-vibe-coder-agent-host-plan.md
```

This file remains outside the PR mutation package.

## Decision

Windows test EBUSY blocker: `FIXED`

CI package: `PASS`

PR readiness: `BLOCKED_WITH_REASON`

Release readiness: `BLOCKED`

Court result: `RELEASE_BLOCKED`
