# Grandmother Rowan's Grimoire

A cottage-witch grimoire that runs entirely in the browser — no server, no build step. Four rooms:

- **🌿 The Apothecary** — look up any herb, resin, root, or tarot card for its correspondences, lore, uses, and three workings.
- **🕯 The Ritual Loom** — choose an intention and the ingredients you own; it weaves rituals toward that goal.
- **📖 The Study** — research a new ingredient or card; the book writes and keeps the page, deepening it on each re-research.
- **✦ The Star Almanac** — calculated natal charts (real astronomy) with a twelve-card zodiac spread, saved to your almanac.

## Use it on GitHub Pages

1. Create a new repository and upload **`index.html`** and **`.nojekyll`** to the root (drag them into *Add file → Upload files*, or commit them).
2. In the repo, go to **Settings → Pages**.
3. Under *Build and deployment*, set **Source: Deploy from a branch**, pick your branch (usually `main`) and folder **`/ (root)`**, then **Save**.
4. Wait a minute, then open `https://<your-username>.github.io/<your-repo>/`. The grimoire will appear.

That's it — the page is static and self-contained. React loads from a public CDN (with an automatic fallback), and everything you save (learned pages, star charts) is stored in your own browser.

## Lighting the hearth (the API key)

Browsing works with no setup. The features that *generate* text — Study research, ritual weaving, and the written parts of a star chart — call Anthropic's API, which needs a key when the page is self-hosted.

1. Get a key from **console.anthropic.com**.
2. In the grimoire, click **⚙ Set the hearth key** under the title, paste the key, and save.

The key is stored **only in your browser** (localStorage) and is sent directly to Anthropic, never to GitHub or anyone else.

> **Note:** a key entered in a browser is visible to anyone who can use that browser or read that page's storage. Use this on a personal or trusted deployment. Don't commit your key into the repository, and don't hand the live page to the public with your key already set. The star-chart *math* runs locally and needs no key; only the written interpretation does.

## Running it locally

Because browsers block some features on `file://`, open it through a tiny local server rather than double-clicking:

```bash
# from the folder containing index.html
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Working fully offline / behind a strict firewall

The page pulls React and the fonts from public CDNs. If your host blocks them:

- Download `react.production.min.js` and `react-dom.production.min.js` (React 18), place them beside `index.html`, and change the two CDN URLs near the top of the loader script to point at the local files.
- The fonts will simply fall back to a serif system font if Google Fonts is unreachable — nothing breaks.

## Sources & disclaimer

Lore is cross-referenced from established works on herbalism, folklore, tarot (Western and non-Western), and astrology, all cited within the app. Everything is offered as symbolic tradition and reflection — not medical, legal, financial, or predictive advice. Mind your flames.
