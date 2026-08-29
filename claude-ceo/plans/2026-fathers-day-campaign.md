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

## STATUS 2026-08-27 — day 8 paused, five days to the order-by

Built 2026-08-19. Still PAUSED. A$0 spent. Meta data for 20–26 Aug shows only
`MXTology – ATC Retargeting` and `MXT-TEST | Static Engine` running —
`MXT_FathersDay_2026_Conversions` (`120257707204770197`) has never delivered an
impression.

**The clock:** Father's Day is Sun 6 Sept. Order-by for delivery is Mon 1 Sept.
That is 5 days. A conversions campaign needs roughly 3 days to exit the learning
phase, which means the useful window closes at the end of this week — after that
the campaign can only be launched as a last-minute urgency play at lower
efficiency, and after 1 Sept it cannot be launched at all.

**Blocker:** budget. Under the standing rule the agent does not set or change ad
spend. The campaign is fully built — CBO A$50/day, `LOWEST_COST_WITHOUT_CAP`,
ends 1 Sept 23:59 ACST, three ads on real Shopify photography, destination
`/pages/build-your-case`. It needs one word from the founder to go live.

**Cost of the delay so far:** 8 days of a 13-day window. Meanwhile the account
spent A$374.87 across 20–26 Aug on retargeting and the static test for
A$961.97 in Meta-attributed value, with three of the last four days returning
zero attributed revenue.

## OUTCOME 2026-08-30 — window closed, campaign not run

Order-by for Father's Day delivery is Mon 1 Sept. As of today the campaign has
never served an impression and no budget decision has been received across
11 days (built 19 Aug; raised in every daily brief 19–30 Aug and in the 28 Aug
weekly review). A conversions campaign cannot exit the learning phase inside the
remaining window, so the campaign will not run for Father's Day 2026.

Recording this as fact rather than raising it a twelfth time. It is not being
deleted — it is being stood down.

**What was spent to get here:** agent build time only. A$0 media. Nothing was
launched, so there is no wasted spend — only a missed occasion.

**What already went out:** a Father's Day teaser email on 22 Aug to 1,047
engaged subscribers — 54.1% open, 0.77% click, **0 orders**, 12 unsubscribes.
The list has heard the Father's Day story once and did not act on it. The paid
campaign was the part that could have converted, and it did not run.

**Reusable assets, all still current:**
- Campaign `120257707204770197`, ad set `120257711507220197`, ads
  `...440197` / `...650197` / `...126120197` — all PAUSED, `OUTCOME_SALES`, CBO
  A$50/day, `LOWEST_COST_WITHOUT_CAP`.
- Three ad concepts on real Shopify photography: "Skip the socks",
  "Disaronno / Maker's / fresh lemon", "He doesn't want another mug".
- Destination `/pages/build-your-case` with `utm_campaign=fathersday-2026`.

**Next occasion to repoint at:** Christmas. The gifting angle and the
build-your-case destination carry over unchanged; the copy needs a seasonal
rewrite and the end date and UTM need updating. Recommend building it in
early October so the budget decision has room to be made before the window
rather than inside it.

**The process lesson, stated plainly:** a campaign that needs a founder decision
to spend must have that decision requested *before* it is built, with a stated
drop-dead date. Building first and asking daily produced eleven asks and one
missed occasion.
