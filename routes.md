# Deploy routes — Eagle Surveying

Bundled, self-contained pages. Repo root is what Vercel serves (no build step).

| Source design file | Deployed file | URL |
|---|---|---|
| Homepage.dc.html | index.html | / |
| Aerial LiDAR Mapping.dc.html | aerial-lidar-mapping.html | /aerial-lidar-mapping |
| Aerial Photogrammetry.dc.html | aerial-photogrammetry.html | /aerial-photogrammetry |
| About.dc.html | about.html | /about |

`vercel.json` maps the design filenames onto these clean URLs, so in-page links resolve
without rewriting the bundles.

## Adding a page

1. Build `<Page Name>.dc.html`, linking to siblings by their source filename
   (e.g. `href="Homepage.dc.html#projects"`, `href="About.dc.html"`).
2. Add a row to the table above and a redirect pair to `vercel.json`.
3. Bundle it into `deploy/` under its slug filename.
4. Re-bundle any existing page whose links changed, and upload only those.

## Slugs reserved for the remaining Reality Capture pages

/terrestrial-laser-scanning
/360-site-documentation
/aerial-thermal-imagery
/construction-progress-monitoring
/volumetric-stockpile-analysis

Surveying service slugs follow the same pattern, with one constraint from the keyword
document: Category 1B uses /boundary-survey-category-1b/.

## Note on the About map

The interactive Texas county map loads d3, topojson, and county geometry from CDNs at
runtime. It works on the deployed site; offline it falls back to a static PNG.
