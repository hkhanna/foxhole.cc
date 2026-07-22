# foxhole.cc

Marketing site for **Foxhole Partners**. Plain HTML and CSS, no build step, hosted on GitHub Pages at [foxhole.cc](https://foxhole.cc).

## Structure

| Route | File |
|---|---|
| `/` | `index.html` |
| `/what/` | `what/index.html` |
| `/who/` | `who/index.html` |
| `/talk/` | `talk/index.html` |

All pages share `style.css`. `404.html` is served by GitHub Pages for unknown routes. `CNAME` holds the custom domain.

## Editing notes

- **Design reference**: the original handoff docs live in `design/` (`HANDOFF.md` and the prototype `Foxhole Partners.dc.html`). The palette is exactly three notes — cream, slate blue, rust — defined as CSS variables at the top of `style.css`. Never introduce a fourth color.
- **Portrait**: the Who page uses a placeholder block. When the client supplies the photo, drop it in (e.g. `images/lisa.jpg`) and swap the placeholder `div` for the commented-out `<img>` right above it in `who/index.html`.
- **Scheduler**: every "Find a time to talk" CTA is `mailto:lisa@foxhole.cc`. On the Talk page the CTA lives in the `div.talk-cta` block, built to be replaced with an inline Calendly/Cal.com embed later.
- **Social card**: every page's Open Graph / Twitter tags point at `images/og-card.png` (2400x1260, rendered at 2x). To change it, edit `design/og-card.html` and re-screenshot: `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --screenshot=images/og-card.png --window-size=1200,630 --hide-scrollbars --force-device-scale-factor=2 "file://$PWD/design/og-card.html"`

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. (Links are root-relative, so open via a local server rather than `file://`.)

## Deploy

Push to `main`; GitHub Pages serves the repo root. In the repo settings, Pages should be set to deploy from branch `main` / `/ (root)` with custom domain `foxhole.cc` and "Enforce HTTPS" on.
