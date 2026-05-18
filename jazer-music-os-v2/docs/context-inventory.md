# Context Inventory

Generated: 2026-05-17

## Project Files Found

| File | Appears to contain | Classification | Conflict authority |
|---|---|---|---|
| `README.md` | Local project orientation and guardrails. | Draft / local guide | Low. Use only for local workflow. |
| `CODEX_HANDOFF.md` | Controlling Codex handoff prompt, locked decisions, Phase 2B scope, and output requirements. | Handoff / controlling prompt | High for this run, especially where it records approved post-Claude decisions. |
| `source/JaZeR_Music_OS_v2_Source_Alignment_Pass.html` | Cross-source alignment and conflict resolution for architecture, database count, hubs, Sessions simplification, Tasks Focus, rollup timing, Releases deferral, and Phase prompt corrections. | Source | Highest source authority. |
| `source/JaZeR_Music_OS_v2_Architecture_Review.html` | Architecture review notes and corrections. | Source | Priority 2. |
| `source/JaZeR_Music_OS_v2_Database_Schema.html` | Database schema audit, relation map, rollup map, formula recommendations, and build sequence. | Source | Priority 3. |
| `source/JaZeR_Music_OS_v2_Workflow_Audit.html` | Creative workflow audit, session logging behavior, release workflow, and task/review rhythm guidance. | Source | Priority 4. |
| `source/JaZeR_Music_OS_v2_UX_Review.html` | UX review and dashboard/page-use recommendations. | Source | Priority 5. |
| `source/JaZeR_Music_OS_v2_Architecture.html` | Original architecture specification. | Source | Priority 6. |
| `source/JaZeR_Music_OS_v2_Claude_Implementation_Plan.html` | Claude implementation plan and phase prompts. | Source / plan | Priority 7, overridden by later reviews and handoff decisions. |
| `source/JaZeR_Music_OS_v2_All_In_One.html` | Consolidated planning file. | Source / compiled planning | Priority 8. |
| `source/JaZeR_Music_OS_v2_Phase1_Deliverable.html` | Prior Phase 1 deliverable. | Source / prior deliverable | Use as settled context unless later files correct it. |
| `source/JaZeR_Music_OS_v2_Phase2A_Deliverable.html` | Phase 2A deliverable for Songs DB and Writing Assets DB. | Source / prior deliverable | Use for Phase 2A context, but `CODEX_HANDOFF.md` controls the approved OQ answers. |
| `source/jazer music os v2 architecture review - HTML.html` | Extra copied architecture review export. | Source duplicate / extra | Use only if primary architecture review is unavailable. |
| `transcripts/claude-phase-2a-handoff.md` | Latest Phase 2A handoff decisions in markdown. | Transcript / handoff | High for Phase 2A decisions; aligns with `CODEX_HANDOFF.md`. |
| `transcripts/jazer-notion-os-v2-rebuild-plans-claude-build.html` | Claude/export-style rebuild planning context. | Transcript | Priority 9. Use only after structured source docs. |
| `transcripts/jazer music os v2 architecture review - HTML.html` | Extra copied architecture review export in transcripts. | Transcript / duplicate | Low unless needed as backup. |
| `docs/context-inventory.md` | This inventory. | Generated output | Not a source of architecture decisions. |

## Decision Control Order

When sources conflict, use this order:

1. `CODEX_HANDOFF.md` for approved post-Claude decisions and current task scope.
2. Source Alignment Pass.
3. Architecture Review.
4. Database Schema Audit.
5. Workflow Audit.
6. UX Review.
7. Architecture Spec.
8. Claude Implementation Plan.
9. All-In-One planning file.
10. Claude transcripts / copied handoffs.

## Notes

- The original source files were copied into this local repo-style folder; originals outside `jazer-music-os-v2/` were not moved.
- Several source filenames were normalized by Windows copy behavior where duplicate names existed.
- Phase 2B work must not execute in Notion, use the Notion API, or begin Phase 3.
