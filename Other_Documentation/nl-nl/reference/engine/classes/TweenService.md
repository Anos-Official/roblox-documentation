<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TweenService -->

TweenService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)

Nederlands

Feedback

Engine-klasse

TweenService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TweenService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[Create](#Create) (instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , tweenInfo :  [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo) , propertyTable :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Tween](/docs/nl-nl/reference/engine/classes/Tween)

 |
| --- | --- |
|

[GetValue](#GetValue) (alpha :  [number](/docs/nl-nl/luau/numbers) , easingStyle :  [Enum.EasingStyle](/docs/nl-nl/reference/engine/enums/EasingStyle) , easingDirection :  [Enum.EasingDirection](/docs/nl-nl/reference/engine/enums/EasingDirection) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SmoothDamp](#SmoothDamp) (current :  Variant , target :  Variant , velocity :  Variant , smoothTime :  [number](/docs/nl-nl/luau/numbers) , maxSpeed :  [number](/docs/nl-nl/luau/numbers) ? , dt :  [number](/docs/nl-nl/luau/numbers) ? ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Tween Creatie

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Color = Color3.new(1, 0, 0)

part.Anchored = true

part.Parent = game.Workspace

local goal = {}

goal.Position = Vector3.new(10, 10, 0)

goal.Color = Color3.new(0, 1, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

```

Een Tween Lussen

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local tweenInfo = TweenInfo.new(

	2, -- Tijd

	Enum.EasingStyle.Linear, -- EasingStyle

	Enum.EasingDirection.Out, -- EasingDirection

	-1, -- RepeatCount (wanneer minder dan nul, zal de tween oneindig lussen)

	true, -- Reverses (tween zal omkeren zodra het zijn doel bereikt)

	0 -- DelayTime

)

local tween = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

tween:Play()

task.wait(10)

tween:Cancel() -- annuleer de animatie na 10 seconden

```

Een Tween Pauzeren

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.BrickColor = BrickColor.new("Heldere groen")

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(50, 10, 0)

local tweenInfo = TweenInfo.new(10, Enum.EasingStyle.Linear)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

task.wait(3)

part.BrickColor = BrickColor.new("Heldere rood")

tween:Pause()

task.wait(2)

part.BrickColor = BrickColor.new("Heldere groen")

tween:Play()

```

---

API-referentie

Methoden

Create

Mogelijkheden: Basic

TweenService:Create (

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , tweenInfo :[TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo) , propertyTable :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[Tween](/docs/nl-nl/reference/engine/classes/Tween)

Parameters

|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

tweenInfo :[TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)

 |
|

propertyTable :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

[Tween](/docs/nl-nl/reference/engine/classes/Tween)

Codevoorbeelden

Tween Creatie

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Color = Color3.new(1, 0, 0)

part.Anchored = true

part.Parent = game.Workspace

local goal = {}

goal.Position = Vector3.new(10, 10, 0)

goal.Color = Color3.new(0, 1, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

```

Een Tween Lussen

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local tweenInfo = TweenInfo.new(

	2, -- Tijd

	Enum.EasingStyle.Linear, -- EasingStyle

	Enum.EasingDirection.Out, -- EasingDirection

	-1, -- RepeatCount (wanneer minder dan nul, zal de tween oneindig lussen)

	true, -- Reverses (tween zal omkeren zodra het zijn doel bereikt)

	0 -- DelayTime

)

local tween = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

tween:Play()

task.wait(10)

tween:Cancel() -- annuleer de animatie na 10 seconden

```

Feedback geven

---

GetValue

Parallel schrijven

Mogelijkheden: Basic

Toegang tot simulatie

TweenService:GetValue (

alpha :[number](/docs/nl-nl/luau/numbers) , easingStyle :[Enum.EasingStyle](/docs/nl-nl/reference/engine/enums/EasingStyle) , easingDirection :[Enum.EasingDirection](/docs/nl-nl/reference/engine/enums/EasingDirection)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

alpha :[number](/docs/nl-nl/luau/numbers)

 |
|

easingStyle :[Enum.EasingStyle](/docs/nl-nl/reference/engine/enums/EasingStyle)

 |
|

easingDirection :[Enum.EasingDirection](/docs/nl-nl/reference/engine/enums/EasingDirection)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SmoothDamp

Parallel schrijven

Mogelijkheden: Basic

Toegang tot simulatie

TweenService:SmoothDamp (

current : Variant , target : Variant , velocity : Variant , smoothTime :[number](/docs/nl-nl/luau/numbers) , maxSpeed :[number](/docs/nl-nl/luau/numbers) ? , dt :[number](/docs/nl-nl/luau/numbers) ?

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

current : Variant

 |
|

target : Variant

 |
|

velocity : Variant

 |
|

smoothTime :[number](/docs/nl-nl/luau/numbers)

 |
|

maxSpeed :[number](/docs/nl-nl/luau/numbers) ?

 |
|

dt :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

Ga naar

▼

TweenService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[Create()](#Create)

[GetValue()](#GetValue)

[SmoothDamp()](#SmoothDamp)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
