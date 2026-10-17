# Design and behavior decisions

## 2026-10-17 — Rare tier is drawn ~1 in 12 (superseded)
> Superseded: rare tier removed with the Tarot deck.
- Tier 3 is "Rare"; uniform draw would make it 1 in 6. Odds are `RARE_ODDS` in `index.html`.
- Rare card gets a gold inset border; tiers 1–2 are otherwise indistinguishable.

## 2026-10-17 — No immediate repeats (active)
- Draw re-rolls if it equals the last card shown.

## 2026-10-17 — Reduced motion skips the flip-through (active; now applies to the reel)
- `prefers-reduced-motion`: no flashing cards, no flip animation; result appears directly.

## 2026-10-17 — Flip-through shows symbols on card backs, never text (superseded)
> Superseded by the Tarot decision below, and the flash mechanism by the vertical reel decision (the no-text rule still holds).
- Requested by developer: other cards must not flash their text while drawing.
- Each step swaps a decorative symbol on the back (12 glyphs, `SYMBOLS` in `index.html`) with a quick edge-on turn; symbols don't map to cards.
- Supersedes the first version, which flashed random card text.

## 2026-10-17 — Tarot cards replace symbols; one strategy per card (active)
- Back of each card is its Rider-Waite-Smith image; flip-through shows other cards' art only. Landing card reveals its fixed strategy plus card name.
- 78 new strategies (not Tarot-themed, distinct from the original 60), reviewed and approved by developer in 5 batches.
- Supersedes: symbol backs, the 3-tier deck, and the rare-card odds/gold border (all removed).
- Card is 3:5 to match the art.

## 2026-10-17 — Vertical reel replaces the edge-on flash; hold before flip (active)
- Requested by developer: cards should look shuffled top→bottom or bottom→top, pausing on the selected card before it flips.
- A strip of 18 face-down cards (`REEL_CARDS`) slides through a card-sized window over 3.08s (`SPIN_MS`; was 2.8s, slowed 10% at developer request) with ease-out `cubic-bezier(.33,1,.68,1)`; direction is random per draw (chosen card is the first strip item for downward travel, the last for upward).
- Once stopped it holds 700ms face-down, then the card flips to reveal the strategy.
- Reduced motion: no reel, no hold; the card flips straight to the result.
- Supersedes: the 9-step edge-on symbol/back flash.
- Rejected: easing `cubic-bezier(.12,.6,.15,1)` — covered 99% of the distance in 0.5s, then crawled for 2s.

## 2026-10-17 — Previous card disappears instantly on a new draw (active)
- Requested by developer: the old card must not sit behind the reel cards as they cycle.
- On "Draw another" the card is hidden at once (`.gone` = `visibility:hidden`, un-flipped with transitions off); no flip-back. It reappears face-down under the reel when the reel stops, then holds and flips.
- Applies to the first draw too (hides the idle card back behind the reel).
- Supersedes: the 700ms flip-back before each spin.

## 2026-10-17 — Click (or Enter/Space) turns the revealed card over (active)
- Requested by developer: flip the card to look at the other side. Strategy side ⇄ Tarot art side.
- Enabled only after the first reveal (`.flippable` on the stage); ignored while a draw is running; a new draw resets the card face-down and hides it as before.
- Stage becomes `role="button"`, `tabindex=0`, `aria-label="Turn the card over"`; focus ring uses `--focus`.
- Reuses the existing `.face-up` toggle and 0.7s flip; no new animation.
