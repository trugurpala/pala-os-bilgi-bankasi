# Pala OS V6 Command Center Control Groups Changed Files Manifest

Date: 2026-06-09

Source repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-os-v6`

## Included In This Mutation Package

New files:

- `.pala/rules/pala-control-groups.json`
- `src/standard-groups.js`

Modified files:

- `docs/world-standards-map.md`
- `src/bootstrap.js`
- `src/config.js`
- `src/dashboard.js`
- `src/server.js`
- `test/pala-v6.test.js`

## Overlapping Local Files From Earlier Market-Radar Package

These remain part of the current local working tree but were introduced or primarily changed by the earlier market-radar implementation:

- `.pala/rules/market-radar.json`
- `src/market-radar.js`
- `docs/oss-upstream-matrix.md`
- `src/cli.js`

Some shared files also contain both previous market-radar changes and this phase's Command Center changes:

- `src/bootstrap.js`
- `src/config.js`
- `src/dashboard.js`
- `src/server.js`
- `test/pala-v6.test.js`

## Excluded / Pre-Existing Dirty Files

- `.pala/rules/world-standards.json`: line-ending dirty state only in current checks; no content diff was shown.
- `docs/v6-vibe-coder-agent-host-plan.md`: pre-existing untracked plan document.
- `legacy/`: pre-existing untracked legacy/cache content, not included.
- Knowledge-bank repo already had unrelated untracked `reports/pala-memory-core/*v0161*` files; they were not touched or staged by this package.

## Evidence Artifacts

- `.pala/evidence/screenshots/command-center-dashboard-final-clean.png`
- Placeholder screenshot output also exists from the local `sak screenshot` command because Playwright is not installed in this runtime; real visual verification used Chrome headless.

## Release Posture

Local implementation verified, source release blocked. No source repo commit, push, or release approval was performed.
