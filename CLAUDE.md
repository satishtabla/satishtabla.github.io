# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static personal website for tabla player Sathish Babu and his Taal Mandir School of Tabla, served by GitHub Pages at `satishtabla.in` (see `CNAME`; `_config.yml` only sets a Jekyll theme, and no Jekyll templating is used). There is no build step, package manager, linter, or test suite. Pushing to `master` deploys.

Preview locally by opening the HTML files directly or with any static server, e.g. `python3 -m http.server`.

## Structure

- Every page is a standalone, hand-written XHTML-doctype `.html` file at the repo root. There are no includes or templates, so the nav (`#nav`), the hamburger menu (`.btnmenu` / `.menuoverlay`, toggling `#container.open`) and the footer with inline SVG social icons are **copy-pasted into every page**. A change to the nav, footer or social links has to be repeated in every `.html` file.
- `style.css` is the only stylesheet in use. It holds custom `@font-face` fonts from `fonts/` and a single mobile breakpoint at `@media (max-width: 575px)`. `style_backup.css` and `index-backup-20240719.html` are old backups and aren't linked.
- `js/`: pages load jQuery 3.3.1 and Fancybox (`jquery.fancybox.min.css` sits at the root). Image lightboxes use the `data-fancybox` attribute on links. A few legacy pages (`concerts.html`, `video.html`, `news2009*.html`, `other-events.html`) still use the old `lightbox.js`, `swfobject.js` and `.swf` Flash players.
- Images live in `images/` (page assets), `gallery/` (photo gallery pages `gallery*.html`) and `certificates/` (the awards page). Thumbnails use a `thumb-` prefix.

## Recurring task: yearly Gurupurnima event page

Each year a new event page is added by copying the previous one:
1. Copy the previous `gurupoornimaYYYY.html` to `gurupoornima<new year>.html`. The page uses a `.fullwidth` block of brochure images and a `.btn-wrap > a.btn` "Download PDF" link.
2. Add the brochure images to `images/` (e.g. `images/Gurupurnima-2026-1.jpg`) and the PDF to the repo root (e.g. `Gurupurnima-2026_Taal_mandir.pdf`).
3. In `index.html`, point the `.homecontent .col2 .other` link (button image `images/btn-gurupurnima.png`) at the new page, and update its `alt` and `title` text.
