# Pala OS V6 v0-dev Skill Install - Changed Files Manifest

Date: 2026-06-09  
Source repo: `<LOCAL_CODEX_ROOT>\pala-os-v6`  
Phase: v0-dev skill installation  
Status: `PASS` for mutation package scope

## Included Source Files

| Path | Status | Purpose |
| --- | --- | --- |
| `skills/v0-dev/SKILL.md` | New | Skill package definition with metadata, tool guidance, installation, API usage, and operational guardrails for v0. |
| `skills/v0-dev/references/patterns.md` | New | Working patterns for chat prompts, integration flow, and UI import cadence. |
| `skills/v0-dev/references/sharp_edges.md` | New | Common edge cases and risk checkpoints (MCP drift, module boundaries, token mismatch, branch surprises). |
| `skills/v0-dev/references/validations.md` | New | Validation checklist before and after importing generated UI output. |
| `skills/registry/seed-skills.json` | Modified | Adds the `v0-dev` seed entry to make registry discoverable to skills + MCP surfaces. |

## New Source Files

| Path | Purpose |
| --- | --- |
| `skills/v0-dev/SKILL.md` | Main skill specification (`name`, `description`, metadata, usage scope). |
| `skills/v0-dev/references/patterns.md` | Prompt/build pattern guidance for reliable v0 usage. |
| `skills/v0-dev/references/sharp_edges.md` | Known failure modes and mitigation guidance. |
| `skills/v0-dev/references/validations.md` | Output quality and post-import hardening checks. |

## Excluded Dirty Files (Pre-existing)

| Path | Reason |
| --- | --- |
| `.pala/rules/world-standards.json` | Pre-existing workspace dirty state, unrelated to this install action. |
| `docs/oss-upstream-matrix.md` | Pre-existing workspace modification. |
| `docs/world-standards-map.md` | Pre-existing workspace modification. |
| `src/bootstrap.js` | Pre-existing workspace modification. |
| `src/cli.js` | Pre-existing workspace modification. |
| `src/config.js` | Pre-existing workspace modification. |
| `src/dashboard.js` | Pre-existing workspace modification. |
| `src/server.js` | Pre-existing workspace modification. |
| `test/pala-v6.test.js` | Pre-existing workspace modification. |
| `.pala/rules/market-radar.json` | Pre-existing untracked file. |
| `.pala/rules/pala-control-groups.json` | Pre-existing untracked file. |
| `docs/v6-vibe-coder-agent-host-plan.md` | Pre-existing untracked file. |
| `legacy/` | Pre-existing untracked directory. |
| `src/market-radar.js` | Pre-existing untracked file. |
| `src/standard-groups.js` | Pre-existing untracked file. |

## Knowledge-bank Files Added

| Path | Purpose |
| --- | --- |
| `reports/pala-os-v6/2026-06-09-v0-dev-skill-install-implementation-report.md` | Implementation report. |
| `reports/pala-os-v6/2026-06-09-v0-dev-skill-install-repo-change-review.md` | Repo change review package. |
| `reports/pala-os-v6/2026-06-09-v0-dev-skill-install-raw-patch-diff.patch` | Raw patch/diff artifact for this mutation package. |

## Source Commit Scope

- Commit not created in this step.
- Local mutation package is constrained to the included source file list above.

