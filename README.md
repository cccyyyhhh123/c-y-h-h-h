# Ledger — one book, one balance

A shared expense ledger for a household or a crew. Everyone types the same six
digits and writes into the same running total. No account, no server, nothing
leaves the browser.

**Author:** Yuhan.Cai
**Stack:** hand-written HTML, CSS and JavaScript — no framework, no build step
**Storage:** `localStorage`

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Home: the hero, four steps, the deposit/spend switch, what the screen is made of, and the open-a-book dialog |
| `pricing.html` | Pricing: three plans, the comparison table and five questions |
| `contact.html` | Contact and about: the form, what the site is built on, links to the other pages |
| `book.html` | The ledger screen: add a line, filter by month or type, delete a mistake |

Every page carries the same navigation bar and footer. Open `index.html` and
press **Open a ledger** — a six-digit key is made for you and the ledger opens
with it.

## Identity

- `images/og-image.jpg` — 1200 × 630, the poster share cards show
- `images/apple-touch-icon.png` — 180 × 180
- `images/favicon-32.png` — 32 × 32 (plus `favicon-192.png` for Android)
- the Open Graph and Twitter tags sit in every page's `<head>`, pointing at the
  live address `https://cccyyyhhh123.github.io/c-y-h-h-h/`

## How it works

- A key is six digits. Anyone holding it opens the same book, because the
  entries are read from `localStorage`.
- `book.html` always opens a book: the key you arrived with, else the last book
  saved in this browser, else a fresh one.
- An entry is one line — date, type (deposit / spend), category, amount, note.
  The balance and the monthly totals are computed from the lines, never typed in.
- Books written by the earlier build still read: their values are mapped to the
  English slugs on load.

## Run it

```bash
# open the file directly
start index.html          # Windows
open index.html           # macOS

# or serve the folder, so relative links behave like production
python -m http.server 8000
# http://localhost:8000/
```

Live on GitHub Pages: **Settings → Pages → Deploy from a branch → `main` /
`/ (root)`**. `index.html` becomes the site root; `pricing.html`, `contact.html`
and `book.html` follow the same relative paths.

## Structure

```
index.html · pricing.html · contact.html · book.html
style.css            one stylesheet for the three content pages
images/              og-image.jpg · apple-touch-icon.png · favicon-32.png · favicon-192.png
```