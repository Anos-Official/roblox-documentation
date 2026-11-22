<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ExperienceNotificationService -->

ExperienceNotificationService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ExperienceNotificationService](/docs/nl-nl/reference/engine/classes/ExperienceNotificationService)

Nederlands

Feedback

Engine-klasse

ExperienceNotificationService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ExperienceNotificationService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CanPromptOptInAsync](#CanPromptOptInAsync) () :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[PromptOptIn](#PromptOptIn) () : ()

 |

Evenementen

|

[OptInPromptClosed](#OptInPromptClosed) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

CanPromptOptInAsync

Opbrengst

Mogelijkheden: Players, Social

ExperienceNotificationService:CanPromptOptInAsync () :[boolean](/docs/nl-nl/luau/booleans)

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

LokaleScript - Implementatie van de Meldingsmachtigingsprompt

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Functie om te controleren of de speler kan worden gevraagd om meldingen in te schakelen

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Luister naar het evenement wanneer de opt-in prompt is gesloten

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt gesloten")

end)

```

Feedback geven

---

PromptOptIn

Mogelijkheden: Players, Social

ExperienceNotificationService:PromptOptIn () : ()

Teruggaves

()

Codevoorbeelden

LokaleScript - Implementatie van de Meldingsmachtigingsprompt

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Functie om te controleren of de speler kan worden gevraagd om meldingen in te schakelen

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Luister naar het evenement wanneer de opt-in prompt is gesloten

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt gesloten")

end)

```

Feedback geven

---

Evenementen

OptInPromptClosed

Mogelijkheden: Players, Social

ExperienceNotificationService.OptInPromptClosed () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

LokaleScript - Implementatie van de Meldingsmachtigingsprompt

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Functie om te controleren of de speler kan worden gevraagd om meldingen in te schakelen

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Luister naar het evenement wanneer de opt-in prompt is gesloten

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt gesloten")

end)

```

Feedback geven

---

Ga naar

▼

ExperienceNotificationService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[CanPromptOptInAsync()](#CanPromptOptInAsync)

[PromptOptIn()](#PromptOptIn)

[Evenementen](#events)

[OptInPromptClosed](#OptInPromptClosed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
