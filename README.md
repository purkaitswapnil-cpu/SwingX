# SwingX: The Daily 1% Club

A one-page tool for SwingX's daily trading journal cards, with two journals on the same page:

- **Stocks:** stock, long or short, entry, exit and quantity.
- **Options:** underlying, strike, CE or PE, buy or sell, expiry, entry and exit premium, lots and lot size.

P&L, P&L %, win rate, average return per trade and total P&L are calculated, and the card downloads as a PNG 1080, 2160 or 3240 px wide. Link straight to a journal with `#stocks` or `#options` at the end of the address.

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

- Stocks: P&L per trade = (exit − entry) × qty. Short trades flip the sign. P&L % = price move ÷ entry.
- Options: P&L per trade = (exit − entry premium) × lots × lot size. Sold options flip the sign, and an exit of 0 counts (expired worthless). P&L % is the move on the premium. Lot sizes are typed in, not built in, because exchanges revise them; the page remembers the last lot size used for each underlying.
- Total capital deployed defaults to the sum of entry × qty (premium × qty for options). You can type your own amount instead, such as the margin used for sold options, and total P&L % uses it.
- Win rate counts trades with P&L above zero. Average return per trade is the mean of the trades' P&L %.
- Only trades with entry, exit and qty filled in go on the card.
- Each journal keeps its own trades, notes, subtitle and capital setting. "New day" clears both journals' trades and notes.
- Entries are saved in the visitor's own browser (localStorage). Nothing is sent to a server.
- Downloads: computers get a PNG download; phones get the share sheet (Save Image), or a download if sharing isn't available.

## Updating the site

Edit `index.html`, commit and push to `gh-pages`. GitHub Pages redeploys in about a minute.

The same page also runs as a private claude.ai artifact (https://claude.ai/artifact/TP9LLBQWsUdQ4cWsrexo7Z). That copy saves images through claude.ai's download prompt; its source is `index.html` without the `<!doctype>`, `<head>` and `<body>` wrapper.
