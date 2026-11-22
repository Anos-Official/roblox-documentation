<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AnimationClip -->

AnimationClip | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AnimationClip.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AnimationClip](/docs/reference/engine/classes/AnimationClip)

English

Feedback

Engine Class

AnimationClip

Not Creatable

---

## Summary

Properties

|

[Length](#Length) :[number](/docs/luau/numbers)

 |
| --- | --- |
|

[Loop](#Loop) :[boolean](/docs/luau/booleans)

 |
|

[Priority](#Priority) :[Enum.AnimationPriority](/docs/reference/engine/enums/AnimationPriority)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[CurveAnimation](/docs/reference/engine/classes/CurveAnimation) , [KeyframeSequence](/docs/reference/engine/classes/KeyframeSequence)

---

API Reference

Properties

Length

Read Only

Not Replicated

Read Parallel

Capabilities: Animation

AnimationClip.Length :[number](/docs/luau/numbers)

Provide feedback

---

Loop

Read Parallel

Capabilities: Animation

AnimationClip.Loop :[boolean](/docs/luau/booleans)

Provide feedback

---

Priority

Read Parallel

Capabilities: Animation

AnimationClip.Priority :[Enum.AnimationPriority](/docs/reference/engine/enums/AnimationPriority)

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

Jump to

▼

AnimationClip

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Length](#Length)

[Loop](#Loop)

[Priority](#Priority)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
