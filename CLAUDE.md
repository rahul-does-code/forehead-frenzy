# Forehead Frenzy

A free Heads Up-style charades party game. One self-contained file: `index.html`.
Live at **https://rahul-does-code.github.io/forehead-frenzy/** (GitHub Pages, branch `main`, root).
The owner plays it from their iPhone home screen and frequently asks Claude (often from the
phone app) to add decks or cards — these updates should be fast and small.

## How to add decks / cards

Everything lives in the `DECKS` array inside the inline `<script>` in `index.html`:

```js
{ id: 'unique-id', name: 'Deck Name', icon: '🎵', color: '#F5379B', words: ['Card one', 'Card two', ...] }
```

- Deck colors rotate through: `#F5379B` (magenta), `#FFC53D` (brass), `#1FC16B` (green), `#7B6CF6` (violet).
- Aim for ~50 cards per deck; keep entries short enough to read across a room, family-friendly by default.
- Use curly apostrophes (’) inside single-quoted JS strings — no backslash escapes.
- Commit and push to `main`; Pages redeploys the same URL in ~1 minute. Nothing to reinstall on the phone.

## Constraints

- `index.html` must stay fully self-contained: no CDNs, fonts, images, or fetch calls.
- Keep `<meta charset="utf-8">` first in `<head>` (emoji break without it).
- CSS gotcha: `#home` and `#results` use author `display:flex`, so hiding them relies on the
  explicit `#home[hidden], #results[hidden] { display: none }` rule — don't remove it.
- Tilt input: `devicemotion` (gravity z) with a `deviceorientation` fallback, auto sign
  calibration, a "Flip tilt" setting, and a "Tilt sensor → Test" diagnostic in Settings.
  Tap zones (right = got it, left = pass) always work as backup.
- The rotated portrait layout (`#stage`) maps iPhone safe-area insets through the 90° turn —
  preserve those `calc()` expressions.
- A legacy copy exists as a claude.ai artifact (tilt doesn't work there — its page wrapper
  blocks motion sensors). GitHub Pages is the real deployment; update the artifact only if convenient.
