# Phase B Scope Evidence Manifest

Date: 2026-06-08

Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`

GitHub repo: `trugurpala/pala-os-v6`

Scope: Phase B Final Mutation Scope only. No source repo mutation.

## Commands Run

| Command | Purpose | Result |
|---|---|---|
| `git status --short` | Local worktree state | Dirty worktree with Phase A/C local mutations. |
| `git branch --show-current` | Current branch | `codex/v6-source-card-gate-radar` |
| `git remote -v` | Remote source | `https://github.com/trugurpala/pala-os-v6.git` |
| `Get-ChildItem -Path .github -Recurse` | GitHub governance files | CODEOWNERS, PR template, issue templates, workflow present. |
| `Get-Content .github\CODEOWNERS` | Owner file | `* @trugurpala` |
| `Get-Content .github\PULL_REQUEST_TEMPLATE.md` | PR evidence checklist | Exists, but no four-artefact rule yet. |
| `Get-Content .github\workflows\pala.yml` | Workflow inspection | Single required candidate job `test`; `nightly-cron` schedule-only. |
| `powershell -NoProfile -ExecutionPolicy Bypass -File scripts\pala_github_gate_audit.ps1` | Existing GitHub gate audit | Gate `BLOCKED`; both checked branches unprotected. |
| `gh repo view trugurpala/pala-os-v6 --json nameWithOwner,visibility,defaultBranchRef,isPrivate,url` | Repo metadata | Private repo, default branch `main`. |
| `gh api repos/trugurpala/pala-os-v6/branches/main --jq '{name,protected,protection_url}'` | Branch protection readback | `protected=false`. |
| `gh api repos/trugurpala/pala-os-v6/branches/main/protection ...` | Protection details | `Branch not protected (HTTP 404)`. |
| `gh api repos/trugurpala/pala-os-v6/rulesets ...` | Ruleset readback | No visible active ruleset output. |
| `gh api repos/trugurpala/pala-os-v6/actions/workflows ...` | Workflow list | `Pala OS V6` active. |
| `gh api repos/trugurpala/pala-os-v6/actions/runs/27123828415/jobs ...` | Latest run jobs | `test` success; `nightly-cron` skipped. |
| `gh api repos/trugurpala/pala-os-v6/commits/98bbf1f.../check-runs ...` | Check run names | Required check candidate: `test`. |
| `gh pr list --repo trugurpala/pala-os-v6 --state open ...` | Open PR governance state | PR #1 draft, review decision empty, check run `test` success. |

## Critical Evidence

```text
main protected=false
main protection endpoint=HTTP 404 Branch not protected
codex/v6-source-card-gate-radar protected=false
rulesets=no visible active ruleset output
GitHub gate audit=BLOCKED
workflow=Pala OS V6 active
required check candidate=test
open PR #1=draft, CLEAN, no review decision
```

## Phase B Scope Files To Mutate Later

No source repo files were changed in this scope step.

Expected future implementation files:

```text
.github/workflows/pala.yml
.github/CODEOWNERS
.github/PULL_REQUEST_TEMPLATE.md
scripts/pala_github_gate_audit.ps1
docs/github-policy-pack.md
test/pala-v6.test.js
```

## Court Status

Current scope evidence supports:

```text
BRANCH_PROTECTION_BLOCKED
RELEASE_BLOCKED
```

Kanıtlanan durum budur.
RELEASE_BLOCKED.
