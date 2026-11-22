<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Pose -->

Pose | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Pose.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [PoseBase](/docs/en-us/reference/engine/classes/PoseBase)
8. /
9. [Pose](/docs/en-us/reference/engine/classes/Pose)

English

Feedback

Engine Class

Pose

---

## Summary

Properties

|

[CFrame](#CFrame) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
| --- | --- |
|

[MaskWeight](#MaskWeight) :[number](/docs/en-us/luau/numbers)

Deprecated

 |

Methods

|

[AddSubPose](#AddSubPose) (pose :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

 |
|

[GetSubPoses](#GetSubPoses) () : Instances

 |
|

[RemoveSubPose](#RemoveSubPose) (pose :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

 |

Inherited Members

3  inherited from [PoseBase](/docs/en-us/reference/engine/classes/PoseBase)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

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

---

API Reference

Properties

CFrame

Read Parallel

Capabilities: Animation

Pose.CFrame :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

MaskWeight

Deprecated

Show details

---

Methods

AddSubPose

Capabilities: Animation

Pose:AddSubPose (pose :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Parameters

|

pose :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

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

GetSubPoses

Capabilities: Animation

Pose:GetSubPoses () : Instances

Returns

Instances

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

RemoveSubPose

Capabilities: Animation

Pose:RemoveSubPose (pose :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Parameters

|

pose :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

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

Pose

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[CFrame](#CFrame)

[MaskWeight](#MaskWeight)

[Methods](#methods)

[AddSubPose()](#AddSubPose)

[GetSubPoses()](#GetSubPoses)

[RemoveSubPose()](#RemoveSubPose)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
