<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Tween -->

Tween | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TweenBase](/docs/nl-nl/reference/engine/classes/TweenBase)
8. /
9. [Tween](/docs/nl-nl/reference/engine/classes/Tween)

Nederlands

Feedback

Engine-klasse

Tween

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Tween)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Instance](#Instance) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[TweenInfo](#TweenInfo) :[TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)

 |

Overgenomen leden

5  overgenomen van [TweenBase](/docs/nl-nl/reference/engine/classes/TweenBase)

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

---

API-referentie

Eigenschappen

Instance

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Tween.Instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

Tween Instantie

```

local TweenService = game:GetService("TweenService")

local function isInstanceAPart(tween)

	local instance = tween.Instance

	return instance:IsA("BasePart")

end

local tweenInfo = TweenInfo.new()

local instance = Instance.new("Part")

local tween = TweenService:Create(instance, tweenInfo, {

	Transparency = 1,

})

print(isInstanceAPart(tween))

```

Feedback geven

---

TweenInfo

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Tween.TweenInfo :[TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)

Codevoorbeelden

TweenInfo Voorbeelden

```

-- Een TweenInfo met alle standaardparameters

TweenInfo.new()

-- Een TweenInfo met zijn tijd ingesteld op 0,5 seconden.

TweenInfo.new(0.5)

-- Een TweenInfo met zijn easing-stijl ingesteld op Back.

TweenInfo.new(0.5, Enum.EasingStyle.Back)

-- Een TweenInfo met zijn easing-richting ingesteld op In.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In)

-- Een TweenInfo die zichzelf 4 keer herhaalt.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, 4)

-- Een TweenInfo die zijn interpolatie omkeert nadat het zijn doel heeft bereikt.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, 4, true)

-- Een TweenInfo die oneindig loopt.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, -1, true)

-- Een TweenInfo met een vertraging van 1 seconde tussen elke interpolatie.

TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.In, 4, true, 1)

```

Feedback geven

---

Ga naar

▼

Tween

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Instance](#Instance)

[TweenInfo](#TweenInfo)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
