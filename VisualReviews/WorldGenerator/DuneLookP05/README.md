# Dune surfaces from the moving train
Thirteen surfaces were rendered on the same western dune field, using the saved Small rail, Mammoth, camera, directional light and terrain. Each ID has two separate images: a close render of the surface on a real dune and a game frame sampled six seconds into a real moving pass. The train starts at 2,570 m along Small; commanded speed is 11 m/s. The displayed moving frame is approximately 66 m beyond the start. A video frame represents about 0.37 m of travel. The fixed surface camera samples the same point for every ID.

00 is the original Hybrid Sand v2. 01 and 02 are RockyDesert Sand A and B using their own normals. 03 is a Poly Haven scan, 04 an ambientCG scan. 05–12 use seeded periodic textures. The normalized normal directions follow the wind. Two projections rotate slightly about it and use a translated second projection. Larger colour variations continue beyond the microtexture fade. Near and mid-distance differences depend on the material. The original terrain seed is 710650, the field is field-m27.3.2 and the saved sunlight rotation is pitch −49°, yaw 128°. The comparison uses DX11/SM5 at 1440 × 810 and a 60 fps cap.

[Rocky A and B surface samples](native-samples.jpg) · [Single labelled moving comparison](comparison.mp4)

The independent near-ground geometry control at the previous shore camera is documented in [the matched crop](triangles.jpg). Forcing maximum landscape detail on eight nearby components leaves the triangular patches visible. No channel in the compared crop changed by more than four 8-bit levels. This rules out a switch to a coarser LOD as a sufficient explanation. Material normals and the shape of the base terrain remain open.

One runtime state change applies each new material to all 1,152 components and reads back the effective textures and parameters. The first three variants were captured in one game load and the remaining ten in another. Across the original thirteen runs the train travelled 186.86–187.21 m per run. Each row reports an individual measured pass. The scene is retained for selection by the author.

Rocky B (02) adds mottling and fine grain in the near-to-middle foreground. Sinuous (08) keeps readable curving crests. MegaRipples (12) has the strongest wide, repeating folds; Forks (09) also shows regular repetition. Ground055L (04) is clearer in the separate sample than in the moving train view. The first 12 run gave frame/GPU p95 of 38.34/39.16 ms. A second isolated captured pass on the same route measured 17.73/22.98 ms. The initial spike did not repeat, and its cause remains unresolved. Reference 00 was 17.83/21.97 ms. The game-material and wind-direction controls are retained for review.


| ID | Surface | Train camera | Surface sample | Frame / GPU p95 (ms) |
|---|---|---|---|---|
| 00 | Hybrid | [View](views/00.jpg) | [Sample](views/00-sample.jpg) | 17.83 / 21.97 |
| 01 | RockyA | [View](views/01.jpg) | [Sample](views/01-sample.jpg) | 17.92 / 21.52 |
| 02 | RockyB | [View](views/02.jpg) | [Sample](views/02-sample.jpg) | 18.42 / 21.96 |
| 03 | sand_03 | [View](views/03.jpg) | [Sample](views/03-sample.jpg) | 18.55 / 22.32 |
| 04 | Ground055L | [View](views/04.jpg) | [Sample](views/04-sample.jpg) | 18.42 / 21.87 |
| 05 | WindScours | [View](views/05.jpg) | [Sample](views/05-sample.jpg) | 17.79 / 22.35 |
| 06 | Capillary | [View](views/06.jpg) | [Sample](views/06-sample.jpg) | 18.40 / 22.90 |
| 07 | LeeCrests | [View](views/07.jpg) | [Sample](views/07-sample.jpg) | 18.08 / 23.20 |
| 08 | Sinuous | [View](views/08.jpg) | [Sample](views/08-sample.jpg) | 18.13 / 22.59 |
| 09 | Forks | [View](views/09.jpg) | [Sample](views/09-sample.jpg) | 17.73 / 22.45 |
| 10 | Interference | [View](views/10.jpg) | [Sample](views/10-sample.jpg) | 17.72 / 22.70 |
| 11 | SlipTongues | [View](views/11.jpg) | [Sample](views/11-sample.jpg) | 19.38 / 25.02 |
| 12 | MegaRipples | [View](views/12.jpg) | [Sample](views/12-sample.jpg) | 38.34 / 39.16 |
