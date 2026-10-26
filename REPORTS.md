# Industry Reports — how it works

The **Industry Reports** section (`#reports` in `index.html`) is driven by the `REPORTS` list near the bottom of `index.html`.

## Add or edit a report
1. Put the free preview PDF in `reports/previews/` (e.g. `reports/previews/hyperscaler-selection-preview.pdf`).
2. In Stripe, create a product for the full report and a Payment Link for it (Payment Links → +New), and copy the link.
3. Add or edit an entry in `REPORTS`: `id`, EN/FR `topic` / `title` / `summary` / `edition`, `highlights` (optional bullet points), `pages`, `cover` (image in `reports/covers/`), `price` (leave `null` to hide the price), `currency`, `previewUrl`, `checkoutUrl`.

Reports display as compact tiles, two per row on desktop and one per row on tablets and phones: cover thumbnail and title, a three-line summary, a "See what's inside" button that expands the `highlights`, and a buy bar with the price, Free Preview and Buy Full Report. The licence wording shows in the small print under each tile.

Never commit a full report to this repo: it's public, so anything in it can be downloaded.

## Free whitepapers
A whitepaper is an entry in `REPORTS` with `free: true`, `price: null` and `checkoutUrl: null`. Its `previewUrl` points to the **full** whitepaper PDF in `reports/whitepapers/` (free, so committing it is fine).

- The tile shows a single **Download Free Whitepaper** button instead of Free Preview / Buy.
- The same email-capture form opens, worded for a whitepaper; the Web3Forms email subject starts with "Whitepaper download".
- Deep link for social posts: `https://bsquared-advisory.com/#whitepaper-5g6g` scrolls to Industry Reports and opens the download form. Add new links in `DEEP_LINKS` in the script.

## What happens on the site
- **Free Preview** opens a form (name, email, optional organisation, optional marketing opt-in). Each submission is emailed to you via Web3Forms, then the preview downloads. The visitor's details are remembered in their browser for next time.
- **Buy Full Report** opens the Stripe Payment Link in a new tab, tagged with the report ID (`client_reference_id`) and pre-filled with the visitor's email if they already requested a preview. After payment, the full PDF is emailed to the buyer manually (stamped with their organisation name).
- Any `checkoutUrl` still containing `REPLACE` shows a "checkout being set up, please get in touch" note instead of opening checkout.

## Reports row layout

The reports section is a single horizontal row (CSS scroll-snap), so the page never grows taller as reports are added.

- Desktop shows about two tiles with a peek of the next; tablet and phone show one tile with a peek. Visitors swipe or use the ‹ › arrows (arrows hidden on phones).
- The "1–2 of N" counter and the arrows update automatically from the `REPORTS` array; nothing to change when adding a report.
- Order in `REPORTS` = order in the row, so put the newest or most important item first.
- Deep links (e.g. `#whitepaper-5g6g`) slide the row to that tile before opening its modal.
