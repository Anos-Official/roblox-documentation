<!-- Source: https://create.roblox.com/docs/parts/meshes -->

Meshes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts/meshes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)

# Meshes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/meshes.md)

[MeshPart](/docs/reference/engine/classes/MeshPart)  objects are descendants of the [BasePart](/docs/reference/engine/classes/BasePart)  class. They represent meshes , which are collections of vertices, edges, and faces that make up a 3D object. Unlike parts, which you can directly create in Studio, you need to use a third-party modeling application like Blender or Maya to create meshes, then import them into Studio as [MeshPart](/docs/reference/engine/classes/MeshPart)  objects.

After importing a mesh into Studio, you can customize its rendering properties, such as textures, level of detail, and collision fidelity. In addition to importing your own meshes, you can also browse and select from user-uploaded meshes using the [Creator Store](/docs/production/creator-store) .

Roblox supports many types of meshes, as long as they adhere to the [general mesh specifications](/docs/art/modeling/specifications) . A basic mesh consists of at least one mesh object and one texture:

![A tree mesh object without a texture.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Example.png) A mesh object sets the shape and geometry of the 3D object

![The texture image map for the leaves of the tree in the previous image.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Texture-Example.png) A texture image map applies a surface appearance and color

![A tree mesh object with the leaves texture applied.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png) The mesh and texture combine to make a unique custom 3D object

Studio also supports meshes with components for creating avatar character models or accessories, such as [rigging and skinning](#rigging-and-skinning)  data.

You can sell [MeshPart](/docs/reference/engine/classes/MeshPart)  assets as avatar bodies, accessories, and clothing on the Marketplace. See [Avatar](/docs/avatar)  for more information.

## [Import meshes](#import-meshes)[](#import-meshes)

You can import meshes into Studio using the [Importer](/docs/studio/importer) . With this tool, you can preview and examine meshes before importing them into your workspace or Toolbox , such as verifying texture, rigging, skinning, and animation data. It also flags issues and rejects meshes with error.

If the mesh file you are importing contains objects using specific naming conventions or contains facial animation data, the Importer automatically detects and converts them into the following objects instead of [MeshPart](/docs/reference/engine/classes/MeshPart) :

-

[Attachment](/docs/reference/engine/classes/Attachment)  — Objects with _Att  at the end of their names.

-

[WrapTarget](/docs/reference/engine/classes/WrapTarget)  — Objects with _OuterCage  at the end of their names.

-

[WrapLayer](/docs/reference/engine/classes/WrapLayer)  — Objects with both _InnerCage  _OuterCage  at the end of their names.

-

[FaceControls](/docs/reference/engine/classes/FaceControls)  — Objects containing avatar character heads and the appropriate facial animation data.

If you want to bulk-import meshes along with non-3D assets, such as images and audio, you can use the [Asset Manager](/docs/projects/assets/manager) ; note, however, that it doesn't support importing meshes with rigging, skinning, and animation data, accessories, or characters with facial animations.

## [Customize meshes](#customize-meshes)[](#customize-meshes)

Unlike basic parts, meshes have more customization options that you can adjust for advanced rendering fidelity.

### [Texture](#texture)[](#texture)

Textures  contribute to the visual appearance of meshes by adding 2D details such as color and patterns. Studio allows you to either apply one texture using the [MeshPart.TextureID](/docs/reference/engine/classes/MeshPart#TextureID)  property, or apply up to four physically-based rendering (PBR) textures within a [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  child object of the mesh or made with a [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  and set in the mesh's [MeshPart.MaterialVariant](/docs/reference/engine/classes/MeshPart#MaterialVariant)  property. PBR textures allow you to represent realistic shading and lighting by using multiple types of texture images, or maps, on a single object.

PBR Textures Single Texture

Studio supports four PBR texture maps, each corresponding to a visual characteristic of an object's surface appearance. Combining multiple texture maps can more accurately simulate color, roughness, and reflectivity in any lighting environment, and enhance the visual elements of your assets and environment. For more information on PBR textures and the texture maps, see [PBR Textures](/docs/art/modeling/surface-appearance) .

![Example of SurfaceAppearance applied to a Bush Mesh](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg)

![Example of SurfaceApperance applied to a Rock Mesh](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-3.jpg)

You can apply PBR textures using one of the following objects:

-

[SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  — Applies PBR textures to the mesh surface and doesn't affect its geometry.

-

[MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  — Represents a custom material that not only applies PBR textures to the mesh surface but also adds physical properties.

To add PBR textures to a mesh:

SurfaceAppearance MaterialVariant

1.

In the [Explorer](/docs/studio/explorer)  window, hover over the [MeshPart](/docs/reference/engine/classes/MeshPart)  object. Click the ⊕  button and select [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance) .

2.

In the [Properties](/docs/studio/properties)  window, edit the properties corresponding to the PBR texture maps.

If you both add [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  as a child object and set the [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  in the mesh's properties, Studio only applies the texture map settings of the [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  object to the mesh. The mesh still has all other settings of the [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  object, such as custom physical properties.

### [Level of detail](#level-of-detail)[](#level-of-detail)

You can dynamically control a mesh's level of detail using its [Enum.RenderFidelity](/docs/reference/engine/enums/RenderFidelity)  property. The default value is [Automatic](/docs/reference/engine/enums/RenderFidelity#Automatic) , meaning the mesh's detail is based on its distance from the camera as outlined in the following table.

| Distance from camera | | Render fidelity | | Example |
| --- | --- |
| Less than 250 studs | | Highest | | ![A potion mesh object that is rendered in the highest level of detail.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Render-Fidelity-High.jpg) |
| 250-500 studs | | Medium | | ![A potion mesh object that is rendered in a medium level of detail. Its edges are more jagged than the previous image.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Render-Fidelity-Medium.jpg) |
| 500 or more studs | | Lowest | | ![A potion mesh object that is rendered in the lowest level of detail. Its edges are more jagged than the previous image, and the liquid is no longer shiny.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Render-Fidelity-Low.jpg) |

### [Collision fidelity](#collision-fidelity)[](#collision-fidelity)

Collision fidelity  determines how closely the visual representation of a mesh matches its physical bounds. The [MeshPart.CollisionFidelity](/docs/reference/engine/classes/MeshPart#CollisionFidelity)  property has the following options:

-

Box  — Creates a bounding collision box, ideal for small or non‑interactive objects.

-

Hull  — Generates a convex hull, suitable for objects with less pronounced indentations or cavities.

-

Default  — Produces an approximate collision shape that supports concavity, suitable for complex objects with semi-detailed interaction needs.

-

PreciseConvexDecomposition  — Offers the most precise fidelity but still not a 1:1 representation of the visual. This option has the most expensive performance cost and takes longer for the engine to compute.

-

Tunable  — Setting [MeshPart.CollisionFidelity](/docs/reference/engine/classes/MeshPart#CollisionFidelity)  to [Tunable](/docs/reference/engine/enums/CollisionFidelity#Tunable)  reveals a [CollisionPrecision](/docs/reference/engine/classes/MeshPart#CollisionPrecision)  slider in the Properties  window. Sliding up produces more precise, more expensive collision geometry, while sliding down produces coarser, cheaper geometry, all without switching to a different fidelity option. The default [CollisionPrecision](/docs/reference/engine/classes/MeshPart#CollisionPrecision)  value isn't fixed; the engine intelligently picks the appropriate precision, and therefore cost, based on the size of the mesh.

Original Mesh Default Box Hull Precise Tunable

![Original mesh of castle tower](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-MeshPart.jpg)

To view collision fidelity in Studio, toggle on Collision fidelity  from the [Visualization Options](/docs/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

For more information on the performance impact of collision fidelity options and how to mitigate them, see [Improve performance](/docs/performance-optimization/improve#physics-computation) . For an in-depth walkthrough on how to choose a collision fidelity option that balances your precision and performance requirements, see [Set physics and rendering parameters](/docs/tutorials/curriculums/environmental-art/optimize-your-experience#review-physics-and-rendering-parameters) .

## [Rigging and skinning](#rigging-and-skinning)[](#rigging-and-skinning)

Rigging  is the process of connecting a mesh with an internal poseable skeleton rig. Rigged meshes allow mesh surfaces to rotate and move using internal bones within a model, such as a character's knee or elbow. Skinning  a rigged mesh allows the rigged mesh object to deform, stretch, and bend in a more realistic manner.

Without skinning, the entire head mesh rotates on a single axis

With skinning, the head mesh bends naturally at the neck, and the bottom of the neck stays connected to the torso

For more information on rigging and skinning, see [Rigging and skinning](/docs/art/modeling/rigging) . After rigging a mesh, you can add animation and poses to it using the Animation Editor . See [Create an animation](/docs/animation/editor#create-an-animation)  for more information. Marketplace 3D assets, such as avatar clothing and bodies, also require rigging and skinning. See [Avatar](/docs/avatar)  for more information on requirements for Marketplace assets.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
