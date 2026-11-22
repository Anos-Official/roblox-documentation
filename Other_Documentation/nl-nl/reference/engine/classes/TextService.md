<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TextService -->

TextService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TextService](/docs/nl-nl/reference/engine/classes/TextService)

Nederlands

Feedback

Engine-klasse

TextService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TextService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[FilterAndTranslateStringAsync](#FilterAndTranslateStringAsync) (stringToFilter :  [string](/docs/nl-nl/luau/strings) , fromUserId :  [number](/docs/nl-nl/luau/numbers) , targetLocales :  [{any}](/docs/nl-nl/luau/tables#arrays) , textContext :  [Enum.TextFilterContext](/docs/nl-nl/reference/engine/enums/TextFilterContext) ) :[TextFilterTranslatedResult](/docs/nl-nl/reference/engine/classes/TextFilterTranslatedResult)

Verouderd

 |
| --- | --- |
|

[FilterStringAsync](#FilterStringAsync) (stringToFilter :  [string](/docs/nl-nl/luau/strings) , fromUserId :  [number](/docs/nl-nl/luau/numbers) , textContext :  [Enum.TextFilterContext](/docs/nl-nl/reference/engine/enums/TextFilterContext) ) :[TextFilterResult](/docs/nl-nl/reference/engine/classes/TextFilterResult)

 |
|

[GetFamilyInfoAsync](#GetFamilyInfoAsync) (assetId :  ContentId ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetTextBoundsAsync](#GetTextBoundsAsync) (params :  [GetTextBoundsParams](/docs/nl-nl/reference/engine/classes/GetTextBoundsParams) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[GetTextSize](#GetTextSize) (string :  [string](/docs/nl-nl/luau/strings) , fontSize :  [number](/docs/nl-nl/luau/numbers) , font :  [Enum.Font](/docs/nl-nl/reference/engine/enums/Font) , frameSize :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[GetTextSizeOffsetAsync](#GetTextSizeOffsetAsync) (fontSize :  [number](/docs/nl-nl/luau/numbers) , font :  [Font](/docs/nl-nl/reference/engine/datatypes/Font) ) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

FilterAndTranslateStringAsync

Verouderd

Details weergeven

---

FilterStringAsync

Opbrengst

Mogelijkheden: UI

TextService:FilterStringAsync (

stringToFilter :[string](/docs/nl-nl/luau/strings) , fromUserId :[number](/docs/nl-nl/luau/numbers) , textContext :[Enum.TextFilterContext](/docs/nl-nl/reference/engine/enums/TextFilterContext)

) :[TextFilterResult](/docs/nl-nl/reference/engine/classes/TextFilterResult)

Parameters

|

stringToFilter :[string](/docs/nl-nl/luau/strings)

 |
|

fromUserId :[number](/docs/nl-nl/luau/numbers)

 |
|

textContext :[Enum.TextFilterContext](/docs/nl-nl/reference/engine/enums/TextFilterContext)

Standaardwaarde: PrivateChat |

Teruggaves

[TextFilterResult](/docs/nl-nl/reference/engine/classes/TextFilterResult)

Codevoorbeelden

Voorbeeld van een Huisdiernaamfilter

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local TextService = game:GetService("TextService")

local Players = game:GetService("Players")

local Remotes = Instance.new("Folder")

Remotes.Name = "PetNamingRemotes"

Remotes.Parent = ReplicatedStorage

local UserNamedPet = Instance.new("RemoteEvent")

UserNamedPet.Name = "UserNamedPet"

UserNamedPet.Parent = Remotes

local SendPetName = Instance.new("RemoteEvent")

SendPetName.Name = "SendPetName"

SendPetName.Parent = Remotes

local RequestAllPetNames = Instance.new("RemoteFunction")

RequestAllPetNames.Name = "RequestAllPetNames"

RequestAllPetNames.Parent = Remotes

local filterResults = {}

local function broadcastPetName(userId)

	local filterResult = filterResults[userId]

	if filterResult then

		for _, player in pairs(Players:GetPlayers()) do

			if player then

				-- start een nieuwe thread zodat de update niet wordt onderbroken

				task.spawn(function()

					-- pak de gefilterde string voor deze gebruiker

					local toUserId = player.UserId

					local filteredString = filterResult:GetNonChatStringForUserAsync(toUserId)

					filteredString = filteredString or ""

					SendPetName:FireClient(player, userId, filteredString)

				end)

			end

		end

	end

end

UserNamedPet.OnServerEvent:Connect(function(player, petName)

	local fromUserId = player.UserId

	-- pcall om fouten op te vangen

	local success, result = pcall(function()

		return TextService:FilterStringAsync(petName, fromUserId)

	end)

	if success then

		filterResults[fromUserId] = result

		broadcastPetName(fromUserId)

	else

		print("Kon de huisdiernaam niet filteren")

	end

end)

RequestAllPetNames.OnServerInvoke = function(player)

	local toUserId = player.UserId

	local petNames = {}

	-- door filterresultaten gaan en de huisdiernaam filteren die verzonden moet worden

	for fromUserId, filterResult in pairs(filterResults) do

		local filteredString = filterResult:GetNonChatStringForUserAsync(toUserId)

		filteredString = filteredString or ""

		-- moet userId naar string converteren zodat het niet via een remote functie kan worden verzonden

		petNames[tostring(fromUserId)] = filteredString

	end

	return petNames

end

Players.PlayerRemoving:Connect(function(oldPlayer)

	local userId = oldPlayer.UserId

	filterResults[userId] = nil

end)

```

Feedback geven

---

GetFamilyInfoAsync

Opbrengst

Mogelijkheden: UI

TextService:GetFamilyInfoAsync (assetId : ContentId ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

assetId : ContentId

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Krijg informatie over lettertypefamilies

```

local TextService = game:GetService("TextService")

local familyToCheck = "rbxasset://fonts/families/Arimo.json"

local success, info = pcall(function()

	return TextService:GetFamilyInfoAsync(familyToCheck)

end)

if success then

	print("Naam van het lettertype:", info.Name)

	print("Gezichten:")

	for _, face in info.Faces do

		print("--------")

		print("Naam:", face.Name)

		print("Gewicht:", face.Weight.Name)

		print("Stijl:", face.Style.Name)

	end

end

```

Feedback geven

---

GetTextBoundsAsync

Opbrengst

Mogelijkheden: UI

TextService:GetTextBoundsAsync (params :[GetTextBoundsParams](/docs/nl-nl/reference/engine/classes/GetTextBoundsParams) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

params :[GetTextBoundsParams](/docs/nl-nl/reference/engine/classes/GetTextBoundsParams)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Codevoorbeelden

Tekstgrootte Meten

```

local TextService = game:GetService("TextService")

-- Verklaar parameters

local params = Instance.new("GetTextBoundsParams")

params.Text = "Hallo wereld!"

params.Font = Font.new("rbxasset://fonts/families/GrenzeGotisch.json", Enum.FontWeight.Thin)

params.Size = 20

params.Width = 200

local success, bounds = pcall(function()

	return TextService:GetTextBoundsAsync(params)

end)

if success then

	print(bounds)

end

```

Feedback geven

---

GetTextSize

Mogelijkheden: UI

TextService:GetTextSize (

string :[string](/docs/nl-nl/luau/strings) , fontSize :[number](/docs/nl-nl/luau/numbers) , font :[Enum.Font](/docs/nl-nl/reference/engine/enums/Font) , frameSize :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

string :[string](/docs/nl-nl/luau/strings)

 |
|

fontSize :[number](/docs/nl-nl/luau/numbers)

 |
|

font :[Enum.Font](/docs/nl-nl/reference/engine/enums/Font)

 |
|

frameSize :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Codevoorbeelden

Tekstgrootte Krijgen

```

local TextService = game:GetService("TextService")

local function getTextBounds()

	local message = "Hallo wereld!"

	local size = Vector2.new(1, 1)

	local bounds = TextService:GetTextSize(message, 12, "SourceSans", size)

	return bounds

end

print(getTextBounds())

```

Feedback geven

---

GetTextSizeOffsetAsync

Opbrengst

Mogelijkheden: UI

TextService:GetTextSizeOffsetAsync (

fontSize :[number](/docs/nl-nl/luau/numbers) , font :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

fontSize :[number](/docs/nl-nl/luau/numbers)

 |
|

font :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Krijg Tekstgrootte Offset

```

local TextService = game:GetService("TextService")

local label = script.Parent.TextLabel

-- Krijg offset aangepast voor de voorkeurstekstgrootte-instelling van de speler

local success, offset = pcall(function()

	return TextService:GetTextSizeOffsetAsync(label.TextSize, label.FontFace)

end)

if success then

	-- Pas de kernhoogte van het label aan door de offset toe te voegen

	label.Size = UDim2.fromOffset(label.Size.X.Offset, label.Size.Y.Offset + offset)

end

```

Feedback geven

---

Ga naar

▼

TextService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[FilterAndTranslateStringAsync()](#FilterAndTranslateStringAsync)

[FilterStringAsync()](#FilterStringAsync)

[GetFamilyInfoAsync()](#GetFamilyInfoAsync)

[GetTextBoundsAsync()](#GetTextBoundsAsync)

[GetTextSize()](#GetTextSize)

[GetTextSizeOffsetAsync()](#GetTextSizeOffsetAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
