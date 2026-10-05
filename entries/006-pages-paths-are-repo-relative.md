# 006 — "Pages paths are repo-relative, so `../` reaches the repo"

**Believed:** 2026-10-05, for about twenty minutes · **Killed:** same day · **Status:** corrected in place

## What we believed

When publishing the svg-instruments gallery on GitHub Pages with source `docs/`, the page referenced assets as `../patterns/...` — repo-relative paths, because in the repository the gallery file sits in `docs/` and the assets one level up.

## Why it seemed true

The paths were correct *in the repo*: open `docs/index.html` locally, or view it on github.com, and `../patterns/` resolves. Browsers resolve relative URLs against the document URL, and on GitHub the document URL does sit one level below the assets.

## What killed it

The served site's root **is** the source directory. With source `docs/`, the site contains only what is under `docs/`; `../patterns/` escapes the site root and 404s. Every asset rendered as a broken image on the live gallery while looking perfect in the repo and in local preview. The repo and the site are different filesystems wearing the same names.

## What changed

- Gallery moved to the repo root and Pages source set to `/`, so repo-relative and site-relative coincide ([svg-instruments](https://github.com/Orvii/svg-instruments), live at orvii.github.io/svg-instruments).
- House rule for any future Pages site: the source directory is the site's `/`. Every asset the page needs must live under it, and relative links must be written against the *site* tree, verified with a curl to the served URL — not against the repo tree.
- Verification rule: a Pages deploy is not verified by opening the file locally or on github.com; it is verified by fetching the served URL for the page *and* for one asset.
