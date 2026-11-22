<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StudioService -->

StudioService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StudioService](/docs/nl-nl/reference/engine/classes/StudioService)

Nederlands

Feedback

Engine-klasse

StudioService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StudioService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[ActiveScript](#ActiveScript) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[DraggerSolveConstraints](#DraggerSolveConstraints) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[DrawConstraintsOnTop](#DrawConstraintsOnTop) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[GridSize](#GridSize) :[number](/docs/nl-nl/luau/numbers)

 |
|

[RotateIncrement](#RotateIncrement) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Secrets](#Secrets) :[string](/docs/nl-nl/luau/strings)

 |
|

[ShowConstraintDetails](#ShowConstraintDetails) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[ShowWeldDetails](#ShowWeldDetails) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[StudioLocaleId](#StudioLocaleId) :[string](/docs/nl-nl/luau/strings)

 |
|

[UseLocalSpace](#UseLocalSpace) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[GetClassIcon](#GetClassIcon) (className :  [string](/docs/nl-nl/luau/strings) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetUserId](#GetUserId) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[PromptImportFile](#PromptImportFile) (fileTypeFilter :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
|

[PromptImportFileAsync](#PromptImportFileAsync) (fileTypeFilter :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[PromptImportFiles](#PromptImportFiles) (fileTypeFilter :  [{any}](/docs/nl-nl/luau/tables#arrays) ) : Instances

Verouderd

 |
|

[PromptImportFilesAsync](#PromptImportFilesAsync) (fileTypeFilter :  [{any}](/docs/nl-nl/luau/tables#arrays) ) : Instances

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

ActiveScript

Alleen-lezen

Niet gerepliceerd

Parallel lezen

StudioService.ActiveScript :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

Actief Script

```

local StudioService = game:GetService("StudioService")

local startTime = os.time()

local activeScript

local function onActiveScriptChanged()

  local newActiveScript = StudioService.ActiveScript

	if activeScript and newActiveScript ~= activeScript then

		local deltaTime = os.time() - startTime

		print(("Je hebt %s bewerkt voor %d:%2.d"):format(activeScript.Name, deltaTime // 60, deltaTime % 60))

	end

	startTime = os.time()

	activeScript = newActiveScript

end

StudioService:GetPropertyChangedSignal("ActiveScript"):Connect(onActiveScriptChanged)

```

Feedback geven

---

DraggerSolveConstraints

Alleen-lezen

Niet gerepliceerd

Parallel lezen

StudioService.DraggerSolveConstraints :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

DrawConstraintsOnTop

Verouderd

Details weergeven

---

GridSize

Alleen-lezen

Niet gerepliceerd

Parallel lezen

StudioService.GridSize :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

RotateIncrement

Alleen-lezen

Niet gerepliceerd

Parallel lezen

StudioService.RotateIncrement :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Secrets

Roblox-scriptbeveiliging

Parallel lezen

StudioService.Secrets :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

ShowConstraintDetails

Alleen-lezen

Niet gerepliceerd

Parallel lezen

StudioService.ShowConstraintDetails :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

ShowWeldDetails

Alleen-lezen

Niet gerepliceerd

Roblox-scriptbeveiliging

Parallel lezen

StudioService.ShowWeldDetails :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

StudioLocaleId

Alleen-lezen

Niet gerepliceerd

Parallel lezen

StudioService.StudioLocaleId :[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Studio Locale Id

```

local locale = game:GetService("StudioService").StudioLocaleId

if locale == "en_US" then

	print("Hallo, jullie")

elseif locale == "en_GB" then

	print("'Ello, gov'na")

elseif locale:sub(1, 2) == "en" then

	print("Hallo")

elseif locale == "fr_FR" then

	print("Bonjour")

end

```

Feedback geven

---

UseLocalSpace

Niet gerepliceerd

Parallel lezen

StudioService.UseLocalSpace :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

GetClassIcon

Plugin-beveiliging

StudioService:GetClassIcon (className :[string](/docs/nl-nl/luau/strings) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

GetUserId

Plugin-beveiliging

StudioService:GetUserId () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

StudioService:GetUserId

```

-- Kan alleen in een plugin worden gebruikt

local StudioService = game:GetService("StudioService")

local Players = game:GetService("Players")

local loggedInUserId = StudioService:GetUserId()

local loggedInUserName = Players:GetNameFromUserIdAsync(loggedInUserId)

print("Hallo,", loggedInUserName)

```

Feedback geven

---

PromptImportFile

Verouderd

Details weergeven

---

PromptImportFileAsync

Opbrengst

Plugin-beveiliging

StudioService:PromptImportFileAsync (fileTypeFilter :[{any}](/docs/nl-nl/luau/tables#arrays) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

fileTypeFilter :[{any}](/docs/nl-nl/luau/tables#arrays)

Standaardwaarde: {} |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

PromptImportFiles

Verouderd

Details weergeven

---

PromptImportFilesAsync

Opbrengst

Plugin-beveiliging

StudioService:PromptImportFilesAsync (fileTypeFilter :[{any}](/docs/nl-nl/luau/tables#arrays) ) : Instances

Parameters

|

fileTypeFilter :[{any}](/docs/nl-nl/luau/tables#arrays)

Standaardwaarde: {} |

Teruggaves

Instances

Feedback geven

---

Ga naar

▼

StudioService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[ActiveScript](#ActiveScript)

[DraggerSolveConstraints](#DraggerSolveConstraints)

[DrawConstraintsOnTop](#DrawConstraintsOnTop)

[GridSize](#GridSize)

[RotateIncrement](#RotateIncrement)

[Secrets](#Secrets)

[ShowConstraintDetails](#ShowConstraintDetails)

[ShowWeldDetails](#ShowWeldDetails)

[StudioLocaleId](#StudioLocaleId)

[UseLocalSpace](#UseLocalSpace)

[Methoden](#methods)

[GetClassIcon()](#GetClassIcon)

[GetUserId()](#GetUserId)

[PromptImportFile()](#PromptImportFile)

[PromptImportFileAsync()](#PromptImportFileAsync)

[PromptImportFiles()](#PromptImportFiles)

[PromptImportFilesAsync()](#PromptImportFilesAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
