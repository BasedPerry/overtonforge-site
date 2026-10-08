# overtonforge.app

The Overton Forge website: plain HTML and CSS, no build step, served by GitHub Pages at https://overtonforge.app.

This README is also the hand-off for anyone, human or AI, picking up work on the site. It records what the site is for, how it's built, the design rules, and what's still open. Keep it current when you change any of those.

## What the brand stands for

Overton Forge is Brandon Perry's one-person studio. The site should feel like **tech made for creators who take risks**: people who put their opinions out there to be judged (commentators, essayists, reaction channels, people who edit what they record). It is **not** aimed at the IG / TikTok dance-trend creator.

The feeling should come from the design, not the copy. Don't write slogans like "made for people like you". Show it through craft, restraint, and honesty.

The name is part of the idea: the Overton window is the range of opinions people accept. The site uses **framing** as a quiet visual motif (crop marks around the hero), never spelled out.

## Two identities

| | Overton Forge (studio) | Recaptr (product) |
|---|---|---|
| Feel | Small press / editorial workshop | Gaming and broadcast gear |
| Pages | `index.html` | `recaptr/` |
| Stylesheet | `styles.css` | `recaptr/recaptr.css` |
| Colors | Coal, ember red, amber, cream (from the logo) | Graphite, signal green, violet, restore blue (mirrors Recaptr's `Brand.swift`) |
| Type | Fraunces (headings), Inter (body), IBM Plex Mono (labels) | Space Grotesk (headings), Inter (body), Space Mono (labels) |
| Mode | Dark only | Dark only |
| Signature cues | Crop-mark frame, numbered sections ("01 — The work"), hairline rules, facts row under the hero, contact as a ruled list, outlined wordmark and colophon in the footer, faint paper grain | REC light, timecode, HUD corner brackets, audio meters, marker flags on a timeline with a moving playhead, chunky keycaps for shortcuts |

Recaptr sits inside the Overton Forge brand but has its own look. It's expressly for gamers, react channels, and creators who edit. Future products (ChainKeeper etc.) can get their own identity the same way.

## Files

- `index.html`: homepage (masthead, hero, project covers, contact list, colophon footer)
- `styles.css`: Overton Forge tokens and components. Colors are under `:root`; per-product card palettes are under **Brand covers**.
- `recaptr/index.html`: Recaptr landing page (hero with app-window mock, Record / Mark / Cut steps, feature grid, free / MIT / no-tracking stats, tip jar)
- `recaptr/support.html`, `recaptr/privacy.html`: **the App Store Support and Privacy URLs point here.** Don't rename or move them. Change their wording only on purpose.
- `recaptr/recaptr.css`: Recaptr identity, shared by the landing page (`body.landing`) and the doc pages (`body.doc`)
- `styles.recaptr-palette.css`: archived cool palette from an earlier version. Reference only, not loaded anywhere.
- `CNAME`: custom domain for GitHub Pages (`overtonforge.app`)

## Homepage: brand covers

Each project card on the homepage is a "cover" printed in its own brand's colors, chosen by `data-brand` on the `<article class="cover">`:

| Card | `data-brand` | Palette status |
|---|---|---|
| Recaptr (featured, full width) | `recaptr` | Real |
| ChainKeeper | `chainkeeper` | **Placeholder**: archive navy and brass, like a case file. Brandon has the real ChainKeeper branding and will share it. |
| The Back-Up Drive | `backupdrive` | **Placeholder**: tape-deck black, REC orange, caption yellow |
| Liquid Depths | `liquiddepths` | **Placeholder**: deep water and refracted cyan |

To roll out a brand, change only that brand's block in `styles.css` (`--b-bg`, `--b-ink`, `--b-text`, `--b-dim`, `--b-accent`, `--b-rule`, `--b-font`, `--b-name-weight`, `--b-name-tracking`). The card picks it up. If the brand needs a new font, add it to the Google Fonts link in `index.html`. Each cover also has a small decorative motif (`.motif-*` in `styles.css`) that can be redrawn to match the real brand.

## Design rules

- Keep the warm Overton Forge palette and fonts on the studio pages. Products get their own palette on their own cover and pages.
- No SaaS clichés: no glowing gradient blobs behind headlines, no pill-shaped everything, no stock illustrations. Corners are small (6px on Overton Forge, 12px on Recaptr).
- **Pricing promise (must stay consistent everywhere):** Recaptr 2 will add paid features. Recaptr 1.x and its source code stay free, forever. This is stated as a byline in the "Free" section of `recaptr/index.html`. Don't write anything that implies all future versions are free.
- Copy stays plain and factual. **Never invent product features or claims.** Recaptr copy comes only from what's on its landing, Support, and Privacy pages; ask Brandon before adding anything new.
- Every page must work at 320px wide with no sideways scrolling, and respect `prefers-reduced-motion` (all animation stops).
- No analytics, no trackers, no build step. The colophon says so; keep it true.

## Placeholders to swap

- `KOFI_URL`: tip jar row on the homepage and tip jar on the Recaptr page. Swap in the Ko-fi link when it exists (HTML comments mark the spot).
- `APP_STORE_URL`: Recaptr download button. On launch day, swap in the App Store link, and change the "Coming soon" status on the homepage cover.

## Open items

- ChainKeeper: apply the real branding to its cover when Brandon shares it; maybe give it its own page like Recaptr.
- Recaptr: the copy doesn't yet say anything specific to reaction videos. Add a section only once Brandon confirms which features matter for reactors (e.g. whether camera + game capture together is supported).
- No `og:image` social preview image yet on either identity.

## History

- **2026-10-01**: first version: plain homepage, plain Recaptr pages, custom domain.
- **2026-10-06**: full redesign on branch `claude/compassionate-galileo-61zxjc`:
  - Homepage rebuilt as an editorial small-press layout with per-brand covers.
  - Recaptr given its own gaming / broadcast identity (new `recaptr/recaptr.css`, old `recaptr/page.css` removed). Support and Privacy wording and URLs unchanged.
  - Not live until that branch is merged into `main`.
- **2026-10-08**: added the pricing byline on the Recaptr page (v2 paid features; 1.x and its source free forever).

## Preview locally

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. Check at phone width (390px and 320px) as well as desktop.

## Deploy

Push or merge to `main`. GitHub Pages rebuilds in about a minute.
