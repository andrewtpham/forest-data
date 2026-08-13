# forest-data

Geospatial data for US national forests, national parks, and trail routes.

## Project Structure

```
forest-data/
├── national-forests/   # Boundary and administrative data
│   ├── FS_Administrative_Forest_simplified.json
│   ├── NPS_Land_Resources_Division_Boundary_and_Tract_Data_Service.geojson
│   ├── NPS_Land_Resources_Division_Boundary_simplified.json
│   └── USFS_Administrative_Forest_simplified.json
└── trails/             # Downloadable GPX route files
    ├── pct-ca/         # PCT California sections
    ├── pct-or/         # PCT Oregon sections
    ├── pct-wa/         # PCT Washington sections
    └── *.gpx           # Individual trail routes
```

## GPX File Naming Convention

All downloadable GPX files follow this pattern:

```
{trail-name}-{distance}-{year}.gpx
```

### Rules

- **Kebab-case** throughout — lowercase, hyphens as separators, no underscores or capitals
- **Trail name** — the recognizable name of the route. Use widely-known abbreviations only when they're more famous than the full name (e.g. `gr20`, `pct`)
- **Distance** — include when it disambiguates (multi-distance events or ultras with variants). Omit for well-known fixed-distance routes
- **Year** — always include. Routes change year to year due to course updates, reroutes, or conditions. Helps readers know how current the data is

### Examples

| File | Why |
|------|-----|
| `gr20-corsica-2024.gpx` | Well-known abbreviation + location + year |
| `tour-du-mont-blanc-2024.gpx` | Full name (no common short abbreviation) + year |
| `grossglockner-ultra-trail-110k-2026.gpx` | Full name + distance (multiple race distances exist) + year |
| `transylvania-50k-2025.gpx` | Name + distance + year |
| `madeira-crossing-2026.gpx` | Name + year (single known route, distance not needed) |

### PCT Section Files

PCT data is organized by state in subfolders (`pct-ca/`, `pct-or/`, `pct-wa/`). Files within follow the official section labeling convention and are not renamed:

```
pct-ca/CA_Sec_A_tracks.gpx
pct-ca/CA_Sec_A_waypoints.gpx
```

## Data Sources

### national-forests/

- **USFS Administrative Forest boundaries** — simplified GeoJSON from the US Forest Service
- **NPS Land Resources Division** — national park boundary and tract data

### trails/

- GPX route files from various trail races and thru-hikes
- PCT section data from official halfmile/Guthook track files
