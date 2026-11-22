<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/DataStoreService -->

DataStoreService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)

Nederlands

Feedback

Engine-klasse

DataStoreService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/DataStoreService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetDataStore](#GetDataStore) (name :  [string](/docs/nl-nl/luau/strings) , scope :  [string](/docs/nl-nl/luau/strings) , options :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

 |
| --- | --- |
|

[GetGlobalDataStore](#GetGlobalDataStore) () :[DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

 |
|

[GetOrderedDataStore](#GetOrderedDataStore) (name :  [string](/docs/nl-nl/luau/strings) , scope :  [string](/docs/nl-nl/luau/strings) ) :[OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)

 |
|

[GetRequestBudgetForRequestType](#GetRequestBudgetForRequestType) (requestType :  [Enum.DataStoreRequestType](/docs/nl-nl/reference/engine/enums/DataStoreRequestType) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[ListDataStoresAsync](#ListDataStoresAsync) (prefix :  [string](/docs/nl-nl/luau/strings) , pageSize :  [number](/docs/nl-nl/luau/numbers) , cursor :  [string](/docs/nl-nl/luau/strings) ) :[DataStoreListingPages](/docs/nl-nl/reference/engine/classes/DataStoreListingPages)

 |
|

[SetRateLimitForRequestType](#SetRateLimitForRequestType) (requestType :  [Enum.DataStoreRequestType](/docs/nl-nl/reference/engine/enums/DataStoreRequestType) , baseLimit :  [number](/docs/nl-nl/luau/numbers) , perPlayerLimit :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

DataStore Budget

```

local DataStoreService = game:GetService("DataStoreService")

for _, enumItem in pairs(Enum.DataStoreRequestType:GetEnumItems()) do

	print(enumItem.Name, DataStoreService:GetRequestBudgetForRequestType(enumItem))

end

```

---

API-referentie

Methoden

GetDataStore

Mogelijkheden: DataStore

DataStoreService:GetDataStore (

name :[string](/docs/nl-nl/luau/strings) , scope :[string](/docs/nl-nl/luau/strings) , options :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

scope :[string](/docs/nl-nl/luau/strings)

Standaardwaarde: "global" |
|

options :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Standaardwaarde: nil |

Teruggaves

[DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

Feedback geven

---

GetGlobalDataStore

Mogelijkheden: DataStore

DataStoreService:GetGlobalDataStore () :[DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

Teruggaves

[DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

Codevoorbeelden

Krijg GlobalDataStore Instantie

```

local DataStoreService = game:GetService("DataStoreService")

local GlobalDataStore = DataStoreService:GetGlobalDataStore()

print(GlobalDataStore.Name)

```

Feedback geven

---

GetOrderedDataStore

Mogelijkheden: DataStore

DataStoreService:GetOrderedDataStore (

name :[string](/docs/nl-nl/luau/strings) , scope :[string](/docs/nl-nl/luau/strings)

) :[OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

scope :[string](/docs/nl-nl/luau/strings)

Standaardwaarde: "global" |

Teruggaves

[OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)

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

Feedback geven

---

GetRequestBudgetForRequestType

Mogelijkheden: DataStore

DataStoreService:GetRequestBudgetForRequestType (requestType :[Enum.DataStoreRequestType](/docs/nl-nl/reference/engine/enums/DataStoreRequestType) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

requestType :[Enum.DataStoreRequestType](/docs/nl-nl/reference/engine/enums/DataStoreRequestType)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Afdrukverzoekbudget

```

local DataStoreService = game:GetService("DataStoreService")

local globalStore = DataStoreService:GetGlobalDataStore()

local function printBudget()

	local budget = DataStoreService:GetRequestBudgetForRequestType(Enum.DataStoreRequestType.SetIncrementAsync)

	print("Huidig set/increment budget:", budget)

end

for i = 1, 5 do

	local key = "key" .. i

	local success, err = pcall(function()

		globalStore:SetAsync(key, true)

	end)

	if success then

		printBudget()

	else

		print(err)

	end

end

```

Feedback geven

---

ListDataStoresAsync

Opbrengst

Mogelijkheden: DataStore

DataStoreService:ListDataStoresAsync (

prefix :[string](/docs/nl-nl/luau/strings) , pageSize :[number](/docs/nl-nl/luau/numbers) , cursor :[string](/docs/nl-nl/luau/strings)

) :[DataStoreListingPages](/docs/nl-nl/reference/engine/classes/DataStoreListingPages)

Parameters

|

prefix :[string](/docs/nl-nl/luau/strings)

 |
|

pageSize :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

cursor :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[DataStoreListingPages](/docs/nl-nl/reference/engine/classes/DataStoreListingPages)

Feedback geven

---

SetRateLimitForRequestType

Mogelijkheden: DataStore

DataStoreService:SetRateLimitForRequestType (

requestType :[Enum.DataStoreRequestType](/docs/nl-nl/reference/engine/enums/DataStoreRequestType) , baseLimit :[number](/docs/nl-nl/luau/numbers) , perPlayerLimit :[number](/docs/nl-nl/luau/numbers)

) : ()

Parameters

|

requestType :[Enum.DataStoreRequestType](/docs/nl-nl/reference/engine/enums/DataStoreRequestType)

 |
|

baseLimit :[number](/docs/nl-nl/luau/numbers)

 |
|

perPlayerLimit :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Codevoorbeelden

Stel Snelheidslimieten In

```

local MigrateScript = require(script.Parent.MigrateScript)

local DataStoreService = game:GetService("DataStoreService")

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardRead, 1000, 0)

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardWrite, 2000, 0) -- twee schrijfbewerkingen, dus heeft dubbele limiet nodig als lezen

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardList, 100, 0)

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardRemove, 1000, 0)

local sourceStore = DataStoreService:GetDataStore("ds_to_migrate")

local destinationStore1 = DataStoreService:GetDataStore("ds_destination_1")

local destinationStore2 = DataStoreService:GetDataStore("ds_destination_2")

-- Helper om te wachten op budget

local function waitForBudget(requestType)

	while (DataStoreService:GetRequestBudgetForRequestType(requestType) <= 0) do

		task.wait(1)

	end

end

waitForBudget(Enum.DataStoreRequestType.StandardList)

local success, pages = pcall(function()

	return sourceStore:ListKeysAsync()

end)

if success then

	while true do

		local items = pages:GetCurrentPage()

		for _, item in ipairs(items) do

			-- 1. Haal gegevens op uit de bron

			waitForBudget(Enum.DataStoreRequestType.StandardRead)

			local getSuccess, value = pcall(function()

				return sourceStore:GetAsync(item.KeyName)

			end)

			if getSuccess and value ~= nil then

				-- 2. Migreer gegevens naar bestemmingen

				waitForBudget(Enum.DataStoreRequestType.StandardWrite)

				local setSuccess, err = pcall(function()

					destinationStore1:SetAsync(item.KeyName, MigrateScript.Migrate1(value))

				end)

				if setSuccess then

					print("Sleutel succesvol gemigreerd naar bestemming 1: " .. item.KeyName)

				else

					warn("Mislukt om sleutel te migreren naar bestemming 1: " .. item.KeyName .. " - " .. tostring(err))

				end

waitForBudget(Enum.DataStoreRequestType.StandardWrite)

				local setSuccess, err = pcall(function()

					destinationStore2:SetAsync(item.KeyName, MigrateScript.Migrate2(value))

				end)

				if setSuccess then

					print("Sleutel succesvol gemigreerd naar bestemming 2: " .. item.KeyName)

				else

					warn("Mislukt om sleutel te migreren naar bestemming 2: " .. item.KeyName .. " - " .. tostring(err))

				end

				-- 3. Verwijder gegevens uit de bron

				waitForBudget(Enum.DataStoreRequestType.StandardRemove)

				local deleteSuccess, err = pcall(function()

					sourceStore:RemoveAsync(item.KeyName)

				end)

				if deleteSuccess then

					print("Sleutel succesvol verwijderd uit de bron: " .. item.KeyName)

				else

					warn("Mislukt om sleutel te verwijderen uit de bron: " .. item.KeyName .. " - " .. tostring(err))

				end

			else

				warn("Mislukt om sleutel op te halen uit de bron: " .. item.KeyName)

			end

		end

		if pages.IsFinished then break end

		-- 3. Ga naar de volgende pagina

		waitForBudget(Enum.DataStoreRequestType.StandardList)

		local nextSuccess = pcall(function()

			pages:AdvanceToNextPageAsync()

		end)

		if not nextSuccess then

			warn("Mislukt om naar de volgende pagina te gaan.")

			break

		end

	end

	print("Migratieproces voltooid.")

else

	warn("Mislukt om sleutels te lijsten.")

end

```

Feedback geven

---

Ga naar

▼

DataStoreService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetDataStore()](#GetDataStore)

[GetGlobalDataStore()](#GetGlobalDataStore)

[GetOrderedDataStore()](#GetOrderedDataStore)

[GetRequestBudgetForRequestType()](#GetRequestBudgetForRequestType)

[ListDataStoresAsync()](#ListDataStoresAsync)

[SetRateLimitForRequestType()](#SetRateLimitForRequestType)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
