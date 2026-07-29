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
2. **Inbox triage** — see the mailbox coverage table in `AGENT-ROSTER.md`. Scan
   the covered mailboxes only (currently aussiefloat@gmail.com and
   Vancouver@floralimage.com) and **name which ones were scanned** in the report.
   Never write "all inboxes".
   - List emails from the last 24h that need the founder's reply, most important
     first, one line each on why.
   - Create Gmail **draft** replies for the routine ones; flag the judgment calls.
     The Microsoft connector cannot create drafts — for Outlook items, put the
     suggested reply text in the report.
   - If mail forwarded from another account is labelled (e.g. `MXTology`), triage
     it as its own section so the businesses stay separate.
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
