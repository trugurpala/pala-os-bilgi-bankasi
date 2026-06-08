# PR #1 Owner Approval Without Merge Evidence Manifest

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

PR: `https://github.com/trugurpala/pala-os-v6/pull/1`

Head commit: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

Requested action: owner approval without merge

Actual result: `BLOCKED_BY_GITHUB_SELF_APPROVAL_RULE`

Release posture: `RELEASE_BLOCKED`

## Knowledge Bank Files Added

- `reports/pala-os-v6/2026-06-08-pr-1-owner-approval-without-merge-report.md`
- `reports/pala-os-v6/2026-06-08-pr-1-owner-approval-without-merge-evidence-manifest.md`
- `reports/pala-os-v6/2026-06-08-pr-1-owner-approval-without-merge-review.md`
- `reports/pala-os-v6/2026-06-08-pr-1-owner-approval-without-merge-raw-patch-diff-note.md`

## Commands And Results

Pre-action PR readback:

```powershell
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,title,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url,headRefName,baseRefName,headRefOid,reviews
```

Result:

- Draft: `false`
- Merge state: `BLOCKED`
- Review decision: `REVIEW_REQUIRED`
- Reviews: `[]`
- Head: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

Approval command:

```powershell
gh pr review 1 --repo trugurpala/pala-os-v6 --approve --body "Owner approval for governance hardening review only. No merge approval. Release remains RELEASE_BLOCKED. Docker runtime proof remains NOT_AVAILABLE_WITH_REASON. Source audit remains PARTIAL with blockedFiles=0."
```

Result:

```text
failed to create review: GraphQL: Review Can not approve your own pull request (addPullRequestReview)
```

Post-action PR readback:

```powershell
gh pr view 1 --repo trugurpala/pala-os-v6 --json number,title,isDraft,mergeStateStatus,reviewDecision,statusCheckRollup,url,reviews,headRefOid
```

Result:

- Draft: `false`
- Merge state: `BLOCKED`
- Review decision: `REVIEW_REQUIRED`
- Reviews: `[]`
- Head: `61b5962f639baa61f497fdac3ba8b3e35863ed75`

Checks:

```powershell
gh pr checks 1 --repo trugurpala/pala-os-v6
```

Result:

- `Cursor Bugbot`: `PASS`
- `source-court-audit`: `PASS`
- `legacy-boundary`: `PASS`
- `test`: `PASS`
- `court`: `PASS`
- `nightly-cron`: `SKIPPED`

Court:

```powershell
node src/cli.js court
```

Result:

- `RELEASE_BLOCKED`

Source audit:

```powershell
node src/cli.js source audit --json
```

Result:

- `PARTIAL`
- `blockedFiles=0`

Source working tree:

```powershell
git status -sb
```

Result:

```text
## codex/v6-source-card-gate-radar...origin/codex/v6-source-card-gate-radar
?? docs/v6-vibe-coder-agent-host-plan.md
```

## Source Mutation Scope

- Source files changed: `NONE`
- Source commits created: `NONE`
- Source branch pushes: `NONE`
- PR body updates: `NONE`
- PR approvals created: `NONE`
- Merges: `NONE`
- Releases: `NONE`

## Excluded File Confirmation

- `docs/v6-vibe-coder-agent-host-plan.md` remains untracked and outside PR.

## Final Status

- Approval command: `FAILED_BY_GITHUB_SELF_APPROVAL_RULE`
- Review decision: `REVIEW_REQUIRED`
- Merge state: `BLOCKED`
- Court: `RELEASE_BLOCKED`
