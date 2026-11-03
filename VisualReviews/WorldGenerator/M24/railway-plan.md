# Proposed Railway corridor in A

This is a measured siting study for the next milestone. No track or gameplay actor has been added. Working coordinates below are metres in the same XY frame as the Landscape data. Z is a proposed railhead profile, pending a check of the actual track mesh pivot, rail height and ballast thickness.

The candidate follows the open passage for 624.3 m. A read-only search sampled centerlines every 5 m in Y and scored cuts, fills and dune encroachment. The proposed constant grade is +1.50%. Centerline terrain differs from this profile by at most 1.93 m of cut or 1.89 m of fill, before allowances for rail and ballast. The present dune contribution along the line peaks at 0.28 m. This provides valley access without removing a tall crest.

| X | Y | Proposed Z |
|---:|---:|---:|
| 11.32 | -300 | 4.71 |
| 11.48 | -175 | 6.59 |
| 6.97 | -50 | 8.47 |
| 7.51 | 75 | 10.34 |
| 21.03 | 200 | 12.23 |
| 49.26 | 320 | 14.08 |

1. At the Desert Terrain level, store an explicit corridor ID, version and world-space centerline. Fit a gently curved spline and sample its actual grade and radius by arc length. Recheck the whole fit at 1 m intervals. The existing Railway system owns the playable spline, connections and meshes.
2. Measure the existing railhead offset, sleeper width and ballast profile. Sweep the largest of the five consists, allowing for its overhang on curves. Use that sweep to size the graded bed, lateral and overhead clearance, and shoulder width. Measure the orbit camera clearance separately. The initial 1.5% grade is a design target to test with the train.
3. At terrain composition, apply a zero dune-contribution mask across the bed and a smooth falloff across shoulders. Blend the remaining surface to the surveyed bed elevation with a smooth cross-section. Apply the bed constraint after dune blending so that a second overlapping dune cannot push sand back onto the track. Keep the standalone Single Dune preset and math pinned.
4. Instantiate the existing track actor and use its spline mesh regeneration. Persist actual track GUIDs and endpoint handles. The network subsystem indexes only loaded components by GUID; unloading removes a track, and ordinary duplication can assign a new GUID. Retain the corridor-to-track identity mapping across local terrain changes. Refuse movement into an unresolved next segment until it is loaded.
5. For an edit, regenerate only terrain regions intersecting the union of old/new clearance and shoulder footprints, with neighboring samples for slopes and normals. Hash the other regions. Check railhead-to-bed contact, wheel/rail alignment, camera clearance, switch connectivity, braking on grade and unload/reload with a real train before extending the corridor.
