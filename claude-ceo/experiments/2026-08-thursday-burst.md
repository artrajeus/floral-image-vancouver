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
- **Unique discount code per burst** (e.g. BURST1-style, created in Shopify at
  launch, only revealed in this burst's ad + landing page). Redemptions =
  hard attribution.
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
