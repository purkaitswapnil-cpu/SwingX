# SwingX: The Daily 1% Club

A one-page tool for SwingX's daily trading journal card. Enter each trade's stock, direction (long or short), entry, exit and quantity. P&L, P&L %, win rate, average return per trade and total P&L are calculated, and the card downloads as a PNG 1080, 2160 or 3240 px wide.

**Live site:** https://purkaitswapnil-cpu.github.io/SwingX/ (GitHub Pages, served from the `gh-pages` branch)

## What's here

```
index.html      the whole app: page, styles and the canvas that draws the card
gateway.webp    Gateway of India sketch in the card header
howrah.webp     Howrah Bridge sketch in the card header
.nojekyll       tells GitHub Pages to serve the files as they are
```

There is no build step and there are no dependencies. Fonts (Poppins and Kalam) load from Google Fonts.

## How the numbers work

- P&L per trade = (exit − entry) × qty. Short trades flip the sign. P&L % = price move ÷ entry.
- Total capital deployed defaults to the sum of entry × qty. You can type your own amount instead, and total P&L % uses it.
- Win rate counts trades with P&L above zero. Average return per trade is the mean of the trades' P&L %.
- Only trades with entry, exit and qty filled in go on the card.
- Entries are saved in the visitor's own browser (localStorage). Nothing is sent to a server.
- Downloads: computers get a PNG download; phones get the share sheet (Save Image), or a download if sharing isn't available.

## Updating the site

Edit `index.html`, commit and push to `gh-pages`. GitHub Pages redeploys in about a minute.

The same page also runs as a private claude.ai artifact (https://claude.ai/artifact/TP9LLBQWsUdQ4cWsrexo7Z). That copy saves images through claude.ai's download prompt; its source is `index.html` without the `<!doctype>`, `<head>` and `<body>` wrapper.
