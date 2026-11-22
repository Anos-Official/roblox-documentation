<!-- Source: https://create.roblox.com/docs/players/teams -->

Implement teams | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/teams.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)

# Implement teams

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/teams.md)

You can divide players in your game into multiple teams using the [Teams](/docs/reference/engine/classes/Teams)  service. By [configuring](#add-teams)  the [Teams](/docs/reference/engine/classes/Teams)  service and [assigning teams](#assign-players-to-teams) , players are automatically differentiated by their [display name](/docs/characters/name-health-display)  color, as well as their name in the default player list.

## [Add teams](#add-teams)[](#add-teams)

By default, no teams are configured. To add teams:

1.

In the [Explorer](/docs/studio/explorer)  hierarchy, hover over the [Teams](/docs/reference/engine/classes/Teams)  object and click the ⊕  icon to show a list of objects.

2.

Insert a new [Team](/docs/reference/engine/classes/Team)  object under the [Teams](/docs/reference/engine/classes/Teams)  service.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Teams-Team.png)

3.

Select the new [Team](/docs/reference/engine/classes/Team)  object and, in the [Properties](/docs/studio/properties)  window, change the team [Name](/docs/reference/engine/classes/Team#Name)  and assign a unique matching [TeamColor](/docs/reference/engine/classes/Team#TeamColor) . A team's name and color both appear in the game's player list.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Team-Name-TeamColor.png)

4.

Repeat these steps to add more teams.

## [Assign players to teams](#assign-players-to-teams)[](#assign-players-to-teams)

By default, Roblox auto-assigns  new players joining the game to the team with the fewest members, and you can still use the following steps to assign players to a specific team.

1.

Select each [Team](/docs/reference/engine/classes/Team)  object in the [Teams](/docs/reference/engine/classes/Teams)  service to display its properties.

2.

Uncheck the [AutoAssignable](/docs/reference/engine/classes/Team#AutoAssignable)  checkbox.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Team-AutoAssignable-Disabled.png)

3.

Assign a player to a specific team by changing their [Player.Team](/docs/reference/engine/classes/Player#Team)  property to the team name in the format of Teams[TEAM_NAME] , such as Teams["Blue Team"] .

## [Team spawn locations](#team-spawn-locations)[](#team-spawn-locations)

You can use [SpawnLocation](/docs/reference/engine/classes/SpawnLocation)  objects to spawn players of different teams at specific locations when they join or respawn. By default, [SpawnLocations](/docs/reference/engine/classes/SpawnLocation)  are neutral  and any player can spawn upon them, so you need to lock each one to the team that can occupy it using the following steps:

1.

Using the [Explorer](/docs/studio/explorer) , insert a new [SpawnLocation](/docs/reference/engine/classes/SpawnLocation)  into the workspace.

2.

With the new [SpawnLocation](/docs/reference/engine/classes/SpawnLocation)  selected, uncheck its [Neutral](/docs/reference/engine/classes/SpawnLocation#Neutral)  checkbox in the [Properties](/docs/studio/properties)  window.

3.

Set the spawn's [TeamColor](/docs/reference/engine/classes/SpawnLocation#TeamColor)  property to the [TeamColor](/docs/reference/engine/classes/Team#TeamColor)  of an existing [team](#add-teams) . For example, if the intended team's [Team.TeamColor](/docs/reference/engine/classes/Team#TeamColor)  is Lapis , set the spawn's [SpawnLocation.TeamColor](/docs/reference/engine/classes/SpawnLocation#TeamColor)  to Lapis  as well.

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Team-Name-TeamColor.png)[Team.TeamColor](/docs/reference/engine/classes/Team#TeamColor)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/SpawnLocation-TeamColor.png)[SpawnLocation.TeamColor](/docs/reference/engine/classes/SpawnLocation#TeamColor)

Note that the [SpawnLocation.TeamColor](/docs/reference/engine/classes/SpawnLocation#TeamColor)  property is different from [SpawnLocation.BrickColor](/docs/reference/engine/classes/SpawnLocation#BrickColor)  and [SpawnLocation.Color](/docs/reference/engine/classes/SpawnLocation#Color)  which represent the visual  color of the spawn object and are not related to team functionality.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
