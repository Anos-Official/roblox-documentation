<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/MemoryStoreHashMapPages -->

MemoryStoreHashMapPages | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/nl-nl/reference/engine/classes/Pages)
8. /
9. [MemoryStoreHashMapPages](/docs/nl-nl/reference/engine/classes/MemoryStoreHashMapPages)

Nederlands

Feedback

Engine-klasse

MemoryStoreHashMapPages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/MemoryStoreHashMapPages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

3  overgenomen van [Pages](/docs/nl-nl/reference/engine/classes/Pages)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

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

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
