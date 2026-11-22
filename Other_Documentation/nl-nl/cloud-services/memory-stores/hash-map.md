<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores/hash-map -->

Geheugenopslag hash map | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Geheugenopslag hash map

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Hash maps , vergelijkbaar met gesorteerde maps, stellen je in staat om gegevens in het geheugen op te slaan als sleutel-waarde paren. In tegenstelling tot gesorteerde maps behouden ze geen ordeningsgaranties. Deze gegevensstructuur is nuttig voor gevallen die eenvoudige gegevenscaching en snelle toegang vereisen, zoals gedeelde inventarissen, fysieke veilinghuizen, en meer. Hash maps beheren automatisch de partitionering van je gegevens en zijn zeer nuttig als je meer dan 1.000 sleutels hebt. Voor kleinere sleutelruimtes raden we [gesorteerde maps](/docs/nl-nl/cloud-services/memory-stores/sorted-map)  aan.

## [Limieten](#limieten)[](#limieten)

Hash maps hebben een limiet voor de sleutelgrootte van 128 tekens en een limiet voor de waarde van 32 KB.

Verder gebruiken hash maps dezelfde [API-aanroep](/docs/nl-nl/cloud-services/memory-stores#api-requests-limits)  en [geheugenquotum](/docs/nl-nl/cloud-services/memory-stores#geheugengroottequotum)  limieten als de andere gegevensstructuren voor geheugenopslag.

## [Verkrijg een hash map](#verkrijg-een-hash-map)[](#verkrijg-een-hash-map)

Om een hash map te verkrijgen, roep je [MemoryStoreService:GetHashMap()](/docs/nl-nl/reference/engine/classes/MemoryStoreService#GetHashMap)  aan met een naam voor de hash map. De naam is globaal binnen het spel, zodat je dezelfde hash map op elk script kunt benaderen met deze naam.

Een Hash Map Verkrijgen

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

```

Nadat je een hash map hebt verkregen, kun je een van de volgende functies aanroepen om gegevens erin te lezen of te schrijven:

| Functie | | Actie |
| --- | --- |
| [MemoryStoreHashMap:SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#SetAsync) | | [Voeg](#voeg-gegevens-toe-of-overschrijf-deze)  een nieuwe sleutel toe of overschrijf de waarde als de sleutel al bestaat. |
| [MemoryStoreHashMap:GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#GetAsync) | | [Lees](#verkrijg-gegevens)  een bepaalde sleutel. |
| [MemoryStoreHashMap:ListItemsAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync) | | [Lijst](#verkrijg-gegevens)  items in een hash map. |
| [MemoryStoreHashMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync) | | [Werk](#werk-gegevens-bij)  de waarde van een sleutel bij nadat je deze uit een hash map hebt opgehaald. |
| [MemoryStoreHashMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#RemoveAsync) | | [Verwijder](#verwijder-gegevens)  een sleutel uit de hash map. |

Voor uitgebreide documentatie over elke functie, zie [MemoryStoreHashMap](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap) .

Alle functies die toegang hebben tot gegevensstructuren in geheugenopslag zijn asynchrone netwerkoproepen die af en toe kunnen mislukken. Je moet deze oproepen omhullen in [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  om fouten op te vangen en af te handelen, zoals weergegeven in de codevoorbeelden.

## [Voeg gegevens toe of overschrijf deze](#voeg-gegevens-toe-of-overschrijf-deze)[](#voeg-gegevens-toe-of-overschrijf-deze)

Om een nieuwe sleutel toe te voegen of de waarde van een sleutel in de hash map te overschrijven, roep je [MemoryStoreHashMap:SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#SetAsync)  aan met de naam  van de sleutel, de waarde  en een vervaltijd  in seconden. Het geheugen ruimt automatisch op zodra de sleutel vervalt. De maximale vervaltijd is 3.888.000 seconden (45 dagen).

Gegevens Toevoegen aan een Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync("User_1234", 1000, 30)

end)

if setSuccess then

	print("Instellen geslaagd.")

end

```

## [Verkrijg gegevens](#verkrijg-gegevens)[](#verkrijg-gegevens)

Je kunt ofwel een waarde ophalen die is gekoppeld aan een specifieke sleutel, of meerdere sleutel-waarde paren in de hash map ophalen.

### [Verkrijg gegevens met één sleutel](#verkrijg-gegevens-met-één-sleutel)[](#verkrijg-gegevens-met-één-sleutel)

Om een waarde op te halen die is gekoppeld aan één sleutel uit de hash map, roep je [MemoryStoreHashMap:GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#GetAsync)  aan met de naam  van de sleutel.

Een Bepaalde Sleutel Verkrijgen uit een Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync("User_1234", 1000, 30)

end)

if setSuccess then

	print("Instellen geslaagd.")

end

local item

local getSuccess, getError = pcall(function()

	item = hashMap:GetAsync("User_1234")

end)

if getSuccess then

	print(item)

else

	warn(getError)

end

```

### [Verkrijg gegevens met meerdere sleutel-waarde paren](#verkrijg-gegevens-met-meerdere-sleutel-waarde-paren)[](#verkrijg-gegevens-met-meerdere-sleutel-waarde-paren)

Om alle sleutel-waarde paren uit de hash map als één operatie op te halen, roep je [MemoryStoreHashMap:ListItemsAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync)  aan met de gewenste paginagrootte. Deze functie lijst alle bestaande sleutels op een gepagineerde manier. Bijvoorbeeld, de volgende codevoorbeelden haalt tot 32 items uit de hash map op.

Items Lijsten in een Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

-- Verkrijg lijst van items, 32 items per keer

local success, pages = pcall(function()

	return hashMap:ListItemsAsync(32)

end)

if success then

	while true do

		-- Verkrijg de huidige pagina

		local entries = pages:GetCurrentPage()

		-- Itereer door alle sleutel-waarde paren op de pagina

		for _, entry in ipairs(entries) do

			print(entry.key .. " : " .. tostring(entry.value))

		end

		-- Controleer of de laatste pagina is bereikt

		if pages.IsFinished then

			break

		else

			print("----------")

			-- Ga naar de volgende pagina

			pages:AdvanceToNextPageAsync()

		end

	end

end

```

## [Werk gegevens bij](#werk-gegevens-bij)[](#werk-gegevens-bij)

Om de waarde van een sleutel uit een hash map op te halen en deze bij te werken, roep je [MemoryStoreHashMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  aan met de naam  van de sleutel, een callbackfunctie  om de sleutel bij te werken, en een vervaltijd  in seconden.

Voor de meeste spellen kunnen meerdere servers tegelijkertijd dezelfde sleutel bijwerken en de waarde wijzigen. Aangezien [UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  altijd de laatste waarde wijzigt voordat deze wordt bijgewerkt, moet je deze gebruiken om de laatste waarde als invoer voor je callbackfunctie te lezen.

Bijvoorbeeld, de volgende codevoorbeelden werken het aantal middelen van een middel in een gedeelde inventaris bij. [UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  zorgt ervoor dat alle bijdragen van spelers in deze gedeelde inventaris terechtkomen, zelfs als deze bijdragen gelijktijdig worden gedaan. In deze functie wordt ook een maximaal aantal middelen van 500 afgedwongen.

Hulpbronnen Aantal Bijwerken voor een Middel in een Gedeelde Inventaris

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("ResourceInventory")

local function contributeResources(itemResource, addedCount)

	local success, newResourceCount = pcall(function()

		return hashMap:UpdateAsync(itemResource, function(resource)

			resource = resource or {count = 0}

			resource.count = resource.count + addedCount

			-- zorg ervoor dat we het maximale aantal middelen niet overschrijden

			if resource.count > 500 then

				resource.count = 500

			end

			return resource

		end, 1200)

	end)

	if success then

		print(newResourceCount)

	end

end

```

De latentie voor [UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  is vergelijkbaar met [GetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#GetAsync)  en [SetAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#SetAsync)  tenzij er concurrentie is.

Wanneer er concurrentie optreedt, probeert het systeem automatisch de operatie opnieuw totdat een van deze drie dingen gebeurt: de operatie slaagt, de callbackfunctie retourneert nil , of het maximale aantal herhalingen is bereikt. Als het systeem het maximale aantal herhalingen bereikt, retourneert het een conflict.

## [Verwijder gegevens](#verwijder-gegevens)[](#verwijder-gegevens)

Je kunt [MemoryStoreHashMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#RemoveAsync)  gebruiken voor zowel het verwijderen van één sleutel uit de hash map als het verwijderen van alle gegevens in een geheugenopslag hash map.

### [Verwijder een sleutel](#verwijder-een-sleutel)[](#verwijder-een-sleutel)

Om een sleutel uit de hash map te verwijderen, roep je [MemoryStoreHashMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#RemoveAsync)  aan met een naam  van de sleutel.

Verwijder een Sleutel uit een Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync("User_1234", 1000, 30)

end)

if setSuccess then

	print("Instellen geslaagd.")

end

local removeSuccess, removeError = pcall(function()

	hashMap:RemoveAsync("User_1234")

end)

if not removeSuccess then

	warn(removeError)

end

```

### [Verwijder alle gegevens](#verwijder-alle-gegevens)[](#verwijder-alle-gegevens)

Om alle gegevens in een hash map te verwijderen, lijst je al je items met [MemoryStoreHashMap:ListItemsAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync) , en verwijder je ze vervolgens met [MemoryStoreHashMap:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap#RemoveAsync) .

Verwijder alle gegevens in een Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

-- Verkrijg lijst van items, 32 items per keer

local success, pages = pcall(function()

	return hashMap:ListItemsAsync(32)

end)

if success then

	while true do

		-- Verkrijg de huidige pagina

		local entries = pages:GetCurrentPage()

		local removeSuccess = true

		local removeError = nil

		-- Itereer door alle sleutel-waarde paren op de pagina

		for _, entry in ipairs(entries) do

			print(entry.key .. " : " .. tostring(entry.value))

			removeSuccess, removeError = pcall(function()

				hashMap:RemoveAsync(entry.key)

			end)

			if not removeSuccess then

				warn(removeError)

			end

		end

		-- Controleer of de laatste pagina is bereikt

		if pages.IsFinished then

			print("Klaar met het verwijderen van alle gegevens.")

			break

		else

			print("----------")

			-- Ga naar de volgende pagina

			pages:AdvanceToNextPageAsync()

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
