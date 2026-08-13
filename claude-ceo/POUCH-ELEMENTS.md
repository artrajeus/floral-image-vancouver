# Pouch Elements — Source of Truth

**This file is the ONLY authority on which Higgsfield Element may be used for
pouch imagery.** Element *names* are ambiguous and `created_at` does not encode
which label generation an Element depicts. Always match on **UUID**.

Last reconciled against live Higgsfield: **2026-08-10**.

## The rule

Before generating any pouch image:

1. Call `show_reference_elements` (action=`list`).
2. For each flavour in the creative, look up its UUID **in the table below**.
3. Generate **only** if the flavour's row says `approved` AND that UUID still
   exists in the live list.
4. If a flavour is `quarantined` or absent — **stop and tell the founder.**
   Never substitute a different flavour, never fall back to an older Element,
   never generate the pouch from a text description instead.

## Canonical source resolved (2026-08-13)

**Shopify product media IS the current artwork.** Verified by eye, not by
timestamp: the Shopify `mxt-glow-*` studio shots and `espresso-martini-*.jpg`
match the founder's 2026-08-04 reference photos exactly — gradient **M** monogram
with horizontal "MXTOLOGY" beneath it, and a full-bleed illustrated artwork panel
per flavour carrying the flavour name vertically in white.

The 19 legacy Elements describe a *different* design (vertical iridescent
"MXT OLOGY" wordmark, plain colour right panel, no illustration). They are
superseded, not merely old. My earlier note that Shopify "may itself be a
generation behind" was wrong and is withdrawn.

**Rebuild source:** `https://cdn.shopify.com/s/files/1/0553/8145/8978/files/mxt-glow-<flavour>.jpg`
(no `mxt-glow-` asset exists for Espresso Martini; use `espresso-martini-5692062.jpg`.)

## Status: ALL ELEMENTS QUARANTINED (2026-08-10)

Every Element in the workspace was created **2026-06-19/20** or **2026-07-03**.
The new pouch label artwork was supplied by the founder around **2026-08-04**
with an instruction to rebuild. **That rebuild was never carried out.** No
Element has been created since 2026-07-03, so every one of them depicts
pre-August labels.

Consequence: **no pouch imagery may be generated until the rebuild is done.**
Creative produced before this date — including the three Instagram images from
the 2026-08-10 kickoff — uses superseded artwork and must not be published.

| Flavour | Approved UUID | Status | Notes |
|---|---|---|---|
| Pornstar Martini | `049e6b43-ed4c-44eb-b047-9ad95ded41af` | ✅ **approved** | `mxt-pornstar-CURRENT-202608` · source `mxt-glow-pornstar-martini.jpg` · built 2026-08-13 |
| Tommy's Margarita | `0beecfb3-8141-42d3-8e85-eaf091bb1fcd` | ✅ **approved** | `mxt-margarita-CURRENT-202608` · source `mxt-glow-tommys-margarita.jpg` · built 2026-08-13 |
| Aussie Berry Bliss | `4660d157-ae54-4f78-bb18-73158c23216d` | ✅ **approved** | `mxt-berry-CURRENT-202608` · source `mxt-glow-aussie-berry-bliss.jpg` |
| Amaretto Whisky Sour | `aa8f8e8b-b01b-4946-95a4-76ad5b4dcf6d` | ✅ **approved** | `mxt-amaretto-CURRENT-202608` · source `mxt-glow-amaretto-whisky-sour.jpg` |
| Granny Smith Fireball | `b9473bf5-9183-4582-a75b-2c7e1f507690` | ✅ **approved** | `mxt-fireball-CURRENT-202608` · source `mxt-glow-granny-smith-fireball.jpg` |
| Mai Tai | — | ⏳ media imported | `10575e0a-0d31-4c75-af20-40a7ba5f3059` |
| Fabulous AF Cosmo | — | ⏳ media imported | `4822c527-4148-4899-92ce-326213e4c3a8` · Shopify title rename still pending |
| Shiso Sour | — | ⏳ media imported | `0eab24a6-4d33-4186-93b3-4f8737d91f1c` |
| Elderflower Gin Gimlet | — | ⏳ media imported | `48028790-cc46-4242-ab08-b4b04349df09` |
| Espresso Martini | — | ⏳ media imported | `9b3d2104-af99-4239-963e-7beead1073fa` · no `mxt-glow-` asset; from `espresso-martini-5692062.jpg` |
| Piña Colada | — | ⏳ media imported | `115db1db-7f74-487a-8b0a-63f4b0e94eaf` · no `mxt-glow-` asset; from `scene-pina-colada.webp` |

### Stale Elements — do not use any of these

19–20 Jun 2026: `mxt-pornstar-martini-pouch`, `mxt-espresso-martini-pouch`,
`mxt-tommys-margarita-pouch`, `mxt-elderflower-gimlet-pouch`,
`mxt-amaretto-whisky-sour-pouch`, `mxt-mai-tai-pouch`,
`mxt-granny-fireball-pouch`, `mxt-aussie-berry-bliss-pouch`,
`mxt-pina-colada-pouch`, `mxt-fabulous-af-cosmo-pouch`, `mxt-shiso-sour-pouch`,
`mxt-pornstar-martini-v2`, `mxt-aussie-berry-bliss-v2`, `mxt-mai-tai-v2`,
`mxt-mai-tai-v3`.
3 Jul 2026: `mxt-pornstar-pouch`, `mxt-amaretto-pouch`, `mxt-espresso-pouch`,
`mxt-fireball-pouch`.

The Higgsfield MCP exposes only `list` / `get` / `create` — it **cannot rename
or delete**. These 19 can only be removed by the founder in the Higgsfield UI.
Until they are, this file is the sole guard against picking one.

## Rebuild procedure

For each flavour, in this order:

1. Take the current pouch image from the **Shopify product record** (the store is
   the upstream source of truth for live artwork) or from founder-supplied files
   if the founder confirms those supersede Shopify.
2. `media_upload` → PUT the bytes → `media_confirm`.
3. `show_reference_elements` action=`create` with the returned `media_id`.
   Name it `mxt-<flavour>-YYYYMM` so the generation is legible from the name.
4. Record the new UUID **and its source image URL** in the table above, set
   status to `approved`, and commit.

Provenance is the point. A row without a source URL is not approved, however
new it looks.

## Reconciliation

- **Every Friday review:** list live Elements, diff against this table. Report
  any approved UUID that has vanished, and any live Element not recorded here.
- **On any founder artwork change:** quarantine every affected flavour in this
  file *first*, then rebuild. Quarantine before rebuild, never after.
