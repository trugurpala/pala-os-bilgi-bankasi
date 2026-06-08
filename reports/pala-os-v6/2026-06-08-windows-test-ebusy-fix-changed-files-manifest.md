# Windows Test EBUSY Fix - Changed Files Manifest

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

Source branch: `codex/v6-source-card-gate-radar`

Source PR: `#1 Strengthen V6 source-card gate radar`

Source fix commit: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

## Mutation Package

Included source files:

```text
test/pala-v6.test.js
```

## New Files

```text
NONE
```

## File Notes

```text
test/pala-v6.test.js
  Adds a bounded Windows-safe rm wrapper for test workspace cleanup.
  Retries EBUSY, EPERM, and ENOTEMPTY only.
  Preserves real test failures by throwing on non-retryable errors and after final retry.
```

## Excluded / Pre-existing Dirty Files

Not included:

```text
docs/v6-vibe-coder-agent-host-plan.md
```

Reason: outside hardening PR scope.

## Diff Stat

```text
1 file changed, 22 insertions(+), 1 deletion(-)
```

## Source Repo Post-Push State

```text
## codex/v6-source-card-gate-radar...origin/codex/v6-source-card-gate-radar
?? docs/v6-vibe-coder-agent-host-plan.md
```

## Boundaries

Main direct push: `NO`

PR merge: `NO`

Release: `NO`

Deploy: `NO`

New feature: `NO`

New dashboard surface: `NO`

Source branch push: `YES`
