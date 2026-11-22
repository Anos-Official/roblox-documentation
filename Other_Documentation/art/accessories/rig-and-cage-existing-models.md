<!-- Source: https://create.roblox.com/docs/art/accessories/rig-and-cage-existing-models -->

Rigging and caging models (Blender) | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/accessories/rig-and-cage-existing-models.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Avatar items

# Rigging and caging models (Blender)

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/accessories/rig-and-cage-existing-models.md)

You can use a third party modeling tool, such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) , to modify an existing 3D object into a layerable 3D model that you can [import and convert](/docs/avatar/accessory-fitting-tool)  into Studio as an [Accessory](/docs/reference/engine/classes/Accessory) . To create a layered model, you must parent  (Blender) or bind  (Maya) a 3D model to a mannequin armature and then modify two additional meshes to fit around the inner and outer surface of the accessory model.

This guide covers the basic workflow for converting a 3D model into a layerable model in Blender using the following steps:

1.

[Importing](#import)  a 3D asset into a template Blender project file.

2.

[Parenting](#parent-and-weight)  the imported mesh object to the project file's armature rig with Blender's Automatic Weights feature.

1.

Manual skinning is not covered, see [Skin a simple mesh](/docs/art/modeling/skin-a-simple-mesh)  for an overview of manual skinning.

3.

[Editing](#edit-inner-and-outer-cage-meshes)  the Inner and Outer Cage meshes to represent the inner and outer surface of the model.

A full list of asset requirements for a layered model can be found in [Layered model specifications](/docs/avatar/rigid-accessories/specifications) .

This guide uses [Blender version 3.0](https://www.blender.org/download/releases/3-0/) . If you are using another version of Blender, there may be minor differences in UI and settings.

## [Import](#import)[](#import)

Set up the project by opening the [rig template project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip)  and importing the [sample accessory model](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Tshirt-model.fbx) .

To import and parent the accessory model:

1.

In Blender, open the [rig template project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip) . This file contains the default armature required for layered accessories.

 ![Blender Mannequin Template Project](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-template-opened.png)

2.

In the Outliner, toggle the Hide icon to visually remove any non-armature objects in your workspace, such as Attachments.

3.

In the File Menu, select Import  and click FBX (.fbx) . Select the accessory model file you intend to fit onto the mannequin. The accessory populates in the workspace and, depending on how the asset was modeled, may need resizing or adjustment to fit on the mannequin.

## [Parent and weight](#parent-and-weight)[](#parent-and-weight)

For this basic accessory, parent the imported mesh to the template mannequin armature using Blender's [Automatic Weights](https://docs.blender.org/manual/en/latest/animation/armatures/skinning/parenting.html#with-automatic-weights)  feature. Parenting the accessory model mesh to the armature in this way enables the 3D model to move and deform naturally with the character in Studio.

Complex clothing and accessory items with moving parts may require more precise skinning with Blender's [Weight Painting](https://docs.blender.org/manual/en/3.5/grease_pencil/modes/weight_paint/introduction.html#weight-paint)  or other skinning tools. See [Skin a simple mesh](/docs/art/modeling/skin-a-simple-mesh)  for an example of manual skinning.

To parent the mesh object with the mannequin armature:

1.

In the Outliner, temporarily hide both of the Cage objects to expose the Armature by toggling the Hide icon.

2.

In the Workspace, click the mesh object, then hold Shift  and click  the mannequin's armature.

3.

Right click, or use Ctrl P  (⌘ P ) to parent the accessory to the armature by selecting Automatic Weights .

4.

Reduce visual clutter by hiding all objects except the cages  and model . Click on the ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-hide-symbol.png)  symbol next to the object in the Outliner panel.

## [Edit inner and outer cage meshes](#edit-inner-and-outer-cage-meshes)[](#edit-inner-and-outer-cage-meshes)

After parenting and weighting your clothing item, you can start adding the cage meshes to your clothing to indicate the inner and outer surfaces of your clothing.

When setting up the cages, the accessory model needs to fit on top of the inner cage and then the outer cage must be adjusted to fit tightly over the model object.

You can quickly add these two full-body meshes from the [Clothing_Cage_Template.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip)  into your existing project.

Don't delete vertices or alter the UVs on the Inner or Outer Cages as this can cause errors when importing in Studio or when equipping onto a character.

To quickly add clothing cages to your project:

1.

Download the [Clothing_Cage_Template.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip)  project.

2.

In your current Blender project, switch to Object Mode and navigate to File  > Append . A file browser displays.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-append.png)

3.

Click on the Clothing_Cage_Template.blend file and navigate to the Object  folder.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-append-cages.png)

4.

In the Object folder, hold Shift  and select both YourClothingName_InnerCage  and YourClothingName_OuterCage  and click Append . The two cage mesh objects populate in your project.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-workspace-cages.png)

To modify cages for your accessory model:

1.

In the Outliner panel, rename the _InnerCage  and _OuterCage  meshes to match the imported mesh object (ex. Tshirt_InnerCage, Tshirt_OuterCage). Make sure this exactly matches the mesh name that you imported.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-selecting-cage-in-outlier.png)

2.

In the Outliner window, select the _OuterCage mesh and switch to Edit Mode  Tab .

3.

In the Viewport, enable X-Ray  view and Materials View  to improve visibility and access to the vertices of the outer cage mesh.

4.

While in Edit Mode, adjust the vertices with the Edit Mode tools so that the Outer Cage completely covers the top of the accessory.

When manipulating vertices, try to keep each face (the space between vertices) consistently sized and retain symmetry wherever possible. Use the symmetry toggles on the top right of the Viewport when applicable.

A finished outer cage should completely cover the accessory with minimal extra space. For comparison, you can download a [completed caged version](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Tshirt-caged.fbx)  of the Tshirt model.

When finished with the caging and modeling of your asset, see [Exporting requirements](/docs/art/modeling/export-requirements#blender)  for details on exporting the model from Blender.

After exporting, see [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  and [Converting clothing accessories tutorial](/docs/art/accessories/creating/converting)  for instructions on importing and converting the model into a usable accessory.

## [Tips for editing cages](#tips-for-editing-cages)[](#tips-for-editing-cages)

The following tips may be helpful when manipulating your cage vertices:

-

On the top-right of the Viewport, toggle different [Viewport Shading](https://docs.blender.org/manual/en/latest/editors/3dview/display/shading.html)  options, such as Material Preview  and X-Ray , when necessary to better access vertices and view your caging progress.

-

You can hide vertices you're currently not adjusting by using Hide  (H ) and Unhide  (Alt H ; ⌥ H ).

-

Multiple vertices can be selected and adjusted at the same time. Use Move , Scale , or any other Blender tools to make adjustments to multiple vertices at once.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
