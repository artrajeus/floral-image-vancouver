# CEO Operating Rhythm

All times Adelaide / Australian Central (ACST, UTC+9:30). Cron schedules are
stored in UTC and don't auto-shift for daylight saving — when ACDT starts in
October, reports land an hour later on the clock until the crons are nudged.

## Daily — CEO Daily Brief (7:00am ACST, every day)

1. **Numbers** (vs yesterday and 7-day average):
   - Shopify: sales, orders, AOV (ShopifyQL).
   - Meta Ads: spend, ROAS, CPA (Windsor/Supermetrics).
   - Klaviyo: recent campaign opens/clicks/revenue.
   - Instagram: follower count, engagement on latest posts (Windsor/Supermetrics).
2. **Inbox triage — business mailboxes only.** Personal mail
   (artrajeus@gmail.com, artraje@hotmail.com) is out of scope; never triage or
   report it. See the coverage table in `AGENT-ROSTER.md`, **name the mailboxes
   actually scanned**, and never write "all inboxes".

   **Search syntax — corrected 2026-08-17. Read this before running the triage.**
   `label:<ID>` **does not work** in this Gmail connector: it returns an empty
   result silently instead of erroring, so it reads as "quiet day" when it is
   actually a broken query. Verified against `Label_774` ("1: To respond", 351
   threads, mail from that same day) — returned nothing. **Always search by
   display name: `label:MXTology`.** Confirm any label name against
   `list_labels` before relying on it.

   The old spec's `Label_46` was wrong as well — in this account that ID is
   `Business/Postcards For Change/Templates`, unrelated to MXTology. The
   MXTology label is `Label_5869056844117415831`, display name `MXTology`.
   Every "MXTology returned nothing" reported before 2026-08-17 was a false
   negative on both counts and must not be cited as evidence about forwarding.

   Run these searches:
   - `label:MXTology newer_than:1d` — MXTology mail. **Report MXTology first**
     — it is revenue priority #1. If this returns nothing, re-run without the
     date filter to confirm the label resolves at all before calling it a quiet
     day, and say which check you ran.
   - `to:aussiefloat@gmail.com newer_than:1d` — Aussie Floats. Do **not** use
     `in:inbox` for this: the connected Gmail account is artrajeus@gmail.com
     (see AGENT-ROSTER.md), so a bare inbox search returns the founder's
     personal mail, which is out of scope.
   - Outlook search, last 24h — Floral Image (Vancouver@floralimage.com).

   Then: list emails needing the founder's reply, most important first, one line
   each on why. Create Gmail **draft** replies for routine ones, flagging judgment
   calls. For a forwarded MXTology thread, note in the report which address the
   reply should be sent *from* (the "Send mail as" address), since the draft
   defaults to aussiefloat. The Microsoft connector cannot create drafts — for
   Outlook items, put the suggested reply text in the report body.
3. **Task status** — what each agent workstream has in flight, on-track / at-risk /
   blocked, with the blocker named.
4. **Today's top 3** — the three highest-revenue-impact actions for today.
5. Keep the brief under ~400 words. Lead with anything needing a decision.

## Monday — Weekly Kickoff (6:00am ACST)

1. Pull last week's scorecard numbers (same sources as daily).
2. Set this week's plan against the "definition of a good week" in CEO.md:
   - Meta ads: which campaigns to audit, what creative to draft.
   - Klaviyo: this week's newsletter/campaign topic (tie to products, season,
     events).
   - Instagram: 3+ content pieces — themes and formats.
   - Festivals/events: which events to research, who to contact.
3. **Start the work** — don't just plan. Draft what can be drafted immediately.
4. Check the calendar for deadlines/events this week and fold them into the plan.
5. Deliver the plan as the Monday report.

## Friday — Weekly Review (3:00pm ACST)

1. Score the week against Monday's plan and the definition of a good week —
   done / partial / missed for each item, with reasons.
2. **Quality check** every deliverable produced this week against
   QUALITY-STANDARDS.md. List anything below standard and fix or flag it.
2a. **Reconcile pouch Elements.** Call `show_reference_elements` (action=`list`)
   and diff the live workspace against `POUCH-ELEMENTS.md`: report any approved
   UUID that has disappeared, any live Element not recorded in the file, and any
   flavour still quarantined. Assets are only "current" if the manifest says so —
   never judge by Element name or `created_at`.
3. Revenue readout: week vs prior week (Shopify + Klaviyo attributed + ads).
4. Carry-overs and recommendations for next week's kickoff.

## Monthly (first Monday, as part of kickoff)

- Run the `eca-aeo-audit` skill on the store.
- Xero review: P&L, cash position, top customers.

## Escalation rules

- Anything requiring spend, sending, or publishing → prepare fully, then surface
  for approval in the report. Never auto-send.
- If a data source fails or a connector is unauthenticated → say so in the report
  with the exact reconnect step. Never fill gaps with estimates.
- If the same task slips two weeks running → open the Friday review with it.
