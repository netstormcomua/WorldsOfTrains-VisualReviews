# M27.1 | Desert look development on the D2 railway

**Daylight is the recommended reference for the next review.** It separates the slip faces and brings detail back to the shaded Mammoth body. Warm light is useful for a lower, more dramatic crest shot. The pitch of the ripples now changes and their fronts split and fade in patches. The horizon treatment removes the dark wedge visible behind the right shoulder in the reference camera. A horizontal atmospheric gradient is still visible in open views.

| Controlled Unreal evidence | What to inspect |
|---|---|
| [Original D2 and final daylight corridor](01-before-after.jpg) | Same gameplay height, train and elevated composition |
| [Sand alone](02-surface.jpg) | Compare the 72 cm view and the same foreground crop under the original light |
| [Single-change controls](03-isolated.jpg) | Reference, surface, daylight illumination, and atmosphere with distant terrain |
| [Day and warm presets](04-day-warm.jpg) | Same locomotive, crest and horizon in two lighting conditions |
| [Reversible track pass](05-railbed.jpg) | The same sleepers and adjacent sand with and without shoulder treatment and top dust |
| [Distant edge before and after](06-horizon.jpg) | Same horizon and same crop, including the previously dark wedge |
| [Five-second moving Mammoth](moving-mammoth.mp4) | 120 consecutive Unreal game frames at a fixed 24 simulation steps/s, silent |

## What changed

The versioned sand material uses broad colour and flow variation, wind-oriented patchy ripple normals, fine Rocky Desert texture inputs and granular roughness. The first material pass made regular parallel ridges and overly pale patches. The selected version uses two bending, partially merging ripple patterns and a narrower mineral colour range. Fine relief fades before becoming subpixel. At long distances a cheaper path retains the broad colour variation. [Surface contract, photographic references and lighting settings](surface-and-light.md)

Seven fixed cameras were captured on the reference world before editing. Original D2 packages and the source Rocky Desert sand packages were checked by hash. Camera transforms, FOV and manual exposure matched across all seven comparison worlds. Thirty collision samples per world agreed with the original terrain. Existing core dune geometry provided enough slope and crest variation for this look test. Additional 64 × 64 outer patches carry distant low ridges beyond the old edge. The atmosphere-only pass includes those patches, Sky Atmosphere and exponential haze.

For the corridor, a material instance binds a distance field derived from the surveyed spline. Compact, broken deposition between roughly 3.5 and 9 m from its centre softens the sand shoulder. A separate track instance uses the original PBR atlas and a patch mask on upward-facing, less metallic surfaces for dust near the sleepers. The fixed crop shows the change in colour while the rail and sleeper silhouettes stay visible. The edge of the underlying railway mesh still reads as a straight manufactured strip. This pass has no displaced sand, physical ballast stones or wheel-clearance correction.

## Limits and review decision

The middle ground reads more clearly, but near sand still has patches of soft detail and some similarly oriented ripple runs. The daylight slopes are quite pale, and the warm preset can lose separation on the locomotive's underside. Evaluate the moving shot as well as the stills before adopting the material elsewhere. These are editor-game captures on the short existing route. Long-distance temporal stability, packaged performance and the response under other biomes or weather remain to be evaluated.

## Rendering measurements

DX11 / SM5, RTX 2060 Max-Q 6 GB, 1440 × 810, 100% screen percentage, VSync off and uncapped. GPU p95 uses RHI frame cycles for settled intervals across seven cameras, excluding screenshot requests. Peak dedicated GPU allocation was sampled from Windows' per-process GPU counters at about four-second intervals. It can miss short spikes. Process working set and dedicated GPU allocation describe different memory pools.

| Stage | GPU p95 (ms) | Peak dedicated GPU (MiB) | Peak process RAM (MiB) |
|---|---:|---:|---:|
| Original D2 | 7.56 | 602 | 2,794 |
| Sand alone | 21.52 | 602 | 3,022 |
| Light alone | 23.55 | 797 | 2,951 |
| Air and horizon alone | 23.79 | 602 | 3,025 |
| Combined daylight | 6.13 | 699 | 2,957 |
| Combined warm | 15.87 | 798 | 2,949 |
| Final daylight with track dust | 6.79 | 746 | 2,984 |

Fresh launches showed substantial variability. A second baseline run measured 8.22 ms, daylight 16.00 ms, and warm 14.83 ms. The optimized corridor before the last track-dust adjustment measured 6.41 and 5.96 ms. The measured pass supports trying the final daylight map on this machine, but does not establish a general speedup. In particular, single-change stage costs cannot be added together. No packaged or DX12 comparison was run.

Unreal's DX11 representative shader statistics for the core material gave 1,121 pixel instructions and six samplers for the original, versus 454 and eight for the new sand and corridor instances. The representative vertex count was 136 in each case. Separately compiling just the custom surface evaluation with the SM5 compiler gave 115 instruction slots / seven sample opcodes for ordinary sand and 155 / eight for the corridor specialization. The full representative shader, standalone surface and per-frame GPU times measure different costs.

The final train boarded, crossed the two-spline connection, covered 513.66 m, stopped, exited and reset on the 624.37 m alignment. The continuous five-second clip covers 67.54 m of actual simulated motion. [Machine-readable measurements](measurements.json)
