# Pala Memory Core v0.17 Repo Change Review

## Review Scope
- Source repo: `trugurpala/pala-memory-core`
- Branch: `codex/v0-17-open-source-intelligence-gate`
- Commit: `5997d7c96d4c1857fc72be701f34f15132d5ebbd`
- Draft PR: https://github.com/trugurpala/pala-memory-core/pull/3

## File-by-File Review
| File | Review |
|---|---|
| `pala.py` | Adds `source court` CLI with offline default, metadata-only online mode, generated JSON report, doctor checks, and dashboard export payload. No clone/install/vendor path added. |
| `dashboard/index.html` | Adds OSI cards and table while preserving existing token intelligence cards. Browser verification confirmed visible section, 8 rows, and no console errors. |
| `docs/open-source-candidates.json` | Adds exact registry entries requested by owner, including unknown/search-only candidates that remain `HOLD`. |
| `docs/open-source-intelligence.md` | Documents purpose, registry, decision rules, license/source/token/security policy, dashboard cards, and prompt discipline. |
| `docs/commands.md` | Adds only the `source court` command section. |
| `.github/workflows/pala-memory-core-ci.yml` | Adds offline source court smoke and generated file hygiene check. |

## Evidence Summary
- Offline source court: 8 candidates, 0 PASS, 8 HOLD, 0 REJECT.
- Online metadata check: 3 PASS, 5 HOLD, 0 REJECT.
- Generated ignore: `data/reports/*` and `dashboard/records.json` matched `.gitignore`.
- CI: PR #3 smoke checks passed.

## Risks
- Online PASS relies on current GitHub API metadata and should be reviewed by owner before marking the PR ready.
- Unknown Vibe/search candidates intentionally remain discovery-only.
- Dashboard is a static local view; richer sorting/filtering for OSI candidates is not included in v0.17.

## Court Decision
`OSI_READY_FOR_OWNER_REVIEW`: ready for owner review as a draft PR, not approved for merge or release.
