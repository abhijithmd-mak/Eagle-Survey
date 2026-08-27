# Eagle Surveying — website

Static site. No build step, no framework, no dependencies. Every file sits at the
repository root so a folder upload cannot silently drop nested files.

## Deploy (Vercel)

Import this repository as a Vercel project and deploy with the defaults:

- Framework preset: **Other**
- Build command: *(leave empty)*
- Output directory: *(leave empty — the repo root IS the site)*

`vercel.json` sets `cleanUrls`, so `/about` serves `about.html`. Do not delete it
or every internal link breaks.

## What is here

| | |
|---|---|
| `*.html` | 30 pages, one per route, links written as clean slugs |
| `support.js` | the shared runtime every page loads |
| `*.webp` `*.jpg` `*.png` `*.gif` `*.svg` | 160 images, referenced by bare filename |
| `pointcloud.json` | point data for the homepage capture animation |
| `vercel.json` | `cleanUrls` + `trailingSlash: false` |
| `routes.md` | route table, Vimeo ids, and how the pages are regenerated |

Photography ships as WebP; a few images stay JPG, PNG or GIF where those encode
smaller or carry animation. Video streams from Vimeo as background players; no
video files are committed. Leaflet loads from unpkg for the homepage map.

## Editing

These HTML files are generated from design sources. Edit the design, re-export, and
commit the result — hand-editing a page here means the next export overwrites it.
`routes.md` documents the source-file → route mapping and the export rewrites.

## Known pending

- The seven Reality Capture pages carry `<!-- CANONICAL URL PENDING MAK PRODUCTION
  ROUTE -->`; add canonical tags once the production domain is fixed.
- Copper accents use per-ground values (`#996133`/`#E3904C` and similar) rather than
  the single `#A96B38` brand token, because the literal token falls below WCAG AA at
  eyebrow sizes on several section backgrounds.
