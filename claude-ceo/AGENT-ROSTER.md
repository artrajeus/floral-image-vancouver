# MXTology Agent Roster

Inventory of every agent/capability connected to this Claude account (audited
2026-07-27). "Agents" here are the connected MCP servers, plugins, and skills the
CEO orchestrates.

## Revenue drivers

### 1. Meta Ads agent
- **Windsor.ai MCP** — read performance data for Meta Ads, Google Ads, TikTok,
  LinkedIn + **write actions**: create/pause/enable Meta campaigns, ad sets, ads;
  set budgets; boost organic posts.
- **Supermetrics MCP** — 150+ source reporting (Meta Ads, GA4, etc.) for audits.
- **Motion Creative Analytics MCP** — Meta-only creative performance insights
  (spend/scaling/hook analysis, demographic breakdowns, competitor ad libraries).
  Call `get_auth_context` first, then `get_creative_insights` with
  `insightType=SPEND` before any other insight type.
- **adspirer-ads-agent plugin** (enabled) — ads workflows.
- CEO duties: weekly performance audit (ROAS, CPA, spend, creative fatigue),
  draft new ad copy/creative briefs, recommend budget moves. Budget changes and
  campaign launches require founder approval.

### 2. Email / Klaviyo agent
- **Klaviyo MCP** — full campaign lifecycle: create campaigns and email templates,
  segments/lists, flow reports, campaign reports, send (send requires approval).
- CEO duties: draft ≥1 newsletter/campaign weekly, review flow + campaign
  performance, list growth.

### 3. Instagram / content agent
- **Higgsfield MCP** — image/video/audio generation, shorts studio, virality
  predictor, TikTok publishing.
- **Windsor.ai** — can create Instagram image posts (approval required to publish).
- CEO duties: ≥3 content pieces/week aligned to engagement, follower growth, sales.

## Supporting agents

### Store agent
- **Shopify MCP** — products, collections, orders, customers, inventory,
  ShopifyQL analytics, discounts.
- **Skills**: `eca-aeo-audit` (SEO/AI-visibility audit, run monthly),
  `ecommerce-blog-writer` (SEO/AEO blog posts).

### Inbox agent

**Scope: business mailboxes only.** Personal mail is deliberately excluded
(founder decision 2026-07-30) — do not triage or report on
artrajeus@gmail.com or artraje@hotmail.com.

**Mailbox coverage — CORRECTED 2026-08-17. The 2026-07-30 table was wrong on
the most basic fact and is superseded.**

The connected Gmail account is **artrajeus@gmail.com**, not aussiefloat@gmail.com.
Evidence: every `SENT`-labelled message returned by the connector has
`sender: artrajeus@gmail.com`, and `in:inbox` returns mail addressed to
artrajeus@gmail.com. This matters because the standing rule excludes
artrajeus@gmail.com as personal — so a bare `in:inbox` triage was excluding the
entire connected mailbox and reporting the result as a quiet day.

| Business mailbox | Covered? | Via |
|---|---|---|
| artrajeus@gmail.com | ✅ connected, but **out of triage scope by founder rule** | Gmail connector is authenticated as this account |
| Vancouver@floralimage.com | ✅ yes | Microsoft 365 connector (`get_me` confirms) |
| aussiefloat@gmail.com | ❓ unverified | search `to:aussiefloat@gmail.com`; returned nothing in the last 2 days, so coverage is unproven, not confirmed |
| aaron@mxtology.com.au | ⏳ pending forward | not reachable directly (Microsoft returns ErrorInvalidUser) |
| mxtologycocktails@gmail.com | ⏳ pending forward | same |

**This needs a founder decision.** The mailbox the founder actually works out of
is artrajeus@gmail.com, and it is the one he wants taken to inbox zero — but the
2026-07-30 rule puts it out of scope. Either the rule narrows to *personal
threads within* that mailbox, or the inbox agent has almost nothing to triage.

**Label routing — corrected:**
- `MXTology` = `Label_5869056844117415831` (201 threads). Search it as
  `label:MXTology`.
- `Label_46` / `Label_47` / `Label_48` in the old table are **not** MXTology
  labels — they are `Business/Postcards For Change/{Templates,Website,logins}`.
- No `MXTology/Aaron` or `MXTology/Cocktails` sub-labels exist yet.
- **`label:<ID>` search syntax silently returns empty in this connector.**
  Always search by display name.

Founder setup required once, per forwarded account: turn on auto-forward to
aussiefloat@gmail.com; add a filter applying the matching label (**do not tick
"Skip the Inbox"**); and add the address under aussiefloat's Settings → Accounts
→ "Send mail as" so draft replies leave from the correct address.

- Tools: Gmail — search threads, read messages, labels, create/update drafts.
  Microsoft 365 — email search and read only (**cannot create drafts**; supply
  suggested reply text in the report instead).
- CEO duties: daily scan of the **covered** mailboxes; flag emails needing a
  reply; prepare Gmail draft replies (drafts only — founder sends). Every daily
  brief must state which mailboxes were scanned, and must not imply coverage of
  the uncovered ones.
- Note: the connected Gmail account belongs to **Aussie Floats**, not MXTology —
  its labels and threads are CRIB/freight/AIMS work. MXTology festival, wholesale
  and supplier enquiries land in the uncovered mxtologycocktails@gmail.com.

### Calendar agent
- **Google Calendar MCP** — list/search/create events, suggest times.

### Finance agent
- **Xero MCP** — cash position, P&L, financial position, top customers by revenue,
  receivables.

### Events/outreach agent
- Web search + Gmail drafts. Research festivals/events, find booking agents and
  organiser contacts, draft outreach emails.

## Other connected (not core to weekly rhythm)
- **Google Drive MCP** — file search/read.
- **Kiwi flight search, hotel/attraction search MCPs** — travel logistics for
  festivals/events when booked.
- **GitHub MCP** — this repo.

## Gaps / action needed
- **aaron@mxtology.com.au and mxtologycocktails@gmail.com await forwarding** —
  the highest-priority gap, since MXTology revenue is goal #1 and festival,
  wholesale and supplier enquiries land there. Labels and triage spec are ready;
  only the founder-side forwarding/send-as setup remains. Until then, every daily
  brief must say these two are not yet flowing.
- **Canva is disconnected** — its tools are unavailable until the founder
  re-authorises it in claude.ai connector settings. Useful for branded IG/ad
  design once reconnected.
- **Motion Creative Analytics trial expired** — Windsor covers current ad
  reporting; only reactivate for competitor ad-library analysis.
- No Slack/WhatsApp connector — reports arrive via session notifications
  (push/email) and Gmail drafts.
