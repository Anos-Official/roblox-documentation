<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/scripting/create-player-hazards -->

Maak spelersgevaren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Maak spelersgevaren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Op dit moment kunnen spelers van elk platform vallen zonder gevolgen. Deze sectie begeleidt je bij het creëren van een grote onzichtbare gevaar op dezelfde hoogte als het water in je spel. Wanneer een speler in het gevaar valt, wordt hun gezondheid verlaagd tot nul en respawnen ze aan het begin van het spel.

## [Maak een basis watergevaar](#maak-een-basis-watergevaar)[](#maak-een-basis-watergevaar)

Bouw met Assistent Bouw het Zelf

Maak een basis watergevaar

```

In Workspace > World, maak een nieuwe map genaamd Hazards.

Binnen de Hazards-map, maak een blokdeel genaamd Hazard met Size 825, 1, 576 en CFrame.Position 174, -6.5, 38 zodat het deel het water rond het eiland en de platforms bedekt.

Stel Transparantie in op 1 zodat het deel onzichtbaar is en het daadwerkelijke water als het gevaar verschijnt, schakel CanCollide uit zodat spelers erdoorheen vallen in het water, en schakel Anchored in zodat de fysica het niet verplaatst.

```

## [Detecteer wanneer spelers het gevaar aanraken](#detecteer-wanneer-spelers-het-gevaar-aanraken)[](#detecteer-wanneer-spelers-het-gevaar-aanraken)

Het gevaar doet niets totdat je een script schrijft dat Touched  luistert en de gezondheid van de speler op nul zet.

Bouw met Assistent Bouw het Zelf

Maak HazardService

```

In ServerScriptService, maak een Script genaamd HazardService met de volgende code:

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

Code uitleg

De HazardService  heeft veel overeenkomsten met CoinService . Echter, in plaats van een munt te verzamelen, wordt de gezondheid van de speler op 0  gezet wanneer ze een gevaar aanraken.

Voel je vrij om gevaarobjecten in je spel te wijzigen, toe te voegen of te verwijderen om unieke obstakels te creëren. Zolang ze in de Hazards  map zijn, verbindt de code loop de gebeurtenishandler met al je gevaren.

## [Verbind met de levenscyclus van de speler](#verbind-met-de-levenscyclus-van-de-speler)[](#verbind-met-de-levenscyclus-van-de-speler)

De levenscyclus van de speler vertegenwoordigt gebeurtenissen die plaatsvinden wanneer spelers in je spel interageren, zoals deelnemen, verlaten of respawnen. Je moet handlers verbinden aan deze gebeurtenissen om logica uit te voeren voor elke belangrijke levenscyclus gebeurtenis.

Bouw met Assistent Bouw het Zelf

Voeg levenscyclus handlers toe aan CoinService

```

In ServerScriptService, voeg de volgende code toe aan de onderkant van het bestaande CoinService Script (vervang geen van de bestaande code — voeg dit erna toe):

```lua

local function onPlayerAdded(player)

	-- Reset de munten van de speler naar 0

	updatePlayerCoins(player, function(_)

		return 0

	end)

	player.CharacterAdded:Connect(function(character)

		-- WaitForChild zou de spelerloop stoppen, dus dit moet in een aparte thread worden gedaan

		task.spawn(function()

			-- Wanneer een speler sterft

			character:WaitForChild("Humanoid").Died:Connect(function()

				-- Reset de munten van de speler naar 0

				updatePlayerCoins(player, function(_)

					return 0

				end)

			end)

		end)

	end)

end

-- Initialiseer eventuele spelers die zijn toegevoegd voordat je verbinding maakt met de PlayerAdded gebeurtenis

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

Code uitleg

De code definieert functies om het aantal munten te resetten tijdens de juiste levenscyclus gebeurtenissen:

-

[Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  wordt geactiveerd wanneer een speler het spel betreedt, en stelt het aantal munten in op 0 .

-

[Player.CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  wordt geactiveerd wanneer het karaktermodel van een speler aan de wereld wordt toegevoegd. Dit gebeurt na [PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  en telkens wanneer de speler respawnt.

-

[Humanoid.Died](/docs/nl-nl/reference/engine/classes/Humanoid#Died)  wordt geactiveerd wanneer een speler sterft, en stelt het aantal munten in op 0 . [task.spawn()](/docs/nl-nl/reference/engine/libraries/task#spawn)  creëert een aparte thread voor het afhandelen hiervan, zodat andere aspecten van de levenscyclus van de speler kunnen worden uitgevoerd.

-

[Player.PlayerRemoved](/docs/nl-nl/reference/engine/classes/Player#PlayerRemoved)  wordt geactiveerd wanneer een speler het spel verlaat om de status van de speler op te schonen.

-

Deze code bevat een potentieel probleem waarbij spelers munten kunnen verzamelen voordat de Players.PlayerAdded  gebeurtenis wordt uitgevoerd en vervolgens hun aantal munten op nul wordt gezet. Om dit probleem te verhelpen, overweeg oplossingen zoals codeplanning of het bevriezen van het karakter van de speler totdat de initialisatie is voltooid. Deze oplossingen omvatten echter complexere scripconcepten die buiten de reikwijdte van deze tutorial vallen.

## [Speeltest](#speeltest)[](#speeltest)

Selecteer Test  in de dropdown en klik op Speel . Verzamel een paar munten, spring dan in het water. Je karakter zou moeten sterven en aan het begin respawnen, met hun aantal munten gereset naar 0 .

[Volgende](/docs/nl-nl/tutorials/curriculums/core/scripting/script-an-upgrade-button)[Vorige](/docs/nl-nl/tutorials/curriculums/core/scripting/record-and-display-player-data)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
