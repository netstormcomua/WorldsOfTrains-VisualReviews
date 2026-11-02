# Dune Lab — modular generator and interactive editor review

2026-11-02. Tool implementation ready for user review. Dune morphology remains the pinned M2.1 implementation; this milestone does not claim artistic approval or new production-ready dune shapes.

## Review images

| Material | Image |
| --- | --- |
| Three UI-generated presets, identical overview camera | [S1 / S3 / S4](variants-comparison.jpg) |
| Native Unreal panel and actual preview | [Dune Lab UI](dune-lab-ui.jpg) |
| Gameplay-height and top views | [S4 views](gameplay-and-top.jpg) |
| Geometry diagnostic | [Neutral top and side](neutral-diagnostic.jpg) |

These are actual Unreal Editor captures. Only cropping, resizing, JPEG compression and captions were applied. A 2m marker is present. The side capture uses a larger editor window; it is a diagnostic view, not a pixel-aligned before/after comparison.

## What was implemented

A native Slate panel controls one selectable preview mesh in an isolated 252m test level. It exposes preset selection, numeric/slider parameters, seed, Generate, Reset, custom preset save/load, fast/final quality, sand/neutral materials, four fixed cameras, presentation overlays, screenshot capture and level saving. Slider regeneration occurs on release; Python calculation is asynchronous. The existing Unreal viewport provides orbit, zoom and focus.

Single Dune and Dune Field now have small independent adapters. Single Dune calls the existing pinned M2.1 geometry implementation; the field adapter composes those same contributions in stable instance-ID order. No shape formula was duplicated. Schema version 1 and implementation m21.1 are explicit, with checked legacy implementation hashes. Unknown versions fail instead of silently adopting new geometry.

The contract uses metres, world XY/yaw, a regular 1m evaluation grid, optional base terrain and influence/exclusion masks. Outputs are additive height contributions with reproducibility metadata. The Lab builds its mesh from that same contribution; it does not require a Landscape actor per dune. Production field boundary blending remains a separate composition operation. Future versions must be adopted explicitly, while old versions and presets remain available.

## Verified

- Ten previous M2.1 single/terrain/field outputs match their legacy R16 hashes exactly through the new composition adapter. Reversed input ordering is stable.
- Fourteen exposed shape/seed controls change numeric geometry. Determinism, input immutability, masks, world translation, version rejection and preset JSON round trips pass.
- Fast 2m preview samples the full 1m heightfield: common vertices agree exactly. Interpolated fast-mode deviation is about 0.154–0.250m across six presets. Use Final 1m for judging crests.
- Saved level reopened with one preview actor and one mesh section. Two reapplications produced no duplicate preview. All 169 collision probes passed; maximum discrepancy was 0.0000611cm.
- S1, S3 and S4 were generated through the actual UI. A custom 28m-height preset survived save, reset and load. Camera/material/quality modes, presentation, viewport capture and Save Lab were exercised.
- 135 protected existing generator scripts/test assets were unchanged. Original maps and asset materials were not overwritten.

The numeric test covers every exposed parameter; this is not a claim that every individual slider was exhaustively mouse-tested. Python-only calculation took about 0.024–0.028s in the recorded batch; that excludes process startup, editor mesh construction, collision and rendering. No packaged-build or frame-time performance claim is made.

## Visual assessment

S1 gives the cleanest long silhouette for exploring crest controls, but its tapered end remains too pointed. S3 clearly demonstrates multiple bends and height variation, although some shoulders resemble separate mounds. S4 makes asymmetry and horns easiest to inspect from above; at 4.5m its broad windward slope still resembles a smooth hill. None is presented as artistically approved.

The 1m grid limits close crest detail. Fine sand repetition, low-contrast warm material, the flat studio horizon and overly rounded low-angle silhouettes remain visible. Neutral material exposes the rectangular preview tile against the sand studio ground; that boundary is intentional diagnostic presentation, not a proposed biome transition. Material overhaul and new morphology were outside this tool milestone.

## How to use

Open the dedicated Dune Lab level and Window > Dune Lab. Choose a built-in preset; edit values or release a slider to regenerate. Use Fast for exploration and Final for inspection. Top/Overview/Gameplay/Side restore consistent viewpoints. Select the preview and use Unreal's normal focus/orbit/zoom controls. Presentation hides editor overlays; Escape clears the yellow selection outline. Save a custom preset under a unique name; load it from the selector. Save Lab stores the preview and versioned configuration; Capture viewport writes a PNG locally.

The tool currently depends on the configured local Python/NumPy installation. Presets are schema-versioned JSON. Existing custom names are not overwritten. A custom preset retaining a built-in internal display name may reopen with the built-in selector label while the saved configuration remains intact; reselect the custom file before using Reset. Preset-name text is a save target, not a guarantee that the active shape matches that name.

## Next review

Evaluate tool usability and the differences between S1/S3/S4, then choose the isolated shape weakness to improve with a new explicit generator version. Validate that version against existing field fixtures before adoption. Railway, new biomes and world expansion remain deferred. A new demonstration video was not recorded; selected screenshots and the panel are available for review.

See [parameters and fixed cameras](parameters.json), [technical results](technical-results.json) and [capture provenance](capture-provenance.json). No source code, Unreal packages, original assets or private logs are included.
