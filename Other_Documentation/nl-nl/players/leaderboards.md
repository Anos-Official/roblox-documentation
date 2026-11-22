<!-- Source: https://create.roblox.com/docs/nl-nl/players/leaderboards -->

Ranglijsten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Ranglijsten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox heeft een ingebouwde ranglijst  in de Spelerslijst. Hier , Vrienden  en Globaal  zijn weergaven van dezelfde lijst: Hier  toont sessierangschikkingen voor spelers op de huidige server, en Vrienden  en Globaal  tonen persistente rangschikkingen vanuit een geordende gegevensopslag die je registreert in Creator Hub.

 ![Ranglijst Scherm](https://prod.docsiteassets.roblox.com/assets/players/leaderboard/Leaderboard-On-Screen.jpg)

## [Weergaven van ranglijsten](#weergaven-van-ranglijsten)[](#weergaven-van-ranglijsten)

De Spelerslijst vergelijkt scores over deze weergaven:

| Weergave | | Rangschikkingen |
| --- | --- |
| Hier | | Sessierangschikkingen voor spelers op de huidige server, vanuit leaderstats . |
| Vrienden | | Persistente rangschikkingen onder de vrienden van een speler die de ervaring hebben gespeeld. |
| Globaal | | Persistente rangschikkingen onder spelers in de ervaring. |

Gebruik [leaderstats](#beheer-sessieranglijsten-met-leaderstats)  om Hier  te vullen. Gebruik [een geordende gegevensopslag](#beheer-persistente-ranglijsten-met-een-geordende-gegevensopslag)  om Vrienden  en Globaal  te vullen.

## [Beheer sessieranglijsten met leaderstats](#beheer-sessieranglijsten-met-leaderstats)[](#beheer-sessieranglijsten-met-leaderstats)

Een leaderstats -map op elke speler stuurt de Hier -weergave. De volgende stappen stellen die map in, voegen statistieken toe, werken ze bij tijdens een sessie, regelen hun volgorde en verbergen de Spelerslijst.

### [Stel leaderstats in](#stel-leaderstats-in)[](#stel-leaderstats-in)

Om de ranglijst in te stellen en spelers toe te voegen wanneer ze de ervaring binnenkomen:

1.

Maak een nieuwe [Script](/docs/nl-nl/reference/engine/classes/Script)  binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  en noem het Leaderboard .

 ![Ranglijst Script Invoegen](https://prod.docsiteassets.roblox.com/assets/players/leaderboard/Leaderboards-Insert-Script.png)

2.

Verbind in het script een functie met het [PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded) -evenement.

```

local Players = game:GetService("Players")

local function leaderboardSetup(player)

end

Players.PlayerAdded:Connect(leaderboardSetup)

```

3.

Maak binnen de verbonden functie een nieuwe [Folder](/docs/nl-nl/reference/engine/classes/Folder) -instantie, noem het leaderstats , en maak het een kind van de speler.

```

local Players = game:GetService("Players")

local function leaderboardSetup(player)

	local leaderstats = Instance.new("Folder")

	leaderstats.Name = "leaderstats"

	leaderstats.Parent = player

end

Players.PlayerAdded:Connect(leaderboardSetup)

```

Het is essentieel dat de map leaderstats  met allemaal kleine letters is genoemd. Roblox voegt de speler niet toe aan de ranglijst als je het op een andere manier noemt.

### [Voeg statistieken toe](#voeg-statistieken-toe)[](#voeg-statistieken-toe)

Ranglijsten gebruiken waarde-type objecten  om spelersstatistieken op te slaan en weer te geven. Dit script toont de goud van een speler met een [IntValue](/docs/nl-nl/reference/engine/classes/IntValue) , een tijdelijke aanduiding voor een geheel getal.

Voeg in de leaderboardSetup() -functie de regels 8 tot en met 11 toe:

```

local Players = game:GetService("Players")

local function leaderboardSetup(player)

	local leaderstats = Instance.new("Folder")

	leaderstats.Name = "leaderstats"

	leaderstats.Parent = player

	local gold = Instance.new("IntValue")

	gold.Name = "Gold"

	gold.Value = 0

	gold.Parent = leaderstats

end

Players.PlayerAdded:Connect(leaderboardSetup)

```

Deze regels bereiken het volgende:

1.

Een [IntValue](/docs/nl-nl/reference/engine/classes/IntValue) -instantie wordt gemaakt.

2.

De [Name](/docs/nl-nl/reference/engine/classes/Instance#Name)  van de instantie wordt ingesteld op "Gold" . Dit is precies hoe de statistiek op de ranglijst zal verschijnen.

 ![Stat naam 'Gold' weergegeven op ranglijst](https://prod.docsiteassets.roblox.com/assets/players/leaderboard/Leaderboard-Stat-Name.png)

3.

De initiële [Value](/docs/nl-nl/reference/engine/classes/IntValue#Value)  van de statistiek wordt ingesteld op 0 . Stel dit in op elke waarde die je wilt, inclusief een waarde die is opgeslagen in een [gegevensopslag](/docs/nl-nl/cloud-services/data-stores)  als je [persistente ranglijsten](#beheer-persistente-ranglijsten-met-een-geordende-gegevensopslag)  implementeert.

Let op dat de waarde van objecten zoals [IntValue](/docs/nl-nl/reference/engine/classes/IntValue) , [NumberValue](/docs/nl-nl/reference/engine/classes/NumberValue) , en [StringValue](/docs/nl-nl/reference/engine/classes/StringValue)  moet worden ingesteld via hun Value -eigenschap, zoals in gold.Value  op regel 10.

4.

De instantie wordt als kind toegevoegd aan de leaderstats -map, waardoor deze aan de ranglijst wordt toegevoegd. Wanneer een speler de ervaring binnenkomt, verschijnt hun naam op de lijst.

 ![Meerdere spelers weergegeven op ranglijst](https://prod.docsiteassets.roblox.com/assets/players/leaderboard/Leaderboards-Multiple-Players.png)

### [Werk statistieken bij](#werk-statistieken-bij)[](#werk-statistieken-bij)

Om de ranglijststatistiek van een speler bij te werken, wijzig je de Value -eigenschap van die statistiek binnen hun leaderstats -map. Je kunt bijvoorbeeld de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  aan elk ophaalobject koppelen om de Gold -statistiek van de speler die het verzamelt te verhogen.

```

local Players = game:GetService("Players")

local goldChunk = script.Parent

local function onPartTouch(otherPart)

	local partParent = otherPart.Parent

	local player = Players:GetPlayerFromCharacter(partParent)

	local leaderstats = player and player:FindFirstChild("leaderstats")

	local goldStat = leaderstats and leaderstats:FindFirstChild("Gold")

	if goldStat then

		-- Vernietig de ophaal

		goldChunk:Destroy()

		-- Werk de ranglijststatistiek van de speler bij

		goldStat.Value += 10

	end

end

goldChunk.Touched:Connect(onPartTouch)

```

### [Orden statistieken](#orden-statistieken)[](#orden-statistieken)

Er zijn drie manieren om de volgorde van statistieken in een ranglijst te regelen:

-

Voeg de statistieken toe in de volgorde waarin je wilt dat ze verschijnen.

-

Voeg een kind [BoolValue](/docs/nl-nl/reference/engine/classes/BoolValue)  genaamd IsPrimary  toe aan de statistiek en stel de waarde in op true  om de statistiek als eerste in de ranglijst te plaatsen.

-

Voeg een kind [NumberValue](/docs/nl-nl/reference/engine/classes/NumberValue)  genaamd Priority  toe aan de statistiek en stel de waarde in op een geheel getal. Hogere prioriteitswaarden verschijnen eerder in de ranglijst. Statistieken zonder prioriteit hebben een standaardprioriteit van 0 .

Dit codevoorbeeld toont hoe je een IsPrimary -waarde aan een statistiek toevoegt:

```

local Players = game:GetService("Players")

local function leaderboardSetup(player)

	local leaderstats = Instance.new("Folder")

	leaderstats.Name = "leaderstats"

	leaderstats.Parent = player

	local gold = Instance.new("IntValue")

	gold.Name = "Gold"

	gold.Value = 0

	gold.Parent = leaderstats

	local isPrimary = Instance.new("BoolValue")

	isPrimary.Name = "IsPrimary"

	isPrimary.Value = true

	isPrimary.Parent = gold

end

Players.PlayerAdded:Connect(leaderboardSetup)

```

IsPrimary  heeft voorrang boven alle Priority -waarden. Als meerdere statistieken IsPrimary -waarden hebben die zijn ingesteld op true , bepalen hun Priority -waarden de volgorde op de ranglijst.

### [Verberg de ranglijst](#verberg-de-ranglijst)[](#verberg-de-ranglijst)

Om de ranglijst te verbergen, bijvoorbeeld op een menu scherm of tijdens een cutscene, roep je [SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  aan vanuit een clientscript.

```

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.PlayerList, false)

```

## [Beheer persistente ranglijsten met een geordende gegevensopslag](#beheer-persistente-ranglijsten-met-een-geordende-gegevensopslag)[](#beheer-persistente-ranglijsten-met-een-geordende-gegevensopslag)

Deze functie is in beta . Functionaliteit en beschikbaarheid kunnen veranderen.

Vrienden  en Globaal  lezen scores uit een [geordende gegevensopslag](/docs/nl-nl/reference/engine/classes/OrderedDataStore)  die je registreert in Creator Hub. De geordende gegevensopslag blijft de bron van waarheid, en Roblox toont de geconfigureerde scores in de Spelerslijst. Dit stelt je in staat om persistente sociale en globale rangschikkingen toe te voegen zonder een aparte ranglijstinterface of rangschikkingsservice te bouwen.

De initiële beta ondersteunt één actieve persistente ranglijst per ervaring. Alleen een geregistreerde, actieve ranglijst verschijnt in de Vrienden  en Globaal  weergaven.

### [Gegevensvereisten](#gegevensvereisten)[](#gegevensvereisten)

Voordat je een ranglijst registreert, bevestig dat de gegevens aan deze vereisten voldoen:

-

Een enkele geordende gegevensopslag ondersteunt de ranglijst.

-

Elke speler heeft één numerieke score in die geordende gegevensopslag.

-

Elke sleutel identificeert één speler op basis van gebruikers-ID, hetzij direct of via een consistent formaat dat de gebruikers-ID bevat.

-

Je ervaring schrijft score-updates naar de geordende gegevensopslag. Het platform leest scores maar schrijft ze niet.

-

Je score-schrijflogica draait op de server.

### [Bereid geordende gegevens voor](#bereid-geordende-gegevens-voor)[](#bereid-geordende-gegevens-voor)

Kies het pad dat overeenkomt met hoe je ervaring momenteel scores opslaat.

#### [Gebruik een bestaande geordende gegevensopslag](#gebruik-een-bestaande-geordende-gegevensopslag)[](#gebruik-een-bestaande-geordende-gegevensopslag)

Als je ervaring al ranglijstscores opslaat in een compatibele geordende gegevensopslag, houd die gegevensopslag dan en registreer deze in Creator Hub. Bevestig dat elke invoer een numerieke score bevat en dat de sleutel consistent één speler identificeert.

Je hoeft de ranglijstgegevens niet opnieuw op te bouwen of deze in een aparte rangschikkingsservice te kopiëren.

#### [Maak een geordende gegevensopslag](#maak-een-geordende-gegevensopslag)[](#maak-een-geordende-gegevensopslag)

Als je nog geen ranglijstgegevens hebt, maak dan een geordende gegevensopslag en voeg deze toe aan je bestaande server-side scoreflow. Schrijf één numerieke score voor elke speler en gebruik de gebruikers-ID van de speler als sleutel of neem de gebruikers-ID op in een consistent sleutelformaat.

```

local DataStoreService = game:GetService("DataStoreService")

local playerScores = DataStoreService:GetOrderedDataStore("PlayerScores")

local function saveScore(player, score)

	local success, errorMessage = pcall(function()

		playerScores:SetAsync(tostring(player.UserId), score)

	end)

	if not success then

		warn(errorMessage)

	end

end

```

Verifieer dat scores aanwezig zijn voordat je de gegevensopslag registreert in Creator Hub. Voor meer informatie over het opslaan en sorteren van persistente waarden, zie [geordende gegevensopslagen](/docs/nl-nl/cloud-services/data-stores#geordende-gegevensopslag) .

#### [Migreer scores van een andere backend](#migreer-scores-van-een-andere-backend)[](#migreer-scores-van-een-andere-backend)

Als een standaard gegevensopslag, externe database of een andere backend je ranglijstgegevens opslaat, migreer dan de scores die je wilt weergeven naar een geordende gegevensopslag. Behoud één numerieke score per speler en gebruik een consistent sleutelformaat dat de speler identificeert.

Na de migratie, werk je scoreflow bij zodat nieuwe scorewijzigingen de geordende gegevensopslag blijven bereiken.

### [Configureer een ranglijst in Creator Hub](#configureer-een-ranglijst-in-creator-hub)[](#configureer-een-ranglijst-in-creator-hub)

Voordat je begint, bevestig dat je ervaring geldige scores naar de geordende gegevensopslag schrijft.

1.

Open [Creator Hub](https://create.roblox.com/dashboard/creations) .

2.

Selecteer de ervaring die de geordende gegevensopslag bezit.

3.

Registreer de geordende gegevensopslag die je ranglijstscores bevat.

4.

Schakel de ranglijst in voor de ervaring.

5.

Bevestig dat de ranglijst actief is.

6.

Test de ranglijst in de ervaring en verifieer dat scores verschijnen zoals verwacht.

Het deactiveren van een ranglijst verbergt deze voor spelers, maar verwijdert de geordende gegevensopslag of scores niet.

![De Ranglijst pagina voor een ervaring in Creator Hub, met een Maak-knop voor het configureren van een ranglijst.](https://prod.docsiteassets.roblox.com/assets/players/leaderboard/Creator-Hub-Persistent-Leaderboard.png) Maak en beheer ranglijstconfiguraties vanaf de Ranglijst pagina in Creator Hub.

### [Test Vrienden en Globaal weergaven](#test-vrienden-en-globaal-weergaven)[](#test-vrienden-en-globaal-weergaven)

Test met spelers die al score-invoeren hebben.

1.

Sluit je aan bij de ervaring als een speler met een opgeslagen score.

2.

Open de ranglijst in de ervaring.

3.

Selecteer Vrienden  en bevestig dat geschikte vrienden verschijnen met de verwachte scores.

4.

Selecteer Globaal  en bevestig dat de speler verschijnt met de verwachte rang en score.

5.

Werk de score van de speler bij via je bestaande server-side workflow.

6.

Bevestig dat de ranglijst de bijgewerkte waarde weergeeft.

Als een speler of score niet verschijnt, verifieer dan de naam van de geordende gegevensopslag, numerieke waarde, speler sleutelformaat en actieve configuratie.

![Een persistente ranglijst in de ervaring die spelersrangschikkingen, namen en scores toont.](https://prod.docsiteassets.roblox.com/assets/players/leaderboard/Persistent-Leaderboard-Friends.png) Verifieer persistente rangschikkingen in de ranglijst in de ervaring.

### [Beheer scores](#beheer-scores)[](#beheer-scores)

Blijf scores bijwerken, corrigeren en modereren via je workflow voor geordende gegevensopslag. Creator Hub beheert welke ranglijst actief is, maar vervangt je score-schrijf- of moderatielogica niet.

Bescherm score-schrijfacties met server-side validatie en controleer verdachte of onmogelijke waarden voordat ze invloed hebben op spelersrangschikkingen.

### [FAQ](#faq)[](#faq)

Moet ik een bestaande gegevensopslag ranglijst opnieuw opbouwen?

Nee. Als de scores al in een compatibele geordende gegevensopslag staan, registreer die gegevensopslag dan in Creator Hub.

Wat als ik een andere ranglijst backend gebruik?

Migreer de scores die je wilt weergeven naar een geordende gegevensopslag en registreer deze vervolgens in Creator Hub.

Wie beheert score-updates en moderatie?

Jij. De geordende gegevensopslag blijft de bron van waarheid, en je server-side workflow blijft scores bijwerken en modereren.

Kan ik meerdere ranglijsten weergeven?

De initiële beta ondersteunt één actieve persistente ranglijst per ervaring.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
