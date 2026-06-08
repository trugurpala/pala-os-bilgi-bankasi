# Phase E Repo Change Review

## Scope

Phase E implements the Dashboard Truth Contract only. It does not add a new dashboard screen, skill, agent, deploy, release, source repo commit, source repo push, or PR merge.

## What changed

- `buildDashboardTruthContract()` produces an 11-panel machine-readable truth contract.
- `buildAppState()` includes Docker smoke evidence and the dashboard truth contract.
- `/api/state` includes the full truth contract by normal state serialization.
- `/api/health` includes truth status summary and source stamp gate summary.
- HTML dashboard renders a Truth Contract table and marks token economy as estimated.
- Tests validate the fake-green rules.
- `docs/dashboard-truth-contract.md` documents panel semantics and PASS conditions.

## Evidence commands

| Command | Result |
|---|---|
| `curl http://127.0.0.1:8787/api/state` | `dashboardTruthContract.status=RELEASE_BLOCKED`, `panels=11`, Docker `NOT_AVAILABLE_WITH_REASON`, Source Court `PARTIAL`, raw legacy files not exposed |
| `curl http://127.0.0.1:8787/api/health` | `ok=true`, `court=RELEASE_BLOCKED`, `dashboardTruthStatus=RELEASE_BLOCKED` |
| `node src/cli.js court` | `decision=RELEASE_BLOCKED`, `sourceStampGate=PARTIAL` |
| `node src/cli.js source audit --json` | `status=PARTIAL`, active files 88, blocked files 0 |
| `npm.cmd test` | `37/37 PASS` |
| `git status --short` | Dirty source repo, no source commit |

## Risks

- The raw patch file is generated against current `HEAD`, while the source repo already contains Phase A/B/C dirty files. The manifest separates Phase E files from pre-existing dirty files.
- Docker Boot remains `NOT_AVAILABLE_WITH_REASON` because Docker daemon runtime proof is still absent; dashboard correctly refuses `PASS`.
- Source Court remains `PARTIAL`; dashboard correctly refuses to show a greener source panel.
- Release Court remains `RELEASE_BLOCKED` because owner approval is absent.
- Token economy is still estimate-based, so it is intentionally `estimated: true` and `PARTIAL`.

## Expected effect

- Dashboard can no longer present a single green overall status while child panels are blocked, partial, unknown, or release-blocked.
- Dashboard state can be consumed by tests, API clients, and future court logic.
- Legacy archive stays sanitized through Source Court summary; raw `files` list is not exposed in dashboard state.

## Rollback plan

1. Remove `buildDashboardTruthContract()` and related helpers from `src/policy.js`.
2. Remove Docker evidence loading and `dashboardTruthContract` assignment from `src/bootstrap.js`.
3. Remove truth summary fields from `/api/health` in `src/server.js`.
4. Remove Truth Contract nav/table and token estimated text from `src/dashboard.js`.
5. Remove Phase E tests from `test/pala-v6.test.js`.
6. Delete `docs/dashboard-truth-contract.md`.
7. Run `npm.cmd test`.

No legacy archive deletion is involved. No GitHub branch protection rollback is involved. No source repo commit/push/release was performed.

## Court posture

Review package is complete, so Phase E can receive a court decision.

Phase E implementation: `PASS`.

Product release state: `RELEASE_BLOCKED`.
