# Madame Claude — Implementation Notes

## Overview
Madame Claude is a tarot reading parlor page. It deterministically draws
cards (based on a seed derived from the day or a user-supplied override) and
optionally sends the reading + user's input to the Anthropic API directly
from the browser for a Claude-generated interpretation. Without an API key,
a local/offline reading voice is used instead.

## Structure
- `index.html` — main markup: consult form, settings (spread, seed, API key,
  model), card table/spread, and reading output panel.
- `css/base.css` — resets, typography, buttons, focus states, reduced-motion.
- `css/parlor.css` — page background, header, footer, deck shuffle animation.
- `css/cards.css` — card spread layouts (single, three-card, Celtic Cross),
  flip animation, captions.
- `css/panels.css` — form/panel styling, settings grid, reading text panel.
- `js/main.js` (module entry) — wiring for form submission, deck shuffle,
  card reveal, and reading rendering/streaming.

## Navigation
- Added a "← Home" link at the top of the page header (`.parlor__home`)
  linking to `/`, so visitors can return to the site root/index from the
  game page. Styled subtly with `--ink-dim` color, brightening to `--gold`
  on hover/focus to match the parlor's aesthetic.

## Privacy / API Key Handling
- The API key field is optional. When provided, requests go directly from
  the browser to `api.anthropic.com`. The key is not persisted unless the
  "Remember on this device" checkbox is checked.

## Follow-ups
- If additional footer/header navigation is needed (e.g. links to other
  games), consider extracting a shared nav partial to avoid duplicating
  the `.parlor__home` pattern across game pages.