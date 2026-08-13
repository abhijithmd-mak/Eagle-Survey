# Eagle Surveying — static site

Deploy `site/` as the project root on Vercel. No build step, no framework.
Largest file is ~153 KB, so this pushes to GitHub through the web UI without
hitting the file-size limit.

## Structure — deliberately flat

Every file sits in this one folder, no subdirectories, so a folder upload cannot
silently drop nested files:

- `*.html` — 30 pages, links written as clean slugs
- `support.js` — the runtime every page loads (68 KB, shared)
- `*.jpg` / `*.png` / `*.svg` — 56 images, referenced by bare filename
- `vercel.json` — `cleanUrls` so `/about` serves `about.html`

88 files total, largest 153 KB. Because links are already slugs, no redirect table
is needed. If images are ever re-grouped into folders, the `src` attributes must be
updated to match.

| Source design file | Deployed file | URL |
|---|---|---|
| Homepage.dc.html | index.html | / |
| About.dc.html | about.html | /about |
| Projects.dc.html | projects.html | /projects |
| FAQs.dc.html | faqs.html | /faqs |
| Aerial LiDAR Mapping.dc.html | aerial-lidar-mapping.html | /aerial-lidar-mapping |
| Aerial Photogrammetry.dc.html | aerial-photogrammetry.html | /aerial-photogrammetry |
| Terrestrial Laser Scanning.dc.html | terrestrial-laser-scanning.html | /terrestrial-laser-scanning |
| 360 Site Documentation.dc.html | 360-site-documentation.html | /360-site-documentation |
| Aerial Thermal Imagery.dc.html | aerial-thermal-imagery.html | /aerial-thermal-imagery |
| Construction Progress Monitoring.dc.html | construction-progress-monitoring.html | /construction-progress-monitoring |
| Volumetric and Stockpile Analysis.dc.html | volumetric-stockpile-analysis.html | /volumetric-stockpile-analysis |
| ALTA-NSPS Land Title Survey.dc.html | alta-nsps-land-title-survey.html | /alta-nsps-land-title-survey |
| Category 1A Land Title Survey.dc.html | category-1a-land-title-survey.html | /category-1a-land-title-survey |
| Category 1B Standard Land Survey.dc.html | boundary-survey-category-1b.html | /boundary-survey-category-1b |
| Topographic Survey.dc.html | topographic-survey.html | /topographic-survey |
| Tree Survey.dc.html | tree-survey.html | /tree-survey |
| Platting Services.dc.html | platting-services.html | /platting-services |
| Construction Staking.dc.html | construction-staking.html | /construction-staking |
| Form Board Survey.dc.html | form-board-survey.html | /form-board-survey |
| As-Built Survey.dc.html | as-built-survey.html | /as-built-survey |
| Easement Exhibits and Legal Descriptions.dc.html | easement-exhibits-legal-descriptions.html | /easement-exhibits-legal-descriptions |
| Elevation Certificate.dc.html | elevation-certificate.html | /elevation-certificate |
| Industry - Data Centers.dc.html | data-centers.html | /data-centers |
| Industry - Industrial Manufacturing and Logistics.dc.html | industrial-manufacturing-logistics.html | /industrial-manufacturing-logistics |
| Industry - Commercial and Retail Development.dc.html | commercial-retail-development.html | /commercial-retail-development |
| Industry - Municipal and Public Infrastructure.dc.html | municipal-public-infrastructure.html | /municipal-public-infrastructure |
| Industry - Education and Higher-Ed Campuses.dc.html | education-campuses.html | /education-campuses |
| Industry - Multi-Family and Master-Planned.dc.html | multi-family-master-planned.html | /multi-family-master-planned |
| Industry - Energy Solar BESS and Transmission.dc.html | energy-solar-bess-transmission.html | /energy-solar-bess-transmission |
| Industry - Specialized High-Visibility Venues.dc.html | specialized-venues.html | /specialized-venues |

## Video

All video streams from Vimeo as background players
(`background=1&autoplay=1&loop=1&muted=1`), sized in JS to cover its panel rather
than letterbox. No video files are committed.

| Section | Vimeo id |
|---|---|
| Homepage — hero flythrough | 1214538057 |
| Projects — featured Buc-ee's panel | 1217621681 |
| Homepage — Blue UAS | 1217318028 |
| Aerial LiDAR Mapping — hero | 1217314191 |
| Aerial Photogrammetry — hero | 1217314194 |
| Terrestrial Laser Scanning — hero | 1217314193 |
| 360 Site Documentation — hero | 1217314192 |

The 360 hero also loads the Vimeo Player API and resets playback at 8.2s
(`heroClipEnd` prop) so the burned-in title near the end of that clip never shows.

Vimeo videos must be public, or unlisted with the deploy domain whitelisted under
privacy settings. Background mode requires a Vimeo Plus/Pro plan; on a free plan the
player shows its controls.

## Regenerating

Pages are the `.dc.html` design files with three mechanical rewrites: sibling
`href="<Name>.dc.html"` → `/slug`, `./support.js` → `support.js`, and nothing else.
Edit the design file, then re-export.
