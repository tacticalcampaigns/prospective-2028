# Prospective 2028 Races — Utah

Static single-page dashboard: every Utah district on the November 2028
general-election ballot — all 75 State House seats, the 14 State Senate
seats up that year, and all 4 U.S. House seats — with the presumed 2028
incumbent and past general-election results (2022, 2024, 2026) by district.

Live at https://data.tacticalcampaigns.com/prospective-2028/ — part of the
Tactical Data suite (Tactical Campaigns).

## What's on the page

- Folder tabs for House / Senate / Congress, each with a Leaflet map and a
  sortable, searchable table.
- A year filter (2022 / 2024 / 2026) that updates both the map colors and
  the table.
- A partisan heatmap: districts colored by the selected year's Republican
  vs. Democratic vote-share margin (red for R ahead, blue for D ahead,
  intensity by margin size). Districts not up in the selected year render
  neutral gray.
- Table columns: district, 2028 incumbent, registered active voters,
  winner, R / D / other votes with shares, 2024 GOP strength (RRS), and
  change vs. the 2024 baseline in points.

## Data sources

- 2022 results: Utah official precinct-level results (oe2022 precinct CSV),
  aggregated by office and district.
- 2024 results: Utah official results export (general11052024).
- 2026 results: Utah state All-Results report as of the Nov 12, 2026
  snapshot (state lastUpdated 2026-11-13T01:10:43Z). **Unofficial until
  the Nov 23, 2026 canvass.**
- Registration (2026 only): active registered voters from Ali Majid's
  November 2026 Dashboard (Tableau Public extract). District-level
  registration for 2022/2024 is not publicly available; the page shows
  n/a for those years rather than an estimate.
- GOP strength 2024 (RRS): (Republican votes for Governor + Attorney
  General + Treasurer + Auditor, divided by 4) / 2024 presidential
  turnout, from official 2024 precinct-level results mapped to current
  district lines.

## Caveats

- **Congressional districts, 2022/2024:** those elections ran under the
  pre-2026 district lines and are not comparable to the current
  2026–2032 court-ordered map, so no 2022/2024 congressional results are
  shown; the map renders those districts gray for those years.
- **HD48 is the only race still uncalled** as of the Nov 12 snapshot
  (Jake Hunsaker (R) leads by 298 votes); it carries a PRESUMED badge.
  Every other 2028 incumbent is the decided winner of the most recent
  election for the seat.
- District boundaries: Utah Geospatial Resource Center (AGRC). The
  congressional GeoJSON is the 2026–2032 court-ordered map.

## Build

`build_site.py` (in the parent directory) reads `data/races.json` and
regenerates `site/index.html` with the data embedded at build time. The
page is fully static — no backend. Re-run the generator after any data
update and re-push `index.html`.
