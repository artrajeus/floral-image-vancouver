# Father's Day 2026 — Meta campaign build

**Father's Day (AU): Sunday 6 September 2026.** 18 days out from 19 Aug.
Approved 2026-08-19 as the replacement for the killed snow campaign.

## Built so far

**Campaign `MXT_FathersDay_2026_Conversions` — id `120257707204770197`**
Objective `OUTCOME_SALES`, status **PAUSED**, no budget set, special ad
categories none. Spends nothing until enabled.

## Account IDs — RESOLVED 2026-08-19, do not ask for these again

| Value | ID | Where it came from |
|---|---|---|
| Meta ad account | `1058059948561713` | standing |
| **Facebook Page ID** | **`137867822740681`** | founder supplied 2026-08-04; used to create the burst 1 ad. Recovered from the session transcript. |
| **Meta Pixel ID** | **`723291006083300`** | live storefront web-pixels config (`pixel_type: facebook_pixel`) at mxtology.com.au |
| Instagram actor | via Windsor field `instagram_actor_id` | per-ad |

**How to recover them if lost again:** the page id is in the session transcript
(`grep '"page_id"'`). The pixel id is in the storefront HTML — fetch
`https://mxtology.com.au/` and grep `webPixelsConfigList` for
`"pixel_type":"facebook_pixel"`. It is NOT in the visible page source via a
naive `fbq(` grep, which is why the first attempt missed it.

## BUILT 2026-08-19 — all paused, zero spend

| Object | ID | State |
|---|---|---|
| Campaign `MXT_FathersDay_2026_Conversions` | `120257707204770197` | PAUSED · OUTCOME_SALES · CBO daily **A$50** · `LOWEST_COST_WITHOUT_CAP` |
| Ad set `FathersDay_AU_25-65_Broad` | `120257711507220197` | PAUSED · OFFSITE_CONVERSIONS/PURCHASE on pixel `723291006083300` · AU 25–65 broad + Advantage · ends **1 Sept 23:59 ACST** |
| Ad A — Skip the socks | `120257711514440197` | PAUSED |
| Ad B — Disaronno / Maker's / fresh lemon | `120257711522650197` | PAUSED |
| Ad C — He doesn't want another mug | `120257711526120197` | PAUSED |

All three point at `/pages/build-your-case` with
`utm_source=facebook&utm_medium=paid&utm_campaign=fathersday-2026` plus a
per-ad `utm_content`.

**Build gotcha, same as burst 1:** the account default demands a bid cap, so
`create_adset` 400s with *"Bid amount or bid constraints required for bid
strategy"*. Fix is a three-step order — `set_campaign_budget` first (bid strategy
cannot be set on a budget-less campaign), then `update_campaign`
`bid_strategy=LOWEST_COST_WITHOUT_CAP`, then `create_adset` with no ad set
budget (CBO carries it). Record this; it has now cost two builds.

**Creative:** real Shopify product photography, not generated art —
`mxt-glow-amaretto-whisky-sour.jpg` (A, B) and `espresso-martini-5692062.jpg`
(C). Both verified HTTP 200 image/jpeg before use. Note `mxt-glow-espresso-martini.jpg`
does **not** exist (404) — consistent with `POUCH-ELEMENTS.md`. Zero label-garbling
risk versus generated pouches.

**Windsor returns no rows for this campaign** — expected, paused campaigns
produce no insights. Verify in Ads Manager, not Windsor.

## Inventory reality — this shapes the whole campaign

| Gift SKU | Price | Units |
|---|---|---|
| 🍸 THE WHOLE GANG — all 11 | $132 | **20** |
| MXTology Club — Whole Gang | $132 | 3 |
| 10-packs (Amaretto/Cosmo/Mai Tai/Pornstar/Piña/Gimlet/Berry/Fireball) | $120 | 2–6 each |

**The obvious Father's Day hamper is nearly out of stock.** All bundles
together are roughly $5–6k of sellable value, and the Whole Gang alone caps at
$2,640. A campaign pointed at bundles would stock out in days.

Singles are deep: Pornstar 175, Piña Colada 141, Fabulous Cosmopolitan 98,
**Amaretto Whisky Sour 89**, Espresso Martini 87, Mai Tai 50.

**Therefore: destination is `/pages/build-your-case`, not a bundle page.**
That is also where the winning MOF video sent traffic (2.63× ROAS over 30 days),
so it is proven. Mention the Whole Gang in copy as the premium option, but do
not make it the landing page.

**Hero flavour: Amaretto Whisky Sour** — Disaronno and Maker's Mark, "low light,
quiet jazz" — the most dad-shaped product in the range, and 89 units deep.

## Ad copy — 3 variants for founder approval

Audience: AU, 25–65, broad + interests (whisky, craft spirits, gifting).
Objective: sales, purchase optimisation. Free shipping over **$60**.
Benchmark to beat: `#3 - MOF` video at 4.90% CTR / 2.63× ROAS. The bar for
these statics is lower — `Static Engine` runs 14% CTR at ~1 purchase on $225,
so **judge these on purchases, not CTR.**

**A — "Skip the socks"** *(matches the Klaviyo teaser angle)*
> Skip the socks. Dad's bar, sorted.
> Real cocktails — Amaretto Whisky Sour, Espresso Martini, Mai Tai — made by
> bartenders, sealed in a pouch, no shaker required. Build his case, free
> shipping over $60. Order by 1 Sept for Father's Day.
> CTA: SHOP_NOW → /pages/build-your-case

**B — "The bar he'd build"**
> Disaronno. Maker's Mark. Fresh lemon. No bartender required.
> The Amaretto Whisky Sour is the one Dad will actually finish. Pick his six,
> we ship it. Free shipping over $60.
> CTA: SHOP_NOW → /pages/build-your-case

**C — "He doesn't want another mug"**
> He doesn't want another mug.
> Eleven bar-made cocktails, pouched. Build Dad a case of the ones he'd
> actually order. Free shipping over $60 — order by 1 Sept.
> CTA: SHOP_NOW → /pages/build-your-case

## Creative

Generate from the **approved** Elements in `POUCH-ELEMENTS.md` — UUID match,
single pouch, upright or held in hand only (the two failing compositions are
banned). Lead flavour Amaretto Whisky Sour
(`aa8f8e8b-b01b-4946-95a4-76ad5b4dcf6d`), second Espresso Martini
(`607b7da6-a1e6-4e3d-a805-f4f2366b946f`). Every frame eyeballed against the real
label before it leaves the session.

## Timing

- **Order-by date: Mon 1 September** — five clear business days to 6 Sept.
  Founder to confirm against actual courier cut-offs before this goes in copy.
- Ads should be live by **Fri 21–Mon 24 Aug** to give Meta learning time.
- Conflict noted: burst 2 is Thu 27 Aug. This campaign runs through it and will
  contaminate pair 2 — accepted on 2026-08-19, since Muster ends 21 Aug and MOF
  has been at $0 since 14 Aug, leaving the account with no prospecting.
