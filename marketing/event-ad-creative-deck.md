# Event Ad Creative Deck — copy baked into the image

**Built 16 Sep 2026.** Three festivals, one formula, taken straight from what Mundi Mundi proved: **the scroll-stopper is the event's own rule, not our product.** Mundi ran 5.5× ROAS at 11.7% CTR on event-named creative while the same list converted 1 order per 1,199 emails. Nobody stops for "bar-quality cocktails". They stop for a fact about the festival they've already bought a ticket to.

## The rule of the format

Every creative is **4:5**, and every one has three text zones:

| Zone | Job | Rule |
|---|---|---|
| **Black band, top quarter** | The interrupt — the event's own restriction, stated flat | Max 4 words on line 1. White. |
| **Cyan line under it** | The turn — what that restriction means for them | Max 6 words. |
| **Pink strip, bottom edge** | Qualifier — event name + glass-free | Small caps, one line. |

**Why a solid band and not type over the photo:** flat colour behind lettering renders cleanly; type laid over a busy photo is what produced the butchered labels on the first Deni page. Keep it.

**Do not bake the shipping deadline into the image.** It goes stale in days and strands the asset — Dragon Dreaming's "order by Mon 14 Sep" is already dead copy. Deadlines live in the ad's primary text, where you can edit them daily. The one exception is the final-48h variant, which is a deliberately disposable asset.

---

## 1. Deni Ute Muster — 2–3 Oct, Deniliquin NSW

**The rule that does the work:** one carton per adult camper, max thirty cans of beer **or pre-mix spirits**, or a 4L cask. Strictly no glass. BYO campsite only — nothing into the Festival Arena.

**Why it stops the scroll:** the allowance is a number every Deni camper already has in their head. We're not adding to it, we're re-spending it.

### In-image copy

| | Line 1 (white) | Line 2 (cyan) | Strip |
|---|---|---|---|
| **A — lead** | YOU GET 30 | MAKE 12 OF THEM COUNT | DENI UTE MUSTER · STRICTLY NO GLASS |
| B | 30 CANS. NO GLASS. | TWELVE OF THEM COULD BE COCKTAILS | DENI UTE MUSTER · PRE-MIX IS ALLOWED |
| C | PRE-MIX IS ALLOWED | NOBODY SAID IT HAD TO BE BEER | DENI UTE MUSTER · STRICTLY NO GLASS |
| D — final 48h | LAST DAY TO ORDER | IT WON'T BEAT YOU TO DENI | FREE SHIPPING ENDS TONIGHT |

### Ad text

**Primary text**
> Deni lets every adult camper bring one carton — thirty cans of beer or pre-mix spirits. Most of the paddock spends all thirty on the same warm tinnies.
>
> The Deni Pack is twelve bar-made cocktails in pouches. They count as pre-mix, so they fit inside your allowance. They're glass-free, so they clear the gate. And they take up one shelf of the esky.
>
> Same allowance as everyone else. Considerably better camp.

**Headline:** Twelve cocktails inside your 30-can allowance
**Description:** Glass-free. Free shipping. $159.
**CTA:** Shop now

---

## 2. Savannah in the Round — 8–11 Oct, Kerribee Park, Mareeba QLD

**The rule that does the work:** the festival precinct is completely dry — no BYO alcohol past the gate at all, bags searched, glass-free across the whole site. BYO is welcome at the campgrounds.

**Why it stops the scroll:** most people assume "BYO festival" means BYO everywhere. Being told the precinct is dry is genuinely new information, and it reframes camp as the only bar they control.

### In-image copy

| | Line 1 (white) | Line 2 (cyan) | Strip |
|---|---|---|---|
| **A — lead** | THE PRECINCT IS DRY | YOUR CAMP DOESN'T HAVE TO BE | SAVANNAH IN THE ROUND · GLASS-FREE SITE |
| B | NOTHING CROSSES THE GATE | SO STOCK THE SIDE THAT'S YOURS | SAVANNAH IN THE ROUND · BYO AT CAMP |
| C | 30°C. FOUR DAYS. | ONE ESKY SHELF SORTS IT | SAVANNAH IN THE ROUND · GLASS-FREE SITE |
| D — final 48h | FNQ TAKES LONGER | ORDER TODAY OR MISS THE RANGE | FREE SHIPPING ENDS TONIGHT |

### Ad text

**Primary text**
> Savannah's festival precinct is completely dry. No BYO past the gate, bags searched on entry, and the whole site is glass-free.
>
> Which makes your campground the only bar you actually control for four days. Worth stocking properly.
>
> The Savannah Pack is twelve bar-made cocktails weighted tropical on purpose — Piña Colada, Tommy's Margarita, Mai Tai — because thirty degrees on the Tablelands is no place for something heavy.

**Headline:** The precinct is dry. Your camp doesn't have to be.
**Description:** Glass-free. Free shipping. $159.
**CTA:** Shop now

> **FNQ note:** delivery into Mareeba/Cairns runs longer than the southern states, so the binding constraint is transit, not their departure date. Say so in the ad — it converts urgency that's otherwise invisible.

---

## 3. Dragon Dreaming — 25–28 Sep, Wee Jasper, Lake Burrinjuck NSW

**The rule that does the work:** no alcohol is sold on site at all. Fully BYO, glass confiscated at the gate, security screens for excessive quantities. Barefoot festival.

**Why it stops the scroll:** this is the strongest scarcity story of the three and the only one that's absolute. There is no fallback bar. What they carry in on Thursday is the entire weekend.

### In-image copy

| | Line 1 (white) | Line 2 (cyan) | Strip |
|---|---|---|---|
| **A — lead** | THERE IS NO BAR | YOU ARE THE BAR | DRAGON DREAMING · NOTHING SOLD ON SITE |
| B | NO BAR. NO GLASS. | NO RE-SUPPLY. | DRAGON DREAMING · WEE JASPER |
| C | WHAT YOU CARRY IN | IS THE WHOLE WEEKEND | DRAGON DREAMING · GLASS IS CONFISCATED |
| D — barefoot angle | IT'S A BAREFOOT FESTIVAL | THAT'S WHY GLASS IS BANNED | DRAGON DREAMING · POUCHES CAN'T BREAK |

### Ad text

**Primary text**
> No alcohol is sold anywhere at Dragon Dreaming. Whatever you carry into Wee Jasper on Thursday is what you're drinking until Monday — and glass is confiscated at the gate.
>
> So the esky you pack *is* the weekend. There's no walking up to a bar when it runs dry, and the nearest bottle shop is a long way back down the road.
>
> Twelve bar-made cocktails, completely glass-free, clipped to a lanyard so you can dance with both hands.

**Headline:** There's no bar at Dragon Dreaming
**Description:** Twelve real cocktails. Glass-free. $159.
**CTA:** Shop now

---

## Testing plan

Run **one campaign per event**, three creatives each (A lead + two challengers), same budget, same audience. Kill on CTR first — Mundi's 11.7% is the benchmark and a creative under ~4% is not stopping anyone. Only then judge ROAS.

The variable being tested is **which restriction stings most**, not which photo is prettiest. Keep the photo constant within an event so the copy is the only thing moving.

## Production notes

- Generated on Higgsfield; requested `nano_banana_pro` but the service **actually ran `nano_banana_2`** on every job (visible in `jobs_wait` metadata).
- Winning method: generate the headline band **onto an already-approved close-up** passed as `image_references`. Generating the whole ad from scratch renders the copy perfectly but redraws the pouches too tall (~1.5–1.6 h:w against the real 1.36) and can swap Pornstar's artwork for a comic-book girl.
- Lettering renders reliably at this size — the earlier label failures were pixel density, not prompting. Big type on flat colour is the easy case.
