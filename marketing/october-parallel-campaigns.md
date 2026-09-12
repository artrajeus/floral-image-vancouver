# Three Parallel Event Campaigns — built 9–10 Sep 2026

Running concurrently so Meta gets conversion data from three distinct buyer profiles at once instead of learning one audience at a time.

## Shipping change (applies to all three)

"FREE Express Post included" is retired while there's runway. All three packs now read **"Free shipping"** and carry an honest standard-post cut-off. Express comes back closer to each event as a switchable upgrade — that's the margin play, and it also gives each campaign a second urgency beat.

Variant titles are now `12 Pack — Free Shipping` on all three SKUs.

## The three

| | Dragon Dreaming | Deni Ute Muster | Savannah in the Round |
|---|---|---|---|
| Dates | **25–28 Sep** (early entry Thu 24) | 2–3 Oct | 8–11 Oct |
| Days out (from 12 Sep) | **13** | 20 | 26 |
| Where | Wee Jasper NSW, Lake Burrinjuck | Deniliquin NSW | Kerribee Park, Mareeba, Tropical Nth QLD |
| Audience | 18–35 bush doof / lakeside camping | 18–45 rural, utes, country | 35–65 regional mainstream, country/rock |
| Product | The Lakeside Pack `8646991544354` | The Deni Pack `8639578243106` | The Savannah Pack `8646719045666` |
| SKU | `MXT-DRAGON-12` | `MXT-DENI-12` | `MXT-SAV-12` |
| Free-shipping cut-off | **Mon 14 Sep** | Fri 19 Sep | Fri 18 Sep (FNQ transit) |
| Status | **ACTIVE** — 20 units | **ACTIVE** — 20 units | **ACTIVE** — 20 units |

## The hook for each — all drawn from the event's own rules

- **Dragon Dreaming — "There's no bar at Dragon Dreaming. You are the bar."** Fully BYO with **no alcohol sold on site at all**, glass confiscated at the gate, barefoot festival. Whatever you carry in on Thursday is the whole weekend. Strongest scarcity story of the three.
- **Deni — "You get 30. Make twelve of them count."** Deni's conditions name *pre-mix spirits* inside the 30-can carton allowance. Page carries a 30-pip visual: twelve lit, eighteen empty.
- **Savannah — "Four days in the tropics. Make camp the good bit."** The precinct is completely dry and glass-free, so camp is the only bar you control. Pack is weighted tropical (2× Piña Colada, 2× Margarita, Mai Tai) for 30°C on the Tablelands.

## Date correction

Dragon Dreaming 2026 is **25–28 September**, not the October long weekend — it's the *earliest* of the three, ahead of Deni. Verified on the event's own site and FAQ. Its free-shipping window closes Monday 14 September; after that it needs express to make the gates.

## Pages

All three rebuilt on the Gympie house template (dark #0b0b10, pink/cyan/green, hero → buybox → contents → full-bleed band → lanyard split → Open·Close·Shake·Sip → price comparison → Ramsay quote → six cards → event rules → shipping → FAQ → non-affiliation fine print), each with an event-specific section: the allowance pips (Deni), the dry-precinct in/out split (Savannah), the no-bar panel (Dragon Dreaming).

Imagery is generated per event and matched to the actual setting — dusty ute paddock, tropical pandanus and savannah grass, eucalypt lake bank. **No campfires in any of them.**

## Imagery — locked (12 Sep)

The approved frame is the Deni esky shot: a weathered white **Esky**-brand cooler open on a red ute's folded tailgate, three MXTOLOGY pouches plus two Great Northern Super Crisp cans and a brown stubby in crushed ice, golden-hour dust. Savannah and Dragon Dreaming were generated **from that exact image as a reference**, changing only the background and the three flavours, so all three read as one shoot.

- Deni — `hf_20260910_043527_34b08cd3` · Espresso Martini / Pornstar Martini / Tommy's Margarita · dusty Riverina paddock
- Savannah — `hf_20260910_073230_cbe1ddaf` · Piña Colada / Tommy's Margarita / Mai Tai · pandanus, savannah grass, red earth, tablelands
- Dragon Dreaming — `hf_20260910_073230_729925d1` · Espresso Martini / Pornstar Martini / Amaretto Whisky Sour · Lake Burrinjuck, pale-trunked gums

### Lanyard proof shots (12 Sep)

The Gympie campground dancing shot is the approved template for "people actually wearing it". Scene-specific versions were generated from that frame for each event, so the energy, framing and lanyards carry across while the setting and styling match the crowd:

- Deni — `hf_20260912_045513_9212a81c` · dusty Riverina paddock, rows of utes with roll bars, swags, hats and boots
- Savannah — `hf_20260912_045518_cb45c8b4` · pandanus palms, red earth, tablelands behind, dressed for 30°C, no flannel
- Dragon Dreaming — `hf_20260912_045311_5b593b98` · Lake Burrinjuck, pale gums, bucket hats, barefoot — deliberately not country

### Text on labels — what actually works

The live Deni close-up shipped with butchered label text (misspelled MXTOLOGY, garbled flavour names). Root cause is **pixel density, not prompting**: at wide framing the lettering is too small for the model to hold, and iterative "fix this word" passes just move the error somewhere else — each pass corrects what you name and garbles what you don't.

**The fix is to shoot tight.** A close-up where the pouches fill most of the frame renders MXTOLOGY, the flavour names, ESKY and GREAT NORTHERN all correctly in one pass. Any shot where label text needs to be legible must be framed tight; any wide shot should keep the pouches small enough that the text reads as texture rather than words.

**Rule for all future images:** only the `-CORRECTED-2608` MXTOLOGY pouch elements already loaded in Higgsfield, plus `mxt-pouch-SCALE-2609` (`a2292171-0137-47e3-9395-3771d7b84916`) for size. Never let the model invent a pouch. Scale that's now locked in: pouch 125mm × 170mm, **1.26× a 375ml can's height and 1.8× its width**, can rim landing ~80% up the pouch just under the Y-window top; stubby 1.3× taller than the pouch with its shoulder at the pouch's top seal.

The in-page hero/band images on all three product pages were swapped to match — the old generic-pouch renders are gone from both the galleries and the description HTML.

## Live status (12 Sep)

All three products are **ACTIVE at 20 units each** (60 total across one physical pool — the same twelve pouches, three badges). Bash Pack still holds 19; Grand Final Pack 100.

### Email

| Campaign | Send (AEST) | Klaviyo ID | State |
|---|---|---|---|
| Dragon Dreaming E1 "There's no bar at Dragon Dreaming" | **Sun 13 Sep, 10:00am** | `01M29YWRMXRYG2DPK1QB6B471C` | Draft — press send |
| Deni E1 "You get 30. Make 12 of them count." | Tue 16 Sep, 10:00am | `01M22AR6VSNNJWXNQ8GN2P6H7X` | Draft |
| Deni E2 "Last day for free shipping to Deni" | Fri 19 Sep, 9:00am | `01M22AR91J64XXX27GSDDFFVGM` | Draft |

Both Deni emails were rewritten: "Free Express Post" and the 28 Sep last-post date are gone, replaced by free shipping with a **Fri 19 Sep** cut-off, matching the page. E2 moved from 28 Sep to 19 Sep; E1 moved off Mon 14 Sep to Tue 16 Sep so the engaged list isn't hit two days running with Dragon Dreaming's Sunday send. All carry per-event UTMs.

Note the Klaviyo quirk: templates already bound to a campaign message return 404 on update. The fix is create-new-template → `assign_template_to_campaign_message`, which clones it onto the message.

## Still open

1. **Savannah has no email arc yet.** Its cut-off is Fri 18 Sep — needs an E1 this coming week.
2. **Meta: three campaigns specced, none launched.** This is the actual revenue lever — Mundi ran 5.5× ROAS at 11.7% CTR while email converted 1 order per 1,199 recipients. Dragon Dreaming's window is nearly shut; if only one runs, run that one. Needs budget sign-off.
3. Confirm the free-shipping cut-offs against real dispatch times, especially Mareeba.
4. The 20/20/20 split is nominal against one physical pouch pool — if a single event sells through hard, rebalance the other two down before they oversell.
