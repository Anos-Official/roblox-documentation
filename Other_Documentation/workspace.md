<!-- Source: https://create.roblox.com/docs/workspace -->

3D workspace | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)

# 3D workspace

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/index.md)

[Workspace](/docs/reference/engine/classes/Workspace)  is a container service that holds objects that you want the Roblox Engine to render in the 3D world. You typically will add these objects to the workspace:

-

[BasePart](/docs/reference/engine/classes/BasePart)  objects, which includes both [Part](/docs/reference/engine/classes/Part)  and [MeshPart](/docs/reference/engine/classes/MeshPart)  objects.

-

[Attachment](/docs/reference/engine/classes/Attachment)  objects, which you can attach to special effect generators like a [ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter) , UI objects like a [BillboardGui](/docs/reference/engine/classes/BillboardGui) , physical [Constraints](/docs/reference/engine/classes/Constraint) , and more.

-

[Model](/docs/reference/engine/classes/Model)  objects that organize geometric groupings.

-

[Script](/docs/reference/engine/classes/Script)  objects that are parented by other objects in the workspace. Scripts aren't rendered but can affect another object's rendering.

## [Parts](#parts)[](#parts)

[Part](/docs/reference/engine/classes/Part)  objects represent the primitive building blocks in Roblox. By default, all parts have their physics simulated and are rendered if they appear in the 3D workspace. Parts can take the shape of blocks, spheres, cylinders, wedges, or corner wedges. In addition, [TrussPart](/docs/reference/engine/classes/TrussPart)  acts as a truss beam that characters can climb like a ladder.

![A single Block part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Block.png) Block

![A single Sphere part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Sphere

![A single Cylinder part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Cylinder.png) Cylinder

![A single Wedge part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Wedge.png) Wedge

![A single Corner Wedge part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Corner-Wedge.png) Corner Wedge

You can also apply [solid modeling](/docs/parts/solid-modeling)  operations to parts, such as union or negate, to combine them into something more complex like bowls or hollow pipes.

## [Meshes](#meshes)[](#meshes)

A [MeshPart](/docs/reference/engine/classes/MeshPart)  is an object that represents a mesh (a collection of vertices, edges, and faces that make up a 3D object). You typically create meshes using third-party software such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) , then import them as a [MeshPart](/docs/reference/engine/classes/MeshPart)  using Studio.

Meshes can include far more detail than any solid modeling you can do in Studio. They can also have internal rigs and textures, allowing you to create lifelike objects that you can pose and animate.

![A high-quality treasure chest mesh with a texture.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mesh-Textured.jpg) Mesh with texture

![A realistic looking leafy bush with shadows and depth.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mesh-SurfaceAppearance.jpg) Mesh with SurfaceAppearance

## [Terrain](#terrain)[](#terrain)

The [Terrain](/docs/reference/engine/classes/Terrain)  object allows you to generate and sculpt detailed and realistic terrain environments, such as mountains, bodies of water, grass-covered hills, or a flat desert. Using the [Terrain Editor](/docs/studio/terrain-editor) , you can easily generate and alter large regions of terrain.

 ![A viewport view of desert terrain with mountains in the distance.](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Showcase.jpg)

## [Models](#models)[](#models)

A [Model](/docs/reference/engine/classes/Model)  is a container object for geometric groupings , such as [BasePart](/docs/reference/engine/classes/BasePart) , [Motor6D](/docs/reference/engine/classes/Motor6D)  objects, and other models. Models can be simple groupings or you can set a primary part within the model, so that it functions as an assembly, which the physics engine treats as a single rigid body. Models can also contain scripts that act on the individual objects of the model.

![A humanoid model of a creepy girl with four red eyes standing in an A pose. She wears a maroon dress with webs and bright red stockings.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-3D.jpg) A model named Octavia

![A close up view of the model's children in the Explorer window that comprise the model.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-Hierarchy.png) The groupings that comprise the model

## [Workspace access in scripts](#workspace-access-in-scripts)[](#workspace-access-in-scripts)

Within a script, you can access a place's [Workspace](/docs/reference/engine/classes/Workspace)  in three different ways, all of which are valid.

-

game:GetService("Workspace")

-

workspace

-

game.Workspace

From there, you can carry out a large set of use cases to script logic for your games and create dynamic worlds and interactions. For example:

-

Obtain a reference to any object in the workspace to change its properties during runtime.

-

Obtain a reference to a user's [Camera](/docs/reference/engine/classes/Camera)  object to [manipulate their view](/docs/workspace/camera)  of the workspace.

-

Listen for events on objects in the workspace to carry out logic at specific times, such as when a user's playable character [touches an object](/docs/workspace/collisions) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
