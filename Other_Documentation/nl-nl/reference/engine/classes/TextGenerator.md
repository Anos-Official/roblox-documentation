<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TextGenerator -->

TextGenerator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TextGenerator](/docs/nl-nl/reference/engine/classes/TextGenerator)

Nederlands

Feedback

Engine-klasse

TextGenerator

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TextGenerator)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Seed](#Seed) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[SystemPrompt](#SystemPrompt) :[string](/docs/nl-nl/luau/strings)

 |
|

[Temperature](#Temperature) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TopP](#TopP) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GenerateTextAsync](#GenerateTextAsync) (request :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Genereer Tekst

```

local Workspace = game:GetService("Workspace")

local textGenerator = Instance.new("TextGenerator")

textGenerator.Parent = Workspace

textGenerator.SystemPrompt = "Je bent een behulpzame NPC in een virtuele wereld."

textGenerator.Temperature = 0.8

textGenerator.TopP = 0.6

textGenerator.Seed = 7

local function getResponse(userInput)

	local request = {

		UserPrompt = userInput,

		MaxTokens = 50

	}

	local success, response = pcall(function()

		return textGenerator:GenerateTextAsync(request)

	end)

	if success then

		if response then

			print("Gegenereerde Tekst: " .. response.GeneratedText)

			print("Context Token: " .. response.ContextToken)

			print("Model: " .. response.Model)

			return response

		end

	else

		warn("Tekstgeneratie mislukt: " .. tostring(response))

	end

	return nil

end

getResponse("Vertel me iets cools.")

```

---

API-referentie

Eigenschappen

Seed

Parallel lezen

Mogelijkheden: Basic

TextGenerator.Seed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SystemPrompt

Parallel lezen

Mogelijkheden: Basic

TextGenerator.SystemPrompt :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Temperature

Parallel lezen

Mogelijkheden: Basic

TextGenerator.Temperature :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TopP

Parallel lezen

Mogelijkheden: Basic

TextGenerator.TopP :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GenerateTextAsync

Opbrengst

Mogelijkheden: Basic

TextGenerator:GenerateTextAsync (request :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

request :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

Ga naar

▼

TextGenerator

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Seed](#Seed)

[SystemPrompt](#SystemPrompt)

[Temperature](#Temperature)

[TopP](#TopP)

[Methoden](#methods)

[GenerateTextAsync()](#GenerateTextAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
