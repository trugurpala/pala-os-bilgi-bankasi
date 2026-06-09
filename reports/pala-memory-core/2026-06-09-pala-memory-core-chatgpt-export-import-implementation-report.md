# Pala Memory Core ChatGPT Export Import Implementation Report

Date: 2026-06-09
Local repo: `C:\Users\Pala-Home-1\Desktop\Codex\pala-memory-core`
GitHub repo: `https://github.com/trugurpala/pala-memory-core`
Release: `https://github.com/trugurpala/pala-memory-core/releases/tag/v0.5.0-chatgpt-export-import-preview`
Phase: ChatGPT export import preview
Status: PASS for local ChatGPT export import preview

## Summary

Pala Memory Core now includes a local ChatGPT export import connector.

Implemented:

- Added `python pala.py import chatgpt-export <path>`
- Supports `.zip`, folders, `.json`, `.html`, `.md`, and `.txt`
- Splits ChatGPT-style `mapping` JSON conversations into local memory records
- Supports `--project`, `--tag`, `--max-records`, and `--max-chars`
- Handles UTF-8 BOM JSON files
- Keeps generated records ignored by Git
- Published product commit `e61f3c8`
- Published release `v0.5.0-chatgpt-export-import-preview`
- Ran backup connector after import and pushed redacted package to the knowledge bank

## Changed Files

See `2026-06-09-pala-memory-core-chatgpt-export-import-changed-files-manifest.md`.

## Evidence Commands

```powershell
python .\pala.py import chatgpt-export .\data\inbox\chatgpt-export-sample.zip --project trugurpala/pala-memory-core --tag smoke-test --max-records 3 --max-chars 2000
python .\pala.py brief today
python .\pala.py dashboard export
git -C 'C:\Users\Pala-Home-1\Desktop\Codex\pala-memory-core' commit -m 'Add ChatGPT export import preview'
git -C 'C:\Users\Pala-Home-1\Desktop\Codex\pala-memory-core' push origin main
gh release create v0.5.0-chatgpt-export-import-preview --repo trugurpala/pala-memory-core --title 'v0.5.0 ChatGPT Export Import Preview'
python .\pala.py backup github --push
```

Observed import output:

```text
saved 20260609T132447Z-sample-chatgpt-export-conversation
data\records\2026-06-09\20260609T132447Z-sample-chatgpt-export-conversation.md
imported 1 record(s) from C:\Users\Pala-Home-1\Desktop\Codex\pala-memory-core\data\inbox\chatgpt-export-sample.zip
brief saved data\reports\2026-06-09-brief.md
dashboard data saved dashboard\records.json
```

Observed backup output:

```text
github backup package saved C:\Users\Pala-Home-1\Desktop\Codex\pala-os-bilgi-bankasi\reports\pala-memory-core-backups\2026-06-09-20260609T132528Z-pala-memory-core-backup
records=3 artifacts=3 committed=True pushed=True
```

Product commit:

```text
e61f3c8 Add ChatGPT export import preview
```

Knowledge-bank backup commit:

```text
1a57e21 Add Pala Memory Core backup 2026-06-09-20260609T132528Z-pala-memory-core-backup
```

## Status

| Area | Status |
|---|---|
| ChatGPT export import command | PASS |
| ZIP import | PASS |
| ChatGPT-style mapping JSON parsing | PASS |
| BOM-safe JSON decoding | PASS |
| Daily brief refresh | PASS |
| Dashboard export refresh | PASS |
| Knowledge-bank backup after import | PASS |
| Real official export corpus test | PENDING |
| Browser/Playwright capture | PENDING |
| Mobile share/import flow | PENDING |
| Google Drive backup | PENDING |

## Rollback Note

Rollback product changes by reverting commit `e61f3c8` in `trugurpala/pala-memory-core` and deleting release `v0.5.0-chatgpt-export-import-preview`. Rollback the smoke-test backup package by reverting knowledge-bank commit `1a57e21`.

## Release Posture

Suitable for personal prototype use with local export files. Not a complete ChatGPT integration because it does not call ChatGPT APIs, does not automate mobile capture, and has not been validated against a large real official export corpus.

