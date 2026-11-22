<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap -->

MemoryStoreSortedMap | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [MemoryStoreSortedMap](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap)

Nederlands

Feedback

Engine-klasse

MemoryStoreSortedMap

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/MemoryStoreSortedMap)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetAsync](#GetAsync) (key :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
| --- | --- |
|

[GetRangeAsync](#GetRangeAsync) (direction :  [Enum.SortDirection](/docs/nl-nl/reference/engine/enums/SortDirection) , count :  [number](/docs/nl-nl/luau/numbers) , exclusiveLowerBound :  Variant , exclusiveUpperBound :  Variant ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetSizeAsync](#GetSizeAsync) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[RemoveAsync](#RemoveAsync) (key :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[SetAsync](#SetAsync) (key :  [string](/docs/nl-nl/luau/strings) , value :  Variant , expiration :  [number](/docs/nl-nl/luau/numbers) , sortKey :  Variant ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[UpdateAsync](#UpdateAsync) (key :  [string](/docs/nl-nl/luau/strings) , transformFunction :  [function](/docs/nl-nl/luau/functions) , expiration :  [number](/docs/nl-nl/luau/numbers) ) :[Tuple](/docs/nl-nl/luau/tuples)

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

MemoryStoreSortedMap:GetAsync (key :[string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

GetRangeAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreSortedMap:GetRangeAsync (

direction :[Enum.SortDirection](/docs/nl-nl/reference/engine/enums/SortDirection) , count :[number](/docs/nl-nl/luau/numbers) , exclusiveLowerBound : Variant , exclusiveUpperBound : Variant

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

direction :[Enum.SortDirection](/docs/nl-nl/reference/engine/enums/SortDirection)

 |
|

count :[number](/docs/nl-nl/luau/numbers)

 |
|

exclusiveLowerBound : Variant

 |
|

exclusiveUpperBound : Variant

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Gegevens ophalen van MemoryStore Sleutels

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local myMap = MemoryStoreService:GetSortedMap("MySortedMap")

function printAllKeys(map)

	-- de initiële ondergrens is nil wat betekent dat we vanaf het eerste item beginnen

	local exclusiveLowerBound = nil

	-- deze lus gaat door totdat het einde van de kaart is bereikt

	while true do

		-- haal tot honderd items op, beginnend vanaf de huidige ondergrens

		local items = map:GetRangeAsync(Enum.SortDirection.Ascending, 100, exclusiveLowerBound)

		for _, item in ipairs(items) do

			print(item.key)

			print(item.sortKey)

		end

		-- als de oproep minder dan honderd items retourneert, betekent dit dat we het einde van de kaart hebben bereikt

		if #items < 100 then

			break

		end

		-- de laatst opgehaalde sleutel is de exclusieve ondergrens voor de volgende iteratie

		exclusiveLowerBound = {}

		exclusiveLowerBound["key"] = items[#items].key

		exclusiveLowerBound["sortKey"] = items[#items].sortKey

	end

end

printAllKeys(myMap)

```

Feedback geven

---

GetSizeAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreSortedMap:GetSizeAsync () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

RemoveAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreSortedMap:RemoveAsync (key :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

SetAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreSortedMap:SetAsync (

key :[string](/docs/nl-nl/luau/strings) , value : Variant , expiration :[number](/docs/nl-nl/luau/numbers) , sortKey : Variant

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
|

sortKey : Variant

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

UpdateAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreSortedMap:UpdateAsync (

key :[string](/docs/nl-nl/luau/strings) , transformFunction :[function](/docs/nl-nl/luau/functions) , expiration :[number](/docs/nl-nl/luau/numbers)

) :[Tuple](/docs/nl-nl/luau/tuples)

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

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

Een MemoryStore Gesorteerde Kaart Bijwerken

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local map = MemoryStoreService:GetSortedMap("Leaderboard")

local Players = game:GetService("Players")

function updateLeaderboard(itemKey, killsToAdd, deathsToAdd)

	local success, newStats, newScore = pcall(function()

		return map:UpdateAsync(itemKey, function(playerStats, playerScore)

			playerStats = playerStats or { kills = 0, deaths = 0 }

			playerStats.kills += killsToAdd

			playerStats.deaths += deathsToAdd

			if playerStats then

				-- `playerScore` is de sortKey die wordt gebruikt om items in de kaart te sorteren

				playerScore = playerStats.kills / math.max(playerStats.deaths, 1)

				return playerStats, playerScore

			end

			return nil

		end, 30)

	end)

end

-- Voeg één kill toe aan alle spelers

for i, player in pairs(Players:GetPlayers()) do

	updateLeaderboard(player.UserId, 1, 0)

end

-- Voeg 5 kills en 1 death toe aan speler met userId 12345

updateLeaderboard(12345, 5, 1)

```

Feedback geven

---

Ga naar

▼

MemoryStoreSortedMap

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetAsync()](#GetAsync)

[GetRangeAsync()](#GetRangeAsync)

[GetSizeAsync()](#GetSizeAsync)

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
