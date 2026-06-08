# Repo Change Review Policy

Date: 2026-06-08

Owner directive: implementation reports are not enough by themselves. A reviewer must also be able to see what changed in the source repo.

## Rule

For every meaningful local mutation in a Pala OS repo, publish an append-only repo-change review package to the knowledge-bank repo.

The package must include:

- Phase name and source repo path.
- Included mutation files.
- Excluded/pre-existing dirty files.
- New files.
- Changed tracked files.
- Raw diff or patch file when practical.
- File-by-file change explanation.
- Evidence commands and observed results.
- Clear release posture.

## Patch Handling

If the source repo has untracked files, export them as full new-file snapshots in the raw patch or explain why they are not included.

If tracked files contain earlier unrelated dirty changes, state that clearly and separate the phase-specific intent from the full local diff.

## Safety

Never publish secrets, API keys, local runtime databases, private credentials, `.env` contents, or sensitive customer data.

Knowledge-bank publication is reviewer evidence. It is not source repo release approval.

Default release posture remains `RELEASE_BLOCKED`.
