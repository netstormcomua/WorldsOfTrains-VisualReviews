# M23 | C40 crest and terrain review

Three candidates use the explicit Single Dune m23.1 implementation. Original C40 is rerendered with the same cameras and light as the candidates. All four use seed 17, a 40 m design height and a 1 m grid across 504 m. Actual sampled peaks are 39.27 to 39.85 m after crest rounding. The white post is 2 m high.

| Review | What to compare |
| --- | --- |
| [Neutral relief and plan](01-neutral-shapes.jpg) | Trace the crest and the taper of each shoulder in both views. |
| [Gameplay height, opposite sides](02-gameplay-both-sides.jpg) | Same 4.5 m camera positions and FOV for each row. |
| [Cinematic, near base and elevated](03-cinematic-near.jpg) | How much of the shape survives a low windward approach? |
| [End profiles](04-crest-profile.jpg) | The slip face turning into the rising windward surface. |
| [Partial overlap on uneven ground](05-terrain-overlap.jpg) | R2 flat versus the same R2 with a smaller, offset R1 on rolling ground. |
| [Presets, cameras and measurements](measurements.json) | Exact configurations, hashes, collision and terrain results. |

## Artistic assessment

R3 is the review recommendation. From the reverse gameplay camera the slip face turns into a long illuminated shoulder. The end view shows a distinct lip and a continuous sweep into the ground. The windward near view still has a rounded summit. R1 gives the clearest single offset crown and the longest uninterrupted approach. R2 gives the most sinuous ridge in plan, but its broad crest reads almost level from the reverse low camera. A direct low windward view is still the least distinctive angle across the family.

The new shape warps the position of the crown along the span, reduces the body and slip-face widths with local crest height and joins the two slopes with a short tangent-continuous fillet. Existing controls cover crown bias, crest bends, footprint, slip angle and taper. The diagnostic uses matte material, a directional key at 25 degrees, fill, sky light and fixed manual exposure. The cinematic shot uses the separate sand/light preset. These are static Unreal game captures. The sky gives even the matte fixture a slight tint; the absolute brightness of sand is not part of the geometry comparison. No global or local increase in mesh resolution was used.

## Terrain findings

M2.1 already sampled a complete base grid, adjusted slip-face run using its directional gradient and merged positive contributions before adding the base once. Its bounded fixtures and Landscape component probes did not establish independent region continuity. It had no footprint-wide placement rejection.

The new shared geometry protects the immediate crest from slope compensation and gradually adapts the lee run below it. Across three presets and four test surfaces (flat, inclined plane, curved rise and uneven), the grid location of the highest **relative** dune contribution matched the flat reference. The highest **world-space** point moved by up to 11.4 m. Windward and lee grades in the main body were 22.2–26.8 and 29.7–33.5 degrees, respectively (98th and 2nd signed percentiles along the wind axis). Outside the footprint the final surface equals the base. In the 0–5 cm toe band, the 99th percentile contribution gradient stayed below 0.09 m/m.

The placement preflight samples the full positive footprint. Its adjustable 15-degree base limit rejected a steep plane and a localized steep shoulder. Separate checks bracketed the limit at 14.9 and 15.1 degrees. The shape-quality samples used smoother bases up to 6.38 degrees. For partial overlaps the existing smooth maximum added at most 0.60 m above the higher contribution at a blend width of 2.4 m. World-coordinate subregions used one external sample on each edge. Stitched values and their finite-difference normals matched the complete calculation exactly. Convex and concave bases also passed at three wind orientations.

## Verification and limits

Eight single-dune/light maps and one uneven-ground pair were saved and reopened. The single-dune maps retained one preview actor and one mesh section after two applications. All nine maps were collision-probed at 169 locations each. The capture harness recorded six 1600 x 900 screenshots per map. The four M22 mesh fixtures, the m22.1 implementation digest and ten earlier pinned field/single configurations passed regression. The M23 geometry remains a candidate for artistic approval.

Production acceptance still requires independently imported Landscape regions, including normals and collision at LOD or streaming boundaries, an in-motion visual check, and shape evaluation on representative grounds approaching the placement limit. The test pair uses the existing merge on a common substrate. It does not change a pinned Dune Field production preset.
