# Oblique — agent entry point

Concept: static web app. Press a button, Tarot cards flip past face-down, one lands and flips to reveal its one strategy (78 Rider-Waite-Smith cards, 78 strategies).

Reading order: this file → [STATUS.md](STATUS.md) → [NEXT-SESSION.txt](NEXT-SESSION.txt).

| Need | File |
|---|---|
| What's built / tested | [STATUS.md](STATUS.md) |
| Why a choice was made | [DECISIONS.md](DECISIONS.md) → `decisions/` |
| When something changed | [BUILD-LOG.md](BUILD-LOG.md) → `build-log/` |
| Recurring lessons | [standing-rules.md](standing-rules.md) |
| Where we left off | [NEXT-SESSION.txt](NEXT-SESSION.txt) |
| Live checks owed | [TESTING-OWED.md](TESTING-OWED.md) |

Architecture (rarely changes):
- No build step. `index.html` + `tarot.js` + `cards/NN.jpg` (360x600), hosted on GitHub Pages.
- `docs/tarot-strategies-draft.md` is the source of truth for card text; `tarot.js` is generated from it. Card N in `cards/` = Nth row (Major 0-21, Wands, Cups, Swords, Pentacles).
- Art: Rider-Waite-Smith (1909), Wikimedia Commons, all marked Public domain at download time.
- `oblique-strategies-deck.md` (original 60) is an archive; the app no longer uses it.