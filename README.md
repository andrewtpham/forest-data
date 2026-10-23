# forest-data

Trail routes and boundary data for maps. The GPX files are free to download. See [ATTRIBUTION.md](ATTRIBUTION.md) for where each file comes from.

## Project structure

```
forest-data/
├── national-forests/        # US forest and park boundaries
│   ├── fs-administrative-forest-simplified.json
│   ├── nps-land-resources-division-boundary-and-tract-data-service.geojson
│   ├── nps-land-resources-division-boundary-simplified.json
│   └── usfs-administrative-forest-simplified.json
└── trails/
    ├── *.gpx                # One file per trail or race route
    └── pct/                 # Pacific Crest Trail
        ├── pacific-crest-trail.geojson                      # Whole trail with elevation, one feature per section
        ├── pacific-crest-trail-complete-simplified.geojson  # Whole trail, simplified, no elevation
        ├── pacific-crest-trail-pcta-simplified.gpx          # Whole trail, simplified, no elevation (26 MB)
        ├── sections/        # One GeoJSON per section: desert, sierra, northern-california, oregon, washington
        └── halfmile/        # Halfmile section tracks and waypoints
            ├── ca/          # Sections A to R
            ├── or/          # Sections B to G
            └── wa/          # Sections H to L
```

## Downloading a file

Open a file on GitHub and click **Download raw file**. To link to a file or load it in code, use its raw URL:

```
https://raw.githubusercontent.com/andrewtpham/forest-data/refs/heads/main/trails/gr20-corsica-2024.gpx
```

The NPS boundary file is stored in Git LFS, so its raw URL returns a pointer. Download it from the GitHub page instead.

## File naming

Trail GPX files follow this pattern:

```
{trail-name}-{distance}-{year}.gpx
```

### Rules

- **Kebab-case.** Lowercase, with hyphens as separators. No underscores or capitals.
- **Trail name.** The name people know the route by. Use an abbreviation only when it's better known than the full name, such as `gr20` or `pct`.
- **Distance.** Include it when a race has more than one distance. Leave it out for routes with one fixed length.
- **Year.** Include it on every trail and race file. Courses change from year to year with reroutes and conditions, and the year tells readers how current the route is.

### Examples

| File | Why |
|------|-----|
| `gr20-corsica-2024.gpx` | Known abbreviation, location and year |
| `tour-du-mont-blanc-2024.gpx` | Full name and year |
| `grossglockner-ultra-trail-110k-2026.gpx` | Full name, distance (the race has several) and year |
| `transylvania-50k-2025.gpx` | Name, distance and year |
| `madeira-crossing-2026.gpx` | Name and year (one known route) |

### PCT files

PCT files live in `trails/pct/` and use kebab-case too. Whole-trail and section files are named after the trail or section and carry no year. Halfmile files keep their section labels in lowercase:

```
trails/pct/sections/pct-sierra.geojson
trails/pct/halfmile/ca/ca-sec-a-tracks.gpx
trails/pct/halfmile/ca/ca-sec-a-waypoints.gpx
```

## Git LFS

Only the NPS boundary file uses Git LFS (see `.gitattributes`). Commit every trail file as a plain file. A raw URL for a file in LFS serves the pointer, which breaks the maps on andrewpham.dev.
