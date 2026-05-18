# Phase 2B - Sessions, Releases, and Tasks Schema

## Decisions Carried Forward

- OQ-1 - Formula cap: formula properties count separately from the 12 manual data-property cap. Songs DB remains 12 data properties plus `Status Progress %`.
- OQ-2 - Writing Assets Status options: use exactly `Raw`, `Developing`, `Archived`. Do not use `Attached` or `Used`; attachment and usage are inferred from relations and linked Song state.
- OQ-3 - Songs DB Key property: use one 12-option root-note Select: `C`, `C#`, `D`, `E-flat`, `E`, `F`, `F#`, `G`, `A-flat`, `A`, `B-flat`, `B`. Do not add Mode now.
- Sessions Count exception: once Sessions DB exists, `Sessions Count` may be added to Songs DB because it gives immediate visible reward for logging. This is the only early Songs DB rollup exception.
- No extra databases or hubs are introduced. The locked model remains 1 Master Dashboard, 5 Core Databases, 3 Active Hubs, 1 Brand Reference Page, and FL Studio Plugin Command Center as external sibling/reference only.

## Sessions DB Property Map

| Property Name | Notion Type | Required / Optional | Options | Default visibility | Purpose | Build timing |
|---|---|---|---|---|---|---|
| Name | Title | Required system field, manual entry not required | None | Visible | Notion requires a title. Keep manual naming out of the workflow; use `Auto Name` as the display reference in views. | Phase 2B |
| Session Type | Select | Required | `Writing`, `Freestyle`, `Recording`, `Production`, `Mix Review` | Visible | Captures what kind of work happened with one click. | Phase 2B |
| Date | Date | Required | Defaults to today in templates | Visible | Timestamp for the event log and source for last-session rollups. | Phase 2B |
| Song | Relation to Songs DB | Required | Select linked Song | Visible | Connects the event to the song it moved forward. Enables `Sessions Count` on Songs DB. | Phase 2B |
| Duration | Number | Optional | Minutes | Hidden / below fold | Optional time tracking only. Defer use unless session-length tracking proves useful. | Phase 2B as hidden optional |
| Energy | Select | Optional | `Fired Up`, `Focused`, `Neutral`, `Forced` | Hidden / below fold | Quick subjective read without turning session logging into journaling. | Phase 2B as hidden optional |
| Key Win | Text | Optional | One sentence | Hidden / below fold | Captures the main result of the session. Long notes go in the page body. | Phase 2B as hidden optional |
| Next Step | Text | Optional | One sentence | Hidden / below fold | Records where to resume without creating a task for every session. | Phase 2B as hidden optional |
| Auto Name | Formula | Optional computed | `Session Type + Date` display | Visible in compact views if useful | Reduces naming friction. Not a replacement for Notion's required Title field. | Phase 2B |

Sessions DB has no `Status` property and no Sessions-to-Writing-Assets relation.

## Releases DB Property Map

Releases DB is designed now as a written spec. Build the actual Notion database only when a real release is about 60 days out.

| Property Name | Notion Type | Required / Optional | Options | Default visibility | Purpose | Build timing |
|---|---|---|---|---|---|---|
| Release Title | Title | Required | None | Visible | Name of the release; may differ from a song title. | Spec now, build pre-release |
| Status | Select | Required | `Planned`, `In Prep`, `Submitted`, `Live`, `Promoting`, `Complete` | Visible | Tracks release lifecycle without building a deep campaign system. | Spec now, build pre-release |
| Format | Select | Required | `Single`, `EP`, `Album` | Visible | Supports the requested release planning types. `Compilation` is deferred unless a real need appears. | Spec now, build pre-release |
| Release Date | Date | Required | Target or confirmed date | Visible | Core release deadline and formula input. | Spec now, build pre-release |
| Songs | Relation to Songs DB | Required | Linked Songs | Visible | Connects singles, EPs, and albums to their song records. | Spec now, build pre-release |
| Tasks | Relation to Tasks DB | Required | Linked Tasks | Visible | Connects release prep and promo work to the release record. | Spec now, build pre-release |
| Distributor | Select | Optional | `DistroKid`, `Amuse`, `TuneCore`, `CD Baby`, `Direct`, `Other` | Visible when in prep | Stores distribution context only when submission is real. | Spec now, build pre-release |
| UPC | Text | Optional | None | Hidden until submitted | Distribution identifier assigned during submission. | Build pre-release |
| Distribution Link | URL | Optional | None | Hidden until live | Stores live release URL after publish. | Build pre-release |
| Playlist Pitch Deadline | Date | Optional but expected for release prep | Usually release date minus 7 days | Visible | Highest-leverage deadline in the release workflow. | Build pre-release |
| Artwork Done | Checkbox | Optional readiness flag | Checked/unchecked | Visible during prep | Keeps release readiness concrete without excessive properties. | Build pre-release |
| Metadata Verified | Checkbox | Optional readiness flag | Checked/unchecked | Visible during prep | Confirms title, artist, genre, ISRC, and distributor metadata. | Build pre-release |
| Promo Assets Ready | Checkbox | Optional readiness flag | Checked/unchecked | Visible during prep | Confirms launch content is prepared. | Build pre-release |
| Song Count | Rollup | Computed | Count Songs | Visible for EP/Album | Shows release size and EP/album progress. | Build with Releases DB |
| Open Release Tasks | Rollup | Computed | Count linked Tasks where `Status` is not `Done` | Visible | Core release readiness signal. | Build with Releases DB |
| Days Until Release | Formula | Computed | Integer countdown | Visible | Powers release prioritization and Release Health. | Build with Releases DB |
| Release Health | Formula | Computed | `At Risk`, `Active`, `Planned` | Visible | Summarizes readiness from date, task, artwork, and promo state. | Build with Releases DB |

## Tasks DB Property Map

| Property Name | Notion Type | Required / Optional | Options | Default visibility | Purpose | Build timing |
|---|---|---|---|---|---|---|
| Task | Title | Required | Action-verb naming | Visible | Specific action to complete. Long context goes in the page body. | Phase 2B |
| Task Type | Select | Required | `Production`, `Release Prep`, `Content`, `Brand / Website`, `Admin`, `Review` | Visible | Global cross-hub categorization. Select, not multi-select. | Phase 2B |
| Status | Select | Required | `Open`, `In Progress`, `Done`, `Blocked` | Visible | Minimal execution state. No `Someday/Maybe`. | Phase 2B |
| Focus | Checkbox | Required | Checked/unchecked | Visible | Separates current execution priority from Due Date. Primary dashboard task filter later. | Phase 2B |
| Priority | Select | Optional | `High`, `Medium`, `Low` | Visible | Manual importance signal. Separate from Focus. | Phase 2B |
| Due Date | Date | Optional | Real deadline only | Visible | Deadline tracking. Do not invent dates for normal production tasks. | Phase 2B |
| Notes | Text | Optional | Short text only | Hidden / below fold | Small context field. Long context belongs in task page body. | Phase 2B |
| Song | Relation to Songs DB | Optional generally, required for Production tasks | Linked Song | Visible when relevant | Prevents duplicate production-task tracking inside isolated pages. | Phase 2B |
| Release | Relation to Releases DB | Optional generally, required for release prep/content tied to a release | Linked Release | Visible when relevant | Connects release work to release readiness. Document now; activate when Releases DB exists. | Phase 2B spec; active when Releases DB exists |
| Overdue | Formula | Computed | Flag if due date has passed and status is not Done | Visible in Due views | Surfaces tasks that need immediate resolution or deletion. | Phase 2B |
| Days Until Due | Formula | Computed | Integer countdown | Hidden unless useful | Sorting aid for dated tasks. Nice-to-have; may be deferred if build friction rises. | Optional Phase 2B / defer |

## Relation Build Order

Build relation dependencies in the order that prevents orphaned links and avoids placeholder complexity. Summary: Songs must exist before Sessions and Tasks can point to it; Releases relations are specified now but built only in the pre-release window.

See `docs/relation-build-order.md`.

## Formula / Rollup Map

Build only formulas and rollups that support decisions. Summary: `Auto Name` and `Overdue` can be built in Phase 2B; `Sessions Count` is the only early Songs DB rollup exception; Releases formulas/rollups wait until Releases DB is actually built.

See `docs/formula-rollup-map.md`.

## Cut / Deferred Properties

Cut anything that creates maintenance without daily use: Sessions Status, Sessions-to-Writing-Assets relation, deep analytics, and extra databases. Defer nice-to-have rollups and release-only properties until real data exists.

See `docs/deferred-properties-log.md`.

## Open Questions

None block Phase 2B approval.

## QA Check

- No 6th database proposed: Pass.
- No extra hub proposed: Pass.
- No Writing Assets split proposed: Pass.
- No FL Studio Plugin CC merge proposed: Pass.
- No Sessions Status property proposed: Pass.
- No Sessions-to-Writing-Assets relation proposed: Pass.
- No dashboard content storage proposed: Pass.
- No Recent Sessions dashboard widget proposed: Pass.
- No Weekly Review template proposed before 14 days of real use: Pass.
- No CRM, finance, touring, collaborator, sample library, or deep analytics system proposed: Pass.
