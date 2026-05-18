# Phase 2B Approval Review

## Executive Summary

Verdict: approve.

Phase 2B is coherent, scoped, and aligned with the locked architecture. It adds the missing operational databases without introducing a 6th database, extra hub, dashboard storage, Notion execution, or Phase 3 work. The only build-sensitive issue is that Releases DB is intentionally spec-only until a real release window exists, so the manual Notion build must not create premature placeholder relations.

## What Phase 2B Adds

Sessions DB adds a low-friction event log for completed creative work. It records what type of session happened, when it happened, and which Song it advanced. It gives Songs DB the approved `Sessions Count` reward signal without turning sessions into tasks.

Releases DB adds a release-planning spec for Singles, EPs, and Albums. It tracks release status, release date, distribution/publishing readiness, promo readiness, linked Songs, and linked release Tasks. It is designed now but built in Notion only when a real release is about 60 days out.

Tasks DB adds the global execution layer across hubs. It tracks actionable work by type, status, `Focus`, priority, due date, optional Song, and optional Release. `Focus` is the core daily execution signal and stays separate from due-date planning.

## Final Property Counts

| Database | Data-entry properties | Formulas | Rollups | Relations | Total properties specified |
|---|---:|---:|---:|---:|---:|
| Sessions DB | 7 | 1 | 0 | 1 | 9 |
| Releases DB | 11 | 2 | 2 | 2 | 17 |
| Tasks DB | 7 | 2 | 0 | 2 | 11 |

Notes:

- Sessions DB data-entry count includes `Name` as the required Notion Title property, but manual naming is not part of the intended workflow.
- Tasks DB `Days Until Due` is optional/deferable; if deferred, Tasks DB starts at 10 total specified properties.
- Releases DB is a written spec until the first real release window.

## Critical Guardrails Check

| Guardrail | Result |
|---|---|
| No 6th database | Pass |
| No extra hub | Pass |
| No Sessions Status property | Pass |
| No Sessions-to-Writing-Assets relation | Pass |
| No Recent Sessions dashboard widget | Pass |
| No dashboard content storage | Pass |
| No Weekly Review before 14 days of real use | Pass |
| No CRM / finance / touring / collaborator / sample library / deep analytics expansion | Pass |

## Build Now vs Defer

| Item | Build now / defer | Reason | Trigger for revisiting |
|---|---|---|---|
| Sessions DB schema | Build now | Core Phase 2B database; gives immediate session logging structure. | N/A |
| Sessions-to-Songs relation | Build now | Required for session history and approved `Sessions Count`. | N/A |
| Sessions `Auto Name` formula | Build now | Reduces manual naming friction. | Revise only if Notion display behavior makes it confusing. |
| Songs `Sessions Count` rollup | Build now after Sessions DB exists | Approved exception; rewards session logging. | N/A |
| Sessions optional fields | Build now but hide below fold | Useful when wanted, but should not slow logging. | Remove/hide further if logging takes over 10 seconds. |
| Sessions Status property | Do not build | Sessions are event records, not tasks. | Only revisit if a separate future planning workflow is approved, likely in Tasks DB instead. |
| Sessions-to-Writing-Assets relation | Do not build | High-friction manual linking with no workflow return. | Only revisit if real usage proves song-level lineage is insufficient. |
| Tasks DB schema | Build now | Global execution layer needed before dashboard design. | N/A |
| Tasks `Focus` checkbox | Build now | Core daily execution filter, separate from Due Date. | N/A |
| Tasks `Overdue` formula | Build now | Supports dated task cleanup and deadline awareness. | N/A |
| Tasks `Days Until Due` formula | Defer / optional | Sorting aid, not approval-critical. | Build if dated tasks become common. |
| Tasks-to-Songs relation | Build now | Required for production task context. | N/A |
| Tasks-to-Releases relation | Defer activation | Releases DB does not exist yet if release window is not active. | Activate when Releases DB is built. |
| Releases DB written spec | Build now as documentation | Prevents future release-system drift. | N/A |
| Releases DB actual Notion database | Defer | Avoids empty release infrastructure before a real release window. | Build when a release is about 60 days out. |
| Releases formulas and rollups | Defer until Releases DB exists | They depend on real release data and relations. | Build with Releases DB. |
| Last Session rollup | Defer | Less urgent than `Sessions Count`; needs real session history. | Day 30+ or 10+ logged sessions. |
| Open Tasks Count rollup on Songs | Defer | Avoids empty rollup clutter. | Real active task volume or Day 30+. |
| Asset Count rollup on Songs | Defer | Needs meaningful Writing Assets volume. | 30+ Writing Assets. |
| Days Stale / Stale Warning formulas | Defer | Needs real session behavior to avoid false urgency. | Day 30+ after Last Session exists. |
| Recent Sessions dashboard widget | Do not build | Historical, not actionable. | Do not revisit for Phase 3; use `Songs in Production` instead. |

## Notion Build Risk

| Risk | Why it matters | Exact prevention step |
|---|---|---|
| Confusing `Name` vs `Auto Name` in Sessions DB | Notion requires a Title property, but manual session naming is intentionally avoided. | Keep `Name` as plain Title, add `Auto Name` as Formula, and make views show `Session Type`, `Date`, `Song`, and `Auto Name` rather than asking for manual title entry. |
| Too many visible Sessions fields | Session logging fails if it feels like a form. | In the default Session template, keep only `Session Type`, `Date`, and `Song` visible/prominent. Put `Duration`, `Energy`, `Key Win`, and `Next Step` below the fold. |
| Accidentally adding Sessions Status | This turns an event log into a task system. | Before creating Sessions DB properties, check the property list against the QA file and explicitly skip `Status`. |
| Accidentally creating Sessions-to-Writing-Assets relation | Adds post-session maintenance and violates the source decision. | Only create one Sessions relation: `Song`. Put created assets in page body notes if needed. |
| Creating Releases DB too early | Empty release infrastructure adds clutter and untested formulas. | Keep Releases DB as documentation until a release is about 60 days out. Do not create the Notion DB during initial build unless that trigger is true. |
| Creating a placeholder `Release` relation in Tasks before Releases DB exists | Placeholder relations are easy to misname or rebuild incorrectly later. | Document `Release` in Tasks DB now, but only create the actual relation when Releases DB exists. |
| Miscounting `Focus` as a deadline substitute | Focus and Due Date solve different problems. | Use `Focus = true` for current execution priority. Use `Due Date` only for real deadlines. |
| Overusing `Priority` instead of `Focus` | A High priority backlog can still become ignored. | Build the default task view around `Focus = true`, not Priority. |
| Building deferred Songs rollups too early | Empty rollups create schema noise and weak trust in the system. | Build only the approved `Sessions Count` early. Hold `Last Session`, `Open Tasks Count`, and `Asset Count` until their triggers. |
| Formula syntax mismatch during manual Notion build | Notion formula syntax can be picky and may differ from the written intent. | Treat formulas as intent specs first. Build the simplest Notion formula that produces the stated output, then test with one sample record. |
| `Brand / Website` naming inconsistency | Source audit used `Brand`; handoff requires `Brand / Website`. | Use the Phase 2B schema value exactly: `Brand / Website`. |
| Release status versus Song status confusion | Releases and Songs have separate lifecycle states. | Keep release states only in Releases DB; do not mirror them into Songs except normal Song Status transitions like `Released`. |

## Approval Recommendation

Approve Phase 2B as-is.

No existing Phase 2B docs need revision. The package is strict enough to build from, and the remaining risks are manual-build execution risks rather than schema contradictions.

## If Approved, Next Prompt

```text
Phase 2B is approved.

Do not execute in Notion yet.
Do not use a Notion API.

Start Phase 3 as a local documentation/spec task only.

Read:
- CODEX_HANDOFF.md
- docs/phase-2b-approval-review.md
- docs/phase-2b-sessions-releases-tasks-schema.md
- docs/relation-build-order.md
- docs/formula-rollup-map.md
- docs/deferred-properties-log.md
- docs/phase-3-readiness-brief.md

Produce the Phase 3 Master Dashboard and navigation implementation package in markdown.

Preserve these guardrails:
- Master Dashboard contains filtered views only.
- No raw notes, standalone records, archive content, embedded documents, or long-form writing lives directly on the dashboard.
- No Recent Sessions dashboard widget.
- No extra database.
- No extra hub.
- Production Hub remains dashboard sections only: Songs in Production and Production Tasks.
- Brand remains one compact Brand Reference Page.
- FL Studio Plugin Command Center remains external sibling/reference only.
- Do not create a Weekly Review template before 14 days of real use.

Stop after producing the Phase 3 files and wait for approval before any Notion execution.
```
