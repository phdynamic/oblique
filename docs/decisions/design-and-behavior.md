# Design and behavior decisions

## 2026-10-17 — Rare tier is drawn ~1 in 12 (active)
- Tier 3 is "Rare"; uniform draw would make it 1 in 6. Odds are `RARE_ODDS` in `index.html`.
- Rare card gets a gold inset border; tiers 1–2 are otherwise indistinguishable.

## 2026-10-17 — No immediate repeats (active)
- Draw re-rolls if it equals the last card shown.

## 2026-10-17 — Reduced motion skips the flip-through (active)
- `prefers-reduced-motion`: no flashing cards, no flip animation; result appears directly.

## 2026-10-17 — Flip-through shows symbols on card backs, never text (active)
- Requested by developer: other cards must not flash their text while drawing.
- Each step swaps a decorative symbol on the back (12 glyphs, `SYMBOLS` in `index.html`) with a quick edge-on turn; symbols don't map to cards.
- Supersedes the first version, which flashed random card text.

## 2026-10-17 — Tarot cards replace symbols; one strategy per card (active)
- Back of each card is its Rider-Waite-Smith image; flip-through shows other cards' art only. Landing card reveals its fixed strategy plus card name.
- 78 new strategies (not Tarot-themed, distinct from the original 60), reviewed and approved by developer in 5 batches.
- Supersedes: symbol backs, the 3-tier deck, and the rare-card odds/gold border (all removed).
- Card is 3:5 to match the art.
