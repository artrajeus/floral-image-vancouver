# Bootstrap prompt

A self-contained prompt for building this engine from scratch in a fresh Claude
account, with no access to `artrajeus/mxtology-content`.

**How to use it.** Fill in the bracketed block at the top, paste the whole thing
as your first message in a new Claude Code session with an empty private repo
attached, and answer the questions it asks before letting it build. It is
deliberately long — the length is the rules, and the rules are the part that
makes the output trustworthy rather than merely fluent.

**Expect it to take several sessions.** It is staged, with checkpoints. A single
run that claims to have built all of it has skipped the testing.

---

<!-- ─────────────── PASTE EVERYTHING BELOW THIS LINE ─────────────── -->

You are going to build me an automated social content system, in this
repository, over several sessions. Read this whole brief before doing anything.

## The business

- **Name:** [BUSINESS NAME]
- **What it sells:** [ONE SENTENCE — be specific enough that this could not
  describe a competitor]
- **Where:** [CITY / REGION], timezone [IANA ZONE, e.g. America/Vancouver]
- **Channels:** Instagram [@HANDLE] and the Facebook Page [PAGE NAME]
- **Website:** [URL]
- **Who approves publishing:** [YOUR NAME] — nobody and nothing else, ever

## What we are building

A repository that runs the feed. Three parts:

1. **A publisher** that talks to the Meta Graph API from GitHub Actions on an
   hourly cron. It posts images, carousels, Reels and Stories, posts the first
   comment, crossposts to the Facebook Page, and commits the resulting media IDs
   back so the repo is the record of what actually went out.
2. **A queue** of content packages, two files each, version controlled.
3. **A skill** — `.claude/skills/<name>/SKILL.md` — that is the operator. It
   reads a brand kit, a strategy doc, an ideas inbox and a source of truth, then
   produces packages into the queue. It never publishes and never approves.

The repository is the record. The skill is the operator. The publisher is the
only thing allowed to touch the platform.

## Before you build anything, interview me

Do not start writing code, and do not invent any of the following. Ask me, in
one message, as a numbered list. If I answer vaguely, push back once.

1. **What is the source of truth for factual claims?** Every number and spec in
   a caption has to trace to something checkable. If the business has a product
   API (Shopify, a PIM, a booking system), that is it. If it sells a service and
   has no such API, the answer is almost certainly a `facts/` directory in this
   repo — markdown, one file per claimable area, so a claim has a commit and an
   author. Tell me which, and if it is `facts/`, propose the file list.
2. **Where will rendered images be hosted?** The Graph API fetches a URL; it
   will not take a local file. It must be publicly reachable, stable, and serve
   a real `image/jpeg` content type. Propose an option and tell me the tradeoff.
3. **Brand kit inputs** — palette hex values, display and body typefaces, the
   two or three named visual treatments every asset must land in, and the voice.
   Ask for what you need rather than inventing it. If I do not have it, say so
   in the brand kit as a gap rather than filling it.
4. **The consent and compliance surface.** What in this business's advertising
   is legally or ethically constrained? Age-restricted product rules, client
   premises and brands appearing in photographs, consent for identifiable
   people, employment claims in job ads, professional-body advertising rules,
   health or environmental claims. Ask me directly. **Do not assume there are
   none** — every business has some, and the ones nobody wrote down are the
   expensive ones.
5. **Cadence.** How often can this business genuinely say something true? A
   single-location service business does not have daily news and should not
   pretend to. Three a week that are all true beats seven where two are padding.

Then write me a short plan and wait for my go-ahead.

## The rules the system is built around

These are not preferences. Each one is a defect that shipped once on the system
this is modelled on, and the reason matters more than the rule — a rule without
its reason gets argued away in six months.

**1. You never approve anything.** Every package carries
`status: draft | approved | posted` and `approved_by`. The publisher refuses to
post anything not `approved`. You are forbidden from setting that field under
any circumstances, including when I say "looks good" in passing — approval is
recorded in the file, by name, with a date. A system that can generate *and*
publish is a system that can publish something wrong at 8am with nobody awake.

**2. Every number traces to a call made in the same session.** Price, stock,
spec, rating, count, capacity. Not from earlier in the conversation, not from
memory, not from a summary endpoint. A caption once claimed "59 left" against a
live inventory of 19 — nobody lied, the figure was just stale by the time it
shipped. Where an API offers several plausible fields, name the exact one in the
skill and say why the others are wrong.

**3. Never infer a fact from what you already know about the category.** A
cocktail brand's Espresso Martini was written as vodka, because that is what an
Espresso Martini is. Theirs is spiced rum. It shipped, and the founder caught
it. The departures from the obvious version are usually the brand's best
content, and they are exactly what you will get wrong. Fetch the full record —
search and summary endpoints truncate, and the truncation hides the field you
are about to guess at. Build a claim table in every package:

```
| Claim | Verified against |
```

If the source of truth does not state something, cut it or mark it ⚠ for me.
Never fill the gap with something plausible.

**4. AI never draws the thing the business sells.** A redrawn label, a generated
version of a product or an installation — plausible, generic, and wrong. Two
sanctioned paths: composite a real photograph, or produce assets with none of
the product in them. Where a model *does* render the product from a reference,
**check every image at 1:1 against that reference** — zoomed to native pixels,
not on a contact sheet. On the source system that check caught an upside-down
wordmark, two misspelled wordmarks, a mirrored product name, an entirely
invented package design, and wrong product colours four separate times. None
were visible at feed size, which is what makes them dangerous: they surface
later, on a product page or in a screenshot.

Related, and worth writing into the skill: **under roughly 150px on a 2k render,
a model stops reproducing branding and starts designing it.** The fix is
compositional — closer camera, one branded object in frame, an explicit list of
what must not be invented — never a re-roll at the same composition.

**5. AI people are never presented as real people.** Styled advertising imagery
with people in it is fine. An AI person captioned as a customer, a testimonial
or a member of staff is not. The line is the claim, not the pixels.

**6. No source photograph runs in two posts — and the obvious check finds
nothing.** Every tile is a composite: type, scrims and crop baked in. Two posts
built on the same photograph produce two different files with two different
names. On the source system, comparing output files found 101 distinct files and
zero repeats while the same photograph sat in two live posts. So the check runs
on the **source**: every package records `source_images`, and three states stay
distinguishable —

- `["scene-x.jpg"]` — one photograph
- `[]` — a type tile, genuinely no source
- field absent — **unrecorded**, reported as a gap, not passed

Conflating the last two is how a duplicate check quietly passes on a queue it
cannot see. Write a script that enforces this and run it before anything queues.

**7. Verify the asset, not the intention.** After rendering, open the images.
Confirm the display face is the one specified — a broken font file falls back to
a system face silently, without erroring, and shipped a batch that way. Write
alt text **last, from the finished image**; alt text once described a headline
that had since been rewritten. Before a URL goes in a package, `curl` it and
assert both `200` and `image/jpeg` — a post failed once because the URL returned
an HTML error page, and the only diagnostic the platform gave was "Only photo or
video can be accepted as media type".

**8. A mock must not share the code's assumptions.** Seventeen green assertions
certified a publisher that could not post to Facebook at all, because the real
Graph API issues a *separate* token for a Page and rejects the user token on
Page endpoints — and the mock had been written from the same misunderstanding as
the code. Build the mock to model the platform's actual behaviour, including the
parts the code currently gets wrong.

## Platform facts that will otherwise cost you a day each

- **A Page token is not a user token.** Publishing as a Page needs the Page's own
  token from `/me/accounts`. This is the single most common first-run failure.
- **Facebook grants a scope and a Page in two separate clicks**, and silently
  skips the second. A token can hold every scope and still see zero Pages. The
  selection dialog only reappears when you request a scope it has not seen
  before — so adding any new scope forces it back. That is the fix.
- **Tokens expire every 60 days**, and `debug_token` withholds `expires_at` when
  a token inspects itself. Count remaining days from a first-seen date the repo
  records, keyed on a hash of the token, or the expiry warning can never fire.
- **`backdated_time` does not work.** Backfilled posts land stamped with their
  creation time. If we backfill, the dates will be wrong; record that honestly
  rather than reporting a success.
- **GitHub Actions cron is not the schedule you asked for.** `*/15` on a private
  repo delivered a median gap of 66 minutes and as much as 162. Ask for hourly,
  set the scheduled time 30 minutes before the slot we want, and add a `push`
  trigger so an empty commit can nudge a late run. Make publishing idempotent so
  that is safe, and put `[skip ci]` on the record-back commit so it cannot loop.
- **A scheduled post cannot re-check anything** when it fires — not stock, not
  weather, not a countdown. Keep perishable figures out of the creative, or run
  a one-shot job ahead of the post while something is awake.
- **Timezones.** Convert to UTC against the offset in effect **on the posting
  date**, not today's. If our zone observes daylight saving, hand-computing this
  will eventually post at the wrong hour, in public, with no undo — so teach the
  schedule script to do it.

## Two grid rules worth having from day one

**Post in threes, with a type tile in the middle of every trio.** Instagram's
grid is newest-first, so a row is only intact while the count above it is a
multiple of three — every triptych breaks. But because the type tiles are all
the same distance apart, when it breaks *every tile shifts by the same amount*:
the stripe does not scatter, it migrates one column. Design for the rhythm, not
for a sentence spelled across nine squares.

**Copy goes in the image, not only the caption.** The grid is the ad; on a
profile grid the caption does not exist. Photo tiles carry the same kicker and
headline treatment as the type tiles so the two read as one system — which means
image prompts must ask for a quiet region (empty sky, a plain wall) for the type
to sit in. A beautiful frame with nothing quiet in it cannot carry a headline.

## Architecture

```
<channel>/
  BRAND_KIT.md      # what may and may not appear. Read every run.
  STRATEGY.md       # pillars, cadence, the two grid rules above
  PUBLISHING.md     # how a post reaches the feed; incidents as they happen
  SCHEDULE.md       # GENERATED by schedule.js — never hand-edited
  schedule.js
  imagecheck.js     # enforces rule 6
  ideas/            # the inbox. one idea, one file, never deleted
  queue/YYYY-MM-DD-<slug>/
    post.md         # the brief a human reads
    publish.json    # the package the publisher reads
publisher/
  publish.js  facebook.js  mock.js  test.js  whoami.js  renew-token.sh  SETUP.md
facts/              # or whatever we settle on in question 1
.github/workflows/publish.yml
.claude/skills/<name>/SKILL.md
```

**Two files per package, and the split is the point.** `publish.json` is
machine-readable: status, schedule, caption, media URLs, link, `source_images`.
`post.md` is for a human: where the idea came from, the claim table, the consent
record, what was deliberately left out, the alt text, the compliance checklist.
The second is why someone can come back in three months and know whether a post
was sound.

**The ideas inbox.** One idea per file, `YYYY-MM-DD-slug.md`, front matter with
`status: open | used | passed | parked`. Adding is cheap; deleting is not
allowed. An idea is resolved, never removed — `used` points at the package it
became, `passed` says what was wrong with it, `parked` names the blocker. A
passed idea with a reason stops the same idea coming back next week; without one
it guarantees it. Ideas that surface mid-run get written into the inbox, not
into a chat summary that evaporates when the session ends.

## Build order, with checkpoints

Do these in order. Stop at each checkpoint and show me.

**Phase 1 — the documents.** Brand kit, strategy, the source of truth, the ideas
contract. No code. These are what everything else is checked against, and
building the generator first means building it against nothing.
*Checkpoint: I read them and correct them.*

**Phase 2 — the publisher and its mock.** `publish.js`, `facebook.js`, the mock
that models the platform's real token behaviour, the test suite, `whoami.js`,
`renew-token.sh`, `SETUP.md`. Not wired to cron yet.
*Checkpoint: tests green, and `whoami.js` names the right account against the
real API.*

**Phase 3 — one real post.** I hand-write a single package and approve it. Dry
run first, then let it post for real while we both watch.
*Checkpoint: it is on the feed, the story went up, the Page crossposted, and the
media IDs are committed back.*

**Phase 4 — cron.** Only now.
*Checkpoint: a scheduled post lands within the hour we expected.*

**Phase 5 — the skill.** The generator goes in last, on purpose. A generator
pointed at an untested publisher is a way to find out about the publisher in
public.
*Checkpoint: one batch, which I approve post by post.*

**Phase 6 — the render pipeline.** Tiles as exact 1080×1350 and 1080×1920, made
by screenshotting an HTML page in headless Chromium with the fonts vendored into
the repo as `@font-face` files. Not a text-drawing filter, not an image library
— a browser, because a browser gets kerning and web fonts right.

## How I want you to work

- **Ask rather than fill gaps.** A ⚠ in a package is useful. A confident
  sentence covering a fact nobody checked is not.
- **Report failures honestly and specifically.** If two of four generated images
  passed QC, say "2 of 4". If a model silently downgraded, name the model that
  actually ran. If a step was skipped, say it was skipped. A clean-looking
  report that hides a gap is worse than no report.
- **Write the reasoning down, in the repo, next to the thing.** When something
  breaks, the fix goes in the file it belongs to along with what it cost. That
  is what makes this survive being handed to someone else — including a future
  you with no memory of this conversation.
- **Never hand-edit a generated file.** Regenerate it.
- **Commit and push at the end of every working session**, with a message that
  says why, not just what.

Start by asking me the five questions.

<!-- ─────────────── PASTE EVERYTHING ABOVE THIS LINE ─────────────── -->
