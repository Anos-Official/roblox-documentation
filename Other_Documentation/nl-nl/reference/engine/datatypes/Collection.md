<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/Collection -->

Collection | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [Collection](/docs/nl-nl/reference/engine/datatypes/Collection)

Nederlands

Feedback

Engine-gegevenstype

Collection

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/Collection)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Query](#Query) :[string](/docs/nl-nl/luau/strings)

 |
|

[Root](#Root) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Methoden

|

[Destroy](#Destroy) ()

 |
|

[ForEach](#ForEach) (callback :  [function](/docs/nl-nl/luau/functions) )

 |
|

[GetCount](#GetCount) () :[number](/docs/nl-nl/luau/numbers)

 |

Codevoorbeelden

Verzameling Levenscyclus en Evenementen

```

local CollectionService = game:GetService("CollectionService")

-- Een live collectie van onderdelen gemarkeerd als "MapleLeaf" die directe kinderen zijn van een model gemarkeerd als "MapleTree"

local mapleLeaves: Collection = CollectionService:CreateCollection("Model.MapleTree > Part.MapleLeaf")

local function sway(leaf: Part, deltaTime: number)

	leaf.CFrame *= CFrame.fromEulerAnglesXYZ(0, math.rad(20) * deltaTime, 0)

end

local function fall(leaf: Part)

	leaf.Anchored = false

end

-- OnAdded wordt eenmaal aangeroepen voor elke blad die al overeenkomt, en vervolgens voor elke nieuwe overeenkomst

function mapleLeaves.OnAdded(leaf: Part)

	leaf.Material = Enum.Material.Neon

end

-- OnRemoved wordt aangeroepen wanneer een blad stopt met overeenkomen (niet-gemarkeerd, opnieuw geparent naar buiten de boom, of vernietigd)

function mapleLeaves.OnRemoved(leaf: Part)

	leaf.Material = Enum.Material.Plastic

end

-- RunService callback: wordt eenmaal per hartslag aangeroepen voor elk blad in de collectie

function mapleLeaves.OnHeartbeat(leaf: Part, deltaTime: number)

	sway(leaf, deltaTime)

end

-- Evenement callback: verbindt met BasePart.Touched op elk blad

function mapleLeaves.OnTouched(leaf: Part, other: BasePart)

	fall(leaf)

end

-- Eigenschap callback: wordt aangeroepen wanneer de kleur van een blad verandert

function mapleLeaves.OnPropertyChanged.Color(leaf: Part)

	if leaf.Color == Color3.fromRGB(124, 92, 70) then

		fall(leaf)

	end

end

-- Stel elk blad dat momenteel in de collectie is groen in

mapleLeaves:ForEach(function(leaf: Part)

	leaf.Color = Color3.fromRGB(0, 255, 0)

end)

```

---

API-referentie

Eigenschappen

Enabled

Collection.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Query

Collection.Query :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Root

Collection.Root :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

Methoden

Destroy

Collection:Destroy ()

Feedback geven

---

ForEach

Collection:ForEach (callback :[function](/docs/nl-nl/luau/functions) )

Parameters

|

callback :[function](/docs/nl-nl/luau/functions)

 |

Feedback geven

---

GetCount

Collection:GetCount () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

Collection

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Enabled](#Enabled)

[Query](#Query)

[Root](#Root)

[Methoden](#methods)

[Destroy()](#Destroy)

[ForEach()](#ForEach)

[GetCount()](#GetCount)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
