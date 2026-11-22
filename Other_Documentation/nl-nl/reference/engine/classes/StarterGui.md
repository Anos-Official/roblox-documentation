<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StarterGui -->

StarterGui | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [BasePlayerGui](/docs/nl-nl/reference/engine/classes/BasePlayerGui)
8. /
9. [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)

Nederlands

Feedback

Engine-klasse

StarterGui

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StarterGui)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[ClipsDescendantsSupportsRotation](#ClipsDescendantsSupportsRotation) :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

 |
| --- | --- |
|

[ProcessUserInput](#ProcessUserInput) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[ResetPlayerGuiOnSpawn](#ResetPlayerGuiOnSpawn) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[RtlTextSupport](#RtlTextSupport) :[Enum.RtlTextSupport](/docs/nl-nl/reference/engine/enums/RtlTextSupport)

 |
|

[ScreenOrientation](#ScreenOrientation) :[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation)

 |
|

[ShowDevelopmentGui](#ShowDevelopmentGui) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[VirtualCursorMode](#VirtualCursorMode) :[Enum.VirtualCursorMode](/docs/nl-nl/reference/engine/enums/VirtualCursorMode)

 |

Methoden

|

[GetCore](#GetCore) (parameterName :  [string](/docs/nl-nl/luau/strings) ) : Variant

 |
|

[GetCoreGuiEnabled](#GetCoreGuiEnabled) (coreGuiType :  [Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[SetCore](#SetCore) (parameterName :  [string](/docs/nl-nl/luau/strings) , value :  Variant ) : ()

 |
|

[SetCoreGuiEnabled](#SetCoreGuiEnabled) (coreGuiType :  [Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType) , enabled :  [boolean](/docs/nl-nl/luau/booleans) ) : ()

 |

Overgenomen leden

1  overgenomen van [BasePlayerGui](/docs/nl-nl/reference/engine/classes/BasePlayerGui)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

ClipsDescendantsSupportsRotation

Niet scriptbaar

Parallel lezen

Mogelijkheden: UI

StarterGui.ClipsDescendantsSupportsRotation :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

Feedback geven

---

ProcessUserInput

Verborgen

Niet gerepliceerd

Plugin-beveiliging

Parallel lezen

Mogelijkheden: UI

StarterGui.ProcessUserInput :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

ResetPlayerGuiOnSpawn

Verouderd

Details weergeven

---

RtlTextSupport

Niet scriptbaar

Parallel lezen

Mogelijkheden: UI

StarterGui.RtlTextSupport :[Enum.RtlTextSupport](/docs/nl-nl/reference/engine/enums/RtlTextSupport)

Feedback geven

---

ScreenOrientation

Parallel lezen

Mogelijkheden: UI

StarterGui.ScreenOrientation :[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation)

Feedback geven

---

ShowDevelopmentGui

Parallel lezen

Mogelijkheden: UI

StarterGui.ShowDevelopmentGui :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

VirtualCursorMode

Niet scriptbaar

Parallel lezen

Mogelijkheden: UI

StarterGui.VirtualCursorMode :[Enum.VirtualCursorMode](/docs/nl-nl/reference/engine/enums/VirtualCursorMode)

Feedback geven

---

Methoden

GetCore

Opbrengst

Mogelijkheden: UI

StarterGui:GetCore (parameterName :[string](/docs/nl-nl/luau/strings) ) : Variant

Parameters

|

parameterName :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

Variant

Feedback geven

---

GetCoreGuiEnabled

Mogelijkheden: UI

StarterGui:GetCoreGuiEnabled (coreGuiType :[Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

coreGuiType :[Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Controleren of een Core GUI is ingeschakeld

```

local StarterGui = game:GetService("StarterGui")

print(StarterGui:GetCoreGuiEnabled("PlayerList"))

```

Feedback geven

---

SetCore

Mogelijkheden: UI

StarterGui:SetCore (

parameterName :[string](/docs/nl-nl/luau/strings) , value : Variant

) : ()

Parameters

|

parameterName :[string](/docs/nl-nl/luau/strings)

 |
|

value : Variant

 |

Teruggaves

()

Codevoorbeelden

StarterGui Instellingen Kern GUI

```

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCore("AvatarContextMenuTheme", {

	BackgroundImage = "",

	BackgroundTransparency = 0.5,

	BackgroundColor = Color3.fromRGB(111, 145, 242),

	NameTagColor = Color3.fromRGB(0, 0, 200),

	NameUnderlineColor = Color3.fromRGB(213, 233, 255),

	ButtonFrameColor = Color3.fromRGB(15, 24, 65),

	ButtonFrameTransparency = 0.2,

	ButtonUnderlineColor = Color3.fromRGB(213, 233, 255),

	Font = Enum.Font.SciFi,

})

```

Feedback geven

---

SetCoreGuiEnabled

Mogelijkheden: UI

StarterGui:SetCoreGuiEnabled (

coreGuiType :[Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType) , enabled :[boolean](/docs/nl-nl/luau/booleans)

) : ()

Parameters

|

coreGuiType :[Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType)

 |
|

enabled :[boolean](/docs/nl-nl/luau/booleans)

 |

Teruggaves

()

Feedback geven

---

Ga naar

▼

StarterGui

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[ClipsDescendantsSupportsRotation](#ClipsDescendantsSupportsRotation)

[ProcessUserInput](#ProcessUserInput)

[ResetPlayerGuiOnSpawn](#ResetPlayerGuiOnSpawn)

[RtlTextSupport](#RtlTextSupport)

[ScreenOrientation](#ScreenOrientation)

[ShowDevelopmentGui](#ShowDevelopmentGui)

[VirtualCursorMode](#VirtualCursorMode)

[Methoden](#methods)

[GetCore()](#GetCore)

[GetCoreGuiEnabled()](#GetCoreGuiEnabled)

[SetCore()](#SetCore)

[SetCoreGuiEnabled()](#SetCoreGuiEnabled)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
