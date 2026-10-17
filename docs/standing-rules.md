# Standing rules

- Check `git rev-parse --show-toplevel` before touching remotes. → build-log/2026-10.md, 2026-10-17
- Edit strategies in `docs/tarot-strategies-draft.md`, then regenerate `tarot.js`. → build-log/2026-10.md, 2026-10-17
- Preview pane can't load sibling files from file://; test over `python3 -m http.server`. → build-log/2026-10.md, 2026-10-17
- Browser-pane animation tests: front the tab first (`tabs_select`); background tabs freeze animations. Keep scripts short or run async and poll. → build-log/2026-10.md, 2026-10-17
- Web Animations with `fill: 'forwards'` leave finished animations behind; `getAnimations()[0]` is the oldest, not the current. → build-log/2026-10.md, 2026-10-17
- Measure sizes only after an element is displayed; `display:none` elements report 0. → build-log/2026-10.md, 2026-10-17
- Percent heights need a parent with a definite height. → build-log/2026-10.md, 2026-10-17
