# SwingX: The Daily 1% Club

A one-page tool for SwingX's daily trading journal cards, with two journals on the same page:

- **Stocks:** stock, long or short, entry, exit and quantity.
- **Options:** underlying, strike, CE or PE, buy or sell, expiry, entry and exit premium, lots and lot size.

P&L, P&L %, win rate, average return per trade and total P&L are calculated, and the card downloads as a PNG. The card is always 3:4 portrait (1080 × 1440, 2160 × 2880 or 3240 × 4320) however many trades it holds: with few trades the notes boxes get more room, with many the table rows get slimmer. Link straight to a journal with `#stocks` or `#options` at the end of the address.

**Live site:** https://purkaitswapnil-cpu.github.io/SwingX/ (GitHub Pages, served from the `gh-pages` branch)

## What's here

```
index.html                    the whole app: page, styles and the canvas that draws the card
brand/swingx-logo.svg         logo for light backgrounds
brand/swingx-logo-on-dark.svg logo on the ink background (the main version)
brand/swingx-icon.svg         app icon, profile picture and favicon
.nojekyll                     tells GitHub Pages to serve the files as they are
```

There is no build step and there are no dependencies. The font (Manrope) loads from Google Fonts.

## Brand

- Colours: ink `#0F1B2D` (card background runs `#14243D` to `#091322`), electric blue `#2F6BFF`, light blue `#7AA0FF` for the x and labels on dark, green `#2FD27D` for gains, red `#FF6B6B` for losses.
- Type: Manrope ExtraBold for the wordmark and numbers, SemiBold for text.
- Logo: a blue rounded tile with one price swing (up, a pullback, up again) ending in a live dot, then the lowercase wordmark `swingx` with a light-blue x. The logo files in `brand/` have their lettering converted to outlines.

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
