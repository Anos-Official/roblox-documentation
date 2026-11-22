<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Fire -->

Fire | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Fire.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Fire](/docs/en-us/reference/engine/classes/Fire)

English

Feedback

Engine Class

Fire

---

## Summary

Properties

|

[Color](#Color) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Heat](#Heat) :[number](/docs/en-us/luau/numbers)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/en-us/luau/numbers)

 |
|

[SecondaryColor](#SecondaryColor) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[Size](#Size) :[number](/docs/en-us/luau/numbers)

 |
|

[size](#size) :[number](/docs/en-us/luau/numbers)

Deprecated

 |
|

[TimeScale](#TimeScale) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Lighting Torches

```

local Workspace = game:GetService("Workspace")

for _, descendant in Workspace:GetDescendants() do

	if descendant.Name == "Torch" and descendant:IsA("BasePart") then

		local fire = Instance.new("Fire")

		fire.Heat = 10

		fire.SecondaryColor = Color3.new(1, 1, 1)

		fire.Size = math.max(descendant.Size.X, descendant.Size.Z) -- Pick the larger of the two dimensions

		fire.Parent = descendant

	end

end

```

Toggle Fire Effect

```

local part = script.Parent

local clickDetector = Instance.new("ClickDetector")

clickDetector.Parent = part

local fire = Instance.new("Fire")

fire.Parent = part

local light = Instance.new("PointLight")

light.Parent = part

local function onClick()

	fire.Enabled = not fire.Enabled

	light.Enabled = fire.Enabled

end

clickDetector.MouseClick:Connect(onClick)

```

---

API Reference

Properties

Color

Read Parallel

Capabilities: Basic

Fire.Color :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

Enabled

Read Parallel

Capabilities: Basic

Fire.Enabled :[boolean](/docs/en-us/luau/booleans)

Code Samples

Enabled

```

local Debris = game:GetService("Debris")

local function douseFlames(fire)

	fire.Enabled = false -- No more new particles

	Debris:AddItem(fire, 2) -- Remove the object after existing particles have expired

end

local part = Instance.new("Part")

part.Anchored = true

part.Parent = workspace

local fire = Instance.new("Fire")

fire.Parent = part

douseFlames(part.Fire)

```

Provide feedback

---

Heat

Not Replicated

Read Parallel

Capabilities: Basic

Fire.Heat :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LocalTransparencyModifier

Hidden

Not Replicated

Read Parallel

Capabilities: Basic

Fire.LocalTransparencyModifier :[number](/docs/en-us/luau/numbers)

Provide feedback

---

SecondaryColor

Read Parallel

Capabilities: Basic

Fire.SecondaryColor :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

Size

Not Replicated

Read Parallel

Capabilities: Basic

Fire.Size :[number](/docs/en-us/luau/numbers)

Provide feedback

---

size

Deprecated

Show details

---

TimeScale

Read Parallel

Capabilities: Basic

Fire.TimeScale :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

Fire

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Color](#Color)

[Enabled](#Enabled)

[Heat](#Heat)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[SecondaryColor](#SecondaryColor)

[Size](#Size)

[size](#size)

[TimeScale](#TimeScale)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
