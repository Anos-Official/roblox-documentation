<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores -->

Gegevensopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Gegevensopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  stelt je in staat om gegevens op te slaan die tussen sessies moeten blijven bestaan, zoals items in de inventaris van een speler of vaardigheidspunten. Gegevensopslag is consistent per spel, zodat elke plaats in een spel dezelfde gegevens kan openen en wijzigen, inclusief plaatsen op verschillende servers.

Als je gedetailleerde toegangscontrole aan je gegevensopslag wilt toevoegen en deze buiten Studio of Roblox-servers wilt openen, kun je [Open Cloud API's voor gegevensopslag](/docs/nl-nl/cloud/reference/DataStore)  gebruiken.

Om alle gegevensopslag in een spel via de Creator Hub te bekijken en te monitoren, gebruik je de [Gegevensopslagbeheerder](/docs/nl-nl/cloud-services/data-stores/data-stores-manager) .

Voor tijdelijke gegevens die je vaak moet bijwerken of openen, gebruik je [geheugenopslag](/docs/nl-nl/cloud-services/memory-stores) .

## [Studio-toegang inschakelen](#studio-toegang-inschakelen)[](#studio-toegang-inschakelen)

Standaard kunnen spellen die in Studio worden getest geen toegang krijgen tot gegevensopslag, dus je moet ze eerst inschakelen. Toegang tot gegevensopslag in Studio kan gevaarlijk zijn voor live spellen omdat Studio dezelfde gegevensopslag opent als de clienttoepassing. Om te voorkomen dat productiegegevens worden overschreven, schakel deze instelling niet in voor live spellen. Schakel het in voor een aparte testversie van het spel.

Om Studio-toegang in een [gepubliceerd](/docs/nl-nl/production/publishing/publish-games-and-places)  spel in te schakelen:

1.

Open het Bestand  ⟩ Ervaringsinstellingen  venster van Studio.

2.

Navigeer naar Beveiliging .

3.

Schakel de schakelaar Studio-toegang tot API-services inschakelen  in.

4.

Klik op Opslaan .

## [Toegang tot gegevensopslag](#toegang-tot-gegevensopslag)[](#toegang-tot-gegevensopslag)

Om toegang te krijgen tot een gegevensopslag binnen een spel:

1.

Voeg [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  toe aan een server-side [Script](/docs/nl-nl/reference/engine/classes/Script) .

2.

Gebruik de functie [GetDataStore()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetDataStore)  en geef de naam op van de gegevensopslag die je wilt gebruiken. Als de gegevensopslag niet bestaat, maakt Studio er een aan wanneer je je spelgegevens voor de eerste keer opslaat.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

```

De server kan alleen toegang krijgen tot gegevensopslag via [Scripts](/docs/nl-nl/reference/engine/classes/Script) . Pogingen tot client-side toegang in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  veroorzaken een fout.

## [Gegevens maken](#gegevens-maken)[](#gegevens-maken)

Een gegevensopslag is in wezen een woordenboek, vergelijkbaar met een Luau-tabel. Een unieke sleutel  indexeert elke waarde in de gegevensopslag, zoals de unieke [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  van een gebruiker of een benoemde string voor een spelpromotie.

| Gebruikersgegevenssleutel | | Waarde |
| --- | --- |
| 31250608 | | 50 |
| 351675979 | | 20 |
| 505306092 | | 78000 |
| Promotiegegevenssleutel | | Waarde |
| ActiveSpecialEvent | | SummerParty2 |
| ActivePromoCode | | BONUS123 |
| CanAccessPartyPlace | | true |

Om een nieuwe invoer te maken, roep je [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  aan met de sleutelnaam en een waarde.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, errorMessage = pcall(function()

	gameStore:SetAsync("User_1234", 50)

end)

if not success then

	print(errorMessage)

end

```

Functies zoals [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  die toegang krijgen tot de inhoud van een gegevensopslag zijn netwerkoproepen die af en toe kunnen mislukken. Om fouten op te vangen en af te handelen, zorg ervoor dat je deze oproepen in [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  wikkelt.

## [Gegevens bijwerken](#gegevens-bijwerken)[](#gegevens-bijwerken)

Om een opgeslagen waarde in een gegevensopslag te wijzigen, roep je [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  aan met de sleutelnaam van de invoer en een callbackfunctie die definieert hoe je de invoer wilt bijwerken. Deze callback neemt de huidige waarde en retourneert een nieuwe waarde op basis van de logica die je definieert. Als de callback nil  retourneert, wordt de schrijfoperatie geannuleerd en wordt de waarde niet bijgewerkt.

De callbackfunctie die je doorgeeft aan [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  heeft geen  toestemming om te wachten. Het kan geen wachtfuncties zoals [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  bevatten.

```

local DataStoreService = game:GetService("DataStoreService")

local nicknameStore = DataStoreService:GetDataStore("Nicknames")

local function makeNameUpper(currentName)

	local nameUpper = string.upper(currentName)

	return nameUpper

end

local success, updatedName = pcall(function()

	return nicknameStore:UpdateAsync("User_1234", makeNameUpper)

end)

if success then

	print("Hoofdletter Naam:", updatedName)

end

```

### [Instellen versus bijwerken](#instellen-versus-bijwerken)[](#instellen-versus-bijwerken)

Gebruik instellen om snel een specifieke sleutel bij te werken. De functie [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) :

-

Kan gegevensinconsistentie veroorzaken als twee servers proberen dezelfde sleutel tegelijkertijd in te stellen

-

Telt alleen mee voor de schrijflimiet

Gebruik bijwerken om meerdere serverpogingen te verwerken. De functie [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) :

-

Leest de huidige sleutelwaarde van de server die deze het laatst heeft bijgewerkt voordat er wijzigingen worden aangebracht

-

Is langzamer omdat het leest voordat het schrijft

-

Telt mee voor zowel de lees- als schrijflimieten

## [Gegevens lezen](#gegevens-lezen)[](#gegevens-lezen)

Om de waarde van een gegevensopslaginvoer te lezen, roep je [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  aan met de sleutelnaam van de invoer.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, currentGame = pcall(function()

	return gameStore:GetAsync("User_1234")

end)

if success then

	print(currentGame)

end

```

De waarden die je ophaalt met [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  kunnen soms niet synchroon zijn met de backend vanwege het [caching](/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching#caching)  gedrag. Voor meer informatie, zie [Caching uitschakelen](/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching#caching-uitschakelen) .

## [Gegevens verhogen](#gegevens-verhogen)[](#gegevens-verhogen)

Om een geheel getal in een gegevensopslag te verhogen, roep je [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync)  aan met de sleutelnaam van de invoer en een getal voor hoeveel je de waarde wilt wijzigen. [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync)  is een handige functie die je in staat stelt om [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  niet aan te roepen en handmatig het geheel getal te verhogen.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, newGame = pcall(function()

	return gameStore:IncrementAsync("Player_1234", 1)

end)

if success then

	print(newGame)

end

```

## [Gegevens verwijderen](#gegevens-verwijderen)[](#gegevens-verwijderen)

Om een invoer te verwijderen en de waarde die aan de sleutel is gekoppeld terug te geven, roep je [RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync)  aan.

```

local DataStoreService = game:GetService("DataStoreService")

local nicknameStore = DataStoreService:GetDataStore("Nicknames")

local success, removedValue = pcall(function()

	return nicknameStore:RemoveAsync("User_1234")

end)

if success then

	print(removedValue)

end

```

## [Metadata](#metadata)[](#metadata)

Geordende gegevensopslag ondersteunt geen [versiebeheer](/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching#versiebeheer)  en metadata, dus [DataStoreKeyInfo](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo)  is altijd nil  voor sleutels in een [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore) . Als je versiebeheer en metadata wilt ondersteunen, gebruik dan [DataStore](/docs/nl-nl/reference/engine/classes/DataStore) .

Er zijn twee soorten metadata die aan sleutels zijn gekoppeld:

-

Service-gedefinieerd : Standaard alleen-lezen metadata, zoals de meest recente update tijd en creatietijd. Elk object heeft service-gedefinieerde metadata.

-

Door gebruiker gedefinieerd : Aangepaste metadata voor tagging en categorisatie. Gedefinieerd met behulp van het [DataStoreSetOptions](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions)  object en de functie [SetMetadata()](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions#SetMetadata) .

Om metadata te beheren, breid je de functies [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) , [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync) , en [RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync)  uit.

-

[SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  accepteert de optionele derde en vierde argumenten:

-

Een tabel van [UserIds](/docs/nl-nl/reference/engine/classes/Player#UserId) . Dit kan helpen bij het volgen en verwijderen van auteursrechten en intellectuele eigendomsrechten.

-

Een [DataStoreSetOptions](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions)  object, waar je aangepaste metadata kunt definiëren met behulp van de functie [SetMetadata()](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions#SetMetadata) .

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local setOptions = Instance.new("DataStoreSetOptions")

setOptions:SetMetadata({["GameElement"] = "Fire"})

local success, errorMessage = pcall(function()

    gameStore:SetAsync("User_1234", 50, {1234}, setOptions)

end)

if not success then

    print(errorMessage)

end

```

-

[GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync) , en [RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync)  retourneren een tweede waarde in het [DataStoreKeyInfo](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo)  object. Deze tweede waarde bevat zowel service-gedefinieerde eigenschappen als functies om door gebruiker gedefinieerde metadata op te halen.

-

De functie [GetUserIds()](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo#GetUserIds)  haalt de tabel van [UserIds](/docs/nl-nl/reference/engine/classes/Player#UserId)  op die je aan [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  hebt doorgegeven.

-

De functie [GetMetadata()](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo#GetMetadata)  haalt door gebruiker gedefinieerde metadata op die je aan [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  hebt doorgegeven via [SetMetadata()](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions#SetMetadata) .

-

De eigenschap [Version](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo#Version)  haalt de versie van de sleutel op.

-

De eigenschap [CreatedTime](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo#CreatedTime)  haalt de tijd op waarop de sleutel is gemaakt, geformatteerd als het aantal milliseconden sinds de epoch.

-

De eigenschap [UpdatedTime](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo#UpdatedTime)  haalt de laatste tijd op waarop de sleutel is bijgewerkt, geformatteerd als het aantal milliseconden sinds de epoch.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, currentGame, keyInfo = pcall(function()

    return gameStore:GetAsync("User_1234")

end)

if success then

    print(currentGame)

    print(keyInfo.Version)

    print(keyInfo.CreatedTime)

    print(keyInfo.UpdatedTime)

    print(keyInfo:GetUserIds())

    print(keyInfo:GetMetadata())

end

```

-

De callbackfunctie van [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  neemt een extra parameter in het [DataStoreKeyInfo](/docs/nl-nl/reference/engine/classes/DataStoreKeyInfo)  object dat de huidige sleutelstatus beschrijft. Het retourneert de gewijzigde waarde, de sleutels die zijn gekoppeld aan [UserIds](/docs/nl-nl/reference/engine/classes/Player#UserId) , en de metadata van de sleutel.

```

local DataStoreService = game:GetService("DataStoreService")

local nicknameStore = DataStoreService:GetDataStore("Nicknames")

local function makeNameUpper(currentName, keyInfo)

    local nameUpper = string.upper(currentName)

    local userIDs = keyInfo:GetUserIds()

    local metadata = keyInfo:GetMetadata()

    return nameUpper, userIDs, metadata

end

local success, updatedName, keyInfo = pcall(function()

    return nicknameStore:UpdateAsync("User_1234", makeNameUpper)

end)

if success then

    print(updatedName)

    print(keyInfo.Version)

    print(keyInfo.CreatedTime)

    print(keyInfo.UpdatedTime)

    print(keyInfo:GetUserIds())

    print(keyInfo:GetMetadata())

end

```

Bij het aanroepen van [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync) , en [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , moet je altijd metadata-definities bijwerken met een waarde, zelfs wanneer er geen wijzigingen zijn in de huidige waarde. Als je dat niet doet, verlies je de huidige waarde.

Voor limieten bij het definiëren van metadata, zie de [metadata-limieten](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#metadata-limieten) .

## [Geordende gegevensopslag](#geordende-gegevensopslag)[](#geordende-gegevensopslag)

Standaard sorteren gegevensopslag hun inhoud niet. Als je gegevens op een geordende manier wilt ophalen, zoals in persistente leaderboard-statistieken, roep je [GetOrderedDataStore()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetOrderedDataStore)  aan in plaats van [GetDataStore()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetDataStore) .

```

local DataStoreService = game:GetService("DataStoreService")

local characterAgeStore = DataStoreService:GetOrderedDataStore("CharacterAges")

```

Geordende gegevensopslag ondersteunt dezelfde basisfuncties als standaard gegevensopslag, plus de unieke functie [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync) . Dit haalt meerdere gesorteerde sleutels  op op basis van een specifieke sorteervolgorde, paginagrootte en minimum-/maximumwaarden.

Het volgende voorbeeld sorteert karaktergegevens in pagina's met drie invoeren, elk in aflopende volgorde, en doorloopt vervolgens de pagina's en geeft de naam en leeftijd van elk karakter weer.

```

local DataStoreService = game:GetService("DataStoreService")

local characterAgeStore = DataStoreService:GetOrderedDataStore("CharacterAges")

-- Vul geordende gegevensopslag

local characters = {

	Mars = 19,

	Janus = 20,

	Diana = 18,

	Venus = 25,

	Neptune = 62

}

for char, age in characters do

	local success, errorMessage = pcall(function()

		characterAgeStore:SetAsync(char, age)

	end)

	if not success then

		print(errorMessage)

	end

end

-- Sorteert gegevens in aflopende volgorde in pagina's van drie invoeren elk

local success, pages = pcall(function()

	return characterAgeStore:GetSortedAsync(false, 3)

end)

if success then

	while true do

		-- Haalt de huidige (eerste) pagina op

		local entries = pages:GetCurrentPage()

		-- Itereert door alle sleutel-waarde paren op de pagina

		for _, entry in entries do

			print(entry.key .. " : " .. tostring(entry.value))

		end

		-- Controleert of de laatste pagina is bereikt

		if pages.IsFinished then

			break

		else

			print("----------")

			-- Gaat naar de volgende pagina

			pages:AdvanceToNextPageAsync()

		end

	end

end

```

Wanneer je door [GetOrderedDataStore()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetOrderedDataStore)  iterates met [AdvanceToNextPageAsync()](/docs/nl-nl/reference/engine/classes/Pages#AdvanceToNextPageAsync) , is de limiet voor verzoeken dezelfde als de maximale paginagrootte die je hebt ingesteld voor een geordende gegevensopslag. [AdvanceToNextPageAsync()](/docs/nl-nl/reference/engine/classes/Pages#AdvanceToNextPageAsync)  heeft altijd dezelfde limiet als de klasse die het oorspronkelijk vereist.

### [Meerdere invoeren lezen](#meerdere-invoeren-lezen)[](#meerdere-invoeren-lezen)

Om meerdere geordende gegevensopslag  invoeren in één verzoek te lezen, roep je [BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync)  aan met een array van sleutels. Dit is de batch-tegenhanger van het lezen van invoeren één voor één met [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync) .

[BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync)  retourneert een woordenboek dat elke aangevraagde sleutel koppelt aan een tabel met een value -veld. Sleutels die niet bestaan, worden weggelaten uit het woordenboek, dus bevestig dat een sleutel aanwezig is voordat je de waarde leest.

Elke sleutel die je aanvraagt, telt als één leesverzoek, dus een enkele oproep voor N  sleutels telt als N  verzoeken tegen de geordende gegevensopslag [leeslimiet](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#toegangsbeperkingen) .

Het volgende voorbeeld leest drie spelerscores in één verzoek en doorloopt vervolgens de sleutels en geeft elke score weer die bestaat.

```

local DataStoreService = game:GetService("DataStoreService")

local playerScores = DataStoreService:GetOrderedDataStore("PlayerScores")

local keys = {"Player_123", "Player_456", "Player_789"}

local success, results = pcall(function()

	return playerScores:BatchGetAsync(keys)

end)

if success then

	for _, key in keys do

		local entry = results[key]

		if entry then

			print(key .. " : " .. tostring(entry.value))

		else

			print(key .. " heeft geen opgeslagen invoer")

		end

	end

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
