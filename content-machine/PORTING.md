# Porting the content machine to Floral Image

Source repository: **`artrajeus/mxtology-content`** (private, same GitHub
account). Copy from there rather than from anything reproduced here — a second
copy of `publish.js` in a second repo is a fork that rots. This document is the
manifest and the diff.

Target: **`artrajeus/floral-image-content`**, private.

---

## 1. The manifest

### Copy verbatim — no business logic inside

| From `mxtology-content` | Notes |
|---|---|
| `publisher/publish.js` | Graph API client. Images, carousels, Reels, Stories, first comments. Change the four constants at the top (IG user id, FB Page id, timezone, queue path). |
| `publisher/facebook.js` | Page crosspost, including the page-token resolution that took a live failure to find. |
| `publisher/mock.js` | Fake Graph API. Issues separate user and Page tokens — keep that. |
| `publisher/test.js` | 29 assertions, 7 scenarios. Runs against the mock. |
| `publisher/whoami.js` | Token identity check. Run it first, always. |
| `publisher/renew-token.sh` | 60-day renewal. Pure bash, no `jq`, validates input before calling Meta. |
| `publisher/SETUP.md` | Six scopes and the traps. Read it before touching the Meta app. |
| `.github/workflows/publish.yml` | Hourly cron, push trigger, `workflow_dispatch` with dry-run. |
| `instagram/imagecheck.js` | "No photograph runs twice." Path constant only. |
| `instagram/schedule.js` | Regenerates `SCHEDULE.md`. Path constant only. |
| `instagram/ideas/README.md` | The inbox contract. Change the brand name; nothing else. |
| `instagram/ideas/_TEMPLATE.md` | Idea front matter. |

The render pipeline is worth copying too, though it lives in a scratchpad rather
than the repo and should be committed properly this time: a Chromium screenshot
of an HTML page with `@font-face` files vendored in, producing exact 1080×1350
and 1080×1920 tiles. There is no font-rendering library involved, no `drawtext`,
no ImageMagick. It is a browser, and it gets kerning and web fonts right because
it is a browser.

### Rewrite from the template — brand-specific

| File | Template here | What changes |
|---|---|---|
| `<channel>/BRAND_KIT.md` | `templates/BRAND_KIT.md` | Everything. Palette, type, voice, and the banned list. |
| `<channel>/STRATEGY.md` | `templates/STRATEGY.md` | Pillars, cadence, KPIs. **Keep §5 (the stripe) and §6 (no photo twice) nearly verbatim** — they are structural, not brand-specific. |
| `<channel>/PUBLISHING.md` | copy MXTology's, then cut | Keep "the approval rule", "what can auto-post", "what the publisher cannot do". Drop the incident write-ups — Floral Image will have its own. |
| `.claude/skills/floral-image-content-machine/SKILL.md` | `skills/floral-image-content-machine/SKILL.md` | Already adapted. Read it; the four `TODO(fi)` markers are the decisions only you can make. |

### Do not copy

`instagram/queue/*`, `instagram/ideas/*.md` (the actual ideas),
`instagram/SCHEDULE.md` (generated), `publisher/backfill-*`,
`publisher/token-state.json`, `storefront/*`, and the
`mxtology-pouch-render` skill. All MXTology content or MXTology-specific.

---

## 2. Decision one: what is the source of truth?

**This is the only part of the system with no obvious Floral Image equivalent,
and the fact gate does not work without it.**

MXTology has Shopify. Every claim in every caption — ABV, volume, price, the
distillery, what is actually in the bottle — is fetched live from the product
listing before a word of copy is written, and the package records which call it
came from. That is what makes the output trustworthy rather than merely fluent.

Floral Image sells a service, and services do not have a product API. So
something has to play that role, and it has to be:

- **readable by Claude in-session** (a URL, a repo file, a connected tool — not a
  PDF on someone's desktop),
- **the thing that is actually correct** when it and a caption disagree,
- **maintained by a human**, because a source of truth nobody updates is worse
  than none.

Realistic options, best first:

1. **A `facts/` directory in the content repo.** Markdown, one file per claimable
   area: service and what is included, coverage area, pricing and what it does
   and does not cover, the guarantee, the hiring terms, client names you are
   permitted to use. Version controlled, so a changed claim has a commit and an
   author. Slowest to set up, and by a distance the most robust.
2. **The live site**, fetched each run. Already true by definition, needs no
   maintenance — but only covers what is on the site, and the site is marketing
   copy rather than a spec.
3. **A connected CRM or scheduling system**, if one exists, for anything about
   routes, clients or capacity.

Whichever you choose, write it into the skill's fact-gate section by name, and
keep the rule that a claim with no source is either cut or flagged ⚠. Never
filled in with something plausible.

**One caution specific to this business.** The hiring page in this repo makes
claims — pay band, hours, van and phone included, "semi-retirement" framing.
Recruitment claims in Canada are enforceable and BC has employment-standards
rules about what can be advertised. Those belong in `facts/` with a note of who
signed them off, and they should not be paraphrased into a caption by anything
that has not read the file.

---

## 3. Decision two: where do rendered images live?

The Graph API will not accept a local file. It fetches a URL, and that URL must
be **publicly reachable, stable, and serve a real `image/jpeg` content type**.
The third one is not pedantry — a post failed once because the URL returned an
HTML error page and the only diagnostic was "Only photo or video can be accepted
as media type".

MXTology uses Shopify Files, via a three-step staged upload
(`stagedUploadsCreate` → multipart POST to Google Cloud Storage → `fileCreate` →
poll until `fileStatus: READY`). Floral Image has no Shopify, so pick one:

- **GitHub Pages** off the content repo. Free, already in the stack, serves
  correct content types, and the URL is stable and public. Note that it makes
  every rendered tile public at a guessable path — fine for marketing art,
  think twice before anything else goes in there.
- **Cloudflare R2 or S3** with a public bucket. Cleanest separation, costs
  approximately nothing at this volume, one more credential to hold.
- **The existing web host** for floralimage.com, if it can take an upload from
  CI.

Whichever it is, keep the verification step that MXTology has: after upload,
`curl` the URL and assert both `200` and `image/jpeg` before it goes in
`publish.json`. That check is four lines and it catches the failure that is
otherwise invisible until the post silently does not go out.

---

## 4. What changes in the rules, and what does not

### Unchanged, copy the reasoning wholesale

- Claude never approves. Only the founder, recorded with name and date.
- Every number traces to a call made in the same session.
- No source photograph runs in two posts, and the check is on the source.
- Verify the rendered asset, not the intention: open the images, check the
  fonts, write alt text last from the finished file.
- The stripe rule and posting in threes.
- Copy burned into the tile, not left in the caption.
- A mock must not share the code's assumptions.

### Changed

**Alcohol compliance comes out entirely.** No 18+, no responsible-drinking line,
no "nobody who could look under 25", no rapid-consumption rule. That is a
meaningful amount of the MXTology gate and none of it applies.

**Something replaces it, and it is not nothing.** For Floral Image the
equivalent risks are:

- **Client premises and client brands.** A photograph of a display in a lobby
  shows someone else's business. Permission to photograph is not permission to
  advertise with it. The brand kit needs a list of clients who have agreed, and
  the default for everyone else is no.
- **People in frame.** Staff and clients are real people in a small city.
  Written consent, and a standing rule that anyone can withdraw it later.
- **Recruitment claims**, per §2 above.
- **Live plants and "fresh" language.** Floral Image's model is maintained
  artificial and preserved displays refreshed on a route. Any wording implying
  fresh-cut flowers where the product is not fresh-cut is the same class of
  error as MXTology's banned phrases, and should go on the banned list by name
  with the reason attached.

**"AI never draws the pouch" becomes "AI never draws a display we install."**
Same reasoning, arguably stronger: a generated arrangement looks plausible and
generic, and a client who recognises their own lobby behind a display they never
had is a phone call you do not want. Real photographs of real installs, or
imagery with no display in it at all.

**The rhythm changes.** MXTology posts daily into a consumer feed. A B2B
service in one city does not have daily news and should not pretend to. Three a
week is a defensible cadence; the machine's value there is less about volume and
more about never shipping an unverified claim and never repeating a photograph —
which matters *more* when the photo library is finite, not less.

---

## 5. Standing it up — the runbook

```bash
# 1. New private repo, and the parts that carry no business logic
gh repo create artrajeus/floral-image-content --private
# copy from mxtology-content: publisher/, .github/workflows/publish.yml,
# instagram/{imagecheck.js,schedule.js,ideas/README.md,ideas/_TEMPLATE.md}
# rename instagram/ -> social/ if you prefer; update the path constants

# 2. The documents, from templates/ in this directory
#    social/BRAND_KIT.md, social/STRATEGY.md, social/PUBLISHING.md
#    facts/ — the source of truth, per §2

# 3. The skill
mkdir -p .claude/skills/floral-image-content-machine
# copy SKILL.md from this directory; resolve the four TODO(fi) markers

# 4. Meta app, following publisher/SETUP.md. Six scopes. Tick the Page.
bash publisher/renew-token.sh
node publisher/whoami.js          # must name the right IG account

# 5. Secrets: IG_TOKEN (and whatever the image host needs)

# 6. Dry run against ONE hand-written approved package
node publisher/publish.js --dry-run
gh workflow run publish.yml -f dry_run=true

# 7. One real post, watched. Then let cron have it.
```

The skill goes in last on purpose. A generator pointed at a publisher nobody has
tested is a way to find out about the publisher in public.

---

## 6. What to tell the Floral Image Claude on day one

Paste this, once the repo exists:

> This repo runs our Instagram and Facebook. Read `content-machine/README.md`
> for how the system works and why each rule exists, then
> `.claude/skills/floral-image-content-machine/SKILL.md`, which is the operator
> and governs every content run. Before writing any copy, read `social/BRAND_KIT.md`
> and `facts/`. You never set `status: approved` on anything — only I do that.
> Every claim in a caption traces to a file in `facts/` or a tool call you made
> in the same session; anything else is cut or flagged ⚠ for me. Start by
> reading those files and telling me what is missing before you produce
> anything.

The last sentence matters more than it looks. The first useful thing a fresh
instance can do is audit the setup, because on day one the brand kit is a
template, `facts/` is half empty, and it is better to hear that than to receive a
confident batch built on gaps.
