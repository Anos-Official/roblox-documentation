<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Backpack -->

Backpack | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Backpack.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Backpack](/docs/reference/engine/classes/Backpack)

English

Feedback

Engine Class

Backpack

---

## Summary

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Backpack Give Tool

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

	local player = Players:GetPlayerFromCharacter(character)

	local tool = Instance.new("Tool")

	local backpack = player:FindFirstChildOfClass("Backpack")

	tool.Parent = backpack

end

local function onPlayerAdded(player)

	if player.Character then

		onCharacterAdded(player.Character)

	end

	player.CharacterAdded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Backpack Overview

```

local Players = game:GetService("Players")

-- Accessing Backpack from a server script

local backpack = Players.PlayerName.Backpack

-- Accessing Backpack from a client script

local backpack = Players.LocalPlayer.Backpack

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
