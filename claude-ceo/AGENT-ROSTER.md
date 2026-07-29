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

**Mailbox coverage (verified 2026-07-30) — this is NOT "all inboxes":**

| Business mailbox | Covered? | Via |
|---|---|---|
| aussiefloat@gmail.com | ✅ yes | Gmail connector is authenticated as this account |
| Vancouver@floralimage.com | ✅ yes | Microsoft 365 connector (`get_me` confirms) |
| aaron@mxtology.com.au | ⏳ pending forward | neither connector can reach it directly (Microsoft returns ErrorInvalidUser; Gmail is aussiefloat-only). Arrives once forwarding is on, labelled `MXTology/Aaron` |
| mxtologycocktails@gmail.com | ⏳ pending forward | same — arrives labelled `MXTology/Cocktails` |

**Routing (labels already created in aussiefloat@gmail.com):**
- `MXTology` (Label_46) — parent, catches all MXTology mail
- `MXTology/Aaron (aaron@mxtology.com.au)` (Label_47)
- `MXTology/Cocktails (mxtologycocktails@gmail.com)` (Label_48)

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
