# Columns 735 m · Directional sun shadows

The upper panel is the original lit frame. The lower panel has shadow casting disabled on the main directional sun. Direct lighting, manual exposure, camera, terrain and material were held fixed in one DX11/SM5 game session.

[Two measured dune edges](edges.jpg) · [Independent shadow check on the locomotive and track](witness.jpg)

| Median signed screen luminance step (0–255) | Shadows on | Shadows off |
|---|---:|---:|
| Upper diagonal edge | −8.373 | −0.056 |
| Short left edge | +3.467 | −0.671 |

The initial crop reproduced the archived lit frame within 0.40 luminance levels on average. A positive control used 94 pairs of nearby screen locations selected by ray traces before the switch. The median differential brightening was 9.24 levels, and 82% of pairs exceeded two levels. Both target edges largely disappeared with solar shadow casting disabled. This identifies a substantial shadow contribution at this viewpoint. A correction that retains useful train and terrain shadows still requires separate testing. The production light was not modified.
