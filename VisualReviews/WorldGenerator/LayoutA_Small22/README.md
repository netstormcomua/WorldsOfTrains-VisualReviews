# Small dune loop · Layout A 2.2

The quarter-view camera on Mammoth crossed the steep dune shoulder on the original 2.1 approach. At the four-second frame, the camera was 28.28 m below the collision surface. At a fixed pose the long narrow triangles remained when dynamic shadows were disabled. Raising the diagnostic camera 90 m cleared them. [Controlled camera and shadow comparison](camera-probe.jpg)

The 2.2 terrain recipe lowers the near dune shoulder locally. The same gameplay camera, field of view and orbit commands were used in both moving runs. At the approach, the camera now clears the surface by 17.89 m. During the full 23-second sample the minimum clearance was 17.85 m. The camera was below the Landscape in 461 of 1343 samples before the change and zero of 1351 afterwards. The large angular bank at the turn has receded. Slight faceting remains on the more distant dune.

[Approach comparison](small-front.jpg) · [Turn comparison](small-turn.jpg) · [Original drive](small-before.mp4) · [Revised drive](small-after.mp4)

The revised run covered 1.45 km with 68 rail and clearance checks. The four sector edges and heights at 70 saved rail positions match the source. An independent rebuild reproduced the heightfield digest. The Small review covers this approach and its turn.

## Frame timings

DX11, 1440 × 810, 100% screen percentage, 60 fps cap, VSync off. Values below are per-counter 95th percentiles in milliseconds. Game, render and GPU report separate engine counters, which may refer to different pipelined frames.

| Sample | Wall frame | Game | Render | GPU |
|---|---:|---:|---:|---:|
| Small, original moving capture | 18.34 | 4.86 | 10.66 | 19.88 |
| Small, revised moving capture | 18.05 | 4.96 | 11.90 | 21.04 |
| Revised map, ordinary station departure, seconds 6–26 | 17.48 | 4.49 | 11.69 | 21.80 |
| Heaviest four-second departure window, seconds 5–9 | 17.84 | 5.18 | 12.65 | 22.52 |

The independent station departure used the full-lap driving controls with the usual quarter camera. The train moved from its own berth, with no recording or screenshots during the measurement. The station exit was selected because the earlier 1 Hz trajectory showed repeated late samples there. That trajectory did not record individual frame times. The 42.56–46.12 ms frame p95 previously recorded on full 2.1 journeys was not reproduced by these short runs. The cause of the difference remains open.

[Sample counts and counters](timings.json) · [Terrain preset](preset.json)
