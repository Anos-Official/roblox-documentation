<!-- Source: https://create.roblox.com/docs/en-us/art/characters/creating/caging -->

Caging character head | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/creating/caging.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Caging character head

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/creating/caging.md)

Caging  is the process of updating the [cage mesh component](/docs/en-us/avatar/character-bodies#cage-meshes)  of your avatar character. To allow your character to correctly wear layered accessories, you must update the default template cage mesh object to match the sculpting changes you made to your custom character.

Since this tutorial only applies modeling changes to the head, the caging instructions below only apply to the Head_OuterCage  object. If you make geometry changes to other parts of the character, you must also adjust those specific _OuterCage  objects to match your sculpting changes.

Do not delete any vertices or faces of the provided cages. Destructive modification of the cages can cause import issues and prevent the character model from equipping clothing and cosmetics.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Pre-Caging.png)  Default head cage mesh no longer fits over sculpted head

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Caging.png) Head cage mesh after adjustment

If your character body shape incorporates many changes with different body parts, it may be more efficient to use the [Blender Cage Template](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Body_Cage_Templates.zip) . This Blender project file includes a helper full-body std_cage_deformable  mesh to automatically apply vertex changes to the individual body-part cages at the same time.

To begin caging your character:

1.

In the Layout  tab, hide everything in the Outliner except the Head_OuterCage  and the Head_Geo  objects.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Caging-Outer-Cage-Objects.png)

2.

With Head_OuterCage  selected, navigate to Object Properties  > Viewport Display  and set the Display As  to Wire .

3.

Switch to Edit  mode, then enable X-Axis symmetry  and Topology Mirror  to ensure you are making symmetrical vertex changes to your cage.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Caging-Symmetry-Settings.png)

4.

Using the Grab  tool (G ), click and grab parts of the cage mesh and align it to fit tightly over the goblin head mesh. Keep the following in mind:

-

Never delete any of the cage vertices.  Missing vertices can cause errors and issues with equipping clothing accessories.

-

If editing the base of your head cage, ensure that the base of the Head  cage aligns with the top of the UpperTorso  cage.

-

In different Select modes, hold Shift  and click multiple vertices/edges/faces to select and edit the geometry.

-

You can verify a tight fit by grabbing vertices and moving them into the Head_Geo  mesh to check where the meshes intersect and moving the cage vertices until the cage mesh just covers the head mesh.

-

Toggle visibility on your different mesh objects to improve visibility and access to vertices.

5.

After the wireframe is tightly fitted over the head mesh, set the Display As  back to Solid  and spot check and fix any intersecting vertices.

Your final product should feature a cage mesh that sits directly over the head mesh without any of the Head_Geo  geometry intersecting through the solid sections of the cage.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Caging.png)

For a comparison reference, you can download [this version of the tutorial project with caging completed](https://prod.docsiteassets.roblox.com/assets/art/reference-files/checkpoint/3_Goblin-caged.blend) .

[Next](/docs/en-us/art/characters/creating/combine-head-geometry)[Previous](/docs/en-us/art/characters/creating/texturing-pbr)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
