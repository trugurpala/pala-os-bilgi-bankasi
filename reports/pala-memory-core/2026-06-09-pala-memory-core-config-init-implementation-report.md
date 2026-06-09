# Pala Memory Core Config Init Implementation Report

Date: 2026-06-09
Source repo: `trugurpala/pala-memory-core`
Source commit: `0c9334bc1dd3d987440c393c71a5b8365f2164d4`
Release: `v0.15.0-config-init-preview`
GitHub release: https://github.com/trugurpala/pala-memory-core/releases/tag/v0.15.0-config-init-preview
Knowledge-bank backup commit: `86800aecd0ec7cdc30a5a68756331b6ef4310b9f`

## Phase

Local config/init preview.

## Status

PASS for config creation, ignored local config, committed example config, config-driven path defaults, config-aware doctor, config-driven backup/report/dashboard behavior, product release, and knowledge-bank publication.

## Summary

This change adds `python pala.py init`, which writes a local `pala.config.json` and creates local data folders. The config stores default paths for:
- Knowledge-bank repo
- Drive-folder backup target
- Mobile share folder
- Dashboard host
- Dashboard port

Path precedence is:

```text
CLI argument > environment variable > pala.config.json > built-in default
```

`pala.config.json` is intentionally ignored by Git. `pala.config.example.json` is committed as a template.

## Changed Files

Included in mutation package:
- `.gitignore`
- `pala.py`
- `pala.config.example.json`
- `README.md`
- `INSTALL.md`
- `docs/backlog.md`
- `docs/commands.md`
- `docs/roadmap.md`
- `docs/v0.1-acceptance.md`
- `docs/v0.15-config-init.md`

New files:
- `pala.config.example.json`
- `docs/v0.15-config-init.md`

Excluded or pre-existing dirty files:
- `pala.config.json` is ignored and user-specific.
- Generated runtime data under `data/` and `dashboard/records.json` remained ignored by `.gitignore`.

## Evidence Commands

Executed in `C:\Users\Pala-Home-1\Desktop\Codex\pala-memory-core`:

```powershell
python -m py_compile .\pala.py
python -m json.tool .\pala.config.example.json
python .\pala.py init --force --knowledge-bank <repo> --drive-target <folder> --mobile-share <folder> --dashboard-port 8799 --create-targets
git status --short --ignored pala.config.json pala.config.example.json .gitignore
python .\pala.py backup drive --all
python .\pala.py backup github --all --push
python .\pala.py report vault --all --json
python .\pala.py doctor --strict
python .\pala.py dashboard serve
python .\pala.py backup github --all --push
```

Observed key output:

```text
config saved pala.config.json
!! pala.config.json
?? pala.config.example.json
PASS | config           | Config file | pala.config.json
PASS | config           | Config version | version=1
PASS | knowledge-bank   | Knowledge-bank repo | <configured repo>
PASS | drive            | Drive folder target | <configured folder>
status=200 stopped=<pid>
records=8 artifacts=3 committed=True pushed=True
```

## Rollback Note

Rollback the product change with:

```powershell
git revert 0c9334bc1dd3d987440c393c71a5b8365f2164d4
git push origin main
git push origin :refs/tags/v0.15.0-config-init-preview
```

The knowledge-bank report is append-only and should be corrected with a new addendum rather than overwritten.

## Release Posture

Preview release. The config is local and ignored. It does not install dependencies or create remote GitHub/Drive resources automatically.
