# Weekly Review — Friday 16 October 2026

## Two of my own findings were wrong, and the week's best work wasn't mine

### 1. The Instagram token did not expire. Retracted.

I put "the token expires Monday 12 October" in the top three actions four days
running, and opened Monday's kickoff with it. **A publish run succeeded today,
16 October, with the fingerprint still `24f6cc2c242a` from 7 September.** The
token was valid the whole time. I took the expiry date from a note in the 5
October kickoff and never re-derived it, then escalated it daily. The queue
being empty was the real problem; the token was never the blocker.

What is true: posting was dark from **1 October to 16 October**, fifteen days,
and the queue has now been rebuilt to **69 packages**. `2026-10-08-far-north` was
**shelved**, not approved — its Mareeba window closed.

### 2. The pouch spec is resolved, empirically, and my reconciliation was wrong.

Another session (`session_01RgUAQf5BNq19PdcizLKWZZ`) settled in one test what I
held for a founder ruling for a fortnight. Four ingredient still lifes (Shiso,
Tommy's, Berry Bliss, Amaretto) **passed at feed size and failed at 1:1** against
the official packshots, in the same four ways each:

- flavour panel drawn as a floating inset card instead of **running to the pouch edge**
- artwork drawn complete instead of **cropped off the edge**
- the M monogram drawn rounded instead of **the chevron**
- the flavour name on one line instead of **stacked, third word at half size**

Cause recorded: only `mxt-cosmo-REAL-2609` and `mxt-pornstar-REAL-2609` are built
from packshots; every other flavour fell back to `-CORRECTED-2608` prose, which
says the pouch is *"squat and wide, almost square"* when **it is portrait, 3:4**,
and says Tommy's liquid is lime-green when **it is pale straw-gold**.

**On 9 October I wrote that the proportions conflict "dissolved" — that SCALE-2609
measured the body and REAL-2609 measured overall, so both were right. That was
wrong.** The squat description is simply incorrect and it caused four render
failures. I reconciled two numbers on a calculator instead of testing them
against the artwork, which is the same mistake as the August "newest = current"
failure in a different costume.

Neither prose lineage was fully right. The chevron monogram, the stacked flavour
name and the straw-gold liquid appear in **no element I read**. The packshot is
the authority.

**New rule, now in the content repo's `POUCH-REFERENCE.md`:** no flavour is
rendered without a `-REAL-` element built from its own packshot, and the 1:1
check is against the packshot and nothing else. Four new elements built
(`mxt-{shiso,berry,tommys,amaretto}-REAL-2610`). **Seven flavours still have no
`-REAL-` element, and Espresso Martini and Piña Colada have no packshot anywhere
— those two need a photo from Aaron before anything is rendered of them.**

Also recorded there: **props are ingredient claims.** The first Amaretto shot had
almonds in frame; Disaronno is apricot kernel oil, so the almonds were a false
claim no caption check would catch.

## Scorecard vs Monday's plan

| Good week | Result | Why |
|---|---|---|
| Meta audit + 1 creative | **Partial** | Windsor restored 13 Oct and the four-day read was delivered. No creative drafted |
| 1 Klaviyo campaign | **Missed** | Hops & Hooves Draft since 27 Sept — **nineteen days, third week running** |
| 3+ Instagram **posted** | **Partial** | One publish run, today, after fifteen days dark. Queue rebuilt to 69 |
| 2+ event outreach | **Done** | Redcape head office drafted. Robbie Ringland's reply **still unsent, seven days** |
| Founder-flagged mail answered | **Done — mostly by Aaron** | Josh, Brady, Steve, Stephen, Vipul, Wilhelm all handled by hand |
| Daily briefs | **Done** | 7/7 |

## Revenue — Mon–Fri, like for like

| | 12–16 Oct | 5–9 Oct |
|---|---|---|
| Paid orders | **14** | 7 |
| Revenue | **$3,197.09** | $1,616.94 |
| AOV | $228.36 | $230.99 |

**+98% revenue on double the orders.** The best week since the Hops & Hooves
invoice, and this time it is the store, not a festival.

**Two trade accounts opened, both off $0 sample packs:**
- **#2138 Josh, Cellarbrations South West Rocks** — $847 incl GST, all 11 flavours
- **#2147 Mason Castle Tavern** — $905, sampled 9 Oct, ordered 14 Oct. Five days.

**Meta — the four-day read is complete and the campaign does not pay.**

| | 13 Oct | 14 Oct | 15 Oct | 16 Oct |
|---|---|---|---|---|
| Spend | $79.12 | $179.64 | $168.78 | $83.49 |
| Purchases | 2 | 2 | **0** | 1 |
| ROAS | 2.84× | 1.44× | **0.00×** | 1.41× |

Week: **$512.38 spend, 5 purchases, $600.91 attributed — 1.17×, CPA $102.48.**
At pouch margin, break-even needs roughly 2.2×. The budget doubled on day two and
halved again today, which also means this was never a clean four-day test. The
shape is the familiar one: **fifth demonstration that this account punishes fast
scaling.** Recommendation unchanged — $20–25/day and hold.

**Klaviyo flows: $204.94** (Win-back $126.97 on 26 recipients, $4.88 each;
Welcome $77.97 on 47). Post-Purchase reached 80 and converted none.
**Welcome Series recipients went 12 → 47** — list growth from the Club launch,
the clearest good news in the email channel for weeks.
**Abandoned Checkout reached 4 people against 14 paid orders. Ninth week.**

## The strategic finding of the week

**The shelf is allocated, not sold.** Two buyers said so independently:

- Nat, Cellarbrations Yarraville: a competitor pouch returned *"via ALM IBA
  allocation. For the time being, these are the only sku's I'll keep."*
- Stephen Young, RLS Group: *"I have not tried either Quips or your product. It is
  simply a matter of space, we range products which we have to from IBA, of which
  **Quips gained ranging in our IBA program**."*

The competitor is **Quips**. Stephen declined without tasting. Brady at
Dunsborough asked *"do you have these in ALM or Liquid Mix"* — three stores in a
week. **Cold store-level outreach is competing against a mandate it cannot
outrank.** The Metcash meeting slipped from Wednesday to today, 14:00 AEST, and
IBA ranging is the whole ask.

**And a price has been named.** Stu Henley, Premix King: *"it all comes down to
the retail pricepoint… i would like to see them sit at 8.99."* Group-wide. $8.99
retail implies roughly $4.90–5.00 wholesale against the current $7. **Still no
Xero connector, so there is no cost-per-pouch to test that against.** That is now
the single most valuable missing number in the business.

## Quality check

- **Fixed in flight:** template `RzebeW` read "$60"; now "$100, every state and
  territory", matching the live profile and Aaron's own reply to Pascal. Still
  Draft, unsent to 53 people.
- **Below standard, mine:** the 9 October proportions reconciliation (above).
- **Below standard, mine:** the token expiry warning (above).
- **Two authority files now exist.** `claude-ceo/POUCH-ELEMENTS.md` says it is
  "the ONLY authority"; the content repo's new `POUCH-REFERENCE.md` holds the
  packshot rule. Flagged, not merged — which file governs is Aaron's call, and
  guessing is how this went wrong the first time.
- **Two product faults open:** Mark's Cosmo tasting of caramel syrup, and Jai's
  seven separated Piña Coladas. Neither has a batch answer. Premix King will taste
  product before they decide.

**Element reconcile:** `bed44330` (Cosmo CURRENT) present and `completed`.
Workspace now holds the four new `-REAL-2610` elements. The blanket "generate no
pouch imagery" block should be replaced by the packshot rule — recommended, not
applied.

**Thursday Burst:** closed 2026-08-27. Eighth week with nothing to score. The
trigger should stop asking.

## Monday's carry-overs

1. **Cost per pouch** — connect Xero. Premix King is waiting on a number only
   that answers.
2. **IBA ranging** — today's outcome decides whether cold store outreach
   continues at all.
3. **Send Hops & Hooves.** Nineteen days, 53 people, now factually correct.
4. **Send Robbie Ringland's reply** — Cup Day is 3 November, eighteen days out.
5. **Packshots for Espresso Martini and Piña Colada** — nothing renders of them
   until Aaron supplies one.
6. **Both product faults to Julia.**
7. Abandoned Checkout, ninth week. 4 of 14.
