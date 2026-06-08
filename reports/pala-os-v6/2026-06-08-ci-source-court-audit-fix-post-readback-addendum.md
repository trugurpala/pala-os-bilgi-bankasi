# CI Source Court Audit Fix - Post-Readback Addendum

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

Source PR: `#1 Strengthen V6 source-card gate radar`

Source fix commit: `32362b5626b7f3264c49f3676343389c009e407f`

Knowledge-bank base package: `2026-06-08-ci-source-court-audit-fix-*`

## Reason For Addendum

The base CI fix report was published while PR test jobs were still pending. A later post-push readback completed enough to refine the status.

This is append-only. The earlier report files are preserved.

## Updated PR Check Readback

```text
source-court-audit: PASS x2
legacy-boundary: PASS x2
test: PASS x1, FAIL x1
court: PASS x1, SKIPPED x1
nightly-cron: SKIPPED x2
```

## Source Court Fix Status

The target blocker is fixed:

```text
source-court-audit: PASS
```

## New Remaining CI Blocker

The push-event `test` job failed outside the source-court-audit scope:

```text
job: test
step: Run tests
test: docker smoke writes evidence without requiring container startup
error: EBUSY: resource busy or locked, rmdir 'C:\Users\RUNNER~1\AppData\Local\Temp\pala-os-v6-2I5YMU'
```

The pull_request-event `test` job passed, and the pull_request-event `court` job passed.

## Court And Release

Local court remains:

```text
RELEASE_BLOCKED
```

No release, deploy, merge, or main direct push was performed.

## Updated Decision

source-court-audit fix: `PASS`

Overall CI: `FAIL_WITH_NEW_TEST_BLOCKER`

PR readiness: `BLOCKED_WITH_REASON`

Release: `RELEASE_BLOCKED`
