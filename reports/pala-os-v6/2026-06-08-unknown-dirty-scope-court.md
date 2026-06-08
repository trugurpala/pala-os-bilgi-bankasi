# Unknown Dirty Scope Court

## Rule

Unknown files cannot enter the hardening PR. A file must be tied to Phase A/C/B/D/E, explicitly owner-approved as governance/core hardening, or moved to a separate PR.

## Court table

| File | Current Status | Origin Guess | Related Phase | Decision | Include In PR? | Reason |
|---|---|---|---|---|---|---|
| `README.md` | Modified | Documents `core audit`, `/api/environment-limits`, `/api/operator-actions`, `/api/core-foundation` | Unknown / active radar bundle | `NEEDS_OWNER_APPROVAL` | Conditional | It documents active untracked governance/core radar endpoints, but that radar bundle was not cleanly authorized inside Phase A/C/B/D/E. |
| `docs/inheritance-backlog.json` | Modified | Adds source court decision for adapted governance doc | Phase A | `INCLUDE_IN_HARDENING_PR` | Yes | It supports Phase A Source Court provenance for `docs/v6-dunya-standardi-karargah-tr.md`. |
| `docs/v6-dunya-standardi-karargah-tr.md` | Modified | Adapted governance doc from legacy Pala source | Phase A | `INCLUDE_IN_HARDENING_PR` | Yes | It has a source stamp and is part of Source Court hardening. |
| `docs/v6-vibe-coder-agent-host-plan.md` | Untracked | Product/agent-host planning document | None proven | `NEEDS_SEPARATE_PR` | No | It is a product/agent-host plan, not required for Source Court, Legacy Boundary, GitHub Governance, Docker/MCP proof, or Dashboard Truth. |
| `src/core-foundation.js` | Untracked | Core foundation radar module | Unknown / governance core | `NEEDS_OWNER_APPROVAL` | Conditional | It is active code imported by the current state/dashboard flow, but its origin is outside the approved Phase A/C/B/D/E package. |
| `src/environment-limits.js` | Untracked | Environment/provider limit radar module | Unknown / governance core | `NEEDS_OWNER_APPROVAL` | Conditional | It is active dashboard/API state code, but not proven as part of the hardening phases. |
| `src/operator-actions.js` | Untracked | Operator action/token economy queue module | Unknown / governance core | `NEEDS_OWNER_APPROVAL` | Conditional | It is active dashboard/API state code, but needs explicit owner acceptance before entering hardening PR. |

## Include list

Approved for hardening PR:

- `docs/inheritance-backlog.json`
- `docs/v6-dunya-standardi-karargah-tr.md`

Conditional owner approval needed:

- `README.md`
- `src/core-foundation.js`
- `src/environment-limits.js`
- `src/operator-actions.js`

Exclude from hardening PR:

- `docs/v6-vibe-coder-agent-host-plan.md`

## Impact

PR readiness remains blocked until the owner decides whether the active radar bundle is included in the hardening PR or extracted/removed before commit.

Court result: `BLOCKED_WITH_REASON`.

Reason: unknown active source files cannot be committed without owner decision.

Kanıtlanan durum budur.
RELEASE_BLOCKED.
