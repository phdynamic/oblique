# Architecture and hosting decisions

## 2026-10-17 — Static files, no build step (active)
- Plain HTML/JS/CSS; cards loaded via `<script src="tarot.js">` (was deck.js) so it works from `file://` too.
- Repo `phdynamic/oblique` is separate from the home-dir repo (`twitterarchive`); never set remotes from a subfolder without checking `git rev-parse --show-toplevel`.

## 2026-10-17 — Art from Wikimedia Commons RWS scans, shrunk to 360x600 (active)
- API listed all 78 files as "Public domain"; thumbnails fetched then re-encoded (JPEG q78, centre-cropped to 3:5) → ~78KB each, 6.1MB total.
- All images preloaded on page load so the flip-through never shows a blank back.
- `deck.js` removed; `tarot.js` replaces it.
