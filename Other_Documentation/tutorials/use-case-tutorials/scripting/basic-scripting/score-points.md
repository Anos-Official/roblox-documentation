<!-- Source: https://create.roblox.com/docs/tutorials/use-case-tutorials/scripting/basic-scripting/score-points -->

Score points | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/scripting/basic-scripting/score-points.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Scripting
6. /
7. Basic gameplay

# Score points

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/score-points.md)

In previous tutorials, you made a variety of game features including [fading platforms](/docs/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)  and [deadly lava](/docs/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava) . This tutorial ties these together into a playable game where users see who can stay alive the longest. Every second they stay alive, a point will be added to their score.

## [Set up](#set-up)[](#set-up)

First up, you'll need to set the scene for your game. Duplicate the [fading platforms](/docs/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)  you made in the previous tutorial and let users compete to stay on the board of platforms for as long as possible.

You can also use [deadly lava](/docs/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)  to kill users when they fall off the platforms, or just let them fall to their doom. Make sure you place a SpawnLocation  somewhere where users can jump onto the platforms to start playing.

![Spawn point above a grid of fading platforms, above a lava floor](https://prod.docsiteassets.roblox.com/assets/tutorials/scoring-points/sceneInPlace.jpg)

## [Player points](#player-points)[](#player-points)

Roblox has a built-in Leaderboard  for showing user stats. When you set player points through the leaderboard, they show up on the right side of the screen in the game.

 ![Leaderboard with username and points shown](https://prod.docsiteassets.roblox.com/assets/tutorials/scoring-points/leaderboard.jpg)

You'll learn more customizable ways to display information in later tutorials, but the leaderboard is the simplest way of making a visible scoring system in Roblox.

It's best to put scripts which set up game state into ServerScriptService  because they will automatically run when the game starts. In ServerScriptService , create a script called SetupPoints .

 ![SetupPoints script in place in ServerScriptService in the Explorer window](https://prod.docsiteassets.roblox.com/assets/tutorials/scoring-points/setupPointsScript.jpg)

## [Listen for players](#listen-for-players)[](#listen-for-players)

In Roblox, a service  is an object which performs a range of useful functions. The [Players](/docs/reference/engine/classes/Players)  service has an event called [PlayerAdded](/docs/reference/engine/classes/Players#PlayerAdded)  that you can use to set up points for each user who joins the game.

You can access services with the [GetService](/docs/reference/engine/classes/ServiceProvider#GetService)  function in the [game](/docs/reference/engine/classes/DataModel)  object. [game](/docs/reference/engine/classes/DataModel)  is a variable accessible from anywhere which contains everything in your game.

1.

Create a variable for the Players service using game:GetService("Players") .

2.

Create a function called onPlayerAdded  with a parameter for the incoming player.

3.

Connect the onPlayerAdded  function to the PlayerAdded event.

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

When declaring a variable to contain a service, it's best to name it with the exact name of the service ("Players" ), even though this means breaking usual naming conventions for variables.

## [Create a stats folder](#create-a-stats-folder)[](#create-a-stats-folder)

To make a user's points display in the leaderboard, all you need to do is create a new [Folder](/docs/reference/engine/classes/Folder)  in their [Player](/docs/reference/engine/classes/Player)  object called "leaderstats"  and put their points in there. New objects can be created from within a script via the [Instance.new()](/docs/reference/engine/datatypes/Instance#new)  function.

1.

Create a new Folder  object using Instance.new("Folder") , storing the result in a new variable called leaderstats .

```

local function onPlayerAdded(player)

	local leaderstats = Instance.new("Folder")

end

```

2.

Set the Name property of leaderstats  to "leaderstats" .

3.

Parent leaderstats  to player .

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	local leaderstats = Instance.new("Folder")

   leaderstats.Name = "leaderstats"

   leaderstats.Parent = player

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Make sure you name the folder exactly  as it is shown here ("leaderstats" ) or it will not work!

## [Create the points](#create-the-points)[](#create-the-points)

The leaderboard system reads any values in the leaderstats  folder and displays whatever it finds.

To add a stat which will track a player's points, a new IntValue  object can be parented to the leaderstats  folder. The name of the value object will be displayed alongside its current value.

1.

Use a variable named points  to create a new IntValue  object using [Instance.new()](/docs/reference/engine/datatypes/Instance#new) .

2.

Set the Name  to "Points" .

3.

Set the Value  to 0 ; this is what the leaderboard will initially display for the player.

4.

Parent the points  object to the leaderstats  folder.

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Test your game and you should see the leaderboard appear in the top right with the names of your users and a points score next to them.

## [Count time](#count-time)[](#count-time)

Each user should earn a point for each second they are alive. A while  loop and the [task.wait()](/docs/reference/engine/libraries/task#wait)  function can be used to update the value of points every second.

1.

At the end of the script, create a while  loop with true  as the condition.

2.

In the loop, [task.wait()](/docs/reference/engine/libraries/task#wait)  for 1 second.

```

Players.PlayerAdded:Connect(onPlayerAdded)

while true do

  task.wait(1)

end

```

## [Player list](#player-list)[](#player-list)

To run code for every user in the game, you need to iterate through the array  of users returned by the [GetPlayers](/docs/reference/engine/classes/Players#GetPlayers)  function.

An array is a list of items stored in order. Each item can be accessed by its index  position, starting from 1 . You can get the length of an array by prefixing it with # .

1.

Store the result of [Players:GetPlayers()](/docs/reference/engine/classes/Players#GetPlayers)  in a playerList  variable.

2.

Create a for  loop with a starting value of 1 and an end value of #playerList , so that you get one iteration of the loop per player.

```

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for currentPlayer = 1, #playerList do

    -- Add your logic here for each player in the playerList

  end

end

```

## [Award points](#award-points)[](#award-points)

To award a point to each user in the for loop, you'll need to get the user out of the array and add 1 to the Points  object stored in their leaderstats  folder.

Objects stored in an array are accessed using square brackets  - for instance, the first item in the playerList  array can be accessed with playerList[1] . If you write playerList[currentPlayer]  in the for loop, you can move through each user in the list with every iteration of the loop.

1.

Store the user at playerList[currentPlayer]  in a variable called player .

2.

Store the user's Points  object in a variable called points .

3.

Set the [Value](/docs/reference/engine/classes/IntValue#Value)  property of points  to points.Value + 1 .

```

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for currentPlayer = 1, #playerList do

    local player = playerList[currentPlayer]

    local points = player.leaderstats.Points

    points.Value += 1

  end

end

```

Test your game and you should find that the leaderboard shows your player's score counting up by 1 every second.

## [Listen for characters](#listen-for-characters)[](#listen-for-characters)

The goal of the game is to see who can stay alive the longest, so users who die will need to have their points reset to 0.

You'll need to get the Character  model for the user in order to detect when they have died. This model is only added to the game * after*  the [Player](/docs/reference/engine/classes/Player)  object has been loaded and you can use the [CharacterAdded](/docs/reference/engine/classes/Player#CharacterAdded)  event to listen for when the character is ready to use. Create a function called onCharacterAdded  with two parameters: one for the character, one for the player.

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

end

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

```

Although you included user in the onCharacterAdded  function's parameters, the actual [CharacterAdded](/docs/reference/engine/classes/Player#CharacterAdded)  event only returns the character, not the associated user. To pass the player  object as well, use an [anonymous function](/docs/luau/functions#anonymous-functions)  for the event connection.

```

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

  player.CharacterAdded:Connect(function(character)

    onCharacterAdded(character, player)

  end)

end

```

## [Reset points](#reset-points)[](#reset-points)

When a user dies, their [Humanoid](/docs/reference/engine/classes/Humanoid)  automatically fires a [Died](/docs/reference/engine/classes/Humanoid#Died)  event. You can use this event to find out when to reset their points.

The Humanoid is found inside the Character model, but the contents of that model are only assembled as the user spawns. To make your code safely wait for the Humanoid object to load, use the [WaitForChild()](/docs/reference/engine/classes/Instance#WaitForChild)  function. You can call it on any parent object, passing the string name of the child you're waiting for. Create a variable to wait for the Humanoid using character:WaitForChild("Humanoid") .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  local humanoid = character:WaitForChild("Humanoid")

end

```

The function you need to connect to the Died event is very short and will only ever be needed here, so you can use an anonymous function again.

1.

Connect a new anonymous function to the Humanoid's Died  event.

2.

In the anonymous function, create a variable called points  for the player's Points  object.

3.

Set the [Value](/docs/reference/engine/classes/IntValue#Value)  property of points  to 0 .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  local humanoid = character:WaitForChild("Humanoid")

  humanoid.Died:Connect(function()

    local points = player.leaderstats.Points

    points.Value = 0

  end)

end

```

Test this out and you'll see the user's score resets when they die.

## [Check the player](#check-the-player)[](#check-the-player)

If users keep earning points even when dead, it's hardly in the spirit of the game, so the code needs to check if users are alive before awarding a point.

You need to start by defining an attribute  in the onPlayerAdded  function which can be used to check whether the user is alive. At this point, the user is not yet alive and spawned, as their character model still needs to be added.

Attributes allow you to customize objects in Roblox with your own data. An attribute consists of a name and a value. You can create one on any object using the [SetAttribute](/docs/reference/engine/classes/Instance#SetAttribute)  function. Call [SetAttribute](/docs/reference/engine/classes/Instance#SetAttribute)  on player  to create a new attribute  called "IsAlive"  with the value false .

```

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

  player:SetAttribute("IsAlive", false)

  player.CharacterAdded:Connect(function(character)

    onCharacterAdded(character, player)

  end)

end

```

Once the user's character model respawns, the value of IsAlive  needs to be changed to true  so that the user can start earning points again.

1.

In onCharacterAdded , set the IsAlive  attribute of player  to true .

2.

In onCharacterDied , set the IsAlive  attribute of player  to false .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  player:SetAttribute("IsAlive", true)

  local humanoid = character:WaitForChild("Humanoid")

  humanoid.Died:Connect(function()

    local points = player.leaderstats.Points

    points.Value = 0

    player:SetAttribute("IsAlive", false)

  end)

end

```

Finally, IsAlive  should be checked  before any point is awarded in the while  loop at the end of the script. The [GetAttribute](/docs/reference/engine/classes/Instance#GetAttribute)  function takes the name of an attribute and returns the value. In the while  loop, wrap the code to award a point in an if  statement with the condition player:GetAttribute("IsAlive") .

```

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for currentPlayer = 1, #playerList do

    local player = playerList[currentPlayer]

    if player:GetAttribute("IsAlive") then

      local points = player.leaderstats.Points

      points.Value += 1

    end

  end

end

```

Test your game out now and you should find the user earns points every second they are alive, and stays at 0 when not alive. Have your friends play with you and see who can get the highest score.

This is just the start: you can continue improving your game for your users. Here are some tips:

-

Place the code for all of the platforms into a single script, making it much easier to update.

-

Create a lobby area where users wait to be teleported to the game area, allowing users to start simultaneously.

-

Announce the winners of each round.

## [Final code](#final-code)[](#final-code)

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  player:SetAttribute("IsAlive", true)

  local humanoid = character:WaitForChild("Humanoid")

  humanoid.Died:Connect(function()

    local points = player.leaderstats.Points

    points.Value = 0

    player:SetAttribute("IsAlive", false)

  end)

end

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

  player:SetAttribute("IsAlive", false)

  player.CharacterAdded:Connect(function(character)

    onCharacterAdded(character, player)

  end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for i = 1, #playerList do

    local player = playerList[i]

    if player:GetAttribute("IsAlive") then

      local points = player.leaderstats.Points

      points.Value += 1

    end

  end

end

```

[Previous](/docs/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
