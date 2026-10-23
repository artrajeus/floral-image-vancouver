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

## ⛔ BLOCKED 2026-10-02 — the approved spec is contested. Do not generate.

A newer Element declares one of the approved UUIDs below to be **wrong**.
`mxt-cosmo-REAL-2609` (`9320c528-e78f-43c1-97b0-00d39a0f8307`, created
2026-09-10) states in its own description:

> "SUPERSEDES mxt-cosmo-CORRECTED-2608, **mxt-cosmo-CURRENT-202608** and
> mxt-pouch-SCALE-2609, ALL OF WHICH DESCRIBE THE PACKAGING WRONGLY. Ignore
> those elements entirely."

`mxt-cosmo-CURRENT-202608` is `bed44330-1fd6-4896-a120-d41feb4f14f0`, marked
✅ approved in the table below. `mxt-pornstar-REAL-2609`
(`122e71ca-cb5a-40f0-8cd6-d335212ac7b2`) makes the same claim against the
pornstar lineage.

Three points were originally recorded as disputed. **The 2026-10-09 reconcile
read all 61 descriptions in full and two of the three dissolve on reading.
One real conflict remains.**

1. **Flavour artwork — STILL DISPUTED. This is the only open question.**
   `-CURRENT-202608` (all eleven approved Elements) says *"RIGHT PANEL:
   full-bleed … illustration"*. `-REAL-2609` says *"a SEPARATE INSET RECTANGULAR
   LABEL with rounded corners, applied to the lower-right of the pouch face,
   with BLACK FOIL CLEARLY VISIBLE AROUND ALL FOUR OF ITS EDGES."* These cannot
   both be true of the same physical pouch. **Founder call. Nothing generates
   until it is made.**

   Weight of evidence, for the ruling only — not a licence to act on it: the
   inset-label claim is made by exactly two Elements (`mxt-cosmo-REAL-2609`,
   `mxt-pornstar-REAL-2609`). Full-bleed is stated by all eleven approved
   Elements, all eleven `-CORRECTED-2608`, `mxt-pouch-SCALE-2609`, and
   `mxt-pornstar-V3/V4/V5/V6-2609` — including `V6`, created **eleven minutes
   before** `mxt-pornstar-REAL-2609` from the same September reference set. So
   the 2609 generation contradicts *itself* on this point, which is why the
   count cannot settle it.

2. **Proportions — NOT a conflict. Withdrawn 2026-10-09.** The two Elements are
   measuring different things and agree once that is noticed.
   `mxt-pouch-SCALE-2609` gives **125mm wide × 170mm tall including the top seal
   band**, then calls the pouch squat on the basis of *"the body alone is about
   140mm tall, so the body is only ~1.15× as tall as it is wide"* — 140/125 =
   1.12. `-REAL-2609` says *"roughly 3 wide to 4 tall"* = 1.33, against
   170/125 = **1.36 including the seal band**. Body ratio 1.12, overall ratio
   1.36. Both are correct; neither contradicts the other. Every 2609 Element
   that states millimetres states the same 125 × 170.

3. **Rainbow wordmark — NOT a conflict with the Elements.
   `QUALITY-STANDARDS.md` was wrong and has been corrected (2026-10-09).** The
   standards file described the pouch as carrying "the iridescent rainbow MXT
   OLOGY wordmark". **No live Element says that of a pouch.** All eleven
   approved Elements say the opposite in their own text — *"both HORIZONTAL —
   NO vertical rainbow wordmark"* — and so does every `-CORRECTED-2608` and
   every 2609 Element. The rainbow MXT-over-OLOGY lockup is real, but it
   belongs to the **"Party In A Box" mailer carton lid**
   (`mxt-partybox-CURRENT-202608`): *"centred 'MXT' in bright rainbow-gradient
   capitals … directly above 'OLOGY' in solid white capitals."* The standards
   file had transposed the box lid onto the pouch. Fixed at source; no founder
   ruling needed.

**Nothing has been re-pointed and nothing has been quarantined.** Which lineage
is correct is a founder call and this file reserves it to the founder. Until it
is ruled on: **generate no pouch imagery.** Do not resolve this by picking the
newer Element, the longer description, or the one that sounds more confident —
that is precisely the reasoning that caused the 2026-08-10 failure.

**Reconcile rule added 2026-10-02:** the Friday reconcile must **diff the Element
descriptions**, not only check that each approved UUID is present and
`completed`. A presence check cannot catch a newer Element declaring an approved
one wrong, which is how this sat undetected for three weeks.

**Reconcile 2026-10-09:** 61 Elements live, unchanged. All 11 approved UUIDs
present and `completed`. No Element created since 2026-09-14 and no description
edited since the 2026-10-02 read — the workspace is static, so the block is
costing imagery and nothing is resolving it on its own. Descriptions diffed in
full per the rule above; result is the three-point breakdown restated above.

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
| Mai Tai | `f981a19d-1e9b-409b-ab82-5dac2578dac6` | ✅ **approved** | `mxt-maitai-CURRENT-202608` · source `mxt-glow-mai-tai.jpg` |
| Fabulous AF Cosmo | `bed44330-1fd6-4896-a120-d41feb4f14f0` | ✅ **approved** | `mxt-cosmo-CURRENT-202608` · source `mxt-glow-fabulous-af-cosmo.jpg` · Shopify title now reads “Fabulous Cosmopolitan” (rename confirmed 2026-09-14 AEO audit) |
| Shiso Sour | `8b0a225a-a278-4a94-befd-a50a89c49754` | ✅ **approved** | `mxt-shiso-CURRENT-202608` · source `mxt-glow-shiso-sour.jpg` |
| Elderflower Gin Gimlet | `b2fa3fbb-a4c9-4c6d-802e-ffc03156fc25` | ✅ **approved** | `mxt-gimlet-CURRENT-202608` · source `mxt-glow-elderflower-gin-gimlet.jpg` |
| Espresso Martini | `607b7da6-a1e6-4e3d-a805-f4f2366b946f` | ✅ **approved** | `mxt-espresso-CURRENT-202608` · source `espresso-martini-5692062.jpg` (bar scene — no `mxt-glow-` asset exists) |
| Piña Colada | `e672b03a-a71c-4ee5-ada7-19330621263c` | ✅ **approved** | `mxt-pina-CURRENT-202608` · source `scene-pina-colada.webp` (beach scene — no `mxt-glow-` asset exists) |

**All 11 flavours are now approved.** Two of them (Espresso Martini, Piña Colada)
were built from lifestyle scene photographs rather than clean studio shots
because Shopify carries no `mxt-glow-` asset for them — their Element
descriptions instruct the model to use only the pouch and ignore the
surrounding scene. If either renders poorly, shoot a studio `mxt-glow-` frame
for it and rebuild.

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
