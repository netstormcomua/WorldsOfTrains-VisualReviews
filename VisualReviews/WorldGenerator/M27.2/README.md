# M27.2 | Can the D2 desert pass for a photograph?

The near sand is the strongest candidate. Its small ridges and granular variation survive a close view, and successive forms overlap into the shade. The wide shot still gives away the generator: the primary crest is smooth over a long distance and several supporting ridges have a similar outline. The train shot gains some warm reflected light with software Lumen, while the sleeper spacing and broad metallic highlights still read as manufactured assets. M27.1 remains the baseline. This is a candidate for artistic review.

| Selected game capture | How to compare |
|---|---|
| [A · wind-marked surface](hero-A.jpg) | Compare the forked near ripple fronts and their shadow boundary with plate A of the photographic board. Camera 0.48 m above the candidate surface, 47° horizontal FOV, DX11. |
| [B · Mammoth below the dune crests](hero-B.jpg) | Compare the side lighting and the shape behind the engine with plate B. The photograph is a landscape analogue and contains no locomotive. Camera 3.1 m, 43° FOV, software Lumen. |
| [C · desert basin from gameplay height](hero-C.jpg) | Compare the gaps between foreground, middle ground and hazy background with plate C. Camera 4.5 m above a natural flank, 63° FOV, DX11. |

[Photographic reference board](00-photographic-board.jpg) · [Individual photo credits and licenses](references.md) · [Three matching M27.1 / M27.2 camera pairs](01-matched.jpg)

## What made the visible difference

The pure scan gave a gritty close-up and an implausibly dark coastal cast across inland hills. The purely procedural version kept the directional flow but repeated it too evenly. The selected hybrid retains dry mineral colour from the wind-driven surface, rejects much of the scan's low-frequency colour, and blends scanned grain-scale luminance, normals and roughness into sheltered and windward areas. The M27.1 substrate is versioned independently and the original D2 and primary dune controls were preserved. [Material comparison](02-materials.jpg) · [Specific gaps, reference analysis, geometry changes and scan provenance](gap-analysis.md)

The isolated geometry test exposed a jagged shadow on shallow slopes. Switching off screen-space contact shadows removed it with the same mesh, camera and sun. Reducing the coverage of secondary relief helped break up long parallel rows. At the track, low wind deposits partly surround the sleeper ends. Removing only the visual deposit actor in the control exposes the original contact line. The rail mesh and its collision retain their original geometry. [Diagnostic views](04-diagnostics.jpg)

## Rendering and motion

Playable runs DX11 / SM5 with captured sky lighting. Cinematic runs DX12 / SM6 with software Lumen diffuse GI and distance fields. A third DX12 raster run isolates the API and shader-model change. All are per-launch choices. Matched runs used the same saved map, seven camera transforms, manual exposure, 1440 × 810 output, 100% screen percentage and uncapped rendering. Hardware ray tracing, Nanite and volumetric fog stayed disabled. The RDG pass list confirmed Lumen scene lighting, screen-probe gathering and global signed-distance-field tracing. [Rendering comparison](03-rendering.jpg)

| Mode | GPU p95, runs 1 / 2 (ms) | Peak process dedicated GPU allocation (MiB) | Peak process RAM (MiB) |
|---|---:|---:|---:|
| M27.1, matched DX11 reference | 21.20 / 21.21 | 861 | 3,145–3,176 |
| M27.2 Playable, DX11 | 15.06 / 22.52 | 870 | 3,222–3,230 |
| M27.2 DX12 raster, GI off | 22.75 / 22.78 | 1,103 | 3,905–3,980 |
| M27.2 Cinematic, DX12 software Lumen | 48.86 / 49.17 | 1,755 | 4,198–4,288 |

These are editor-game measurements on an RTX 2060 Max-Q with 6 GB of VRAM. Peak observed device temperatures reached 87–88 °C. GPU clocks and per-process Windows memory counters were sampled during each run. The Playable repeats straddle the baseline cost. A speedup is unconfirmed. Lumen consistently cost about 26 ms more at p95 than DX12 raster on this workload. Its most visible contribution is the light and colour in shadow on the engine. The Landscape material representative pixel shader was 529 instructions / 9 samplers for the selected hybrid. Full-world residency, packaged performance and daylight changes over a long journey remain open.

Both five-second clips contain 120 consecutive Unreal game frames at a fixed 24 Hz simulation step and cover 67.54 m of train movement. Compare the sand near the camera, contact edge and shade on the locomotive. These movies play smoothly by construction; their playback speed is independent of the rendering costs above. [Playable train pass](playable-train.mp4) · [Cinematic train pass](cinematic-train.mp4)

A separate 104-frame camera test held position for 32 frames, then pulled away across the dune. On the fixed foreground crop, 20 settled frame pairs gave a mean absolute luminance change of 0.51 on an 8-bit scale for both pipelines; the 99th percentile was two code values. No large transition step was evident across the sampled pullback. Fine ripple rows remain recognizable at grazing angles. A single crop and camera path cannot rule out temporal artifacts elsewhere.

On the final world an actual captain boarded at the door, crossed the spline junction, drove 513 m, braked, exited and reset. The spawn quadrant now loads before play after an early copy allowed the captain to fall through the terrain. Across 264 collision probes below the track the maximum difference from the reference bed was 0.035 cm. The release review includes the near-field deposits, and the snapshot of ten protected source packages matched. [Measurements, camera poses and GPU pass evidence](measurements.json)

## Remaining problems, in visual priority order

1. **Middle-distance shape and distribution.** Several convex crests still share the same smooth outline and abrupt ending. The close secondary layer has limited influence on these silhouettes.
2. **Rail and locomotive scale cues.** Repeating squared sleepers and high contrast on some metal panels remain particularly legible in stills. The deposits improve contact but cannot change the original model.
3. **Surface and air variation.** The hybrid has more varied grain, but still shows locally persistent ripple direction and more uniform sky and distant dust than the photographs. The substrate has no separate grain geometry. Normal detail cannot reproduce every near shadow.
4. **Scale-up.** The optical module can be shared across tiles. The 1 km D2 corridor distance field and single decorative deposit mesh are local fixtures. A larger world needs region-specific distance fields, bounded deposit meshes, streaming tests and fresh performance measurements before adoption.
