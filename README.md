# Grandmother Rowan's Grimoire

A cottage-witch grimoire that runs entirely in the browser — no server, no build step. Four rooms:

- **🌿 The Apothecary** — look up any herb, resin, root, or tarot card for its correspondences, lore, uses, and three workings.
- **🕯 The Ritual Loom** — choose an intention and the ingredients you own; it weaves rituals toward that goal, and keeps the ones worth keeping.
- **📖 The Study** — research a new ingredient or card; the book writes and keeps the page, deepening it on each re-research.
- **✦ The Star Almanac** — calculated natal charts (real astronomy) with a twelve-card zodiac spread, saved to your almanac.
- **🗝 The Chest** — carry the whole grimoire out as a single backup scroll, and unroll it again anywhere.

## Keeping and printing what you make

**Download any single thing.** Every entry, kept weaving, and star chart has a **⇩ PDF** button. It opens your browser's print dialog — choose **Save as PDF** as the destination for a clean, legible black-on-white copy, laid out for the page (no menus, no dark background). Individual entries can also be saved as **JSON** if you want the raw data.

**Back up everything.** In **🗝 The Chest**, one button writes the entire grimoire — every learned page, every kept ritual weaving, and every star chart — into a single dated `.json` scroll.

**Restore it anywhere.** In the same room, upload a backup scroll and the book carves it back into its individual pages, weavings, and charts. Two ways to unroll it:

- **Add to the book** — keeps what you already have and folds the new pages in (good for merging two grimoires).
- **Replace the book entirely** — starts fresh from the scroll alone.

> **Worth knowing:** the grimoire lives in your browser's own storage. Clearing site data, or using private browsing, will empty it. Carry a scroll out of the Chest now and then.

## Use it on GitHub Pages

1. Create a new repository and upload **`index.html`** and **`.nojekyll`** to the root (drag them into *Add file → Upload files*, or commit them).
2. In the repo, go to **Settings → Pages**.
3. Under *Build and deployment*, set **Source: Deploy from a branch**, pick your branch (usually `main`) and folder **`/ (root)`**, then **Save**.
4. Wait a minute, then open `https://<your-username>.github.io/<your-repo>/`. The grimoire will appear.

That's it — the page is static and self-contained. React loads from a public CDN (with an automatic fallback), and everything you save (learned pages, star charts) is stored in your own browser.

## Lighting the hearth (getting your own API key)

Browsing works with no setup. The features that *generate* text — Study research, ritual weaving, and the written parts of a star chart — call Anthropic's API. Each person supplies their **own** key, so their own (very small) usage is billed to their own account. Here is how to get one from scratch.

### Step 1 — Open the Anthropic Console

Go to **[console.anthropic.com](https://console.anthropic.com)** and sign in, or create an account if you don't have one.

> The **Console** is the developer side of Anthropic and is separate from the Claude chat app. Even if you already pay for Claude Pro, that subscription does **not** include API usage — the API is billed separately (see Step 2). You may need to set up a Console account even if you already have a Claude.ai login.

### Step 2 — Add a little billing credit

The API is prepaid by usage, so there must be some credit on file or your key won't work.

1. In the Console, open **Billing** (sometimes **Plans & Billing**).
2. Add a payment method and buy a small amount of credit. A few dollars lasts a very long time here — each research or chart is only a handful of short requests.
3. **Set a monthly spending limit** while you're there (even $5). Because the key will live in your browser, a low cap is your safety net.

### Step 3 — Create the key

1. Go to **Settings → API Keys** (direct link: **[console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys)**).
2. Click **Create Key**, give it a name you'll recognize like `grimoire`, and confirm.
3. The key is shown **only once** — a long string beginning with `sk-ant-`. Copy it right away and keep it somewhere safe. Once you close the dialog the full key is never shown again; if you lose it, just delete it and create a new one.

### Step 4 — Enter it in the grimoire

1. On your grimoire page, click **⚙ Set the hearth key** beneath the title.
2. Paste the key and save.

The key is stored **only in your browser** (localStorage) and is sent directly to Anthropic — never to GitHub, the page's author, or anyone else.

### Keeping the key safe

- **Never commit your key into the repository** or paste it into any file you upload. Only ever enter it through the ⚙ button on the live page.
- A key entered in a browser can be read by anyone who can use that browser. Enter it only on a device you control, and don't hand someone your live page with your key already set.
- The spending limit from Step 2 means that even in the worst case, your exposure is capped.
- The star-chart **math** runs entirely in your browser and needs no key at all — only the written interpretation, the Study, and the ritual weaving do.

> **A note on Claude Pro:** there is no way to link this tool to a Claude Pro subscription — Pro and the API are separate products, and Pro does not grant API credit. If you'd rather not have each user bring a key, that requires running your own small backend server that holds one key and meters usage; the file in this repo cannot do that on its own.

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
