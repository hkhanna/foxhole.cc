# foxhole.cc

Marketing site for **Foxhole Partners**. Plain HTML and CSS, no build step, hosted on GitHub Pages at [foxhole.cc](https://foxhole.cc).

## Structure

The site is a single page: `index.html` + `style.css`. Sections are the hero, the What block (statement + Strategy / Operations / Communications accordion, `#what`), and Who (`#who`). The only JS is the accordion toggle, inline at the bottom of `index.html`.

`404.html` is served by GitHub Pages for unknown routes. `CNAME` holds the custom domain.

## Editing notes

- **Design reference**: the current design comes from `foxhole-homepage-preview_1.html`. Palette is navy `#2b3a45`, cream `#ece5d8`, rust `#c47a5d`, defined as CSS variables at the top of `style.css`. Type is Source Serif 4 throughout. `design/` holds the handoff docs for the *previous* multi-page design (Newsreader / Schibsted Grotesk) and is historical.
- **Portrait**: `images/lisa.jpg`, cropped to 3:4 in CSS.
- **Scheduler**: the "Find a time to talk" CTA is `mailto:lisa@foxhole.cc`.
- **Social card**: Open Graph / Twitter tags point at `images/og-card.png` (2400x1260, rendered at 2x). To change it, edit `design/og-card.html` and re-screenshot: `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --screenshot=images/og-card.png --window-size=1200,630 --hide-scrollbars --force-device-scale-factor=2 "file://$PWD/design/og-card.html"`

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. (Links are root-relative, so open via a local server rather than `file://`.)

## Deploy

Push to `main`; GitHub Pages serves the repo root. In the repo settings, Pages should be set to deploy from branch `main` / `/ (root)` with custom domain `foxhole.cc` and "Enforce HTTPS" on.
