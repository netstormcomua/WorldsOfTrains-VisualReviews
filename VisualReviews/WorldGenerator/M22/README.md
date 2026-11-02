# M22 — taller single dunes, implementation m22.1

2026-11-02. Four new 24–50 m presets are ready for artistic review. This is an isolated morphology milestone, not approval of the desert biome. Existing m21.1 presets and field fixtures remain pinned and unchanged.

## Images to evaluate

| Material | Image |
| --- | --- |
| Four new dunes, identical cinematic overview | [A24 / B32 / C40 / D50](four-dunes.jpg) |
| Previous S4 and all new dunes, two fixed 4.5 m cameras | [Low-camera comparison](low-camera-comparison.jpg) |
| New shapes without sand detail or deep shadows | [Neutral top and side views](neutral-geometry.jpg) |
| Previous S4 versus C40; first versus revised A24 | [Before / after](before-after.jpg) |
| Actual native panel after UI generation | [Dune Lab UI](dune-lab-ui.jpg) |

All scene images are actual Unreal renders. Processing is limited to labels, uniform resizing and JPEG compression. Cameras, exposure and lighting are consistent within each comparison; no image relighting or retouching. The UI screenshot deliberately combines a neutral material with cinematic lighting to show that these controls are independent. A 2 m marker is present, although small in aerial views. PREV is the previous S4 formula evaluated on the same larger empty test grid, not a replacement of its original saved map.

## Geometry changes

- Height now drives horizontal growth: horizontal dimensions are reference dimensions at 20 m height, multiplied by `(height / 20)^0.85`. Old m21.1 dimensions retain their original literal meaning. This is a new version, not an automatic migration.
- Broad rising windward profile meets a steeper leeward face, with a narrow smooth crest fillet rather than broad grid smoothing. Curvature, bend count, bend amplitude, height variation, asymmetry and seed remain configurable.
- Crest height tapers in an arch toward the ends. Low ends retain a broader footprint and a longer toe, reducing the thin blade shape seen in the first iteration. No chaotic noise or aggressive erosion was added.
- A24 is compact and bowed; B32 has a longer sinuous crest; C40 has a stronger curved asymmetric form; D50 is the largest, gently undulating ridge. All retain a related family appearance; they are not four independent dune classes.

| Preset | Target / measured height | Effective width parameter | Maximum sampled slope |
| --- | --- | --- | --- |
| A24 | 24 / 23.81 m | 210 m | 35.14° |
| B32 | 32 / 31.87 m | 343 m | 36.72° |
| C40 | 40 / 39.85 m | 379 m | 33.52° |
| D50 | 50 / 49.82 m | 458 m | 36.68° |

Width is the generator's across-crest extent parameter, not a measured contour footprint. A 31° lee parameter does not cap the combined 3D slope: crest height changes contribute additional slope.

## Assessment and recommendation

**C40 is the recommended review candidate**, because its curved crest, unequal ends and clear lee face read best from the low leeward camera. Its height is more convincing than previous S4 without the overly wide mass of D50. This is a recommendation, not artistic approval.

A24 has smoother low endings than its first iteration, but its windward silhouette still reads as an ordinary rounded hill. B32 is useful for long ridges, though its low camera view remains broad and somewhat uniform. D50 gives the strongest scale impression, but fills much of the low-angle frame and still resembles B32 in overall morphology. C40's far end remains slightly pointed in some elevated views.

Remaining weaknesses: windward silhouettes are too smooth; crest variation is subtle from ground level; the neutral lighting is low contrast; cinematic sand is rather dark and brown; fine ripple repetition and the flat studio horizon remain. These images establish geometric differences, not a finished environment. Material overhaul and environmental composition were not part of this milestone.

## Technical validation

- Four deterministic presets, repeated generation exact; UI-generated float meshes match batch meshes exactly. New implementation hash and four mesh hashes are frozen as local regression fixtures.
- Ten prior M2.1 single/base-terrain/field fixtures match their previous R16 hashes exactly. Default field composition still selects m21.1. Unknown or mixed versions fail instead of silently upgrading.
- Explicit adoption was tested using the existing field compositor with `single_version=m22.1`, one B32 dune and the existing rolling substrate. Its contribution equals Single Dune output exactly, and repeated field output is identical. This is a numerical integration proof, not a newly authored or visually approved dune field.
- Ten isolated maps saved and reopened; one preview actor and one mesh section each. Two reapplications per map produced no duplicates. 169 collision traces per map, 1,690 total, passed; maximum discrepancy was below 0.001 cm at sampled vertices. This is not exhaustive collision validation between every vertex.
- Native Dune Lab generated all four presets, changed lighting independently, and saved a custom C40 preset with identical versioned configuration. The working Lab was saved separately. This is not an exhaustive mouse test of every parameter slider.
- 100 protected previous files remained byte-identical. Existing source materials, S01/S02 and gameplay were not authored by this task. The user's prior unsaved Lab state was saved separately before the authorized restart.

The Lab uses a procedural mesh sampled from the shared heightfield, **not a new Landscape actor**. Its area is now 504 × 504 m with unchanged 1 m spacing (505 × 505 samples), allowing large dunes without clipping their tails. No global Landscape resolution increase was made. Python calculation was approximately 0.21 seconds per new batch shape, excluding worker startup, mesh construction, collision and rendering. Ten settled DX11 static-camera captures measured p95 around 16.667 ms with a 60 fps cap; this does not establish uncapped performance, moving gameplay or packaged-build performance. Full measurements are in the technical results.

## Local refinement investigation

A 120 × 120 m crest patch was evaluated against a 0.25 m numerical reference. Interpolated 1 m sampling differed by at most 13.45 cm (99th percentile 1.10 cm); 0.5 m sampling reduced maximum error to 4.94 cm. This comparison uses separable interpolation and is not a measurement of every Unreal triangle. Minor close crest faceting remains possible. Local refinement was **not implemented**: at the review camera distances, overall silhouette/profile is the larger limitation. Reconsider a small crest patch only if close-up artistic review demands it, including seam and collision tests.

## Review decision

Please judge C40 against the previous S4, especially both 4.5 m views, and assess whether the remaining rounded windward profile needs another isolated revision. Do not treat greater height alone as a realism improvement. Stop here for artistic approval; no Railway, new biome, dune-group authoring or large-world generation was started.

See [parameters and camera poses](parameters.json), [technical results](technical-results.json), and [capture provenance](capture-provenance.json). This repository contains only selected review artifacts, not game source, Unreal packages, original assets or private logs.
