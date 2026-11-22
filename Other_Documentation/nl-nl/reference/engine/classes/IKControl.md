<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/IKControl -->

IKControl | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)

Nederlands

Feedback

Engine-klasse

IKControl

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/IKControl)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[ChainRoot](#ChainRoot) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[EndEffector](#EndEffector) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[EndEffectorOffset](#EndEffectorOffset) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[Offset](#Offset) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[Pole](#Pole) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[Priority](#Priority) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SmoothTime](#SmoothTime) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Target](#Target) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[Type](#Type) :[Enum.IKControlType](/docs/nl-nl/reference/engine/enums/IKControlType)

 |
|

[Weight](#Weight) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GetChainCount](#GetChainCount) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetChainLength](#GetChainLength) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetNodeLocalCFrame](#GetNodeLocalCFrame) (index :  [number](/docs/nl-nl/luau/numbers) ) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[GetNodeWorldCFrame](#GetNodeWorldCFrame) (index :  [number](/docs/nl-nl/luau/numbers) ) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[GetRawFinalTarget](#GetRawFinalTarget) () :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[GetSmoothedFinalTarget](#GetSmoothedFinalTarget) () :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

IKControl setup

```

local character = script.Parent.Character

local humanoid = character.Humanoid

local root = character.HumanoidRootPart

-- Maak een nieuwe attachment om te gebruiken als de IKControl.Target

local target = Instance.new("Attachment")

target.CFrame = CFrame.new(-1, 0, -1)

target.Parent = root

local ikControl = Instance.new("IKControl")

ikControl.Type = Enum.IKControlType.Position

ikControl.EndEffector = character.LeftHand

ikControl.ChainRoot = character.LeftUpperArm

ikControl.Target = target

ikControl.Parent = humanoid

```

---

API-referentie

Eigenschappen

ChainRoot

Parallel lezen

Mogelijkheden: Animation

Toegang tot simulatie

IKControl.ChainRoot :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Animation

Toegang tot simulatie

IKControl.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

EndEffector

Parallel lezen

Mogelijkheden: Animation

Toegang tot simulatie

IKControl.EndEffector :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

EndEffectorOffset

Parallel lezen

Mogelijkheden: Animation

IKControl.EndEffectorOffset :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Offset

Parallel lezen

Mogelijkheden: Animation

IKControl.Offset :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Pole

Parallel lezen

Mogelijkheden: Animation

IKControl.Pole :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

Priority

Parallel lezen

Mogelijkheden: Animation

IKControl.Priority :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SmoothTime

Parallel lezen

Mogelijkheden: Animation

IKControl.SmoothTime :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Target

Parallel lezen

Mogelijkheden: Animation

Toegang tot simulatie

IKControl.Target :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

Type

Parallel lezen

Mogelijkheden: Animation

Toegang tot simulatie

IKControl.Type :[Enum.IKControlType](/docs/nl-nl/reference/engine/enums/IKControlType)

Feedback geven

---

Weight

Parallel lezen

Mogelijkheden: Animation

Toegang tot simulatie

IKControl.Weight :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetChainCount

Mogelijkheden: Animation

IKControl:GetChainCount () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetChainLength

Mogelijkheden: Animation

IKControl:GetChainLength () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetNodeLocalCFrame

Mogelijkheden: Animation

IKControl:GetNodeLocalCFrame (index :[number](/docs/nl-nl/luau/numbers) ) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

GetNodeWorldCFrame

Mogelijkheden: Animation

IKControl:GetNodeWorldCFrame (index :[number](/docs/nl-nl/luau/numbers) ) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

GetRawFinalTarget

Mogelijkheden: Animation

IKControl:GetRawFinalTarget () :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Teruggaves

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

GetSmoothedFinalTarget

Mogelijkheden: Animation

IKControl:GetSmoothedFinalTarget () :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Teruggaves

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Ga naar

▼

IKControl

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[ChainRoot](#ChainRoot)

[Enabled](#Enabled)

[EndEffector](#EndEffector)

[EndEffectorOffset](#EndEffectorOffset)

[Offset](#Offset)

[Pole](#Pole)

[Priority](#Priority)

[SmoothTime](#SmoothTime)

[Target](#Target)

[Type](#Type)

[Weight](#Weight)

[Methoden](#methods)

[GetChainCount()](#GetChainCount)

[GetChainLength()](#GetChainLength)

[GetNodeLocalCFrame()](#GetNodeLocalCFrame)

[GetNodeWorldCFrame()](#GetNodeWorldCFrame)

[GetRawFinalTarget()](#GetRawFinalTarget)

[GetSmoothedFinalTarget()](#GetSmoothedFinalTarget)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
