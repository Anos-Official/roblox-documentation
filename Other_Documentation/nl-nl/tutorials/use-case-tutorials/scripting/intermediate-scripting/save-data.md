<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/save-data -->

Sla spelerdata op met standaard datastores | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Gegevensopslag

# Sla spelerdata op met standaard datastores

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Datastores  zijn een service die je kunt gebruiken om persistente spelerdata  op te slaan en te laden over verschillende spelersessies. Ze slaan belangrijke informatie op, zoals de voortgang of inventaris van een speler, en stellen je in staat om deze op te halen voor de speler de volgende keer dat ze je spel betreden. Zonder datastores zou een speler al zijn voortgang verliezen elke keer dat ze het spel verlaten.

Er zijn twee soorten datastores: standaard en geordend. Deze tutorial gebruikt standaard datastores , die gegevens opslaan zoals nummers, strings en tabellen die niet gerangschikt of gesorteerd hoeven te worden.

Met de [Gold Rush datastore tutorial - Start](https://www.roblox.com/games/116344152904993/Gold-Rush-save-data-tutorial-Start)  .rbxl -bestand als startpunt en het [Gold Rush datastore tutorial - Complete](https://www.roblox.com/games/114290473705422/Gold-Rush-save-data-tutorial-Complete)  .rbxl -bestand als referentie, biedt deze tutorial je de basis die je nodig hebt om de voortgang van spelers op te slaan en meer consistente spellen te creëren, inclusief richtlijnen over:

-

Het opslaan en laden van de hoeveelheid goud die een speler heeft verzameld.

-

Het bijwerken van de UI om de goudinventaris van de speler weer te geven.

-

Het automatisch opslaan van de goudinventaris van de speler elke 30 seconden.

-

Het opslaan van de positie van de speler wanneer ze het spel verlaten.

-

Het herstellen van de positie van de speler wanneer ze het spel opnieuw betreden.

Het [Gold Rush datastore tutorial - Start](https://www.roblox.com/games/116344152904993/Gold-Rush-save-data-tutorial-Start)  startbestand bevat al code die de speler in staat stelt om goud te verzamelen en de UI bijwerkt met hun goudscore, maar deze gegevens blijven niet bestaan over sessies omdat het bestand geen datastores bevat. Zonder datastores worden de score en positie van de speler gereset wanneer ze het spel verlaten.

Aan het einde van deze tutorial zou je twee scripts met datastores onder [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  moeten hebben:

1.

Een bijgewerkt [GoldManager](#goldmanager)  script dat de goud van de speler bijhoudt, laadt en automatisch opslaat.

2.

Een bijgewerkt [PositionManager](#positionmanager)  script dat de positie van de speler opslaat wanneer ze het spel verlaten en hun positie herstelt wanneer ze terugkomen in het spel.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/data-storage/DataStoreTutorial.png)

## [Studio-toegang tot API-services inschakelen](#studio-toegang-tot-api-services-inschakelen)[](#studio-toegang-tot-api-services-inschakelen)

Datastores worden niet lokaal op je apparaat opgeslagen, dus je spel is afhankelijk van server-naar-server communicatie met de backend van Roblox om ze te gebruiken. Standaard beperkt Studio deze communicatie om misbruik of onbedoeld gebruik te voorkomen. Toegang tot API-services in Studio is uitgeschakeld totdat je dit expliciet inschakelt om ervoor te zorgen dat alleen vertrouwde spellen kunnen lezen van en schrijven naar de backendservers van Roblox.

Om Studio-toegang tot API-services in te schakelen zodat je datastores kunt gebruiken:

1.

Open het [Gold Rush datastore tutorial - Start](https://www.roblox.com/games/116344152904993/Gold-Rush-save-data-tutorial-Start)  .rbxl -bestand in Studio en maak een lokale kopie.

2.

[Publiceer je spel](/docs/nl-nl/production/publishing/publish-games-and-places#publiceer-games) .

3.

Ga terug naar Studio, ga naar Bestand  ⟩ Ervaringsinstellingen  ⟩ Beveiliging .

4.

Zet Studio-toegang tot API-services inschakelen  aan.

5.

Sla je wijzigingen op.

## [Maak een standaard datastore](#maak-een-standaard-datastore)[](#maak-een-standaard-datastore)

Bij het maken van een datastore moet je altijd de DataStoreService  aanroepen vanuit een server-side [Script](/docs/nl-nl/reference/engine/classes/Script) . Dit is belangrijk omdat:

-

Roblox alle toegang tot datastores vanuit de client blokkeert, zodat alleen de server toestemming heeft om persistente spelerdata te benaderen en te wijzigen.

-

Server-side scripts draaien in een gecentraliseerde omgeving, waardoor ervoor wordt gezorgd dat de gegevens die worden gelezen en geschreven naar je datastore nauwkeurig en geldig zijn.

-

Aangezien client-side scripts op het apparaat van de speler draaien, zou elke speler mogelijk het spel kunnen misbruiken en gegevens van andere spelers kunnen stelen of overschrijven als de client toegang had tot je datastores.

Je moet je datastore ook een unieke naam geven om je gegevens georganiseerd te houden en te voorkomen dat ze overlappen of conflicteren in verschillende datastores. In deze tutorial wordt de datastore die de goudinventaris van de speler opslaat en bewaart PlayerGold  genoemd.

Om de PlayerGold datastore te maken:

1.

Open het bestaande GoldManager  script onder ServerScriptService .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/intro-to-saving-data/ServerScriptService-GoldManager.png)

2.

Initialiseer de DataStoreService  boven de andere services aan de bovenkant van het script en roep [GetDataStore](/docs/nl-nl/reference/engine/classes/DataStoreService#GetDataStore)  aan met de string "PlayerGold" .

```

local DataStoreService = game:GetService("DataStoreService")

local goldStore = DataStoreService:GetDataStore("PlayerGold")

```

## [Sla spelerdata op en laad deze](#sla-spelerdata-op-en-laad-deze)[](#sla-spelerdata-op-en-laad-deze)

Datastores bestaan uit sleutels, die gegevens identificeren, en waarden, die gegevens opslaan.

|  | | Sleutel | | Waarde |
| --- | --- |
| Beschrijving | | Een sleutel is een unieke identificator die je kunt gebruiken om een specifiek stuk gegevens te benaderen.
Sleutels stellen je in staat om je gegevens te organiseren, zodat je ze gemakkelijk kunt beheren en debuggen. | | Een waarde is de daadwerkelijke data die je wilt opslaan of laden, zoals de inventaris van een speler of hun instellingen.
Waarden stellen je in staat om voortgang tussen sessies op te slaan, evenals spelerdata op te halen de volgende keer dat ze je spel betreden. |
| Toegestane formaten | | Kunnen alleen strings zijn. | | Kunnen nummers, strings, booleans of tabellen zijn. |
| Voorbeelden | | "Player_A" , "TopScore" , "GameSetting" | | 100 , "Level_5" , true , {gold = 100, level = 5} |

In deze tutorial is de sleutel de userId  van de speler en de waarde is de hoeveelheid goud die ze hebben verzameld. Om deze sleutel en waarde te gebruiken om spelerdata op te slaan en te laden:

1.

Voeg in het GoldManager  script een hulpfunctie genaamd saveGold  toe om het goud van de speler op te slaan in de PlayerGold datastore.

```

local function saveGold(userId, value)

   local success, err = pcall(function()

      -- `userId` is de unieke ID van de speler

      -- `value` is de hoeveelheid goud die voor die speler moet worden opgeslagen

      goldStore:SetAsync(userId, value)

   end)

end

```

2.

OPTIONEEL

 Voeg een waarschuwing toe aan saveGold  die de ID van de speler en een foutmelding afdrukt. Hoewel dit niet verplicht is, is deze stap een goede praktijk voor gemakkelijker debuggen in het geval dat je functie faalt.

```

local function saveGold(userId, value)

   local success, err = pcall(function()

      -- `userId` is de unieke ID van de speler

      -- `value` is de hoeveelheid goud die voor die speler moet worden opgeslagen

      goldStore:SetAsync(userId, value)

   end)

   if not success then

      warn("[OPSLAAN FOUT] Kon goud niet opslaan voor", userId, ":", err)

   end

end

```

3.

Wijzig het onPlayerAdded  evenement om het goud van de speler te laden wanneer ze voor het eerst het spel betreden. De bijgewerkte onPlayerAdded  functie:

-

Probeert de inhoud in de PlayerGold datastore te laden. Het retourneert ofwel het opgeslagen goud van de speler of een waarde van 0 als de speler geen goud heeft of het spel nog niet eerder heeft gespeeld.

-

Biedt je een debuglog om je te helpen je code gemakkelijker te debuggen. Deze debuglog bevat het opgeslagen goud van de binnenkomende speler, of een foutmelding als onPlayerAdded  niet in staat is om toegang te krijgen tot de datastore.

-

Werkt de UI bij om het opgeslagen goud van de speler op hun scherm weer te geven.

```

local function onPlayerAdded(player)

   local userId = player.UserId

   local success, storedGold = pcall(function()

      return goldStore:GetAsync(userId)

   end)

   if success then

      local currentGold = storedGold or 0

      playerGold[userId] = currentGold

      uiEvent:FireClient(player, {

         gold = currentGold,

         doTween = false,

         showAlert = not success

      })

   else

      uiEvent:FireClient(player, { showAlert = true })

      warn("Kon goud niet laden voor", player.Name)

   end

end

```

4.

Wijzig het onPlayerRemoving  evenement om de saveGold  functie die je eerder hebt gemaakt aan te roepen en het goud van de speler op te slaan wanneer ze het spel verlaten.

```

local function onPlayerRemoving(player)

   local userId = player.UserId

   if playerGold[userId] then

      saveGold(userId, playerGold[userId])

   end

end

```

## [Sla spelerdata automatisch op](#sla-spelerdata-automatisch-op)[](#sla-spelerdata-automatisch-op)

Het automatisch opslaan van de gegevens van een speler is een goede praktijk omdat het de speler beschermt tegen het verliezen van hun gegevens. Als je alleen de gegevens van de speler opslaat wanneer ze het spel verlaten met onPlayerRemoving , kun je hun laatste voortgang verliezen als ze onverwacht de verbinding met de server verbreken.

Zorg ervoor dat je niet te vaak automatisch opslaat om throttling-fouten en verzoeklimieten te voorkomen. Een goede autosave-interval is ergens tussen de 30 en 120 seconden, afhankelijk van hoe vaak spelers waardevolle voortgang in je spel behalen.

Om de gegevens van de speler automatisch op te slaan:

1.

Maak een nieuwe constante om te bepalen hoe vaak je wilt dat je spel automatisch de gegevens van de speler opslaat. Een constante is een variabele waarvan de waarde niet verandert terwijl het spel draait. Je kunt deze constante gebruiken om naar de autosave-interval te verwijzen in je script en om de frequentie van het automatisch opslaan gemakkelijk aan te passen.

```

-- Dit getal is in seconden

local AUTOSAVE_INTERVAL = 30

```

2.

Voeg een autosave coroutine toe aan de bestaande onPlayerAdded  functie om een achtergrondlus te creëren die draait terwijl de speler in het spel is. Een coroutine is een functie die asynchroon draait; het kan op bepaalde punten pauzeren, hervatten waar het was gebleven en parallel met andere delen van je script draaien zonder deze te blokkeren.

In dit script wacht de autosave coroutine achtergrondlus op het aantal seconden in je AUTOSAVE_INTERVAL  constante, en roept vervolgens de saveGold  functie aan die je eerder hebt gemaakt.

```

coroutine.wrap(function()

   while player.Parent do

      task.wait(AUTOSAVE_INTERVAL)

      if playerGold[userId] then

         print("[AUTOSAVE] Opslaan", playerGold[userId], "goud voor", player.Name)

         saveGold(userId, playerGold[userId])

      end

   end

end)()

```

## [Sla en laad de positie van de speler](#sla-en-laad-de-positie-van-de-speler)[](#sla-en-laad-de-positie-van-de-speler)

Om de positie van een speler op te slaan, moet je werken met hun [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  in plaats van het [Player](/docs/nl-nl/reference/engine/classes/Player)  object zelf. De Character  van een speler vertegenwoordigt hun fysieke model in de 3D-wereld en heeft de coördinaten voor hun huidige positie en oriëntatie, terwijl het Player  object alleen het gebruikersaccount vertegenwoordigt.

Omdat datastores alleen basisdatatypes zoals nummers, strings en tabellen kunnen opslaan, kun je geen complexe objecten zoals [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  of [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  waarden direct opslaan. Om de positie van een speler op te slaan, moet je deze splitsen in drie afzonderlijke getallen (de X-, Y- en Z-coördinaten) en ze afzonderlijk opslaan. Wanneer je de positie later laadt, kun je de Vector3  opnieuw opbouwen met de opgeslagen coördinaten.

Om de positie van het karakter op te slaan en te laden:

1.

Open het bestaande PositionManager  script onder ServerScriptService .

2.

Initialiseer de DataStoreService  aan de bovenkant van het script en roep GetDataStore  aan met de string "PlayerPosition" .

```

local DataStoreService = game:GetService("DataStoreService")

local positionStore = DataStoreService:GetDataStore("PlayerPosition")

```

3.

Voeg een hulpfunctie genaamd savePosition  toe die de userId  van een speler en een Vector3  positie accepteert. Aangezien je Vector3  waarden niet direct kunt opslaan, converteer je de positie naar een tabel van X, Y, Z  getallen.

```

local function savePosition(player, position)

   local userId = player.UserId

   local success, err = pcall(function()

      positionStore:SetAsync(userId, {position.X, position.Y, position.Z})

   end)

end

```

4.

OPTIONEEL

 Voeg een waarschuwing toe aan savePosition  die een foutmelding en de naam van de speler afdrukt voor wie je de positie niet kon opslaan. Hoewel dit niet verplicht is, is deze stap een goede praktijk voor gemakkelijker debuggen in het geval dat je functie faalt.

```

local function savePosition(player, position)

   local userId = player.UserId

   local success, err = pcall(function()

      positionStore:SetAsync(userId, {position.X, position.Y, position.Z})

   end)

   if not success then

      warn("Kon positie niet opslaan voor", player.Name, ":", err)

   end

end

```

5.

Voeg een andere hulpfunctie genaamd loadPosition  toe om de opgeslagen coördinaten voor een speler in de PlayerPosition datastore te laden. Gebruik [PivotTo](/docs/nl-nl/reference/engine/classes/PVInstance#PivotTo)  om de positie van het karakter in de wereld te herstellen. Aangezien de opgeslagen positie van de speler als een tabel wordt geretourneerd, moet je een Vector3  opnieuw opbouwen en deze vervolgens omzetten naar een CFrame  om het karakter te verplaatsen.

```

local function loadPosition(userId, character)

   local userId = player.UserId

   local success, savedCoords = pcall(function()

      return positionStore:GetAsync(userId)

   end)

   if success and savedCoords then

      local pos = Vector3.new(savedCoords[1], savedCoords[2], savedCoords[3])

      print("Herstelde positie voor", player.Name)

      character:PivotTo(CFrame.new(pos))

   elseif not success then

      warn("Kon positie niet laden voor", player.Name)

   end

end

```

6.

Wijzig het onPlayerAdded  evenement om de positie-logica in te stellen voor elke speler die je spel betreedt. Binnen de bijgewerkte onPlayerAdded  functie:

-

CharacterAdded  roept loadPosition  aan om de laatste bekende locatie van het karakter te herstellen wanneer het karakter van een speler spawnt.

-

CharacterRemoving  roept savePosition  aan om de huidige positie van het karakter van de speler op te slaan als ze uit het spel worden verwijderd.

-

[GetPivot](/docs/nl-nl/reference/engine/classes/PVInstance#GetPivot)  krijgt de exacte locatie van het karakter in de wereld op het moment dat ze worden verwijderd.

```

local function onPlayerAdded(player)

   local userId = player.UserId

   player.CharacterAdded:Connect(function(character)

      loadPosition(player, character)

   end)

   player.CharacterRemoving:Connect(function(character)

      local pos = character:GetPivot().Position

      savePosition(player, pos)

   end)

end

Player.PlayerAdded:Connect(onPlayerAdded)

```

## [Eindcode](#eindcode)[](#eindcode)

Zie de volgende codefragmenten voor de complete GoldManager  en PositionManager  scripts. Je kunt ze rechtstreeks plakken en uitvoeren in het [Gold Rush save data tutorial - Start](https://www.roblox.com/games/5268331031/Gold-Rush)  .rbxl -bestand in Studio.

### [GoldManager](#goldmanager)[](#goldmanager)

```

-- Verkrijg services

-- Verkrijg services

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local CollectionService = game:GetService("CollectionService")

local DataStoreService = game:GetService("DataStoreService")

-- Remote event om de UI bij te werken

local uiEvent = ReplicatedStorage:WaitForChild("UIEvent")

-- Data store voor het opslaan van de goudstukken van de speler

local goldStore = DataStoreService:GetDataStore("PlayerGold")

-- Tabel om de goudstukken van de speler voor een enkele sessie op te slaan

local playerGold = {}

-- Constanten

local GOLD_VALUE = 10           -- Hoeveel elk goudstuk waard is

local GOLD_REGEN_DELAY = 2      -- De vertraging voordat een stuk opnieuw verschijnt (in seconden)

local AUTOSAVE_INTERVAL = 30    -- Hoe vaak de goudstukken van de speler worden opgeslagen (in seconden)

-- Functie om de speler een goudstuk te laten verzamelen

local function processGoldTouch(chunk, player)

	-- Verberg het stuk wanneer de speler het verzamelt

	chunk.Parent = nil

	-- Voeg het stuk toe aan de goudscore van de speler voor deze sessie

	local userId = player.UserId

	playerGold[userId] = (playerGold[userId] or 0) + GOLD_VALUE

	print(player.Name, "heeft nu", playerGold[userId], "goud")

	-- Werk de UI bij om de nieuwe goudscore voor deze sessie weer te geven

	uiEvent:FireClient(player, {

		gold = playerGold[userId],

		doTween = true,

		showAlert = false

	})

	-- Wacht even en laat dan het goudstuk dat net is verzameld opnieuw verschijnen

	task.delay(GOLD_REGEN_DELAY, function()

		chunk.Parent = workspace.GoldChunks

	end)

end

-- Loop door alle delen die zijn gemarkeerd met "Gold" en verbind ze met aanrakingdetectie

for _, chunk in ipairs(CollectionService:GetTagged("Gold")) do

	chunk.Touched:Connect(function(otherPart)

		local player = Players:GetPlayerFromCharacter(otherPart.Parent)

		if player then

			processGoldTouch(chunk, player)

		end

	end)

end

-- Functie om het goud van de speler op te slaan in de datastore

local function saveGold(player, value)

	local userId = player.UserId

	local success, err = pcall(function()

		goldStore:SetAsync(userId, value)

	end)

	if not success then

		warn("Kon goud niet opslaan voor", player.Name, ":", err)

	end

end

-- Functie om de speler het spel te laten betreden

local function onPlayerAdded(player)

	local userId = player.UserId

	print(player.Name, "is het spel binnengekomen")

	-- Probeer het goud van de speler uit de datastore te laden

	local success, storedGold = pcall(function()

		return goldStore:GetAsync(userId)

	end)

	if success then

		-- Stel de huidige goudscore voor de sessie in met de waarde uit de datastore voor de speler

		local currentGold = storedGold or 0

		playerGold[userId] = currentGold

		-- Werk de UI bij met de waarde uit de datastore voor de speler

		uiEvent:FireClient(player, {

			gold = currentGold,

			doTween = false,

			showAlert =  false

		})

		print("Gelaagd", currentGold, "goud voor", player.Name)

	else

		-- Meld de speler dat hun goud niet kon worden geladen

		uiEvent:FireClient(player, { showAlert = true })

		warn("Kon goud niet laden voor", player.Name)

	end

	-- Start de autosave coroutine om het goud van de speler elke 30 seconden op te slaan

	coroutine.wrap(function()

		while player.Parent do

			task.wait(AUTOSAVE_INTERVAL)

			if playerGold[userId] then

				saveGold(player, playerGold[userId])

				print("Autosaving", playerGold[userId], "goud voor", player.Name)

			end

		end

	end)()

end

-- Functie om de speler het spel te laten verlaten

local function onPlayerRemoving(player)

	local userId = player.UserId

	print(player.Name, "heeft het spel verlaten")

	-- Controleer of het goud van de speler werd bijgehouden

	if playerGold[userId] then

		-- Sla het goud van de speler op in de datastore voordat ze vertrekken

		saveGold(player, playerGold[userId])

	end

end

-- Verbind de evenementen voor het binnenkomen en verlaten van spelers

Players.PlayerAdded:Connect(onPlayerAdded)

Players.PlayerRemoving:Connect(onPlayerRemoving)

```

### [PositionManager](#positionmanager)[](#positionmanager)

```

-- Verkrijg services

local Players = game:GetService("Players")

local DataStoreService = game:GetService("DataStoreService")

-- Data store voor het opslaan van de positie van de speler

local positionStore = DataStoreService:GetDataStore("PlayerPosition")

-- Functie om de positie van de speler op te slaan als een tabel van {X, Y, Z}

local function savePosition(player, position)

	local userId = player.UserId

	local success, err = pcall(function()

		positionStore:SetAsync(userId, {position.X, position.Y, position.Z})

	end)

	if not success then

		warn("Kon positie niet opslaan voor", player.Name, ":", err)

	end

end

-- Functie om de laatst opgeslagen positie van de speler te laden en hun karakter te verplaatsen

local function loadPosition(player, character)

	local userId = player.UserId

	local success, savedCoords = pcall(function()

		return positionStore:GetAsync(userId)

	end)

	if success and savedCoords then

		local pos = Vector3.new(savedCoords[1], savedCoords[2], savedCoords[3])

		print("Herstelde positie voor", player.Name)

		character:PivotTo(CFrame.new(pos))

	elseif not success then

		warn("Kon positie niet laden voor", player.Name)

	end

end

-- Functie om de speler het spel te laten betreden

local function onPlayerAdded(player)

	local userId = player.UserId

	-- Probeer de positie van de speler te laden wanneer hun karakter spawnt

	player.CharacterAdded:Connect(function(character)

		loadPosition(player, character)

	end)

	-- Sla de positie van de speler op wanneer hun karakter wordt verwijderd

	player.CharacterRemoving:Connect(function(character)

		local pos = character:GetPivot().Position

		savePosition(player, pos)

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
