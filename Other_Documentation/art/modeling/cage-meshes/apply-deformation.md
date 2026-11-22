<!-- Source: https://create.roblox.com/docs/art/modeling/cage-meshes/apply-deformation -->

Apply deformation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/cage-meshes/apply-deformation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Modeling
6. /
7. Cage meshes

# Apply deformation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/cage-meshes/apply-deformation.md)

Once a target caged mesh and a layered caged mesh are imported into your experience, you can apply a deformation by parenting both [MeshParts](/docs/reference/engine/classes/MeshPart)  within a [Model](/docs/reference/engine/classes/Model)  and adding a [WeldConstraint](/docs/reference/engine/classes/WeldConstraint) .

 ![A grey twisted target, a red-and-white checker cube, and the checker cube reshaped to match the twisted target, in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Apply-Deformation-Hero.png)

## [Deform a mesh](#deform-a-mesh)[](#deform-a-mesh)

Download the reference files to follow along. The Blender project contains every shape, and each .fbx  imports as a ready-made target or layered mesh with its cages.

| ** File** | | ** Description** |
| --- | --- |
| [Cage-Mesh-Examples.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cage-Mesh-Examples.blend) | | A Blender project containing every target and layered mesh in this guide, with their cages. |
| [Cube_Target.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cube_Target.fbx) | | A cube target, ready to import as a [MeshPart](/docs/reference/engine/classes/MeshPart)  with a [WrapTarget](/docs/reference/engine/classes/WrapTarget) . |
| [Sphere_Target.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Sphere_Target.fbx) | | A sphere target, ready to import as a [MeshPart](/docs/reference/engine/classes/MeshPart)  with a [WrapTarget](/docs/reference/engine/classes/WrapTarget) . |
| [Cube-Flattened_Target.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cube-Flattened_Target.fbx) | | A flattened cube target, ready to import as a [MeshPart](/docs/reference/engine/classes/MeshPart)  with a [WrapTarget](/docs/reference/engine/classes/WrapTarget) . |
| [Layered-Mesh1.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Layered-Mesh1.fbx) | | A layered mesh with inner and outer cages, ready to import as a [MeshPart](/docs/reference/engine/classes/MeshPart)  with a [WrapLayer](/docs/reference/engine/classes/WrapLayer) . |
| [Layered-Mesh2.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Layered-Mesh2.fbx) | | A second layered mesh, ready to import as a [MeshPart](/docs/reference/engine/classes/MeshPart)  with a [WrapLayer](/docs/reference/engine/classes/WrapLayer) . |

1.

Ensure that your workspace includes two 3D objects: a target [MeshPart](/docs/reference/engine/classes/MeshPart)  and a layered [MeshPart](/docs/reference/engine/classes/MeshPart) .

1.

Confirm the target has a [WrapTarget](/docs/reference/engine/classes/WrapTarget)  and the deforming mesh has a [WrapLayer](/docs/reference/engine/classes/WrapLayer) .

![The Studio Explorer showing the target MeshPart with a child WrapTarget object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapTarget-Explorer.png) Target: a [WrapTarget](/docs/reference/engine/classes/WrapTarget)

![The Studio Explorer showing the layered MeshPart with a child WrapLayer object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapLayer-Explorer.png) Deforming mesh: a [WrapLayer](/docs/reference/engine/classes/WrapLayer)

2.

(Optional) If testing or applying multiple deformations, make a copy of your layered mesh to ensure you have an original copy later.

2.

In the Explorer, parent both target and layered [MeshParts](/docs/reference/engine/classes/MeshPart)  in one [Model](/docs/reference/engine/classes/Model) .

 ![The Studio Explorer showing the target and layered MeshParts grouped in one Model.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Group-And-Align.png)

3.

Add a [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  to the layered [MeshPart](/docs/reference/engine/classes/MeshPart) , then:

1.

Set Part0  to the layered mesh.

2.

Set Part1  to the target mesh.

 ![The WeldConstraint properties with Part0 set to the layered mesh and Part1 set to the target.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WeldConstraint-First-Layer.png)

4.

In the Properties window, change [WrapLayer.Order](/docs/reference/engine/classes/WrapLayer#Order)  from the default value to another number, such as 2  or 5 .

1.

Changing this property triggers the deformation in the 3D workspace so the layered mesh reshapes to match the shape of the target.

2.

If the order is incorrect with other layers, such as a T-shirt wrapping over a sweater, you can change this property at any time.

 ![The WrapLayer properties with the Order property set.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapLayer-Order-Property.png)

5.

(Optional) The deformation is retained after it computes, so you can delete the duplicated layered mesh and the [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  and reset [WrapLayer.Order](/docs/reference/engine/classes/WrapLayer#Order) , leaving a single deformed mesh. This is useful to simplify your workspace when applying multiple deformations.

 ![A grey cube target beside the checker layered mesh deformed onto it, in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Basic-Deformation.png)

6.

Experiment further. Try deforming the reference layered meshes onto the other target shapes, or [deform multiple meshes onto a single target](#deform-multiple-meshes-to-a-single-target) .

## [Deform multiple meshes to a single target](#deform-multiple-meshes-to-a-single-target)[](#deform-multiple-meshes-to-a-single-target)

You can continue to add layered meshes to a target by repeating the process of adding a layered mesh and a weld. Every time a layered mesh is added to a target, Roblox recalculates the surface of the mesh, allowing you to continually add to your target mesh.

Every mesh you layer onto a target must share the same UV layout as the target. Roblox pairs each layer to the target by UV, so mismatched UVs won't deform correctly.

1.

With your existing deformed mesh in the workspace, add a new layered [MeshPart](/docs/reference/engine/classes/MeshPart)  into your [Model](/docs/reference/engine/classes/Model) .

 ![The Studio Explorer showing a second layered MeshPart added to the Model alongside the first.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Add-Second-WrapLayer.png)

2.

Add a [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  to the new layered [MeshPart](/docs/reference/engine/classes/MeshPart) , then:

1.

Set Part0  to the original layered mesh.

2.

Set Part1  to the new layered mesh.

 ![The WeldConstraint properties with Part0 set to the first layered mesh and Part1 set to the second.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WeldConstraint-Second-Layer.png)

3.

Change [WrapLayer.Order](/docs/reference/engine/classes/WrapLayer#Order)  in the Properties window. Changing this property triggers the deformation, and the mesh reshapes to match the target. Each layer's [WrapLayer.Order](/docs/reference/engine/classes/WrapLayer#Order)  determines which one renders on top.

![The second layer rendering on top of the first in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Ordering-Example-1.png) The first layer's [WrapLayer.Order](/docs/reference/engine/classes/WrapLayer#Order)  is 1  and the second layer's is 2 , so the second layer renders on top.

![The first layer rendering on top of the second in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Ordering-Example-2.png) Updating the first layer's [WrapLayer.Order](/docs/reference/engine/classes/WrapLayer#Order)  to 2 , and setting the second layer to 1 , brings the first layer on top.

## [Deform an accessory on an avatar](#deform-an-accessory-on-an-avatar)[](#deform-an-accessory-on-an-avatar)

All Roblox avatars share the same standard body cage. Because cages pair by UV, an accessory caged to that shared layout fits every avatar body. Note that the example meshes in this guide use their own cages, so they aren't compatible with Roblox's standard body cage.

![Head and upper-torso cage meshes shown as wireframes on an avatar.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Visual.png)  Head and Upper Torso cage mesh objects (wireframe)

![The Explorer showing cage objects on each of the 15 avatar body parts.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Data-Model.png) Cage objects must exist for each of the 15 body parts

When creating avatar characters and avatar accessories, a similar process of layering applies to a [Humanoid](/docs/reference/engine/classes/Humanoid)  character's body cages, and the layered accessory pipeline composes the layered mesh automatically. This allows fitting across body types and transferring skinning data through [WrapLayer.AutoSkin](/docs/reference/engine/classes/WrapLayer#AutoSkin) .

If you are creating your own custom non-Marketplace characters that utilize a unique cage / UV solution, see [Layered accessories on non-R15](/docs/characters/appearance#layered-accessories-on-non-r15) .

For an overview of creating your first layered accessory, see the following video:

For the full avatar workflow, see [Layered accessories](/docs/avatar/layered-accessories) , the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool) , and [Automatic Skinning Transfer](/docs/avatar/automatic-skinning-transfer) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
