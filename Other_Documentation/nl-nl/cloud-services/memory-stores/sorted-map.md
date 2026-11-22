<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores/sorted-map -->

Geordende kaart van geheugenopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Geordende kaart van geheugenopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De geordende kaart  gegevensstructuur van [geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)  stelt je in staat om frequente in-memory gegevens op te slaan als sleutel-waarde paren met een optionele sorteersleutel en een specifieke volgorde te behouden op basis van de sorteersleutels en sleutels. In tegenstelling tot wachtrijen bepaalt de volgorde waarin sleutels een kaart binnenkomen niet de volgorde van verwerking, waardoor geordende kaarten nuttig zijn voor het sorteren van gegevensorganisatie voor het implementeren van in-game entiteiten voor betrokkenheid, zoals ranglijsten en cross-server veilingen.

## [Limieten](#limieten)[](#limieten)

Naast de [limieten voor de grootte van gegevensstructuren](/docs/nl-nl/cloud-services/memory-stores#limieten-voor-de-grootte-van-gegevensstructuren) , hebben geordende kaarten een limiet voor de sleutelgrootte van 128 tekens, een limiet voor de waarde-grootte van 32 KB en een limiet voor de sorteersleutelgrootte van 128 tekens.

Als je gegevens moet opslaan die deze limiet voor je spel overschrijden, kun je de sharding-techniek toepassen om ze te splitsen en te verdelen via sleutelprefix  in meerdere gegevensstructuren. Sharding van geheugenopslag kan ook helpen om de schaalbaarheid van je systeem te verbeteren.

## [Verkrijg een geordende kaart](#verkrijg-een-geordende-kaart)[](#verkrijg-een-geordende-kaart)

Om een geordende kaart te verkrijgen, roep je [MemoryStoreService:GetSortedMap()](/docs/nl-nl/reference/engine/classes/MemoryStoreService#GetSortedMap)  aan met een naam  die je wilt definiëren voor de kaart. De naam is globaal binnen het spel, zodat je dezelfde geordende kaart op elk script kunt openen met de naam.

Een Geordende Kaart Verkrijgen

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

```

Nadat je een geordende kaart hebt verkregen, kun je een van de volgende functies aanroepen:

| Functie | | Actie |
| --- | --- |
| [MemoryStoreSortedMap:SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#SetAsync) | | [Voeg](#voeg-gegevens-toe-of-overschrijf-deze)  een nieuwe sleutel toe of overschrijf de waarde en/of sorteersleutel als de sleutel al bestaat. |
| [MemoryStoreSortedMap:GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetAsync) | | [Lees](#verkrijg-gegevens)  een specifieke sleutel. |
| [MemoryStoreSortedMap:GetRangeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetRangeAsync) | | [Lees](#verkrijg-gegevens)  alle bestaande sleutels of een specifieke reeks daarvan. |
| [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync) | | [Werk bij](#werk-gegevens-bij)  de waarde van een sleutel en/of sorteersleutel na het ophalen ervan uit een geordende kaart. |
| [MemoryStoreSortedMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#RemoveAsync) | | [Verwijder](#verwijder-gegevens)  een sleutel uit de geordende kaart. |
| [MemoryStoreSortedMap:GetSizeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetSizeAsync) | | [Krijg](#verkrijg-grootte)  het aantal items in de geordende kaart. |

Alle functies die toegang hebben tot gegevensstructuren in geheugenopslag zijn asynchrone netwerkoproepen die af en toe kunnen mislukken. Je moet deze oproepen omhullen in [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  om fouten op te vangen en af te handelen, zoals het codevoorbeeld in elke sectie doet.

## [Voeg gegevens toe of overschrijf deze](#voeg-gegevens-toe-of-overschrijf-deze)[](#voeg-gegevens-toe-of-overschrijf-deze)

Om een nieuwe sleutel toe te voegen of de waarde of sorteersleutel van een sleutel in de geordende kaart te overschrijven, roep je [MemoryStoreSortedMap:SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#SetAsync)  aan met de sleutel naam , de waarde , een vervaltijd  in seconden en een optionele sorteersleutel . Het geheugen ruimt automatisch op zodra de sleutel vervalt. De maximale vervaltijd is 3.888.000 seconden (45 dagen). De sorteersleutel, indien opgegeven, moet een geldig nummer (geheel of drijvend punt) of een string zijn.

In de sorteervolgorde van je sleutels heeft een sorteersleutel voorrang boven een sleutel. Bijvoorbeeld, bij het sorteren in oplopende volgorde, worden numerieke sorteersleutels eerst gesorteerd, gevolgd door string sorteersleutels, gevolgd door items zonder sorteersleutel. Alle items met numerieke sorteersleutels worden gesorteerd op sorteersleutel; als de sorteersleutel voor twee items gelijk is, worden ze gesorteerd op sleutel. Evenzo worden alle items met string sorteersleutels gesorteerd op sorteersleutel; als de sorteersleutel voor twee items gelijk is, worden ze gesorteerd op sleutel. Alle items zonder sorteersleutel worden alleen gesorteerd op de sleutel.

Voorbeeld van enkele gegevens gesorteerd in oplopende volgorde -

```

{key: "player1", value: someValue1, sortKey: -1}

{key: "player2", value: someValue2, sortKey: 0}

{key: "player4", value: someValue3, sortKey: 1}

{key: "player5", value: someValue4, sortKey: 1}

{key: "player3", value: someValue5, sortKey: 3.14}

{key: "player6", value: someValue6, sortKey: "someString"}

{key: "player0", value: someValue7}

{key: "player7", value: someValue8}

```

Let op hoe player0  na alle sleutels met een sorteersleutel sorteert. player6  sorteert na alle sleutels met een numerieke sorteersleutel. player4  en player5  hebben dezelfde sorteersleutel, dus ze worden in oplopende volgorde op sleutel gesorteerd.

Gegevens Toevoegen aan een Geordende Kaart

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

local setSuccess, _ = pcall(function()

	return sortedMap:SetAsync("User_1234", 1000, 30, 3.14152)

end)

if setSuccess then

	print("Instellen geslaagd.")

end

```

## [Verkrijg gegevens](#verkrijg-gegevens)[](#verkrijg-gegevens)

Je kunt ofwel een gegevenswaarde en sorteersleutel ophalen die aan een specifieke sleutel zijn gekoppeld, of meerdere waarden en sorteersleutels voor sleutels binnen een bereik ophalen.

### [Verkrijg gegevens met één sleutel](#verkrijg-gegevens-met-één-sleutel)[](#verkrijg-gegevens-met-één-sleutel)

Om een waarde en sorteersleutel op te halen die aan één sleutel uit de geordende kaart zijn gekoppeld, roep je [MemoryStoreSortedMap:GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetAsync)  aan met de sleutel naam .

Een Bepaalde Sleutel Verkrijgen uit een Geordende Kaart

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

local setSuccess, _ = pcall(function()

	return sortedMap:SetAsync("User_1234", 1000, 30, 3.14152)

end)

if setSuccess then

	print("Instellen geslaagd.")

end

local item

local getSuccess, getError = pcall(function()

	item = sortedMap:GetAsync("User_1234")

end)

if getSuccess then

	print(item)

else

	warn(getError)

end

```

### [Verkrijg gegevens met meerdere sleutels](#verkrijg-gegevens-met-meerdere-sleutels)[](#verkrijg-gegevens-met-meerdere-sleutels)

Om gegevens voor meerdere sleutels uit de geordende kaart als één operatie op te halen, roep je [MemoryStoreSortedMap:GetRangeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetRangeAsync)  aan. Deze functie lijst standaard alle bestaande sleutels op, maar je kunt de boven- en ondergrenzen voor het sleutelbereik instellen. Bijvoorbeeld, de volgende codevoorbeeld haalt tot 20 items op, beginnend vanaf het begin van de geordende kaart, met sleutels groter dan of gelijk aan 10 , sorteersleutels groter dan of gelijk aan 100  en sleutels kleiner dan of gelijk aan 50 , sorteersleutels kleiner dan of gelijk aan 500 .

Een Bereik van Sleutels Verkrijgen uit een Geordende Kaart

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

local lowerBound = {}

lowerBound["key"] = "10"

lowerBound["sortKey"] = 100

local upperBound = {}

upperBound["key"] = "50"

upperBound["sortKey"] = 500

-- Verkrijg tot 20 items beginnend vanaf het begin

local getSuccess, items = pcall(function()

	return sortedMap:GetRangeAsync(

		Enum.SortDirection.Ascending, 20, lowerBound, upperBound)

end)

if getSuccess then

	for _, item in items do

		print(item.key)

		print(item.sortKey)

	end

end

```

## [Werk gegevens bij](#werk-gegevens-bij)[](#werk-gegevens-bij)

Om de waarde en sorteersleutel van een sleutel uit een geordende kaart op te halen en deze bij te werken, roep je [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  aan met de sleutel naam , een callbackfunctie  om de waarde en sorteersleutel voor deze sleutel bij te werken, en een vervaltijd  in seconden. De maximale vervaltijd is 3.888.000 seconden (45 dagen).

Voor de meeste spellen kunnen meerdere servers tegelijkertijd dezelfde sleutel bijwerken en de waarde wijzigen. Aangezien [UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  altijd de laatste waarde wijzigt voordat deze wordt bijgewerkt, moet je deze gebruiken om de laatste waarde als invoer voor je callbackfunctie te lezen.

Bijvoorbeeld, het volgende codevoorbeeld werkt de score in een ranglijst voor een speler bij. De score wordt berekend als kills / deaths. [UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  zorgt ervoor dat de kills en deaths worden bijgewerkt voor de meest recente waarden, zelfs als meerdere game-servers tegelijkertijd hetzelfde item bijwerken. De kills en deaths van een speler zijn monotoon toenemende waarden en kunnen daarom alleen in waarde toenemen in een sessie.

De ranglijstscore voor een speler in een Geordende Kaart Bijwerken

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("Leaderboard")

local function updateLeaderboard(itemKey, killsToAdd, deathsToAdd)

	local success, newStats, newScore = pcall(function()

		return sortedMap:UpdateAsync(itemKey, function(playerStats, playerScore)

			playerStats = playerStats or { kills = 0, deaths = 0 }

			playerStats.kills += killsToAdd

			playerStats.deaths += deathsToAdd

			if playerStats then

				-- `playerScore` is de sorteersleutel die wordt gebruikt om items in de kaart te sorteren

				playerScore = playerStats.kills / math.max(playerStats.deaths, 1)

				return playerStats, playerScore

			end

			return nil

		end, 30)

	end)

	if success then

		print(newStats)

		print(newScore)

	end

end

```

De latentie voor [UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync)  is vergelijkbaar met [GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetAsync)  en [SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#SetAsync)  tenzij er concurrentie is.

Wanneer er concurrentie optreedt, probeert het systeem automatisch de bewerking opnieuw totdat een van deze drie dingen gebeurt: de bewerking slaagt, de callbackfunctie nil  retourneert, of het maximale aantal herhalingen is bereikt. Als het systeem het maximale aantal herhalingen bereikt, retourneert het een conflict.

## [Verwijder gegevens](#verwijder-gegevens)[](#verwijder-gegevens)

Je kunt [MemoryStoreSortedMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#RemoveAsync)  gebruiken voor zowel het verwijderen van één sleutel uit de geordende kaart als het verwijderen van alle gegevens in een geheugenopslag geordende kaart.

### [Verwijder een sleutel](#verwijder-een-sleutel)[](#verwijder-een-sleutel)

Om een sleutel uit de geordende kaart te verwijderen, roep je [MemoryStoreSortedMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#RemoveAsync)  aan met een sleutel naam .

Verwijder een Sleutel uit een Geordende Kaart

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

local setSuccess, _ = pcall(function()

	return sortedMap:SetAsync("User_1234", 1000, 30, "someStringSortKey")

end)

if setSuccess then

	print("Instellen geslaagd.")

end

local removeSuccess, removeError = pcall(function()

	sortedMap:RemoveAsync("User_1234")

end)

if not removeSuccess then

	warn(removeError)

end

```

### [Verwijder alle gegevens](#verwijder-alle-gegevens)[](#verwijder-alle-gegevens)

Om geheugen in geordende kaarten te verwijderen, lijst je al je sleutels op met [MemoryStoreSortedMap:GetRangeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetRangeAsync) , en verwijder ze vervolgens met [MemoryStoreSortedMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#RemoveAsync) .

Verwijder Geheugen in een Geordende Kaart

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

-- Initiële ondergrens van nil begint flush vanaf het eerste item

local exclusiveLowerBound = nil

while true do

	-- Verkrijg tot honderd items beginnend vanaf de huidige ondergrens

	local getRangeSuccess, items = pcall(function()

		return sortedMap:GetRangeAsync(Enum.SortDirection.Ascending, 100, exclusiveLowerBound)

	end)

	if getRangeSuccess then

		local removeSuccess = true

		local removeError = nil

		for _, item in items do

			removeSuccess, removeError = pcall(function()

				sortedMap:RemoveAsync(item.key)

			end)

		end

		-- Als er een fout was bij het verwijderen van items, probeer het opnieuw met dezelfde exclusieve ondergrens

		if not removeSuccess then

			warn(removeError)

		-- Als het bereik minder dan honderd items is, is het einde van de kaart bereikt

		elseif #items < 100 then

			break

		else

			-- De laatst opgehaalde sleutel is de exclusieve ondergrens voor de volgende iteratie

			exclusiveLowerBound = {}

			exclusiveLowerBound["key"] = items[#items].key

			exclusiveLowerBound["sortKey"] = items[#items].sortKey

		end

	end

end

```

## [Verkrijg grootte](#verkrijg-grootte)[](#verkrijg-grootte)

Om het aantal items in de geordende kaart te krijgen, roep je [MemoryStoreSortedMap:GetSizeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#GetSizeAsync)  aan.

De Grootte van een Geordende Kaart Verkrijgen

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local sortedMap = MemoryStoreService:GetSortedMap("SortedMap1")

local setSuccess, _ = pcall(function()

	return sortedMap:SetAsync("User_1234", 1000, 30, 3.14152)

end)

if setSuccess then

	print("Instellen geslaagd.")

end

local size

local success, sizError = pcall(function()

	size = sortedMap:GetSizeAsync()

end)

if success then

	print(size)

else

	warn(sizeError)

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
