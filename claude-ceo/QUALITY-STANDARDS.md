# Quality Standards

Every deliverable is checked against these before it appears in a report as "done".

## Hard facts — check these before any copy or creative ships
- **⛔ Free shipping threshold is CONTESTED as of 2026-10-06. Do not quote a
  figure until this is resolved.** This line read "$60 (not $66), matches the
  store product pages". The live default delivery profile says otherwise:

  | Rate (General profile, all 8 AU states/territories) | Threshold | Price | Active |
  |---|---|---|---|
  | Standard | **$100.00 and above** | **$0.00** | yes |
  | Standard | $0 – $99.99 | $7.97 | yes |
  | Express Post — 2 Day | none | $30.00 | yes |
  | Express | $0 – $149 | $30.00 | **no** |

  The delivery profile is what actually charges at checkout, and it sets the free
  threshold at **$100**, not $60. Either the product pages are now out of date or
  the profile was changed; resolving which is a founder call.

  **Copy already shipped with "$60" that needs checking:** Klaviyo template
  `RzebeW` (the Hops & Hooves follow-up, drafted 28 Sept, still unsent to 53
  people), and the Bottle-O Bros draft `r-1960200949237936241` and the generic
  2027 festival pitch `r8934145290925456920`.

  Two other profiles exist and ship free with no threshold: **Event Packs —
  Express Included** (free Express on the 12-packs) and **MXTology Club — Free
  Shipping** (free Standard for members). That is why the $159 packs always
  arrive postage-free.
- **Pouch artwork: `POUCH-ELEMENTS.md` is the ONLY authority.** Never pick a
  Higgsfield Element by name, by description, or by how recent it looks — match
  the **UUID** in that file and check its status is `approved`. Element names
  collide across generations (three different "pornstar" Elements exist) and
  `created_at` does not tell you which label generation an Element depicts.
  **Inferring "newest = current" from a timestamp caused a real failure on
  2026-08-10** — creative shipped on superseded labels. Run the preflight in
  `POUCH-ELEMENTS.md` before every generation; if a flavour is quarantined or
  absent, stop and ask. Never substitute, never fall back to an older Element,
  never describe the pouch in prose instead.
  **⛔ The prose spec in the next paragraph is CONTESTED as of 2026-10-02 and
  must not be relied on. See the BLOCKED note at the top of `POUCH-ELEMENTS.md`:
  the approved `-CURRENT-202608` Elements and the newer `-REAL-2609` Elements
  disagree on whether the flavour artwork is full-bleed or an inset label, and on
  the pouch proportions; and the approved margarita Element's own text says there
  is NO vertical rainbow wordmark, contradicting the line below. Generate no
  pouch imagery until the founder rules.**

  Each approved Element carries the full spec: rectangular foil stand-up pouch,
  flat bottom seal, never glass-shaped, glossy black left panel with the
  iridescent rainbow MXT OLOGY wordmark, flavour name on the right panel,
  Y-shaped window with a flavour-specific liquid colour, white screw cap
  upper-left. Embed `<<<element_id>>>` in the prompt. Elements are only
  supported on `nano_banana_2`, `nano_banana_flash`, `gpt_image_2`,
  `seedream_v4_5`, `seedream_v5_lite` and `cinematic_studio_2_5` — NOT on
  `marketing_studio_image`, which invents labels.
- Product photography on Shopify is current (re-shot late July 2026).

## All content
- On-brand for MXTology: confident, fun, premium cocktail culture. No generic
  AI filler phrases.
- A single clear call to action.
- Grounded in a real product, offer, event, or data point — no invented claims,
  prices, or dates.
- Correct links checked, correct spelling of MXTology.

## Generated pouch imagery — composition rule (added 2026-08-13)
Evidence from 7 generations: **single pouch, upright or held in hand → 5/5 passed.**
Two compositions fail reliably and must not be attempted:
- **Pouch lying on its side** — the model rotates the artwork with it, so the
  wordmark and flavour name render mirrored/upside-down and the foil loses its
  black.
- **Multiple pouches in a scene** — text garbles (`MXTOLDGY`, `TOOHMYS
  MARGARIFA`) and third-party props hallucinate in. One attempt put a real
  competitor dairy brand and a retired, racially-loaded cheese brand in frame.
**Always eyeball every generated image against the real label before it leaves
the session.** Check: MXTOLOGY spelled correctly, flavour name correct and
right-way-up, gradient M monogram present, no third-party trademarks in shot.

## Meta ads
- Hook in the first line; primary text ≤125 chars where possible for the headline.
- Audience and objective stated with the draft.
- Compared against current best-performing ad — state why this should beat it.

## Klaviyo emails
- Subject line + preview text drafted (with one A/B alternative).
- Mobile-friendly single-column layout; alt text on images.
- Correct list/segment named; UTM tags on links.
- Rendered/previewed before being called done.

## Instagram
- Format stated (reel/carousel/single); hook in first 3 words of caption.
- Caption + hashtag set (mix of niche and broad) + suggested post time.
- Visual asset generated or briefed, not just described.

## Festival/event outreach
- Correct contact person and event named; one-paragraph pitch, specific ask,
  and a proposed next step.
- No embellished claims about MXTology's track record.

## Reports
- Numbers cite their source and period.
- Leads with decisions needed, not background.
- Under ~400 words for daily, ~700 for weekly.
