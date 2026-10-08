# Quantman Strategy Portfolio Analyser

Browser-based portfolio analyser for trading strategies. Upload your strategy CSVs to compare performance, drawdowns, correlations and margin needs, and find the combinations that diversify risk. Runs entirely client-side.

## Features

- **Performance** – per-strategy and combined portfolio summary
- **Worst Days** – the biggest single-day losses
- **Drawdowns** – largest drawdowns and how long each took to recover
- **Correlation Matrix** – monthly P&L correlation heatmap across all loaded strategies
- **Selected Strategy Matrix** – full correlation table for your shortlist
- **Least Correlated Pairs** – the best pairs to combine, sorted from lowest to highest correlation
- **Shared Trade Days** – calendar days on which two strategies both traded
- **Margin Analysis** – peak margin (premium tied up at one time) for the shortlisted strategies

## Usage

1. Open `index.html` in any modern browser. No build step, server or dependencies needed.
2. Click **Upload** or drag and drop one or more `.csv` files anywhere on the page.
3. Shortlist the strategies you want to compare using the chips.
4. Explore the tabs.

## CSV format

The first row is treated as a header. Each following row is one trade, and these columns (0-indexed) are read:

| Column | Meaning |
|--------|---------|
| 2 | Quantity (lot size) |
| 4 | Entry price |
| 5 | Entry time |
| 8 | Exit time |
| 9 | Profit / loss |

Rows with fewer than 10 columns or non-numeric price/P&L values are skipped.

Strategy names are taken from the file name. A name containing `-NF <name>` uses the part after it, and otherwise a leading number prefix is removed.

## Notes

- Margin is calculated as `entry price × quantity`, which suits **option buying**. It is not exchange margin for option selling or futures.
- Correlation is Pearson correlation on **monthly P&L**.
- Currency is displayed in ₹.
- All processing happens locally in your browser, and no data is uploaded anywhere.

## Hosting

Since it is a single static file, it works on GitHub Pages: enable Pages for the repo and point it to the root branch.
