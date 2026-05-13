# pensa-ar-web

The umbrella landing for **Pensa Software** at
[pensa.ar](https://pensa.ar) — the home page that introduces the
company and links out to each individual product
(SentinelX, Drop, DNI Scanner, Pensa Reviewer, auth, etc.).

Served from `/var/www/pensa.ar/html/` on the production host
(`orion`). nginx routes:

- `https://pensa.ar/` → this static content

## Layout

```
.
├── index.html               Umbrella landing — introduces Pensa Software
├── contacto.html            Contact page
├── privacidad.html          Privacy policy
├── wallpaper.html           Free wallpapers (download landing)
├── wallpaper_a.html         Specific wallpaper page
├── wallpaper_b.html         Specific wallpaper page
├── ads.txt                  AdSense site verification (public)
├── robots.txt               Crawler directives
├── sitemap.xml              Sitemap for search engines
│
├── auth/                    Sub-landing: pensa.ar/auth — Keycloak as a product
│   └── index.html
├── dniscanner/              Sub-landing: pensa.ar/dniscanner — DNI scanner product
│   ├── index.html
│   └── politica-privacidad.html
├── pensareviewer/           Sub-landing: pensa.ar/pensareviewer
│   └── index.html
├── legal/                   Public legal documents
│   └── marca/               Pensa Software® trademark documentation
│       ├── index.html
│       └── documentos/index.html
│
└── icons/                   Brand assets — favicons, logo variants
    ├── favicon.svg          Primary brand mark
    ├── favicon.ico, .png    Browser-compatible favicons
    ├── pensa-logo*.png      Logo variants (cyan, border, round, etc.)
    └── ic_*.png, *.webp     Product-specific icons
```

## Relationship to other repos

`pensa.ar` is the umbrella site. Each individual product owns its
own primary domain and (where relevant) its own repo:

| Product         | Primary domain              | Web repo                              |
|-----------------|-----------------------------|---------------------------------------|
| SentinelX Cloud | sentinelx.app               | github.com/pensados/sentinelx-app-web |
| SentinelX legacy| sentinelx.pensa.ar          | github.com/pensados/sentinelx-pensa-web |
| Drop            | drop.pensa.ar               | (TBD)                                 |
| Pensa Software® brand | pensa.ar/legal/marca  | (this repo, under legal/marca/)       |

The sub-landings inside this repo (`auth/`, `dniscanner/`,
`pensareviewer/`) are SEO/discovery pages for products that don't
have their own dedicated domain yet — content lives here, linked
from the umbrella `index.html`.

## Deploy workflow

Files in this repo ARE the live website — the working tree IS
`/var/www/pensa.ar/html/`. There is no separate deploy step:
editing here changes what nginx serves immediately.

To pull changes onto the running server:

```bash
ssh orion
cd /var/www/pensa.ar/html
git pull
```

## License

Apache License 2.0 — see [LICENSE](./LICENSE).

Copyright 2026 Carlos Javier Torres Pensa
Pensa Software® — https://sentinelx.app
