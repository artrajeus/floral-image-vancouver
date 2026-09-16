# Floral Image Brand Kit (social) — TEMPLATE

Fill every section. The skill reads this file before every run, and a section
left as a placeholder is a section the machine will quietly work around.

---

## Who we are

One paragraph. What the business actually does, for whom, where. Be specific
enough that a caption written from it could not describe a competitor.

Then the one-line positioning — the sentence a caption should never contradict.

---

## Product and service facts

**Do not put claimable figures here.** They live in `facts/` so they have a
single owner and a commit history. This section names *which* file holds what:

| Claim area | File |
|---|---|
| Service, inclusions, refresh interval | `facts/service.md` |
| Pricing | `facts/pricing.md` |
| Coverage area | `facts/coverage.md` |
| Clients we may name or show | `facts/clients.md` |
| Hiring terms | `facts/hiring.md` |

---

## Voice

Five to eight lines. Write them as contrasts, not adjectives — "we say X, not Y"
is checkable and "warm and professional" is not.

Then the voice check the skill runs before shipping: one question with a right
answer.

---

## Visual identity

- **Palette.** Hex values with names, and what each is for. Include the ink and
  the paper — the background colours matter as much as the accents.
- **Type.** Display face and body face, with the actual font files committed to
  the repo so renders are reproducible. Note the fallback behaviour to watch
  for: a broken font file falls back silently without erroring.
- **The looks.** Two or three named treatments every asset must land in, each
  with a prompt template or a render recipe. MXTology uses Noir Premium /
  Festival Sunlight / Loud Type. Name yours, and make one of them a
  photograph-free type tile — that is what carries the grid rhythm.
- **Tile specs.** 1080×1350 feed, 1080×1920 story. Margins, safe areas, where the
  kicker and headline sit.

---

## Consent register

The section with no MXTology equivalent, and the one most likely to cause real
harm if it is wrong.

### Clients we may show or name

| Client | May name? | May show premises? | Permission held | Date |
|---|---|---|---|---|

**Anyone not on this list is a no.** Not "probably fine", not "unrecognisable" —
no. Add a row before you add a photograph.

### People

Written consent held on file, per person, and anyone may withdraw it later. If
consent is withdrawn: the post comes down, and the source photograph is listed
under "Withdrawn" below so it is never reused.

### Withdrawn — never reuse

---

## Banned from the feed

Imagery and formats that never appear. Include the reason for each, because a
rule without a reason gets argued away in six months.

---

## Banned phrases — everywhere, not just the feed

Exact strings, with the reason attached. These get swept across the website and
any listings too, not only new posts.

Start with the fresh-flower family, since the product is maintained artificial
and preserved displays:

| Phrase | Why |
|---|---|
| "fresh flowers" (of a display that is not fresh-cut) | False claim about the product |
| "delivered fresh" | Same |
| "just picked" | Same |

> MXTology's list is four phrases that had made it onto 42 live product pages
> before anyone swept for them. Assume yours are already live somewhere and
> check the site, not just the queue.
