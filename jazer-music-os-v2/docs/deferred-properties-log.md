# Deferred Properties Log

## Cut - Do Not Build

| Item | Applies to | Reason |
|---|---|---|
| Sessions Status property | Sessions DB | Sessions are event records. Planned work belongs in Tasks DB. |
| Sessions-to-Writing-Assets relation | Sessions DB / Writing Assets DB | High-friction manual linking with no workflow return. Use Song relations and page body notes instead. |
| Recent Sessions dashboard widget | Master Dashboard | Historical context, not action context. Phase 3 should use `Songs in Production` instead. |
| Weekly Review template at launch | Workspace operations | Wait until at least 14 days of real use before formalizing review maintenance. |
| Someday/Maybe task status | Tasks DB | Tasks need execution states. Long-range parking belongs in song status/page body decisions, not task status. |
| CRM, finance, touring, collaborator, sample library, deep analytics systems | Workspace architecture | Adds databases or maintenance layers outside the locked 5-database model. |
| FL Studio Plugin CC relations | Workspace architecture | Plugin CC is external sibling/reference only, linked by URL if needed. |

## Deferred Until Day 30+ Or Real Data

| Item | Applies to | Trigger | Reason |
|---|---|---|---|
| Last Session rollup | Songs DB | 10+ logged sessions or Day 30+ | Useful for stale-work tracking after the habit exists. |
| Open Tasks Count rollup | Songs DB | Real active task volume | Avoid empty rollup clutter during initial build. |
| Asset Count rollup | Songs DB | 30+ Writing Assets | Counting an empty or tiny asset pool is not useful. |
| Days Stale formula | Songs DB | Last Session rollup exists | Depends on real session data. |
| Stale Warning formula | Songs DB | Days Stale exists and real usage history exists | Avoid false urgency before the workspace has a baseline. |
| Days Until Due formula | Tasks DB | Dated tasks become common | Nice-to-have sorting aid, not core Phase 2B approval requirement. |

## Deferred Until First Real Release Window

| Item | Applies to | Trigger | Reason |
|---|---|---|---|
| Releases DB actual Notion build | Releases DB | A release is about 60 days out | Spec now, build when it becomes operational. |
| UPC | Releases DB | Distributor assigns UPC | Empty until submission. |
| Distribution Link | Releases DB | Release is live | Empty until publish. |
| Release Health formula | Releases DB | Releases DB exists with real release date/tasks | Depends on release readiness data. |
| Song Count and Open Release Tasks rollups | Releases DB | Releases DB is built | Useful immediately once release planning is real. |
| Songs Ready rollup | Releases DB | EP or Album is in progress | Not useful for simple single releases. |

## Locked Exceptions

| Item | Applies to | Timing | Reason |
|---|---|---|---|
| Sessions Count rollup | Songs DB | Build after Sessions DB exists | Approved early exception. It rewards logging and helps the Sessions habit stick. |
