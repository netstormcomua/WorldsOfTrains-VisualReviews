# One dune scene, ten dust intensities
00 is the clear control. 01вЂ“10 are ten separate game captures on the Small dune route with Mammoth at 2,635 m, the same quarter camera, sunlight, Hybrid Sand v2, seed 27334 and wind phase 8 s. Every level has a full-size image. 04 keeps the train, the rail curve and distant dune legible. At 06 the train remains readable as the distant crest loses definition. At 09вЂ“10 the foreground silhouette and near rails survive while the far route disappears.

The render uses the existing Layout A distant dust / LightDust1 wind setup with its 4.2, в€’1.5 m/s wind vector. Broad overlapping Unreal local fog volumes and volumetric height fog produce the denser levels. The volume positions are seeded once and held at identical phase across all stills. The sunlight stays at pitch в€’49В°, yaw 128В°. Clear keeps the scene's normal distance atmosphere. The experimental settings use native Unreal fog; UDS particles and separate surface-stream cards are disabled. The level 06 clip shows the dust banks moving with the train stationary.

DX11/SM5, 1440 Г— 810, 60 fps cap. Frame p95 for 04 / 06 / 08 was 17.69 / 17.56 / 17.95 ms. At 06 the moving banks measured 18.57 ms p95. The first 65-frame measurement at 10 gave 74.01 ms frame / 123.29 ms GPU p95. A separate 240-frame capture at the same camera and phase measured 17.36 / 21.14 ms, with its clear control at 17.63 / 21.92 ms. The high first sample remains recorded; its cause was not isolated. Repeating the clear and strongest frames in a separate load changed the full-frame mean by 0.52 and 0.21 on an 8-bit scale. Technical capture is complete; the choice of a gameplay or filming preset is open.


[All eleven fixed-phase game views](all-levels.jpg) · [Moving dust at 06](wind-06.mp4)

[00](intensities/00.jpg) | [01](intensities/01.jpg) | [02](intensities/02.jpg) | [03](intensities/03.jpg) | [04](intensities/04.jpg) | [05](intensities/05.jpg) | [06](intensities/06.jpg) | [07](intensities/07.jpg) | [08](intensities/08.jpg) | [09](intensities/09.jpg) | [10](intensities/10.jpg)
