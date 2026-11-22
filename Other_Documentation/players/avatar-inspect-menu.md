<!-- Source: https://create.roblox.com/docs/players/avatar-inspect-menu -->

Avatar Inspect Menu | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/avatar-inspect-menu.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)
6. /
7. Player UI

# Avatar Inspect Menu

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/avatar-inspect-menu.md)

The Avatar Inspect Menu  allows users to view another user's Roblox avatar character, try on items, and even make purchases within a game. Roblox enables this menu by default and users in your game can access this menu in three ways:

-

Opening the game's main menu and clicking the View  button next to a user in the Players  tab.

-

Clicking on a user's name in the player list.

-

Selecting the Inspect option in the [Avatar Context Menu](/docs/players/avatar-context-menu) , an opt-in feature which provides additional user-to-user social interaction.

You can customize a user's Avatar Inspect Menu  in the following ways:

-

Change the inspect target from the user's Roblox avatar to their [current in-game appearance](#inspect-currently-equipped-items) .

-

Change the inspect target to a [specific User ID](#inspect-specific-users) , even if they are not in the game.

For more specific catalog access, you can also use the [Avatar Editor Service](/docs/players/avatar-editor)  to access and make changes to a user's platform-wide avatar within a game.

## [Inspect currently equipped items](#inspect-currently-equipped-items)[](#inspect-currently-equipped-items)

By default, the Inspect Menu shows the same information as the user's Roblox Avatar profile page. The avatar outfit may not match the user's current appearance, since you may have opted to equip different accessories or avatar items at that specific moment.

In the cases where the default Inspect Menu may not be accurate to the current character's outfit, you can inspect a character's current outfit with the following steps:

1.

Disable the default profile-based Inspect Menu by setting [GuiService:SetInspectMenuEnabled()](/docs/reference/engine/classes/GuiService#SetInspectMenuEnabled)  with a value of false .

2.

Get a current [HumanoidDescription](/docs/reference/engine/classes/HumanoidDescription)  from the target player character.

3.

Call [GuiService:InspectPlayerFromHumanoidDescription()](/docs/reference/engine/classes/GuiService#InspectPlayerFromHumanoidDescription)  to load the Inspect menu based off of the [HumanoidDescription](/docs/reference/engine/classes/HumanoidDescription) .

Use the following code sample to inspect the currently equipped items of a specific player:

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Make profile-based Inspect Menu inaccessible

GuiService:SetInspectMenuEnabled(false)

local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

if humanoid then

	-- Get current HumanoidDescription from a player character

	local humanoidDescription = humanoid:GetAppliedDescription()

	-- Load the inspect menu from a humanoid description

	GuiService:InspectPlayerFromHumanoidDescription(humanoidDescription, player.Name)

end

```

## [Inspect specific users](#inspect-specific-users)[](#inspect-specific-users)

The Avatar Inspect Menu can inspect players who aren't in the current game. You can use [GuiService:InspectPlayerFromUserId()](/docs/reference/engine/classes/GuiService#InspectPlayerFromUserId)  to inspect a player from any [Player.UserId](/docs/reference/engine/classes/Player#UserId) .

Use the following code sample to open the Avatar Inspect Menu based on a [UserId](/docs/reference/engine/classes/Player#UserId) :

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

-- Get user ID by username

local success, userId = pcall(function()

	return Players:GetUserIdFromNameAsync("RobloxUser")

end)

if success then

	GuiService:InspectPlayerFromUserId(userId)

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
