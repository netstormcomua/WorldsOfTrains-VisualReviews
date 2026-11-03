# M24 | From a single dune to a streamed desert Landscape

**A (Open passage) is the recommended Railway test site. B (Oblique ridges) has the strongest overlapping silhouettes. C (Sheltered basin) gives the largest open floor.** All three use the approved m23.1 geometry and the R3, R1 and R2 preset families. This milestone is ready for review.

| Material | Review question |
|---|---|
| [Three compositions](01-fields.jpg) | Compare the same elevated and 4.5 m cameras. Which space would you want to travel through? |
| [Reverse and crossing views](02-ground.jpg) | Look at foreground occlusion, slip faces and spacing between groups. |
| [LOD and reload comparison](03-streaming.jpg) | Inspect the same oblique view across the four-region intersection at forced 0, mixed 0/2 and automatic LOD after reload. |
| [Rejected and final horizon](04-horizon.jpg) | The rectangular background break was visible from above. Distant non-colliding sand ridges close that silhouette in the final shot. |
| [Traversal samples](05-traversal.jpg) and [three-second MP4](A-traversal.mp4) | 72 actual Unreal camera positions through A. Camera center is 4.5 m above the sampled surface. Playback is 24 fps from offline captures. |
| [Technical measurements](measurements.json) and [Railway plan](railway-plan.md) | Reproducibility, actual collision/streaming tests and proposed corridor. |

## Geometry and composition

The 1,008 x 1,008 m core consists of four independent, streamable 505 x 505 Landscapes with 1 m spacing. Twelve coarser Landscape patches surround the test area. A distant visual backdrop completes the horizon. Each map has 448 Landscape components, including 256 in the playable core. The three terrain presets each contain 24 stable placements on broad hills and a shallow valley. The largest primary dunes are 47, 49 and 49 m in A, B and C. Smaller supporting masses range down to about 8 m.

Desert Terrain m24.1 samples the world-space substrate; Dune Field m24.1 explicitly requests Single Dune m23.1 for each placement. It checks the entire positive footprint against the local slope limit, trims empty samples, and combines the overlapping height contributions in stable ID order. Terrain adds the substrate once. There is no rectangular fade at the edge of a core region. The earlier field generator and its defaults remain pinned. No new isolated dune geometry was introduced.

A has a legible passage between tall shoulders; parts of its foreground are still sparse. B builds stronger foreground-to-background depth, but its nearest dune blocks the distant view at one of the fixed cameras. C reads well from above; its broad open foreground has little scale information from ground height. Small attached crescents and the uniform sand treatment can still repeat at distance. The inspected final views show no obvious rectangular cut at the core crossing. The outer skyline remains subdued.

## Checks performed

- Each map was saved and reopened in Unreal 5.8. On each core, 384 line traces at vertices and Landscape component boundaries matched the imported height to within 0.07 cm. A real probe on a footprint with a 14.85-degree base slope matched to 0.036 cm. The first C layout hit 15.60 degrees and was rejected. The accepted C substrate has a gentler bank; its steepest occupied sample is 14.41 degrees.
- Repeated generation reproduced all 16 exported region hashes in each composition. Rebuilding NE from only intersecting configurations reproduced the full-build tile. A 10% reduction of one supporting dune changed only NE in all three numeric experiments. In a separately saved Unreal copy of A/NE, the edited collision surface moved by 3.908 m at the strongest changed point. Reopening the reference restored the old collision height. All five original A map packages retained their pre-edit hashes during that test.
- In a standalone editor-game run of A, all four loaded quadrants were exercised, NE was fully unloaded, and its interior ray hit nothing while a neighboring region still supported collision. Re-adding the same level package restored the sampled height and normal. Across 242 pairs 20 cm apart straddling the two core axes, maximum total elevation difference was 11.26 cm on sloping ground and minimum collision-normal dot product was 0.9912. These differences include the natural terrain gradient. The captured LOD comparison was inspected separately; no open crack was apparent at the tested viewpoint.
- Isolated generation and sampling of all regions took 9.2–10.8 s on the repeat pass, with peak Python working sets of 375–422 MiB. Independent NE generation took 3.7–5.7 s. The three static editor-game runs at 1440 x 810 / DX11 were capped at 60 fps; p95 frame time was approximately 16.67 ms, with peak process memory of 1.48–2.61 GiB. Screenshot capture time during offline motion is reported separately.
- Rechecked ten earlier pinned M2.1 configurations, four M22 fixtures and the M23 reference meshes. The review uses manually controlled streaming sublevels. World Partition, packaged-build traversal, physics of a moving train and a production performance budget require their own tests.

The candidate corridor in A is 624 m long. Its proposed grade is +1.5%. The existing Railway spline, mesh builder and loaded-track GUID registry were inspected. Actual track placement and train traversal await review.
