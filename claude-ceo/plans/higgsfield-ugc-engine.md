# Plan: Higgsfield UGC Engine

**Goal (founder, 2026-08-17):** stop depending on shooting real footage. Feed our
own winning videos into Higgsfield as reference and have it produce its own
versions, so UGC-style creative becomes something we generate on demand.

**Status:** plan only. Nothing generated yet.

## Why this matters now

`#3 - MOF` is dead — $0 spend on 14, 15 and 16 August. The whole campaign was
carried by **one video**:

| Ad | Spend | CTR | Purchases | Revenue | ROAS |
|---|---|---|---|---|---|
| "Thats good, Its Strong, Delicious – Build your case" (video) | $2,417.95 | 4.90% | 46 | $6,367.31 | 2.63× |
| "Thats good, Its Strong, Delicious" (old destination) | $528.80 | 4.80% | 2 | $168 | 0.32× |
| AI Static – Tommy's Margarita | $6.84 | 1.15% | 1 | $82 | — |
| AI Static – Aussie Berry Bliss | $13.12 | 1.43% | 0 | $0 | 0 |
| AI Static – Amaretto Whisky Sour | $13.66 | 0.28% | 0 | $0 | 0 |

(30 days to 2026-08-16, ad set `First Impressions – Copy`, via Windsor.)

One creative did 46 of 49 purchases. It has now fatigued. **Creative supply is
the bottleneck on the account's main revenue engine**, which is exactly what this
is meant to fix.

**Sober note:** every AI creative we have run in this ad set has underperformed
the real video by 3–17× on CTR. That is a small sample on tiny spend, but it is
the only evidence we have, and it points the same way. This plan is therefore
structured as a cheap test, not a bet.

## What Higgsfield can and cannot actually do

Verified against the live MCP tool surface on 2026-08-17. Account: **Ultra plan,
1,285.76 credits.**

**It cannot** take our video and "re-render it" in new variants. There is no
video-to-video restyle of our own footage — the `faceless-channel-video`
workflow explicitly excludes it. Two real routes exist instead:

### Route A — extract the formula, regenerate (the scalable one)

1. `video_analysis_create` on the winning ad → scene-by-scene breakdown.
   *Caveat from the tool itself: accuracy drops as clips get longer, so analyse
   the 15–30s ad, never a long cut.*
2. Turn that breakdown into a brief: hook beat, reaction beat, product beat, CTA.
3. Run `ugc-flow` (talking-head creator review — the default UGC workflow) with
   that structure and the approved pouch Element as the product reference.
4. Variants come from re-running with different creators/settings, not from
   re-rendering our footage.

Other workflows available if we want different formats later:
`ugc-product-flow` (product only, voiceover), `ugc-unboxing-flow`,
`ugc-try-on-flow`, `ugc-tutorial-flow`, `ugc-saas-flow` (builds from a page URL —
could run straight off the build-your-case landing page).

### Route B — motion transfer (narrow, high fidelity)

`motion_control` (Kling 3.0) takes **a character still + a reference motion
video** and animates the still with the video's motion and camera move. That is
the literal "use our video as the reference" mechanic — same performance, a
different person. Useful for cloning the exact beat that works. Not a volume play.

### Supporting tools worth using

- `virality_predictor` — score hook strength before we spend on the ad, not after.
- `personal_clipper_create` — cut longer footage into shorts.
- `reframe` — 9:16 / 1:1 / 4:5 versions without regenerating.
- `upscale_video` — finish to 2K/4K.

## Blocker

**We do not have the source video file.** Options, cheapest first:

1. If the ad is on our YouTube, `video_analysis_create` takes a YouTube URL
   directly — no upload needed.
2. Otherwise: export it from Meta Ads Manager and drop the file or an HTTPS link
   to me; `media_import_url` pulls it straight in (50 MB limit).

Nothing in Route A or B starts without this.

## Hard gate before anything ships

`QUALITY-STANDARDS.md` already records that generated pouch imagery garbles the
label in two compositions (pouch on its side, multiple pouches in frame). **Video
is a harder case, not an easier one — every frame has to hold the label.**

So: no generated video reaches an ad account until it has been watched
frame-by-frame against the real pouch, checking MXTOLOGY spelling, correct
flavour name the right way up, gradient M monogram, and no third-party
trademarks. Same standard as the statics, applied per frame. If the label breaks,
we use `ugc-product-flow` with a real product photo composited rather than a
generated pouch.

## Proposed first test (cheap, decision-grade)

| Step | Action | Gate |
|---|---|---|
| 1 | Get the source video (founder) | — |
| 2 | `video_analysis_create` → structure of the winner | Read the breakdown together |
| 3 | Generate **3** `ugc-flow` variants on that structure | Label check, frame by frame |
| 4 | `virality_predictor` on all 3 | Keep the top 2 |
| 5 | Launch as a **new** MOF campaign (fresh campaign resets Meta's learning; the current one is throttled to $0) | — |
| 6 | Read at 3 days vs the old video's 4.9% CTR baseline | Beat it → scale. Miss badly → the AI route is closed for this format and we shoot real footage |

Keep step 3 to three variants. The point is to find out whether the format works
at all before building a factory on top of it.

## Open questions for the founder

1. Where is the source video — YouTube, or does it need exporting from Meta?
2. Do we have a real creator's face/likeness we're allowed to use as the
   character still for Route B, or does it have to be a generated person?
3. Ship generated UGC under the MXTology brand without disclosure, or label it?
   Worth deciding before it goes live, not after.
