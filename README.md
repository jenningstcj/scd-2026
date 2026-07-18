# Strategic Claims Direction — Site (2026 rebuild)

Static site for [strategicclaimsdirection.com](https://strategicclaimsdirection.com/),
built with [MkDocs](https://www.mkdocs.org/) and the
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme.

This replaces the old `scd-gatsby` site, which no longer builds (Gatsby 2 /
React 16, circa 2018) and depended on Material Design Lite's CSS/JS being
served from `code.getmdl.io`, a CDN that has since gone offline. All page
content was migrated over; styling is now self-contained so there's no
external CDN dependency to break again.

## Structure

```
docs/
  index.md            Home
  about.md             About SCD
  services.md          Our Services
  claims-audits.md      Claims Audits
  publications.md       Published Articles
  assets/               Images, favicon
  stylesheets/extra.css SCD brand colors
mkdocs.yml              Site config, nav, theme
```

## Local development

A virtualenv with `mkdocs-material` is already set up in `.venv/`.

```sh
source .venv/bin/activate
mkdocs serve
```

Visit `http://127.0.0.1:8000`. Pages live-reload on save.

If starting fresh (no `.venv/` yet):

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install mkdocs-material
```

## Build

```sh
source .venv/bin/activate
mkdocs build
```

## Deploy

```sh
source .venv/bin/activate
mkdocs build
mkdocs gh-deploy
```

Outputs static HTML/CSS/JS to `site/`, ready to upload to any static host
(Firebase Hosting, Netlify, S3, etc. — the old site used Firebase, see
`scd-gatsby/firebase.json`).

## Known gaps from the old site

- The old site linked to a resume download
  (`docs/Gary Jennings - July 2016.docx`) that was already missing from the
  `scd-gatsby` repo — not carried over here. Add it under `docs/assets/` and
  link it from `docs/index.md` if you have the file.
