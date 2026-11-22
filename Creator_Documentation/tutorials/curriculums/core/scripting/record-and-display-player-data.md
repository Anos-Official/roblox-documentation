<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/core/scripting/record-and-display-player-data -->

Record and display player data | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/core/scripting/record-and-display-player-data.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Record and display player data

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/core/scripting/record-and-display-player-data.md)

Now that you can detect when a player has collected a coin, you need to count how many coins players have collected and make that amount visible on a leaderboard.

## [Create a module script to record coin collection](#create-a-module-script-to-record-coin-collection)[](#create-a-module-script-to-record-coin-collection)

To handle the storage and management of each player's coin collection data, you need to create a [ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript)  object to contain a data structure and functions that access coin collection data for every player. Module scripts are reusable code that other scripts can require. In this case, the CoinService requires this module script so that it can update coin collection data when players touch coins.

Build with Assistant Build it Yourself

Create PlayerData

```

In ServerStorage, create a ModuleScript named PlayerData with the following code:

```lua

local PlayerData = {}

PlayerData.COIN_KEY_NAME = "Coins"

local playerData = {

  --[[

    [userId: string] = {

      ["Coins"] = coinAmount: number

    }

  ]]

}

local function defaultPlayerData()

  return {

    [PlayerData.COIN_KEY_NAME] = 0

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

Code explanation

The module script defines a PlayerData  table that contains zero or many playerData  tables, which represent coin collection data for a player. Every script that requires this module script receives the same copy of the PlayerData  table, allowing multiple scripts to modify and share coin collection data.

#### Declare the data structures

The module script begins with a declaration of an empty table, PlayerData , which is returned at the end of the script. It also contains accessor methods to get and set values in the table.

The playerData  table contains comments that describe the structure of the table, which makes the code easier to understand. In this case, a playerData  table contains a userId  and a corresponding field named Coins  that represents the amount of collected coins for that player.

```

local PlayerData = {}

PlayerData.COIN_KEY_NAME = "Coins"

local playerData = {

  --[[

    [userId: string] = {

        ["Coins"] = coinAmount: number

    }

  ]]

}

...

return PlayerData

```

#### Define a local data accessor

getData()  is a local function that retrieves data for a specific playerData  table. If a player hasn't collected a coin, it returns a table from the defaultPlayerData()  function to ensure every player has some data associated with them. A common convention is to create simple, public-facing functions that offload logic to locally-scoped functions that do the heavy lifting.

```

local function defaultPlayerData()

  return {

    [PlayerData.COIN_KEY_NAME] = 0

  }

end

local function getData(player)

  local data = playerData[tostring(player.UserId)] or defaultPlayerData()

  playerData[tostring(player.UserId)] = data

  return data

end

```

#### Define public data accessors

getValue()  and updateValue()  are public-facing functions that other scripts that require this module script can call. In our case, the CoinService  uses these functions to update a player's coin collection data whenever that player touches a coin.

```

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

```

## [Implement a leaderboard](#implement-a-leaderboard)[](#implement-a-leaderboard)

You can represent the coin collection data visually with an on-screen leaderboard. Roblox includes a built-in system that automatically generates a leaderboard using a default UI.

Build with Assistant Build it Yourself

Create Leaderboard

```

In ServerStorage, create a ModuleScript named Leaderboard with the following code:

```lua

local Leaderboard = {}

-- Creating a new leaderboard

local function setupLeaderboard(player)

  local leaderstats = Instance.new("Folder")

  -- 'leaderstats' is a reserved name Roblox recognizes for creating a leaderboard

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  return leaderstats

end

-- Creating a new leaderboard stat value

local function setupStat(leaderstats, statName)

  local stat = Instance.new("IntValue")

  stat.Name = statName

  stat.Value = 0

  stat.Parent = leaderstats

  return stat

end

-- Updating a player's stat value

function Leaderboard.setStat(player, statName, value)

  local leaderstats = player:FindFirstChild("leaderstats")

  if not leaderstats then

    leaderstats = setupLeaderboard(player)

  end

  local stat = leaderstats:FindFirstChild(statName)

  if not stat then

    stat = setupStat(leaderstats, statName)

  end

  stat.Value = value

end

return Leaderboard

```

```

Code explanation

The following sections describe how the leaderboard works in more detail.

#### Create a leaderboard

The setupLeaderboard()  function creates a new folder instance named leaderstats  and sets it as a child of the specified player. Roblox automatically recognizes a folder named leaderstats  as a container of stats and creates a UI element to display the stats. It requires the values in leaderstats  to be stored as "value" objects (such as [StringValue](/docs/en-us/reference/engine/classes/StringValue) , [IntValue](/docs/en-us/reference/engine/classes/IntValue)  or [NumberValue](/docs/en-us/reference/engine/classes/NumberValue) ).

```

-- Creating a new leaderboard

local function setupLeaderboard(player)

  local leaderstats = Instance.new("Folder")

  -- 'leaderstats' is a reserved name Roblox recognizes for creating a leaderboard

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  return leaderstats

end

-- Creating a new leaderboard stat value

local function setupStat(leaderstats, statName)

  local stat = Instance.new("IntValue")

  stat.Name = statName

  stat.Value = 0

  stat.Parent = leaderstats

  return stat

end

```

#### Update player stats

setStat()  is the only public function in the Leaderboard  module. It creates stat values for a specified player or the leaderboard itself if it doesn't already exist.

[FindFirstChild()](/docs/en-us/reference/engine/classes/Instance#FindFirstChild)  takes the name of an object and returns the object if it exists, or nil  if it doesn't. It's a common, safe method of finding out if an object exists before you use it.

```

-- Updating a player's stat value

function Leaderboard.setStat(player, statName, value)

  local leaderstats = player:FindFirstChild("leaderstats")

  if not leaderstats then

    leaderstats = setupLeaderboard(player)

  end

  local stat = leaderstats:FindFirstChild(statName)

  if not stat then

    stat = setupStat(leaderstats, statName)

  end

  stat.Value = value

end

```

## [Integrate the module scripts](#integrate-the-module-scripts)[](#integrate-the-module-scripts)

With both modules in place, require them in the CoinService  script to manage and display player coin data.

Build with Assistant Build it Yourself

Update CoinService

```

In ServerScriptService, replace the existing CoinService Script's code with the following:

```lua

-- Initializing services and variables

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local ServerStorage = game:GetService("ServerStorage")

-- Modules

local Leaderboard = require(ServerStorage.Leaderboard)

local PlayerData = require(ServerStorage.PlayerData)

local coinsFolder = Workspace.World.Coins

local coins = coinsFolder:GetChildren()

local COIN_KEY_NAME = PlayerData.COIN_KEY_NAME

local COOLDOWN = 10

local COIN_AMOUNT_TO_ADD = 1

local function updatePlayerCoins(player, updateFunction)

  -- Update the coin table

  local newCoinAmount = PlayerData.updateValue(player, COIN_KEY_NAME, updateFunction)

  -- Update the coin leaderboard

  Leaderboard.setStat(player, COIN_KEY_NAME, newCoinAmount)

end

-- Defining the event handler

local function onCoinTouched(otherPart, coin)

  if coin:GetAttribute("Enabled") then

    local character = otherPart.Parent

    local player = Players:GetPlayerFromCharacter(character)

    if player then

      -- Player touched a coin

      coin.Transparency = 1

      coin:SetAttribute("Enabled", false)

      updatePlayerCoins(player, function(oldCoinAmount)

        oldCoinAmount = oldCoinAmount or 0

        return oldCoinAmount + COIN_AMOUNT_TO_ADD

      end)

      task.wait(COOLDOWN)

      coin.Transparency = 0

      coin:SetAttribute("Enabled", true)

    end

  end

end

-- Setting up event listeners

for _, coin in coins do

  coin:SetAttribute("Enabled", true)

  coin.Touched:Connect(function(otherPart)

    onCoinTouched(otherPart, coin)

  end)

end

```

```

Code explanation

The changes to the original CoinService  script include:

-

Importing the PlayerData  and Leaderboard  modules with the [require()](/docs/en-us/reference/engine/globals/LuaGlobals#require)  function.

-

Declaring COIN_AMOUNT_TO_ADD  as the number of coins to add when a player collects a coin, and COIN_KEY_NAME  as the key name defined in PlayerData .

-

Creating the helper function updatePlayerCoins()  to update the player's coin count and associated leaderboard stat.

-

Replacing the placeholder print()  statement in onCoinTouched()  with a call to updatePlayerCoins() .

## [Playtest](#playtest)[](#playtest)

Select Test  from the dropdown and click Play . Walk into a coin and confirm that the leaderboard appears in the corner and that your coin count increases as you collect more coins.

[Next](/docs/en-us/tutorials/curriculums/core/scripting/create-player-hazards)[Previous](/docs/en-us/tutorials/curriculums/core/scripting/script-game-behavior)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
