# Ten independent sandstone mountain experiments
The control and all ten alternatives use mesa 1.0, seed 81150, a fixed camera and directional light, and the native rock materials. Each starts from the same pinned control. The two 1.1 hybrids are separate combinations. All images are from Unreal. Read the comparison sheets left to right, starting with the control on each sheet.

| Trial | Visible result from the common camera |
| --- | --- |
| 01 · Group scales | Larger crowns raise and split the skyline. The separate courses remain conspicuous. |
| 02 · Joint offsets | Neighbouring faces break alignment. Overall mass changes little. |
| 03 · Exposed faces | Directed faces produce long vertical highlights on the front. The repeated directions are visible. |
| 04 · Bed horizons | Longer horizontal ledges become more legible. The front still reads as stacked stone. |
| 05 · Continuous shell | Fills recesses behind the existing blocks. Speckling in the ground near the foot limits this comparison. |
| 06 · Cross-cut gullies | Cuts break the top edge and introduce shadowed divisions. Selected for the reverse moving view. |
| 07 · Displaced beds | Sections shift relative to each other. Their full extent is difficult to read at this distance. |
| 08 · Spur and saddle | The lighter projecting shoulder extends the base on the left. Selected for the reverse moving view. |
| 09 · Differential weathering | Recesses darken below resistant courses. The distant silhouette stays close to the control. |
| 10 · Gully talus | Additional small rocks change the foot. They have little effect on the main face from this camera. |

The separate mesa hybrid has 224 native blocks and reaches 156.18 m. The towers have 135 and reach 245.53 m. All 359 native pieces cross the exported ground surface in the sampled mesh-vertex test. The continuous form removes much of the stacked-block appearance. Broad smooth slopes and straight tower walls remain apparent. Shell-only controls isolate the contribution of the sparse native outcrops.

The color control uses the visible SM_RockSide_A24 actor in the original RockyDesert Demo. Hiding only this actor removes part of the ledge. Its explicit component override and the mesh default resolve to the same MI_Side_Rock_A1. The warm Demo appearance survives restoring the default slot. The paired specimens in the study use identical orientation and uniform scale 1.75. No global color change was applied. These observations do not isolate a particular lighting or exposure setting.

One load of the factor map produced 13 fixed views. Frame intervals at the 95th percentile were 17.45–18.28 ms on this machine, over 100 frames per view at a 60 fps cap. The reverse clips use a moving camera on the opposite side. Full measurements are in checks.json. There is no matched timing for loading each variant separately. This is a technical study awaiting the author's artistic choice.

In reverse-06-08.mp4 the gullies (06) are on the left and the spur (08) on the right. Both recordings include actual motion. A dark regular pattern is visible on the hybrid walls in the opposite-side movement, particularly on the towers. The material on these faces still needs a close inspection. The 06 recorder produced 12.56 s of source footage. The paired clip ends with the shorter input. Reverse-view frame p95 was 18.20 ms for 06 and 18.15 ms for 08. The first fixed factor image was saved 11 min 10 s after writing the control recipe. Thirteen fixed views took 52 s from the first to the last image. This excludes initial tool development.
