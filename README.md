# HCDL Site Theme

Custom black/dark theme and page snippets for the HCDL dynasty league on
MyFantasyLeague.com (league 43736, `www45.myfantasyleague.com`, built on top
of MFL's "Onyx" skin).

## Layout

- `css/theme.css` — site-wide override stylesheet. Loaded by URL from MFL's
  admin, applies to every page (nav, tables, cards, buttons, etc).
- `pages/` — full HTML snippets for MFL's per-page "Custom HTML" content
  boxes (Rules, Home page modules, etc). Copy-paste these directly into the
  relevant MFL admin page.

## Installing the site-wide theme

1. Enable GitHub Pages for this repo: **Settings > Pages > Source: Deploy
   from a branch > `main` / `(root)`**.
2. Once Pages is live, the stylesheet is served at:
   `https://matthewjaustin.github.io/hcdl-site/css/theme.css`
3. In MFL: **For Commissioners > Setup > Appearance Setup > Images & Other
   URLs**, paste that URL into the custom CSS field.
4. Every push to `main` updates the live stylesheet — no re-upload needed.

## Notes on MFL's CSS cascade

MFL loads stylesheets in this order: `MFLBaseCSS.css` → skin CSS
(`Onyx.css`) → skin `responsive.css` → your custom CSS URL. `theme.css`
relies on loading last to win the cascade, and uses `!important` only where
the base skin also used `!important` (card/table backgrounds).

The class/ID names it targets (`.report`, `.homepagemodule`,
`.myfantasyleague_menu`, `.oddtablerow`/`.eventablerow`, etc.) were pulled
from the live league's page source and the Onyx skin CSS directly — MFL
doesn't document these, so if a future MFL update renames something, re-pull
the page source (logged-in `curl`/view-source) and check before assuming the
selector still matches.
