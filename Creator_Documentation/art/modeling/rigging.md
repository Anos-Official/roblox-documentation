<!-- Source: https://create.roblox.com/docs/en-us/art/modeling/rigging -->

Rigging and skinning | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/rigging.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Modeling

# Rigging and skinning

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/rigging.md)

Rigging  is the process of connecting a mesh with an internal poseable skeleton rig and bone structure. Rigged meshes allow mesh surfaces to rotate and move where internal bones are placed within the model during the modeling process. Rigging is often performed in conjunction with skinning , creating a natural looking stretch and bend when models are animated or repositioned. You can create rigged meshes with third-party software such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) .

A normal model can only rotate on its pivot point.

A rigged model (or mesh) can rotate with any bone of its associated rig.

A rigged model with no skinning data.

A skinned model that bends organically with the bone rotation.

See the following resources to learn the basics and intermediate steps required to skin models in Blender:

-

[Rig a simple mesh](/docs/en-us/art/modeling/rig-a-simple-mesh)

-

[Skin a simple mesh](/docs/en-us/art/modeling/skin-a-simple-mesh)

-

[Rig a humanoid model](/docs/en-us/art/modeling/rig-a-humanoid-model)

-

[Skin a humanoid model](/docs/en-us/art/modeling/skin-a-humanoid-model)

## [Rigs and bones](#rigs-and-bones)[](#rigs-and-bones)

The rig , or bone structure, within a rigged mesh creates additional poseable points for the 3D model in Studio. By rotating or moving the bones of a mesh, the parts of the mesh assigned to those bones can move independently from the rest of the mesh. The assignment of influence between meshes and bones, such as a LowerLeftArm  bone driving the movement of the LowerLeftArm  geometry, is set in a third-party application like Blender or Maya. When imported into Studio, Roblox saves this influence assignment data to the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  asset data.

Once you successfully [import](/docs/en-us/parts/meshes#import-meshes)  a rigged mesh model into Studio, Studio represents this rig structure with [Bone](/docs/en-us/reference/engine/classes/Bone)  instances that you can then pose and animate. You can view bones in Studio by enabling Show Constraint Details  from the View  menu, or when you are using the [Animation Editor](/docs/en-us/animation/editor) .

When [Bone](/docs/en-us/reference/engine/classes/Bone)  objects are used in animation, they affect the appearance of the parts but don't change the physical shape in cases such as [collision detection](/docs/en-us/workspace/collisions) .

![A translucent humanoid outline, showing various sphere points where the constraints exist.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Constraint-Details.jpg) Constraint Details enabled

![A translucent humanoid outline, showing 15 pink bones objects over various limbs.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Bone-Visualization.jpg) When using the Animation Editor

## [Types of rigs](#types-of-rigs)[](#types-of-rigs)

Rigged models use a naming convention starting with "R" and ending with the number of individual meshes that make up the model. This is used to quickly identify the type and number of meshes that a model has. Although R6 and R15 models are common, a model can be of varying subjects, sizes and can have any number of individual meshes, such as a R5, R20, or R200.

-

R1  refers to a single mesh that is rigged, or associated with an internal skeleton structure. Many models, such as a tree or accessory item, are good candidates to be made into an R1 model. Even NPC humanoid characters can be created as R1 models, but they will not be able to take full advantage of the animation and humanoid options available for R15 characters.

See [Rig a simple mesh](/docs/en-us/art/modeling/rig-a-simple-mesh)  for instructions on turning a basic mesh into an R1 model in Blender.

-

R15  typically refers to humanoid models used as player or avatar characters. An R15 model is made up of 15 specific meshes that are parented to a single [R15 rig](/docs/en-us/avatar/character-bodies/specifications#rigging) . An R15 character model often includes skinning data to allow the model to bend and pose naturally. Roblox uses the R15 standard for all avatars, and requires the [technical specifications](/docs/en-us/avatar/character-bodies/specifications)  to ensure universal behavior and quality.

See [Rig a humanoid model](/docs/en-us/art/modeling/rig-a-humanoid-model)  for instructions on turning a character model into an R15 humanoid model in Blender.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
