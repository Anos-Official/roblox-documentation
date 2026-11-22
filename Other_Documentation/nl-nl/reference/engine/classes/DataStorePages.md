<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/DataStorePages -->

DataStorePages | Documentatie - Roblox Creator Hub

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
9. [DataStorePages](/docs/nl-nl/reference/engine/classes/DataStorePages)

Nederlands

Feedback

Engine-klasse

DataStorePages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/DataStorePages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

3  overgenomen van [Pages](/docs/nl-nl/reference/engine/classes/Pages)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Basisprincipes van OrderedDataStore

```

local DataStoreService = game:GetService("DataStoreService")

local pointsStore = DataStoreService:GetOrderedDataStore("Points")

local function printTopTenPlayers()

	local isAscending = false

	local pageSize = 10

	local pages = pointsStore:GetSortedAsync(isAscending, pageSize)

	local topTen = pages:GetCurrentPage()

	-- De gegevens in 'topTen' zijn opgeslagen met de index als de index op de pagina

	-- Voor elk item is 'data.key' de sleutel in de OrderedDataStore en 'data.value' de waarde

	for rank, data in ipairs(topTen) do

		local name = data.key

		local points = data.value

		print(name .. " is gerangschikt als #" .. rank .. " met " .. points .. " punten")

	end

	-- Mogelijk de volgende pagina laden...

	--pages:AdvanceToNextPageAsync()

end

-- Maak wat gegevens aan

pointsStore:SetAsync("Alex", 55)

pointsStore:SetAsync("Charley", 32)

pointsStore:SetAsync("Sydney", 68)

-- Toon de top tien spelers

printTopTenPlayers()

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
