<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Keyframe -->

Keyframe | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Keyframe.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Keyframe](/docs/reference/engine/classes/Keyframe)

English

Feedback

Engine Class

Keyframe

---

## Summary

Properties

|

[Time](#Time) :[number](/docs/luau/numbers)

 |
| --- | --- |

Methods

|

[AddMarker](#AddMarker) (marker :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
|

[AddPose](#AddPose) (pose :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
|

[GetMarkers](#GetMarkers) () : {[KeyframeMarker](/docs/reference/engine/classes/KeyframeMarker) }

 |
|

[GetPoses](#GetPoses) () : {[Pose](/docs/reference/engine/classes/Pose) }

 |
|

[RemoveMarker](#RemoveMarker) (marker :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
|

[RemovePose](#RemovePose) (pose :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Keyframe Generate Poses

```

local function generateKeyframe(model)

	if not model.PrimaryPart then

		warn("No primary part set")

		return

	end

	local rootPart = model.PrimaryPart:GetRootPart()

	if not rootPart then

		warn("Root part not found")

		return

	end

	local partsAdded = {}

	partsAdded[rootPart] = true

	local function addPoses(part, parentPose)

		-- get all of the joints attached to the part

		for _, joint in pairs(part:GetJoints()) do

			-- we're only interested in Motor6Ds

			if joint:IsA("Motor6D") then

				-- find the connected part

				local connectedPart = nil

				if joint.Part0 == part then

					connectedPart = joint.Part1

				elseif joint.Part1 == part then

					connectedPart = joint.Part0

				end

				if connectedPart then

					-- make sure we haven't already added this part

					if not partsAdded[connectedPart] then

						partsAdded[connectedPart] = true

						-- create a pose

						local pose = Instance.new("Pose")

						pose.Name = connectedPart.Name

						parentPose:AddSubPose(pose)

						-- recurse

						addPoses(connectedPart, pose)

					end

				end

			end

		end

	end

	local keyframe = Instance.new("Keyframe")

	-- populate the keyframe

	local rootPose = Instance.new("Pose")

	rootPose.Name = rootPart.Name

	addPoses(rootPart, rootPose)

	keyframe:AddPose(rootPose)

	return keyframe

end

local character = script.Parent

local keyframe = generateKeyframe(character)

print(keyframe)

```

---

API Reference

Properties

Time

Read Parallel

Capabilities: Animation

Keyframe.Time :[number](/docs/luau/numbers)

Code Samples

Get KeyframeSequence Length

```

local function getSequenceLength(keyframeSequence)

	local length = 0

	for _, keyframe in pairs(keyframeSequence:GetKeyframes()) do

		if keyframe.Time > length then

			length = keyframe.Time

		end

	end

	return length

end

local keyframeSequence = Instance.new("KeyframeSequence")

getSequenceLength(keyframeSequence)

```

Provide feedback

---

Methods

AddMarker

Capabilities: Animation

Keyframe:AddMarker (marker :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

marker :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

Add Marker/Remove Marker

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker = Instance.new("KeyframeMarker")

marker.Name = "FootStep"

marker.Value = 100

keyframe:AddMarker(marker) --marker.Parent = keyframe

task.wait(2)

keyframe:RemoveMarker(marker) --marker.Parent = nil

```

Provide feedback

---

AddPose

Capabilities: Animation

Keyframe:AddPose (pose :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

pose :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

Keyframe Generate Poses

```

local function generateKeyframe(model)

	if not model.PrimaryPart then

		warn("No primary part set")

		return

	end

	local rootPart = model.PrimaryPart:GetRootPart()

	if not rootPart then

		warn("Root part not found")

		return

	end

	local partsAdded = {}

	partsAdded[rootPart] = true

	local function addPoses(part, parentPose)

		-- get all of the joints attached to the part

		for _, joint in pairs(part:GetJoints()) do

			-- we're only interested in Motor6Ds

			if joint:IsA("Motor6D") then

				-- find the connected part

				local connectedPart = nil

				if joint.Part0 == part then

					connectedPart = joint.Part1

				elseif joint.Part1 == part then

					connectedPart = joint.Part0

				end

				if connectedPart then

					-- make sure we haven't already added this part

					if not partsAdded[connectedPart] then

						partsAdded[connectedPart] = true

						-- create a pose

						local pose = Instance.new("Pose")

						pose.Name = connectedPart.Name

						parentPose:AddSubPose(pose)

						-- recurse

						addPoses(connectedPart, pose)

					end

				end

			end

		end

	end

	local keyframe = Instance.new("Keyframe")

	-- populate the keyframe

	local rootPose = Instance.new("Pose")

	rootPose.Name = rootPart.Name

	addPoses(rootPart, rootPose)

	keyframe:AddPose(rootPose)

	return keyframe

end

local character = script.Parent

local keyframe = generateKeyframe(character)

print(keyframe)

```

Keyframe Add/Remove Pose

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local pose = Instance.new("Pose")

pose.EasingStyle = Enum.PoseEasingStyle.Cubic

pose.EasingDirection = Enum.PoseEasingDirection.Out

local pose2 = Instance.new("Pose")

pose2.EasingStyle = Enum.PoseEasingStyle.Cubic

pose2.EasingDirection = Enum.PoseEasingDirection.Out

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

keyframe:RemovePose(pose) -- pose.Parent = nil

task.wait(2)

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

pose:AddSubPose(pose2) -- pose2.Parent = pose

task.wait(2)

pose:RemoveSubPose(pose2) -- pose2.Parent = nil

```

Provide feedback

---

GetMarkers

Capabilities: Animation

Keyframe:GetMarkers () : {[KeyframeMarker](/docs/reference/engine/classes/KeyframeMarker) }

Returns

{[KeyframeMarker](/docs/reference/engine/classes/KeyframeMarker) }

Code Samples

Get Keyframe Markers Attached to a Keyframe

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker1 = Instance.new("KeyframeMarker")

marker1.Name = "FootStep"

marker1.Value = 100

local marker2 = Instance.new("KeyframeMarker")

marker2.Name = "Wave"

marker2.Value = 100

keyframe:AddMarker(marker1) --marker.Parent = keyframe

keyframe:AddMarker(marker2) --marker.Parent = keyframe

local markers = keyframe:GetMarkers()

for _, marker in pairs(markers) do

	print(marker.Name)

end

```

Provide feedback

---

GetPoses

Capabilities: Animation

Keyframe:GetPoses () : {[Pose](/docs/reference/engine/classes/Pose) }

Returns

{[Pose](/docs/reference/engine/classes/Pose) }

Code Samples

Keyframe Reset Poses

```

local function resetPoses(parent)

	-- both functions are equivalent to GetChildren

	local poses = parent:IsA("Keyframe") and parent:GetPoses() or parent:IsA("Pose") and parent:GetSubPoses()

	for _, pose in pairs(poses) do

		if pose:IsA("Pose") then

			pose.CFrame = CFrame.new()

			-- recurse

			resetPoses(pose)

		end

	end

end

```

Provide feedback

---

RemoveMarker

Capabilities: Animation

Keyframe:RemoveMarker (marker :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

marker :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

Add Marker/Remove Marker

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker = Instance.new("KeyframeMarker")

marker.Name = "FootStep"

marker.Value = 100

keyframe:AddMarker(marker) --marker.Parent = keyframe

task.wait(2)

keyframe:RemoveMarker(marker) --marker.Parent = nil

```

Provide feedback

---

RemovePose

Capabilities: Animation

Keyframe:RemovePose (pose :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

pose :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

Keyframe Add/Remove Pose

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local pose = Instance.new("Pose")

pose.EasingStyle = Enum.PoseEasingStyle.Cubic

pose.EasingDirection = Enum.PoseEasingDirection.Out

local pose2 = Instance.new("Pose")

pose2.EasingStyle = Enum.PoseEasingStyle.Cubic

pose2.EasingDirection = Enum.PoseEasingDirection.Out

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

keyframe:RemovePose(pose) -- pose.Parent = nil

task.wait(2)

keyframe:AddPose(pose) -- pose.Parent = keyframe

task.wait(2)

pose:AddSubPose(pose2) -- pose2.Parent = pose

task.wait(2)

pose:RemoveSubPose(pose2) -- pose2.Parent = nil

```

Provide feedback

---

Jump to

▼

Keyframe

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Time](#Time)

[Methods](#methods)

[AddMarker()](#AddMarker)

[AddPose()](#AddPose)

[GetMarkers()](#GetMarkers)

[GetPoses()](#GetPoses)

[RemoveMarker()](#RemoveMarker)

[RemovePose()](#RemovePose)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
