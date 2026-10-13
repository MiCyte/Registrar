# Ohio: administrative entities

Every Ohio county, city, village and township the registrar outlines, as GeoJSON. GitHub draws
each file as a map: open one to see it.

| file | what it holds |
|---|---|
| [`counties.geojson`](counties.geojson) | the 88 counties |
| [`municipalities/<county>.geojson`](municipalities/) | each county's cities, villages and townships (2,232 in all) |
| [`summary.json`](summary.json) | counts and when this export was made |

Each feature carries:

| property | meaning |
|---|---|
| `name` | display name (`Akron City`) |
| `slug` | the gazetteer label (`akron_city`) |
| `node` | the gazetteer node the outline is filed under: a position in the msn address space (`3-2-3-17-77-1-1`) |
| `level` | `county`, or `community` for a municipality |
| `jurisdiction` | `county`, `city`, `village` or `township` |
| `entity_msn` | the msn of the administrative-entity profile that cites this outline (`3-2-3-17-77-1-1-1-1-1`); empty where none does yet |
| `entity_title` | that profile's title (`city_of_akron`) |
| `county` | the county a municipality stands in |

## Sources

- **Counties:** US Census cartographic boundaries (1:20,000,000), held since 2026-08-21.
- **Municipalities:** cities and villages from Ohio's OGRIP corporation boundaries, classified
  city or village by the Census (TIGERweb incorporated places); townships from ODNR's *current*
  civil townships (not the 1983 survey grid OGRIP also publishes). Retrieved 2026-10-12 and
  simplified to about 20 m. Sixteen places OGRIP still outlines are not in the Census's
  incorporated places any more (dissolved villages such as Amelia and Brady Lake) and are not
  included.
- 68 municipalities and Columbus have an outline but no profile yet; their `entity_msn` is
  empty.

## What this is, and is not

A readable projection of the registrar's datums, exported by `export_registrar_geojson` in the
core. It describes the registry; it does not replace it. An instance reads the registrar's
resources as MSS payloads over MSN (the registry still is at
`https://micyte.com/__mss/public/stills/registry.mss`), never from these files.
