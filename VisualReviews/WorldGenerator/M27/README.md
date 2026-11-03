# M27 | Two world layouts and three playable desert slices

**Review decision.** Use D2 as the ordinary valley and D3 for short, intentional reveals. The existing field generator already creates a visibly richer ride when given closer, offset crests. Before scaling up, tune the placement rules to alternate a near shoulder with an opening and test that pattern on a second alignment. The present evidence supports a short desert pass. It does not establish that one density will sustain a whole 10 km journey.

## Proposed 10 × 10 km layouts

Both drawings show the five-train and captain start in the southeastern dunes, a central placeholder, broad biome transitions, two 300 m massif centres and one optional 500 m centre. These markers are proposed placements. The previous 500 m recipe occupies about 6.6 × 3.85 km; a boundary placement would extend partly beyond the map or replace a nearby 300 m mass. The two rail itineraries share the light-coloured station section between turnouts. Salt flats and rocky mountains exist only on these plans.

| Option | Train experience | Small / large loop, plan length |
|---|---|---|
| [A · Three sides of the basin](plan-A.jpg) | The low loop skirts the centre. The longer journey follows the salt basin on the northwest and the rocky shoulder in the northeast. Recommended for distinct reveals and early testing of each transition. | 14.4 / 25.8 km |
| [B · Western sand ridge](plan-B.jpg) | The western crest stays in sight for longer. The large loop crosses a northern saddle and returns along the eastern salt margin. This offers more length to stage a climb, but more time looking at one ridge. | 14.3 / 25.0 km |

The highlighted candidate scenic portions measure approximately 5.1 km (A) and 7.0 km (B) in plan. Even a continuous 1.5% climb throughout would gain only about 77 or 105 m before transition allowances. The profiles, turnouts, curves, return descents, terrain grading and actual train braking require a separate survey.

## Density experiment

Each playable map uses the same 1,008 × 1,008 m Landscape core, lighting, material, 624.37 m two-spline railway, Mammoth, captain and controls. D1 reproduces the M25 graded core byte-for-byte. D2 adds eight offset ridges in the widest openings. D3 adds twelve more supporting forms, varying shape, height, yaw and crest phase. Field m24.1 uses the pinned Single Dune m23.1 shapes. We held the terrain within 30 m of the spline and the outer rim fixed. The five-train station is a feature of the future layout; each test uses one train to keep the comparisons controlled.

| Slice | Forms in the recipe | Nearby area with >3 m of dune relief | Median lateral distance to ≥5 m relief |
|---|---:|---:|---:|
| D1 · baseline | 24 | 32.9% | 166 m |
| D2 · infill | 32 | 61.7% | 71 m |
| D3 · secondary ridges | 44 | 72.3% | 59 m |

Coverage measures the 30–170 m band beside the surveyed line between Y = −260 and +270 m. Relief is measured above the shared substrate. The distance metric uses 132 east/west probes along the nearly north/south line, censored at 300 m. It describes space alongside this route, rather than universal dune-to-dune spacing.

* [Top-down relief plans and actual elevated Unreal views](01-layouts.jpg). The plans were generated from the heightfields before scene assembly. D2 closes the larger empty gaps while keeping a recognizable valley. D3 creates clustered shoulders and a more continuous wall on parts of the alignment.
* [Gameplay-height and low train views](02-ground.jpg). At 4.5 m the baseline has a long stretch of empty middle distance. D2 brings a second silhouette into that space. The fixed 2.4 m Mammoth view changes comparatively little, because the locomotive dominates the frame.
* [Along and across the railway](03-sightlines.jpg). D2 retains a clear opening ahead. In D3 the smaller crests layer particularly well across the valley, while several near crests merge into a broad outline in the forward view. The smooth exposed sand and repeated ripple detail remain visible on all three maps.
* [Synchronized actual train passes](train-passes.mp4). Existing train dynamics drove each run. The 4-second silent review samples 48 frames per map at nominal 8 m intervals. It is accelerated playback.

The saved maps reopened with five fixed cameras each. The original duplication step assigned new track IDs and removed their connection; it stopped the first train at the junction. After reconnecting the two endpoints in each new world and reopening, all three drives boarded the Mammoth from the start, crossed the junction, travelled 513.5–513.6 m, stopped, exited and reset. This was an editor-game test of the open slice, not an end-to-end run of either planned loop. The two world layouts and all three slice choices await review.

[Measurements and camera positions](measurements.json)
