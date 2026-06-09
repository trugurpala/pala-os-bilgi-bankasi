# Pala OS V6 Court Release Decision Fix - Repo Change Review

Date: 2026-06-09  
Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`  
Phase: Repo change review package  
Status: `PASS` for local review; release remains `RELEASE_BLOCKED`

## Review Scope

Included files:

- `src/policy.js`
- `src/cli.js`
- `test/pala-v6.test.js`

Excluded dirty files:

- `docs/v6-vibe-coder-agent-host-plan.md` - pre-existing untracked file; not part of this mutation.

New source files:

- None.

Raw patch:

- `reports/pala-os-v6/2026-06-09-court-release-decision-fix-raw-patch-diff.patch`

## Tracked Diff Stat

```text
src/cli.js           | 30 +++++++++++++++------------
src/policy.js        | 57 +++++++++++++++++++++++++++++++++++++++++++++-------
test/pala-v6.test.js | 28 ++++++++++++++++++++++++++
3 files changed, 95 insertions(+), 20 deletions(-)
```

## File-by-File Change Notes

### `test/pala-v6.test.js`

Added a TDD reproducer:

- Sets `PALA_OWNER_APPROVED=1`.
- Calls `evaluateCourt()` with zero blocked required standards, a source card, a ledger record, and a `PARTIAL` source-stamp gate.
- Asserts `court.decision === 'PASS'`.
- Asserts `court.releaseReady === true`.
- Restores the previous owner approval environment variable.

RED result before fix:

- Expected `PASS`, actual `RELEASE_BLOCKED`.

### `src/policy.js`

Added `resolveReleaseGateState()` as the canonical release gate calculator.

The helper now computes:

- `decision`
- `gate`
- `verdict`
- `releaseReady`
- source-card presence
- ledger evidence presence
- blocked required count
- source-stamp gate status/passability

Updated `evaluateCourt()` to use this helper and return coherent `decision`, `releaseReady`, `gate`, and `releaseStatus` values.

### `src/cli.js`

Imported and reused `resolveReleaseGateState()` in `buildCourtDecisionPayload()`.

This removes duplicate release gate calculation and keeps the nested `releaseGate`, `verdictSummary`, and top-level court decision aligned.

## Evidence Commands

RED:

```powershell
node --test --test-name-pattern "owner-approved court returns" test\pala-v6.test.js
```

RED result:

```text
actual: RELEASE_BLOCKED
expected: PASS
```

GREEN:

```powershell
node --test --test-name-pattern "owner-approved court returns" test\pala-v6.test.js
npm.cmd test
```

CLI behavior checks:

```powershell
$env:PALA_OPEN_BROWSER='0'; $env:PALA_OWNER_APPROVED='1'; node src/cli.js court
$env:PALA_OPEN_BROWSER='0'; Remove-Item Env:PALA_OWNER_APPROVED -ErrorAction SilentlyContinue; node src/cli.js court
```

Release precheck:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts\pala_release_precheck.ps1
```

Git evidence:

```powershell
git status -sb
git diff --stat origin/codex/v6-source-card-gate-radar...HEAD
git log --oneline origin/codex/v6-source-card-gate-radar..HEAD
```

## Observed Results

- Full test suite: 39 tests passed, 0 failed.
- Owner-approved court simulation: `decision=PASS`, `releaseGate.status=PASS`, `releaseReady=true`.
- Normal court: `decision=RELEASE_BLOCKED`, `releaseGate.status=BLOCKED`, `releaseReady=false`.
- Release precheck: still blocked because owner approval is missing.
- Source branch: ahead of upstream by 2 local commits.

## Risk Review

Residual risks:

- `sourceStampGate.status=PARTIAL` is treated as passable. This matches the current local court behavior where partial governance/reference tracking is non-release-blocking, but it should remain explicit and tested.
- Source branch is not pushed; web-based reviewers will not see the source commits until the owner approves a push.
- Node built-in SQLite still emits experimental warnings in tests; this is unrelated to the fix.

No secrets, local DB dumps, runtime ledgers, or private credentials are included.

## Release Posture

No release approval is granted. This change fixes internal court consistency only. Normal state remains `RELEASE_BLOCKED` until owner approval is explicitly present.
