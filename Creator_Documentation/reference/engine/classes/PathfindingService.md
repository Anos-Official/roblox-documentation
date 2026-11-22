<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/PathfindingService -->

PathfindingService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PathfindingService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [PathfindingService](/docs/en-us/reference/engine/classes/PathfindingService)

English

Feedback

Engine Class

PathfindingService

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[EmptyCutoff](#EmptyCutoff) :[number](/docs/en-us/luau/numbers)

Deprecated

 |
| --- | --- |

Methods

|

[ComputeRawPathAsync](#ComputeRawPathAsync) (start :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , maxDistance :  [number](/docs/en-us/luau/numbers) ) :[Path](/docs/en-us/reference/engine/classes/Path)

Deprecated

 |
|

[ComputeSmoothPathAsync](#ComputeSmoothPathAsync) (start :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , maxDistance :  [number](/docs/en-us/luau/numbers) ) :[Path](/docs/en-us/reference/engine/classes/Path)

Deprecated

 |
|

[CreatePath](#CreatePath) (agentParameters :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[Path](/docs/en-us/reference/engine/classes/Path)

 |
|

[FindPathAsync](#FindPathAsync) (start :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Path](/docs/en-us/reference/engine/classes/Path)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Using the Pathfinding Service

```

local PathfindingService = game:GetService("PathfindingService")

local agentParams = {

	AgentRadius = 2.0,

	AgentHeight = 5.0,

	AgentCanJump = false,

}

local currentWaypointIdx = 1

local path = PathfindingService:CreatePath(agentParams)

local humanoidRootPart = script.Parent:FindFirstChild("HumanoidRootPart")

local targetPosition = Vector3.new(50, 0, 50)

path:ComputeAsync(humanoidRootPart.Position, targetPosition)

-- When the path is blocked...

local function OnPathBlocked(blockedWaypointIdx)

	-- Check if the obstacle is further down the path

	if blockedWaypointIdx > currentWaypointIdx then

		-- Recompute the path

		path:ComputeAsync(humanoidRootPart.Position, targetPosition)

		if path.Status == Enum.PathStatus.Success then

			-- Retrieve update waypoint list with path:GetWaypoints()

			-- and Continue walking towards target

		else

			-- Error, path not found

		end

	end

end

path.Blocked:Connect(OnPathBlocked)

```

---

API Reference

Properties

EmptyCutoff

Deprecated

Show details

---

Methods

ComputeRawPathAsync

Deprecated

Show details

---

ComputeSmoothPathAsync

Deprecated

Show details

---

CreatePath

Capabilities: Basic

PathfindingService:CreatePath (agentParameters :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[Path](/docs/en-us/reference/engine/classes/Path)

Parameters

|

agentParameters :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[Path](/docs/en-us/reference/engine/classes/Path)

Code Samples

Creating a Path with Pathfinding Service

```

local Workspace = game:GetService("Workspace")

local PathfindingService = game:GetService("PathfindingService")

-- This model contains a start, end and three paths between the player can walk on: Snow, Metal and LeafyGrass

local PathOptionsModel = script.Parent.PathOptions

local startPosition = PathOptionsModel.Start.Position

local finishPosition = PathOptionsModel.End.Position

-- Create a path that avoids Snow and Metal materials

-- This will ensure the path created avoids the Snow and Metal paths and guides

-- the user towards the LeafyGrass path

local path = PathfindingService:CreatePath({

	AgentRadius = 3,

	AgentHeight = 6,

	AgentCanJump = false,

	Costs = {

		Snow = math.huge,

		Metal = math.huge,

	},

})

-- Compute the path

local success, errorMessage = pcall(function()

	path:ComputeAsync(startPosition, finishPosition)

end)

-- Confirm the computation was successful

if success and path.Status == Enum.PathStatus.Success then

	-- For each waypoint, create a part to visualize the path

	for _, waypoint in path:GetWaypoints() do

		local part = Instance.new("Part")

		part.Position = waypoint.Position

		part.Size = Vector3.new(0.5, 0.5, 0.5)

		part.Color = Color3.new(1, 0, 1)

		part.Anchored = true

		part.CanCollide = false

		part.Parent = Workspace

	end

else

	print(`Path unable to be computed, error: {errorMessage}`)

end

```

Provide feedback

---

FindPathAsync

Deprecated

Show details

---

Jump to

▼

PathfindingService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[EmptyCutoff](#EmptyCutoff)

[Methods](#methods)

[ComputeRawPathAsync()](#ComputeRawPathAsync)

[ComputeSmoothPathAsync()](#ComputeSmoothPathAsync)

[CreatePath()](#CreatePath)

[FindPathAsync()](#FindPathAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
