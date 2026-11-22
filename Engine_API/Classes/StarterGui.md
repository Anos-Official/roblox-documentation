<!-- Source: https://create.roblox.com/docs/reference/engine/classes/StarterGui -->

StarterGui | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StarterGui.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [BasePlayerGui](/docs/reference/engine/classes/BasePlayerGui)
8. /
9. [StarterGui](/docs/reference/engine/classes/StarterGui)

English

Feedback

Engine Class

StarterGui

Not Creatable

Service

---

## Summary

Properties

|

[ClipsDescendantsSupportsRotation](#ClipsDescendantsSupportsRotation) :[Enum.RolloutState](/docs/reference/engine/enums/RolloutState)

 |
| --- | --- |
|

[ProcessUserInput](#ProcessUserInput) :[boolean](/docs/luau/booleans)

 |
|

[ResetPlayerGuiOnSpawn](#ResetPlayerGuiOnSpawn) :[boolean](/docs/luau/booleans)

Deprecated

 |
|

[RtlTextSupport](#RtlTextSupport) :[Enum.RtlTextSupport](/docs/reference/engine/enums/RtlTextSupport)

 |
|

[ScreenOrientation](#ScreenOrientation) :[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation)

 |
|

[ShowDevelopmentGui](#ShowDevelopmentGui) :[boolean](/docs/luau/booleans)

 |
|

[VirtualCursorMode](#VirtualCursorMode) :[Enum.VirtualCursorMode](/docs/reference/engine/enums/VirtualCursorMode)

 |

Methods

|

[GetCore](#GetCore) (parameterName :  [string](/docs/luau/strings) ) : Variant

 |
|

[GetCoreGuiEnabled](#GetCoreGuiEnabled) (coreGuiType :  [Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType) ) :[boolean](/docs/luau/booleans)

 |
|

[SetCore](#SetCore) (parameterName :  [string](/docs/luau/strings) , value :  Variant ) : ()

 |
|

[SetCoreGuiEnabled](#SetCoreGuiEnabled) (coreGuiType :  [Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType) , enabled :  [boolean](/docs/luau/booleans) ) : ()

 |

Inherited Members

1  inherited from [BasePlayerGui](/docs/reference/engine/classes/BasePlayerGui)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

ClipsDescendantsSupportsRotation

Not Scriptable

Read Parallel

Capabilities: UI

StarterGui.ClipsDescendantsSupportsRotation :[Enum.RolloutState](/docs/reference/engine/enums/RolloutState)

Provide feedback

---

ProcessUserInput

Hidden

Not Replicated

Plugin Security

Read Parallel

Capabilities: UI

StarterGui.ProcessUserInput :[boolean](/docs/luau/booleans)

Provide feedback

---

ResetPlayerGuiOnSpawn

Deprecated

Show details

---

RtlTextSupport

Not Scriptable

Read Parallel

Capabilities: UI

StarterGui.RtlTextSupport :[Enum.RtlTextSupport](/docs/reference/engine/enums/RtlTextSupport)

Provide feedback

---

ScreenOrientation

Read Parallel

Capabilities: UI

StarterGui.ScreenOrientation :[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation)

Provide feedback

---

ShowDevelopmentGui

Read Parallel

Capabilities: UI

StarterGui.ShowDevelopmentGui :[boolean](/docs/luau/booleans)

Provide feedback

---

VirtualCursorMode

Not Scriptable

Read Parallel

Capabilities: UI

StarterGui.VirtualCursorMode :[Enum.VirtualCursorMode](/docs/reference/engine/enums/VirtualCursorMode)

Provide feedback

---

Methods

GetCore

Yields

Capabilities: UI

StarterGui:GetCore (parameterName :[string](/docs/luau/strings) ) : Variant

Parameters

|

parameterName :[string](/docs/luau/strings)

 |

Returns

Variant

Provide feedback

---

GetCoreGuiEnabled

Capabilities: UI

StarterGui:GetCoreGuiEnabled (coreGuiType :[Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType) ) :[boolean](/docs/luau/booleans)

Parameters

|

coreGuiType :[Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType)

 |

Returns

[boolean](/docs/luau/booleans)

Code Samples

Checking if a Core GUI is Enabled

```

local StarterGui = game:GetService("StarterGui")

print(StarterGui:GetCoreGuiEnabled("PlayerList"))

```

Provide feedback

---

SetCore

Capabilities: UI

StarterGui:SetCore (

parameterName :[string](/docs/luau/strings) , value : Variant

) : ()

Parameters

|

parameterName :[string](/docs/luau/strings)

 |
|

value : Variant

 |

Returns

()

Code Samples

StarterGui Setting Core GUI

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

Provide feedback

---

SetCoreGuiEnabled

Capabilities: UI

StarterGui:SetCoreGuiEnabled (

coreGuiType :[Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType) , enabled :[boolean](/docs/luau/booleans)

) : ()

Parameters

|

coreGuiType :[Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType)

 |
|

enabled :[boolean](/docs/luau/booleans)

 |

Returns

()

Provide feedback

---

Jump to

▼

StarterGui

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[ClipsDescendantsSupportsRotation](#ClipsDescendantsSupportsRotation)

[ProcessUserInput](#ProcessUserInput)

[ResetPlayerGuiOnSpawn](#ResetPlayerGuiOnSpawn)

[RtlTextSupport](#RtlTextSupport)

[ScreenOrientation](#ScreenOrientation)

[ShowDevelopmentGui](#ShowDevelopmentGui)

[VirtualCursorMode](#VirtualCursorMode)

[Methods](#methods)

[GetCore()](#GetCore)

[GetCoreGuiEnabled()](#GetCoreGuiEnabled)

[SetCore()](#SetCore)

[SetCoreGuiEnabled()](#SetCoreGuiEnabled)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
