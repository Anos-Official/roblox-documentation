<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/scripting/script-an-upgrade-button -->

Script een upgradeknop | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Script een upgradeknop

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Spelers kunnen nu munten verzamelen en deze verliezen wanneer ze sterven, maar de munten doen verder niets, en het grootste deel van de 3D-wereld is ontoegankelijk zonder de mogelijkheid om heel hoog te springen. Dit gedeelte van de tutorial leert je hoe je de logica voor je spel kunt voltooien door een knop op het scherm toe te voegen die munten uitgeeft om de springkracht te verhogen.

## [Maak de upgradeknop](#maak-de-upgradeknop)[](#maak-de-upgradeknop)

2D-interfaces in Roblox bestaan meestal uit een verzameling GUI-componenten binnen een GUI-container. In dit geval heb je alleen een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) -component nodig die Upgrade Jump (5 Munten) zegt binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) -container.

Bouw met Assistent Bouw het Zelf

Stel de upgrade GUI in

```

In ReplicatedStorage, maak een map genaamd Instances.

Binnen de Instances-map, maak een ScreenGui genaamd JumpPurchaseGui met ResetOnSpawn uitgeschakeld.

Binnen JumpPurchaseGui, maak een TextButton genaamd JumpButton met de volgende eigenschappen:

- Text: "Upgrade Jump (5 Munten)"

- TextSize: 25

- AnchorPoint: 1, 1

- Position: {1, 0}, {1, 0}

Ook binnen de Instances-map, maak een RemoteFunction genaamd IncreaseJumpPowerFunction.

Ten slotte, op de StarterPlayer-service, schakel de CharacterUseJumpPower-eigenschap in.

```

## [Definieer springkrachtgegevens](#definieer-springkrachtgegevens)[](#definieer-springkrachtgegevens)

Momenteel wordt alleen het aantal munten opgeslagen voor elke speler in het PlayerData -modulescript. Je moet ook de springkracht op dezelfde manier opslaan en bijwerken. Omdat de functies in PlayerData  niet specifiek zijn voor de gegevens die worden gewijzigd, is het enige wat nodig is om de springkracht van de speler op te slaan, het toevoegen van een Jump -sleutel en het initialiseren van de initiële waarde in defaultPlayerData() .

Bouw met Assistent Bouw het Zelf

Update PlayerData met springkracht

```

In ServerStorage, vervang de bestaande code van het PlayerData ModuleScript door de volgende:

```lua

local PlayerData = {}

PlayerData.COIN_KEY_NAME = "Munten"

PlayerData.JUMP_KEY_NAME = "Spring"

local playerData = {

	--[[

		[userId: string] = {

			["Munten"] = coinAmount: number,

			["Spring"] = jumpPower: number

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

## [Update springkrachtgegevens](#update-springkrachtgegevens)[](#update-springkrachtgegevens)

Nu PlayerData  in staat is om springkracht bij te houden, moet je logica op de server implementeren om de springkracht te upgraden op basis van een verzoek van de client van de speler.

De server en client kunnen communiceren via [RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction) . Remote events blokkeren niet wanneer ze worden geactiveerd en kunnen worden gebruikt voor eenrichtingscommunicatie. Remote functions daarentegen blokkeren totdat ze een antwoord ontvangen, wat zorgt voor tweerichtingscommunicatie.

Voor deze tutorial moet de client weten of de server de springkracht van de speler met succes heeft verhoogd, dus je moet een remote function gebruiken.

Bouw met Assistent Bouw het Zelf

Maak JumpService

```

In ServerScriptService, maak een Script genaamd JumpService met de volgende code:

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

	-- Update de springkracht tabel

	local newJumpPower = PlayerData.updateValue(player, JUMP_KEY_NAME, updateFunction)

	-- Update de springkracht van de speler

	local character = player.Character or player.CharacterAdded:Wait()

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.JumpPower = newJumpPower

		-- Update de spring leaderboard

		Leaderboard.setStat(player, JUMP_KEY_NAME, newJumpPower)

	end

end

local function onPurchaseJumpIncrease(player)

	local coinAmount = PlayerData.getValue(player, COIN_KEY_NAME)

	if coinAmount < JUMP_COIN_COST then

		return false

	end

	-- Verhoog de springkracht van de speler

	updateJumpPower(player, function(oldJumpPower)

		oldJumpPower = oldJumpPower or 0

		return oldJumpPower + JUMP_POWER_INCREMENT

	end)

	-- Update de munttabel

	local newCoinAmount = PlayerData.updateValue(player, COIN_KEY_NAME, function(oldCoinAmount)

		return oldCoinAmount - JUMP_COIN_COST

	end)

	-- Update de munten leaderboard

	Leaderboard.setStat(player, COIN_KEY_NAME, newCoinAmount)

	return true

end

local function onCharacterAdded(player)

	-- Reset de springkracht van de speler wanneer het karakter wordt toegevoegd

	updateJumpPower(player, function(_)

		return 0

	end)

end

-- Initialiseer alle spelers die zijn toegevoegd voordat je verbinding maakt met het PlayerAdded-evenement

for _, player in Players:GetPlayers() do

	onCharacterAdded(player)

end

-- Normale initialisatie van spelers vanuit het PlayerAdded-evenement

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

Code uitleg

De volgende secties beschrijven de code in meer detail.

-

Update de springkrachtgegevens  - updateJumpPower()  werkt de springkracht van de speler en de leaderboard bij om visuele feedback te geven. Deze functie lijkt op de code die spelers schade toebrengt in [Maak spelersgevaren](/docs/nl-nl/tutorials/curriculums/core/scripting/create-player-hazards) . Mits er een [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  model en [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  bestaan voor de speler die wordt geüpgraded, werkt de functie de [JumpPower](/docs/nl-nl/reference/engine/classes/Humanoid#JumpPower)  eigenschap bij naar de nieuwe waarde die door PlayerData  is opgeslagen, en verhoogt deze met 30. Als je wilt dat je spel iets langer meegaat, kun je dit getal verlagen.

-

Valideer serververzoeken  - onPurchaseJumpIncrease()  controleert eerst of de speler daadwerkelijk het aantal munten heeft dat nodig is om de upgrade aan te schaffen. Alle verzoeken  van clients naar de server moeten gevalideerd  worden om te voorkomen dat kwaadwillenden valse verzoeken indienen en je spel exploiteren.

## [Voeg de knop toe aan de speler GUI](#voeg-de-knop-toe-aan-de-speler-gui)[](#voeg-de-knop-toe-aan-de-speler-gui)

Een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  object wordt alleen op het scherm weergegeven als het is gekoppeld aan het [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  object van een speler. Standaard bevat dit de systeem-GUI zoals het chatvenster. Je moet nu een script maken in ReplicatedStorage  om de upgradeknop in de GUI van elke speler te kopiëren en gedrag te implementeren voor wanneer de knop wordt ingedrukt.

Bouw met Assistent Bouw het Zelf

Maak JumpButtonClickHandler

```

In ReplicatedStorage, maak een Script genaamd JumpButtonClickHandler met RunContext ingesteld op Client en de volgende code:

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

		-- purchased zal het foutbericht zijn als success false is

		error(purchased)

	elseif success and not purchased then

		warn("Niet genoeg munten!")

	end

end

jumpButton.Activated:Connect(onButtonClicked)

-- Voeg de JumpPurchaseGui toe aan de GUI van de speler

jumpPurchaseGui.Parent = playerGui

```

```

Code uitleg

De volgende secties beschrijven de code in meer detail.

-

Verkrijg referenties naar de GUI en serverfunctie  - De variabelen IncreaseJumpPowerFunction , jumpPurchaseGui , en jumpButton  bevatten referenties naar de functie en GUI die de functie aanroept die je later nodig hebt.

-

Definieer de gebeurtenis handler  - onButtonClicked()  definieert de logica voor wanneer gebruikers op de upgradeknop klikken. Het gebruikt [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  (beschermde aanroep) om de [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  aan te roepen. Elke client-servercommunicatie zoals deze vereist [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  om fouten of verbindingsproblemen af te handelen.

-

Verbind de handler met de knop  - Het [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  evenement is compatibel op alle platforms, inclusief muis-, touchscreen- of gamepadcontexten. Het wordt geactiveerd wanneer een klik , aanraking  of gamepadknop  wordt losgelaten.

## [Speeltest](#speeltest)[](#speeltest)

Selecteer Test  in de dropdown en klik op Speel . De Upgrade Jump  knop verschijnt in de rechterbenedenhoek.

Probeer op de knop te klikken voordat je munten verzamelt om te controleren of het je geen extra springkracht geeft, klik dan op de knop opnieuw nadat je wat munten hebt verzameld en kijk of de upgrade werkt.

Met de code compleet, probeer de moeilijkheidsgraad aan te passen: voeg munten toe als het tempo te langzaam aanvoelt, of verwijder er een paar en verstop ze op moeilijkere plekken als upgrades te gemakkelijk komen.

[Volgende](/docs/nl-nl/tutorials/curriculums/core/building/create-basic-visual-effects)[Vorige](/docs/nl-nl/tutorials/curriculums/core/scripting/create-player-hazards)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
