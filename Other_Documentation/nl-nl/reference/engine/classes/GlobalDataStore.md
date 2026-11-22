<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/GlobalDataStore -->

GlobalDataStore | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GlobalDataStore](/docs/nl-nl/reference/engine/classes/GlobalDataStore)

Nederlands

Feedback

Engine-klasse

GlobalDataStore

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/GlobalDataStore)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[BatchGetAsync](#BatchGetAsync) (keys :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
| --- | --- |
|

[GetAsync](#GetAsync) (key :  [string](/docs/nl-nl/luau/strings) , options :  [DataStoreGetOptions](/docs/nl-nl/reference/engine/classes/DataStoreGetOptions) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[IncrementAsync](#IncrementAsync) (key :  [string](/docs/nl-nl/luau/strings) , delta :  [number](/docs/nl-nl/luau/numbers) , userIds :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [DataStoreIncrementOptions](/docs/nl-nl/reference/engine/classes/DataStoreIncrementOptions) ) : Variant

 |
|

[OnUpdate](#OnUpdate) (key :  [string](/docs/nl-nl/luau/strings) , callback :  [function](/docs/nl-nl/luau/functions) ) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Verouderd

 |
|

[RemoveAsync](#RemoveAsync) (key :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[SetAsync](#SetAsync) (key :  [string](/docs/nl-nl/luau/strings) , value :  Variant , userIds :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [DataStoreSetOptions](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions) ) : Variant

 |
|

[UpdateAsync](#UpdateAsync) (key :  [string](/docs/nl-nl/luau/strings) , transformFunction :  [function](/docs/nl-nl/luau/functions) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[DataStore](/docs/nl-nl/reference/engine/classes/DataStore) , [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)

---

API-referentie

Methoden

BatchGetAsync

Opbrengst

Mogelijkheden: DataStore

GlobalDataStore:BatchGetAsync (

keys :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

keys :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Batch ophalen van spelerscores

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

Feedback geven

---

GetAsync

Opbrengst

Mogelijkheden: DataStore

GlobalDataStore:GetAsync (

key :[string](/docs/nl-nl/luau/strings) , options :[DataStoreGetOptions](/docs/nl-nl/reference/engine/classes/DataStoreGetOptions)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

options :[DataStoreGetOptions](/docs/nl-nl/reference/engine/classes/DataStoreGetOptions)

Standaardwaarde: nil |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

IncrementAsync

Opbrengst

Mogelijkheden: DataStore

GlobalDataStore:IncrementAsync (

key :[string](/docs/nl-nl/luau/strings) , delta :[number](/docs/nl-nl/luau/numbers) , userIds :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[DataStoreIncrementOptions](/docs/nl-nl/reference/engine/classes/DataStoreIncrementOptions)

) : Variant

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

delta :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

userIds :[{any}](/docs/nl-nl/luau/tables#arrays)

Standaardwaarde: {} |
|

options :[DataStoreIncrementOptions](/docs/nl-nl/reference/engine/classes/DataStoreIncrementOptions)

Standaardwaarde: nil |

Teruggaves

Variant

Feedback geven

---

OnUpdate

Verouderd

Details weergeven

---

RemoveAsync

Opbrengst

Mogelijkheden: DataStore

GlobalDataStore:RemoveAsync (key :[string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

SetAsync

Opbrengst

Mogelijkheden: DataStore

GlobalDataStore:SetAsync (

key :[string](/docs/nl-nl/luau/strings) , value : Variant , userIds :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[DataStoreSetOptions](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions)

) : Variant

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

value : Variant

 |
|

userIds :[{any}](/docs/nl-nl/luau/tables#arrays)

Standaardwaarde: {} |
|

options :[DataStoreSetOptions](/docs/nl-nl/reference/engine/classes/DataStoreSetOptions)

Standaardwaarde: nil |

Teruggaves

Variant

Feedback geven

---

UpdateAsync

Opbrengst

Mogelijkheden: DataStore

GlobalDataStore:UpdateAsync (

key :[string](/docs/nl-nl/luau/strings) , transformFunction :[function](/docs/nl-nl/luau/functions)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

transformFunction :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

Ga naar

▼

GlobalDataStore

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[BatchGetAsync()](#BatchGetAsync)

[GetAsync()](#GetAsync)

[IncrementAsync()](#IncrementAsync)

[OnUpdate()](#OnUpdate)

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
