<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/TweenService -->

TweenService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TweenService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [TweenService](/docs/en-us/reference/engine/classes/TweenService)

English

Feedback

Engine Class

TweenService

Not Creatable

Service

---

## Summary

Methods

|

[Create](#Create) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , tweenInfo :  [TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo) , propertyTable :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[Tween](/docs/en-us/reference/engine/classes/Tween)

 |
| --- | --- |
|

[GetValue](#GetValue) (alpha :  [number](/docs/en-us/luau/numbers) , easingStyle :  [Enum.EasingStyle](/docs/en-us/reference/engine/enums/EasingStyle) , easingDirection :  [Enum.EasingDirection](/docs/en-us/reference/engine/enums/EasingDirection) ) :[number](/docs/en-us/luau/numbers)

 |
|

[SmoothDamp](#SmoothDamp) (current :  Variant , target :  Variant , velocity :  Variant , smoothTime :  [number](/docs/en-us/luau/numbers) , maxSpeed :  [number](/docs/en-us/luau/numbers) ? , dt :  [number](/docs/en-us/luau/numbers) ? ) :[Tuple](/docs/en-us/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

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

Looping a Tween

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local tweenInfo = TweenInfo.new(

	2, -- Time

	Enum.EasingStyle.Linear, -- EasingStyle

	Enum.EasingDirection.Out, -- EasingDirection

	-1, -- RepeatCount (when less than zero the tween will loop indefinitely)

	true, -- Reverses (tween will reverse once reaching its goal)

	0 -- DelayTime

)

local tween = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

tween:Play()

task.wait(10)

tween:Cancel() -- cancel the animation after 10 seconds

```

Pausing a Tween

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.BrickColor = BrickColor.new("Bright green")

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(50, 10, 0)

local tweenInfo = TweenInfo.new(10, Enum.EasingStyle.Linear)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

task.wait(3)

part.BrickColor = BrickColor.new("Bright red")

tween:Pause()

task.wait(2)

part.BrickColor = BrickColor.new("Bright green")

tween:Play()

```

---

API Reference

Methods

Create

Capabilities: Basic

TweenService:Create (

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , tweenInfo :[TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo) , propertyTable :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[Tween](/docs/en-us/reference/engine/classes/Tween)

Parameters

|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

tweenInfo :[TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo)

 |
|

propertyTable :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

[Tween](/docs/en-us/reference/engine/classes/Tween)

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

Looping a Tween

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local tweenInfo = TweenInfo.new(

	2, -- Time

	Enum.EasingStyle.Linear, -- EasingStyle

	Enum.EasingDirection.Out, -- EasingDirection

	-1, -- RepeatCount (when less than zero the tween will loop indefinitely)

	true, -- Reverses (tween will reverse once reaching its goal)

	0 -- DelayTime

)

local tween = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

tween:Play()

task.wait(10)

tween:Cancel() -- cancel the animation after 10 seconds

```

Provide feedback

---

GetValue

Write Parallel

Capabilities: Basic

Simulation Access

TweenService:GetValue (

alpha :[number](/docs/en-us/luau/numbers) , easingStyle :[Enum.EasingStyle](/docs/en-us/reference/engine/enums/EasingStyle) , easingDirection :[Enum.EasingDirection](/docs/en-us/reference/engine/enums/EasingDirection)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

alpha :[number](/docs/en-us/luau/numbers)

 |
|

easingStyle :[Enum.EasingStyle](/docs/en-us/reference/engine/enums/EasingStyle)

 |
|

easingDirection :[Enum.EasingDirection](/docs/en-us/reference/engine/enums/EasingDirection)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

SmoothDamp

Write Parallel

Capabilities: Basic

Simulation Access

TweenService:SmoothDamp (

current : Variant , target : Variant , velocity : Variant , smoothTime :[number](/docs/en-us/luau/numbers) , maxSpeed :[number](/docs/en-us/luau/numbers) ? , dt :[number](/docs/en-us/luau/numbers) ?

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

current : Variant

 |
|

target : Variant

 |
|

velocity : Variant

 |
|

smoothTime :[number](/docs/en-us/luau/numbers)

 |
|

maxSpeed :[number](/docs/en-us/luau/numbers) ?

 |
|

dt :[number](/docs/en-us/luau/numbers) ?

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

Jump to

▼

TweenService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[Create()](#Create)

[GetValue()](#GetValue)

[SmoothDamp()](#SmoothDamp)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
