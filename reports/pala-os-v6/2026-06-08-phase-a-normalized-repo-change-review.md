# Phase A Normalized Repo Change Review

## Review stance

This review covers the Phase A Source Court hardening package after normalization. It is a review-completeness artefact, not a new implementation pass.

## Intended behavioral effect

- Active files receive deterministic classification.
- Legacy-derived active code cannot PASS without source stamp, source card, court decision, validator link, and required fields.
- Governance docs are tracked as `GOVERNANCE_DOC`, not silently downgraded to `REFERENCE_ONLY`.
- Reference-only material cannot be release evidence.
- Dashboard/court can read a machine-readable `sourceStampGate`.
- Release remains owner-controlled and `RELEASE_BLOCKED`.

## Evidence

| Evidence | Result |
|---|---|
| Source audit status | `PARTIAL` |
| Active files | `88` |
| Blocked files | `0` |
| Partial files | `56` |
| Governance docs | `31` |
| Legacy adapted | `1` |
| OSS adapted | `0` |
| PALA original | `31` |
| Reference only | `26` |
| Test suite | `37/37 PASS` |
| Court | `RELEASE_BLOCKED` |

## Risks

- The current dirty worktree combines multiple phases, so shared-file raw diff cannot be treated as a clean Phase A-only commit diff.
- Source stamp gate remains `PARTIAL`; this is acceptable only because current gaps are non-release-blocking governance/reference metadata.
- `docs/v6-dunya-standardi-karargah-tr.md` is adapted governance content and must stay tied to its source stamp and source court decision.
- Unknown dirty files must not enter the hardening PR without owner decision.

## Rollback plan

If Phase A must be reverted from a future PR:

1. Remove `src/source-court.js`.
2. Remove `docs/source-stamp-contract.md`.
3. Revert Source Court path/config additions from `src/config.js`.
4. Revert `sourceStampGate` policy/court integration from `src/policy.js`.
5. Revert app-state integration from `src/bootstrap.js`.
6. Revert CLI source audit command from `src/cli.js`.
7. Remove Phase A tests from `test/pala-v6.test.js`.
8. Revert Phase A source-court entries from `docs/inheritance-backlog.json` and `docs/v6-dunya-standardi-karargah-tr.md`.
9. Run `npm.cmd test`, `node src/cli.js source audit --json`, and `node src/cli.js court`.

## Court decision

Phase A normalized review package: `PASS`.

Phase A runtime gate: `PARTIAL`.

Product release: `RELEASE_BLOCKED`.
