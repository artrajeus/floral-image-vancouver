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

## Scorecard — Week 1 (BURST), w/c 2026-08-03

Recorded 2026-08-07 15:00 ACST. **Friday was incomplete at the time of writing**,
so weekly aggregates are stated Mon–Thu vs Mon–Thu against the control week.

| Measure | This week (3–6 Aug) | Prior week (27–30 Jul) |
|---|---|---|
| Shopify revenue | $3,405.74 | $1,127.61 |
| Orders | 28 | 11 |
| Meta spend | $1,049.56 | $752.62 |
| Blended ROAS | 3.25× | 1.50× |
| Meta CPA | $41.98 | $83.62 |

**Burst 1 direct metrics** (6 Aug 09:01 → 7 Aug 09:00): spend **$72.21**,
14,732 impressions, 371 clicks, 13,043 reach, **CPM $4.90**, CPC $0.195,
CTR 2.52%. Same-day CPM on `#3 - MOF` was $45.38 — the burst bought reach
**9.3× cheaper**. Total including the 4 Aug accidental spend: $82.68 of $90.
**306 Shopify sessions** attributed. No discount code (by design).
IG on burst day: reach 3,309, 11 interactions (best in three weeks), **+0 followers**.

**Not yet readable:** the retargeting mechanism check needs 7–9 Aug complete.
Do this at Monday's kickoff, not here.

**Confounder — Mundi Mundi.** On 6 Aug it produced $959.97 of the $1,510.77
Meta-attributed revenue (64%) on $119.02 spend. Pair 1 remains compromised for
the weekly-aggregate rule, exactly as predicted. The week's headline lift must
not be credited to the burst.

### Measurement corrections found this week
- **The planned `utm_campaign=burst-20260806` tag did not land.** Shopify sessions
  show the Meta **campaign id** (`120257261774290197`) as `utm_campaign` instead.
  Attribution still works — read bursts by campaign id, not by the burst- slug.
  Update the Burst spec's UTM line rather than changing the ads mid-experiment.
- **Burst-attributed orders cannot be read from ShopifyQL.** `utm_campaign` exists
  on the `sessions` table but not on `sales`, so only sessions are countable.
  Order-level attribution has to come from the referrer breakdown
  (`social/facebook`) or from Meta itself. Measurement item 3 above overstates
  what the tooling can deliver.

## Scorecard — Week 2 (control), w/c 2026-08-10

Recorded 2026-08-17 06:00 ACST, full week complete.

| Measure | Control wk (10–16 Aug) | Burst wk (3–9 Aug) |
|---|---|---|
| Shopify total sales | $6,213.34 | $7,600.94 |
| Orders | 44 | 59 |
| AOV | $141.21 | $128.83 |
| Meta spend | $1,700.12 | $1,891.43 |
| Blended ROAS | 3.65× | 4.02× |
| Meta-attributed revenue | $4,610.25 | $6,922.97 |

**These two weeks are not comparable and the difference must not be read as a
burst effect.** Pair 1 was dropped on 2026-08-10 because Mundi Mundi ran across
both sides. This table is recorded for the business scorecard only.

## PAIR 2 IS ABOUT TO REPEAT THE PAIR-1 FAILURE (found 2026-08-17)

`MXT_Muster_2026_Conversions` (campaign `120257582631120197`, ad set
`Muster_Interests_QLD_NthNSW` / `120257582642200197`) is `ACTIVE` with
**`adset_end_time` = 2026-08-21T14:00:00+0800 = Fri 21 Aug 16:00 ACST.**

That places it Mon 17 – Fri 21 August: **entirely inside burst week 2, and not at
all inside control week 2 (24–30 Aug).** It is a deadline-driven festival
campaign scaling hard — $0.47 → $131.01 → $189.97 across its first three days, at
8.3–10.9% CTR — so it will likely add $800–1,000 of spend and a revenue spike to
the burst week alone. The burst itself is A$80–100. The confounder is an order of
magnitude larger than the signal.

This is the same shape as Mundi Mundi, which forced pair 1 to be dropped. Running
burst 2 on Thu 20 Aug as scheduled would leave **zero clean pairs out of three**
and the experiment unanswerable at full cost.

**APPROVED BY FOUNDER 2026-08-17: burst 2 slips to Thursday 27 August.**
w/c 2026-08-17 is now a no-burst week. The schedule below is the live schedule.

| Week starting (Mon) | Condition | Burst day |
|---|---|---|
| 2026-08-17 | *(skipped — Muster running)* | — |
| 2026-08-24 | **BURST** | Thu 2026-08-27 |
| 2026-08-31 | control | — |
| 2026-09-07 | **BURST** | Thu 2026-09-03 → moved to Thu 2026-09-10 |
| 2026-09-14 | control | — |

Muster ends 21 Aug, so 24 Aug onwards is clean. Cost: one week of delay, and the
final read moves to late September. **The Windsor trial expires ~2026-09-03 and
must be renewed regardless** — under the slipped schedule it is load-bearing for
the back half of the data, not optional.

*(Not taken)* Alternative if the founder wants to hold the date: run Thu 20 Aug and read burst 2
on direct/mechanism metrics only (CPM, CPC, CTR, campaign-id-attributed sessions,
post-burst retargeting lift), abandoning the weekly-aggregate rule entirely. That
is defensible — campaign-separable metrics survive contamination — but it changes
the experiment's decision rule mid-flight and should be recorded as such.

**Standing lesson, now twice observed:** this account runs deadline-driven
festival campaigns on the founder's own outreach calendar, and those are the
business's real revenue driver. Weekly-aggregate A/B design is structurally
fragile here. Any future test should be designed on campaign-separable metrics
from the start.

## Week 3 (w/c 2026-08-17) — SKIPPED, not a study week

Recorded Fri 2026-08-21 15:10 ACST. Founder approved the one-week slip on
2026-08-17, so this week carries **no burst and is not a control** — it is
excluded from the design entirely. The live schedule is: BURST Thu 27 Aug,
control w/c 31 Aug, BURST Thu 10 Sep, control w/c 14 Sep.

Business numbers for the record (Mon–Fri, Fri partial at time of writing):

| Measure | This week (17–21 Aug) | Prior week (10–14 Aug) |
|---|---|---|
| Shopify revenue | $2,154.97 | $4,447.97 |
| Orders | 20 | 29 |
| AOV | $107.75 | $153.38 |
| Meta spend | $853.07 | $1,268.58 |
| Meta-attributed revenue | $1,425.97 | $3,264.97 |
| Meta ROAS | 1.67× | 2.57× |
| Meta CPA | $85.31 | $57.66 |
| **Blended ROAS** | **2.53×** | **3.51×** |

Revenue down 51.5% week on week on 31% fewer orders.

**Confounders this week**
- `MXT_Muster_2026_Conversions` ran Mon–Fri: **$637.43 spend, $1,295 attributed,
  2.03×**. It ends **Fri 21 Aug 16:00 ACST**. Its absence from next week is
  itself a step change to note when reading the 27 Aug burst.
- `#3 - MOF` spent **$0 all week** (last spend 13 Aug). The account's historic
  workhorse is gone, so week-on-week comparisons now span two different account
  structures.
- `Snow Season 2026 — Espresso Martini — Seed` ran 2.5h on 17 Aug ($1.02) and was
  killed on 19 Aug — negligible, but logged.
- **A new always-on prospecting campaign (`MXT_FathersDay_2026_Conversions`,
  `120257707204770197`) is built and paused.** If it launches before Thu 27 Aug it
  contaminates the burst week. Founder accepted that trade on 2026-08-19; record
  it against pair 2 when the burst is read.

**Element reconciliation (Friday step 2a): clean.** All 11 approved UUIDs in
`POUCH-ELEMENTS.md` are live and `completed`. The 19 stale Elements are still
present and still unremoved — unchanged from the manifest, no new unrecorded
Elements.

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
- **CORRECTION 2026-08-10: Mundi Mundi was extended, and control week 1 is now
  contaminated too.** The founder extended the order cut-off; the ad set
  `MundiMundi_Interests_AU` now ends **2026-08-13 21:59 (+0800)**, i.e. it runs
  through Thursday 13 August — four days into control week 1 (10–16 Aug), and on
  its heaviest spend days yet ($179 on 9 Aug alone). The earlier note that "the
  account is clean from 2026-08-11 onwards" is **wrong and withdrawn.**
  Pair 1 is now compromised on *both* sides: a deadline-urgency campaign inflated
  the burst week AND inflates the control week. **Pair 1 must be dropped entirely
  from the weekly-aggregate decision rule** rather than merely discounted. The
  decision now rests on pairs 2 and 3 (w/c 17-08 vs 24-08, w/c 31-08 vs 07-09),
  which is why the 4th pair proposed on 2026-08-05 matters more, not less.
  Lesson: a confounder's end date is a founder decision, not a fixed fact —
  re-check campaign end times at every kickoff instead of trusting the logged date.
- Measurement confirmed working
  end to end: Windsor (Meta spend/CPM/reach + Instagram) restored 2026-08-04 on
  the aaron@mxtology.com.au trial; Shopify covers code redemptions and UTM
  orders. Note: Windsor trial expires ~2026-09-03, around week 4 — renew or move
  to Basic before then or the back half of the data is lost.
  Context: Canberra Uni gig (Reece Mastin) falls Fri 7 Aug, the day after.
