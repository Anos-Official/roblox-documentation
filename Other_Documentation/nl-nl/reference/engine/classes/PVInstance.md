<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PVInstance -->

PVInstance | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)

Nederlands

Feedback

Engine-klasse

PVInstance

Niet maakbaar

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PVInstance)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Origin](#Origin) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
| --- | --- |
|

[Pivot Offset](#Pivot-Offset) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |

Methoden

|

[GetPivot](#GetPivot) () :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[PivotTo](#PivotTo) (targetCFrame :  [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[Camera](/docs/nl-nl/reference/engine/classes/Camera) , [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , [Model](/docs/nl-nl/reference/engine/classes/Model)

---

API-referentie

Eigenschappen

Origin

Niet gerepliceerd

Niet scriptbaar

Parallel lezen

PVInstance.Origin :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Pivot Offset

Niet gerepliceerd

Niet scriptbaar

Parallel lezen

PVInstance.Pivot Offset :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Methoden

GetPivot

Parallel schrijven

Toegang tot simulatie

PVInstance:GetPivot () :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Teruggaves

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Codevoorbeelden

Eenvoudige Teleportatie van Personages

```

-- Deze code moet worden geplaatst in een LocalScript onder StarterPlayerScripts

local Players = game:GetService("Players")

local ContextActionService = game:GetService("ContextActionService")

local player = Players.LocalPlayer

local function doTeleport(_actionName, inputState, _inputObject)

	local character = player.Character

	if character and character.Parent and inputState == Enum.UserInputState.Begin then

		-- Verplaats het personage 10 studs vooruit in de richting waarin ze kijken

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(0, 0, -10))

	end

end

ContextActionService:BindAction("Teleport", doTeleport, true, Enum.KeyCode.F)

```

Feedback geven

---

PivotTo

Toegang tot simulatie

PVInstance:PivotTo (targetCFrame :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) ) : ()

Parameters

|

targetCFrame :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |

Teruggaves

()

Codevoorbeelden

Eenvoudige Teleportatie van Personages

```

-- Deze code moet worden geplaatst in een LocalScript onder StarterPlayerScripts

local Players = game:GetService("Players")

local ContextActionService = game:GetService("ContextActionService")

local player = Players.LocalPlayer

local function doTeleport(_actionName, inputState, _inputObject)

	local character = player.Character

	if character and character.Parent and inputState == Enum.UserInputState.Begin then

		-- Verplaats het personage 10 studs vooruit in de richting waarin ze kijken

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(0, 0, -10))

	end

end

ContextActionService:BindAction("Teleport", doTeleport, true, Enum.KeyCode.F)

```

Feedback geven

---

Ga naar

▼

PVInstance

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Origin](#Origin)

[Pivot Offset](#Pivot-Offset)

[Methoden](#methods)

[GetPivot()](#GetPivot)

[PivotTo()](#PivotTo)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
