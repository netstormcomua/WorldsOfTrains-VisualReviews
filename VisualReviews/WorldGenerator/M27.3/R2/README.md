# M27.3 — D2 revision 2

5 November 2026. Technical and visual review candidate; **artistic approval is pending**. This is a refinement of the existing D2 test, not a larger world. Images are actual Unreal DX11 captures. No generated concept artwork, retouching or source assets are included.

## Review material

| Material | File |
|---|---|
| Geometry before/after, identical material and daylight | [01-geometry.jpg](01-geometry.jpg) |
| R1 versus R2 presentation, identical cameras | [02-final-comparison.jpg](02-final-comparison.jpg) |
| Terrain / dust / clouds / combined ablation | [03-atmosphere-ablation.jpg](03-atmosphere-ablation.jpg) |
| Fixed camera at two weather phases | [04-weather-phases.jpg](04-weather-phases.jpg) |
| Representative Mammoth view | [05-train-view.jpg](05-train-view.jpg) |
| Actual real-time train traversal, 45 seconds, silent | [train-pass.mp4](train-pass.mp4) |
| Measurements | [measurements.json](measurements.json) |
| Version pins, seeds and weather settings | [parameters.json](parameters.json) |

Judge connected shoulders and saddles in image 1 independently of atmospheric presentation. Image 3 isolates the weather layers. Image 4 shows evolution over 60 seconds, not a geometry change. Comparison panels have a gutter; their boundary is not a terrain cliff.

## Changes and visual assessment

- New explicit composition adapter `field-m27.3.2`, reusing pinned `field-m27.3`, `m24.1` and Single Dune `m23.1`. The Single Dune algorithm was not rewritten. Twenty-two existing dune instances and ten secondary ribbons remain; eight main profiles and existing secondary slots were adjusted instead of adding repeated rows.
- Crest height, bend, skew, length, saddles and sheltered secondary placement vary more. A strong first draft was rejected. The selected recipe blends 55% of the new height contribution into the R1 baseline, with two local smoothing passes on the existing 1 m grid. The principal change is the connected middle-distance saddle, visible in Across. Opening remains deliberately close to the previous large silhouette.
- Five uneven sand deposits approach the track shoulders. Maximum addition is 13.28 cm; the inner 3.5 m corridor remains numerically unchanged. This is subtle at train distance. Screen-space contact shadows were rejected because they introduced dark jagged terrain artifacts; train source materials were not edited.
- Local fog volumes replace translucent dust cards, whose rectangular edges were visible against fog. A shared deterministic wind controller moves/fades ground and crest parcels, with local ground sampling. Two valley pockets provide the clearly visible suspended-sand effect. Final near-ground density was reduced after motion review.
- A new moving cloud layer and matching projected light-function mask use the same wind clock. The mask has slightly stronger attenuation and narrower transitions than R1. A warmer lower-hemisphere sky capture adds some fill without Lumen. The Mammoth's deepest cavities remain dark.

**Strengths:** stronger connected intermediate forms without noisy erosion; preserved broad valleys; additional atmospheric separation; coherent sky movement; playable train traversal retained.

**Remaining limitations:** some forms still resemble smooth hills from certain directions; the outer landscape remains a test backdrop. The cloud plane is an inexpensive approximation, not volumetric cloud simulation. Ground skimming/spindrift and tiny near-camera motes exist in the prototype but are not yet consistently legible as convincing wind-blown sand. Valley haze is the reliable visible result. Dark blurred marks near the moving train are also present in the earlier R1 traversal; their source was not isolated in this pass. Do not attribute their removal to R2. This review does not certify photorealism or production readiness.

## Validation

- Approximately 1008 × 1008 m core, four new 1 m Landscape regions, twenty-four Landscape actors including the existing outer context. No global resolution increase.
- Full versus tiled generation, repeated subregion generation and pinned input hashes pass. A local secondary-ridge edit changes 19,018 samples in NW; local regeneration exactly matches full regeneration, with three unaffected tiles unchanged.
- Heightfield preparation and checks took approximately 28.24 seconds. Geometry delta from R1 is −18.67 to +12.42 m; 99th-percentile slope is 34.54°. The 12 m protected railway corridor and seven camera feet remain exact in the generated geometry.
- Four stage maps saved/reopened. Four core Landscapes per stage, seven unchanged cameras and unchanged Hybrid Sand v2 material/daylight settings. Weather stages are opt-in and replace their own tagged actors when authored.
- 264 railway terrain probes per stage: maximum collision-height difference from baseline 0.366 cm; minimum surveyed railhead-to-terrain clearance 71.29 cm. These measurements protect the existing rail bed; they are not a claim of perfect sleeper-level visual contact.
- 162 component-boundary probe pairs: minimum adjacent normal dot 0.99349. Maximum height change across the 20 cm probe span is 10.21 cm on a slope, not a seam gap. Twenty-eight heightfield/collision samples per map: maximum error 0.039 cm.
- Fifty-seven protected prior files match their snapshots; a separate ten-file older package check also passes. Existing game systems and approved generator versions were preserved.
- Actual real-time railway runs cover approximately 511 m in 51.45 seconds, peak speed 9.52 m/s, junction crossing, exit and reset. Maximum wheel-height residual is approximately 0.0046 cm. No fixed simulation step or screenshot capture in the performance runs.

## DX11 performance and temporal investigation

RTX 2060 Max-Q, 1440 × 810 output, existing DX11 raster baseline. Tests at a 60 FPS cap are frame-pacing tests; capped GPU timers must not be interpreted as pure rendering work.

| Controlled series | p99 frame time | Highest observed frame | GPU temperature |
|---|---:|---:|---:|
| R1 baseline, two runs | 16.668–16.673 ms | 30.91 ms | 64–71 °C |
| R2, two initial runs | 16.671–16.673 ms | 35.75 ms | 68–73 °C |
| R2 with experimental AA, two initial runs | 16.667–16.668 ms | 37.18 ms | 70–74 °C |
| Final softened dust, standard / experimental AA | 16.674 / 16.675 ms | 34.87 / 47.36 ms | 85 / 86 °C |

The first six runs reported no thermal slowdown. The later AA run reported a thermal-limit flag in 3.09% of sampled intervals. Recurrent isolated spikes occur around 41 seconds / 410 m; the cause is not isolated. Peak game RAM across these non-recording tests is approximately 2.31–3.16 GiB. Temperature and clock variation remain a real limitation; stable p99 does not mean zero hitching.

At fixed C2, uncapped settled GPU medians were 4.20 ms for terrain/contact, 4.71 ms for dust only, 4.69 ms for clouds only and 4.82 ms for the combined final. These are short scene observations with varying GPU clocks, not additive per-effect microbenchmarks.

An optional capture preset uses 110% screen percentage, TAA frame weight 0.06, 16 samples and filter size 1.05. It was tested in real movement and remains optional. A motion-compensated video residual probe was inconclusive at its compression/detail floor; no quantitative reduction of flicker is claimed. The project-wide 100% playable default is unchanged. Reflective train edges and grazing sand detail still deserve evaluation on the user's display.

## Video evidence and repeatability

The public clip captures only the Unreal window through Windows Graphics Capture, not the desktop. Desktop captures with other windows overlapping were rejected and remain private. This capture method follows the [Windows Capture documentation](https://github.com/NiiightmareXD/windows-capture/tree/main/windows-capture-python).

The clip is 45 seconds at 30 FPS, 1280 × 720, using the optional AA preset. The source delivered 1,339 distinct capture updates; 11 frame slots hold the previous image to preserve elapsed time. There is no frame interpolation or simulation time acceleration. The window border was cropped; no terrain/image defect was retouched. Video encoding and recording are excluded from the performance table. The video is silent; audio was not re-evaluated in this visual revision.

Stage maps, versioned recipes, input hashes, camera rig and fixed weather phases are retained locally for reshooting. Demonstrations: geometry-only versus weather; wind strength/phase changes in the opt-in actor; the existing train pass followed by exit/reset. General scene-selection UI is outside this revision.

## Recommendation

Review R2's connected saddle and localized haze against R1. Keep standard DX11 as the playable baseline; retain the AA option for capture until display-level motion review confirms its benefit. Do not treat the fine wind effects or thermal investigation as fully solved. Stop here for artistic feedback before any larger terrain or biome work.
