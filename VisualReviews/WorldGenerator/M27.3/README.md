# M27.3 — Terrain-aware dune composition

4 November 2026. Prepared for artistic review. Recommended composition **B**. Artistic approval remains with Anton.

## Review materials

| Material | File |
|---|---|
| Reference and three compositions | [Aerial and valley comparison](01-compositions.jpg) |
| Middle-distance geometry | [Matched gameplay cameras](02-middle-distance.jpg) |
| Clouds, local dust and warm ground illumination | [Controlled layer comparison](03-layers.jpg) |
| Train underside and moving cloud shadow | [Detail comparison](04-light-and-motion.jpg) |
| Selected B with clouds and warm ground illumination | [Valley image](selected-valley.jpg) |
| Actual train motion, selected presentation | [5-second video](selected-train.mp4) |
| Original M27.2 versus B, original daylight | [Matched train passes](shape-train-comparison.mp4) |
| Clear / cloud / cloud+dust / warm hemisphere | [Four matched train passes](layers-train-comparison.mp4) |
| Technical measurements | [JSON](measurements.json) |

All scene images originate from Unreal DX11 captures. Collages resize and label the captures. Movies contain 120 actual simulated train frames over 67.54 m at fixed 24 Hz, without audio. They illustrate motion and image continuity. Real-time performance is measured separately.

## Composition and reference assessment

The existing photographic board shows connected sand shoulders, discontinuous smaller crests and unequal open valleys. M27.2 has comparatively isolated crescents, repeated satellite spacing and similarly rounded middle-distance profiles. The new pass changes the composition layer while preserving the approved sand material and underlying Single Dune implementation. The original reference board and licensing information remain in the [M27.2 review](../M27.2/README.md).

**A** replaces isolated satellites with interrupted secondary ridges while retaining the primary masses. Some openings improve considerably, but the established rail-side cameras change only slightly.

**B** connects broader shoulders and shorter crests into compound masses. The C2 camera gains a visible saddle and a second layer of terrain. Across the track, the slope has a more varied continuous crest. This is the strongest candidate for the next approved integration.

**C** offsets primary masses and alternates heights more strongly. It creates deeper variation in the aerial view, but some near formations become solid walls and several small endings remain conspicuous. Its strongest changes are less consistently useful along the route.

The inspected views still reveal overly smooth primary silhouettes, horizontal surface bands near the track and some recognizable repeated crest shapes. The aerial composition remains more arranged than a continuous natural sand sea. B is an improvement candidate with these limitations.

## Versioned geometry

The new `field-m27.3` composition version uses the pinned `m24.1` field and `m23.1` Single Dune implementation. It replaces ten existing satellite slots with variable-height curved sand ridges, retaining 22 reusable single-dune instances. All alternatives use the same 32 feature slots. Saved recipes record explicit shapes and seeds, generated from layout seeds 27301, 27302 and 27303.

Secondary ridge relief is approximately 4–15 m, with variable curvature, crown height, asymmetry, smooth taper and bounded interruptions. Low transition shoulders supply smaller geometric relief. Existing Hybrid Sand v2 normals provide fine ripples. B ridge lengths span 101.7–197.75 m. The algorithm samples the shared smooth substrate and moderates new deposits on steep underlying slopes. A compact blending operation integrates overlapping masses. A bounded slope-relaxation pass removes steep new tips while preserving protected terrain.

The D2 core remains 1008 × 1008 m at 1 m spacing. Composition differences taper into the existing outer landscape. The original railway corridor is byte-identical within 32 m of its surveyed path, with a gradual transition outside it. Existing railway topology and gameplay remain authoritative.

| Check | Result |
|---|---|
| Full output versus independently generated tiles | Exact R16 equality for A/B/C |
| Repeated cross-boundary window | Exact equality for A/B/C |
| NW ridge edit and local regeneration | Equal to full regeneration, other three tiles byte-identical |
| B local edit extent | 16,879 changed samples |
| Unknown configuration/implementation versions | Rejected |
| Previous pinned field/terrain fixtures | Three regression cases pass, m23.1 implementation hash retained |
| Original source packages | Ten protected M27.2 package hashes match |
| Reopened map comparison | Seven cameras, daylight and sand material match across alternatives |
| Landscape collision | 28 lattice probes per map, A/B/C error below 0.046 cm |
| Railway terrain probes | 264 per map, bed deviation below 0.019 cm |
| Boundary probes | 162 pairs per map, normal dot at least 0.9935 for A/B/C |
| Actual train checks | A/B/C complete approximately 513.65 m, junction, stop, exit and reset |

Boundary height differences measured across 20 cm are up to 11.32 cm on sloping surfaces. This is a finite-distance slope measurement. Exact shared-edge R16 samples and the visual inspection provide the separate continuity checks. No new boundary cut or floating sand formation was observed in the selected views. Probe coverage is finite.

Maximum sampled slopes are approximately 43.5° for B and 52.2° for C, compared with 55.2° in the inherited reference. These are steep blended/local features and remain a limitation for physically realistic unconsolidated sand. Composition displacement against M27.2 reaches −20.77/+25.07 m for B because primary masses also move and widen. This exceeds the relief of an individual secondary ridge.

An initial automated exit check requested exit while still moving too quickly. The QA driver now waits until nearly stopped and verifies on-foot status. Final tests pass at zero exit speed. Gameplay exit rules were preserved.

## Comparable cameras and motion

Original M27.2 cameras are retained, with two additional fixed cameras chosen where all alternatives have nearly equal ground height. Opening and Shoulder are approximately 4.5 m above ground, with less than 0.16 m terrain variation across variants. C2 and Across provide matched gameplay comparisons. B2 is the existing lower train camera. An auxiliary Wide camera ends about 15.2 m above C's changed terrain and is treated as an elevated diagnostic, excluded from the published gameplay comparison.

Sequential samples from the real train passes show continuous travel and coherent silhouettes. The full source sequences remain available locally. Fine rail/ripple shimmer and subtle temporal effects require longer interactive viewing, and the short fixed-step captures do not establish frame-pacing stability.

## Optional atmosphere and Mammoth illumination

After the fixed-daylight comparison, B was tested with a slow cloud layer, broad sunlight modulation, two low local dust volumes and warm ground illumination as separate experiments.

- Clouds use a low-cost planar layer at 760 m and a corresponding directional light function, moving at 3.1/1.3 m/s with maximum sunlight attenuation of 22%. The 36/96 second comparison demonstrates gradual motion. Skyward views can reveal the flat, painterly cloud representation.
- Dust uses two shallow local fog volumes. It leaves silhouettes readable, but its contribution is weak in these views. The selected presentation omits it.
- A warm lower-hemisphere Skylight value slightly lifts Mammoth's underside. It changes scene illumination, preserves source train materials and creates no additional shadow-casting light. It is an artistic approximation of ground bounce. Deep wheel contact areas remain dark.
- The selected presentation combines B, slow clouds and warm ground illumination. Original-light B remains the composition comparison candidate.

## DX11 performance

Repeated controlled camera runs used the same resolution and settings, plus GPU temperature, clocks and throttle flags. Camera order was also reversed. The following values are GPU p95 milliseconds from the B2 view, followed by the approximate sampled GPU clock.

| Scene | First layer review | Repeated review |
|---|---|---|
| Clear B | 5.59 ms / 1395 MHz | 8.83 ms / 1155 MHz |
| Clouds | 5.81 ms / 1350 MHz | 6.06 ms / 1275 MHz |
| Clouds + dust | 6.00 ms / 1290 MHz | 5.97 ms / 1305 MHz |
| Warm hemisphere | 8.18 ms / 1365 MHz | 6.20 ms / 1365 MHz |
| Selected presentation | 7.26 ms / 975 MHz | 5.93 ms / 1320 MHz |

At 86–87 °C several runs report active thermal slowdown and clocks near 975 MHz. Other runs report active power limits. This explains part of the variability, but does not explain every spike. Mixed-view whole-run p95 ranges roughly 5.7–17.3 ms. These runs do not isolate a reliable causal overhead for each atmosphere layer. A stable-clock, thermally controlled comparison remains required before claiming a production performance budget.

The review runs peak around 3.0 GiB process memory and 0.84–0.90 GiB sampled process-dedicated GPU memory. The latter is the WDDM process counter, not total GPU occupancy. The verified B gameplay run reaches about 3.15 GiB process memory. Software Lumen remains optional and was not used in this baseline.

## Requested decision

Evaluate B's compound shoulders, valley opening and middle-distance depth against the original daylight reference. Separately evaluate whether the cloud layer and warm underside illumination improve the scene enough to retain. Full photographic realism and a stable production performance budget remain open. Development stops here for artistic review.
