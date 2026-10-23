# Ledger — one book, one balance

A shared expense ledger for a household or a crew. Everyone types the same six
digits and writes into the same running total. No account, no server, nothing
leaves the browser.

**Author:** Yuhan.Cai · **Stack:** hand-written HTML, CSS and JavaScript (no
framework, no build step) · **Storage:** `localStorage`

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Home, pricing and contact merged into one document (three sections, one navigation bar) |
| `book.html` | The working ledger: add a line, filter by month or type, delete a mistake |

Open `index.html` in a browser (or serve the folder), then press **Open a
ledger** — a six-digit key is made for you and the ledger opens with it.

## How it works

- A key is six digits. Anyone holding it opens the same book on their own
  copy of the page, because the entries are read from `localStorage`.
- `book.html` always opens a book: the key you arrived with, else the last
  book saved in this browser, else a fresh one.
- An entry is one line — date, type (deposit / spend), category, amount, note.
  The balance and the monthly totals are computed from the lines, never typed in.
- Books written by the earlier Chinese-tagged build still read: their values are
  mapped to the English slugs on load.

## Run it

No build step is required.

```bash
# either: open the file directly
start index.html          # Windows
open index.html           # macOS

# or: serve the folder (recommended, so relative links behave like production)
python -m http.server 8000
# then visit http://localhost:8000/
```

Deploying on GitHub Pages: push the repository, then **Settings → Pages →
Deploy from a branch → `main` / `/ (root)`**. `index.html` becomes the site root
and `book.html` stays reachable at `/book.html`.

## Structure

```
index.html   home · pricing · contact (merged)
book.html    the ledger screen
```

Fonts are loaded from Fontshare (General Sans) and Google Fonts (Inter); both
fall back to the system stack offline.
