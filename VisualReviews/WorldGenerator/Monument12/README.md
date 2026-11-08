# Monument sandstone range from Mammoth

First in-game review of art direction 01. Three separately seeded silhouettes stand beside the existing Outer track. The broad mesa is 172 m high, the narrow butte 127 m and the long plateau 192 m. [Selected concept](https://raw.githubusercontent.com/netstormcomua/WorldsOfTrains-VisualReviews/8bceb01c1042069ec3d1e573e09a8c3aeae30f18/VisualReviews/WorldGenerator/MountainConcepts01/01-mesas.jpg) · [Valley of the Gods reference](https://www.blm.gov/visit/valley-gods).

[Eastern rail view](images/east.jpg) · [Western approach](images/far.jpg) · [Near approach](images/near.jpg) · [Near view with range hidden](images/control.jpg) · [Ordinary side camera](images/drive.jpg) · [11-second DX11 drive, silent](outer-drive.mp4)

[First pass and revision](images/first-and-revised.jpg). Left is 1.2.0, right is 1.2.1. Top row shows the standard side-camera passage at approximately seven seconds. Lower row shows a full-resolution crop from each. In the revision the native blocks sit deeper in the upper ledges, the cliff and blocks share a sandstone finish, and most ledges taper out around the cliff.

SingleMountain 1.2.1 builds each body's shell. MountainRange 1.0.1 places three saved presets. Combined shell geometry is 35,784 triangles. 502 native RockyDesert rock instances are distributed across three instanced components, with additional triangles that depend on the active mesh LOD. The triplanar cliff texture repeats every 7.4 m. The lowest sampled footprint-to-track clearance is approximately 176 m. Seeds, transforms, hashes and frame measurements are in [parameters.json](parameters.json).

## Runtime

Unreal DX11/SM5, 1440 × 810, 100% screen percentage, 60 fps cap. The first two runs use the same moving inspection camera, start, throttle and lighting. Each records eight seconds after the initial second. The third uses Mammoth's standard side camera and records the window. Times below are 95th percentiles.

| Condition | Travel (m) | Frame (ms) | GPU (ms) | Frame samples |
|---|---:|---:|---:|---:|
| Range hidden | 319.4 | 17.31 | 17.22 | 481 |
| Range visible | 319.4 | 17.39 | 17.15 | 480 |
| Native side camera with recording | 636.6 | 17.69 | 17.49 | 890 |

The video was encoded at 30 fps from 28.2 distinct captured frames/s. Held frames belong to the recorder. A single capped pair measures this isolated episode. It does not establish an uncapped throughput gain or a budget on the full game map.

The west approach compresses the three profiles into one. In the near view the main face and fluted buttresses read clearly, but large patches of scree look smooth and some dark blocks remain conspicuous against sunlit sandstone. The isolated sand plain makes the foot transition especially visible. Art review is open; this range has not been integrated into the production map.

