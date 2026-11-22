<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/KeyframeSequence -->

KeyframeSequence | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/KeyframeSequence.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AnimationClip](/docs/en-us/reference/engine/classes/AnimationClip)
8. /
9. [KeyframeSequence](/docs/en-us/reference/engine/classes/KeyframeSequence)

English

Feedback

Engine Class

KeyframeSequence

---

## Summary

Properties

|

[AuthoredHipHeight](#AuthoredHipHeight) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |

Methods

|

[AddKeyframe](#AddKeyframe) (keyframe :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

 |
|

[GetKeyframes](#GetKeyframes) () : {[Keyframe](/docs/en-us/reference/engine/classes/Keyframe) }

 |
|

[RemoveKeyframe](#RemoveKeyframe) (keyframe :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

 |

Inherited Members

3  inherited from [AnimationClip](/docs/en-us/reference/engine/classes/AnimationClip)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

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

KeyframeSequence Instantiation

```

-- Create the sequence

local keyframeSequence = Instance.new("KeyframeSequence")

keyframeSequence.Loop = false

keyframeSequence.Priority = Enum.AnimationPriority.Action

--  Create a keyframe

local keyframe = Instance.new("Keyframe")

keyframe.Time = 0

-- Create sample poses

local rootPose = Instance.new("Pose")

rootPose.Name = "HumanoidRootPart"

rootPose.Weight = 0

local lowerTorsoPose = Instance.new("Pose")

lowerTorsoPose.Name = "LowerTorso"

lowerTorsoPose.Weight = 1

-- Set the sequence hierarchy

rootPose:AddSubPose(lowerTorsoPose)

keyframe:AddPose(rootPose)

keyframeSequence:AddKeyframe(keyframe)

-- Parent the sequence

keyframeSequence.Parent = workspace

```

---

API Reference

Properties

AuthoredHipHeight

Hidden

Plugin Security

Read Parallel

Capabilities: Animation

KeyframeSequence.AuthoredHipHeight :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

AddKeyframe

Capabilities: Animation

KeyframeSequence:AddKeyframe (keyframe :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Parameters

|

keyframe :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

KeyframeSequence Instantiation

```

-- Create the sequence

local keyframeSequence = Instance.new("KeyframeSequence")

keyframeSequence.Loop = false

keyframeSequence.Priority = Enum.AnimationPriority.Action

--  Create a keyframe

local keyframe = Instance.new("Keyframe")

keyframe.Time = 0

-- Create sample poses

local rootPose = Instance.new("Pose")

rootPose.Name = "HumanoidRootPart"

rootPose.Weight = 0

local lowerTorsoPose = Instance.new("Pose")

lowerTorsoPose.Name = "LowerTorso"

lowerTorsoPose.Weight = 1

-- Set the sequence hierarchy

rootPose:AddSubPose(lowerTorsoPose)

keyframe:AddPose(rootPose)

keyframeSequence:AddKeyframe(keyframe)

-- Parent the sequence

keyframeSequence.Parent = workspace

```

Provide feedback

---

GetKeyframes

Capabilities: Animation

KeyframeSequence:GetKeyframes () : {[Keyframe](/docs/en-us/reference/engine/classes/Keyframe) }

Returns

{[Keyframe](/docs/en-us/reference/engine/classes/Keyframe) }

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

RemoveKeyframe

Capabilities: Animation

KeyframeSequence:RemoveKeyframe (keyframe :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Parameters

|

keyframe :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

KeyframeSequence RemoveKeyframe

```

local keyframeSequence = Instance.new("KeyframeSequence")

keyframeSequence.Parent = workspace

local keyframe = Instance.new("Keyframe")

keyframeSequence:AddKeyframe(keyframe)

task.wait(2)

keyframeSequence:RemoveKeyframe(keyframe)

```

Provide feedback

---

Jump to

▼

KeyframeSequence

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[AuthoredHipHeight](#AuthoredHipHeight)

[Methods](#methods)

[AddKeyframe()](#AddKeyframe)

[GetKeyframes()](#GetKeyframes)

[RemoveKeyframe()](#RemoveKeyframe)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
