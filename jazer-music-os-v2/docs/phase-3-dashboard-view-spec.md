# Phase 3 - Dashboard View Spec

## Purpose

This file specifies the linked database views that appear on the Master Dashboard. It is a build checklist, not a Notion execution log.

## View Summary

| Dashboard Zone | View Name | Database | View type | Build timing |
|---|---|---|---|---|
| Zone 2 | Focus Now | Tasks DB | Table / list | Phase 3 spec, build when executing dashboard |
| Zone 3A | Songs in Production | Songs DB | Gallery / compact table | Phase 3 spec, build when executing dashboard |
| Zone 3B | Unattached Ideas | Writing Assets DB | Compact list / gallery | Phase 3 spec, build when executing dashboard |
| Zone 4 | Release Pipeline | Releases DB | Table in toggle | Defer until Releases DB exists |

## Focus Now

Database: Tasks DB.

Filter:

```text
Focus = true
AND Status is not Done
```

Sort:

```text
Priority descending
Due Date ascending
```

Visible properties:

- Task
- Task Type
- Song
- Priority
- Due Date
- Overdue

Hidden properties:

- Notes
- Release, unless Releases DB exists and a release is active

Display rule:

- 5-7 rows maximum.
- No board view.
- Hide source database title.

## Due This Week

Database: Tasks DB.

Build timing: not a primary dashboard zone. This view should exist in Tasks DB and may be linked from Launch Hub. Add to dashboard only if `Focus Now` fails to surface dated work after real use.

Filter:

```text
Due Date is on or before 7 days from today
AND Status is not Done
```

Sort:

```text
Due Date ascending
```

Reason for dashboard deferral:

The dashboard already has a primary task surface. Adding both `Focus Now` and `Due This Week` as separate top-level dashboard sections risks task-list sprawl. The approved distinction remains: Focus is execution; Due Date is planning.

## Songs in Production

Database: Songs DB.

Filter:

```text
Status is Recording
OR Status is Producing
OR Status is Mixing
```

Deferred refinement:

```text
Open Tasks Count > 0
```

Do not add the deferred refinement until `Open Tasks Count` exists.

Sort:

```text
Priority descending
Status order: Recording, Producing, Mixing
```

Visible properties:

- Status
- Priority
- BPM
- Key
- Sessions Count
- Reference Track

Hidden properties:

- Long text fields
- Archive/release-only fields
- Any deferred rollup that does not exist yet

## Unattached Ideas

Database: Writing Assets DB.

Preferred filter if `Floating` exists:

```text
Floating = true
```

Fallback filter:

```text
Song is empty
AND Status is not Archived
```

Sort:

```text
Date Created descending
```

Visible properties:

- Asset Type
- Status
- Date Created
- Energy

Hidden properties:

- Full body content
- Archived records
- Song relation when empty, unless useful for QA

## Release Pipeline

Database: Releases DB.

Build timing:

```text
Only when a release is about 60 days out and Releases DB has been built.
```

Filter:

```text
Status is not Complete
```

Sort:

```text
Release Date ascending
```

Visible properties:

- Release Title
- Format
- Status
- Release Date
- Days Until Release
- Release Health
- Open Release Tasks

Display rule:

- Table.
- Put inside a toggle labeled `Release Pipeline`.
- Collapse or omit when there is no active release.

## Explicitly Forbidden Dashboard Views

| View | Reason |
|---|---|
| Recent Sessions | Rejected by source alignment and UX review. |
| All Songs | Catalog surface, not dashboard surface. |
| All Tasks | Too broad; destroys focus. |
| Archived Anything | Vault owns archive content. |
| Brand / Website Links | Brand Reference Page owns static brand reference. |
| FL Studio Plugin Database | Plugin CC remains external linked reference only. |
