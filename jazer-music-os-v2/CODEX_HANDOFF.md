# Codex Handoff - JaZeR Music OS v2

You are taking over the JaZeR Music OS v2 Notion workspace build from a Claude planning session.

Your role is not to write app code unless explicitly asked for code later. Your role is to act as a repo-based implementation planner, documentation engineer, schema auditor, Notion build-spec formatter, and QA partner.

## Primary Goal

Turn the existing project documents, Claude handoff notes, and phase decisions into a clean implementation package that can be used to build JaZeR Music OS v2 in Notion without reopening settled architecture decisions.

## Important Operating Rule

Do not directly modify Notion.
Do not create, delete, rename, or move Notion pages/databases.
Do not use any Notion API, MCP server, browser automation, or external connector unless the user explicitly writes:

```text
EXECUTE IN NOTION NOW
```

Until then, produce files, markdown specs, checklists, and QA reports inside this local project folder only.

## First Actions

Read this file first.

Then inspect the repository/folder before writing anything. Find and read the available project files, especially:

1. `source/JaZeR_Music_OS_v2_Source_Alignment_Pass.html`
2. `source/JaZeR_Music_OS_v2_Architecture_Review.html`
3. `source/JaZeR_Music_OS_v2_Database_Schema.html`
4. `source/JaZeR_Music_OS_v2_Workflow_Audit.html`
5. `source/JaZeR_Music_OS_v2_UX_Review.html`
6. `source/JaZeR_Music_OS_v2_Architecture.html`
7. `source/JaZeR_Music_OS_v2_Claude_Implementation_Plan.html`
8. `source/JaZeR_Music_OS_v2_All_In_One.html`
9. Any Claude transcript or handoff markdown files in `transcripts/`

If file names differ, identify the closest matching files and state what was found.

Before creating Phase 2B docs, create:

```text
docs/context-inventory.md
```

It must list:

1. Every project file found
2. What each file appears to contain
3. Whether it is source, transcript, draft, backup, or generated output
4. Which files should control decisions when sources conflict

After the context inventory is complete, proceed to Phase 2B exactly as instructed here.

## Source Priority Order

When sources conflict, use this priority order:

1. Source Alignment Pass
2. Architecture Review
3. Database Schema Audit
4. Workflow Audit
5. UX Review
6. Architecture Spec
7. Claude Implementation Plan
8. All-In-One planning file
9. Claude chat transcripts / pasted handoffs

Do not blindly follow older wording if a later source corrected it.

## Current State From Claude

Phase 1 is approved.
Open-question answers were recorded.
Sessions Count exception is carried forward.
Claude completed Phase 2A and paused before Phase 2B.

## Phase 2A Approved Decisions

Record these as locked:

OQ-1 - Formula cap:
Formula properties count separately from the 12 data-property cap. The cap is for manual data-entry burden, not computed fields. Keep Songs DB at 12 data properties plus Status Progress % formula. Do not cut any Songs DB data property.

OQ-2 - Writing Assets Status options:
Use the 3-option Status model:

- Raw
- Developing
- Archived

Do not use Attached or Used as Writing Assets Status options. Attachment state is determined by whether the Song relation is filled. Usage/release state is inferred from the linked Song record. The relation is the source of truth.

OQ-3 - Songs DB Key property:
Use a single 12-option root-note Select:

- C
- C#
- D
- E-flat
- E
- F
- F#
- G
- A-flat
- A
- B-flat
- B

Do not add a separate Mode property now. Major/minor belongs in the Song page body template for now. Revisit after 30 days only if real filtering needs prove it necessary.

Sessions Count exception:
Sessions Count may be added to Songs DB once Sessions DB exists because it gives immediate visible reward for logging. This is the only early Songs DB rollup exception. Do not use this as permission to add other early rollups.

## Locked Architecture

Confirm and preserve:

- 1 Master Dashboard
- 5 Core Databases
- 3 Active Hubs
- 1 Brand Reference Page
- FL Studio Plugin Command Center as external sibling / linked reference only

Core databases - exactly 5:

1. Songs DB
2. Writing Assets DB
3. Sessions DB
4. Releases DB
5. Tasks DB

Active hubs - exactly 3:

1. Song Lab
2. Launch Hub
3. Vault

## Demoted / Reframed Areas

Production Hub is not a sidebar hub. It becomes Master Dashboard sections only:

- Songs in Production
- Production Tasks

Brand Hub is not a hub. It becomes one compact Brand Reference Page:

- Identity
- Website
- Drive Research

## FL Studio Plugin CC Rule

The FL Studio Plugin Command Center is an external sibling/reference system. It may be linked by URL only. Do not merge it into Music OS v2. Do not create Notion relations to it unless explicitly requested later.

## Master Dashboard Rule

The Master Dashboard contains filtered views only. No raw notes, no standalone records, no archive content, no embedded documents, and no long-form writing lives directly on the dashboard.

## Writing Assets Rule

Writing Assets DB is unified. Do not split it into separate Ideas, Hooks, Lyrics, Freestyles, or Concepts databases.
Do not create a Writing Assets Type called Concept.
Use Songs DB Status = Concept for named song project placeholders.

## Phase 2B Task

Produce the Phase 2B implementation package for:

1. Sessions DB
2. Releases DB
3. Tasks DB

Do not execute in Notion.
Do not move to dashboard design yet.
Do not start Phase 3.

## Phase 2B Constraints

Sessions DB:

- Event log, not task system
- No Status property
- Logging should take under 10 seconds
- Required properties must stay very low-friction
- Include Session Type options
- Include Song relation
- Do not create Sessions <-> Writing Assets relation

Releases DB:

- Designed now, but actual Notion build may be deferred until the first real release window if appropriate
- Support Single / EP / Album style release planning
- Include relation to Songs
- Include relation to Tasks
- Include only release properties that support release prep, distribution, publishing, or promo readiness

Tasks DB:

- Global cross-hub database
- Include Focus checkbox
- Focus is separate from Due Date
- Task Type must support Production, Release Prep, Content, Brand / Website, Admin, and Review unless a source directly conflicts
- No Someday/Maybe status
- Long context goes in the task page body, not excessive properties

## Output Files To Create

Create a clean implementation package in markdown:

```text
docs/phase-2b-sessions-releases-tasks-schema.md
docs/relation-build-order.md
docs/formula-rollup-map.md
docs/deferred-properties-log.md
docs/phase-2b-qa-check.md
docs/phase-3-readiness-brief.md
```

Do not overwrite existing files unless they are clearly draft files created in this run.

## Phase 2B Deliverable Structure

In `docs/phase-2b-sessions-releases-tasks-schema.md`, use this exact structure:

```text
# Phase 2B - Sessions, Releases, and Tasks Schema

## Decisions Carried Forward
## Sessions DB Property Map
## Releases DB Property Map
## Tasks DB Property Map
## Relation Build Order
## Formula / Rollup Map
## Cut / Deferred Properties
## Open Questions
## QA Check
```

For every property, include:

- Property Name
- Notion Type
- Required / Optional
- Options, if Select or Multi-select
- Default visibility
- Purpose
- Build timing

Open Questions should only list questions that genuinely block Phase 2B approval.

QA Check must confirm:

- No 6th database proposed.
- No extra hub proposed.
- No Writing Assets split proposed.
- No FL Studio Plugin CC merge proposed.
- No Sessions Status property proposed.
- No Sessions <-> Writing Assets relation proposed.
- No dashboard content storage proposed.
- No Recent Sessions dashboard widget proposed.
- No Weekly Review template proposed before 14 days of real use.
- No CRM, finance, touring, collaborator, sample library, or deep analytics system proposed.

## Quality Standard

Be strict. Prefer a workspace that will actually be used over a beautiful system that becomes maintenance debt.

Every property must justify its existence.
Every relation must prevent duplication.
Every formula or rollup must have a build timing.
If a property is nice-to-have, defer it.

## Stop Condition

Stop after producing Phase 2B files and a concise summary of what changed.
Wait for user approval before Phase 3.
