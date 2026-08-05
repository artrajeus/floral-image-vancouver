# Experiment: Weekly 24h Traffic Burst ("Thursday Burst")

Status: **Approved by founder 2026-07-28 — starts with the 2026-08-03 Weekly Kickoff.**
Owner: Claude CEO (drafts + measurement), founder (launch approvals).

## Hypothesis

A cheap 24-hour traffic-objective burst (observed: ~$5 CPM / $0.21 CPC on the
2026-07-25 "National Margarita Day — 24h Traffic (LP v2)" campaign, vs ~$40–50
CPM on purchase campaigns) refills the retargeting pool and, paired with a
same-day email/IG hook, lifts *full-week* revenue and blended ROAS via the
purchase-optimised campaigns in the following days.

## Design (6 weeks, 3 on / 3 off, alternating)

| Week starting (Mon, Adelaide) | Condition | Burst day |
|---|---|---|
| 2026-08-03 | **BURST** | Thu 2026-08-06 |
| 2026-08-10 | control | — |
| 2026-08-17 | **BURST** | Thu 2026-08-20 |
| 2026-08-24 | control | — |
| 2026-08-31 | **BURST** | Thu 2026-09-03 |
| 2026-09-07 | control | — |

Do not move burst days to chase events; alternation is the point. Everything
else (evergreen campaigns, email cadence) stays on its normal schedule in both
conditions.

## Burst spec (each burst week, drafted at Monday kickoff)

- Meta campaign: Traffic objective, 24h schedule (Thu 9:00–Thu 9:00 ACST),
  budget **A$80–100** (match the Margarita Day burst), broad targeting, all
  placements — clone the structure of "National Margarita Day — 24h Traffic
  (LP v2)".
- Creative: one hook per burst (kickoff drafts it; founder approves).
- **No discount code.** (Reversed 2026-08-04.) The original design called for a
  unique code per burst as hard attribution, but a code present only in burst
  weeks changes the offer and makes burst weeks incomparable to control weeks —
  it would have measured "burst + discount" vs "nothing". Shopify referrer
  attribution is confirmed working (last 14 days: 30 orders / $4,110 attributed
  to social/facebook), and the burst ad carries its own utm_campaign, so
  attribution is already covered without altering the offer.
- **UTMs** on the ad link: `utm_source=facebook&utm_medium=burst&utm_campaign=
  burst-YYYYMMDD`.
- Same-day hook on other channels: one IG post; email only if one is already
  scheduled that week (don't add extra sends just for the burst).
- Launch checklist requires founder sign-off on: creative, budget, code, dates.

## Measurement (Friday review + final read after week 6)

Track per week in the review scorecard:
1. Full-week Shopify revenue and orders.
2. Blended ROAS = week revenue ÷ week Meta spend (burst spend included).
3. Burst-code redemptions and UTM-attributed orders/sessions (burst weeks).
4. ATC Retargeting + Cold Prospecting clicks/conversions in the 3 days
   post-burst vs same days in control weeks (the mechanism check).
5. IG reach and follower adds on burst day.

## Decision rule

After the third burst week (w/c 2026-08-31): compare the 3 burst weeks vs the
3 control weeks on blended ROAS and revenue.
- Burst weeks clearly better → make it a standing weekly play.
- No clear difference or worse → kill it. Total cost of the answer ≤ ~A$300.
- Confounders (a sale, stockout, or unrelated spike in any week) must be noted
  in that week's review and the affected pair discounted.

## Held constant for the duration (decided 2026-08-04)

To keep burst vs control comparable, these do NOT change mid-experiment:
- **Google Ads — parked until after week 6.** Founder decision; launching a new
  channel mid-test would make burst and control weeks incomparable. Revisit at
  the mid-September wrap.
- **$120 Seoul Tonic free-gift tier — deferred** for the same reason; the clean
  pre-experiment window closed on 2026-08-03.
- **Free-shipping threshold — unchanged at $60.** (Founder confirmed $60 on
  2026-08-04; earlier notes in this file and in briefs said $66, which was wrong.
  The store product pages say "Free shipping over $60". Evidence it works either
  way: 8 of the last 50 orders sat at exactly $72 — six units, the cheapest
  build-your-box basket. All customer-facing copy must say **$60**.)
- **Meta budget — unchanged.** If performance demands action, refresh creative
  rather than cut budget; budget is the control variable.
- **Email cadence — identical across burst and control weeks.** Never add a send
  only because it is a burst week.

## Log

- **Burst 1 built and staged 2026-08-04.** Meta campaign `120257261774290197`,
  ad set `120257261777680197` (broad AU 18+, all placements, hard end Fri
  2026-08-07 09:00 ACST), ad `120257271191510197`. Traffic objective,
  A$90 lifetime, LOWEST_COST_WITHOUT_CAP (the account default demanded a bid cap,
  which would have throttled cheap reach). Destination: build-your-own box with
  `utm_source=facebook&utm_medium=burst&utm_campaign=burst-20260806`.
- **Enabled early in error 2026-08-04, then paused.** The create_adset action has
  no start_time parameter, only end_time — so enabling before Thursday spreads the
  lifetime budget across days instead of 24 hours. Spent A$9.85 before pausing.
  **Early read is strongly positive: $5.39 CPM, $0.16 CPC, 3.29% CTR, 1,826
  impressions** — cheaper than the Margarita Day burst ($11 CPM) and ~7× cheaper
  than the evergreen campaign (~$37). Re-enable scheduled for Thu 09:00 ACST via
  routine `trig_01LxSWHT9umLqy4AdDuaaw1A`; ~A$80 remains.
  **Lesson for future bursts: always pause until launch morning, since start time
  cannot be set through the connector.**
- **Burst 1 launched 2026-08-06 09:01 ACST** on founder instruction, via Windsor
  `enable_campaign` on campaign `120257261774290197`. Verified after the call:
  campaign, ad set and ad all `ACTIVE`; ad set end time `2026-08-07T07:30+0800`
  = Fri 09:00 ACST, so the hard 24h stop is intact. Settled pre-launch spend from
  the early-enable incident was **A$10.47** (1,939 impressions, 64 clicks,
  $5.40 CPM, $0.164 CPC, 3.30% CTR), leaving **~A$79.53** to run across the
  window. 2026-08-05 returned no spend row at all, confirming the pause held for
  the full day. Windsor showed no rows for 06-08 at launch+2min — its Meta sync
  lags, so day-of delivery must be read later, not at enable time.
- **New campaigns to track as confounders (both launched 2026-08-04):**
  `MXT_MundiMundi_2026_Conversions` — this is a **festival win**, generated by the
  founder's own outreach list (Mundi Mundi Bash), with a client signed on
  2026-08-04 off the back of those emails — and
  `MXT-TEST | Static Engine | Sales`.
  Day-one spend A$48.05 and A$15.19; account daily spend rose from ~A$185 to
  A$230.75.
  **Mundi Mundi runs 2026-08-04 to 2026-08-10 only** (order cut-off for festival
  delivery), i.e. almost entirely inside burst week 1 and not inside control week
  1. It is a deadline-driven urgency campaign, so it will inflate burst week 1's
  revenue independently of the burst. **Pair 1 (burst w/c 03-08 vs control w/c
  10-08) is therefore compromised for the weekly-aggregate decision rule.** The
  burst's own direct metrics (CPM, CPC, CTR, UTM-attributed orders, post-burst
  retargeting lift) remain valid because they are separable by campaign.
  Account is clean from 2026-08-11 onwards.
- Measurement confirmed working
  end to end: Windsor (Meta spend/CPM/reach + Instagram) restored 2026-08-04 on
  the aaron@mxtology.com.au trial; Shopify covers code redemptions and UTM
  orders. Note: Windsor trial expires ~2026-09-03, around week 4 — renew or move
  to Basic before then or the back half of the data is lost.
  Context: Canberra Uni gig (Reece Mastin) falls Fri 7 Aug, the day after.
