<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/scripting/record-and-display-player-data -->

Spelerdata opnemen en weergeven | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Spelerdata opnemen en weergeven

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Nu je kunt detecteren wanneer een speler een munt heeft verzameld, moet je tellen hoeveel munten spelers hebben verzameld en dat bedrag zichtbaar maken op een leaderboard.

## [Maak een modulescript om het verzamelen van munten op te nemen](#maak-een-modulescript-om-het-verzamelen-van-munten-op-te-nemen)[](#maak-een-modulescript-om-het-verzamelen-van-munten-op-te-nemen)

Om de opslag en het beheer van de muntverzamelingsdata van elke speler te verwerken, moet je een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  object maken om een datastructuur en functies te bevatten die toegang hebben tot de muntverzamelingsdata voor elke speler. Modulescripts zijn herbruikbare code die andere scripts kunnen vereisen. In dit geval vereist de CoinService dit modulescript zodat het de muntverzamelingsdata kan bijwerken wanneer spelers munten aanraken.

Bouw met Assistent Bouw het Zelf

Maak PlayerData

```

In ServerStorage, maak een ModuleScript genaamd PlayerData met de volgende code:

```lua

local PlayerData = {}

PlayerData.COIN_KEY_NAME = "Munten"

local playerData = {

  --[[

    [userId: string] = {

      ["Munten"] = coinAmount: number

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

Code uitleg

Het modulescript definieert een PlayerData  tabel die nul of meer playerData  tabellen bevat, die de muntverzamelingsdata voor een speler vertegenwoordigen. Elk script dat dit modulescript vereist, ontvangt dezelfde kopie van de PlayerData  tabel, waardoor meerdere scripts de muntverzamelingsdata kunnen wijzigen en delen.

#### Declareer de datastructuren

Het modulescript begint met een verklaring van een lege tabel, PlayerData , die aan het einde van het script wordt geretourneerd. Het bevat ook accessor-methoden om waarden in de tabel te krijgen en in te stellen.

De playerData  tabel bevat opmerkingen die de structuur van de tabel beschrijven, wat de code gemakkelijker te begrijpen maakt. In dit geval bevat een playerData  tabel een userId  en een bijbehorend veld genaamd Munten  dat het aantal verzamelde munten voor die speler vertegenwoordigt.

```

local PlayerData = {}

PlayerData.COIN_KEY_NAME = "Munten"

local playerData = {

  --[[

    [userId: string] = {

        ["Munten"] = coinAmount: number

    }

  ]]

}

...

return PlayerData

```

#### Definieer een lokale data-accessor

getData()  is een lokale functie die data voor een specifieke playerData  tabel ophaalt. Als een speler geen munt heeft verzameld, retourneert het een tabel van de defaultPlayerData()  functie om ervoor te zorgen dat elke speler enige data heeft die aan hen is gekoppeld. Een veelvoorkomende conventie is om eenvoudige, publiek toegankelijke functies te maken die logica overdragen aan lokaal gedefinieerde functies die het zware werk doen.

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

#### Definieer publieke data-accessors

getValue()  en updateValue()  zijn publiek toegankelijke functies die andere scripts die dit modulescript vereisen kunnen aanroepen. In ons geval gebruikt de CoinService  deze functies om de muntverzamelingsdata van een speler bij te werken telkens wanneer die speler een munt aanraakt.

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

## [Implementeer een leaderboard](#implementeer-een-leaderboard)[](#implementeer-een-leaderboard)

Je kunt de muntverzamelingsdata visueel weergeven met een leaderboard op het scherm. Roblox bevat een ingebouwd systeem dat automatisch een leaderboard genereert met een standaard UI.

Bouw met Assistent Bouw het Zelf

Maak Leaderboard

```

In ServerStorage, maak een ModuleScript genaamd Leaderboard met de volgende code:

```lua

local Leaderboard = {}

-- Een nieuw leaderboard maken

local function setupLeaderboard(player)

  local leaderstats = Instance.new("Folder")

  -- 'leaderstats' is een gereserveerde naam die Roblox herkent voor het maken van een leaderboard

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  return leaderstats

end

-- Een nieuwe leaderboard statwaarde maken

local function setupStat(leaderstats, statName)

  local stat = Instance.new("IntValue")

  stat.Name = statName

  stat.Value = 0

  stat.Parent = leaderstats

  return stat

end

-- De statwaarde van een speler bijwerken

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

Code uitleg

De volgende secties beschrijven hoe het leaderboard in meer detail werkt.

#### Maak een leaderboard

De setupLeaderboard()  functie maakt een nieuwe mapinstantie genaamd leaderstats  en stelt deze in als een kind van de opgegeven speler. Roblox herkent automatisch een map genaamd leaderstats  als een container van statistieken en maakt een UI-element om de statistieken weer te geven. Het vereist dat de waarden in leaderstats  worden opgeslagen als "waarde" objecten (zoals [StringValue](/docs/nl-nl/reference/engine/classes/StringValue) , [IntValue](/docs/nl-nl/reference/engine/classes/IntValue)  of [NumberValue](/docs/nl-nl/reference/engine/classes/NumberValue) ).

```

-- Een nieuw leaderboard maken

local function setupLeaderboard(player)

  local leaderstats = Instance.new("Folder")

  -- 'leaderstats' is een gereserveerde naam die Roblox herkent voor het maken van een leaderboard

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  return leaderstats

end

-- Een nieuwe leaderboard statwaarde maken

local function setupStat(leaderstats, statName)

  local stat = Instance.new("IntValue")

  stat.Name = statName

  stat.Value = 0

  stat.Parent = leaderstats

  return stat

end

```

#### Update spelerstatistieken

setStat()  is de enige publieke functie in de Leaderboard  module. Het maakt statwaarden voor een opgegeven speler of het leaderboard zelf als het nog niet bestaat.

[FindFirstChild()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChild)  neemt de naam van een object en retourneert het object als het bestaat, of nil  als dat niet het geval is. Het is een veelgebruikte, veilige methode om te achterhalen of een object bestaat voordat je het gebruikt.

```

-- De statwaarde van een speler bijwerken

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

## [Integreer de modulescripts](#integreer-de-modulescripts)[](#integreer-de-modulescripts)

Met beide modules op hun plaats, vereis ze in het CoinService  script om de speler muntdata te beheren en weer te geven.

Bouw met Assistent Bouw het Zelf

Update CoinService

```

In ServerScriptService, vervang de bestaande CoinService Script code door de volgende:

```lua

-- Diensten en variabelen initialiseren

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

  -- De muntentabel bijwerken

  local newCoinAmount = PlayerData.updateValue(player, COIN_KEY_NAME, updateFunction)

  -- De munt leaderboard bijwerken

  Leaderboard.setStat(player, COIN_KEY_NAME, newCoinAmount)

end

-- De event handler definiëren

local function onCoinTouched(otherPart, coin)

  if coin:GetAttribute("Enabled") then

    local character = otherPart.Parent

    local player = Players:GetPlayerFromCharacter(character)

    if player then

      -- Speler heeft een munt aangeraakt

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

-- Eventlisteners instellen

for _, coin in coins do

  coin:SetAttribute("Enabled", true)

  coin.Touched:Connect(function(otherPart)

    onCoinTouched(otherPart, coin)

  end)

end

```

```

Code uitleg

De wijzigingen in het oorspronkelijke CoinService  script omvatten:

-

Het importeren van de PlayerData  en Leaderboard  modules met de [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  functie.

-

Het declareren van COIN_AMOUNT_TO_ADD  als het aantal munten dat moet worden toegevoegd wanneer een speler een munt verzamelt, en COIN_KEY_NAME  als de sleutel naam gedefinieerd in PlayerData .

-

Het creëren van de hulpfunctie updatePlayerCoins()  om het aantal munten van de speler en de bijbehorende leaderboardstat bij te werken.

-

Het vervangen van de tijdelijke print()  verklaring in onCoinTouched()  door een aanroep naar updatePlayerCoins() .

## [Speeltest](#speeltest)[](#speeltest)

Selecteer Test  in de dropdown en klik op Speel . Loop naar een munt en bevestig dat het leaderboard in de hoek verschijnt en dat je muntentelling toeneemt naarmate je meer munten verzamelt.

[Volgende](/docs/nl-nl/tutorials/curriculums/core/scripting/create-player-hazards)[Vorige](/docs/nl-nl/tutorials/curriculums/core/scripting/script-game-behavior)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
