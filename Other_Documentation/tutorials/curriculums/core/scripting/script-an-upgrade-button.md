<!-- Source: https://create.roblox.com/docs/tutorials/curriculums/core/scripting/script-an-upgrade-button -->

Script an upgrade button | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/core/scripting/script-an-upgrade-button.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Script an upgrade button

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/core/scripting/script-an-upgrade-button.md)

Players can now collect coins and lose them when they die, but the coins don't do anything, and most of the 3D world is inaccessible without the ability to jump very high. This section of the tutorial teaches you how to finish the logic for your game by adding an on-screen button that spends coins to increase jumping power.

## [Create the upgrade button](#create-the-upgrade-button)[](#create-the-upgrade-button)

2D interfaces in Roblox are typically made up of a collection of GUI components inside of a GUI container. In this case, you only need a [TextButton](/docs/reference/engine/classes/TextButton)  component that says Upgrade Jump (5 Coins) inside a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  container.

Build with Assistant Build it Yourself

Set up the upgrade GUI

```

In ReplicatedStorage, create a folder named Instances.

Inside the Instances folder, create a ScreenGui named JumpPurchaseGui with ResetOnSpawn disabled.

Inside JumpPurchaseGui, create a TextButton named JumpButton with the following properties:

- Text: "Upgrade Jump (5 Coins)"

- TextSize: 25

- AnchorPoint: 1, 1

- Position: {1, 0}, {1, 0}

Also inside the Instances folder, create a RemoteFunction named IncreaseJumpPowerFunction.

Finally, on the StarterPlayer service, enable the CharacterUseJumpPower property.

```

## [Define jump power data](#define-jump-power-data)[](#define-jump-power-data)

Currently, only coin count is stored for each player in the PlayerData  module script. You need to also store and update jump power in the same way. Because the functions in PlayerData  are non-specific to the data being changed, all that's required to store player jump power is to add a Jump  key and initialize its initial value in defaultPlayerData() .

Build with Assistant Build it Yourself

Update PlayerData with jump power

```

In ServerStorage, replace the existing PlayerData ModuleScript's code with the following:

```lua

local PlayerData = {}

PlayerData.COIN_KEY_NAME = "Coins"

PlayerData.JUMP_KEY_NAME = "Jump"

local playerData = {

	--[[

		[userId: string] = {

			["Coins"] = coinAmount: number,

			["Jump"] = jumpPower: number

		}

	--]]

}

local function defaultPlayerData()

	return {

		[PlayerData.COIN_KEY_NAME] = 0,

		[PlayerData.JUMP_KEY_NAME] = 0,

	}

end

local function getData(player)

	local data = playerData[tostring(player.UserId)] or defaultPlayerData()

	playerData[tostring(player.UserId)] = data

	return data

end

function PlayerData.getValue(player, key)

	return getData(player)[key]

end

function PlayerData.updateValue(player, key, updateFunction)

	local data = getData(player)

	local oldValue = data[key]

	local newValue = updateFunction(oldValue)

	data[key] = newValue

	return newValue

end

return PlayerData

```

```

## [Update jump power data](#update-jump-power-data)[](#update-jump-power-data)

Now that PlayerData  is able to track jump power, you need to implement logic on the server to upgrade jump power from a player's client request.

The server and client can communicate through either [RemoteEvents](/docs/reference/engine/classes/RemoteEvent)  or [RemoteFunctions](/docs/reference/engine/classes/RemoteFunction) . Remote events don't yield when they're fired and can be used for one-way communication. Remote functions, on the other hand, yield until they receive a reply, which allows for two-way communication.

For this tutorial, the client needs to know if the server upgraded the player's jump power successfully, so you should use a remote function.

Build with Assistant Build it Yourself

Create JumpService

```

In ServerScriptService, create a Script named JumpService with the following code:

```lua

-- Services

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local ServerStorage = game:GetService("ServerStorage")

local Players = game:GetService("Players")

-- Modules

local Leaderboard = require(ServerStorage.Leaderboard)

local PlayerData = require(ServerStorage.PlayerData)

-- Events

local IncreaseJumpPowerFunction = ReplicatedStorage.Instances.IncreaseJumpPowerFunction

local JUMP_KEY_NAME = PlayerData.JUMP_KEY_NAME

local COIN_KEY_NAME = PlayerData.COIN_KEY_NAME

local JUMP_POWER_INCREMENT = 30

local JUMP_COIN_COST = 5

local function updateJumpPower(player, updateFunction)

	-- Update the jump power table

	local newJumpPower = PlayerData.updateValue(player, JUMP_KEY_NAME, updateFunction)

	-- Update the players jump power

	local character = player.Character or player.CharacterAdded:Wait()

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.JumpPower = newJumpPower

		-- Update the jump leaderboard

		Leaderboard.setStat(player, JUMP_KEY_NAME, newJumpPower)

	end

end

local function onPurchaseJumpIncrease(player)

	local coinAmount = PlayerData.getValue(player, COIN_KEY_NAME)

	if coinAmount < JUMP_COIN_COST then

		return false

	end

	-- Increase player's jump power

	updateJumpPower(player, function(oldJumpPower)

		oldJumpPower = oldJumpPower or 0

		return oldJumpPower + JUMP_POWER_INCREMENT

	end)

	-- Update the coin table

	local newCoinAmount = PlayerData.updateValue(player, COIN_KEY_NAME, function(oldCoinAmount)

		return oldCoinAmount - JUMP_COIN_COST

	end)

	-- Update the coin leaderboard

	Leaderboard.setStat(player, COIN_KEY_NAME, newCoinAmount)

	return true

end

local function onCharacterAdded(player)

	-- Reset player's jump power when the character is added

	updateJumpPower(player, function(_)

		return 0

	end)

end

-- Initialize any players added before connecting to PlayerAdded event

for _, player in Players:GetPlayers() do

	onCharacterAdded(player)

end

-- Normal initialization of players from PlayerAdded event

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function()

		onCharacterAdded(player)

	end)

end

local function onPlayerRemoved(player)

	updateJumpPower(player, function(_)

		return nil

	end)

end

IncreaseJumpPowerFunction.OnServerInvoke = onPurchaseJumpIncrease

Players.PlayerAdded:Connect(onPlayerAdded)

Players.PlayerRemoving:Connect(onPlayerRemoved)

```

```

Code explanation

The following sections describe the code in more detail.

-

Update the jump power data  - updateJumpPower()  updates the jump power of the player and the leaderboard to provide visual feedback. This function resembles the code that damages players in [Create player hazards](/docs/tutorials/curriculums/core/scripting/create-player-hazards) . Provided a [Character](/docs/reference/engine/classes/Player#Character)  model and [Humanoid](/docs/reference/engine/classes/Humanoid)  exist for the player being upgraded, the function updates the [JumpPower](/docs/reference/engine/classes/Humanoid#JumpPower)  property to the new value stored by PlayerData , increasing it by 30. If you want your game to last slightly longer, you can decrease this number.

-

Validate server requests  - onPurchaseJumpIncrease()  first checks that the player actually has the number of coins required to purchase the upgrade. All requests  from clients to the server should be validated  to prevent bad actors submitting false requests and exploiting your game.

## [Add the button to the player GUI](#add-the-button-to-the-player-gui)[](#add-the-button-to-the-player-gui)

A [ScreenGui](/docs/reference/engine/classes/ScreenGui)  object only shows on-screen if it is parented to a player's [PlayerGui](/docs/reference/engine/classes/PlayerGui)  object. By default, this contains the system GUI such as the chat window. You now need to create a script in ReplicatedStorage  to copy the upgrade button into each player's GUI and implement behavior for when the button is pressed.

Build with Assistant Build it Yourself

Create JumpButtonClickHandler

```

In ReplicatedStorage, create a Script named JumpButtonClickHandler with RunContext set to Client and the following code:

```lua

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local IncreaseJumpPowerFunction = ReplicatedStorage.Instances.IncreaseJumpPowerFunction

local jumpPurchaseGui = ReplicatedStorage.Instances.JumpPurchaseGui

local jumpButton = jumpPurchaseGui.JumpButton

local function onButtonClicked()

	local success, purchased = pcall(IncreaseJumpPowerFunction.InvokeServer, IncreaseJumpPowerFunction)

	if not success then

		-- purchased will be the error message if success is false

		error(purchased)

	elseif success and not purchased then

		warn("Not enough coins!")

	end

end

jumpButton.Activated:Connect(onButtonClicked)

-- Add the JumpPurchaseGui to the player's Gui

jumpPurchaseGui.Parent = playerGui

```

```

Code explanation

The following sections describe the code in more detail.

-

Obtain references to the GUI and server function  - The variables IncreaseJumpPowerFunction , jumpPurchaseGui , and jumpButton  contain references to the function and GUI that calls the function that you'll need later.

-

Define the event handler  - onButtonClicked()  defines logic for when users click the upgrade button. It uses [pcall()](/docs/reference/engine/globals/LuaGlobals#pcall)  (protected call) to invoke the [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) . Any client-server communication like this requires [pcall()](/docs/reference/engine/globals/LuaGlobals#pcall)  to handle errors or connection issues.

-

Connect the handler to the button  - The [Activated](/docs/reference/engine/classes/GuiButton#Activated)  event is compatible on all platforms, including mouse, touchscreen, or gamepad contexts. It triggers when a click , touch , or gamepad button  is released.

## [Playtest](#playtest)[](#playtest)

Select Test  from the dropdown and click Play . The Upgrade Jump  button shows up in the bottom-right corner.

Try clicking the button before you collect any coins to check that it doesn't award you additional jumping power, then try collecting some coins and see if the upgrade works when you click again.

With the code complete, try tuning the difficulty: add coins if the pace feels slow, or remove a few and tuck them in trickier spots if upgrades come too easily.

[Next](/docs/tutorials/curriculums/core/building/create-basic-visual-effects)[Previous](/docs/tutorials/curriculums/core/scripting/create-player-hazards)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
