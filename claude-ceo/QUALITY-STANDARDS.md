# Quality Standards

Every deliverable is checked against these before it appears in a report as "done".

## Hard facts — check these before any copy or creative ships
- **Free shipping threshold is $100. RESOLVED 2026-10-09 — the $60 figure is
  dead.** Flagged contested on 2026-10-06; settled today by the founder in
  writing. Replying to Pascal Kensington's question himself at 14:32 ACST he
  wrote: *"standard shipping is free on orders over $100, and it applies to
  every state and territory, including WA, NT and Tasmania."* That agrees with
  the live delivery profile, so the product pages are what is out of date.

  **Copy fixed:** Klaviyo template `RzebeW` (Hops & Hooves follow-up, still
  unsent to 53 people) now reads "Free shipping over $100, every state and
  territory", in both the HTML and plaintext bodies. **Still to check:** the
  store product pages, which are believed to say "$60" and are the original
  source of the error.

  The live rates, for reference: the earlier table below is current.

  | Rate (General profile, all 8 AU states/territories) | Threshold | Price | Active |
  |---|---|---|---|
  | Standard | **$100.00 and above** | **$0.00** | yes |
  | Standard | $0 – $99.99 | $7.97 | yes |
  | Express Post — 2 Day | none | $30.00 | yes |
  | Express | $0 – $149 | $30.00 | **no** |

  The delivery profile is what actually charges at checkout, and it sets the free
  threshold at **$100**, not $60.

  The generic 2027 festival pitch draft `r8934145290925456920` still carries
  "$60" and needs the same fix before it is used. The Bottle-O Bros draft
  `r-1960200949237936241` no longer exists — it was replaced on 2026-10-09 by
  `r3572042073986405144` to `accounts@bottleobros.com.au`, which has not been
  checked against this line.

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
  **⛔ One point in the prose spec below is CONTESTED as of 2026-10-02 and must
  not be relied on: whether the flavour artwork is full-bleed or a separate
  inset label. See the BLOCKED note at the top of `POUCH-ELEMENTS.md`. Generate
  no pouch imagery until the founder rules.** The other two points flagged on
  2026-10-02 were withdrawn on 2026-10-09 — the proportions never conflicted
  (125 × 170mm overall, 140mm body, both Elements right), and the rainbow
  wordmark claim was this file's own error, corrected below.

  **Corrected 2026-10-09 — the pouch has NO vertical rainbow wordmark.** This
  paragraph used to say the pouch carried "the iridescent rainbow MXT OLOGY
  wordmark". All eleven approved Elements state the opposite in their own text:
  *"both HORIZONTAL — NO vertical rainbow wordmark."* The rainbow MXT-over-OLOGY
  lockup belongs to the **Party In A Box mailer carton lid**, not the pouch.

  Each approved Element carries the full spec: rectangular foil stand-up pouch,
  flat bottom seal, never glass-shaped, 125mm wide × 170mm tall including the
  top seal band, glossy black body with the gradient **M** monogram lower-left
  and "MXTOLOGY" in white capitals directly beneath it, both horizontal,
  flavour name set vertically on the right panel,
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
