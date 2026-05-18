# Relation Build Order

## Principle

Build relations only after both endpoint databases exist and the target records/views are stable. Relations should prevent duplicate tracking, not create extra maintenance.

## Phase 2B Relation Sequence

| Step | Relation | Build timing | Direction / naming | Reason |
|---|---|---|---|---|
| 1 | Songs DB to Sessions DB | Phase 2B, after Songs DB exists | On Sessions record: `Song` | Every Session should point to the Song it advanced. This enables session history inside Song pages and the approved early `Sessions Count` rollup. |
| 2 | Songs DB to Tasks DB | Phase 2B, after Songs DB exists | On Task record: `Song` | Production tasks need song context. This prevents production work from being scattered across page bodies and loose notes. |
| 3 | Releases DB to Tasks DB | Spec in Phase 2B; build when Releases DB is created | On Task record: `Release`; on Release record: `Tasks` | Release prep and content tasks need a release readiness surface. Activate only when the Releases DB exists. |
| 4 | Releases DB to Songs DB | Spec in Phase 2B; build when Releases DB is created | On Release record: `Songs` | Supports Single, EP, and Album planning. A release can include many songs; a song may later appear on another release. |

## Relations Not To Build

| Relation | Decision | Reason |
|---|---|---|
| Sessions DB to Writing Assets DB | Cut | Adds manual linking after every session. Writing Assets already relate to Songs; Session page body notes can mention what was created. |
| Tasks DB to Writing Assets DB | Cut for Phase 2B | Not needed for global execution. If a task needs asset context, put it in the task page body or link the relevant Song. |
| FL Studio Plugin Command Center relations | Cut | Plugin CC remains an external sibling/reference system linked by URL only. |

## Naming Rules

- Use singular relation names on child records: `Song`, `Release`.
- Use plural `Songs` only on Releases DB because a release can contain multiple songs.
- Do not create placeholder relations to non-existent databases in Notion during the initial build. Document them here and activate when the endpoint exists.

## Build Verification

- Create one Session linked to one Song and confirm it appears in the Song's session view.
- Create one Production Task linked to one Song and confirm it appears in the Song's task view.
- When Releases DB is eventually built, create one test Release linked to one Song and one Task, then verify `Open Release Tasks` counts correctly.
