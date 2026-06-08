# Phase C Final Mutation Scope - Legacy Boundary Hardening

Date: 2026-06-08
Source repo: `trugurpala/pala-os-v6`
Mode: read-only scope report
Release posture: `RELEASE_BLOCKED`

## Executive Summary

Phase A was accepted.

Evidence:

- Source Court validator implemented.
- Tests PASS: 28/28.
- Source stamp gate: `PARTIAL`.
- Release-blocking source stamp failures: `0`.
- Release remains `RELEASE_BLOCKED`.

Phase C prepares Legacy Boundary Hardening. The goal is to prevent `legacy/**` from leaking into runtime, dashboard, Docker, package, test, skill registry, MCP, or default agent context. Legacy must remain readable only by Source Court and explicit audit/migration commands.

No source repo mutation was performed for this scope report.

## 1. Legacy Areas

| Area | Evidence | Risk | Decision |
|---|---:|---|---|
| `legacy/pala-os` | 1859 files, 91.48 MB | Large archive can pollute Docker context, token context, test discovery, and active product assumptions. | `QUARANTINE` |
| `legacy/pala-os-v3` | 278 files, 0.53 MB | Old agent, skill, and workflow patterns can be mistaken for active runtime. | `QUARANTINE` |
| `legacy/pala-os-v4` | 5 files, 0.51 MB | Old runtime state can be mistaken for current truth. | `QUARANTINE` |
| `docs/legacy/**` | 26 tracked files, about 126 KB | Historical docs can be mistaken for release evidence. | `REFERENCE_ONLY` |
| `skills/registry/legacy-skills-index.json` | 881.5 KB, 489 skills | If loaded by default, Pala OS drifts into a legacy skill repository. | `IMPORT_LATER` |

Git evidence:

- `git ls-files legacy`: 2082 tracked files.
- `git ls-files docs/legacy`: 26 tracked files.
- `git ls-files skills/registry/legacy-skills-index.json`: 1 tracked file.

## 2. Allowed Readers

Only these surfaces may read legacy content:

- `src/source-court.js` in explicit Source Court/provenance mode.
- `node src/cli.js source audit --json`.
- `node src/cli.js legacy audit --path ...`.
- `node src/cli.js legacy archive --path ...`.
- `node src/cli.js legacy skills index --path ...`.
- `scripts/pala_single_source_cleanup.ps1`.
- Tests that explicitly prove boundary behavior.

## 3. Forbidden Readers

These surfaces must not read `legacy/**` directly:

- Runtime boot/default `buildAppState`.
- Dashboard truth layer.
- Docker image/package surface.
- Default test discovery.
- Active skill loader.
- MCP/default agent context.
- API endpoints except sanitized Source Court summary.

## 4. Boundary Policy

Policy:

- `legacy/**` is not production surface.
- `legacy/**` is excluded from default build, test, Docker, package, dashboard, and agent context.
- `docs/legacy/**` is reference-only and cannot be release evidence.
- Legacy may be read only by explicit Source Court or migration/audit commands.
- No legacy deletion in Phase C.

Expected status language:

- Legacy archive: `QUARANTINE`
- Active surface: `PASS` only when clean
- Unknown legacy health: `NOT_AVAILABLE_WITH_REASON`
- Missing evidence: `PARTIAL`
- Release: `RELEASE_BLOCKED`

## 5. Build/Test/Package/Docker Ignore Strategy

Required implementation plan:

- Add `.dockerignore`.
- Exclude `legacy/**` from Docker build context.
- Exclude `docs/legacy/**` from Docker build context unless explicit evidence bundle mode is introduced later.
- Exclude `.pala/**`, `node_modules/**`, `dist/**`, `coverage/**`.
- Exclude `skills/registry/legacy-skills-index.json` from Docker runtime image by default.
- Keep `package.json` test script scoped to `node --test test/pala-v6.test.js`.
- Add CI boundary scan before or beside tests.

Current important finding:

- There is no `.dockerignore`.
- Dockerfile does not copy root `legacy/**`, but Docker build context can still send it.
- Dockerfile copies `docs` and `skills`, so `docs/legacy/**` and `legacy-skills-index.json` can enter the image unless Phase C blocks them.

## 6. Dashboard Source Boundary

Current evidence:

- `src/dashboard.js` has no direct `legacy` path reads.
- `src/server.js` exposes dashboard/API state from `buildAppState`.
- `buildAppState` currently builds Source Court state, which can scan legacy.

Required plan:

- Dashboard must not read root `legacy/**` directly.
- Dashboard must show only sanitized `sourceStampGate` and Source Court summary.
- Dashboard must not use `docs/legacy/**` as release evidence.
- Unknown explicit legacy audit state must render `NOT_AVAILABLE_WITH_REASON`, not green.

## 7. Skill Registry Boundary

Current evidence:

- Active loader in `src/skill-registry.js` reads `SEED_SKILLS_PATH`.
- `LEGACY_SKILLS_INDEX_PATH` exists in config but is used by explicit legacy skill index tooling.
- `skills/registry/legacy-skills-index.json` contains 489 legacy skills and must not be default-loaded.

Required plan:

- Add tests proving `loadSeedSkillRegistry()` never reads `LEGACY_SKILLS_INDEX_PATH`.
- `/api/skills`, MCP skill tools, and dashboard skill registry must expose seed registry only.
- Legacy skills remain `IMPORT_LATER` or `REFERENCE_ONLY`.

## 8. Import / Reference Scan Plan

Required evidence commands after implementation:

```powershell
rg "legacy/" src scripts test .github package.json Dockerfile compose.yaml
rg "legacy-skills-index" src skills test package.json
rg "legacy" src/dashboard.js src/server.js src/bootstrap.js
git ls-files legacy docs/legacy skills/registry/legacy-skills-index.json
node src/cli.js source audit --json
npm.cmd test
```

Optional Docker proof after implementation:

```powershell
docker build --no-cache -t pala-os-v6:phase-c .
```

## 9. Required Tests

Required test cases:

1. `legacy/**` is not active surface.
2. Source Court explicit mode can read legacy.
3. Dashboard profile does not read root legacy directly.
4. Skill loader does not load `legacy-skills-index.json` by default.
5. Docker/package/test surface does not treat legacy as production input.
6. Release remains `RELEASE_BLOCKED`.

## 10. Risks

- Over-excluding legacy can break Source Court provenance analysis.
- Under-excluding legacy can pollute Docker, token context, tests, and dashboard truth.
- Deleting legacy loses provenance and old work. Phase C must not delete.
- Dashboard can still create fake green if it shows legacy decisions without evidence-state distinction.
- Legacy skill index is large enough to distort agent context if loaded by default.

## 11. Rollback Plan

- No deletion.
- Revert `.dockerignore` if Docker/source-court evidence mode is accidentally blocked.
- Revert source boundary config if explicit Source Court read breaks.
- Keep `legacy/**`, `docs/legacy/**`, and `legacy-skills-index.json` in place.
- If tests fail, restore previous Source Court explicit legacy read path first.

## 12. Phase C Expected Result

Expected outcome:

- Legacy archive: `QUARANTINE`.
- Active product surface: clean.
- Legacy access: Source Court / explicit audit only.
- Dashboard: sanitized Source Court summary only.
- Skill registry: seed-only by default.
- Docker context: no legacy archive by default.
- Release remains `RELEASE_BLOCKED`.

## Proposed Mutation Files

Expected modified files:

- `.github/workflows/pala.yml`
- `src/config.js`
- `src/source-court.js`
- `src/bootstrap.js`
- `src/cli.js`
- `src/dashboard.js`
- `src/server.js`
- `src/skill-registry.js`
- `test/pala-v6.test.js`

Expected new files:

- `.dockerignore`
- optionally `docs/legacy-boundary-contract.md`

## Review Order

1. Read changed/scope manifest.
2. Read this scope report.
3. Check proposed mutation files.
4. Approve or correct Phase C execution.

Final:

Kanıtlanan durum budur.
RELEASE_BLOCKED.
