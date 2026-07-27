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
- **Gmail MCP** — search threads, read messages, labels, create/update drafts.
- **Outlook MCP** — email search, calendar, Teams chat, SharePoint.
- CEO duties: daily scan of all inboxes; flag emails needing a reply; prepare
  draft replies (drafts only — founder sends).

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
- **Canva is disconnected** — its tools are unavailable until the founder
  re-authorises it in claude.ai connector settings. Useful for branded IG/ad
  design once reconnected.
- No Slack/WhatsApp connector — reports arrive via session notifications
  (push/email) and Gmail drafts.
