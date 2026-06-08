# Pala OS v6 PR #1 Ready For Owner Review Evidence Manifest

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

PR: `https://github.com/trugurpala/pala-os-v6/pull/1`

Head commit: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

Release posture: `RELEASE_BLOCKED`

## Source Repo Mutation Scope

Source files changed:

- `NONE`

Source commits created:

- `NONE`

Source branch push:

- `NONE`

PR body update:

- `NONE`

GitHub metadata change:

- PR #1 changed from draft to ready for review.

## Knowledge Bank Files Added

- `reports/pala-os-v6/2026-06-08-pr-1-ready-for-owner-review-report.md`
- `reports/pala-os-v6/2026-06-08-pr-1-ready-for-owner-review-evidence-manifest.md`
- `reports/pala-os-v6/2026-06-08-pr-1-ready-for-owner-review-review.md`
- `reports/pala-os-v6/2026-06-08-pr-1-ready-for-owner-review-raw-patch-diff.md`

## Evidence Commands And Results

Command:

```powershell
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,title,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url,headRefName,baseRefName,headRefOid
```

Pre-action result:

- `isDraft=true`
- `mergeStateStatus=BLOCKED`
- `reviewDecision=REVIEW_REQUIRED`
- `headRefOid=61b5962f639baa61f497fdac3ba8b3e35863ed75`

Command:

```powershell
gh pr ready 1 --repo trugurpala/pala-os-v6
```

Result:

- PR #1 marked ready for review.

Command:

```powershell
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,title,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url,headRefName,baseRefName,headRefOid
```

Post-action result:

- `isDraft=false`
- `mergeStateStatus=BLOCKED`
- `reviewDecision=REVIEW_REQUIRED`
- `headRefOid=61b5962f639baa61f497fdac3ba8b3e35863ed75`

Command:

```powershell
gh pr checks 1 --repo trugurpala/pala-os-v6
```

Result:

- `source-court-audit`: `PASS`
- `legacy-boundary`: `PASS`
- `test`: `PASS`
- `court`: `PASS`
- `nightly-cron`: `SKIPPED`
- `Cursor Bugbot`: `PENDING`

Command:

```powershell
node src/cli.js court
```

Result:

- `RELEASE_BLOCKED`

Command:

```powershell
git status -sb
```

Result:

```text
## codex/v6-source-card-gate-radar...origin/codex/v6-source-card-gate-radar
?? docs/v6-vibe-coder-agent-host-plan.md
```

## Excluded Files

Excluded file:

- `docs/v6-vibe-coder-agent-host-plan.md`

Confirmation:

- Still untracked locally.
- Not staged.
- Not committed.
- Outside PR scope.

## Release Posture

- Court: `RELEASE_BLOCKED`
- Merge: `NOT_PERFORMED`
- Release: `NOT_PERFORMED`
- Deploy: `NOT_PERFORMED`
