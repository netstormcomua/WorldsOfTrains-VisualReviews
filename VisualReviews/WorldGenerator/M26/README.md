# M26 | How tall does a dune feel beside a train?

Four separate Unreal game worlds compare the same compound wind-shaped deposit at 100, 300, 500 and 1,000 m. Each contains a full-size stationary Mammoth on a short straight Railway reference track. The distant and aerial cameras are scaled with the formation. The camera-to-train offset, the 4.5 m eye height and the separate fixed 1,650 m summit distance are controlled comparisons. All views use a 75° horizontal field of view. The scenes are ready for artistic review.

| Height | Measured footprint | Core sample spacing | Core export | Peak generator working set | GPU p95 | Frame-tick p95 |
|---:|---:|---:|---:|---:|---:|---:|
| 100 m | 1.32 × 0.77 km | 2.13 m | 2.71 s | 315 MiB | 6.41 ms | 6.81 ms |
| 300 m | 3.97 × 2.31 km | 6.38 m | 2.63 s | 315 MiB | 7.17 ms | 7.53 ms |
| 500 m | 6.61 × 3.85 km | 10.63 m | 2.46 s | 315 MiB | 9.29 ms | 9.29 ms |
| 1,000 m | 13.23 × 7.70 km | 21.27 m | 2.59 s | 315 MiB | 6.68 ms | 7.22 ms |

Footprints use a common small positive threshold in reference coordinates to exclude the flat rim. Core export times cover preparation and four height tiles in a fresh Python process per case; they exclude Unreal import, the distant apron and regression checks. Each case has the same sample budget. GPU timings are measured RHI frame cycles across settled fixed cameras at 1440 × 810, editor game, DX11, VSync off, t.MaxFPS 0. Screenshot frames were excluded. Peak process working set during these captures was 2,877–2,909 MiB. These short samples do not rank intrinsic cost by height or predict packaged or full-world performance.

## Visual evidence

* [Same train, same camera offset](01-train.jpg). The low camera is 117 m horizontally from the train centre in every case. At 300 m the crest rises conspicuously over the locomotive while leaving a second shoulder readable. The gain from 500 to 1,000 m looks smaller here because the higher ridge is farther away.
* [Near the base and exactly 1,650 m from the summit in plan](02-base-fixed.jpg). The 100 m feature reads as a low group. The 300 and 500 m relief still separates into near and far crests. At 1,000 m the fixed-distance observer stands on the lower slope and sees mostly one face. The increased physical relief alone provides few clues to its magnitude.
* [Entire massif, normalized framing](03-entire.jpg), [flank panoramas](04-panorama.jpg) and [three-quarter aerials](05-aerial.jpg). Overlapping crests are most legible from the flank. The train becomes a small mark in the largest panoramas. Much of the near ground is empty; at longer distances the horizon reads as a dark, nearly level band. A future close route will need smaller, physically independent intervening forms, more varied atmospheric depth and trackside scale references.
* [Mixed versus full Landscape LOD](06-lod.jpg). No open seam is evident in the reviewed overview pair. This is a limited viewpoint test. A crest can lose metres of local shape at coarse spacing even when no gap is visible in an overview.
* [Four synchronized lateral passes](lateral-pass.mp4). Each Unreal camera moves 120 m beside the same stationary train, 5.5 m above the foreground. 48 actual frames per scale, assembled at 12 fps into a four-second silent comparison. This is sampled motion, not a real-time driving benchmark.

### Horizontal distance to measured summit (metres)

| Height | Train camera | Near base | Distant | Flank | Three-quarter | Fixed |
|---:|---:|---:|---:|---:|---:|---:|
| 100 | 388 | 278 | 1,272 | 499 | 1,065 | 1,650 |
| 300 | 874 | 761 | 3,817 | 1,498 | 3,194 | 1,650 |
| 500 | 1,361 | 1,246 | 6,362 | 2,497 | 5,324 | 1,650 |
| 1,000 | 2,580 | 2,458 | 12,725 | 4,995 | 10,648 | 1,650 |

## Technical evidence

* Measured summit relief in the reopened Landscapes was 99.999 / 300.000 / 500.000 / 1,000.000 m relative to the train floor. Real Landscape collision was sampled at 24 vertices per map, with an additional summit ray and nine train-ground rays. Maximum vertex error across the four maps was 0.62 cm. Maximum analytic slope in the sampled compound was 37.62°. Height encoding used no clamping. All four core tiles shared identical samples along their adjoining edges.
* A complete independent rebuild matched all saved core height files. A bounded secondary-ridge edit changed only NW. Replacing that tile produced the same heightfield as a full recomposition; the other three tiles remained byte-identical. Current local regeneration still prepares the compact canonical relief in memory before extracting a tile. This does not establish large-world incremental generation time.
* In every actual game map, all four core regions loaded. NE unloaded, its collision disappeared, a neighbor retained collision, and reloading restored its sampled height and normal. Across 242 seam probe pairs per map, largest height differences over a horizontal step of 20 cm were 11.2 / 7.1 / 7.3 / 7.5 cm. These pairs cross sloping terrain. Forced adjacent LOD 0/2 and automatic LOD were exercised. In a separate 4× CPU coarsening experiment the active-surface p95 errors were 0.26 / 0.78 / 1.30 / 2.60 m, with an extreme of 10.70 m for the largest massif. This approximation is distinct from measuring Unreal's actual LOD silhouette error.
* Core geometry is 256 Landscape components across four streamable sublevels. The horizon uses eight additional one-component coarse patches. Early stills revealed the edge of the square core; replacing the background plane with adjoining terrain removed that exposed edge from the selected distant and aerial views. The existing pinned M24 A/B/C heightfield regression and M23.1 implementation check passed.

**Recommendation for the 10 × 10 km world.** Start with 100 m flanks and one 300 m landmark to frame the low train route. A 500 m ridge is a strong candidate for one planned reveal. Keep this 1,000 m configuration as an off-map or edge-of-world experiment: its long footprint exceeds the world width and its steep face needs more foreground references to convey scale. Artistic adoption awaits review.

[Measurements and camera positions](measurements.json) · [Generator design, scenic railway and outstanding M25 work](design.md)
