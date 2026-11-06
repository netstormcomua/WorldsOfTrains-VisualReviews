# M27.3 R3 — D2 tested foundation, with known limitations

Status: iteration closed for review and further scene work. This is not a claim of full photorealism or final artistic approval. The selected foundation is **LightDust1**, with the existing D2 composition, Hybrid Sand v2 and playable DX11 baseline.

## Review material

| Material | File |
|---|---|
| Light dust off / on, matched camera and time | [01-light-dust-off-on.jpg](01-light-dust-off-on.jpg) |
| Cloud profile before / after, dust disabled | [02-cloud-profile-before-after.jpg](02-cloud-profile-before-after.jpg) |
| Actual moving-train frame | [03-train-view.jpg](03-train-view.jpg) |
| Unresolved rail moire: diagnostic crops | [04-rail-known-limitation.jpg](04-rail-known-limitation.jpg) |
| Low camera: dust and ground contact | [05-dust-contact.jpg](05-dust-contact.jpg) |
| Continuous actual train pass, 36 seconds, silent | [train-pass.mp4](train-pass.mp4) |
| Selected parameters | [parameters.json](parameters.json) |
| Technical results | [measurements.json](measurements.json) |

All images are actual Unreal captures or labeled comparisons/crops. Collage gutters are separators, not terrain cuts. No generative retouching. The rail image compares native 100%, diagnostic 200% and a 110% TAA experiment; neither experiment was adopted as a solution.

## What changed

- An owned cloud-material profile removes the horizontal cloud strata seen in the matched control. Only the cloud-type vector changed from (1.5,0,0,0) to (1,1,1,2). Clouds are now smaller separated masses. Source material remains preserved.
- LightDust1 adds very delicate, irregular low drifting dust and occasional small grains. It preserves train, dune and sky readability. This is translucent particle approximation, **not participating volumetric scattering**.
- Particle materials were saved explicitly and their visible square atlas edges were softened with a zero-edge mask. Earlier invalid black-plane captures are excluded.
- The existing composition and working railway/gameplay were retained. No further dune-shape or rail-LOD redesign was performed.

## Visual assessment and remaining limitations

The cloud band is absent in the inspected matching views. Large square particles were not visible in the selected native frames. Dust is intentionally subtle and is more legible in motion than in the wide still image; its artistic strength remains open for review.

Mid-distance rail moire remains visible in native images. It also survives a correctly overridden matte-material control and a no-shadows control. Sampling changes its pattern but did not establish a satisfactory fix. Exact duplicate source-mesh faces were not found, but near overlaps are not ruled out. A geometry/sampling contribution is plausible, not conclusively isolated. This is a **nonblocking backlog item** for this iteration. Source rails, gauge, spline topology and gameplay remain unchanged.

Exact surface streams and crest releases are deferred. A bounded attempt to reuse stock UDS dust was not completed successfully; it is **not** the selected or tested weather preset. No claim is made that a remembered historical storm was recovered.

## Technical validation

Saved and reopened level; deterministic preset regeneration; 747 saved particles, one cloud actor, no duplicate generated content; materials resolve. 38 non-wind actor transforms/classes/labels and 57 protected files remain unchanged. Authoritative railway samples and length match, and this map's track GUIDs remain stable on regeneration.

96 sampled collision/path checks: maximum height discrepancy 0.00691 m. Minimum sampled dust-path horizontal distance from rail: 16.0656 m. Particles have no collision. These are sampled checks, not a proof covering every possible terrain location.

Actual train run: **511.09 m in 51.44 s**, junction crossing, exit and reset passed. Maximum measured wheel residual: 0.00452 cm. DX11, Nanite off, native clock, screen percentage 100, 1440 x 810, 60 fps cap.

| Measured game frame time | Result |
|---|---:|
| p95 | 16.667 ms |
| p99 | 17.066 ms |
| Maximum | 39.319 ms |
| Peak process RAM | 3309 MiB |

This was **Editor-game, not a packaged-build acceptance run**. Audio was not revalidated; the review video is silent. A single matched static dust off/on pair produced GPU p95 13.212/13.184 ms and mean frame 13.005/13.029 ms: within noise of this pair, not proof of universally zero cost.

## Capture and performance caveats

The video is a continuous trim of source capture frames 420–1499 (14–50 seconds of a 50-second recording), 1080 encoded frames at 30 fps. No retiming or interpolation. Full source capture contained 1444 source updates and 56 held frames among 1500 encoded frames. Capture cadence is separate from the 3083 game frame-time samples.

Earlier no-record tracing reproduced approximately 302/244/199 ms stalls involving Present/render waiting and Slate operations. Recording is therefore not a necessary trigger. Earlier 634/1571 ms freezes were not reproduced or explained. The latest run's lower maximum does **not** prove they are fixed.

Read-only system telemetry showed memory pressure/page-ins, but its 1-second sampling cannot establish causality for individual frame spikes. Changing scene/memory conditions are confounders. No user applications were closed to improve the measurement.

## Reproduction and next actions

Use the saved LightDust1 demo, its seed 27334 and fixed WindWide / DustContact cameras; reload resets the native clock. LightDustOff1 is the matched no-dust control. Baked terrain samples must be regenerated after changing terrain or dust trajectories.

Recommended next step: review this playable foundation and proceed with the wider scene plan and reusable constructors after approval, rather than another isolated dust-polish cycle. Rail moire, intermittent stalls and the incomplete UDS experiment remain documented backlog items. No larger world, additional biome or rail expansion is included in this revision.
