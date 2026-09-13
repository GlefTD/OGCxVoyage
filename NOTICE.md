# NOTICE — OGCxVoyage

OGCxVoyage
Copyright (c) 2026 OGCxVoyage contributors

This product is licensed under the MIT License. See `LICENSE`.

OGCxVoyage is an independent community project. It is not affiliated with,
endorsed by, or operated by the Government of Canada.

---

## Données / Data

Les enregistrements affichés proviennent du jeu **Proactive Disclosure — Travel
Expenses** (`travelq`) publié sur [open.canada.ca](https://open.canada.ca/).

- Dataset: https://open.canada.ca/data/dataset/009f9a49-c2d9-4d29-a6d4-1a228da335ce
- Resource (CSV / DataStore): `8282db2a-878f-475c-af10-ad56aa8fa72c`
- Licence des données : [Licence du gouvernement ouvert — Canada](https://ouvert.canada.ca/fr/licence-du-gouvernement-ouvert-canada)
  / [Open Government Licence — Canada](https://open.canada.ca/en/open-government-licence-canada)

Cette licence s’applique aux **données**, pas au code d’OGCxVoyage.
Les totaux « calculés » et les écarts affichés par le mode AUDIT sont des
dérivés produits localement dans le navigateur. Ils ne remplacent pas le
registre officiel.

Records shown come from the Government of Canada proactive disclosure dataset
`travelq`. The Open Government Licence — Canada applies to that **data**, not
to this software. Audit totals and gaps are client-side derivatives.

---

## Logiciel tiers / Third-party software

### IBM Plex Sans / IBM Plex Mono

Loaded from Google Fonts at runtime.

- Copyright IBM Corp.
- Licence : SIL Open Font License 1.1
- https://github.com/IBM/plex

### CKAN DataStore API

OGCxVoyage interrogue l’API publique CKAN d’open.canada.ca
(`https://open.canada.ca/data/api/3/action`). CKAN is open source software
(AGPL) maintained by the CKAN project. This application is a **client** of the
public HTTP API and does not include CKAN source code.

### Cloudflare Workers (optional deploy)

`worker.js` / `wrangler.toml` target the Cloudflare Workers runtime. Using
those files to deploy does not grant any Cloudflare trademark rights.

---

## Inspiration

The desktop/simple-mode interaction is inspired by [AMCx](https://amcx.gleftd.workers.dev/),
another independent explorer by the same original author. OGCxVoyage does not
redistribute AMCx source.

---

## Marques / Trademarks

« Canada », the Canada wordmark, and related official marks are property of
the Government of Canada. The LightRed theme uses red and white as a visual
nod only. Do not present OGCxVoyage as an official Government of Canada
product.
