# Sand surface and look presets

Sand m27.1 is a world-space surface material with a saved default instance. The Single Dune preview, Dune Field, Desert Terrain and Mega Dune Massif can bind the same instance to a world-space surface with a valid geometric normal. D2 is the runtime integration exercised here. A version forms part of the scene preset. The material inputs change appearance only. The supplied D2 corridor instance adds an optional world-aligned distance field derived from the actual Railway spline.

| Input or scale | Behaviour |
|---|---|
| WindXY | Unit wind direction in world XY rotates the flow patterns and ripple normals. |
| PaleSand, OchreSand, MacroStrength | Two restrained mineral colours vary over broad flow patches and with slope orientation. Large patches use a seamless low-frequency field. |
| RippleStrength | Two partially merging ripple trains, bending phase, changing spacing, and an amplitude mask interrupt the repetition. Their derived gradients fade with distance and on lee slopes. |
| Grain, deposits and roughness | Licensed Rocky Desert sand colour and normal inputs combine with internally generated fine grain. A separate roughness signal varies with grain and deposit density. Small detail uses mip filtering and loses influence first. |
| Distance | Far surfaces use the broad colour/flow evaluation. Camera distance suppresses subpixel ripple and grain normals. The optional corridor has a separate cheap far evaluation. |
| CorridorStrength, CorridorDistance | The default instance has zero corridor influence. D2 uses a signed-axis-independent distance-to-track texture with rounded ends. It darkens the shoulder progressively, breaks up the outer margin and mixes back into surrounding sand. The track pass preserves the existing mesh and texture atlas and adds dust on upward-facing, less metallic parts. |

The near 1 m Landscape height samples were reused from D2, including the graded bed. No displacement was added. At gameplay height the existing silhouette already separates into several masses; microrelief in the material gave a cleaner controlled test. The remaining broad empty areas call for a separate composition or placement test if desired. Eight very coarse outer Landscape patches continue the flat edge into two low distant horizon ridges. No material or texture source from Rocky Desert was edited.

## Photographic direction

* In the Namib ground photograph the ripple spacing stays fine while the *visibility* changes across the near slope. The lip reads as a narrow light edge, and the far face carries much less fine contrast. This informed the distance fade and the choice of a directional sun with enough fill to inspect the locomotive. The ochre colour was used as a range of hues rather than a full-frame tint. [PhotoPills, Namib photograph](https://www.photopills.com/sites/default/files/articles/2018/deadvlei-3.jpg) · [NASA, sand colour in the Namib](https://science.nasa.gov/earth/earth-observatory/where-the-dunes-end-146064/)
* Badain Jaran, seen from above, has broad uninterrupted faces beside textured belts and subsidiary ridges. That informed the patchy deposition and the difference between crest and valley shading. This satellite image is a reference for organisation at large scale. Near-surface grain in this prototype comes from the procedural surface and the licensed library. [NASA, Badain Jaran Landsat image](https://science.nasa.gov/earth/earth-observatory/megadunes-and-desert-lakes-in-china-84773/)

## Lighting and atmosphere

Both looks use the same manual exposure, 72° camera FOV and surface recipe. Day uses a 36° sun at 53,500 lux and 5,750 K. Warm uses a 19° sun at 42,500 lux and 5,125 K. Their angular source diameters are 0.54° and 0.62°. The static looks use a captured sky, a restrained fill to approximate indirect light, and three near shadow cascades. Far shadow casting was removed from the distant backdrop. Sky Atmosphere supplies aerial scattering. Lightweight exponential fog begins 220 m away with capped opacity. No volumetric fog, Nanite, Lumen or hardware ray tracing was enabled for these DX11 comparisons.

The lighting is art-directed. The supplementary fill approximates bounce, and the light transport and sand reflectance have not been calibrated against a measured site.
