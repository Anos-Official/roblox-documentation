<!-- Source: https://create.roblox.com/docs/en-us/parts/models -->

Models | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts/models.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)

# Models

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/models.md)

Models  are containers for physical objects that you can use to organize your workspace and group your assets, such as parts, welds, or joints. While models often contain connected parts known as an [assembly](/docs/en-us/physics/assemblies) , they can also contain any number of individual parts or objects, such as scripts, attachments, or other models.

To demonstrate, avatar characters are a single [Model](/docs/en-us/reference/engine/classes/Model)  containing the appropriate humanoid parts, joints, and scripts necessary for runtime behavior:

![An example character model of a humanoid monster girl in a dark purple dress.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-3D.jpg) A model named Octavia

![The groupings which comprise the Octavia model in Studio's Explorer window.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-Hierarchy.png) The groupings that comprise the model

## [Create models](#create-models)[](#create-models)

You can create models using any open use or restricted asset, but any restricted assets that you don't have [explicit permission](/docs/en-us/projects/assets/privacy#view-permissions)  to use are not  visible or audible at runtime unless the game itself has permission to use those assets.

There are two ways to create models:

-

Group objects together to automatically form a [Model](/docs/en-us/reference/engine/classes/Model)  object.

-

Insert an empty [Model](/docs/en-us/reference/engine/classes/Model)  object into the Workspace, then manually add child objects to the model.

To create a model using the grouping method:

1.

In the Explorer  window or 3D viewport, select every object that you want to group into a model.

2.

Right-click on one of the objects and select Group , or press Ctrl G  on Windows or ⌘ G  on Mac. A new [Model](/docs/en-us/reference/engine/classes/Model)  object displays with all of the objects that make up the model nested underneath.

 ![A close up view of the Explorer window. A Model object is highlighted with three nested children.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Group-Simple.png)

To completely ungroup a model back to its original objects, right-click it and select Ungroup , or press Ctrl U  on Windows or ⌘ U  on Mac.

### [Set a primary part](#set-a-primary-part)[](#set-a-primary-part)

If you have a model with parts that are joined together through physical joints like [WeldConstraints](/docs/en-us/reference/engine/classes/WeldConstraint)  or [Motor6Ds](/docs/en-us/reference/engine/classes/Motor6D) , you should specify a [BasePart](/docs/en-us/reference/engine/classes/BasePart)  within the model to become a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart) . A model's [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  is the physical reference that specifies which [BasePart](/docs/en-us/reference/engine/classes/BasePart)  the pivot point and bounding box should move with when the model changes position or orientation.

To set a primary part:

1.

In the Explorer  window, select a model.

2.

In the Properties  window, select the PrimaryPart  property. Your cursor changes.

3.

Back in the Explorer  window, select the part that you want to become your primary part.

## [Select models](#select-models)[](#select-models)

As you hover over models in the viewport, they are outlined to indicate their potential selection. You can select an outlined model by clicking it, or you can select multiple models by holding Shift , Ctrl , or ⌘  as you hover over and click them.

 ![A warehouse view in the 3D viewport. Multiple models are selected and highlighted with a light blue outline.](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window-Object-Selection.jpg)

As models typically contain multiple child [parts](/docs/en-us/parts)  or [meshes](/docs/en-us/parts/meshes) , some children may be hidden from view. To select a specific child without moving the camera around or locating the child in the [Explorer](/docs/en-us/studio/explorer)  hierarchy, click while holding Alt  on Windows or ⌥  on Mac to perform [selection cycling](/docs/en-us/studio/overview#selection-cycling) .

Selection cycling

## [Transform models](#transform-models)[](#transform-models)

You can move, scale, or rotate a model using the Studio [transform](/docs/en-us/parts#transform-parts)  tools. Unless you've set a [primary part](#set-a-primary-part) , a model transforms based on the center of its bounding box.

Additionally, within a [Script](/docs/en-us/reference/engine/classes/Script)  or [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) , you can move or rotate a model through the following methods:

| Method | | Description |
| --- | --- |
| [MoveTo()](/docs/en-us/reference/engine/classes/Model#MoveTo) | | Moves the model's [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  to the given position. If a primary part has not been specified, the root part of the model will be used. |
| [PivotTo()](/docs/en-us/reference/engine/classes/PVInstance#PivotTo) | | Transforms the model along with all of its descendant [PVInstances](/docs/en-us/reference/engine/classes/PVInstance)  such that the pivot is located at the specified [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) . |
| [TranslateBy()](/docs/en-us/reference/engine/classes/Model#TranslateBy) | | Shifts a model by the given [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  offset, preserving the model's orientation. |

## [Model behaviors](#model-behaviors)[](#model-behaviors)

While models act similarly to [Folder](/docs/en-us/reference/engine/classes/Folder)  objects for most purposes in your game, they also exhibit some unique behaviors.

### [Character models](#character-models)[](#character-models)

When a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  is present inside a model that contains a [Part](/docs/en-us/reference/engine/classes/Part)  named Head , Roblox displays a name and/or health bar above that part. For more information, see [Character Name/Health Display](/docs/en-us/characters/name-health-display) .

 ![Character display information above an in-game avatar.](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Display-Indicated.jpg)

### [Destroy height](#destroy-height)[](#destroy-height)

To prevent parts that have fallen off of a game's map from continuing to fall forever, Studio automatically destroys parts that fall below the [Workspace.FallenPartsDestroyHeight](/docs/en-us/reference/engine/classes/Workspace#FallenPartsDestroyHeight)  value. If a part destroyed due to this behavior is the last part in a model, then that model will also be destroyed.

## [Model streaming](#model-streaming)[](#model-streaming)

Instance [streaming](/docs/en-us/workspace/streaming)  dynamically loads and unloads [Models](/docs/en-us/reference/engine/classes/Model)  on a player's device as their character explores the 3D world. With streaming enabled, you can specify the way each model should be treated under streaming behavior. For example, a model set to [Persistent](/docs/en-us/workspace/streaming#persistent)  will never stream out, or a model set to [Atomic](/docs/en-us/workspace/streaming#atomic)  will stream in and out as a single unit with all of its descendants. For more information, see [per-model streaming controls](/docs/en-us/workspace/streaming#per-model-streaming-controls) .

Because the 3D content that exists on the client changes dynamically in a streaming-enabled game, models might suddenly disappear, which can be visually jarring for the player. To avoid this situation, you can set specific models to render as optimized "SLIM" meshes or as lower resolution "imposter" meshes when streamed out. See [model level of detail](/docs/en-us/workspace/streaming/techniques#model-level-of-detail) .

## [Upload models](#upload-models)[](#upload-models)

When you upload or import a .gltf , .fbx  and .obj  model file to the cloud using the [Importer](/docs/en-us/art/accessories/creating-rigid/importing) , Roblox represents it as a cloud-based asset with a unique corresponding ID. This cloud-based asset system allows you to store models through Roblox and reuse them across the platform in various contexts without maintaining local copies as part of each saved Studio game.

To upload a model you made in Studio:

1.

In the Explorer  window, right-click your model. A contextual menu displays.

2.

Select Save to Roblox . The Asset Configuration  window displays.

3.

In the Asset Configuration  window,

1.

Set Content Type  to Development Item .

2.

Set Asset Category  to Model .

3.

Complete the following fields:

-

Title  - The name of your model.

-

Description  - A short description of your model.

-

Creator  - Use the dropdown to select if you'd like to publish this asset as an individual or as part of an associated group.

-

Genre  - The genre of your model.

4.

Click the Save  button. After a moment, the Asset Configuration  window displays your model's asset ID that you can use in your projects or share with other creators, groups, or games. For more information on granting permission to collaborators and games so that they can use your models, see [Asset privacy](/docs/en-us/projects/assets/privacy)

## [Distribute and sell models](#distribute-and-sell-models)[](#distribute-and-sell-models)

You can publicly distribute and sell your own models on the Creator Store for United States Dollars (USD), as long as the models have less than 15,000 dependencies. Each of these dependencies must be an:

-

Open use asset or a restricted asset that you created, excluding audio and video.

-

Audio or video asset that you acquired from the Creator Store.

This monetization method lets you earn 100% of net proceeds on transactions, bypassing platform fees and DevEx rates. For more information on asset and seller requirements, including how to set up a seller account to set prices and receive payouts, see [Creator Store - Distribute and sell assets](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

If you want to distribute a model with a child audio asset that you created, you must distribute the audio asset on the Creator Store * before*  making it a child of the model in order for the audio to be audible at runtime.

When creating models for the Creator Store, ensure:

-

The model and its dependencies adhere to the [Community Rules](https://en.help.roblox.com/hc/articles/203313410) , [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) , [Intellectual Property guidelines](/docs/en-us/production/publishing/ip-guidelines) , and Creator Store requirements.

-

The model is set to a reasonable scale and orientation so that it's usable out of the box when inserted from the Creator Store.

-

All of the model's dependencies import into Studio without any warnings.

-

Each mesh dependency contains no more than 20,000 triangles.

-

Each texture dependency meets Roblox's [texture specifications](/docs/en-us/art/modeling/texture-specifications) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
