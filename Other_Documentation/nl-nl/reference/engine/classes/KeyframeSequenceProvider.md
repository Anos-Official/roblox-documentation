<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/KeyframeSequenceProvider -->

KeyframeSequenceProvider | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [KeyframeSequenceProvider](/docs/nl-nl/reference/engine/classes/KeyframeSequenceProvider)

Nederlands

Feedback

Engine-klasse

KeyframeSequenceProvider

Verouderd

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/KeyframeSequenceProvider)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetAnimations](#GetAnimations) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
| --- | --- |
|

[GetAnimationsAsync](#GetAnimationsAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[GetKeyframeSequence](#GetKeyframeSequence) (assetId :  ContentId ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
|

[GetKeyframeSequenceAsync](#GetKeyframeSequenceAsync) (assetId :  ContentId ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[GetKeyframeSequenceById](#GetKeyframeSequenceById) (assetId :  [number](/docs/nl-nl/luau/numbers) , useCache :  [boolean](/docs/nl-nl/luau/booleans) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
|

[RegisterActiveKeyframeSequence](#RegisterActiveKeyframeSequence) (keyframeSequence :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ContentId

 |
|

[RegisterKeyframeSequence](#RegisterKeyframeSequence) (keyframeSequence :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ContentId

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Maak tijdelijke animatie

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local function createPreviewAnimation(keyframeSequence)

	local hashId = KeyframeSequenceProvider:RegisterKeyframeSequence(keyframeSequence)

	local Animation = Instance.new("Animation")

	Animation.AnimationId = hashId

	return Animation

end

local keyframeSequence = Instance.new("KeyframeSequence")

local animation = createPreviewAnimation(keyframeSequence)

print(animation)

```

---

API-referentie

Methoden

GetAnimations

Verouderd

Details weergeven

---

GetAnimationsAsync

Opbrengst

Mogelijkheden: Animation

KeyframeSequenceProvider:GetAnimationsAsync (userId :[User](/docs/nl-nl/reference/engine/datatypes/User) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

KeyframeSequenceProvider GetAnimationsAsync

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local USER_ID = 0 -- Voer hier je UserId in

local function extractPages(pagesObject)

	local array = {}

	while true do

		local thisPage = pagesObject:GetCurrentPage()

		for _, v in pairs(thisPage) do

			table.insert(array, v)

		end

		if pagesObject.IsFinished then

			break

		end

		pagesObject:AdvanceToNextPageAsync()

	end

	return array

end

local inventoryPages = KeyframeSequenceProvider:GetAnimationsAsync(USER_ID)

local animationIds = extractPages(inventoryPages)

for _, id in pairs(animationIds) do

	print(id)

end

print("totaal: ", #animationIds)

```

Feedback geven

---

GetKeyframeSequence

Verouderd

Details weergeven

---

GetKeyframeSequenceAsync

Opbrengst

Mogelijkheden: Animation

KeyframeSequenceProvider:GetKeyframeSequenceAsync (assetId : ContentId ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

assetId : ContentId

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

Een animatie's KeyframeSequence ophalen

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local ANIMATION_ID = "rbxassetid://507771019"

-- Haal de keyframe sequence voor het asset op

local keyframeSequence

local success, err = pcall(function()

	keyframeSequence = KeyframeSequenceProvider:GetKeyframeSequenceAsync(ANIMATION_ID)

end)

if success then

	-- Itereer over elke keyframe en druk de tijdwaarde af

	local keyframeTable = keyframeSequence:GetKeyframes()

	for key, value in keyframeTable do

		print(`De tijd van keyframe nummer {key} is: {value.Time}`)

	end

else

	print(`Fout bij het ophalen van KeyframeSequence: {err}`)

end

```

Feedback geven

---

GetKeyframeSequenceById

Verouderd

Details weergeven

---

RegisterActiveKeyframeSequence

Mogelijkheden: Animation

KeyframeSequenceProvider:RegisterActiveKeyframeSequence (keyframeSequence :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ContentId

Parameters

|

keyframeSequence :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

ContentId

Codevoorbeelden

Maak tijdelijke animatie

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local function createPreviewAnimation(keyframeSequence)

	local hashId = KeyframeSequenceProvider:RegisterKeyframeSequence(keyframeSequence)

	local Animation = Instance.new("Animation")

	Animation.AnimationId = hashId

	return Animation

end

local keyframeSequence = Instance.new("KeyframeSequence")

local animation = createPreviewAnimation(keyframeSequence)

print(animation)

```

Feedback geven

---

RegisterKeyframeSequence

Mogelijkheden: Animation

KeyframeSequenceProvider:RegisterKeyframeSequence (keyframeSequence :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ContentId

Parameters

|

keyframeSequence :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

ContentId

Codevoorbeelden

KeyframeSequenceProvider:RegisterKeyframeSequence

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local asset = KeyframeSequenceProvider:RegisterKeyframeSequence(workspace.KeyframeSequence)

local animation = Instance.new("Animation")

animation.Name = "TestAnimatie"

animation.AnimationId = asset

animation.Parent = workspace

```

Feedback geven

---

Ga naar

▼

KeyframeSequenceProvider

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetAnimations()](#GetAnimations)

[GetAnimationsAsync()](#GetAnimationsAsync)

[GetKeyframeSequence()](#GetKeyframeSequence)

[GetKeyframeSequenceAsync()](#GetKeyframeSequenceAsync)

[GetKeyframeSequenceById()](#GetKeyframeSequenceById)

[RegisterActiveKeyframeSequence()](#RegisterActiveKeyframeSequence)

[RegisterKeyframeSequence()](#RegisterKeyframeSequence)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
