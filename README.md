# OGCxVoyage

Explorateur libre des **frais de voyage** publiés par le gouvernement du Canada
(`travelq` sur [open.canada.ca](https://open.canada.ca/)).

Open-source explorer for the Government of Canada proactive disclosure dataset
**Travel Expenses** (`travelq`).

> Projet communautaire. **Pas** un produit officiel du gouvernement du Canada.  
> Community project. **Not** a Government of Canada product.

Current UI version: **v0.3.0**

---

## À quoi ça sert / What it does

OGCxVoyage charge les notes de voyage via l’API CKAN DataStore (live) ou via
une capture CSV / CSV.GZ locale, puis laisse naviguer le jeu dans le
navigateur :

- grille triable, recherche, facettes (année, groupe, organisation)
- mode **simple** (cartes, fiche bas d’écran, gestes tactiles)
- favoris (`F`) et copie de fiche (`C`)
- **AUDIT** : total déclaré vs somme aérien + transport + hébergement + repas
  + autres ; lignes en écart ; filtre « écarts seulement »
- **STATS** : mix des types de dépenses et tops (nom, org, destination)
- **DIFF** entre deux captures temporelles
- thèmes **DarkBlue** (écran) et **LightRed** (Canada / impression)
- FR / EN

It is not a dump of the whole open.canada.ca catalogue. It is a client for
one dataset: [travelq](https://open.canada.ca/data/dataset/009f9a49-c2d9-4d29-a6d4-1a228da335ce)
(resource `8282db2a-878f-475c-af10-ad56aa8fa72c`).

---

## Lancer en local / Run locally

Open `index.html` in a browser.

If the live DataStore is blocked by CORS (`file://` or a host without the
proxy), use a local snapshot:

1. Download the official CSV from the dataset page (or the in-app
   « Télécharger officiel » button).
2. Optionally gzip it (`travelq.csv.gz`).
3. **Choisir une capture** / drop the file on the sidebar.

---

## Déployer / Deploy (Cloudflare Worker)

The Worker serves the SPA and proxies CKAN so the live grid works from HTTPS.

```bash
npx wrangler deploy
```

| Path | Role |
|------|------|
| `/` | static `index.html` |
| `/ckan/<action>?…` | proxy `https://open.canada.ca/data/api/3/action/<action>` |

See `wrangler.toml` and `worker.js`.

---

## Fichiers / Layout

```
index.html      # application (UI + logique)
worker.js       # proxy CKAN + assets
wrangler.toml   # déploiement Workers
LICENSE         # MIT
NOTICE.md       # données, polices, non-affiliation
CONTRIBUTING.md
```

Snapshots `ogcx_v0.*.html` are historical builds, not the runtime entry point.

---

## Données / Data licence

Software: MIT (`LICENSE`).

Dataset: [Open Government Licence — Canada](https://open.canada.ca/en/open-government-licence-canada)
/ [Licence du gouvernement ouvert — Canada](https://ouvert.canada.ca/fr/licence-du-gouvernement-ouvert-canada).

Third-party notices: `NOTICE.md`.

---

## Raccourcis / Shortcuts

| Key | Action |
|-----|--------|
| `F` | toggle favourite on the selected row |
| `C` | copy the full fiche to the clipboard |

Prefs (`ogcx_lang`, `ogcx_theme`, `ogcx_pageSize`, `ogcx_tfavs`, …) stay in
`localStorage`.

---

## Contribuer / Contributing

See `CONTRIBUTING.md`. Issues and pull requests in French or English.
