# JaZeR Music OS v2 - Project Context & Instructions

This repository serves as the local implementation-planning package for the **JaZeR Music OS v2** Notion workspace. It contains architecture specs, schema audits, workflow documentation, and phased implementation guides.

## Project Overview

**JaZeR Music OS v2** is a structured Notion system designed for music production, song management, and release planning. 

### Core Architecture
- **5 Core Databases:**
  1. `Songs DB` (Central hub for track projects)
  2. `Writing Assets DB` (Unified bank for ideas, hooks, lyrics, and concepts)
  3. `Sessions DB` (Low-friction event log for production time)
  4. `Releases DB` (Distribution and promo planning)
  5. `Tasks DB` (Global cross-hub task management)
- **3 Active Hubs:**
  1. `Song Lab`
  2. `Launch Hub`
  3. `Vault`
- **1 Master Dashboard:** Filtered views only; no standalone data storage.

## Directory Structure

- `jazer-music-os-v2/source/`: **Primary Source Materials.** Contains HTML exports of planning sessions and audits. Use these as the source of truth.
- `jazer-music-os-v2/transcripts/`: Claude chat exports and handoff transcripts.
- `docs/`: **Implementation Deliverables.** Markdown files containing schema maps, relation orders, and QA checklists for specific build phases.
- `web/` & Root `.html` files: Wireframe visualizations (Dark/Light mode).

## Operating Rules (CRITICAL)

### 1. No Direct Notion Modification
Do NOT attempt to modify Notion, use Notion APIs, or perform browser automation unless the user explicitly provides the following command:
```text
EXECUTE IN NOTION NOW
```
Otherwise, all work must be restricted to local documentation, schema planning, and QA reports.

### 2. Source Priority Order
When project sources conflict, adhere to this priority:
1. `Source Alignment Pass`
2. `Architecture Review`
3. `Database Schema Audit`
4. `Workflow Audit`
5. `UX Review`
6. `Architecture Spec`
7. `Claude Implementation Plan`
8. `All-In-One planning file`
9. Claude chat transcripts / handoffs

### 3. Architecture Constraints
- **Database Cap:** Exactly 5 databases. No 6th database (e.g., no separate "CRM" or "Finance").
- **Writing Assets:** Must remain unified. Do not split into separate databases for Lyrics/Hooks.
- **Sessions DB:** Designed as an event log. No `Status` property; must remain ultra-low friction (<10s logging).
- **FL Studio CC:** External reference only. Link by URL; do not create Notion relations to it.

## Key Files for Context
- `jazer-music-os-v2/CODEX_HANDOFF.md`: The primary operating manual and state log for AI agents. **Read this first.**
- `docs/context-inventory.md`: Complete list of all files and their classification.
- `docs/phase-2b-sessions-releases-tasks-schema.md`: Most recent schema deliverable for the current build phase.

## Current Phase Status
- **Phase 1 (Setup):** Approved & Locked.
- **Phase 2A (Songs & Writing Assets):** Approved & Locked.
- **Phase 2B (Sessions, Releases, Tasks):** Documentation complete in `docs/`. Pending User review/implementation.
- **Phase 3 (Dashboard):** **BLOCKED** until Phase 2B is approved. Do not start Phase 3 work unprompted.
