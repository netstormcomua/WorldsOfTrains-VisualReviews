# M25 | Mammoth through the low valley

Composition A is the approved starting terrain. This separate review map carries the existing Mammoth profile on two connected Railway splines. The desert terrain layer grades to a survey of those splines. The track and vehicle remain authoritative. Original M24 map and Mammoth profile hashes matched the preflight snapshot after the new map reopened.

| Evidence | What to inspect |
|---|---|
| [Approach from 2.1 m](01-approach.jpg) | Locomotive silhouette and shoulder contact |
| [Two sides at 4.5 m and 2.1 m](02-low-views.jpg) | Wheel line, slope behind the train and the reveal down the track |
| [Valley overview](03-valley.jpg) | Relation of the alignment to the open floor and surrounding dune ridges |
| [Moving train, 48 sampled frames](valley-pass.mp4) | Relative motion and shadow under the locomotive; silent, played back at 10 fps |
| [Vertical-scale roadmap](vertical-roadmap.md) | Larger massifs and a separate future panoramic ascent |
| [Measured results](measurements.json) | Geometry, ground probes, movement and scoped runtime measurements |

## Real train and Landscape checks

* Saved and reopened a 624.37 m test alignment with 26 mesh sections, two distinct persistent track identifiers and reciprocal endpoint connectivity. The minimum sampled plan radius was 679 m. The maximum sampled longitudinal grade was 1.50003%.
* Across four Landscape core regions, all shared height samples agree. Heights outside the 36 m survey envelope are byte-identical to the baseline. The largest local cut was 2.86 m and largest fill was 1.32 m. Shoulder width varies with cut/fill. At 1,260 collision probes under the mesh footprint, the largest deviation from the designed sleeper bed was 0.25 cm. The bed embeds the model by 3.5 cm.
* On a fresh game launch, the existing captain's boarding query found the Mammoth from PlayerStart. The test entered the train through the existing boarding method, drove 513.66 m, gained 7.70 m, crossed the spline junction, braked, exited and reset to its starting distance on the original spline. Peak speed 62.1 km/h. All sampled wheelset GUIDs resolved and the maximum vertical wheel reference residual was under 0.005 cm. This checks virtual wheel anchors; it does not measure rendered wheel-flange contact or a full swept-body envelope.
* Peak UE process memory was 3,457 MiB. The review ticker reported 8.70 ms p95 over 4,694 ticks while capturing. This is an offscreen editor-game session; GPU presentation pacing, audio, packaged performance and physical-key input were not measured.

## Visual review

The low front-quarter view gives the locomotive a strong silhouette and shows light across the upper body. The reverse view exposes the curve past the nose. The elevated view makes the low pass and its shallow cut legible, and also exposes the finite test endpoint. At low height the undercarriage loses detail in shadow and the smooth foreground has few scale cues. From above the track reads as a dark strip. This is an open test alignment. Neither a closed loop, an elevated railway nor a megadune has been built in this milestone. Please assess how the train sits in the valley and how much terrain should remain visible around the train.
