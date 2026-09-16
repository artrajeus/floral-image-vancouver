# MXTOLOGY — working facts

Standing facts for this account. Check here before assuming anything about logistics, dates or product.

## Business

- **MXTOLOGY** — ready-to-drink cocktail pouches, Australia. Store: mxtology.com.au (Shopify). Currency AUD, timezone AEST.
- Hero product format: **130ml resealable pouch**, 8.7–16% ABV, glass-free. Twelve-pouch event packs retail **$159**.

## Dispatch — important

- **We dispatch from Mitchell, ACT.** All transit estimates start from Canberra.
- The Shopify location record ("Mxtology HQ") still lists **38 Sydenham Road, Norwood SA 5067**, which is **out of date**. Do not use it for transit maths. Worth correcting in Shopify, since it can affect rate calculation and labels.
- Practical consequences of a Canberra origin:
  - **Wee Jasper / Dragon Dreaming is ~1 hour away** — express is effectively overnight. Our strongest delivery position of the three events.
  - **Deniliquin** is a short interstate hop — express is comfortable at 1–2 business days.
  - **Mareeba / Far North Queensland is the long haul** — express is 3+ business days. For anything FNQ, transit is the binding constraint, not the customer's departure date. Set cut-offs earlier than feels necessary.
- **ACT public holidays stop dispatch.** Labour Day in the ACT is the **first Monday in October** — in 2026 that is **Monday 5 October**. Never schedule a dispatch-dependent cut-off across it.

## Shipping profiles (Shopify)

| Profile | ID | Rate |
|---|---|---|
| General profile (default) | `76624461858` | Free standard over $100; $7.97 under; Express $30 |
| Event Packs — Express Included | `136735195170` | **$0 AusPost Express** — this is the one to move event packs into for the final run |
| MXTology Club — Free Shipping | `137169797154` | Free standard for members |

Moving a variant into the Express profile makes free express automatic at checkout — no code, nothing to select. Rename the variant to `12 Pack — FREE Express Post` at the same time so the storefront matches.

## Date discipline

Always confirm the weekday of a date before putting it in copy — this has gone wrong before ("Friday 19 September" when the 19th was a Saturday). Cheap to check, expensive to publish.

Never bake a shipping deadline into an **image**; it strands the asset when the date passes. Deadlines belong in editable text — page copy, ad primary text, email body.

## Klaviyo

- Campaigns created via the API land in **Draft** and **do not send on their own**, no matter what send time is set. Someone has to press send. Three event emails have already lapsed unsent this way.
- The connector **cannot create segments**, only lists. Geo segments must be built in the Klaviyo UI.
- Templates already bound to a campaign message return 404 on update. The way round it is create a new template, then `assign_template_to_campaign_message`, which clones it onto the message.
- Useful audiences: `WYgbYS` Engaged 90 days · `UcUqnz` Canberra Beer and Cider Fest · `XvccHi` Easter Friday Canberra Races · `UubAay` **Everyone** (avoid — mailing the whole database produces more unsubscribes than clicks).

## Imagery

See `marketing/october-parallel-campaigns.md` for the full rules. The short version: only use MXTOLOGY pouch elements already loaded in Higgsfield, never let the model invent a pouch, and frame tight when label text has to be legible.
