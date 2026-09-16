# The content machine

This is a working description of the automated Instagram/Facebook content system
built for MXTology (`artrajeus/mxtology-content`), written so it can be stood up
again for Floral Image without rediscovering the same failures.

It is not a product. It is a repository, a Claude skill, and a publisher that
runs on GitHub Actions. The repository is the record of what went out; the skill
is the operator; the publisher is the only thing allowed to touch the platform.

Read `PORTING.md` for the file-by-file manifest. This file explains *why* the
parts exist, because the rules are the valuable bit and every one of them is
scar tissue.

---

## What it actually does

Once a day, without anyone opening Instagram:

1. A post that was approved days earlier, and is now due, is published to
   Instagram — image or carousel, plus the first comment, plus a 9:16 Story.
2. The same post is crossposted to the Facebook Page.
3. The resulting media IDs and timestamps are committed back to the repository,
   so the repo knows what is live.

And on demand, when asked for content:

4. Claude reads an ideas inbox, checks a brand kit and a strategy document,
   pulls live product/service data, generates or composites imagery, renders
   type tiles, verifies every claim against a source of truth, writes a package
   to a queue folder, and pushes.

Nothing publishes without a human approval recorded in the package. That is the
load-bearing rule and everything else is arranged around it.

---

## The shape

```
repo/
  <channel>/                    # "instagram/" in MXTology
    BRAND_KIT.md                # what may and may not appear. Read every run.
    STRATEGY.md                 # pillars, cadence, grid rules
    PUBLISHING.md               # how a post reaches the feed, and the failures
    SCHEDULE.md                 # GENERATED. never hand-edited.
    schedule.js                 # regenerates SCHEDULE.md from queue/ + ideas/
    imagecheck.js               # enforces "no photograph runs twice"
    ideas/                      # the inbox — one idea, one file, never deleted
      README.md                 # the inbox contract
      YYYY-MM-DD-slug.md
    queue/
      YYYY-MM-DD-slug/
        post.md                 # the brief: claims, reasoning, compliance
        publish.json            # the machine-readable package
  publisher/
    publish.js                  # Graph API client — images, carousels,
                                # reels, stories, first comments
    facebook.js                 # Page crosspost
    mock.js, test.js            # a fake Graph API and the suite against it
    renew-token.sh             # 60-day token renewal, run by the founder
    SETUP.md                    # scopes, app config, the traps
  .github/workflows/publish.yml # hourly cron + push trigger
  .claude/skills/<name>/SKILL.md # the operator
```

Two files per queued post, and the split matters. `publish.json` is what the
publisher reads: status, schedule, caption, media URLs, link. `post.md` is what
a human reads: where the idea came from, the claim table, what was deliberately
left out, the compliance checklist. The second one is why you can come back in
three months and know whether a post was sound.

---

## The rules, and what each one cost

These are ordered by how much damage they prevent.

### 1. Claude never approves anything

`post.md` front matter carries `status: draft | approved | posted` and
`approved_by`. The publisher refuses to post anything not `approved`, and the
skill is explicitly forbidden from setting that field. Only the founder
approves, recorded with a name and a date.

Without this, a system that can generate and publish is a system that can
publish something wrong at 8am with no one awake.

### 2. Every number comes from a tool call made in the same session

A drop caption once claimed "59 pouches left" against a live inventory of 19.
Nobody lied — the number came from an earlier conversation and was stale by the
time it shipped.

The rule now: any figure in public copy — price, stock, spec, rating, count —
traces to a call made today, and the package names the call. Where an API offers
several plausible fields, the rule names the *exact* one (`available`, never
`totalInventory`, which counts committed stock and overstates what a customer
can actually buy).

### 3. The fact gate: never infer a spec from what you already know

The Espresso Martini was written as vodka, because that is what an Espresso
Martini is. MXTology's is spiced rum. The founder caught it.

Every post that names a thing is built from that thing's full record, fetched
fresh. Summary/search endpoints are for *finding* the record, never for quoting
it — they truncate, and the truncation hides exactly the fields you are about to
get wrong. Each `post.md` carries a claim table:

| Claim | Verified against |

If the source of truth does not state something, it is left out or flagged ⚠ for
the founder. It is never filled with a plausible guess.

### 4. AI never draws the thing you sell

For MXTology that is the pouch: a redrawn label is a misleading-packaging risk
and brand drift in one. The sanctioned paths are compositing a real photograph,
or generating assets that contain no product at all.

Where AI *does* render the product — via reference elements — **every image is
checked at 1:1 against the reference before it can be used.** Not at thumbnail
size, not on a contact sheet. Zoomed to native pixels. That check has caught, in
this project alone: a wordmark rendered upside down, a wordmark reading
`NATOLOGY`, another reading `MATOLOGY`, a mirrored flavour name, an entirely
invented pack with a made-up name band and a cocktail glass on it, and liquid in
the wrong colour four separate times.

The hit rate without that check would be poor and the failures are invisible at
feed size — which is exactly what makes them dangerous. They surface later, on a
product page, in print, in a screenshot.

A generalisation worth carrying over: **the model stops reproducing a label and
starts designing one when the product is small in frame.** Under roughly 150px
on a 2k render it will invent. The fix is compositional — get closer, put one
product in frame, say what it must not invent — not a re-roll.

### 5. AI people are never presented as real people

Styled advertising imagery with people in it is fine. An AI person captioned as
a customer, a testimonial, or a member of staff is not. "The line is the claim,
not the pixels."

### 6. No source photograph runs in two posts

The obvious version of this check finds nothing. Every tile is a composite —
type, scrims and crop are baked in — so the same photograph produces two
different output files with two different names. Comparing outputs found 101
distinct files and zero repeats while the same photo sat in two of them.

The check has to be on the **source**. Every `publish.json` records
`source_images`: the underlying photographs by working filename. `imagecheck.js`
reports repeats, and distinguishes three states that mean different things:

- `["scene-x.webp"]` — one photograph
- `[]` — a type tile, genuinely no source
- field absent — **unrecorded**, and reported as a gap

The empty array and the missing field are not the same, and conflating them is
how a check quietly passes on a queue it cannot see.

### 7. Verify the asset, not the intention

Two shipped defects with one cause: tiles rendered with a broken 14-byte font
file that silently fell back to a system face, and alt text describing a
headline that had since been rewritten.

So: after rendering, **open the images**. Confirm the display face is the one you
specified. Write alt text last, from the finished image. Check the media URL
returns `200` *and* `image/jpeg` — a post once failed because the URL returned an
HTML error page and the platform said only "Only photo or video can be accepted
as media type".

### 8. A mock that shares the code's assumptions tests nothing

Seventeen green assertions certified a publisher that could not post to Facebook
at all. The real Graph API hands out a *separate* token for a Page and rejects
the user token on Page endpoints. The mock did not model that, because it was
written from the same misunderstanding as the code.

The mock now issues two distinct tokens and rejects the wrong one. Suite is 29
assertions across 7 scenarios.

---

## The grid rules (portable, and worth keeping)

**Post in threes, and put a type tile in the middle of every trio.** Instagram's
grid runs newest-first, so a row is only intact while the count above it is a
multiple of three — every triptych breaks eventually. But because the type tiles
are all the same distance apart, when the pattern breaks **every tile shifts by
the same amount**. The stripe does not scatter, it migrates. One stray post moves
it from the centre column to the right.

Design for the rhythm, not for a sentence spelled across nine squares, and the
grid never looks broken.

**Copy goes in the image, not only in the caption.** The grid is the ad. A
caption is a click away and on the profile grid it does not exist at all. Photo
tiles carry the same kicker/headline treatment as the type tiles so the two read
as one system — which in turn means image prompts must ask for a quiet region
(empty sky, a plain wall) for the type to sit in. A beautiful frame with nothing
quiet in it cannot carry a headline.

---

## Things that are true about the platform and cost a day each

- **`backdated_time` does not work.** Backfilled posts land stamped with their
  creation time. If you are backfilling a Page, the dates will be wrong and
  there is nothing to be done about it. Say so rather than recording a success.
- **Tokens expire every 60 days**, and `debug_token` withholds `expires_at` when
  a token inspects itself — so "days remaining" has to be counted from a
  first-seen date the repo records, keyed on a hash of the token.
- **Facebook grants a scope and a Page in two separate clicks** and silently
  skips the second. A token can hold every scope and still see zero Pages. The
  dialog only reappears when you request a scope it has not seen before — so
  adding any new scope forces it back. That trick is the fix.
- **GitHub Actions cron is not the schedule you asked for.** `*/15` on a private
  repo delivered a median gap of 66 minutes and as much as 162. Ask for hourly,
  set `scheduled_utc` 30 minutes before the slot you want, and add a `push`
  trigger so an empty commit can nudge a late run.
- **A scheduled post cannot re-check anything.** Not stock, not weather, not a
  countdown. Either keep perishable figures out of the creative, or run a
  one-shot job ahead of the post to verify while something is awake.

---

## Standing it up for Floral Image

See `PORTING.md` for the manifest. The order that works:

1. **Create the repo.** `artrajeus/floral-image-content`, private. Copy the
   publisher and the two scripts verbatim; write the three documents from the
   templates.
2. **Decide the source of truth.** This is the one genuinely new decision, and
   §3 does not work without it — see `PORTING.md` §2.
3. **Decide where images are hosted.** Also new — see `PORTING.md` §3.
4. **Stand up the Meta app and token** following `publisher/SETUP.md`, six
   scopes, ticking the Page. Run `renew-token.sh`.
5. **Run the publisher in dry-run** against one hand-written approved package
   before letting cron near it.
6. **Only then** install the skill and ask for a batch.

Do not skip step 5. The first live run is where every assumption you inherited
gets tested at once, in public.
