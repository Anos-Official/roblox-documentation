<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/DataStore -->

DataStore | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GlobalDataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore)
8. /
9. [DataStore](/docs/nl-nl/reference/engine/classes/DataStore)

Nederlands

Feedback

Engine-klasse

DataStore

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/DataStore)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetVersionAsync](#GetVersionAsync) (key :  [string](/docs/nl-nl/luau/strings) , version :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
| --- | --- |
|

[GetVersionAtTimeAsync](#GetVersionAtTimeAsync) (key :  [string](/docs/nl-nl/luau/strings) , timestamp :  [number](/docs/nl-nl/luau/numbers) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[ListKeysAsync](#ListKeysAsync) (prefix :  [string](/docs/nl-nl/luau/strings) , pageSize :  [number](/docs/nl-nl/luau/numbers) , cursor :  [string](/docs/nl-nl/luau/strings) , excludeDeleted :  [boolean](/docs/nl-nl/luau/booleans) ) :[DataStoreKeyPages](/docs/nl-nl/reference/engine/classes/DataStoreKeyPages)

 |
|

[ListVersionsAsync](#ListVersionsAsync) (key :  [string](/docs/nl-nl/luau/strings) , sortDirection :  [Enum.SortDirection](/docs/nl-nl/reference/engine/enums/SortDirection) , minDate :  [number](/docs/nl-nl/luau/numbers) , maxDate :  [number](/docs/nl-nl/luau/numbers) , pageSize :  [number](/docs/nl-nl/luau/numbers) ) :[DataStoreVersionPages](/docs/nl-nl/reference/engine/classes/DataStoreVersionPages)

 |
|

[RemoveVersionAsync](#RemoveVersionAsync) (key :  [string](/docs/nl-nl/luau/strings) , version :  [string](/docs/nl-nl/luau/strings) ) : ()

Verouderd

 |

Overgenomen leden

7  overgenomen van [GlobalDataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GetVersionAsync

Opbrengst

Mogelijkheden: DataStore

DataStore:GetVersionAsync (

key :[string](/docs/nl-nl/luau/strings) , version :[string](/docs/nl-nl/luau/strings)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

version :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

GetVersionAtTimeAsync

Opbrengst

Mogelijkheden: DataStore

DataStore:GetVersionAtTimeAsync (

key :[string](/docs/nl-nl/luau/strings) , timestamp :[number](/docs/nl-nl/luau/numbers)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

timestamp :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

Gegevensopslagversies ophalen op basis van tijd

```

local DataStoreService = game:GetService("DataStoreService")

local dataStore = DataStoreService:GetDataStore("DataStore")

local key = "key-123"

function setData(data)

	local success, result = pcall(function()

		dataStore:SetAsync(key, data)

	end)

	if not success then

		warn(result)

	end

end

function getVersionAtTime(timestamp)

	local success, result, keyInfo = pcall(function()

		return dataStore:GetVersionAtTimeAsync(key, timestamp.UnixTimestampMillis)

	end)

	if success then

		if result == nil then

			print("Geen versie gevonden op dat tijdstip")

		else

			print(result, keyInfo.Version)

		end

	else

		warn(result)

	end

end

-- Eerder uitgevoerd op 2024/12/02 6:00 UTC

setData("versie 1")

-- Eerder uitgevoerd op 2024/12/02 9:00 UTC

setData("versie 2")

-- Print "Geen versie gevonden op dat tijdstip"

local time1 = DateTime.fromUniversalTime(2024, 12, 02, 05, 00)

getVersionAtTime(time1)

-- Print "versie 1 <versie>"

local time2 = DateTime.fromUniversalTime(2024, 12, 02, 07, 00)

getVersionAtTime(time2)

-- Print "versie 2 <versie>"

local time3 = DateTime.fromUniversalTime(2024, 12, 02, 10, 00)

getVersionAtTime(time3)

```

Feedback geven

---

ListKeysAsync

Opbrengst

Mogelijkheden: DataStore

DataStore:ListKeysAsync (

prefix :[string](/docs/nl-nl/luau/strings) , pageSize :[number](/docs/nl-nl/luau/numbers) , cursor :[string](/docs/nl-nl/luau/strings) , excludeDeleted :[boolean](/docs/nl-nl/luau/booleans)

) :[DataStoreKeyPages](/docs/nl-nl/reference/engine/classes/DataStoreKeyPages)

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
|

excludeDeleted :[boolean](/docs/nl-nl/luau/booleans)

Standaardwaarde: false |

Teruggaves

[DataStoreKeyPages](/docs/nl-nl/reference/engine/classes/DataStoreKeyPages)

Feedback geven

---

ListVersionsAsync

Opbrengst

Mogelijkheden: DataStore

DataStore:ListVersionsAsync (

key :[string](/docs/nl-nl/luau/strings) , sortDirection :[Enum.SortDirection](/docs/nl-nl/reference/engine/enums/SortDirection) , minDate :[number](/docs/nl-nl/luau/numbers) , maxDate :[number](/docs/nl-nl/luau/numbers) , pageSize :[number](/docs/nl-nl/luau/numbers)

) :[DataStoreVersionPages](/docs/nl-nl/reference/engine/classes/DataStoreVersionPages)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

sortDirection :[Enum.SortDirection](/docs/nl-nl/reference/engine/enums/SortDirection)

Standaardwaarde: Ascending |
|

minDate :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

maxDate :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

pageSize :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Teruggaves

[DataStoreVersionPages](/docs/nl-nl/reference/engine/classes/DataStoreVersionPages)

Codevoorbeelden

Gegevensopslagversies ophalen met een datumfilter

```

local DataStoreService = game:GetService("DataStoreService")

local experienceStore = DataStoreService:GetDataStore("PlayerExperience")

local time = DateTime.fromUniversalTime(2020, 10, 09, 01, 42)

local listSuccess, pages = pcall(function()

	return experienceStore:ListVersionsAsync("User_1234", nil, time.UnixTimestampMillis)

end)

if listSuccess then

	local items = pages:GetCurrentPage()

	for key, info in pairs(items) do

		print("Sleutel:", key, "; Versie:", info.Version, "; Aangemaakt:", info.CreatedTime, "; Verwijderd:", info.IsDeleted)

	end

end

```

Feedback geven

---

RemoveVersionAsync

Verouderd

Details weergeven

---

Ga naar

▼

DataStore

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetVersionAsync()](#GetVersionAsync)

[GetVersionAtTimeAsync()](#GetVersionAtTimeAsync)

[ListKeysAsync()](#ListKeysAsync)

[ListVersionsAsync()](#ListVersionsAsync)

[RemoveVersionAsync()](#RemoveVersionAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
