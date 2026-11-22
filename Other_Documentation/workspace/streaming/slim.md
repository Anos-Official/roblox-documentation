<!-- Source: https://create.roblox.com/docs/workspace/streaming/slim -->

SLIM | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/streaming/slim.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/projects)
6. /
7. [Architecture](/docs/projects/data-model)
8. /
9. [Instance streaming](/docs/workspace/streaming)

# SLIM

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/streaming/slim.md)

SLIM  (Scalable Lightweight Interactive Models) is an automatic optimization system that generates lightweight, optimized representations of [Models](/docs/reference/engine/classes/Model)  and platform avatars using cloud-based transcoding (converting assets into more efficient formats). When enabled, SLIM combines multiple parts into fewer draw calls (rendering commands sent to the GPU) and generates multiple levels of detail, allowing the engine to intelligently select the best representation based on distance, device capability, and available resources.

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Disabled.jpg) Without SLIM — streamed-out models are invisible

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Enabled.jpg) With SLIM — optimized stand-ins remain visible

SLIM provides three key benefits:

-

Visual quality

 — Distant models appear more detailed than the legacy model level‑of‑detail system, maintaining closer fidelity to the original.

-

Consistent transitions

 — All parts within a model switch detail levels simultaneously, eliminating jarring per-part transitions.

-

Performance

 — Composite meshes dramatically reduce draw calls, triangle counts, and memory usage, enabling richer scenes across all device tiers.

Explore SLIM in these published games:

[![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Demo-Models.png)](https://www.roblox.com/games/135885449743134/CPC-Slim-Template)  [City People Cars SLIM Template](https://www.roblox.com/games/135885449743134/CPC-Slim-Template)  — World models with SLIM enabled

[![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Demo-Avatars.png)](https://www.roblox.com/games/81704282913046/SLIM-Platform-Avatars)  [SLIM Platform Avatars](https://www.roblox.com/games/81704282913046/SLIM-Platform-Avatars)  — 200 animated avatars rendered with SLIM

## [Prerequisites](#prerequisites)[](#prerequisites)

SLIM requires the following:

1.

[StreamingEnabled](/docs/reference/engine/classes/Workspace#StreamingEnabled)  must be enabled on the [Workspace](/docs/reference/engine/classes/Workspace)  object. See also [streaming properties](/docs/workspace/streaming/techniques#streaming-properties)  for related recommended settings.

2.

The place must be saved to Roblox  (not a local .rbxl  file), as SLIM uses cloud transcoding to generate optimized assets. If you're testing locally, publish the place and then enable SLIM.

3.

[Team Create](/docs/projects/collaboration)  must be enabled for the game, as SLIM relies on associated properties for cloud asset generation.

## [Technical behavior](#technical-behavior)[](#technical-behavior)

When you publish or playtest a game with SLIM-enabled models, the engine uploads model data to a cloud service that generates optimized composite meshes with multiple levels of detail. At runtime, clients fetch these assets from the CDN and the engine selects the appropriate detail level based on distance and device capability, classifying each SLIM model into rendering zones based on distance from the camera:

 ![Diagram showing the four SLIM rendering zones, colored sky blue, teal, yellow, and vermilion, radiating from a player character.](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Zones.jpg)

| Range | | Data Model State | | Rendering |
| --- | --- |
|  | | Full instances streamed in. | | Traditional part-by-part rendering. |
|  | | Full instances streamed in. | | The engine renders the SLIM composite when more efficient. |
|  | | Instances streamed out. Only a minimal placeholder exists in the [DataModel](/docs/reference/engine/classes/DataModel) , not the full model hierarchy. | | SLIM composite rendering. |
|  | | Minimal placeholder in the [DataModel](/docs/reference/engine/classes/DataModel) . | | Not rendered. |

## [SLIM for models](#slim-for-models)[](#slim-for-models)

SLIM works best on models that represent static world geometry  — buildings, props, vehicles, terrain features, and other environment objects that don't change at/during runtime. Adding or removing parts, changing materials, or modifying geometry at runtime prevents SLIM from rendering the model correctly. See [model structure](/docs/workspace/streaming/techniques#model-structure)  for general model structure guidance and [limitations](#limitations)  for the full list of exclusions.

To enable SLIM on a model, set its [LevelOfDetail](/docs/reference/engine/classes/Model#LevelOfDetail)  property to [SLIM](/docs/reference/engine/enums/ModelLevelOfDetail#SLIM)  in the [Properties](/docs/studio/properties)  window.

 ![The Properties window with the LevelOfDetail property set to SLIM.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Model-LevelOfDetail-SLIM.png)

When SLIM is set on a model, the engine:

1.

Serializes the model's rendering-relevant properties (geometry, materials, textures, transforms) into a compact representation. Supported instance types within the model include [Part](/docs/reference/engine/classes/Part) , [MeshPart](/docs/reference/engine/classes/MeshPart) , [Decal](/docs/reference/engine/classes/Decal) , [Texture](/docs/reference/engine/classes/Texture) , [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance) , [PartOperation](/docs/reference/engine/classes/PartOperation) , [NegateOperation](/docs/reference/engine/classes/NegateOperation) , and [SpecialMesh](/docs/reference/engine/classes/SpecialMesh) .

2.

Uploads this data to the cloud transcoding service on first publish or play.

3.

The cloud service generates a composited mesh with multiple levels of detail, removing hidden internal geometry and optimizing textures.

4.

At runtime, clients fetch the optimized SLIM asset and render it when the engine streams out the original model or when SLIM is more efficient than the full model.

Initial SLIM generation might take a few moments for complex models. The cloud service processes assets in the background, so if a model doesn't appear as SLIM immediately after enabling, wait 1–2 minutes and rejoin; the transcoded asset persists on the CDN and the client fetches it on the next session.

Converting from Streaming Mesh

If your game uses the legacy [StreamingMesh](/docs/reference/engine/enums/ModelLevelOfDetail#StreamingMesh)  setting for [Model.LevelOfDetail](/docs/reference/engine/classes/Model#LevelOfDetail) , you can convert individual models by selecting them and changing the property in the [Properties](/docs/studio/properties)  window, or you can batch-convert multiple models at once using a script like the following in the [Command Bar](/docs/studio/overview#command-bar) . Note that some models which worked with [StreamingMesh](/docs/reference/engine/enums/ModelLevelOfDetail#StreamingMesh)  might need adjustments for SLIM, particularly those with overlapping parts or complex [PartOperation](/docs/reference/engine/classes/PartOperation)  hierarchies.

Batch-Convert StreamingMesh to SLIM

```

for _, descendant in workspace:GetDescendants() do

    if descendant:IsA("Model") and descendant.LevelOfDetail ==

        Enum.ModelLevelOfDetail.StreamingMesh then

        descendant.LevelOfDetail = Enum.ModelLevelOfDetail.SLIM

    end

end

```

## [SLIM for avatars](#slim-for-avatars)[](#slim-for-avatars)

Platform avatars outside of the currently streamed area are not visible by default. Enabling SLIM avatars renders [standard](/docs/avatar/character-bodies/specifications)  player characters — regardless of how many accessories or clothing layers they have — as lightweight, animated stand‑ins that maintain visual fidelity at a fraction of the rendering cost.

Audience in Far Distance Audience in Near Proximity

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Avatars-Enabled-Far.jpg)

SLIM Enabled

~170,000 triangles

~4,000 client instances

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Avatars-Disabled-Far.jpg)

SLIM Disabled

~2,600,000 triangles

~60,000 client instances

The key SLIM-specific property for avatars is [Workspace.EnableSLIMAvatars](/docs/reference/engine/classes/Workspace#EnableSLIMAvatars)  which should be set to [Enabled](/docs/reference/engine/enums/RolloutState#Enabled)  in the Properties  window, alongside [LevelOfDetail](/docs/reference/engine/classes/Model#LevelOfDetail)  set to [SLIM](/docs/reference/engine/enums/ModelLevelOfDetail#SLIM)  on your non‑avatar world models.

 ![The Properties window with the EnableSLIMAvatars property set to Enabled.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-EnableSLIMAvatars.png)

With [EnableSLIMAvatars](/docs/reference/engine/classes/Workspace#EnableSLIMAvatars)  enabled, the engine:

-

Renders a SLIM version when an actual avatar model streams out.

-

Swaps between SLIM and full-resolution representations based on available resources, even inside the streaming radius.

-

Throttles SLIM animations based on scene importance and available bandwidth.

Supported Avatars

-

R15 avatars with a body, dynamic head, [standard](/docs/avatar/character-bodies/specifications#standard-r15-rigs)  or [advanced](/docs/avatar/character-bodies/specifications#advanced-r15-rigs)  R15 rig, and rigid/layered accessories.

-

Avatar changes made between the [CharacterAdded](/docs/reference/engine/classes/Player#CharacterAdded)  event and [CharacterAppearanceLoaded](/docs/reference/engine/classes/Player#CharacterAppearanceLoaded)  event.

-

Avatars defined by StarterHumanoid  or StarterCharacter  under the [StarterPlayer](/docs/reference/engine/classes/StarterPlayer)  service.

Excluded Avatars

-

R6 avatars.

-

NPC characters (even those with a standard or advanced R15 rig).

-

Avatars with custom proportions, body scaling, or experience-applied avatar settings.

-

Avatar changes made after the [CharacterAppearanceLoaded](/docs/reference/engine/classes/Player#CharacterAppearanceLoaded)  event (equipping tools, accessory changes, [Highlight](/docs/reference/engine/classes/Highlight)  additions, etc.).

-

Avatar changes made by [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts) .

Testing SLIM Avatars

Unlike [model SLIM](#slim-for-models)  which you can test alone by moving far from a model until it streams out, SLIM avatars require multiple players in the game to observe. Use one of these [testing modes](/docs/studio/testing-modes)  to test SLIM avatars:

-

[Team Test](/docs/studio/testing-modes#collaborative-testing)  — Join with friends or alternate accounts to see SLIM avatars at distance.

-

[Server and Clients](/docs/studio/testing-modes#multi-client-simulation)  — Launch two or more client windows where each client displays avatar copies that the others render as SLIM when at distance.

Note that avatars must have been transcoded in a SLIM-enabled game before they appear as SLIM. If avatars don't render as SLIM in your first test, rejoin the game after a moment to allow transcoding to complete.

## [Limitations](#limitations)[](#limitations)

| Limitation | | Details |
| Streaming required | | SLIM only functions with [StreamingEnabled](/docs/reference/engine/classes/Workspace#StreamingEnabled)  set to true . Without streaming, SLIM‑eligible models fall back to traditional level‑of‑detail rendering. |
| Static models only | | [Model SLIM](#slim-for-models)  does not support models modified at runtime (parts added/removed, properties changed) or models that play animations. |
| Humanoid instances | | The engine excludes models containing a [Humanoid](/docs/reference/engine/classes/Humanoid)  from static [model SLIM](#slim-for-models)  processing. Use [SLIM avatars](#slim-for-avatars)  for animated player characters. |
| Avatar restrictions | | [SLIM avatars](#slim-for-avatars)  only support R15 player characters. R6 rigs, NPCs, and avatars with custom proportions fall back to default rendering. |
| Cloud dependency | | The cloud service generates and stores SLIM assets on the CDN. Offline or local testing without a published place does not produce SLIM results. |
| Zero-scale models | | The engine excludes models with a [Scale](/docs/reference/engine/classes/Model#Scale)  of 0  from SLIM processing. |
| Platform availability | | On platforms where SLIM is not yet supported, models set to [SLIM](/docs/reference/engine/enums/ModelLevelOfDetail#SLIM)  fall back to [Disabled](/docs/reference/engine/enums/ModelLevelOfDetail#Disabled) . |

## [Debugging](#debugging)[](#debugging)

To better understand the status of SLIM models, Roblox provides several debug tint modes  in the DebugVisualizations  ⟩ SlimTintMode  dropdown of the [Developer Console](/docs/studio/developer-console) . Note that this menu is only available to creators who have Edit  permissions for the game.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/debug-visualizations/SLIM-Tint-Mode-Menu.jpg)

There are multiple tint modes to select from. See [Enum.SlimTintMode](/docs/reference/engine/enums/SlimTintMode)  for the color mappings of each mode.

LOD Data Model State

[LOD](/docs/reference/engine/enums/SlimTintMode#LOD)  colors each mesh by its current level of detail using a blue-to-red heatmap. Blue indicates the lowest detail and warmer colors indicate higher detail.

You can also see SLIM debug visualizations in Studio by selecting a tint mode from the [Visualization Options](/docs/studio/overview#visualization-options)  menu:

 ![A close up view of the 3D viewport with the Visualization Options button indicated in the upper-right corner.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

In addition to the [LOD](/docs/reference/engine/enums/SlimTintMode#LOD) /[DataModelState](/docs/reference/engine/enums/SlimTintMode#DataModelState)  tint modes, Studio offers the [TranscoderStatus](/docs/reference/engine/enums/SlimTintMode#TranscoderStatus)  tint mode. While editing, only this tint mode is available in the visualization options menu; while playing, all the tint modes are available. See [Enum.SlimTranscoderStatus](/docs/reference/engine/enums/SlimTranscoderStatus)  for the color mappings of each status.

## [Troubleshooting](#troubleshooting)[](#troubleshooting)

SLIM model not appearing

-

Verify that [StreamingEnabled](/docs/reference/engine/classes/Workspace#StreamingEnabled)  is true .

-

Confirm the place is published to Roblox and [Team Create](/docs/projects/collaboration)  is enabled.

-

Check that [LevelOfDetail](/docs/reference/engine/classes/Model#LevelOfDetail)  is set to [SLIM](/docs/reference/engine/enums/ModelLevelOfDetail#SLIM)  for the model.

-

Wait 1–2 minutes after first publish for cloud transcoding to complete, then rejoin.

-

Ensure the model doesn't contain a [Humanoid](/docs/reference/engine/classes/Humanoid)  instance.

Solid modeling operations not rendering correctly in SLIM

[PartOperation](/docs/reference/engine/classes/PartOperation)  instances for [solid modeling](/docs/parts/solid-modeling)  (unions, intersections, negations) might not render correctly in some SLIM models. If a union appears missing or distorted in the SLIM representation, try separating the affected [PartOperation](/docs/reference/engine/classes/PartOperation)  into its own model or simplifying the CSG operation.

Z-fighting or flickering on SLIM models

Z-fighting can occur when parts in the original model have overlapping or coplanar faces. To resolve:

-

Move overlapping parts slightly apart (even 0.01  studs is sufficient).

-

Avoid perfectly flush surfaces between adjacent parts in the same model.

Texture or UV shifts on SLIM models

SLIM regenerates UV mappings (how textures are projected onto 3D surfaces) during transcoding. Default Roblox materials might show slightly different tiling patterns compared to the original. To mitigate:

-

Use custom textures via [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  for important surfaces.

-

Group visually related parts into the same model to ensure consistent texturing.

SLIM avatars not rendering

-

Verify [Workspace.EnableSLIMAvatars](/docs/reference/engine/classes/Workspace#EnableSLIMAvatars)  is set to [Enabled](/docs/reference/engine/enums/RolloutState#Enabled) .

-

Test with multiple clients using [Server and Clients](/docs/studio/testing-modes#multi-client-simulation)  test mode (requires at least 2 clients).

-

Ensure the avatar uses a [standard](/docs/avatar/character-bodies/specifications#standard-r15-rigs)  or [advanced](/docs/avatar/character-bodies/specifications#advanced-r15-rigs)  R15 rig without custom proportions.

-

Confirm the game doesn't modify the avatar after the [Player.CharacterAppearanceLoaded](/docs/reference/engine/classes/Player#CharacterAppearanceLoaded)  event.

Visual glitches on animated SLIM avatars

Full-body or finger animations might occasionally show visual artifacts due to bone replication timing. This is a known issue being actively improved. If the issue is severe, verify that animation scripts aren't modifying bone transforms outside of the standard animation pipeline.

Inaccurate triangle count in rendering stats

The rendering stats panel might report incorrect triangle counts when SLIM avatars are enabled. This is a known reporting bug and does not affect actual rendering performance.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
