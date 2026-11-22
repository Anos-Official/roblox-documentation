<!-- Source: https://create.roblox.com/docs/workspace/collisions -->

Collisions | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/collisions.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. Spatial data

# Collisions

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/collisions.md)

A collision occurs when two 3D objects come into contact within the 3D world. For customized collision handling, [BasePart](/docs/reference/engine/classes/BasePart)  has a set of [collision events](#collision-events)  and [collision filtering](#collision-filtering)  techniques, so you can control which physical assemblies collide with others.

## [Collision events](#collision-events)[](#collision-events)

Collision events  occur when two [BaseParts](/docs/reference/engine/classes/BasePart)  touch or stop touching in the 3D world. You can detect these collisions through the [Touched](/docs/reference/engine/classes/BasePart#Touched)  and [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  events which occur regardless of either part's [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide)  property value. When considering collision handling on parts, note the following:

-

A part's [CanTouch](/docs/reference/engine/classes/BasePart#CanTouch)  property determines whether it triggers collision events. If set to false , neither [Touched](/docs/reference/engine/classes/BasePart#Touched)  nor [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  will fire.

-

A part's [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide)  property affects whether it will physically  collide with other parts and cause forces to act upon them. Even if [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide)  is disabled for a part, you can detect touch and non‑touch through [Touched](/docs/reference/engine/classes/BasePart#Touched)  and [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  events.

-

The [Touched](/docs/reference/engine/classes/BasePart#Touched)  and [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  events only fire as a result of physical  movement, not from a [Position](/docs/reference/engine/classes/BasePart#Position)  or [CFrame](/docs/reference/engine/classes/BasePart#CFrame)  changes that cause a part to intersect or stop intersecting another part.

-

The top-level [Terrain](/docs/reference/engine/classes/Terrain)  class inherits from [BasePart](/docs/reference/engine/classes/BasePart) , so you can assign a [collision group](#collision-groups)  to [Terrain](/docs/reference/engine/classes/Terrain)  to determine whether other [BaseParts](/docs/reference/engine/classes/BasePart)  collide with [Terrain](/docs/parts/terrain)  voxels.

For performance optimization, set [CanTouch](/docs/reference/engine/classes/BasePart#CanTouch)  to false  for objects that don't require collisions.

### [Touched](#touched)[](#touched)

The [Touched](/docs/reference/engine/classes/BasePart#Touched)  event fires when a [BasePart](/docs/reference/engine/classes/BasePart)  comes in contact with another, or with a [Terrain](/docs/parts/terrain)  voxel. It only fires as a result of physical simulation  and will not fire when the part's [Position](/docs/reference/engine/classes/BasePart#Position)  or [CFrame](/docs/reference/engine/classes/BasePart#CFrame)  is explicitly set such that it intersects another part or voxel.

The following code pattern shows how the [Touched](/docs/reference/engine/classes/BasePart#Touched)  event can be connected to a custom onTouched()  function. Note that the event sends the otherPart  argument to the function, indicating the other part involved in the collision.

Part Collision

```

local part = workspace.Part

local function onTouched(otherPart)

	print(part.Name .. " collided with " .. otherPart.Name)

end

part.Touched:Connect(onTouched)

```

Note that the [Touched](/docs/reference/engine/classes/BasePart#Touched)  event can fire multiple times in quick succession based on subtle physical collisions, such as when a moving object "settles" into a resting position or when a collision involves a [multi‑part model](#model-collisions) . To avoid triggering more [Touched](/docs/reference/engine/classes/BasePart#Touched)  events than necessary, you can implement a simple debounce system which enforces a "cooldown" period through an instance [attribute](/docs/studio/properties#instance-attributes) .

Part Collision With Cooldown

```

local part = workspace.Part

local COOLDOWN_TIME = 1

local function onTouched(otherPart)

	if not part:GetAttribute("Touched") then

		print(part.Name .. " collided with " .. otherPart.Name)

		part:SetAttribute("Touched", true)  -- Set attribute to true

		task.wait(COOLDOWN_TIME)  -- Wait for cooldown duration

		part:SetAttribute("Touched", false)  -- Reset attribute

	end

end

part.Touched:Connect(onTouched)

```

### [TouchEnded](#touchended)[](#touchended)

The [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  event fires when the entire collision bounds of a [BasePart](/docs/reference/engine/classes/BasePart)  exits the bounds of another [BasePart](/docs/reference/engine/classes/BasePart)  or a filled [Terrain](/docs/parts/terrain)  voxel. It only fires as a result of physical simulation  and will not fire when the part's [Position](/docs/reference/engine/classes/BasePart#Position)  or [CFrame](/docs/reference/engine/classes/BasePart#CFrame)  is explicitly set such that it stops intersecting another part or voxel.

The following code pattern shows how the [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  event can be connected to a custom onTouchEnded()  function. Like [Touched](/docs/reference/engine/classes/BasePart#Touched) , the event sends the otherPart  argument to the function, indicating the other part involved.

Non-Collision Detection

```

local part = workspace.Part

local function onTouchEnded(otherPart)

	print(part.Name .. " is no longer touching " .. otherPart.Name)

end

part.TouchEnded:Connect(onTouchEnded)

```

### [Collision summaries](#collision-summaries)[](#collision-summaries)

[Touched](/docs/reference/engine/classes/BasePart#Touched)  tells you that  a collision happened, but not where it happened, which direction it came from, or how hard it was. For detailed contact data from the physics engine, call [BindToCollisionSummaries()](/docs/reference/engine/classes/BasePart#BindToCollisionSummaries)  on a part. It takes a callback and returns an [RBXScriptConnection](/docs/reference/engine/datatypes/RBXScriptConnection)  that you can disconnect when you no longer need the data. This is a separate API from [Touched](/docs/reference/engine/classes/BasePart#Touched) , so don't call it from inside a [Touched](/docs/reference/engine/classes/BasePart#Touched)  handler.

The callback runs once per frame, after the physics step completes. It receives a table with a summary of every collision the part was involved in during that frame. Each summary describes one contact patch between the subscribed part and another part. Summaries are frozen and can't be changed. Each one has these fields:

| Field | | Type | | Description |
| --- | --- |
| Time | | number | | Simulation time of the substep. |
| Part0 | | [BasePart](/docs/reference/engine/classes/BasePart) | | The subscribed part. |
| Part1 | | [BasePart](/docs/reference/engine/classes/BasePart) | | The other part in the pair. |
| Point | | [Vector3](/docs/reference/engine/datatypes/Vector3) | | Averaged contact point, in world space. |
| Normal | | [Vector3](/docs/reference/engine/datatypes/Vector3) | | Unit normal. It always points away from Part0 . |
| RelativeVelocity | | [Vector3](/docs/reference/engine/datatypes/Vector3) | | Velocity of Part1  relative to Part0  at the contact point, measured before the solver resolves the collision. |
| Area | | number | | Estimated area of the contact patch. |

To get the head-on impact speed, take the dot product of RelativeVelocity  and Normal . To detect glancing hits or sliding, use the tangential component of RelativeVelocity . If you want a value closer to a force, combine the speed with the parts' [AssemblyMass](/docs/reference/engine/classes/BasePart#AssemblyMass) .

Impact-based effects

```

local part = workspace.Part

local function onCollision(summaries)

	for _, summary in summaries do

		local impactSpeed = summary.RelativeVelocity:Dot(summary.Normal)

		if impactSpeed > 10 then

			print("Hard impact at", summary.Point, "with speed", impactSpeed)

		end

	end

end

local connection = part:BindToCollisionSummaries(onCollision)

-- Later, when you no longer need summaries

connection:Disconnect()

```

Keep the following in mind when you use collision summaries:

-

Summaries are only generated on the [network owner](/docs/physics/network-ownership)  that runs the physics simulation, which can be a client or the server. They aren't replicated. If other clients need to know about a collision, process the summary and send only the data they need through your own [remote event](/docs/scripting/events/remote) .

-

Parts with [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide)  set to false  don't produce collision summaries.

-

Complex non-convex parts can produce more than one summary for the same pair of parts.

-

Contacts between two sleeping parts aren't recorded.

-

Processing cost grows with the number of subscribed parts, not with the total number of collisions in the place.

## [Collision filtering](#collision-filtering)[](#collision-filtering)

Collision filtering  defines which physical parts collide with others. You can configure filtering for numerous objects through [collision groups](#collision-groups)  or you can control collisions on a [part‑to‑part](#part-to-part-filtering)  basis with [NoCollisionConstraint](/docs/reference/engine/classes/NoCollisionConstraint)  instances.

### [Collision groups](#collision-groups)[](#collision-groups)

Collision groups  let you assign [BaseParts](/docs/reference/engine/classes/BasePart)  to dedicated groups and specify whether or not they collide with those in other groups. Parts within non‑colliding groups pass through each other completely, even if both parts have their [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide)  property set to true . Collision groups are created and configured on a [Workspace](/docs/reference/engine/classes/Workspace)  or [WorldModel](/docs/reference/engine/classes/WorldModel)  basis.

In the video above, the spinning objects are in different collision groups such that they collide with objects of another color but not with objects of their own color

You can easily set up collision groups through Studio's Collision Groups  editor, accessible through Studio's Window  ⟩ 3D  menu.

#### [Register groups](#register-groups)[](#register-groups)

[Workspace](/docs/reference/engine/classes/Workspace)  stores its own configurable state of collision groups. Additionally, any [WorldModel](/docs/reference/engine/classes/WorldModel)  can opt to use its own collision groups for queries.

Studio Editor Scripting

The editor includes one Default  collision group which cannot be renamed or deleted. All [BaseParts](/docs/reference/engine/classes/BasePart)  automatically belong to this default group unless assigned to another group, meaning that they will collide with all other objects in the Default  group.

To create a new collision group:

1.

By default, groups are registered on [Workspace](/docs/reference/engine/classes/Workspace) , but if you have at least one [WorldModel](/docs/reference/engine/classes/WorldModel)  in your place, a selection dropdown will appear at the top of the collision groups editor. Use the dropdown to configure collision groups across different [WorldModel](/docs/reference/engine/classes/WorldModel)  instances.

 ![Workspace indicated as the collision group editor's currently active world](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Active-World-Dropdown.png)

For any [WorldModel](/docs/reference/engine/classes/WorldModel) , you can toggle on Use Workspace collision groups  to make it use [Workspace](/docs/reference/engine/classes/Workspace)  collision groups for its queries.

 ![Checkbox indicated to toggle a WorldModel's UseWorkspaceCollisionGroups property](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/WorldModel-Use-Workspace-Collision-Groups.png)

2.

Click the Add Group  button along the top of the editor panel, enter a new group name, and press Enter . The new group appears in both columns of list view, or in both the left column and upper row of table view.

List View Table View

![New group added to Collision Groups Editor in List View](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/New-Group-List-View.png)

3.

Repeat the process if necessary, choosing a unique and descriptive name for each group. Note that you can change a group's name during development by clicking in its field, or by selecting it and clicking the rename  button.

 ![Button and field indicated for renaming a group in the Collision Groups Editor](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Rename-Group.png)

#### [Configure group collisions](#configure-group-collisions)[](#configure-group-collisions)

Studio Editor Scripting

Under default configuration, objects in all groups collide with each other. To prevent objects in one group from colliding with objects in another group, uncheck  the box in the respective row/column.

In the following example, objects in the Cubes  group will not  collide with objects in the Doors  group.

List View Table View

![Group configured in List View of Collision Groups Editor](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Configure-Groups-List-View.png)

#### [Assign objects to groups](#assign-objects-to-groups)[](#assign-objects-to-groups)

Studio Editor Scripting

To assign objects to groups you've [registered](#register-groups)  through the Studio editor:

1.

Select one or more [BaseParts](/docs/reference/engine/classes/BasePart)  that qualify as part of a collision group.

2.

Assign them to the group by clicking the ⊕  button for its row. Objects can belong to only one collision group at a time, so placing them in a new group removes them from their current group.

 ![Plus button indicated in Collision Groups Editor for adding selected parts to a group](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Add-To-Group.png)

Once assigned, the new group is reflected under the object's [CollisionGroup](/docs/reference/engine/classes/BasePart#CollisionGroup)  property.

 ![Chosen collision group indicated as the part's CollisionGroup property](https://prod.docsiteassets.roblox.com/assets/physics/collisions/BasePart-CollisionGroup.png)

#### [StudioSelectable group](#studioselectable-group)[](#studioselectable-group)

Tools in Studio use the collision filtering system to determine which objects are candidates for selection when clicking in the 3D viewport. Objects whose assigned collision group does not  collide with StudioSelectable  will be ignored.

For example, if you have checkpoints in a racing game whose effective areas are defined by large transparent parts, you can assign them to a Checkpoints  collision group and then make that group non‑collidable with StudioSelectable  so that they don't get in the way when you're editing the underlying map geometry.

 ![Checkpoints group configured to be non-collidable with StudioSelectable group](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/StudioSelectable-Off.png)

For plugin code, it's recommended that you assign "StudioSelectable"  as the collision group filter of your [RaycastParams](/docs/reference/engine/datatypes/RaycastParams)  when finding parts under the cursor. This allows your plugins to match the selection mechanics that creators have learned to expect from built‑in Studio tools.

Recommended Plugin Selection Raycast

```

local UserInputService = game:GetService("UserInputService")

local raycastParams = RaycastParams.new()

raycastParams.CollisionGroup = "StudioSelectable"  -- To follow the convention

raycastParams.BruteForceAllSlow = true  -- So that parts with CanQuery of "false" can be selected

local mouseLocation = UserInputService:GetMouseLocation()

local mouseRay = workspace.CurrentCamera:ViewportPointToRay(mouseLocation.X, mouseLocation.Y)

local filteredSelectionHit = workspace:Raycast(mouseRay.Origin, mouseRay.Direction * 10000, raycastParams)

```

### [Part-to-part filtering](#part-to-part-filtering)[](#part-to-part-filtering)

To prevent collisions between two specific parts without setting up [collision groups](#collision-groups) , such as between a vehicle's wheel and its chassis, consider the [No Collision](/docs/physics/mechanical-constraints#nocollisionconstraint)  constraint. Advantages include:

-

Collision groups and/or configuration scripts are not required, so you can easily create and share models with customized collision filtering.

-

Connected parts will not collide with each other, but they can still collide with other objects.

### [Disable character collisions](#disable-character-collisions)[](#disable-character-collisions)

Roblox player characters collide with each other by default. This can lead to interesting but unintended gameplay, such as characters jumping on top of each other to reach specific areas. If this behavior is undesirable, you can prevent it through the following [Script](/docs/reference/engine/classes/Script)  in [ServerScriptService](/docs/reference/engine/classes/ServerScriptService) .

Script - Disable Character Collisions

```

local Players = game:GetService("Players")

workspace:RegisterCollisionGroup("Characters")

workspace:CollisionGroupSetCollidable("Characters", "Characters", false)

local function onDescendantAdded(descendant)

	-- Set collision group for any part descendant

	if descendant:IsA("BasePart") then

		descendant.CollisionGroup = "Characters"

	end

end

local function onCharacterAdded(character)

	-- Process existing and new descendants for physics setup

	for _, descendant in character:GetDescendants() do

		onDescendantAdded(descendant)

	end

	character.DescendantAdded:Connect(onDescendantAdded)

end

Players.PlayerAdded:Connect(function(player)

	-- Detect when the player's character is added

	player.CharacterAdded:Connect(onCharacterAdded)

end)

```

## [Model collisions](#model-collisions)[](#model-collisions)

[Model](/docs/reference/engine/classes/Model)  objects are containers for parts rather than inheriting from [BasePart](/docs/reference/engine/classes/BasePart) , so they can't directly connect to [BasePart.Touched](/docs/reference/engine/classes/BasePart#Touched)  or [BasePart.TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  events. To determine whether a model triggers a collision events, you need to loop through its children and connect the custom onTouched()  and onTouchEnded()  functions to each child [BasePart](/docs/reference/engine/classes/BasePart) .

For joined parts by [solid modeling](/docs/parts/solid-modeling)  instead of [Model](/docs/reference/engine/classes/Model)  objects, see [mesh and solid model collisions](#mesh-and-solid-model-collisions) .

The following code sample connects all [BaseParts](/docs/reference/engine/classes/BasePart)  of a multi‑part model to collision events and tracks the total number of collisions with other parts.

Model Collision

```

local model = script.Parent

local numTouchingParts = 0

local function onTouched(otherPart)

	-- Ignore instances of the model intersecting with itself

	if otherPart:IsDescendantOf(model) then return end

	-- Increase count of model parts touching

	numTouchingParts += 1

	print(model.Name, "intersected with", otherPart.Name, "| Model parts touching:", numTouchingParts)

end

local function onTouchEnded(otherPart)

	-- Ignore instances of the model un-intersecting with itself

	if otherPart:IsDescendantOf(model) then return end

	-- Decrease count of model parts touching

	numTouchingParts -= 1

	print(model.Name, "un-intersected from", otherPart.Name, "| Model parts touching:", numTouchingParts)

end

for _, child in model:GetChildren() do

	if child:IsA("BasePart") then

		child.Touched:Connect(onTouched)

		child.TouchEnded:Connect(onTouchEnded)

	end

end

```

## [Mesh and solid model collisions](#mesh-and-solid-model-collisions)[](#mesh-and-solid-model-collisions)

[MeshPart](/docs/reference/engine/classes/MeshPart)  and [PartOperation](/docs/reference/engine/classes/PartOperation)  (parts joined by [solid modeling](/docs/parts/solid-modeling) ) are subclasses of [BasePart](/docs/reference/engine/classes/BasePart) , so meshes and solid modeled parts inherit the same [collision events](#collision-events)  and [collision filtering](#collision-filtering)  options as regular parts. However, since meshes and solid modeled parts usually have more complex geometries, they have a distinctive [CollisionFidelity](/docs/reference/engine/classes/TriangleMeshPart#CollisionFidelity)  property which determines how precisely the physical bounds align with the visual representation for collision handling.

The [CollisionFidelity](/docs/reference/engine/classes/TriangleMeshPart#CollisionFidelity)  property has the following options, in order of fidelity and performance impact from lowest to highest:

-

Box  — Creates a bounding collision box, ideal for small or non‑interactive objects.

-

Hull  — Generates a convex hull, suitable for objects with less pronounced indentations or cavities.

-

Default  — Produces an approximate collision shape that supports concavity, suitable for complex objects with semi-detailed interaction needs.

-

PreciseConvexDecomposition  — Offers the most precise fidelity but still not a 1:1 representation of the visual. This option has the most expensive performance cost and takes longer for the engine to compute.

Original Mesh Default Box Hull Precise

![Original mesh of castle tower](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-MeshPart.jpg)

To view collision fidelity in Studio, toggle on Collision fidelity  from the [Visualization Options](/docs/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

For more information on the performance impact of collision fidelity options and how to mitigate them, see [performance optimization](/docs/performance-optimization/improve#physics-computation) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
