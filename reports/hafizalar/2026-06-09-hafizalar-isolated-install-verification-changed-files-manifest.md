# Hafizalar Isolated Install Verification Changed Files Manifest

Date: 2026-06-09

Source repo: https://github.com/trugurpala/hafizalar

Source commit: 6aad91cbf44d9240a2b9852133617e3ee56c85f5

Base commit: 7b32aadf8528623ca25570e831ffe4e01e390905

Phase: isolated clone install, ChatGPT-only quick install, README install guidance, and runner maintenance

Status: PASS

## Included Files

| File | Status | Phase Note |
| --- | --- | --- |
| `.npmignore` | New | Controls npm package contents and removes `.gitignore fallback` warning. |
| `.github/workflows/test.yml` | Modified | Uses `windows-2025` instead of `windows-latest`. |
| `README.md` | Modified | Adds fast GitHub npm exec install commands and warning note. |
| `docs/INSTALLATION.md` | Modified | Adds fast install section and expected npm Git dependency warning. |
| `test/hafizalar.test.mjs` | Modified | Adds assertions for `.npmignore`, quick install docs, and warning note. |

## New Files

- `.npmignore`

## Modified Files

- `.github/workflows/test.yml`
- `README.md`
- `docs/INSTALLATION.md`
- `test/hafizalar.test.mjs`

## Excluded Dirty Files

None.

## Tracked Diff Stat

```text
.github/workflows/test.yml |  2 +-
.npmignore                 |  6 ++++++
README.md                  | 19 +++++++++++++++++++
docs/INSTALLATION.md       | 29 +++++++++++++++++++++++++++++
test/hafizalar.test.mjs    |  6 ++++++
5 files changed, 61 insertions(+), 1 deletion(-)
```

## Evidence

- Fresh clone test: PASS.
- Fresh clone installer into isolated project: PASS.
- GitHub npm exec quick install into isolated project: PASS.
- Local tests: PASS, 13/13.
- CI: https://github.com/trugurpala/hafizalar/actions/runs/27194393423 PASS.
