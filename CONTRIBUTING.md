# Contributing to OGCxVoyage

Merci. OGCxVoyage is a small single-page explorer for the Government of Canada
`travelq` travel-expense dataset. Keep changes focused and reviewable.

---

## Langues / Languages

- Interface : français et anglais (`I18N` in `index.html`). Every user-visible
  string must exist in **both** locales.
- Issues / PRs : FR or EN is fine. Write the PR title in one language and
  repeat the summary in the other if the change is user-facing.

---

## Avant de coder / Before you start

1. Open an issue describing the bug or feature (or comment on an existing one).
2. Work from the latest `index.html` (current app). Do not revive old
   `ogcx_v0.*.html` snapshots unless the issue is a historical bisect.
3. Keep the app usable as a **single file** (`index.html`) opened from disk.
   The Worker is only a CORS proxy + static host.

---

## Setup

```bash
git clone https://github.com/<org>/OGCxVoyage.git
cd OGCxVoyage
```

Open `index.html` in a browser.

Optional Worker (CORS proxy for the live DataStore):

```bash
npx wrangler dev
```

Deploy:

```bash
npx wrangler deploy
```

---

## Règles de contribution

### Do

- Match the existing style: one HTML file, vanilla JS, CSS variables for
  themes (`data-theme="darkblue"` / `data-theme="lightred"`).
- Persist user prefs in `localStorage` with the `ogcx_` prefix.
- Prefer official CKAN `datastore_search` first, then local CSV / CSV.GZ
  snapshots for offline use and diffs.
- Keep keyboard shortcuts: `F` favourite, `C` copy fiche.
- Bump the visible version string in `<title>` and `header h1 .ver` together.
- Add a short note in the PR: what changed, how to test (live / capture /
  simple mode / audit / both themes).

### Don’t

- Do not vendor the full `travelq` dataset in git.
- Do not add a bundler, framework, or npm UI runtime unless there is a
  discussed issue for it.
- Do not scrape `search.open.canada.ca` HTML. Use the documented CKAN API
  and the official CSV download URL.
- Do not claim Government of Canada affiliation in UI copy or docs.
- Do not commit secrets, Wrangler API tokens, or personal captures.

---

## Data & audit accuracy

`trueTotal` is the sum of `airfare + other_transport + lodging + meals +
other_expenses`. A gap is `|trueTotal - total| >= 0.01`. Treat audit output
as a **hint** that the published row may be inconsistent, not as a legal
finding. If you change that formula, document it in the PR and in the fiche
labels.

---

## Commits & pull requests

- Commits: short imperative subject (`Add LightRed print theme`).
- One concern per PR when possible (theme, audit column, Worker, docs).
- Include before/after notes for UI changes. Screenshots help.
- Maintainers may ask you to rebase on `main`.

---

## Code of conduct (short)

Be decent. No harassment, no hate speech, no dumping of personal information
found in the public dataset into issues or social posts beyond what the
interface already shows. The dataset names public office holders; do not use
this project to target individuals.

By contributing you agree that your contribution is licensed under the MIT
License (`LICENSE`) and that you have the right to submit it.
