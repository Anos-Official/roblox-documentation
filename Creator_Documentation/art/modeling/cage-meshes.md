<!-- Source: https://create.roblox.com/docs/en-us/art/modeling/cage-meshes -->

Cage meshes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/cage-meshes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Modeling
6. /
7. Cage meshes

# Cage meshes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/cage-meshes/index.md)

Cage meshes  are invisible surfaces of a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  that allow other supported meshes to stretch and deform over each other. With cage meshes, you can create a set of meshes that can dynamically resize, reshape, and layer over another mesh of any shape or size.

They power layered accessories  — 3D accessories such as jackets, dresses, and cardigans that stretch to fit a character body and stack naturally on top of one another — and you can also apply them to any [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) , as long as all the cage meshes [share the same UV mapping](#how-cages-pair) .

Reshape volume Deform any shape Layered accessories

![A mesh's outer cage in Blender beside a plain cube and a checker mesh whose volume the cage has reshaped in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Outer-Cage-Hero.png) An outer cage is an invisible surface that can reshape a mesh's volume.

A cage mesh is a simplified copy of a render mesh that defines a wrapping surface. Unlike Roblox's [collision system](/docs/en-us/workspace/collisions) , which works universally, cage meshes can only work with other paired cage meshes.

To fit one mesh over another, Roblox pairs the vertices of one cage with those of the other by their UV coordinates, then reshapes the render mesh so that its cage matches the target cage. Cage meshes are typically configured in a modeling tool such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) .

In specific cases, you can also create and reshape cage meshes programmatically at runtime, such as in experiences that let users build and customize avatar items. See [Avatar in-experience creation](/docs/en-us/avatar/in-experience-creation) .

## [Cage mesh components](#cage-mesh-components)[](#cage-mesh-components)

In Studio, cage meshes are children of a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  and are represented by descendants of the [BaseWrap](/docs/en-us/reference/engine/classes/BaseWrap)  class:

| Cage mesh type | | In Blender | | In Studio |
| --- | --- |
|

[WrapTarget](/docs/en-us/reference/engine/classes/WrapTarget)
 The initial caged surface that other paired cage meshes can target.
Every caging deformation requires a target mesh.

 | | ![The Blender Outliner showing a render mesh with a single _OuterCage.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Target.png)

A render mesh with a single _OuterCage  mesh.

 | | ![The Studio Explorer showing a MeshPart with a child WrapTarget object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapTarget-Explorer.png)

A [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  with a child [WrapTarget](/docs/en-us/reference/engine/classes/WrapTarget) .

 |
|

[WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer)
 Allows its parent [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  to wrap around a [WrapTarget](/docs/en-us/reference/engine/classes/WrapTarget) , such as a layered clothing accessory wrapping over an avatar body.
 All targets and layers must share identical UVs.

 | | ![The Blender Outliner showing a render mesh with an _InnerCage and an _OuterCage.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Layer.png)

A render mesh with an _InnerCage  and an _OuterCage  mesh.

 | | ![The Studio Explorer showing a MeshPart with a child WrapLayer object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapLayer-Explorer.png)

A [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  with a child [WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer) .

 |

Because a cage behaves like a component of its parent, a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  is the only valid parent for these objects. You author cage meshes alongside your render mesh in a modeling application like [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview)  and import them together.

When you import a model that contains cage meshes, make sure Uses Cages  is enabled in the [3D Importer](/docs/en-us/studio/importer#import-settings)  so that Studio detects the cages and creates the cage objects for you.

## [How cages pair](#how-cages-pair)[](#how-cages-pair)

Roblox pairs cages by their UV coordinates  rather than by position, so any two cages that share a UV layout can wrap over each other, even when their shapes differ. This is what lets a single accessory fit bodies of completely different shapes and sizes without remodeling it for each one.

 ![A shared UV layout in the Blender UV editor, laid out as an unwrapped cube cross.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/UV-Map.png)

The following shapes are completely different, but they all share the identical UV map above, so a single layered mesh can deform onto any of them.

![A cube in the Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Cube-shape.png) Cube

![A sphere in the Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Sphere-shape.png) Sphere — shaped from a cube

![A flattened, twisted shape in the Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Flatten-Shape.png) Flattened — sculpted from a cube

## [Create caged assets](#create-caged-assets)[](#create-caged-assets)

Use the following guides to create caged assets. Each guide includes downloadable files and basic implementation steps to follow along.

-

[Create cages in Blender](/docs/en-us/art/modeling/cage-meshes/create-cages)  — author the outer and inner cages for a model and import them into Studio.

-

[Apply deformation](/docs/en-us/art/modeling/cage-meshes/apply-deformation)  — deform a caged mesh onto a target with a [WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer) .

-

[Create your own layered accessory](/docs/en-us/art/accessories/creating)  — create a layered accessory using Roblox's provided reference cages.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
