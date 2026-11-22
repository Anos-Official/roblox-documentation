<!-- Source: https://create.roblox.com/docs/onboarding/artists -->

Onboarding for artists | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/onboarding/artists.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Platform](/docs/en-us/get-started)
4. /
5. [Get started for experienced creators](/docs/onboarding)

# Onboarding for artists

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/onboarding/artists.md)

This page summarizes, at a high level, the engine requirements and conventions that matter most to artists coming from other engines, and each section links to the detailed specifications.

![A realistic leafy bush with PBR textures.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg)

![A realistic mossy rock with PBR textures.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-3.jpg)

## [PBR and materials](#pbr-and-materials)[](#pbr-and-materials)

Roblox uses a metalness and roughness  PBR workflow, not a specular and glossiness workflow. A full PBR material uses these texture maps:

-

Color (albedo) , with an optional alpha channel for transparency.

-

Normal , in OpenGL tangent-space format (Y+), with a MikkTSpace tangent basis.

-

Roughness .

-

Metalness .

For formats, resolutions, and channel details, see [Texture specifications](/docs/art/modeling/texture-specifications)  and [Surface appearance](/docs/art/modeling/surface-appearance) .

Materials on Roblox come in two forms:

-

A material , set on a part or with a custom [MaterialVariant](/docs/reference/engine/classes/MaterialVariant) , defines how a surface looks and how it behaves physically, including density, friction, elasticity, and sound. For details, see [Materials](/docs/parts/materials) .

-

A [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  defines only how a mesh looks. Use it for detailed surfaces like characters and hero props, where the appearance matters more than physical behavior.

Each triangle can only have one material. If a mesh needs several materials, such as skin and cloth on a character, split it into separate meshes by material.

## [Meshes](#meshes)[](#meshes)

-

Triangle budget:  An individual mesh can't exceed 20,000 triangles, which is about 65,535 vertices, and avatar items have their own, lower budgets. If you import a mesh over the limit, Studio automatically decimates it to fit, so reduce the triangle count yourself if you want to control the result. For all requirements, see [Mesh specifications](/docs/art/modeling/specifications) .

-

Size:  Each dimension of a [MeshPart](/docs/reference/engine/classes/MeshPart)  can be at most 2,048 studs. Studio automatically scales down larger imports to fit, so split very large environment pieces into meshes no bigger than 2,048 studs in any dimension.

-

Level of detail:  Each mesh's [RenderFidelity](/docs/reference/engine/classes/MeshPart#RenderFidelity)  lowers its [level of detail](/docs/parts/meshes#level-of-detail)  automatically as it moves away from the camera. In games that use [instance streaming](/docs/workspace/streaming) , [SLIM](/docs/workspace/streaming/slim)  can also generate and render lightweight versions of models when they're outside the streaming radius.

 ![A tree mesh and its texture maps combined to create a single tree.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png)

## [Lighting](#lighting)[](#lighting)

Set the overall look with [Lighting.LightingStyle](/docs/reference/engine/classes/Lighting#LightingStyle) :

-

[Realistic](/docs/reference/engine/enums/LightingStyle#Realistic)  produces naturalistic lighting and generates shadows and ambient occlusion dynamically. It doesn't use baked shadows or baked ambient occlusion.

-

[Soft](/docs/reference/engine/enums/LightingStyle#Soft)  produces a stylized, softer, more ambient look with less precise lights.

Roblox scales lighting quality automatically. As performance demands it, devices fall back to the lower-cost Soft lighting path, which happens most often on low-end mobile devices. [Lighting.PrioritizeLightingQuality](/docs/reference/engine/classes/Lighting#PrioritizeLightingQuality)  controls whether lighting quality or view distance scales down first. For all lighting properties, see [Lighting](/docs/environment/lighting) .

-

Interiors  get dynamic reflections from automatically generated probes, which mostly affect reflections and, to a lesser degree, diffuse lighting.

-

Exteriors  rely on lights, the [skybox](/docs/environment/skybox) , and [atmosphere](/docs/environment/atmosphere)  rather than a dynamic reflection system.

-

Small or thin details , like a hood over a face, might not cast reliable self-shadows. To guarantee the look you want, bake critical self-shadowing and ambient occlusion into the color map.

## [Characters](#characters)[](#characters)

There are two kinds of characters:

-

Platform avatars  follow Roblox's avatar requirements for polygon count, skeleton, materials, and attachments. They work across games and can use the clothing and accessories that players bring with them. For requirements, see [Character body specifications](/docs/avatar/character-bodies/specifications) .

-

Custom characters  don't have to follow avatar requirements. Their rigs can be arbitrary, and their budgets are the same as any other mesh.

Platform avatars use the R15  rig, which has 15 body parts that each correspond to one joint. This one-to-one mapping lets players swap individual body parts from the Marketplace. Avatars also use cages , standard meshes that describe the surface of a character, so that [layered clothing](/docs/avatar/layered-accessories/specifications)  can stretch to fit any body.

For more articulation, advanced R15  rigs, sometimes called R15+, support up to 37 additional optional bones, such as fingers, clavicles, and spine joints. They build on the standard R15 rig, so they use the same tech stack. For the required hierarchy and naming, see [Advanced R15 rigs](/docs/avatar/character-bodies/specifications#advanced-r15-rigs) . Custom characters aren't limited to R15 at all; their joint count and structure are limited only by performance on your target devices.

 ![A Roblox avatar wearing a glossy puffy jacket and jeans.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png)

## [Rigs and animation](#rigs-and-animation)[](#rigs-and-animation)

-

Skinning:  A vertex can be influenced by at most four bones or joints. For all rigging requirements, see [Mesh specifications](/docs/art/modeling/specifications#rigging-and-skinning) .

-

Physics:  Joints, parts, and mesh parts can be physically simulated, but there's no cloth simulation.

-

Facial animation:  Facial animation is joint-based. Heads animate with facial joints and skinning, posed to match the Facial Action Coding System (FACS), and Roblox doesn't support blend shape animation. For details, see [Dynamic heads](/docs/avatar/dynamic-heads) .

### [Animation workflow](#animation-workflow)[](#animation-workflow)

-

Import from your modeling tool:  An .fbx  export can include one animation track. To bring in several animations, export each one separately. For requirements, see [Animations](/docs/art/modeling/specifications#animations) .

-

Animate in Studio:  The [Animation Editor](/docs/animation/editor)  creates keyframe animations on any rig, with [inverse kinematics](/docs/animation/inverse-kinematics)  and a [curve editor](/docs/animation/curve-editor) . [Animation capture](/docs/animation/capture)  generates body and face keyframes from recorded or uploaded video.

-

Play animations in a game:  After you publish an animation, play it from a script or replace a character's default animations. For details, see [Use animations](/docs/animation/using) .

-

Build animation logic:  The [Animation Graph Editor](/docs/animation/graph-editor)  builds behaviors like blend trees in a node-based editor instead of scripts.

## [Asset workflow for teams](#asset-workflow-for-teams)[](#asset-workflow-for-teams)

Teams commonly keep the canonical versions of characters, building kits, and set dressing as [packages](/docs/projects/assets/packages)  in a dedicated assets place. Artists edit the packages there, and every place that uses them can update to the latest version. After a lead approves a change, artists copy it into the shared dev place or publish the package update. For the full team setup, see [Environments](/docs/projects/file-based-workflows#environments) .

## [Environment props](#environment-props)[](#environment-props)

-

Import and iterate:  Bring props in with the [3D Importer](/docs/studio/importer) . When you change a prop in your modeling tool, use [Reimport](/docs/art/modeling/reimport)  to update the existing instances and textures in place, with the same import settings.

-

Collision:  Set each mesh's [collision fidelity](/docs/parts/meshes#collision-fidelity)  to the simplest shape that works. Box  suits small or non-interactive objects, Hull  suits shapes without deep cavities, and Default  supports concave shapes.

-

Surfaces:  Use a [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  for detailed, unique props, and a [material](/docs/parts/materials)  or [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  for tiling surfaces like walls and floors.

-

Reuse:  Turn props that appear in many places into packages so that every copy updates together. For the team setup, see [Asset workflow for teams](#asset-workflow-for-teams) .

## [Terrain](#terrain)[](#terrain)

Terrain is a grid of voxels , 4×4×4 stud cells that each have a material. Sculpt and paint it with the [Terrain Editor](/docs/studio/terrain-editor) , generate it from [heightmaps and colormaps](/docs/parts/terrain#heightmaps-and-colormaps) , or create it from scripts.

-

Materials:  Terrain comes with a set of default materials. You can also paint [custom terrain materials](/docs/parts/custom-terrain-materials) , or apply [custom materials](/docs/parts/materials#custom-materials)  as overrides.

-

Appearance:  You can adjust terrain colors, water appearance, and grass animation. For all options, see [Environmental terrain](/docs/parts/terrain) .

## [Visual effects](#visual-effects)[](#visual-effects)

Effect objects render when you parent them to a part or an attachment. For an overview, see [Effects](/docs/effects) .

-

[Light sources](/docs/effects/light-sources) :  Point, spot, and surface lights.

-

[Particle emitters](/docs/effects/particle-emitters) :  Particles such as fire, smoke, sparks, and magic. A [flipbook](/docs/effects/particle-emitters#flipbooks)  texture animates a particle over its lifetime, with a 2×2, 4×4, 8×8, or custom frame layout. Leave space between frames. Clients turn off flipbooks when they're low on memory, so reuse flipbook textures and keep their resolution as low as you can.

-

[Beams](/docs/effects/beams)  and [trails](/docs/effects/trails) :  Textures drawn between two attachments, or between and behind two attachments as they move.

-

[Highlights](/docs/effects/highlighting) :  Outlines and fills that draw attention to objects.

-

Screen and sky effects:  [Post-processing effects](/docs/environment/post-processing-effects) , [atmosphere](/docs/environment/atmosphere) , and the [skybox](/docs/environment/skybox)  set the overall mood.

## [Audio](#audio)[](#audio)

-

Import requirements:  An audio file must be a single track in .mp3 , .ogg , .wav , or .flac  format, less than 20 MB and 7 minutes long, with a sample rate of 48 kHz or less. ID-verified creators can import 2,000 audio assets every 30 days, and unverified creators can import 100. For details, see [Audio assets](/docs/audio/assets) .

-

Licensed library:  The Creator Store has more than 100,000 free, professionally produced sound effects and music tracks from audio and music partners.

-

Playback:  [Audio objects](/docs/audio/objects)  play sounds positionally in the world or non-positionally, and [audio effects](/docs/audio/effects)  process them, such as with reverb or equalization. For an overview, see [Audio](/docs/audio) .

-

Authoring:  For tips on creating sounds in a digital audio workstation, see [Reaper](/docs/art/reaper) .

## [Plugins and tools](#plugins-and-tools)[](#plugins-and-tools)

You can install community plugins from the [Creator Store](/docs/production/creator-store#find-assets) , or build your own. For details, see [Studio plugins](/docs/studio/plugins) . Roblox also provides these tools for artists:

-

[Avatar Setup](/docs/avatar-setup) :  Processes custom models into avatar bodies and accessories, adding the components they need.

-

[Reimport](/docs/art/modeling/reimport) :  Updates imported meshes and textures in place from your source files.

-

[Project files](/docs/art/modeling/project-files) :  Blender, Maya, and .fbx  templates and reference files.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
