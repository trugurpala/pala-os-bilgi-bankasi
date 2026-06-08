# Phase C Scope Files Manifest

Date: 2026-06-08
Source repo: `trugurpala/pala-os-v6`
Report: `2026-06-08-phase-c-final-mutation-scope.md`
Mode: read-only scope report

## Source Repo Changed Files

None.

This report did not mutate `trugurpala/pala-os-v6`.

## Knowledge Bank Files Added

- `reports/pala-os-v6/2026-06-08-phase-c-final-mutation-scope.md`
- `reports/pala-os-v6/2026-06-08-phase-c-scope-files-manifest.md`

## Proposed Phase C Mutation Files

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
- `docs/legacy-boundary-contract.md` if owner wants a written boundary contract

## Legacy Areas Reviewed

- `legacy/pala-os`
- `legacy/pala-os-v3`
- `legacy/pala-os-v4`
- `docs/legacy/**`
- `skills/registry/legacy-skills-index.json`
- Dockerfile / compose / package / CI surfaces
- Dashboard / server / bootstrap / skill registry surfaces

## Evidence Commands Used For Scope

```powershell
Get-ChildItem -Path legacy -Directory -Force
Get-ChildItem -Path docs\legacy -Directory -Force
rg "legacy/|legacy\\|legacy-skills-index|docs/legacy|LEGACY" src scripts test .github package.json Dockerfile compose.yaml .codex-plugin docs
git ls-files legacy docs/legacy skills/registry/legacy-skills-index.json
rg "loadLegacy|legacy-skills|LEGACY_SKILLS_INDEX_PATH|SEED_SKILLS_PATH|skills registry|seed-skills|legacy" src/skill-registry.js src/bootstrap.js src/server.js src/dashboard.js src/cli.js src/config.js src/source-court.js
```

## Reviewer Should Check

- Is `legacy/**` strictly quarantine?
- Is Docker build context protected?
- Does dashboard avoid direct legacy reads?
- Does skill registry stay seed-only by default?
- Does Source Court still retain explicit legacy access?
- Does release remain `RELEASE_BLOCKED`?

Kanıtlanan durum budur.
RELEASE_BLOCKED.
