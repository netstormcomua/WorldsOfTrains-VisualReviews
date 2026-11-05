# M27.3 R1 — Remove inherited terrain bands and verify real-time travel

5 November 2026. A focused correction to composition B, prepared for artistic review. This is an addendum to the [three-composition M27.3 review](../README.md), not an expansion of the world.

## Review materials

| Material | Link |
|---|---|
| Published B versus corrected B, identical cameras | [Before / after](01-before-after.jpg) |
| Uniform matte material, identical lighting | [Geometry diagnosis](02-geometry-diagnosis.jpg) |
| Clouds and warm lower-hemisphere illumination | [Presentation comparison](03-presentation.jpg) |
| Selected frames from the real-time journey | [Traversal contact sheet](04-realtime-traversal.jpg) |
| Actual moving train, 45 seconds | [Real-time video](train-realtime.mp4) |
| Measurements | [Geometry, collision and performance](measurements.json) |
| Video integrity | [Recording validation](recording-validation.json) |

All images come from Unreal. Only resize, labels, video compression and removal of an 8-pixel window border were applied. The video has no audio. GitHub may download MP4 rather than play it inline.

## Diagnosis and correction

The broad parallel light bands were present with a uniform matte material. Their source was an inherited periodic height contribution from the earlier mid-scale sand pass, rather than Hybrid Sand v2 alone. This contribution reached 0.40625 m in the inherited heightfield and created repetitive shallow waves with roughly 20 m spacing.

The new explicit layer **secondary-sand-m27.3.1** retains 10% of that inherited contribution away from the track. It preserves the inner 8 m railway protection zone exactly and blends the correction smoothly over the following 6 m. The maximum actual height change is 0.349609375 m. Composition **field-m27.3 / B**, its larger connected ridges, and Single Dune **m23.1** remain pinned. Hybrid Sand v2, daylight and cameras remain unchanged. Existing maps and source assets are preserved.

In the fixed matte Across image, row-luminance contrast in the measured foreground strip fell from 2.296 to 0.299 grayscale levels, approximately **87%**. This is a diagnostic for this specific banded image region, not a general realism score. Fine material ripples and some weak geometric undulation remain visible.

## Technical validation

| Check | Result |
|---|---|
| Repeated generation | Exact R16 equality |
| Independent local-region evaluation versus full output | Exact equality |
| Protected 8 m rail zone and outer boundary | Exact preserved samples |
| Saved / reopened maps | Clean and Final, seven matched cameras |
| Landscape core | Four generated core regions per map; no extra preview geometry |
| Rail terrain sampling | 264 probes per map; maximum bed change 0.00835 cm |
| Landscape collision | 28 vertex probes per map; maximum height error 0.04865 cm |
| Boundary normal comparison | 162 pairs per map; minimum normal dot 0.99342 |
| Earlier content | Ten M27.2 package hashes and 26 protected previously published inputs unchanged |
| Train gameplay | Approximately 511 m, spline junction, wheel bindings, zero-speed exit and reset pass |

The boundary probe height difference reaches 10.86 cm across a 20 cm horizontal separation on a slope. That is a finite-distance slope measurement, not a measured gap. Shared-edge equality and inspected rendered views provide the separate continuity evidence. Probe coverage is finite.

## Real-time DX11 performance

Four scenes were tested twice, in forward and reverse order. Each measured interval lasts approximately **51.45 seconds**, with about 3,086 frames. Resolution is 1440 × 810, screen percentage 100%, VSync disabled, frame cap 60. The gameplay QA uses variable real time with **no synchronous PNG capture**. A separate visible-window recording was made afterward.

| Scene | p99 first / repeat, ms | Worst frame first / repeat, ms | Peak GPU temperature first / repeat |
|---|---:|---:|---:|
| M27.2 reference | 16.670 / 16.715 | 27.407 / 30.422 | 65 / 80 °C |
| Published M27.3 B | 16.673 / 16.990 | 26.991 / 31.206 | 66 / 77 °C |
| Corrected B | 16.671 / 17.153 | 27.596 / 34.478 | 67 / 77 °C |
| Corrected presentation | 16.674 / 17.367 | 28.758 / 34.692 | 69 / 74 °C |

Frame p50 is approximately 16.667 ms in every run; p95 stays at or below 16.673 ms. Each unrecorded run has one frame above 25 ms. The repeated Clean and Final runs each have one frame above 33.333 ms. Process peak RAM is approximately 3.1–3.2 GiB.

GPU sensors were sampled every 0.5 seconds. No active thermal-slowdown flags were observed in these runs. Median graphics clocks for Base/Published/Clean were approximately 1035–1050 MHz; Final was 1095–1110 MHz. Power-limit events and temperature differences remain in the raw measurements. Cooling and clock controls were not changed.

These results support a stable **60 FPS budget in this test**, with rare remaining spikes. They do not isolate the exact uncapped GPU cost of the correction or presentation layers. Temperature distributions differed, and engine RHI GPU-frame counters under a frame cap are not treated as pure shader execution time. The earlier 86–87 °C thermal slowdown remains a real observation from the prior test series.

## Recording and temporal observations

An initial GDI window-capture method produced stale or unevenly updated imagery and was rejected. The published video uses desktop duplication of the actual visible game region. It preserves variable capture timestamps: 2,652 decoded frames over 45 seconds, approximately 58.91 FPS, with no exactly identical adjacent decoded frames. The separate game's recorded run has p99 16.673 ms. Capture cadence and game frame time are different measurements.

Overview samples and consecutive frame crops were inspected. Terrain moves continuously relative to the train; no abrupt terrain pop, floating sand or new seam was observed in those samples. Broad cloud lighting changes remain gradual. Small rail highlights and the dune-shadow edge still have fine aliasing, and compression limits the assessment of subtle sand shimmer. This is not a claim that every temporal artifact has been eliminated or that the complete video was reviewed in real-time playback.

## Remaining artistic limitations and decision

The corrected B is the recommended replacement for the banded B presentation. The foreground-to-middle-distance transition is substantially quieter, while the large dune composition remains comparable.

The large silhouettes can still look too smooth; some ridge profiles remain conspicuously shaped, and the abrupt crest segment at the right of the Opening view remains visible. The cloud sheet is an inexpensive approximation, and dark train contact areas remain dark. No complete photorealism or production readiness is claimed.

Please evaluate the Across improvement, continuity during the train journey, the remaining crest shapes and the presentation lighting. Stop here for artistic review; no map expansion, new biome or Railway rewrite is included.
