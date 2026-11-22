<!-- Source: https://create.roblox.com/docs/en-us/studio/pivot-tools -->

Pivot tools | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/pivot-tools.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Pivot tools

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/pivot-tools.md)

The pivot  tools and related properties give you full control over the points around which objects rotate and translate.

## [Interactive Studio tools](#interactive-studio-tools)[](#interactive-studio-tools)

The interactive Studio tools are located in the Model  tab toolbar.

 ![Pivot tool highlighted in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Pivot.png)

When Pivot  is toggled on, you can move or rotate the pivot point of a [part](/docs/en-us/parts)  or [model](/docs/en-us/parts/models) . Once set, rotation and scaling occur around the pivot point. For more information, see [setting a primary part](/docs/en-us/parts/models#set-a-primary-part) .

The following diagrams show example pivot locations in relation to object bounds.

Center Corner Outside Object Bounds

![A blue cube with its pivot point set in the center of the cube. A green circle represents the object's rotation in relation to its pivot point.](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Edit-Pivot-Center-A.jpg)

When you rotate the pivot of a [model](/docs/en-us/parts/models) , the bounding box of the model also rotates.

Orientation = (0, 90, 0) Orientation = (0, 135, 0) Orientation = (0, 180, 0)

![A model of a purple, blue, and red block with its pivot point set on a the edge of the model's bounding box. A green circle represents the object's rotation in relation to its pivot point.](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Edit-Pivot-Model-A.jpg)

You can specify a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  for models, which is a [BasePart](/docs/en-us/reference/engine/classes/BasePart)  within the model that you can use as a positional basis. In terms of pivot points:

1.

When you assign a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  to a model, the existing pivot changes to the pivot point of the [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart) . If you later unassign/clear the [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart) , the pivot point resets to the center  of the model's bounding box.

2.

If you delete  the [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  from a model, the pivot point remains in the same location and does not  revert to its previous position. This prevents a sudden "jump" if you delete any parts from the model.

Initial Pivot Point A. PrimaryPart Assigned B. PrimaryPart Deleted

![](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/PrimaryPart-1.jpg)

### [Snap](#snap)[](#snap)

The Snap  checkbox, available by click‑holding the small corner arrow on the Pivot  button, toggles whether the pivot point snaps to hotspots  such as corners, edges, or centers when you move it with the Edit Pivot  tool. When snapping is enabled, hotspots display as small magenta points.

![](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Hotspots-Part.jpg) Hotspots on a part

![](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Hotspots-Model.jpg) Hotspots on a model

### [Reset](#reset)[](#reset)

The Reset  button moves the pivot point to the center  of an object or model's bounding box. This operation is useful after you've changed the composition of a model and wish to place its pivot point at the center of its new bounding box.

 ![Pivot Reset tool highlighted in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Pivot-Reset.png)

## [Pivot properties](#pivot-properties)[](#pivot-properties)

In addition to the interactive tools, pivot values can be directly set in the [Properties](/docs/en-us/studio/properties)  window.

| Property | | Description |
| --- | --- |
| Origin Position | | Current world location of the object based on its pivot point rather than its bounding box. Useful for setting the precise location of a [Model](/docs/en-us/reference/engine/classes/Model) . |
| Origin Orientation | | Current orientation of the object based around its pivot point rather than its bounding box. |
| Pivot Offset Position | | Precise location of the pivot relative to the object.¹ |
| Pivot Offset Orientation | | Precise pivot orientation.¹ |
| World Pivot Position | | The precise world location of the pivot for [Models](/docs/en-us/reference/engine/classes/Model)  without a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart) . If a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  is set, the model will use Pivot Offset Position  since the pivot becomes relative to that part.¹ |
| World Pivot Orientation | | The precise world orientation for [Models](/docs/en-us/reference/engine/classes/Model)  without a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart) . If a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  is set, the model will use Pivot Offset Orientation  since the pivot becomes relative to that part.¹ |

 1  Changing this property will not move or rotate the object.

## [Manipulate pivots in scripts](#manipulate-pivots-in-scripts)[](#manipulate-pivots-in-scripts)

Beyond the Studio tools, pivot points can be accessed and manipulated in scripts.

| Function or Property | | Description |
| [GetPivot()](/docs/en-us/reference/engine/classes/PVInstance#GetPivot) | | Queries the current world location of an object's pivot as a [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) . This returns an object's position in 3D space regardless of whether it's an individual part or a [Model](/docs/en-us/reference/engine/classes/Model) . |
| [PivotTo()](/docs/en-us/reference/engine/classes/PVInstance#PivotTo) | | Moves the object such that its pivot will be located at the specified [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) . This allows for uniform object movement of both individual parts and models. |
| [BasePart.PivotOffset](/docs/en-us/reference/engine/classes/BasePart#PivotOffset) | | The [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  which specifies the pivot offset; effectively the offset of the pivot from the [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  of the [BasePart](/docs/en-us/reference/engine/classes/BasePart) .² |
| [Model.WorldPivot](/docs/en-us/reference/engine/classes/BasePart#PivotOffset) | | For [Models](/docs/en-us/reference/engine/classes/Model)  without a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart) , the [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  which specifies the model's pivot in world space. If a [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  is set, the model will use [BasePart.PivotOffset](/docs/en-us/reference/engine/classes/BasePart#PivotOffset)  since the pivot becomes relative to that part.² |

 2  Changing this property will not move or rotate the object.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
