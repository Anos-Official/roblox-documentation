<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/core/scripting/create-player-hazards -->

Create player hazards | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/core/scripting/create-player-hazards.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Create player hazards

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/core/scripting/create-player-hazards.md)

Right now, players can fall off any platform with no consequence. This section walks you through creating a large invisible hazard at the same height as the water in your game. When a player falls into the hazard, their health is reduced to zero and they respawn at the start of the game.

## [Create a basic water hazard](#create-a-basic-water-hazard)[](#create-a-basic-water-hazard)

Build with Assistant Build it Yourself

Create a basic water hazard

```

In Workspace > World, create a new folder named Hazards.

Inside the Hazards folder, create a block Part named Hazard with Size 825, 1, 576 and CFrame.Position 174, -6.5, 38 so the part covers the water around the island and platforms.

Set Transparency to 1 so the part is invisible and the actual water appears to be the hazard, disable CanCollide so players fall through it into the water, and enable Anchored so physics doesn't move it.

```

## [Detect when players touch the hazard](#detect-when-players-touch-the-hazard)[](#detect-when-players-touch-the-hazard)

The hazard doesn't do anything until you write a script that listens Touched  and lowers the player's health to zero.

Build with Assistant Build it Yourself

Create HazardService

```

In ServerScriptService, create a Script named HazardService with the following code:

```lua

local Players = game:GetService("Players")

local Workspace = game:GetService("Workspace")

local hazardsFolder = Workspace.World.Hazards

local hazards = hazardsFolder:GetChildren()

local function onHazardTouched(otherPart)

	local character = otherPart.Parent

	local player = Players:GetPlayerFromCharacter(character)

	if player then

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			humanoid.Health = 0

		end

	end

end

for _, hazard in hazards do

	hazard.Touched:Connect(onHazardTouched)

end

```

```

Code explanation

The HazardService  has many similarities to CoinService . However, instead of collecting a coin, the player has their health set to 0  when they touch a hazard.

Feel free to modify, add, or remove hazard objects in your game to create unique obstacles. As long as they are contained in the Hazards  folder, the code loop connects the event handler to all of your hazards.

## [Connect to the player lifecycle](#connect-to-the-player-lifecycle)[](#connect-to-the-player-lifecycle)

The player lifecycle represents events that occur when players interact in your game, such as joining, leaving, or respawning. You need to connect handlers to these events to execute logic for each major lifecycle event.

Build with Assistant Build it Yourself

Add lifecycle handlers to CoinService

```

In ServerScriptService, append the following code to the bottom of the existing CoinService Script (don't replace any of the existing code — add this after it):

```lua

local function onPlayerAdded(player)

	-- Reset player coins to 0

	updatePlayerCoins(player, function(_)

		return 0

	end)

	player.CharacterAdded:Connect(function(character)

		-- WaitForChild would stop the player loop, so below should be done in a separate thread

		task.spawn(function()

			-- When a player dies

			character:WaitForChild("Humanoid").Died:Connect(function()

				-- Reset player coins to 0

				updatePlayerCoins(player, function(_)

					return 0

				end)

			end)

		end)

	end)

end

-- Initialize any players added before connecting to PlayerAdded event

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

local function onPlayerRemoved(player)

	updatePlayerCoins(player, function(_)

		return nil

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

Players.PlayerRemoving:Connect(onPlayerRemoved)

```

```

Code explanation

The code defines functions to reset coin counts during the appropriate lifecycle events:

-

[Players.PlayerAdded](/docs/en-us/reference/engine/classes/Players#PlayerAdded)  fires when a player joins the game, and sets the coin count to 0 .

-

[Player.CharacterAdded](/docs/en-us/reference/engine/classes/Player#CharacterAdded)  fires when a player's character model is added to the world. It occurs after [PlayerAdded](/docs/en-us/reference/engine/classes/Players#PlayerAdded)  and whenever the player respawns.

-

[Humanoid.Died](/docs/en-us/reference/engine/classes/Humanoid#Died)  fires when a player dies, and sets the coin count to 0 . [task.spawn()](/docs/en-us/reference/engine/libraries/task#spawn)  creates a separate thread for handling this, so other aspects of the player life cycle can execute.

-

[Player.PlayerRemoved](/docs/en-us/reference/engine/classes/Player#PlayerRemoved)  fires when a player leaves the game to clean up player state.

-

This code contains a potential issue where players could collect coins before the Players.PlayerAdded  event executes and then have their coin counts reset to zero. To mitigate this issue, consider solutions such as code scheduling or freezing the player's character until initialization finishes. However, these solutions involve more complex scripting concepts that are beyond the scope of this tutorial.

## [Playtest](#playtest)[](#playtest)

Select Test  from the dropdown and click Play . Collect a few coins, then jump into the water. You character should die and respawn at the start, with their coin count reset to 0 .

[Next](/docs/en-us/tutorials/curriculums/core/scripting/script-an-upgrade-button)[Previous](/docs/en-us/tutorials/curriculums/core/scripting/record-and-display-player-data)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
