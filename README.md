# Paper Cost pay page

The UPI payment page that a Paper Cost bill's "Click to Pay" link opens, for the shop's customers.
Served by GitHub Pages at https://himansh04.github.io/pay/.

**Status:** live · **Platforms:** web (GitHub Pages) · **Owner:** Himanshu

## What it does

- Reads the payment from the part of the link after `#`:
  `#pa=<UPI ID>&pn=<shop>&am=<amount>&tn=<note>&k=<p|b>`, and optionally the bill (`b`).
- Shows the bill (items, totals, received, balance) above the payment.
- For a personal UPI ID (`k=p`): a QR with the amount in it, handed to GPay / PhonePe through the
  phone's share sheet. Since 1 April 2024 (NPCI OC-76A) payment apps block a person-to-person
  payment started from a link; a shared or gallery QR still works up to Rs 2,000. Over that, or if
  sharing is not offered, the customer copies the UPI ID.
- For a business UPI ID (`k=b`): real Click to Pay buttons.
- Keeps nothing: no server, no storage, no tracking, and it loads no code from anyone else. The
  part after `#` is never sent to a server.

## Who it is for

Customers of shops that use Paper Cost (IN SYNC's print / stationery shop costing and billing app).

## Tech

One self-contained `index.html` (HTML, CSS, JavaScript, with a bundled QR code generator).
`.nojekyll` makes GitHub Pages serve it as is. `noindex`, so search engines skip it.

## Run it locally

Open `index.html` in a browser with a payment after `#`, for example
`index.html#pa=<UPI ID>&pn=<shop>&am=100&tn=<note>&k=p`.

## Build and release

Do not edit `index.html` here by hand. Its source is `pay-page/page.html` in the Paper Cost repo,
built by `scripts/make-pay-page.js` there; the built page is committed here. GitHub Pages serves
the `main` branch root, so a push to `main` publishes it. Publish only when Himanshu says so.

## Where things live

| What | Where |
|---|---|
| Secrets / keystore | none (the page holds no keys) |
| Backend | none |
| Source | Paper Cost repo: `pay-page/page.html`, `scripts/make-pay-page.js` |
| Live URL | https://himansh04.github.io/pay/ |

## More

- Knowledge base page: `insync-knowledge/products/pay.md`
- Repo standard: `insync-knowledge/engineering/repo-standard.md` (this public Pages repo has only
  `README.md` and `.github/`, no `CLAUDE.md` or `docs/`)
- Everything in this repo is public on the internet: never commit anything private here.
