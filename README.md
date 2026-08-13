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
| `*.jpg` `*.png` `*.svg` | 0 images, referenced by bare filename |
| `vercel.json` | `cleanUrls` + `trailingSlash: false` |
| `routes.md` | route table, Vimeo ids, and how the pages are regenerated |

Video streams from Vimeo as background players; no video files are committed.
See `routes.md` for the id per section and the Vimeo plan/privacy requirements.

## Editing

These HTML files are generated from design sources. Edit the design, re-export, and
commit the result — hand-editing a page here means the next export overwrites it.
`routes.md` documents the source-file → route mapping.
