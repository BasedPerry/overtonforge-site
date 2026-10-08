# Overton Forge site standards

Standard practice for **every** site or web page Overton Forge ships: this site, product pages like Recaptr, and side projects like the FEFW calculator. Run through this list before anything goes live, and again whenever a page's claims change.

These are common practice, not legal advice.

## 1. Disclaimers

### Trademarks and non-affiliation (every site)

Put one small line in the footer of every page that names someone else's product or brand. List the marks the page actually uses, say who owns them, and say we're not affiliated.

- Apple products (Mac, macOS, iPhone, iPad, Final Cut Pro, QuickTime, App Store, Apple Intelligence, Liquid Glass, …):
  > Apple, Mac, … are trademarks of Apple Inc., registered in the U.S. and other countries. [Product] is not affiliated with or endorsed by Apple.
- Other companies get the same treatment (e.g. "YouTube is a trademark of Google LLC.").
- End with "Other names belong to their owners." to cover passing mentions (OBS, Elgato, …).
- **Fan projects** (games, franchises) also need: "Unofficial fan tool, not affiliated with [publisher/developer]", a trademark line for the franchise, and credit and © for any official artwork used.

### Footnotes for conditional claims (Apple style)

Any claim that has a catch gets a superscript number linking to a numbered note just above the footer:

```html
Free<sup class="fn"><a href="#fn-1" aria-label="Footnote 1">1</a></sup>
...
<aside class="footnotes" aria-label="Footnotes"><ol><li id="fn-1">…</li></ol></aside>
```

- Number footnotes in the order they first appear on the page. Reuse the same number when the same claim repeats.
- Needs a footnote:
  - **Price:** any "free" while a paid version is planned.
  - **Hardware limits:** "up to 4K60" and similar.
  - **Feature availability:** features that depend on OS, region, language, or hardware (e.g. Apple Intelligence).
  - **Data accuracy:** numbers that are community-sourced or may change with game or app updates.
- `.fn` and `.footnotes` styles exist in both `styles.css` and `recaptr/recaptr.css`; copy them for new sites.

### Pricing promises

State pricing plans plainly and keep them identical everywhere: page copy, footnotes, README, App Store text.

Current promise: **Recaptr 2 will add paid features as a one-time purchase, not a subscription. Recaptr 1.x and its source code stay free, forever.**

### Tips and donations

Tip jars must say tips are gifts and don't unlock anything.

### User content

Tools that record, capture, or publish need a line (on the Support page at minimum): "You're responsible for having the rights to what you record and publish."

### Privacy

Every app needs a privacy policy page with a "Last updated" date. Never claim "no tracking" or "no analytics" unless it's true for the app **and** the website.

## 2. No third-party requests

- **Self-host fonts.** Never load Google Fonts or other font CDNs; they hand visitors' IP addresses to a third party. Put the `.woff2` files and their licenses in a `fonts/` folder (Fontsource on npm is a good source).
- No analytics, trackers, embeds, or CDN scripts unless the page discloses them.
- Keep font and asset licenses in the repo (e.g. `fonts/LICENSE.txt`).

## 3. Share previews

Every landing page needs a share image so links look right on X, Discord, iMessage, etc.:

- `og:title`, `og:description`, `og:url`, `og:image` (absolute URL), `og:image:width`/`height` (1200×630), `og:image:alt`
- `twitter:card` = `summary_large_image`, plus `twitter:title`, `twitter:description`, `twitter:image`
- The image is made in that brand's own style. Keep the source HTML so it can be regenerated (this repo: `og/*.html`, rendered to `og-image.png`).

## 4. Look, feel, and accessibility

- Each product gets its own identity; the studio identity stays warm and editorial (see README).
- No sideways scrolling at 320px wide; check 320, 390, tablet, and desktop.
- Respect `prefers-reduced-motion`: all animation stops.
- Visible focus outlines, a skip link on long pages, and readable contrast.
- Never invent features or claims in copy. Ask first.

## 5. Before going live

1. Click every footnote marker; each one jumps to its note.
2. Check that no request goes to a third party (browser dev tools → Network).
3. Paste the URL into a share-preview checker, or into iMessage or Discord, and confirm the image shows.
4. Check the page at phone width with reduced motion turned on.

## Applying this to existing sites

| Site | Where to change it | Status |
|---|---|---|
| overtonforge.app (home) | this repo: `index.html`, `styles.css` | Done (2026-10-08) |
| Recaptr pages | this repo: `recaptr/` | Done (2026-10-08) |
| FEFW Growth Calc (`/fefw/`) | **its source repo, `fefw-growth-calc`**, not `fefw/` here. `fefw/` is a compiled Next.js build that gets replaced on every update, so edits here would be lost. | To do (see below) |

### FEFW checklist (as of 2026-10-08)

Already done:
- Footer says "Unofficial fan tool, not affiliated with Nintendo or Intelligent Systems."
- Footer credits artwork (© Nintendo / Intelligent Systems) and data sources.
- Fonts are self-hosted (Next.js), and no analytics were found.

Still to add:
- **Trademark line:** e.g. "Fire Emblem and Nintendo Switch are trademarks of Nintendo." Name exactly the marks the site uses.
- **Data-accuracy footnote:** on stats and growth numbers, e.g. "Community-sourced data; may be incomplete or change with game updates."
- **Share preview:** no `og:*` or `twitter:*` tags and no share image yet. Make one in FEFW's own style.
- **Final checks:** run the "Before going live" steps after the next build.
