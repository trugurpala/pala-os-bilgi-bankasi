# CI Source Court Audit Fix - Changed Files Manifest

Date: 2026-06-08

Source repo: `trugurpala/pala-os-v6`

Source branch: `codex/v6-source-card-gate-radar`

Source PR: `#1 Strengthen V6 source-card gate radar`

Source fix commit: `32362b5626b7f3264c49f3676343389c009e407f`

## Mutation Package

Included source files:

```text
.github/workflows/pala.yml
docs/inheritance-backlog.json
src/source-court.js
test/pala-v6.test.js
```

## New Files

```text
NONE
```

## File Notes

```text
.github/workflows/pala.yml
  Logs Source Court audit status and blockedFiles, and fails explicitly when blockedFiles > 0.

docs/inheritance-backlog.json
  Adds a machine-readable source card for the adapted V6 world-standard governance document.

src/source-court.js
  Merges local SQLite source cards with default source cards from inheritance backlog for clean checkout audits.

test/pala-v6.test.js
  Adds regression coverage for clean-checkout source-card lookup and workflow blockedFiles guard.
```

## Excluded / Pre-existing Dirty Files

The following file remains outside the mutation package:

```text
docs/v6-vibe-coder-agent-host-plan.md
```

It remains untracked in the source repo and was not staged, committed, or pushed.

## Diff Stat

```text
4 files changed, 117 insertions(+), 1 deletion(-)
```

## Source Repo Post-Push State

```text
## codex/v6-source-card-gate-radar...origin/codex/v6-source-card-gate-radar
?? docs/v6-vibe-coder-agent-host-plan.md
```

## Boundaries

Main direct push: `NO`

PR merge: `NO`

Release: `NO`

Deploy: `NO`

New feature: `NO`

New dashboard surface: `NO`

Source branch push: `YES`
