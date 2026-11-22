<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/WeldConstraint -->

WeldConstraint | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)

Nederlands

Feedback

Engine-klasse

WeldConstraint

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/WeldConstraint)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Active](#Active) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Part0](#Part0) :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

 |
|

[Part1](#Part1) :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Active

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Physics

Toegang tot simulatie

WeldConstraint.Active :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Enabled

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Physics

Toegang tot simulatie

WeldConstraint.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Part0

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Physics

Toegang tot simulatie

WeldConstraint.Part0 :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

Codevoorbeelden

Deel0

```

local Workspace = game:GetService("Workspace")

local partA = Instance.new("Part")

local partB = Instance.new("Part")

partA.Position = Vector3.new(0, 10, 0)

partA.Parent = Workspace

partB.Position = Vector3.new(0, 10, 10)

partB.Parent = Workspace

local weld = Instance.new("WeldConstraint")

weld.Part0 = partA

weld.Part1 = partB

weld.Parent = partA

```

Feedback geven

---

Part1

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Physics

Toegang tot simulatie

WeldConstraint.Part1 :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

Codevoorbeelden

Deel1

```

local Workspace = game:GetService("Workspace")

local partA = Instance.new("Part")

local partB = Instance.new("Part")

partA.Position = Vector3.new(0, 10, 0)

partA.Parent = Workspace

partB.Position = Vector3.new(0, 10, 10)

partB.Parent = Workspace

local weld = Instance.new("WeldConstraint")

weld.Part0 = partA

weld.Part1 = partB

weld.Parent = partA

```

Feedback geven

---

Ga naar

▼

WeldConstraint

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Active](#Active)

[Enabled](#Enabled)

[Part0](#Part0)

[Part1](#Part1)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
