# Sylhet Haor Wetland Dashboard

An interactive dashboard showing permanent and seasonal water in four haors (seasonal
wetlands) of greater Sylhet, Bangladesh. Select a haor to see its water area, the split
between permanent and seasonal water, and its 2000-2020 time series.

**Live dashboard:** https://pramila-paul.github.io/sylhet-haor-dashboard/

## The four haors

| Haor | Total water (km²) | Permanent | Seasonal | Permanent share |
|------|------|------|------|------|
| Tanguar Haor | 132.9 | 9.7 | 123.2 | 7.3 % |
| Hakaluki Haor | 117.7 | 15.8 | 101.8 | 13.5 % |
| Dekhar Haor | 25.8 | 0.1 | 25.8 | 0.2 % |
| Hail Haor | 17.7 | 0.0 | 17.7 | 0.0 % |

The gradient in permanent share is the key finding: Hakaluki has a real perennial core,
Tanguar less so, and the two smaller haors are almost entirely seasonal — they dry out each year.

## How it was built

The analysis and the presentation are separate, which is deliberate:

- **Analysis (Python / Google Earth Engine).** Water area was computed from the JRC Global
  Surface Water dataset. Permanent vs seasonal area comes from the `seasonality` band
  (12 months = permanent, 1-11 = seasonal); the yearly time series comes from the
  `YearlyHistory` water class (3 = permanent, 2 = seasonal). Done in a Jupyter notebook
  using `earthengine-api` and `geemap`.
- **Boundaries.** No authoritative haor boundary dataset is publicly available, so each
  haor outline was delineated from JRC water occurrence (thresholding and vectorization).
- **Front-end (JavaScript).** A single static HTML page using Leaflet (map) and Chart.js
  (time series). Results are embedded in the page, so it needs no server or authentication
  and hosts free on GitHub Pages.

## Data

- JRC Global Surface Water (Pekel et al., 2016), via Google Earth Engine.
- Basemap: OpenStreetMap.
- Reference context: amarhaor.com and Banglapedia.

## Limitations

- **Boundaries are approximate** — delineated from water occurrence, not administrative haor
  limits.
- **Time window** — 2000-2020, the period of consistent Landsat coverage; the late 1990s had
  sparse coverage.
- **Resolution** — JRC is 30 m, so small beels and channels are missed or merged.
- **Connected wetland** — at high water the haors merge, so a single haor cannot always be
  cleanly separated from neighbours or feeder rivers.

## Author

Pramila Paul
