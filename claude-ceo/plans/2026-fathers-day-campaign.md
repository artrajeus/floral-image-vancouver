# Father's Day 2026 — Meta campaign build

**Father's Day (AU): Sunday 6 September 2026.** 18 days out from 19 Aug.
Approved 2026-08-19 as the replacement for the killed snow campaign.

## Built so far

**Campaign `MXT_FathersDay_2026_Conversions` — id `120257707204770197`**
Objective `OUTCOME_SALES`, status **PAUSED**, no budget set, special ad
categories none. Spends nothing until enabled.

## Blocked — two IDs needed from the founder

The ad set and ad cannot be created without these, and I will not guess them
(a wrong pixel id silently breaks purchase optimisation):

1. **Meta Pixel ID** — Events Manager → Data Sources. Needed for
   `promoted_object: {pixel_id, custom_event_type: "PURCHASE"}`.
   Not recoverable from the storefront: Shopify serves it through the
   web-pixels sandbox, so it is not in the page HTML.
2. **Facebook Page ID** — Page → About, or Business Settings → Pages.
   Needed to build the ad creative.

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
