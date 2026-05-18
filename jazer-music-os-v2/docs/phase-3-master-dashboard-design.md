# Phase 3 - Master Dashboard Design

## Executive Summary

Phase 3 designs the Master Dashboard and navigation structure as a local implementation spec only.

The approved dashboard is a five-zone operating surface. It answers one question: what should I work on right now? It does not store content, archive notes, host long-form writing, duplicate hub pages, or display historical session logs.

## Locked Phase 3 Rules

- Master Dashboard contains filtered views and action buttons only.
- No raw notes live on the dashboard.
- No standalone records live on the dashboard.
- No archive content lives on the dashboard.
- No embedded documents live on the dashboard.
- No long-form writing lives on the dashboard.
- No `Recent Sessions` dashboard widget.
- No 6th database.
- No extra hub.
- Production Hub remains demoted into dashboard sections only: `Songs in Production` and `Production Tasks`.
- Brand remains one compact Brand Reference Page, not a hub.
- FL Studio Plugin Command Center remains an external sibling/reference link only.
- Weekly Review template remains deferred until at least 14 days of real use.

## Dashboard Definition

A Dashboard Section is a named block on the Master Dashboard containing:

- one linked database view, or
- one approved action-button strip, or
- a compact navigation row.

Dashboard Sections are optimized for the question: what do I do now?

Hub Page Sections are different. They live inside Song Lab, Launch Hub, or Vault and are optimized for deeper work.

## Five-Zone Layout

| Zone | Dashboard Section | Type | Source | Purpose |
|---|---|---|---|---|
| 1 | Quick Capture | Action buttons | Writing Assets DB, Sessions DB | Capture a new idea or log a completed session fast. |
| 2 | Production Tasks | Linked Tasks DB view | Tasks DB | Show current execution tasks, driven by `Focus = true`. |
| 3A | Songs in Production | Linked Songs DB view | Songs DB | Show active song projects in Recording, Producing, or Mixing. |
| 3B | Unattached Ideas | Linked Writing Assets DB view | Writing Assets DB | Surface creative fragments that need attachment, development, or archive. |
| 4 | Release Pipeline | Linked Releases DB view | Releases DB | Show active release work only when a real release exists. |
| 5 | Navigation Footer | Page links | Sidebar pages / external reference | Provide compact exit paths to the three hubs and reference pages. |

This keeps the dashboard at five zones while preserving the required Production sections.

## Zone 1 - Quick Capture

Type: action button strip.

Buttons:

| Button | Creates | Pre-filled values | Required user action | Rule |
|---|---|---|---|---|
| Capture Idea | Writing Assets DB record | `Asset Type = Idea`, `Status = Raw`, `Date Created = auto` | Enter title/body fragment | Must create a usable record in under 8 seconds. |
| Log Session | Sessions DB record | `Date = today` | Select `Session Type` and `Song` | Must require no more than 3 taps after button press on mobile. |

This zone is the only non-view action zone. It does not store content on the dashboard; it creates records in the correct databases.

Do not add a link list here. Do not add explanatory text beyond short button labels.

## Zone 2 - Production Tasks

Primary linked view: Tasks DB.

View name: `Focus Now`.

Filter:

```text
Focus = true
AND Status is not Done
```

Recommended visible properties:

- Task
- Task Type
- Song
- Priority
- Due Date
- Overdue

Sort:

1. Priority descending
2. Due Date ascending, when present
3. Manual order if Notion sorting becomes noisy

Display:

- Table or compact list.
- 5-7 rows maximum.
- Hide database title.
- No board view.

Empty state:

```text
No focus tasks. Open a Song or Task and mark the next action as Focus.
```

Do not combine this with `Due This Week`. Focus and due-date planning remain separate.

## Zone 3A - Songs in Production

Linked view: Songs DB.

Filter:

```text
Status is Recording
OR Status is Producing
OR Status is Mixing
```

Optional later refinement after `Open Tasks Count` exists:

```text
AND Open Tasks Count > 0
```

Do not require this refinement at launch because `Open Tasks Count` is deferred.

Recommended visible properties:

- Status
- Priority
- BPM
- Key
- Sessions Count
- Reference Track

Display:

- Gallery or compact table depending on Notion mobile behavior.
- No cover images in dashboard cards unless they stay compact.
- No board view on the dashboard.

Empty state:

```text
No songs are currently in production. Move a Song into Recording, Producing, or Mixing when it becomes active.
```

## Zone 3B - Unattached Ideas

Linked view: Writing Assets DB.

Filter:

```text
Song is empty
AND Status is not Archived
```

If the `Floating` formula exists, use:

```text
Floating = true
```

Sort:

```text
Date Created descending
```

Recommended visible properties:

- Asset Type
- Status
- Date Created
- Energy

Display:

- Compact list or gallery.
- No archive records.
- No full lyrics displayed directly on the dashboard.

Empty state:

```text
No unattached ideas. Capture something new or keep working from active Songs.
```

## Zone 4 - Release Pipeline

Linked view: Releases DB.

Build timing: only when Releases DB exists. Until then, this zone remains documented but not built.

Filter:

```text
Status is not Complete
```

Recommended visible properties:

- Release Title
- Format
- Status
- Release Date
- Days Until Release
- Release Health
- Open Release Tasks

Sort:

```text
Release Date ascending
```

Display:

- Table.
- Wrapped in a toggle labeled `Release Pipeline` if releases are inactive.
- Hide entirely if Releases DB has not been built.

Empty state:

```text
No active release. Build this section when a release is about 60 days out.
```

## Zone 5 - Navigation Footer

Type: compact link row.

Links:

1. Song Lab
2. Launch Hub
3. Vault
4. Brand Reference Page
5. FL Studio Plugin CC

Rules:

- Five links maximum.
- Brand Reference Page is labeled as reference, not hub.
- FL Studio Plugin CC is linked only; no database relation.
- No link dump section above this footer.

## Views Not Included

| View / section | Decision | Reason |
|---|---|---|
| Recent Sessions | Cut | History, not action. Replaced by `Songs in Production`. |
| Weekly Review | Deferred | Must wait until 14 days of real use. Future home is Song Lab, not dashboard. |
| All Tasks | Cut from dashboard | Too broad; belongs in Tasks DB or Launch Hub. |
| All Songs | Cut from dashboard | Catalog browsing belongs in Songs DB / Song Lab. |
| Archive / Vault content | Cut from dashboard | Archive content belongs in Vault. |
| Brand link dump | Cut from dashboard | Brand Reference Page owns static reference links. |

## Dashboard Success Test

Open the dashboard cold. Within 10 seconds and without scrolling below Zone 3, you should know:

- the focused tasks for now,
- the songs actively in production,
- the unattached ideas that need attention.

If that answer is not clear, the dashboard is not approved.
