# Weekly Review — Friday 2 October 2026

Period: Mon 28 Sept – Thu 1 Oct (Friday excluded; same-day Shopify totals move both
ways, rule adopted 2026-09-12). Compared against Mon 21 – Thu 24 Sept.

## Opens with a quality defect in my own governing documents

**`QUALITY-STANDARDS.md` contradicts the Elements it points at, and a newer
Element says one of the approved UUIDs is wrong.**

`mxt-cosmo-REAL-2609` (`9320c528-e78f-43c1-97b0-00d39a0f8307`, created
2026-09-10) says in its own description:

> "SUPERSEDES mxt-cosmo-CORRECTED-2608, **mxt-cosmo-CURRENT-202608** and
> mxt-pouch-SCALE-2609, **ALL OF WHICH DESCRIBE THE PACKAGING WRONGLY. Ignore
> those elements entirely.**"

`mxt-cosmo-CURRENT-202608` is `bed44330-1fd6-4896-a120-d41feb4f14f0` — a
**✅ approved** UUID in `POUCH-ELEMENTS.md`. The two errors it names:

1. The flavour artwork is **not full-bleed**. It is a separate inset rectangular
   label on the lower-right, with black foil visible around all four edges.
2. The pouch is **not squat**. It is portrait, roughly 3 wide to 4 tall.

Separately, `QUALITY-STANDARDS.md` describes every approved Element as carrying
"glossy black left panel with the iridescent rainbow MXT OLOGY wordmark". The
approved margarita Element `0beecfb3-8141-42d3-8e85-eaf091bb1fcd` says the
opposite in its own text: *"large gradient 'M' monogram … with 'MXTOLOGY' in
white capitals directly beneath, both HORIZONTAL — **NO vertical rainbow
wordmark**."*

**Nothing has been re-pointed and no Element has been quarantined.** Which spec
is correct is a founder call, and `POUCH-ELEMENTS.md` reserves it to the founder.
Both files now carry a BLOCKED note so no generation runs against a contested
spec. **No pouch imagery should be generated until this is ruled on.**

**Why last week's reconcile missed it.** I checked that each approved UUID was
present and `completed`. I did not read the descriptions. A reconcile that only
checks presence cannot catch a newer Element declaring an approved one wrong.
**New rule: the Friday reconcile must diff the Element descriptions, not just the
UUID list.**

## The week's real number is not in Shopify

**Hops & Hooves paid $6,141.60.** Remitted 30 Sept, recipient-created tax invoice
from Xiaoyu Chen at Thoroughbred Park on 1 Oct, explicitly for attending as a
vendor. One day at one festival.

| MXTology revenue recognised, Mon 28 – Thu 1 | |
|---|---|
| Shopify | $1,164.10 |
| **Hops & Hooves (Canberra Racing Club)** | **$6,141.60** |
| **Total** | **$7,305.70** |

The store was 16% of it. Every daily brief this week led with the 16%.

## Revenue readout

| Shopify | This wk M–Th | Last wk M–Th | Δ |
|---|---|---|---|
| Orders (gross) | 11 | 31 | — |
| — $0 (Leoni's replacement) | 1 | 16 | — |
| **Paid orders** | **10** | 16 | **−38%** |
| Revenue | **$1,164.10** | $2,252.81 | **−48%** |
| Paid AOV | $116.41 | $140.80 | −17% |

| Meta (Windsor) | This wk M–Th | Last wk M–Th |
|---|---|---|
| Spend | **$333.78** | $830.95 |
| Purchases | **1** | 9 |
| Attributed value | $132.00 | $1,437.00 |
| ROAS | **0.40×** | 1.73× |
| CPA | $333.78 | $92.33 |
| **Blended MER (Shopify only)** | **3.49×** | 2.71× |
| **Blended MER (incl. festival)** | **21.9×** | — |

Spend fell 60% and attributed ROAS fell with it to 0.40×. Only two campaigns ran:

| Campaign | Spend | Purch. | Value | ROAS |
|---|---|---|---|---|
| `MXT_TablelandsPack_2026_Sales_LP` | $322.99 | 1 | $132.00 | 0.41× |
| `MXTology – ATC Retargeting` | $10.79 | 0 | $0 | 0.00× |

**`ATC Retargeting` stopped spending after 29 September**, having run nine
straight days at zero for $135.56 the week before. I recommended pausing it in
early September, was wrong when it then returned 3.01× and 5.39×, and did not
re-raise it. It has now stopped on its own.

**`TablelandsPack_LP` is the only live campaign and it is not working.** 517
clicks, one $132 order, $322.99. New creative was approved Monday 00:09, so this
*is* the four-day window — but the daily budget moved inside it ($101 → $76 →
$110 → $46), which weakens the read. **Recommendation for approval: hold it flat
at a single figure — $50/day — for four clean days before judging the creative.
Do not let the budget move inside a test window again.**

## Klaviyo — and a recommendation I am withdrawing

| Flow | Recipients | Conv. | Revenue | Rev/recipient |
|---|---|---|---|---|
| Post-Purchase `UUXzun` | 69 | 1 | **$159.00** | $2.30 |
| **Win-back (60 Days) `TSNf8M`** | **39** | **1** | **$142.80** | **$3.66** |
| Welcome Series `SNzMbM` | 34 | 1 | $132.00 | $3.88 |
| Browse Abandonment `TQbYVU` | 5 | 0 | $0 | $0 |
| **Abandoned Checkout `RrNPau`** | **2** | 0 | $0 | $0 |
| Added to Cart `TAVHsW` | 1 | 0 | $0 | $0 |

Total flow revenue **$433.80** on 150 sends, against $332.00 on 429 sends last
week. Up 31% on a third of the volume. Post-Purchase converted for the first
time in the five weeks I have been reporting it.

**I have recommended switching off the win-back flow for three weeks. I am
withdrawing that recommendation.** It earned **$142.80 this week at $3.66 per
recipient** — ahead of Post-Purchase and level with Welcome Series. The defect is
real and documented with three named customers (Kerrie Robertson, Leoni Marshall,
Rowland Percy), and the free-cocktail offer still does not apply at checkout. But
"switch it off" would have cost revenue. **The correct action is to fix the
discount and leave the flow running.** That is a change of position and I should
have reached it sooner by looking at revenue per recipient rather than at the
complaint count.

**`Abandoned Checkout` reached 2 people against 10 paid orders — sixth
consecutive week.** It is the only flow in the account that is genuinely broken
rather than merely imperfect.

No campaign was sent. Nothing was sent, published, launched or budget-changed.

## Scorecard vs Monday's kickoff

| Plan item | Result | Why |
|---|---|---|
| Meta audit daily | **Done** | 5 briefs, 5 audits |
| No new creative (deliberate) | **Overtaken** | New ads were approved in the account on 29 Sept — not by me and not in the plan. Flagged same day |
| Hops & Hooves campaign to the 53 entrants | **Missed** | Campaign `01M3J9DWC1S46CJTAX8BZED8F4` and template `RzebeW` still Draft. The 53 warmest leads in the business, five days cold |
| Instagram — approve or kill `2026-09-27-one-hundred` | **Missed** | Still `draft`; its slot passed unposted |
| Instagram token before 12 Oct | **Open** | Reminder fired Thu 1 Oct 09:00. No evidence either way in the repo; 10 days left |
| Festival outreach | **Partial** | Robbie Ringland draft `r7548850138797574331` still unsent, through a week in which Thoroughbred Park called it a record festival twice and paid $6,141.60. Generic 2027 pitch `r8934145290925456920` unsent |
| Trade terms — the four numbers | **Missed, fourth week** | And now a named group is waiting: Matt, manager of the Bottle-O Bros stores, asked to talk pricing "this week". Draft `r-1960200949237936241` unsent; the window closes today |
| Win-back fix | **Missed** | Three weeks |
| Daily briefs | **Done** | 5/5 |

## Quality check

- **Below standard, flagged not fixed:** the Element/standards contradiction
  above. Recorded in both files as BLOCKED, awaiting a founder ruling.
- **Corrections I made this week, all mine:** the Tender Edge invoice was flagged
  as a possible fraud pattern on 30 Sept and shown to be a genuine order on
  1 Oct (Aaron quoted 500 A5 flyers with them on 24 Sept). The bank-detail change
  still warrants a verification call; leading with fraud was wrong.
- **Instagram and Shopify both settle overnight.** Saturday 26 Sept read 403
  reach on the day and settled to 1,422 with +6 followers. Friday 25 read 347 and
  settled to 669. I quoted both unsettled and corrected both next day. The rule
  holds: do not quote same-day Instagram.
- **Outlook needs `folderName: Inbox`.** A bare dated query returned an empty
  body on 28 Sept and read as a quiet mailbox; with the folder set it returns 46
  items. Fixed from 29 Sept onward.
- **Deliverables produced:** 5 daily briefs, 1 kickoff, 1 review, 1 Klaviyo
  campaign + template (drafted, unsent), 4 Gmail drafts (Bottle-O Bros, Leoni,
  Robbie, generic 2027 pitch), 2 repo corrections (AGENT-ROSTER mailbox table,
  CEO.md Instagram line). **No ad creative, no Instagram asset, no published
  anything** — correct, since everything outward-facing stays a draft.

## Instagram

Mon 28 – Thu 1: **+2 followers, 1,652 reach**, against +21 and 7,337 for the
whole of last week. Reach is paid-driven and Meta spend fell 60%, so this tracks
spend rather than content. The publisher itself is healthy — 44 posts since
10 August, hourly workflow, 635 green runs — and the constraint remains approval,
not production.

## Burst experiment

Closed 2026-08-27. 1 of 3 pairs run, A$82.68 of A$300 spent, no clean pairs. Not
a burst week, not a control week, no burst runs, no codes to redeem, no
retargeting post-burst window, not reopened. Nothing to score.

## Carry-overs for Monday

1. **Rule on the pouch spec.** Which is right — the `-CURRENT-202608` Elements or
   the `-REAL-2609` ones? Until this is answered, no pouch imagery can be
   generated, and `QUALITY-STANDARDS.md` is describing artwork that two of its own
   Elements contradict.
2. **Trade terms — the four numbers.** Fourth week, and the Bottle-O Bros store
   group has been waiting since Sunday. This is now the oldest and most expensive
   open item in the business.
3. **Send the Hops & Hooves campaign** to the 53 entrants, or archive it. Five
   days cold already.
4. **Send the Robbie Ringland reply.** Record festival, two thank-yous,
   $6,141.60 banked. The window for "what else is on this season" is now.
5. **Fix the win-back discount — do not switch the flow off.** Position changed;
   see above.
6. **Abandoned Checkout trigger.** Sixth flag. 2 recipients, 10 orders.
7. **Hold `TablelandsPack_LP` flat at $50/day for four clean days.**
8. **Instagram token** — 10 days left, and approve or kill `one-hundred`.
9. **Mark at Cellarbrations Kingston — eleven days.** A competitor pouch is
   already ranged there and "getting traction".
10. **Student Experience Network**: their Commercial Newsletter goes to members
    Wed 14 Oct and takes promotions; Paul wants SENCON auction/raffle donations.
    Two cheap B2B channels, both time-boxed.
11. **Lodge the Australia Post claim** on Veronica's lost first parcel.
12. GSC / Bing verification — fourth week. Easter Show — fourth week.
13. **Monday 5 October is the first Monday**: monthly AEO audit and Xero review
    are due at kickoff.
