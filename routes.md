# Deploy routes — Eagle Surveying

Bundled, self-contained pages. Drop this folder into Vercel as the project root
(no build step, no framework — static output).

| Source design file | Deployed file | URL |
|---|---|---|
| Homepage.dc.html | index.html | / |
| Aerial LiDAR Mapping.dc.html | aerial-lidar-mapping.html | /aerial-lidar-mapping |

## Adding a page

1. Build the page as `<Service Name>.dc.html`, linking to siblings by their
   **source filename** (e.g. `href="Homepage.dc.html#projects"`,
   `href="Aerial LiDAR Mapping.dc.html"`). Preview links then work as you design.
2. Add the page to the table above with its slug.
3. Bundle each page into `deploy/` under its slug filename.
4. Rewrite the source filenames to slugs inside the bundles, using the table as the map
   (`Homepage.dc.html` -> `/`, `Aerial LiDAR Mapping.dc.html` -> `/aerial-lidar-mapping`, ...).
   Cover both the plain and %20-encoded forms of names containing spaces.

Steps 3-4 are what I run each time you ask for a fresh deploy bundle.

## Slugs planned for the remaining Reality Capture pages

/aerial-photogrammetry
/terrestrial-laser-scanning
/360-site-documentation
/aerial-thermal-imagery
/construction-progress-monitoring
/volumetric-stockpile-analysis

Surveying service slugs follow the same pattern, with one constraint from the keyword
document: Category 1B uses /boundary-survey-category-1b/.
