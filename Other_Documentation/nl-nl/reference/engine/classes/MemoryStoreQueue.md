<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/MemoryStoreQueue -->

MemoryStoreQueue | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [MemoryStoreQueue](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue)

Nederlands

Feedback

Engine-klasse

MemoryStoreQueue

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/MemoryStoreQueue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[AddAsync](#AddAsync) (value :  Variant , expiration :  [number](/docs/nl-nl/luau/numbers) , priority :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
| --- | --- |
|

[GetSizeAsync](#GetSizeAsync) (excludeInvisible :  [boolean](/docs/nl-nl/luau/booleans) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[ReadAsync](#ReadAsync) (count :  [number](/docs/nl-nl/luau/numbers) , allOrNothing :  [boolean](/docs/nl-nl/luau/booleans) , waitTimeout :  [number](/docs/nl-nl/luau/numbers) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[RemoveAsync](#RemoveAsync) (id :  [string](/docs/nl-nl/luau/strings) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

AddAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreQueue:AddAsync (

value : Variant , expiration :[number](/docs/nl-nl/luau/numbers) , priority :[number](/docs/nl-nl/luau/numbers)

) : ()

Parameters

|

value : Variant

 |
|

expiration :[number](/docs/nl-nl/luau/numbers)

 |
|

priority :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Teruggaves

()

Feedback geven

---

GetSizeAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreQueue:GetSizeAsync (excludeInvisible :[boolean](/docs/nl-nl/luau/booleans) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

excludeInvisible :[boolean](/docs/nl-nl/luau/booleans)

Standaardwaarde: false |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

ReadAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreQueue:ReadAsync (

count :[number](/docs/nl-nl/luau/numbers) , allOrNothing :[boolean](/docs/nl-nl/luau/booleans) , waitTimeout :[number](/docs/nl-nl/luau/numbers)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

count :[number](/docs/nl-nl/luau/numbers)

 |
|

allOrNothing :[boolean](/docs/nl-nl/luau/booleans)

Standaardwaarde: false |
|

waitTimeout :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: -1 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

Een MemoryStoreQueue gebruiken

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local DataStoreService = game:GetService("DataStoreService")

local queue = MemoryStoreService:GetQueue("PlayerQueue")

local dataStore = DataStoreService:GetDataStore("PlayerStore")

while true do

	pcall(function()

		-- wacht op een item om te verwerken

		local items, id = queue:ReadAsync(1, false, 30)

		-- controleer of er een item is opgehaald

		if #items > 0 then

			-- markeer het item als verwerkt

			dataStore:UpdateAsync(items[0], function(data)

				data = data of {}

				data.processed = 1

				return data

			end)

			-- verwijder het item uit de queue

			queue:RemoveAsync(id)

		end

	end)

end

```

Feedback geven

---

RemoveAsync

Opbrengst

Mogelijkheden: DataStore

MemoryStoreQueue:RemoveAsync (id :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

id :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Codevoorbeelden

Een MemoryStoreQueue gebruiken

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local DataStoreService = game:GetService("DataStoreService")

local queue = MemoryStoreService:GetQueue("PlayerQueue")

local dataStore = DataStoreService:GetDataStore("PlayerStore")

while true do

	pcall(function()

		-- wacht op een item om te verwerken

		local items, id = queue:ReadAsync(1, false, 30)

		-- controleer of er een item is opgehaald

		if #items > 0 then

			-- markeer het item als verwerkt

			dataStore:UpdateAsync(items[0], function(data)

				data = data of {}

				data.processed = 1

				return data

			end)

			-- verwijder het item uit de queue

			queue:RemoveAsync(id)

		end

	end)

end

```

Feedback geven

---

Ga naar

▼

MemoryStoreQueue

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[AddAsync()](#AddAsync)

[GetSizeAsync()](#GetSizeAsync)

[ReadAsync()](#ReadAsync)

[RemoveAsync()](#RemoveAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
