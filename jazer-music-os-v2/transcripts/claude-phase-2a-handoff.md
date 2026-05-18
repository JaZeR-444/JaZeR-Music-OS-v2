# Claude Phase 2A Handoff

Phase 1 is approved. Claude completed Phase 2A and paused before Phase 2B.

## Locked Phase 2A Decisions

### OQ-1 - Formula Cap

Formula properties count separately from the 12 data-property cap. The cap is for manual data-entry burden, not computed fields.

Keep Songs DB at 12 data properties plus the `Status Progress %` formula. Do not cut any Songs DB data property.

### OQ-2 - Writing Assets Status Options

Use the 3-option Status model:

- Raw
- Developing
- Archived

Do not use `Attached` or `Used` as Writing Assets Status options.

Attachment state is determined by whether the Song relation is filled. Usage/release state is inferred from the linked Song record. The relation is the source of truth.

### OQ-3 - Songs DB Key Property

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

### Sessions Count Exception

`Sessions Count` may be added to Songs DB once Sessions DB exists because it gives immediate visible reward for logging. This is the only early Songs DB rollup exception.

Do not use this as permission to add other early rollups.

## Phase 2B Starting Point

Proceed to Phase 2B only:

- Sessions DB
- Releases DB
- Tasks DB

Do not execute in Notion. Do not use a Notion API. Do not move to Phase 3.
