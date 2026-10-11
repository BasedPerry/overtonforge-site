# overtonforge.app

The Overton Forge website: plain HTML and CSS, no build step, served by GitHub Pages at https://overtonforge.app.

## Files

- `index.html`: homepage (hero, project cards, contact)
- `styles.css`: design tokens and components; colors live under `:root`
- `styles.recaptr-palette.css`: Recaptr card accent
- `recaptr/`: Recaptr landing, support, and privacy pages (the App Store Support and Privacy URLs point here)
- `CNAME`: custom domain for GitHub Pages

## Placeholders

- `KOFI_URL`: done 2026-10-11. The tip jar card on the homepage and the button on the Recaptr page link to https://ko-fi.com/overtonforge.
- `APP_STORE_URL`: Recaptr download button. Swap in the App Store link on launch day, and change the card's "Coming Soon" chip.

## Preview locally

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

Push to `main`. Pages rebuilds in about a minute.
