# overtonforge.app

The Overton Forge website: plain HTML and CSS, no build step, served by GitHub Pages at https://overtonforge.app.

## Files

- `index.html`: homepage (masthead, hero, project covers, contact ledger, colophon footer)
- `styles.css`: design tokens and components; Overton Forge colors live under `:root`
- `styles.recaptr-palette.css`: archived cool palette (reference only, not loaded)
- `recaptr/`: Recaptr landing, support, and privacy pages (the App Store Support and Privacy URLs point here)
- `CNAME`: custom domain for GitHub Pages

## Brand covers

Each project card is a "cover" in its own brand's colors, set by `data-brand` on the card. The palettes are in `styles.css` under **Brand covers**. Recaptr's is real; ChainKeeper, The Back-Up Drive, and Liquid Depths are placeholders. When one of those brands rolls out, change the values in its block (`--b-bg`, `--b-ink`, `--b-accent`, `--b-font`, …) and the card follows.

## Placeholders

- `KOFI_URL`: tip jar card on the homepage and the Recaptr page. Swap in the Ko-fi link when it exists.
- `APP_STORE_URL`: Recaptr download button. Swap in the App Store link on launch day, and change the card's "Coming Soon" chip.

## Preview locally

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

Push to `main`. Pages rebuilds in about a minute.
