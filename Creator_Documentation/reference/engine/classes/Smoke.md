<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Smoke -->

Smoke | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Smoke.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Smoke](/docs/en-us/reference/engine/classes/Smoke)

English

Feedback

Engine Class

Smoke

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

[Opacity](#Opacity) :[number](/docs/en-us/luau/numbers)

 |
|

[RiseVelocity](#RiseVelocity) :[number](/docs/en-us/luau/numbers)

 |
|

[Size](#Size) :[number](/docs/en-us/luau/numbers)

 |
|

[TimeScale](#TimeScale) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Add Smoke to All Fire

```

local function recurseForFire(object)

	-- Check if we found a Fire object that has no Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Create a smoke effect for this fire

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Continue search for Fire objects

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

---

API Reference

Properties

Color

Read Parallel

Capabilities: Basic

Smoke.Color :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Code Samples

Add Smoke to All Fire

```

local function recurseForFire(object)

	-- Check if we found a Fire object that has no Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Create a smoke effect for this fire

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Continue search for Fire objects

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Provide feedback

---

Enabled

Read Parallel

Capabilities: Basic

Smoke.Enabled :[boolean](/docs/en-us/luau/booleans)

Code Samples

Add Smoke to All Fire

```

local function recurseForFire(object)

	-- Check if we found a Fire object that has no Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Create a smoke effect for this fire

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Continue search for Fire objects

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Enabled

```

local Debris = game:GetService("Debris")

local part = Instance.new("Part")

part.Parent = workspace

local smoke = Instance.new("Smoke")

smoke.Parent = part

function stopSmoke(smoke)

	smoke.Enabled = false -- No more new particles

	Debris:AddItem(smoke, 10) -- Remove the object after a delay (after existing particles have expired)

end

stopSmoke(part.Smoke)

```

Provide feedback

---

Opacity

Not Replicated

Read Parallel

Capabilities: Basic

Smoke.Opacity :[number](/docs/en-us/luau/numbers)

Code Samples

Add Smoke to All Fire

```

local function recurseForFire(object)

	-- Check if we found a Fire object that has no Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Create a smoke effect for this fire

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Continue search for Fire objects

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Provide feedback

---

RiseVelocity

Not Replicated

Read Parallel

Capabilities: Basic

Smoke.RiseVelocity :[number](/docs/en-us/luau/numbers)

Code Samples

Add Smoke to All Fire

```

local function recurseForFire(object)

	-- Check if we found a Fire object that has no Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Create a smoke effect for this fire

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Continue search for Fire objects

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Provide feedback

---

Size

Not Replicated

Read Parallel

Capabilities: Basic

Smoke.Size :[number](/docs/en-us/luau/numbers)

Code Samples

Add Smoke to All Fire

```

local function recurseForFire(object)

	-- Check if we found a Fire object that has no Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Create a smoke effect for this fire

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Continue search for Fire objects

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Provide feedback

---

TimeScale

Read Parallel

Capabilities: Basic

Smoke.TimeScale :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

Smoke

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Color](#Color)

[Enabled](#Enabled)

[Opacity](#Opacity)

[RiseVelocity](#RiseVelocity)

[Size](#Size)

[TimeScale](#TimeScale)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
