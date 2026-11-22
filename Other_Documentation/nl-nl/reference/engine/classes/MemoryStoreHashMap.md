<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap -->

MemoryStoreHashMap | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [MemoryStoreHashMap](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMap)

Nederlands

Feedback

Engine-klasse

MemoryStoreHashMap

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/MemoryStoreHashMap)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetAsync](#GetAsync) (key :  [string](/docs/nl-nl/luau/strings) ) : Variant

 |
| --- | --- |
|

[ListItemsAsync](#ListItemsAsync) (count :  [number](/docs/nl-nl/luau/numbers) ) :[MemoryStoreHashMapPages](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMapPages)

 |
|

[RemoveAsync](#RemoveAsync) (key :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[SetAsync](#SetAsync) (key :  [string](/docs/nl-nl/luau/strings) , value :  Variant , expiration :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[UpdateAsync](#UpdateAsync) (key :  [string](/docs/nl-nl/luau/strings) , transformFunction :  [function](/docs/nl-nl/luau/functions) , expiration :  [number](/docs/nl-nl/luau/numbers) ) : Variant

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GetAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreHashMap:GetAsync (key :[string](/docs/nl-nl/luau/strings) ) : Variant

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

Variant

Codevoorbeelden

Gegevens ophalen uit een MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local key = "User_1234"

local value = 1000

local expiration = 30

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync(key, value, expiration)

end)

if setSuccess then

	print("Instellen is gelukt!")

end

local item

local getSuccess, getError = pcall(function()

	item = hashMap:GetAsync(key)

end)

if getSuccess then

	print(item)

else

	warn(getError)

end

```

Feedback geven

---

ListItemsAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreHashMap:ListItemsAsync (count :[number](/docs/nl-nl/luau/numbers) ) :[MemoryStoreHashMapPages](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMapPages)

Parameters

|

count :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[MemoryStoreHashMapPages](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMapPages)

Codevoorbeelden

Lijst met items in een MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local testHashMap = MemoryStoreService:GetHashMap("HashMap1")

local EXPIRATION = 600

local NUM_TEST_ITEMS = 32

local function populateHashMap(hashMap: MemoryStoreHashMap, numItems: number): { [string]: any }

	print("HashMap-gegevens instellen...")

	local createdItems = {}

	for index = 1, numItems do

		local key = tostring(index) -- HashMap-sleutels moeten strings zijn

		local value = `{key}_test_value`

		local success, result = pcall(hashMap.SetAsync, hashMap, key, value, EXPIRATION)

		if success then

			createdItems[key] = value

		else

			warn(`Fout bij het instellen van sleutel {key}: {result}`)

		end

	end

	print("Klaar met het instellen van HashMap-gegevens.")

	return createdItems

end

local function getItemsFromAllPages(pages: MemoryStoreHashMapPages): { [string]: any }

	-- Purely for logging purposes, we track what page number we're on

	local currentPageNumber = 1

	local retrievedItems = {}

	while not pages.IsFinished do

		print(`Items ophalen op pagina {currentPageNumber}...`)

		local items = pages:GetCurrentPage()

		for _, entry in pairs(items) do

			print(`	{entry.key}: {entry.value}`)

			retrievedItems[entry.key] = entry.value

		end

		-- Ga verder naar de volgende pagina als er meer pagina's zijn om te lezen

		if not pages.IsFinished then

			pages:AdvanceToNextPageAsync()

			currentPageNumber += 1

		end

	end

	print("Klaar met het lezen van alle pagina's")

	return retrievedItems

end

local function compareAllItems(retrievedItems: { [string]: any }, expectedItems: { [string]: any }): number

	print("Vergeleken opgehaalde items met verwachte items...")

	local numMatchingItems = 0

	for key, expectedValue in pairs(expectedItems) do

		if retrievedItems[key] == expectedValue then

			numMatchingItems += 1

		else

			warn(`Niet-overeenkomende opgehaalde waarde voor sleutel {key}: verwacht {expectedValue}, opgehaald {retrievedItems[key]}`)

		end

	end

	print("Vergelijking voltooid!")

	return numMatchingItems

end

-- Sleutels die aan de hashmap zijn toegevoegd, worden ook aan deze expectedItems-tabel toegevoegd.

-- Later zullen de opgehaalde hashmap-items worden vergeleken met deze tabel van verwachte items.

local expectedItems = populateHashMap(testHashMap, NUM_TEST_ITEMS)

-- Het ophalen van pagina's kan fout gaan. In dit geval laten we het fout gaan en stoppen we de uitvoering van het programma,

-- maar je kunt het pcall'en en het anders afhandelen.

print(`HashMap-pagina's ophalen met ListItemsAsync...`)

local pages = testHashMap:ListItemsAsync(NUM_TEST_ITEMS)

local retrievedItems = getItemsFromAllPages(pages)

local numMatchingItems = compareAllItems(retrievedItems, expectedItems)

-- Als er geen fouten waren bij het instellen of ophalen van items, zouden alle items overeen moeten komen.

print(`Programma voltooid. {numMatchingItems}/{NUM_TEST_ITEMS} opgehaalde items kwamen overeen met de verwachte waarden.`)

```

Feedback geven

---

RemoveAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreHashMap:RemoveAsync (key :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Codevoorbeelden

Gegevens verwijderen uit een MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local key = "User_1234"

local value = 1000

local expiration = 30

local setSuccess, setError = pcall(function()

	return hashMap:SetAsync(key, value, expiration)

end)

if not setSuccess then

	warn(setError)

end

local removeSuccess, removeError = pcall(function()

	hashMap:RemoveAsync(key)

end)

if removeSuccess then

	print("Verwijderen geslaagd!")

else

	warn(removeError)

end

```

Feedback geven

---

SetAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreHashMap:SetAsync (

key :[string](/docs/nl-nl/luau/strings) , value : Variant , expiration :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

value : Variant

 |
|

expiration :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Gegevens toevoegen aan een MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local key = "User_1234"

local value = 1000

local expiration = 30

local setSuccess, setError = pcall(function()

	return hashMap:SetAsync(key, value, expiration)

end)

if setSuccess then

	print("Instellen geslaagd!")

else

	warn(setError)

end

```

Feedback geven

---

UpdateAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreHashMap:UpdateAsync (

key :[string](/docs/nl-nl/luau/strings) , transformFunction :[function](/docs/nl-nl/luau/functions) , expiration :[number](/docs/nl-nl/luau/numbers)

) : Variant

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

transformFunction :[function](/docs/nl-nl/luau/functions)

 |
|

expiration :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Variant

Codevoorbeelden

Een Geheugenopslag Hash Map Bijwerken

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("ResourceInventory")

local function contributeResources(itemResource, addedCount)

	local success, newResourceCount = pcall(function()

		return hashMap:UpdateAsync(itemResource, function(resource)

			resource = resource or { count = 0 }

			resource.count = resource.count + addedCount

			-- zorg ervoor dat we het maximale hulpbronnenaantal niet overschrijden

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

contributeResources("myResource", 50)

```

Feedback geven

---

Ga naar

▼

MemoryStoreHashMap

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetAsync()](#GetAsync)

[ListItemsAsync()](#ListItemsAsync)

[RemoveAsync()](#RemoveAsync)

[SetAsync()](#SetAsync)

[UpdateAsync()](#UpdateAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
