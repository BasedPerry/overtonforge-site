# overtonforge.app

The Overton Forge website: plain HTML and CSS, no build step, served by GitHub Pages at https://overtonforge.app.

This README is also the hand-off for anyone, human or AI, picking up work on the site. It records what the site is for, how it's built, the design rules, and what's still open. Keep it current when you change any of those.

**Also read `SITE-STANDARDS.md`:** the checklist (disclaimers, footnotes, self-hosted fonts, share images, launch checks) that applies to every Overton Forge site, including FEFW.

## What the brand stands for

Overton Forge is Brandon Perry's one-person studio. The site should feel like **tech made for creators who take risks**: people who put their opinions out there to be judged (commentators, essayists, reaction channels, people who edit what they record). It is **not** aimed at the IG / TikTok dance-trend creator.

The feeling should come from the design, not the copy. Don't write slogans like "made for people like you". Show it through craft, restraint, and honesty.

The name is part of the idea: the Overton window is the range of opinions people accept. The site uses **framing** as its one visual idea (crop marks around the hero, which open out to the corners on load, and the favicon), never spelled out.

## Two identities

| | Overton Forge (studio) | Recaptr (product) |
|---|---|---|
| Feel | Small press / editorial workshop | Gaming and broadcast gear |
| Pages | `index.html` | `recaptr/` |
| Stylesheet | `styles.css` | `recaptr/recaptr.css` |
| Colors | Coal, ember red, amber, cream (from the logo) | Graphite, signal green, violet, restore blue (mirrors Recaptr's `Brand.swift`) |
| Type | Fraunces (headings), Inter (body). No monospace | Space Grotesk (headings), Inter (body), Space Mono only inside keycaps, code and file names. Wordmark: lowercase `re:captr` in Unbounded Bold, the colon's top dot is the red REC light (`.rc-wordmark` in `recaptr/recaptr.css` and `styles.css`). Running text still says "Recaptr" |
| Mode | Dark only | Dark only |
| Signature cues | Crop-mark frame, the real Recaptr window on its cover, contact as a ruled list, outlined wordmark and colophon in a footer set on a lighter coal field, faint paper grain | REC light in the wordmark, the real app window and clip, "How it works" as one recording track with marker flags and a moving playhead, chunky keycaps for shortcuts |

Recaptr sits inside the Overton Forge brand but has its own look. It's expressly for gamers, react channels, and creators who edit. Future products (ChainKeeper etc.) can get their own identity the same way.

## Files

- `index.html`: homepage (masthead, hero, project covers, next-up list, contact list, colophon footer)
- `404.html`: shown by GitHub Pages for any missing path (including under `/fefw/`), so its links are root-relative
- `favicon.svg`: four ember crop marks on coal. Recaptr pages use `recaptr/img/recaptr-icon.png`
- `img/`: studio-level images (`chainkeeper-icon.png`)
- `styles.css`: Overton Forge tokens and components. Colors are under `:root`; per-product card palettes are under **Brand covers**.
- `recaptr/index.html`: Recaptr landing page (hero with the real app window and clip, Record / Mark / Cut on one marker track, two-column feature list, free / MIT / no-tracking stats, tip jar)
- `recaptr/support.html`, `recaptr/privacy.html`: **the App Store Support and Privacy URLs point here.** Don't rename or move them. Change their wording only on purpose.
- `recaptr/recaptr.css`: Recaptr identity, shared by the landing page (`body.landing`) and the doc pages (`body.doc`)
- `styles.recaptr-palette.css`: archived cool palette from an earlier version. Reference only, not loaded anywhere.
- `fonts/`: self-hosted fonts (`fonts.css` plus `.woff2` files, SIL OFL licenses in `LICENSE.txt`). Every page links `fonts/fonts.css`; nothing loads from Google.
- `og/`: source HTML for the share images. Render each at 1200×630 to `og-image.png` (homepage) and `recaptr/og-image.png`.
- `SITE-STANDARDS.md`: standard practice for every site (see above).
- `CLAUDE.md`: short pointer file for Claude sessions.
- `CNAME`: custom domain for GitHub Pages (`overtonforge.app`)

## Homepage: brand covers

Each project card on the homepage is a "cover" printed in its own brand's colors, chosen by `data-brand` on the `<article class="cover">`:

| Card | `data-brand` | Palette status |
|---|---|---|
| Recaptr (featured, full width) | `recaptr` | Real. Plate is the real window (`recaptr/img/recaptr-recording.jpg`) |
| ChainKeeper | `chainkeeper` | Real (2026-10-27): colours from the app's `Theme.swift` (slate, amber `#E0B062`), plate is the app icon with its amber thread run down the card (`img/chainkeeper-icon.png`, from the app's 1024 icon) |

Projects that don't have a brand yet (The Back-Up Drive, Liquid Depths) sit in a plain **Next up** list beside ChainKeeper, not as covers. Give one a cover when its real identity exists.

To add or change a brand, edit only that brand's block in `styles.css` (`--b-bg`, `--b-ink`, `--b-text`, `--b-dim`, `--b-accent`, `--b-font`, `--b-name-weight`, `--b-name-tracking`). If the brand needs a new font, self-host it in `fonts/` (never Google Fonts).

## Design rules

- Keep the warm Overton Forge palette and fonts on the studio pages. Products get their own palette on their own cover and pages.
- No SaaS clichés: no glowing gradient blobs behind headlines, no pill-shaped everything, no stock illustrations. Corners are small (6px on Overton Forge, 12px on Recaptr).
- No generated-page tells (from the 2026-10-27 design-skill audit): no small uppercase or monospace labels above headings, no "01 / 02" numbering unless it's a real sequence, no italic or coloured accent word in a headline, no glass or blurred bars, no glows, no pulsing dots, no single-side borders, no rows of identical cards. Headlines stay at two lines or fewer at every width. Separate surfaces by a step in tone, not lines.
- Motion: one curve, `cubic-bezier(0.22, 1, 0.36, 1)` (`--ease`), 300ms for colour and 500ms for movement. Scroll reveals are CSS-only (`animation-timeline: view()` inside `@supports`), so the site still ships no JavaScript. Everything stops under `prefers-reduced-motion`.
- **Pricing promise (must stay consistent everywhere):** Recaptr 2 will add paid features as a one-time purchase, not a subscription. Recaptr 1.x and its source code stay free, forever. This is stated as a byline in the "Free" section of `recaptr/index.html`, and as footnote ¹ (Apple-style superscript linking to a note above the footer) on every "free" claim: the hero line, the Free section and "$0" on the Recaptr page, and "Free" on the homepage Recaptr card. Any new "free" claim gets the same `<sup class="fn">` marker. Don't write anything that implies all future versions are free.
- Copy stays plain and factual. **Never invent product features or claims.** Recaptr copy comes only from what's on its landing, Support, and Privacy pages; ask Brandon before adding anything new.
- Every page must work at 320px wide with no sideways scrolling, and respect `prefers-reduced-motion` (all animation stops).
- No analytics, no trackers, no third-party requests (fonts are self-hosted), no build step. The colophon says so; keep it true.
- **Disclaimers in place:** trademark / non-affiliation line in every footer; footnotes ¹ (pricing), ² (4K60 depends on hardware), ³ (Apple Intelligence availability) on the Recaptr page; "tips are gifts" on both tip jars; "What you record" rights note on the Support page. See `SITE-STANDARDS.md` before adding claims.

## Placeholders to swap

- `KOFI_URL`: done 2026-10-11. Both tip jars link to https://ko-fi.com/overtonforge.
- `APP_STORE_URL`: done 2026-10-18. The Recaptr download button and the homepage cover link to https://apps.apple.com/app/id6817601217; the cover status reads "Out now".

## Open items

- ChainKeeper: maybe give it its own page like Recaptr once it's on the App Store. Swap the cover plate for a real screenshot then.
- Recaptr: the copy doesn't yet say anything specific to reaction videos. Add a section only once Brandon confirms which features matter for reactors (e.g. whether camera + game capture together is supported).
- FEFW: apply `SITE-STANDARDS.md` in the `fefw-growth-calc` repo (trademark line, data-accuracy footnote, share image). Checklist is in that doc.

## History

- **2026-10-01**: first version: plain homepage, plain Recaptr pages, custom domain.
- **2026-10-06**: full redesign on branch `claude/compassionate-galileo-61zxjc`:
  - Homepage rebuilt as an editorial small-press layout with per-brand covers.
  - Recaptr given its own gaming / broadcast identity (new `recaptr/recaptr.css`, old `recaptr/page.css` removed). Support and Privacy wording and URLs unchanged.
  - Not live until that branch is merged into `main`.
- **2026-10-08**: added the pricing byline on the Recaptr page (v2 paid features; 1.x and its source free forever), plus footnote ¹ on every "free" claim on both pages.
- **2026-10-08**: disclaimers (trademark lines, footnotes ² and ³, tip and recording-rights notes), self-hosted fonts, share images for both identities, and `SITE-STANDARDS.md` as the standard for all sites.
- **2026-10-27**: design-skill refresh (audit with redesign-existing-projects, taste-skill and frontend-design; Brandon approved the list). Homepage: monospace labels, numbering, stat row and italic accent line gone; real Recaptr window on its cover; ChainKeeper in its real colours; Back-Up Drive and Liquid Depths moved to a Next up list; favicon and a 404 page. Recaptr: glow blobs and pill chips gone, the window lands in the first screen, How it works is one track with marker flags, features are a plain two-column list. Support and Privacy pages unchanged.

## Preview locally

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. Check at phone width (390px and 320px) as well as desktop.

## Deploy

Push or merge to `main`. GitHub Pages rebuilds in about a minute.
