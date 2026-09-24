# Industry Reports — how it works

The **Industry Reports** section (`#reports` in `index.html`) is driven by the `REPORTS` list near the bottom of `index.html`.

## Add or edit a report
1. Put the free preview PDF in `reports/previews/` (e.g. `reports/previews/hyperscaler-selection-preview.pdf`).
2. In Stripe, create a product for the full report and a Payment Link for it (Payment Links → +New), and copy the link.
3. Add or edit an entry in `REPORTS`: `id`, EN/FR `topic` / `title` / `summary` / `edition`, `highlights` (optional bullet points), `pages`, `cover` (image in `reports/covers/`), `price` (leave `null` to hide the price), `currency`, `previewUrl`, `checkoutUrl`.

With a single report the section shows one wide featured card; with two or more it switches to a grid automatically.

Never commit a full report to this repo: it's public, so anything in it can be downloaded.

## What happens on the site
- **Free Preview** opens a form (name, email, optional organisation, optional marketing opt-in). Each submission is emailed to you via Web3Forms, then the preview downloads. The visitor's details are remembered in their browser for next time.
- **Buy Full Report** opens the Stripe Payment Link in a new tab, tagged with the report ID (`client_reference_id`) and pre-filled with the visitor's email if they already requested a preview. After payment, the full PDF is emailed to the buyer manually (stamped with their organisation name).
- Any `checkoutUrl` still containing `REPLACE` shows a "checkout being set up, please get in touch" note instead of opening checkout.
