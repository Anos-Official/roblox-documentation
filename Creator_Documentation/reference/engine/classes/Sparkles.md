<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Sparkles -->

Sparkles | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Sparkles.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Sparkles](/docs/en-us/reference/engine/classes/Sparkles)

English

Feedback

Engine Class

Sparkles

---

## Summary

Properties

|

[Color](#Color) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Deprecated

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[SparkleColor](#SparkleColor) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[TimeScale](#TimeScale) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Give Sparkles

```

local Players = game:GetService("Players")

local function onCharacterSpawned(character)

	local hrp = character:WaitForChild("HumanoidRootPart")

	-- Add sparkles that are colored to the player's torso color

	local sparkles = Instance.new("Sparkles")

	sparkles.Parent = hrp

	sparkles.SparkleColor = character:WaitForChild("Body Colors").TorsoColor.Color

	sparkles.Enabled = true

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterSpawned)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

---

API Reference

Properties

Color

Deprecated

Show details

---

Enabled

Read Parallel

Capabilities: Basic

Sparkles.Enabled :[boolean](/docs/en-us/luau/booleans)

Code Samples

Give Sparkles

```

local Players = game:GetService("Players")

local function onCharacterSpawned(character)

	local hrp = character:WaitForChild("HumanoidRootPart")

	-- Add sparkles that are colored to the player's torso color

	local sparkles = Instance.new("Sparkles")

	sparkles.Parent = hrp

	sparkles.SparkleColor = character:WaitForChild("Body Colors").TorsoColor.Color

	sparkles.Enabled = true

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterSpawned)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Enabled

```

local Debris = game:GetService("Debris")

local part = Instance.new("Part")

part.Parent = workspace

local sparkles = Instance.new("Sparkles")

sparkles.Parent = part

function stopSparkling(sparkles)

	sparkles.Enabled = false -- No more new particles

	Debris:AddItem(sparkles, 4) -- Remove the object after a delay (after existing particles have expired)

end

stopSparkling(part.Sparkles)

```

Provide feedback

---

SparkleColor

Read Parallel

Capabilities: Basic

Sparkles.SparkleColor :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Code Samples

Give Sparkles

```

local Players = game:GetService("Players")

local function onCharacterSpawned(character)

	local hrp = character:WaitForChild("HumanoidRootPart")

	-- Add sparkles that are colored to the player's torso color

	local sparkles = Instance.new("Sparkles")

	sparkles.Parent = hrp

	sparkles.SparkleColor = character:WaitForChild("Body Colors").TorsoColor.Color

	sparkles.Enabled = true

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterSpawned)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Provide feedback

---

TimeScale

Read Parallel

Capabilities: Basic

Sparkles.TimeScale :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

Sparkles

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Color](#Color)

[Enabled](#Enabled)

[SparkleColor](#SparkleColor)

[TimeScale](#TimeScale)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
