# Hafizalar Codex + ChatGPT Installer Changed Files Manifest

Date: 2026-06-09

Source repo: https://github.com/trugurpala/hafizalar

Source commit: 3e6a076ede6ae655d450edf6cac69c0e67be9743

Phase: Codex and ChatGPT install package

Status: PASS

## Included Files

| File | Status | Phase Note |
| --- | --- | --- |
| `HAFIZALAR-CHATGPT.md` | New | Adds ChatGPT-specific Hafizalar contract and handoff behavior. |
| `README.md` | Modified | Adds ChatGPT contract pointer, install commands, and Codex vs ChatGPT limits note. |
| `docs/OPENAI-SURFACE-LIMITS.md` | New | Documents separate Codex and ChatGPT working limits using official OpenAI Help Center sources. |
| `package.json` | Modified | Adds `install:hafizalar` script. |
| `scripts/install-hafizalar.mjs` | New | Node installer for `.hafizalar` project setup. |
| `scripts/install-hafizalar.ps1` | New | PowerShell wrapper for Windows usage. |
| `test/hafizalar.test.mjs` | Modified | Adds tests for ChatGPT contract, limits doc, README installer references, and installer behavior. |

## New Files

- `HAFIZALAR-CHATGPT.md`
- `docs/OPENAI-SURFACE-LIMITS.md`
- `scripts/install-hafizalar.mjs`
- `scripts/install-hafizalar.ps1`

## Modified Files

- `README.md`
- `package.json`
- `test/hafizalar.test.mjs`

## Excluded Dirty Files

None.

## Tracked Diff Stat

```text
HAFIZALAR-CHATGPT.md          | 159 +++++++++++++++++++++++++++++++++++++++++
README.md                     |  49 +++++++++++++
docs/OPENAI-SURFACE-LIMITS.md |  76 ++++++++++++++++++++
package.json                  |   1 +
scripts/install-hafizalar.mjs | 161 ++++++++++++++++++++++++++++++++++++++++++
scripts/install-hafizalar.ps1 |  22 ++++++
test/hafizalar.test.mjs       |  71 ++++++++++++++++++-
7 files changed, 538 insertions(+), 1 deletion(-)
```

## Evidence

- Local tests: `npm.cmd test` PASS, 10/10.
- Installer smoke: npm script and PowerShell wrapper PASS.
- CI: https://github.com/trugurpala/hafizalar/actions/runs/27192226686 PASS.
