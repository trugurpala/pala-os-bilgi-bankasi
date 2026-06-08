# Repo Change Review Policy

Date: 2026-06-08

Owner directive: implementation reports are not enough by themselves. A reviewer must also be able to see what changed in the source repo.

## Rule

For every meaningful local mutation in a Pala OS repo, publish an append-only repo-change review package to the knowledge-bank repo.

No Review Package = No Court Decision.

If there is an implementation report but no changed-files manifest, repo-change review, or raw patch/diff, the phase status is at most `PARTIAL`.

The package must include:

- Phase name and source repo path.
- Implementation report.
- Changed-files manifest.
- Repo-change review.
- Included mutation files.
- Excluded/pre-existing dirty files.
- New files.
- Changed tracked files.
- Raw diff or patch file when practical.
- File-by-file change explanation.
- Evidence commands and observed results.
- Clear release posture.

## Required Four Artifacts

Every implementation phase must produce four reviewer artifacts:

1. Implementation Report: what changed, why it changed, test result, evidence, blockers.
2. Changed Files Manifest: included files, excluded files, new files, unchanged important files.
3. Repo Change Review: risk, expected effect, rollback, reviewer checklist.
4. Raw Patch/Diff: the actual local mutation, or a clear `NOT_AVAILABLE_WITH_REASON`.

If any artifact is missing, the court may not mark the phase `PASS`.

## Patch Handling

If the source repo has untracked files, export them as full new-file snapshots in the raw patch or explain why they are not included.

If tracked files contain earlier unrelated dirty changes, state that clearly and separate the phase-specific intent from the full local diff.

## Safety

Never publish secrets, API keys, local runtime databases, private credentials, `.env` contents, or sensitive customer data.

Knowledge-bank publication is reviewer evidence. It is not source repo release approval.

Default release posture remains `RELEASE_BLOCKED`.
