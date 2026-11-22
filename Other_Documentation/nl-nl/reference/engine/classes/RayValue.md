<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/RayValue -->

RayValue | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/nl-nl/reference/engine/classes/ValueBase)
8. /
9. [RayValue](/docs/nl-nl/reference/engine/classes/RayValue)

Nederlands

Feedback

Engine-klasse

RayValue

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/RayValue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[Ray](/docs/nl-nl/reference/engine/datatypes/Ray)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [Ray](/docs/nl-nl/reference/engine/datatypes/Ray) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Ray](/docs/nl-nl/reference/engine/datatypes/Ray) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Stralen, RayValue en Raycasting

```

local partA = workspace.PartA

local partB = workspace.PartB

local origin = partA.Position

local direction = partB.Position - partA.Position

local ray = Ray.new(origin, direction)

local rayValue = Instance.new("RayValue")

rayValue.Value = ray

rayValue.Name = "PartA-to-PartB Ray"

rayValue.Parent = workspace

-- Raycast om eventuele onderdelen te vinden tussen PartA en PartB

local part = workspace:FindPartOnRay(ray)

if part then

	print("Raak onderdeel: " .. part:GetFullName())

else

	-- Dit zou nooit moeten gebeuren, aangezien onze ray begint bij PartA

	-- en wijst naar PartB, dus we zouden altijd PartB moeten raken

	-- of een ander onderdeel.

	print("Geen onderdeel geraakt!")

end

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

RayValue.Value :[Ray](/docs/nl-nl/reference/engine/datatypes/Ray)

Feedback geven

---

Evenementen

Changed

RayValue.Changed (value :[Ray](/docs/nl-nl/reference/engine/datatypes/Ray) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Ray](/docs/nl-nl/reference/engine/datatypes/Ray)

 |

Codevoorbeelden

Hoe RayValue.Changed te Gebruiken

```

local value = Instance.new("RayValue")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

local start = Vector3.new(0, 0, 0)

local lookAt = Vector3.new(10, 10, 10)

local ray = Ray.new(start, (lookAt - start).Unit)

value.Value = ray

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

RayValue

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Value](#Value)

[Evenementen](#events)

[Changed](#Changed)

[changed](#changed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
