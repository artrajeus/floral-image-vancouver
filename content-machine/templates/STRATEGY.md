# Floral Image social strategy — TEMPLATE

Sections 1–4 are yours to write. **Sections 5 and 6 are structural and should be
copied nearly verbatim** from `mxtology-content/instagram/STRATEGY.md` — they are
about how Instagram's grid behaves and how a duplicate check has to work, not
about cocktails.

---

## 1. Where we are

A feed audit. What the grid looks like today, what is working, what is not.
Do this before deciding anything — it dates the document and gives the next
audit something to compare against.

## 2. What the research says

The evidence base for the choices below. Cite it. A strategy whose reasoning is
not written down gets relitigated every quarter by whoever is in the room.

## 3. The strategy

### Positioning
One sentence. The thing a caption must never contradict.

### The unique style
What makes the grid unmistakably yours at thumbnail size, before anyone reads a
word. For a service business this is usually a consistent treatment rather than
a consistent subject — you do not control the lobbies.

### Content pillars
Four or five, each with a one-line definition and an example. The skill rotates
through these so a batch covers most of them.

Starting suggestions for this business, to accept or replace: **The Route** (the
work itself, the van, the early mornings) · **The Space** (a real install, with
consent) · **Behind the Displays** (how they are built and maintained, why
artificial and preserved) · **Say It Loud** (type tiles — the pillar that carries
the grid rhythm) · **Working Here** (recruitment, under the stricter rules).

### Cadence
The output contract the machine is held to. Be honest about what a single-city
B2B service actually has to say — three posts a week that are all true beats
seven where two are padding.

### Every post ships with
The fixed elements: 4:5 feed tile, 9:16 story, alt text, first comment, link.

### Conversion stack
What a post is actually for, and where it sends people. Name the destination
URLs so captions do not invent them.

### KPIs
In priority order, checked monthly. Put the one that matters first and resist
listing reach.

---

## 5. Posting in threes, and the stripe that survives it

**Copy this section verbatim from MXTology.** The short version:

Instagram's grid runs newest-first, so three posts sit at slots 0-1-2 — a row.
Post one more and they slide to 1-2-3, split across two rows. **Every grid
triptych breaks eventually**, and anyone who says otherwise has not run one past
the first dated post that forced a single.

The rule that makes it survive: **in every trio, the middle post chronologically
is a type tile** — solid ground, display type, no photograph. While the rhythm
holds they form a vertical stripe down the centre column. And when it breaks,
every type tile shifts by the same amount, because they are all the same distance
apart. The stripe does not scatter, it migrates: one stray post moves it to the
right column, two to the left. Still a stripe, still one per row, still evenly
spaced.

```
posting in threes          after ONE extra post
▓ █ ▓                      ▓ ▓ █          █ = type tile
▓ █ ▓                      ▓ ▓ █          ▓ = photograph
▓ █ ▓                      ▓ ▓ █
```

Design for the rhythm. The sentence spelled across nine squares is a bonus for
the fortnight it lasts.

---

## 6. No photograph runs twice

**Copy this section verbatim from MXTology**, and take it more seriously than
they do — a service business in one city has a finite library of real install
photographs, and the temptation to re-run a good one is much stronger than it is
for a brand that can shoot another product still life.

The part that is easy to get wrong: **the obvious check finds nothing.** Every
tile is a composite — type, scrims and crop baked in — so two posts built on the
same photograph produce two different files with two different names. On the
sister project, comparing output files found 101 distinct files and zero repeats
while the same photograph sat in two live posts.

The check has to be on the **source**, which means every package records
`source_images` and three states have to stay distinguishable:

- a filename — one photograph
- `[]` — a type tile, genuinely no source
- the field absent — unrecorded, and reported as a gap, not passed

Conflating the last two is how a duplicate check quietly passes on a queue it
cannot actually see.

### Where replacements come from

When the rule blocks a good post, it needs somewhere to go. Options, cheapest
first: a type tile instead (the quote or the stat was probably better as type
anyway), a different crop of a *different* source, a new generation, or a real
shoot. Write down which of these are available to you, because the rule is only
sustainable if the answer is not "argue with the rule".
