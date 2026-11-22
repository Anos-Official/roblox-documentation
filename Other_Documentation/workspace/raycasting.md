<!-- Source: https://create.roblox.com/docs/workspace/raycasting -->

Raycasting | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/raycasting.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. Spatial data

# Raycasting

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/raycasting.md)

At its most basic level, raycasting  is the act of sending out an invisible ray from a [Vector3](/docs/reference/engine/datatypes/Vector3)  point in a specific direction with a defined length. Once cast, you can detect if the ray hits a [BasePart](/docs/reference/engine/classes/BasePart)  or [Terrain](/docs/reference/engine/classes/Terrain)  cell.

Lasers are fired by floating orbs, and raycasting determines whether a laser hits a platform. Platforms touched by the lasers are temporarily destroyed.

You can cast a ray with the [WorldRoot:Raycast()](/docs/reference/engine/classes/WorldRoot#Raycast)  method ([Workspace:Raycast()](/docs/reference/engine/classes/Workspace#Raycast) ) from a [Vector3](/docs/reference/engine/datatypes/Vector3)  origin in a [Vector3](/docs/reference/engine/datatypes/Vector3)  direction.

Basic Raycast

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Vector3.new(0, 0, 0)

local rayDirection = Vector3.new(0, -100, 0)

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection)

```

When casting a ray, the direction parameter should encompass the desired length of the ray. For instance, if the magnitude of the direction is 10, the resulting ray will also be of length 10. The maximum length is 15,000 studs.

When applicable, you can calculate an unknown directional vector (rayDirection ) using a known origin  and destination . This is useful when casting a ray between two points that can change, such as from one player character to another.

1.

The origin plus a directional vector indicate the ray's destination:

rayOrigin + rayDirection = rayDestination \text{rayOrigin} + \text{rayDirection} = \text{rayDestination} rayOrigin + rayDirection = rayDestination

2.

Subtract rayOrigin \text{rayOrigin} rayOrigin  from both sides of the equation:

rayOrigin + rayDirection − rayOrigin = rayDestination − rayOrigin \text{rayOrigin} + \text{rayDirection} - \text{rayOrigin} = \text{rayDestination} - \text{rayOrigin} rayOrigin + rayDirection − rayOrigin = rayDestination − rayOrigin

3.

The ray's direction equals the destination minus the origin:

rayDirection = rayDestination − rayOrigin \text{rayDirection} = \text{rayDestination} - \text{rayOrigin} rayDirection = rayDestination − rayOrigin

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Workspace.TestOrigin.Position

local rayDestination = Workspace.TestDestination.Position

local rayDirection = rayDestination - rayOrigin

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection)

```

## [Filter options](#filter-options)[](#filter-options)

[WorldRoot:Raycast()](/docs/reference/engine/classes/WorldRoot#Raycast)  accepts an optional [RaycastParams](/docs/reference/engine/datatypes/RaycastParams)  object which tells the raycast to selectively include or exclude certain [BaseParts](/docs/reference/engine/classes/BasePart) , ignore the Water  material for [Terrain](/docs/reference/engine/classes/Terrain) , or use a [collision group](/docs/workspace/collisions#collision-filtering) .

| Key | | Description |
| --- | --- |
| FilterDescendantsInstances | | Array  of objects whose descendants are used in filtering raycasting candidates. |
| FilterType | | [Enum.RaycastFilterType](/docs/reference/engine/enums/RaycastFilterType)  enum which determines how the FilterDescendantsInstances  array is used in the raycast operation.
-

[Exclude](/docs/reference/engine/enums/RaycastFilterType)  — Every [BasePart](/docs/reference/engine/classes/BasePart)  is considered except  those that are descendants of objects in the array.

-

[Include](/docs/reference/engine/enums/RaycastFilterType)  — Only [BaseParts](/docs/reference/engine/classes/BasePart)  that are descendants of objects in the array are considered.

 |
| IgnoreWater | | Boolean which determines whether the Water  material is considered when raycasting against [Terrain](/docs/reference/engine/classes/Terrain) . |
| CollisionGroup | | String name of the [collision group](/docs/workspace/collisions#collision-filtering)  used for the raycasting operation. |

Raycast Filtering

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Vector3.zero

local rayDirection = Vector3.new(0, -100, 0)

local raycastParams = RaycastParams.new()

raycastParams.FilterDescendantsInstances = {script.Parent}

raycastParams.FilterType = Enum.RaycastFilterType.Exclude

raycastParams.IgnoreWater = true

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection, raycastParams)

```

## [Hit detection](#hit-detection)[](#hit-detection)

If the raycasting operation hits an eligible [BasePart](/docs/reference/engine/classes/BasePart)  or [Terrain](/docs/reference/engine/classes/Terrain)  cell, a [RaycastResult](/docs/reference/engine/datatypes/RaycastResult)  object is returned containing the results. To test for a hit, confirm that the result is not nil  and utilize the following properties as needed.

| Property | | Description |
| [Instance](/docs/reference/engine/classes/Instance) | | The [BasePart](/docs/reference/engine/classes/BasePart)  or [Terrain](/docs/reference/engine/classes/Terrain)  cell that the ray intersected. |
| Position | | [Vector3](/docs/reference/engine/datatypes/Vector3)  position of the intersection between the ray and the [Instance](/docs/reference/engine/classes/Instance) . |
| Distance | | Distance between the ray origin and intersection point. |
| Material | | The [Enum.Material](/docs/reference/engine/enums/Material)  of the [BasePart](/docs/reference/engine/classes/BasePart)  or [Terrain](/docs/reference/engine/classes/Terrain)  at the intersection point. |
| Normal | | [Vector3](/docs/reference/engine/datatypes/Vector3)  of the normal vector of the intersected face. |

When used in a place with [instance streaming](/docs/workspace/streaming)  enabled, a client may not have streamed in distant [BaseParts](/docs/reference/engine/classes/BasePart) , so a raycast may not detect a hit. Additionally, low-detail "imposter" [Terrain](/docs/reference/engine/classes/Terrain)  and [Models](/docs/reference/engine/classes/Model)  generated by the streaming system are purely visual and are not eligible raycast targets.

You can exempt any [BasePart](/docs/reference/engine/classes/BasePart)  from hit detection by setting its [BasePart.CanQuery](/docs/reference/engine/classes/BasePart#CanQuery)  property to false .

Raycast Hit Detection

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Vector3.zero

local rayDirection = Vector3.new(0, -100, 0)

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection)

if raycastResult then

	print("Instance:", raycastResult.Instance)

	print("Position:", raycastResult.Position)

	print("Distance:", raycastResult.Distance)

	print("Material:", raycastResult.Material)

	print("Normal:", raycastResult.Normal)

else

	warn("No raycast result!")

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
