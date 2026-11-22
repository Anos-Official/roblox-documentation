<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Debris -->

Debris | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Debris.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Debris](/docs/reference/engine/classes/Debris)

English

Feedback

Engine Class

Debris

Not Creatable

Service

---

## Summary

Properties

|

[MaxItems](#MaxItems) :[number](/docs/luau/numbers)

Deprecated

 |
| --- | --- |

Methods

|

[AddItem](#AddItem) (item :  [Instance](/docs/reference/engine/datatypes/Instance) , lifetime :  [number](/docs/luau/numbers) ) : ()

 |
|

[addItem](#addItem) (item :  [Instance](/docs/reference/engine/datatypes/Instance) , lifetime :  [number](/docs/luau/numbers) ) : ()

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Debris AddItem

```

local Debris = game:GetService("Debris")

local ball = Instance.new("Part")

ball.Anchored = false

ball.Shape = Enum.PartType.Ball

ball.TopSurface = Enum.SurfaceType.Smooth

ball.BottomSurface = Enum.SurfaceType.Smooth

ball.Size = Vector3.new(1, 1, 1)

local RNG = Random.new()

local MAX_VELOCITY = 10

while true do

	local newBall = ball:Clone()

	newBall.BrickColor = BrickColor.random()

	newBall.CFrame = CFrame.new(0, 30, 0)

	newBall.Velocity =

		Vector3.new(RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY), 0, RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY))

	newBall.Parent = game.Workspace

	Debris:AddItem(newBall, 2)

	task.wait(0.1)

end

```

---

API Reference

Properties

MaxItems

Deprecated

Show details

---

Methods

AddItem

Capabilities: Basic

Debris:AddItem (

item :[Instance](/docs/reference/engine/datatypes/Instance) , lifetime :[number](/docs/luau/numbers)

) : ()

Parameters

|

item :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

lifetime :[number](/docs/luau/numbers)

Default Value: 10 |

Returns

()

Code Samples

Debris AddItem

```

local Debris = game:GetService("Debris")

local ball = Instance.new("Part")

ball.Anchored = false

ball.Shape = Enum.PartType.Ball

ball.TopSurface = Enum.SurfaceType.Smooth

ball.BottomSurface = Enum.SurfaceType.Smooth

ball.Size = Vector3.new(1, 1, 1)

local RNG = Random.new()

local MAX_VELOCITY = 10

while true do

	local newBall = ball:Clone()

	newBall.BrickColor = BrickColor.random()

	newBall.CFrame = CFrame.new(0, 30, 0)

	newBall.Velocity =

		Vector3.new(RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY), 0, RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY))

	newBall.Parent = game.Workspace

	Debris:AddItem(newBall, 2)

	task.wait(0.1)

end

```

Provide feedback

---

addItem

Deprecated

Show details

---

Jump to

▼

Debris

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[MaxItems](#MaxItems)

[Methods](#methods)

[AddItem()](#AddItem)

[addItem()](#addItem)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
