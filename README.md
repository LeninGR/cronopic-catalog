# cronopic-catalog

Curated catalog data for the **Cronopic** app — a Simkl client for movies, TV shows and anime.

## Files

- `mcu-catalog.json` — the Marvel Cinematic Universe catalog: **122 timeline rows** (phases, chronological order, Earth IDs) and **47 multiverse rows** (20 universes). Every row carries its real Simkl ID, poster path and release year.

## Schema (v1)

```json
{
  "schemaVersion": 1,
  "updatedAt": "2026-09-27T20:37:31.223Z",
  "timeline": [
    {
      "simklId": "55302",
      "title": "Iron Man",
      "phase": "PHASE_ONE",
      "chronologicalOrder": 2,
      "type": "MOVIE",
      "year": 2008,
      "poster": "82/8226212d560588e22",
      "inPhaseRegistry": true,
      "earthId": "EARTH-616"
    }
  ],
  "multiverse": [
    {
      "simklId": "270912",
      "title": "Big Hero 6",
      "universeName": "Big Hero 6 Universe",
      "earthId": "EARTH-14123",
      "releaseOrder": 1,
      "type": "MOVIE",
      "year": 2014,
      "poster": "63/6350710773ba03d4b"
    }
  ]
}
```

- `poster` is a Simkl image path — the full URL is `https://simkl.in/posters/{poster}_m.webp`.
- `type` is `MOVIE` or `SHOW`.
- `phase` is one of `PHASE_ONE` … `PHASE_SIX`.
- `earthId` values come from the curated chronology (e.g. `EARTH-616`, `EARTH-10005`, `MULTIVERSE`).

## How it is generated

Produced by the capture tooling in the Cronopic app repository (`tools/mcu-catalog/`): the curated structure (phases, order, universes) is authored there, and every Simkl ID + poster is resolved once against the Simkl API and verified by title + year.

This repository exists so the app can fetch the whole catalog with a **single request** instead of resolving hundreds of IDs at runtime.

## Sources

- Chronology structure: [elordendemarvel.com](https://elordendemarvel.com)
- Media metadata and images: [Simkl](https://simkl.com)
