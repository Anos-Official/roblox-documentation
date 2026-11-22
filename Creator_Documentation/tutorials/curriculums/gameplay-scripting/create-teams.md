<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/gameplay-scripting/create-teams -->

Create teams | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/gameplay-scripting/create-teams.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Create teams

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/gameplay-scripting/create-teams.md)

Creating teams  lets you sort players into groups that compete to complete a common objective, such as scoring the most points or crossing a finish line before other enemy team members. For a first-person shooter, creating teams is particularly important because it establishes complex, coordinated gameplay strategies beyond the skill set of any individual player.

Using the [sample laser tag game](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  as a reference, this section of the tutorial teaches you how to sort players into teams, including scripting guidance on:

-

Using the [Teams](/docs/en-us/reference/engine/classes/Teams)  service's default functionality to assign players into either the green or pink team.

-

Helping players differentiate between their allies and enemy team members through on-screen and in-game team indicators.

-

Enabling forgiving gameplay that doesn't penalize players for blasting their teammates.

After you complete this section, you will learn about the scripts that allow players to spawn or respawn to a neutral lobby or team spawn zone, customize first-person force field visuals, and handle client state both from the server and the client.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Intro.png)

## [Assign team colors](#assign-team-colors)[](#assign-team-colors)

The sample laser tag game uses the [Teams](/docs/en-us/reference/engine/classes/Teams)  service as a basis for creating two teams because the service offers built-in team sorting behavior that broadly works out-of-the-box. For example, without any additional scripting effort, the service handles actions like:

-

Sorting and balancing players evenly into each team.

-

Grouping players under their team on the leaderboard.

-

Tinting player names in the 3D space to their corresponding team color.

-

Spawning players to distinct spawn locations that only their team can access.

Because of this default functionality, the sample enables the [Teams](/docs/en-us/reference/engine/classes/Teams)  service, then uses two distinct [Team](/docs/en-us/reference/engine/classes/Team)  objects with different [Team.Color](/docs/en-us/reference/engine/classes/Team#Color)  properties values to represent each team: mint  for the team that assembles on one side of the map, and carnation pink  for the team that assembles on the opposite side of the map. These specific colors are useful because they are complementary, meaning that they contrast each other well, and they enable players to easily scan their surroundings and orient themselves within the building and to other players.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Green-Team-Players.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Pink-Team-Players.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Green-Team-Properties.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Pink-Team-Properties.png)

To learn more about this color theme, see [Select a Color Theme](/docs/en-us/tutorials/curriculums/user-interface-design/choose-an-art-style#select-a-color-theme)  from the UI Curriculum.

It's important to note the exact [BrickColor](/docs/en-us/reference/engine/datatypes/BrickColor)  name for the [Team.Color](/docs/en-us/reference/engine/classes/Team#Color)  property because the game uses this name throughout many scripts in the game to keep track of players as they sort into teams, increment points as players tag out enemy players during a round, and update custom UI elements. For example, when a round begins, ReplicatedStorage  ⟩ HUDGuiSetup  requires startSyncingTeamColor ,and startSyncingTeamPoints  which both reference [Team.Color](/docs/en-us/reference/engine/classes/Team#Color)  to perform unique actions for each team.

startSyncingTeamColor startSyncingTeamPoints

startSyncingTeamColor  references [Team.Color](/docs/en-us/reference/engine/classes/Team#Color)  so that it can assign the correct color and icon for the player's team indicator at the bottom-left corner of their screen.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Green-Team.jpg) Green Team

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Pink-Team.jpg) Pink Team

```

local function setPlayerTeamIcon(gui: ScreenGui)

	for _, teamColorIcon in gui.PlayerDisplay.TeamIcons:GetChildren() do

		local iconTeamColor = teamColorIcon:GetAttribute(GuiAttribute.teamColor)

		teamColorIcon.Visible = localPlayer.TeamColor == iconTeamColor

	end

end

local function startSyncingTeamColor(gui: ScreenGui)

	setPlayerTeamIcon(gui)

	localPlayer:GetPropertyChangedSignal("Team"):Connect(function()

		setPlayerTeamIcon(gui)

	end)

end

```

## [Display team indicators](#display-team-indicators)[](#display-team-indicators)

Once a player is sorted into a team, they need to be able to quickly decipher what team they belong to, and differentiate between their allies and enemy team members. This ability is important because the gameplay of a first-person shooter game requires players to make quick strategic decisions while they're in combat zones so that they don't get tagged out and lose the round.

To set players up for success, the sample laser tag game provides multiple team indicators both on-screen and in the 3D space:

-

Player Indicator  – Custom on-screen UI that displays the player's team color and icon.

-

Team Indicator  – Custom in-game UI that displays the player's team color.

-

Leaderboard Indicator  – Default Teams service on-screen UI that groups players underneath their team color.

-

Name Tint  – Default Teams service in-game UI that tints the player's name above their head to their team color.

** On-screen Indicators**

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Player-Indicator.jpg) Player Indicator

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Leaderboard-Indicator.jpg) Leaderboard Indicator

** In-game Indicators**

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Team-Indicator.jpg) Team Indicator

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Name-Tint.jpg) Name Tint

You don't need to do any additional work for the Leaderboard Indicator or Name Tint outside of assigning team colors from the previous section of the tutorial, but the custom UI team indicators require more programming effort to both display the indicators and occlude enemy indicators when they are behind walls. For a full explanation of the scripts that control the custom UI behavior, as well as how to implement each UI element itself, see [Player Indicator](/docs/en-us/tutorials/curriculums/user-interface-design/implement-designs-in-studio#player-indicator)  and [Team Indicator](/docs/en-us/tutorials/curriculums/user-interface-design/implement-designs-in-studio#team-indicator)  from the UI Curriculum.

## [Disable friendly fire](#disable-friendly-fire)[](#disable-friendly-fire)

While some first-person shooter games penalize players who blast their own teammates, the sample laser tag game allows for more forgiving gameplay by disabling friendly fire. This design decision allows everyone to only increase their team score, not subtract from it due to gameplay accidents.

To understand how the sample implements this functionality, examine how ServerScriptService  ⟩ LaserBlastHandler  ⟩ processTaggedPlayers  ⟩ onPlayerTagged  handles dealing damage to tagged players. When the server detects a collision between a player's blast and another player, it calls the onPlayerTagged  function to understand which player fired the blast, which player was hit by the blast, and how much damage it should remove from the player's health according to the blaster type.

```

local function onPlayerTagged(playerBlasted: Player, playerTagged: Player, damageAmount: number)

```

Before it decreases health, the script first verifies if the tagged player is on the same team as the player who initiated the blast. If they are on the same team, the script ignores the blast data entirely.

```

local character = playerTagged.Character

	local isFriendly = playerBlasted.Team == playerTagged.Team

	-- Disallow friendly fire

	if isFriendly then

		return

	end

```

However, if the tagged player is  on the enemy team, the player takes the appropriate amount of damage according to the blaster type. In addition, if the player takes enough damage to become tagged out, the script rewards a point to the team of the player that initiated the blast. For more information on how the sample tracks points, see [Add rounds](/docs/en-us/tutorials/curriculums/gameplay-scripting/add-rounds#track-points)  later in the tutorial.

```

local humanoid = character and character:FindFirstChild("Humanoid")

	if humanoid and humanoid.Health > 0 then

		local damage = math.min(damageAmount, humanoid.Health)

		humanoid:TakeDamage(damage)

		if humanoid.Health <= 0 then

			Scoring.incrementScore(playerBlasted, 1)

		end

	end

end

return onPlayerTagged

```

For more information on what happens when a player fires their blaster, see [Implement blaster behavior](/docs/en-us/tutorials/curriculums/gameplay-scripting/implement-blasters)  and [Detect hits](/docs/en-us/tutorials/curriculums/gameplay-scripting/detect-hits)  later on in the tutorial.

If you were to test the game right now, all players would randomly spawn at either spawn zone at opposite ends of the arena regardless of what team they belong to, meaning that each team would spawn right next to each other.

To address this issue, the following section of the tutorial teaches you about the custom logic behind restricting team spawning to certain spawn locations, handling client state as players leave the spawn area after selecting their blaster, and respawning players back to their spawn zone or lobby area when their health reaches zero.

[Next](/docs/en-us/tutorials/curriculums/gameplay-scripting/spawn-respawn)[Previous](/docs/en-us/tutorials/curriculums/gameplay-scripting)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
