# Pala Memory Core v0.17 Open Source Intelligence Gate Implementation Report

## Source
- Source repo: `trugurpala/pala-memory-core`
- Phase: `v0.17 open source intelligence gate`
- Branch: `codex/v0-17-open-source-intelligence-gate`
- Commit: `5997d7c96d4c1857fc72be701f34f15132d5ebbd`
- Draft PR: https://github.com/trugurpala/pala-memory-core/pull/3

## Status
- Result: `OSI_READY_FOR_OWNER_REVIEW`
- CI: `smoke` passed on draft PR.
- Release posture: no main merge, no release, no tag.

## Changed Files
- `.github/workflows/pala-memory-core-ci.yml`
- `dashboard/index.html`
- `docs/commands.md`
- `docs/open-source-candidates.json`
- `docs/open-source-intelligence.md`
- `pala.py`

## Evidence Commands
- `python -m py_compile pala.py`
- `python pala.py source court`
- `python pala.py source court --json`
- `python pala.py source court --online`
- `python pala.py token intel`
- `python pala.py doctor`
- `python pala.py dashboard export --all`
- `python pala.py list --limit 10`
- `git check-ignore -v data/reports/open-source-intelligence.json`
- `git check-ignore -v data/reports/token-intelligence.json`
- `git check-ignore -v dashboard/records.json`
- Browser verification: OSI section visible, 8 table rows, no console errors.

## Summary
The v0.17 gate adds a local-first Open Source Intelligence Court for external repos, MCP candidates, SDKs, and Vibe tooling. The default court is offline and keeps every candidate in `HOLD` unless metadata has been checked. Online mode uses GitHub API metadata only and does not clone, install, or vendor external code.

## Rollback Note
Rollback is the single source commit on branch `codex/v0-17-open-source-intelligence-gate`. Do not merge PR #3 if owner review rejects the candidate policy.

## Release Posture
This report is evidence only. It does not approve release, merge, or deployment.
