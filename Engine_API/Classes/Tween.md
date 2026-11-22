<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Tween -->

Tween | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Tween.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [TweenBase](/docs/reference/engine/classes/TweenBase)
8. /
9. [Tween](/docs/reference/engine/classes/Tween)

English

Feedback

Engine Class

Tween

---

## Summary

Properties

|

[Instance](#Instance) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[TweenInfo](#TweenInfo) :[TweenInfo](/docs/reference/engine/datatypes/TweenInfo)

 |

Inherited Members

5  inherited from [TweenBase](/docs/reference/engine/classes/TweenBase)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Tween Creation

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Color = Color3.new(1, 0, 0)

part.Anchored = true

part.Parent = game.Workspace

local goal = {}

goal.Position = Vector3.new(10, 10, 0)

goal.Color = Color3.new(0, 1, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

```

---

API Reference

Properties

Instance

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

Tween.Instance :[Instance](/docs/reference/engine/datatypes/Instance)

Code Samples

Tween Instance

```

local TweenService = game:GetService("TweenService")

local function isInstanceAPart(tween)

	local instance = tween.Instance

	return instance:IsA("BasePart")

end

local tweenInfo = TweenInfo.new()

local instance = Instance.new("Part")

local tween = TweenService:Create(instance, tweenInfo, {

	Transparency = 1,

})

print(isInstanceAPart(tween))

```

Provide feedback

---

TweenInfo

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

Tween.TweenInfo :[TweenInfo](/docs/reference/engine/datatypes/TweenInfo)

Code Samples

TweenInfo Examples

```

-- A TweenInfo with all default parameters

TweenInfo.new()

-- A TweenInfo with its time set to 0.5 seconds.

TweenInfo.new(0.5)

-- A TweenInfo with its easing style set to Back.

TweenInfo.new(0.5, Enum.EasingStyle.Back)

-- A TweenInfo with its easing direction set to In.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In)

-- A TweenInfo that repeats itself 4 times.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, 4)

-- A TweenInfo that reverses its interpolation after reaching its goal.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, 4, true)

-- A TweenInfo that loops indefinitely.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, -1, true)

-- A TweenInfo with a delay of 1 second between each interpolation.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, 4, true, 1)

```

Provide feedback

---

Jump to

▼

Tween

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Instance](#Instance)

[TweenInfo](#TweenInfo)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
