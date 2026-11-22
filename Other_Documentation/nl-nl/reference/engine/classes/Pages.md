<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Pages -->

Pages | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/nl-nl/reference/engine/classes/Pages)

Nederlands

Feedback

Engine-klasse

Pages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Pages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[IsFinished](#IsFinished) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |

Methoden

|

[AdvanceToNextPageAsync](#AdvanceToNextPageAsync) () : ()

 |
|

[GetCurrentPage](#GetCurrentPage) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[AudioPages](/docs/nl-nl/reference/engine/classes/AudioPages) , [BanHistoryPages](/docs/nl-nl/reference/engine/classes/BanHistoryPages) , [CapturesPages](/docs/nl-nl/reference/engine/classes/CapturesPages) , [CatalogPages](/docs/nl-nl/reference/engine/classes/CatalogPages) , [DataStoreKeyPages](/docs/nl-nl/reference/engine/classes/DataStoreKeyPages) , Meer weergeven...

Codevoorbeelden

Pagina Iterator

```

-- Herformatteer pagina's als tabellen

local function pagesToTable(pages)

	local items = {}

	while true do

		table.insert(items, pages:GetCurrentPage())

		if pages.IsFinished then

			break

		end

		pages:AdvanceToNextPageAsync()

	end

	return items

end

local function iterPageItems(pages)

	local contents = pagesToTable(pages)

	-- Volg het huidige paginanummer, beginnend bij 1

	local pageNum = 1

	-- Verkrijg het laatste paginanummer zodat we er niet overheen itereren

	local lastPageNum = #contents

	-- voor hervat deze coroutine totdat er niets meer te doorlopen is

	return coroutine.wrap(function()

		-- Loop totdat het paginanummer groter is dan het laatste paginanummer

		while pageNum <= lastPageNum do

			-- Doorloop alle vermeldingen van de huidige pagina

			for _, item in ipairs(contents[pageNum]) do

				-- Pauzeer de loop om de ontwikkelaar de vermelding en het paginanummer te laten afhandelen

				coroutine.yield(item, pageNum)

			end

			pageNum += 1

		end

	end)

end

-- Gebruik de iterPageItems functie om door de pagina's van een cataloguszoekopdracht te itereren

local AvatarEditorService = game:GetService("AvatarEditorService")

local parameters = CatalogSearchParams.new()

parameters.SearchKeyword = "Haar"

local catalogPages = AvatarEditorService:SearchCatalogAsync(parameters)

for item, pageNumber in iterPageItems(catalogPages) do

	print(item, pageNumber)

end

```

---

API-referentie

Eigenschappen

IsFinished

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Pages.IsFinished :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

AdvanceToNextPageAsync

Opbrengst

Pages:AdvanceToNextPageAsync () : ()

Teruggaves

()

Feedback geven

---

GetCurrentPage

Pages:GetCurrentPage () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Ga naar

▼

Pages

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[IsFinished](#IsFinished)

[Methoden](#methods)

[AdvanceToNextPageAsync()](#AdvanceToNextPageAsync)

[GetCurrentPage()](#GetCurrentPage)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
