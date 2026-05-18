# Phase 3 - Navigation Spec

## Sidebar Hierarchy

The workspace sidebar has one root dashboard, three active hubs, one brand reference page, and one external sibling/reference link.

```text
Master Dashboard
├─ Song Lab
│  ├─ The Book of JaZeR
│  ├─ Songs DB
│  └─ Writing Assets DB
├─ Launch Hub
│  ├─ Tasks DB
│  └─ Releases DB
├─ Vault
│  ├─ Archive Batch pages
│  └─ Phase 3I Protocol link
├─ Brand Reference Page
└─ FL Studio Plugin CC (external link only)
```

## Active Hubs

| Hub | Purpose | Must contain | Must not contain |
|---|---|---|---|
| Song Lab | Creative work surface for songs, writing assets, and song-page work. | Songs DB, Writing Assets DB, The Book of JaZeR. | Release campaign management, archive batches, brand reference dump. |
| Launch Hub | Execution and release planning surface. | Tasks DB, Releases DB when built, release/task filtered views. | Song lyric drafts, raw creative fragments, brand static docs. |
| Vault | Archive and historical storage surface. | Archive batches, Phase 3I protocol link. | Active tasks, active song work, dashboard widgets. |

## Reference Pages

| Page | Type | Purpose | Rules |
|---|---|---|---|
| Brand Reference Page | Reference Page | Holds identity, website, and Drive research links. | No database views. No recurring workflow. Not a hub. |
| FL Studio Plugin CC | External sibling/reference link | Links to the separate Plugin Command Center system. | URL only. No merge. No relation. No copied database. |

## Dashboard Navigation Footer

The dashboard footer mirrors the key destinations without replacing the sidebar.

Footer links:

1. Song Lab
2. Launch Hub
3. Vault
4. Brand Reference Page
5. FL Studio Plugin CC

Rules:

- Five links maximum.
- Do not add extra resource links.
- Do not include direct links to individual records.
- Do not add document embeds.
- Use this as an exit ramp from the dashboard, not as a reference library.

## Naming Rules

- Use `Song Lab`, not `Creative Hub`.
- Use `Launch Hub`, not `Release Hub`, unless later approved.
- Use `Vault`, not `Archive Hub`.
- Use `Brand Reference Page`, not `Brand Hub`.
- Use `FL Studio Plugin CC` as an external reference label only.
- Use `Dashboard Section` only for Master Dashboard blocks.
- Use `Hub Page Section` only for sections inside Song Lab, Launch Hub, or Vault.

## Navigation Guardrails

- No Production Hub sidebar page.
- No Brand Hub sidebar page.
- No extra first-level hubs.
- No CRM, finance, touring, collaborator, sample library, or analytics pages.
- No Weekly Review sidebar page before 14 days of real use.
