# Mundi Mundi 2026 — Buyer Audience, Emails & UGC Competition

**Built:** 8 Aug 2026. Purpose: separate everyone who came through the Mundi Mundi Facebook campaign into their own Klaviyo audience, email them before the Bash (20–22 Aug), and run a best-post competition through the event.

## The audience

- **Klaviyo list `Ts4LQR` — "Mundi Mundi Bash 2026 — Campaign Audience".** Seeded with all 5 Bash Pack purchasers from Shopify (orders #1843, #1860, #1862, #1866, #1868 — incl. the internal test order, useful for QA). Each profile also carries custom properties `mundi_mundi_2026: bash-pack-buyer` / `event_audience: mundi-mundi-2026` so they stay identifiable forever, independent of the list.
- **Why a list, not a segment:** the Klaviyo connector can read segments but not create them, and anonymous ad-click visitors can't be emailed anyway — only identified profiles can. The list captures every *actionable* person today.
- **To auto-capture future FB-ad people, create this dynamic segment in the Klaviyo UI (2 min):** Lists & Segments → Create Segment → "Mundi Mundi 2026 — All Touches" with OR conditions: (1) *Placed Order where item = The Bash Pack — 12 Glass-Free Cocktails for Mundi Mundi*, (2) *person is in list "Mundi Mundi Bash 2026 — Campaign Audience"*, (3) *Active on Site / Viewed Product where utm_campaign contains "mundi"* (available if Klaviyo web tracking captured the UTM). Going forward the Gympie campaign's `utm_campaign=gympie-muster-2026` convention makes this per-event segmentation automatic.

## The emails (both DRAFT — review and send)

| Campaign | When (AEST) | Content |
|---|---|---|
| `01KZFXVFT16QHYKXTK5WA76ADE` — Buyers E1 "Comp Launch + Top-Up" | **Sun 9 Aug, 9:00am** | Thanks/anticipation, last top-up call (last post Wed 12 Aug), competition announcement |
| `01KZFXVKZY37ZT6697HG0N6WG8` — Buyers E2 "See You on the Plains" | **Tue 18 Aug, 5:00pm** | Pre-departure checklist (ice, campsite-only BYO), competition reminder — no hard sell |

Smart sending is off (tiny warm list; both emails matter). UTM: `mundi-buyers-2026`.

## The competition — "Best Campsite Bar on the Plains"

- **Enter:** post a photo/video of your MXTOLOGY camp bar at the Bash on Facebook or Instagram, tag **@mxtology** + **#MXTologyBash**.
- **Prize:** $250 MXTology Bar Tab gift card (existing SKU — near-zero hard cost).
- **Judging:** best post chosen on creativity — a game of skill, not chance, so no lottery/trade-promotion permit needed in any state. Entries close 11:59pm AEST Mon 31 Aug; winner announced Tue 1 Sep.
- **Why buyers-only first:** 5 people with packs in hand are the guaranteed content source; the public social posts widen the funnel.

### Social announcement copy (ready to post from @mxtology once prize is confirmed)

> 🏜️ **CALLING EVERYONE HEADED TO THE MUNDI MUNDI BASH.** The best campsite bar on the Plains wins a **$250 MXTOLOGY Bar Tab**. Post your camp bar setup — fairy lights, red dirt, Espresso Martini in hand — tag @mxtology and #MXTologyBash. Best post takes the tab. Closes 11:59pm AEST 31 Aug. Winner announced 1 Sep. 18+, judged on creativity. Drink responsibly — BYO lives at the campsite. 🍸

Post timing: Mon 10 Aug (feed + story), re-share entries through Bash weekend, winner post Tue 1 Sep. The winner post doubles as launch creative for the Gympie/Deni campaigns ("this could be your campsite").

## Post-event follow-through (per playbook §T+1)

1 Sep winner email to list `Ts4LQR` → Club subscription offer → tag conversions. When Mundi Mundi 2027 dates drop, this list is the first re-arm audience.
