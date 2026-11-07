# Layout A — the salt basin and its mountain ranges

One versioned playable map contains the five-train station, all 21 rail splines, the Small dune loop, the Outer mountain route and the Columns line through the basin. The hand and megastructure retain their blockout geometry.

[Outer](images/outer.jpg) · [Columns shoreline](images/columns.jpg) · [Small loop](images/small.jpg) · [Station and platform](images/station-platform.jpg) · [Volumetric light comparison](images/volumetric-light.jpg)

## Geometry and surfaces

[Matched Outer approach, before and after](images/outer-front-matched.jpg) · [Matched orbital views](images/outer-turn-matched.jpg). Both runs used the same camera commands and starting point on a moving train. At the northern shoulder, six cross-sections 55 m from the track now measure 0.8–2.2 m above datum. The local terrain is sampled at 2.75 m, with grouped native-proportion ledges and talus. All source height samples above 600 m retain their prior heights.

- North mesa massif, 1113 m above the salt datum, 8.53 km along its axis above the 130 m threshold.
- East dissected massif, 941 m above the salt datum, 6.44 km along its axis above the 130 m threshold.
- South dissected massif, 764 m above the salt datum, 9.90 km along its axis above the 130 m threshold.

The dune fields reuse the pinned D2 heightfield. The dry ground uses the D2 Hybrid graph, its photographic detail, normals and lighting preset. Wet sand, crust and shallow pools share a registered field with the basin terrain. Rock placements retain their native proportions. A dry-ground selection of the LightDust1 surface effect and optional volumetric fog are integrated.

## Gameplay checks

The map returned 15 fixed-step fleet and route tests. Ordinary DX11 laps are reported below. The four silent clips are continuous samples at the named route locations.

- Small: 21.08 km in 7.30 minutes, frame-time p95 45.35 ms, maximum 65.21 ms.
- Outer: 52.35 km in 13.81 minutes, frame-time p95 42.56 ms, maximum 92.31 ms.
- Columns: 48.52 km in 13.01 minutes, frame-time p95 46.12 ms, maximum 60.05 ms.

All five trains returned to their own berth, allowed the captain to exit, departed again and passed reset in the fixed-step tests. Mammoth completed the three full real-time journeys in one 1440 x 810 DX11 game session. The four shorter recordings, taken in a separate session, measured frame-time p95 between 17.66 and 18.35 ms.

The short Outer segment measured 18.00 ms p95 before the foothill revision and 18.20 ms after. Each is one sample. The short segments include screenshot capture.

Same-camera volumetric fog p95 was 17.70 ms off and 17.19 ms on. These are individual short samples.

[Outer drive](outer.mp4) · [Columns approach](columns-shore.mp4) · [Dune route](small.mp4) · [Platform approach](platform.mp4)

The northern range scale was accepted for further work. The new Outer approach shows ledges and talus. The view after the turn is mostly sandy foothill. A thin dark wedge remains at the edge of the Small view, and some distant shoreline contours show the terrain grid. Surface dust is subtle. Overall artistic review is pending.
