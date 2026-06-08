# Phase E Implementation Report - Dashboard Truth Contract

## 1. Degisen dosyalar

- `src/policy.js` - `buildDashboardTruthContract()` eklendi; panel bazli truth status, fallback, evidence, risk ve estimated alanlari makine-okunur hale getirildi.
- `src/bootstrap.js` - en son Docker smoke evidence okunup app state'e eklendi; dashboard truth contract state uretiminin parcasina alindi.
- `src/server.js` - `/api/health` dashboard truth status, truth summary ve source stamp gate ozetini donuyor.
- `src/dashboard.js` - dashboard HTML icinde Truth Contract tablosu render ediliyor; token economy tahminse `estimated` olarak gosteriliyor.
- `test/pala-v6.test.js` - fake-green kontrolleri, `/api/state` contract testi, Docker PASS engeli, raw legacy sizinti testi ve release blocked testi eklendi.
- `docs/dashboard-truth-contract.md` - panel truth table ve status sozlesmesi eklendi.

## 2. Yeni dosyalar

- Source repo: `docs/dashboard-truth-contract.md`
- Bilgi bankasi artefactlari:
  - `2026-06-08-phase-e-implementation-report.md`
  - `2026-06-08-phase-e-changed-files-manifest.md`
  - `2026-06-08-phase-e-repo-change-review.md`
  - `2026-06-08-phase-e-raw-patch-diff.patch`

## 3. Panel truth table

| Panel | Data Source | Evidence Source | Fallback State | PASS Condition | Truth Risk |
|---|---|---|---|---|---|
| Overview | `buildAppState.summary + court + sourceStampGate` | SQLite evidence counts, source cards, ledger, court | `RELEASE_BLOCKED` | Court not blocked, source gate `PASS`, ledger has evidence | Overview can hide child blockers |
| Mission Control | `route`, `nextActions`, `jobRuns`, `runs` | SQLite command/job runs | `NOT_AVAILABLE_WITH_REASON` | Mission/run ledger proves active mission | Route text can look decisive without evidence |
| CI Court | GitHub bridge/audit state | GitHub CLI/API readback and workflow runs | `NOT_AVAILABLE_WITH_REASON` | Governance readback and required checks proven | CI green can fake governance |
| Evidence Center | `ledger`, `sourceCards`, `evidenceSprint` | SQLite ledger and source-card table | `PARTIAL` | Ledger and source cards both present | Empty evidence must never PASS |
| Source Court | sanitized Source Court audit | Source Court summary and sourceStampGate | `NOT_AVAILABLE_WITH_REASON` | Source stamp gate `PASS` | Raw legacy files must not leak |
| Skill Registry | seed skill registry | `skills/registry/seed-skills.json` | `NOT_AVAILABLE_WITH_REASON` | Seed registry loads, legacy index not default | Legacy index can become active by mistake |
| MCP Health | MCP registry and stdio proof | MCP health CLI/test evidence | `NOT_AVAILABLE_WITH_REASON` | Live MCP proof attached to state | Registry is not live health |
| Docker Boot | latest `.pala/evidence/docker` smoke JSON | Docker version, compose build/up/health/down | `NOT_AVAILABLE_WITH_REASON` | daemon available, compose build/up/health/down pass | compose config alone is not runtime proof |
| Benchmark Radar | `benchmark/benchmark-state.json` | benchmark categories and counts | `NOT_AVAILABLE_WITH_REASON` | fixture-backed suite has no blocked category | placeholder benchmark can look like proof |
| Token Economy | `tokenBudget`, `tokenSnapshots` | SQLite token snapshots or estimate | `PARTIAL` | measured accounting exists | estimate can be mistaken for metric |
| Release Court | `evaluateCourt()` | owner approval, standards, source cards, ledger, source gate | `RELEASE_BLOCKED` | owner approval and no release blockers | release must never green without owner |

## 4. `/api/state` sonucu

Canli server kaniti:

```json
{
  "stateStatus": "RELEASE_BLOCKED",
  "statePanelCount": 11,
  "dockerPanel": "NOT_AVAILABLE_WITH_REASON",
  "sourcePanel": "PARTIAL",
  "releasePanel": "RELEASE_BLOCKED",
  "tokenEstimated": true,
  "legacyRawFilesExposed": false,
  "overallNotGreenerThanPanels": true
}
```

## 5. `/api/health` sonucu

```json
{
  "healthOk": true,
  "healthCourt": "RELEASE_BLOCKED",
  "healthTruthStatus": "RELEASE_BLOCKED",
  "healthSourceStampGate": "PARTIAL"
}
```

## 6. Dashboard fake-green kontrolleri

- Docker daemon kaniti yokken Docker Boot paneli `PASS` donmuyor.
- Source Court gate `PARTIAL` iken Source Court paneli `PARTIAL` kaliyor.
- Owner approval yokken Release Court ve overall dashboard `RELEASE_BLOCKED`.
- `sourceCourtAudit.files` dashboard state icinde expose edilmiyor.
- Bos evidence senaryosu `PASS` alamiyor.
- Unknown external state `NOT_AVAILABLE_WITH_REASON`.
- Token economy `estimated: true`.
- Overall status child panellerden daha yesil olamiyor.

## 7. Test sonucu

`npm.cmd test`:

```text
tests 37
pass 37
fail 0
```

## 8. Court sonucu

`node src/cli.js court`:

```text
decision: RELEASE_BLOCKED
reason: owner approval missing; 0 required standard(s) still blocked; source cards present; ledger has records; source stamp gate PARTIAL
sourceStampGate: PARTIAL
ledgerRecordsCount: 250
```

## 9. Kalan blockerlar

- Release owner approval yok: `RELEASE_BLOCKED`.
- Source Stamp Gate genel durum `PARTIAL`: governance/reference audit metadata izleniyor.
- Docker build/up container proof hala Docker daemon olmadigi icin Phase D'den `NOT_AVAILABLE_WITH_REASON`.
- Branch protection Phase B'de aktif, ancak solo-owner review deadlock riski hala governance riski.

## 10. Phase E sonucu

Phase E Dashboard Truth Contract: `PASS`.

Urun release durumu: `RELEASE_BLOCKED`.

## 11. Sonraki oneri

Bir sonraki is, accumulated Phase A/C/B/D/E local mutation setini owner review paketinden gecirmek ve uygun gorulurse kaynak repoda PR akisini baslatmaktir. Docker daemon kaniti alinmadan Docker/D release iddiasi `PASS` sayilmamalidir.

Kanıtlanan durum budur.
RELEASE_BLOCKED.
