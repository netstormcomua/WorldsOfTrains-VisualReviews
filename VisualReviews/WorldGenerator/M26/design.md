# M26 | Massif contract and next route experiments

## Reusable composition

Desert Terrain selects a bounded contribution from Mega Dune Massif m26.1. Its inputs are a versioned layout, a pinned reference relief, a requested height in metres, and increasing world-coordinate sampling axes. The layout contains stable instance IDs, individual seeds, parameters, origins and wind angles. Unknown generator versions are rejected. The same layout was intentionally used for all four sizes to isolate scale.

The module builds a compact, gently tilted sand apron and delegates eight primary, secondary and supporting dune contributions to Field m24.1. Field calls Single m23.1 with saved R1/R2/R3 shapes. Layers overlap through the established field blend. The entire compound relief is sampled with proportional horizontal and vertical dimensions. No single-dune math was copied and no existing preset height limit was raised. The reference relief is pinned independently of edits. Moving or adding a small ridge cannot silently renormalize the rest of the world. Outside its support the massif contributes zero. The measured prototypes use a flat host datum; conforming a whole massif to arbitrary steep substrate and enforcing a railway protection mask are later Desert Terrain responsibilities.

The near core has four independently streamable 505 × 505 Landscape regions. Their shared grid has 1,009 × 1,009 unique samples. Actual spacing varies with the laboratory scale. Eight non-overlapping 64 × 64 background Landscapes provide the far sand beyond the flat rim, one component each. Their outermost ring is review scenery and excluded from measured massif relief. Automatic render LOD is used for ordinary views. A forced mixed-LOD view tests the seam explicitly. The 1,000 m prototype has insufficient close-up terrain resolution for railway grading. For production, retain coarse world-coordinate macro relief, allocate aligned high-resolution patches for track and close-ups, constrain shared coarse/fine edge samples, and apply the railbed last.

Encoding uses one 16-bit datum (+550 m) and vertical scale 250 for the entire laboratory. Quantization step 1.953125 cm, maximum round-off 0.977 cm, representable interval −90 m to approximately +1,189.98 m. Out-of-range values are rejected before conversion. A higher datum or larger range is a new configuration with new precision tests.

## Possible railway experience in a 10 × 10 km desert

* Keep the approved M25 valley as the low experience. Use a modest massif flank to hide the horizon on approach. Distinct near dunes, the train, and a more distant wall should appear in different planes.
* For a small loop, stay low and return around a toe. For a larger loop, branch before a natural saddle, climb a broad shelf, reveal the basin obliquely and descend to a compatible return junction. Preserve sight distance for stopping. A tall landmark beside a route does not require a summit railway.
* Treat +100 m as the first possible lookout. At sustained 1.5% this requires at least 6.67 km of horizontal climb and a comparable descent, before transitions, switches and braking allowances. +250 m requires 16.67 km each way at the same grade. Survey a feasible alignment and test performance and braking with the actual train before choosing either. No elevated loop or full world was built in M26.
* Ordinary 100 m relief and selected 300 m landmarks are the first integration candidates. Reserve 500 m for a single well-composed viewshed. The 1,000 m example needs around 13.2 km along its crest footprint and is better evaluated at the map boundary or beyond it. Recomposition into a smaller footprint would require another slope and shape review.

## M25 items still open

The original 624.37 m alignment was retained. The prior drive covered 513.66 m. End-to-end traversal, the complete rendered body clearance envelope, final railbed materials, packaged performance, World Partition railway streaming, and long uphill/downhill train dynamics remain open. M26 uses a stationary real Mammoth on a separate straight reference track. Its Landscape streaming checks do not test rail streaming.
