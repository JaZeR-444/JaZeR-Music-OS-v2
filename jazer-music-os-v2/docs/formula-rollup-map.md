# Formula / Rollup Map

## Build Now In Phase 2B

| Item | Type | Database | Depends on | Build timing | Purpose |
|---|---|---|---|---|---|
| Auto Name | Formula | Sessions DB | `Session Type`, `Date` | Phase 2B | Displays `Session Type - Date` and removes manual naming pressure. Keep Notion Title field present because Title cannot be a formula. |
| Overdue | Formula | Tasks DB | `Due Date`, `Status` | Phase 2B | Flags dated tasks that are past due and not Done. |
| Sessions Count | Rollup | Songs DB | Songs-to-Sessions relation | Phase 2B after Sessions DB exists | Approved exception. Gives immediate visible reward for logging sessions. |

## Specify Now, Build When Releases DB Exists

| Item | Type | Database | Depends on | Build timing | Purpose |
|---|---|---|---|---|---|
| Song Count | Rollup | Releases DB | Releases-to-Songs relation | Pre-release build | Shows how many songs are on a Single, EP, or Album. |
| Open Release Tasks | Rollup | Releases DB | Releases-to-Tasks relation, Task `Status` | Pre-release build | Core release readiness signal. |
| Days Until Release | Formula | Releases DB | `Release Date` | Pre-release build | Countdown used by release sorting and health logic. |
| Release Health | Formula | Releases DB | `Days Until Release`, `Open Release Tasks`, `Artwork Done`, `Promo Assets Ready` | Pre-release build | Summarizes release readiness without manual inspection. |

## Defer Until Real Data Exists

| Item | Type | Database | Depends on | Build timing | Reason |
|---|---|---|---|---|---|
| Last Session | Rollup | Songs DB | Sessions relation, Session `Date` | Day 30+ unless needed earlier for a real stale-work review | Useful, but less immediately motivating than Sessions Count. |
| Open Tasks Count | Rollup | Songs DB | Tasks relation, Task `Status` | Day 30+ | Needs real tasks to avoid empty schema clutter. |
| Asset Count | Rollup | Songs DB | Writing Assets relation | Day 30+ and 30+ Writing Assets | Useful after the creative asset pool exists. |
| Days Stale | Formula | Songs DB | `Last Session` rollup | Day 30+ | Only useful after regular session logging exists. |
| Stale Warning | Formula | Songs DB | `Days Stale`, Song `Status` | Day 30+ | Avoid false urgency before the workspace has a baseline. |
| Days Until Due | Formula | Tasks DB | `Due Date` | Optional / defer | Sorting aid only. Build if dated tasks become common. |

## Skip

| Item | Type | Reason |
|---|---|---|
| Average Session Rating | Rollup | Subjective average does not support a real decision. |
| Total Session Hours | Rollup | Inaccurate if Duration is optional; trivia rather than workflow signal. |
| Writing Assets by Type on Songs | Rollup set | Would require multiple properties. Use filtered linked views inside Song pages instead. |
| Release Date rollup on Songs | Rollup | Creates brittle dependency. Use release records and direct song properties instead. |

## Formula Notes

Use simple formulas during build. If Notion formula syntax changes or a formula is awkward in the UI, preserve the intent and simplify rather than expanding the property layer.

`Overdue` intent:

```text
If Due Date exists, Due Date is before today, and Status is not Done, show "Overdue"; otherwise blank.
```

`Auto Name` intent:

```text
If Session Type exists, show "Session Type - formatted Date"; otherwise show "New Session".
```
