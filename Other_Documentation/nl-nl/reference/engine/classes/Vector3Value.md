<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Vector3Value -->

Vector3Value | Documentatie - Roblox Creator Hub

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
9. [Vector3Value](/docs/nl-nl/reference/engine/classes/Vector3Value)

Nederlands

Feedback

Engine-klasse

Vector3Value

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Vector3Value)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Teleporter Deel

```

-- Plak me in een Script binnen een Deel

local part = script.Parent

local teleportPosition = part.TeleportPosition

local function onTouch(otherPart)

	-- Zoek eerst de HumanoidRootPart. Als we het niet kunnen vinden, verlaat dan.

	local hrp = otherPart.Parent:FindFirstChild("HumanoidRootPart")

	if not hrp then

		return

	end

	-- Teleporteer nu door de CFrame in te stellen op een die is gemaakt van

	-- de opgeslagen TeleportPosition

	hrp.CFrame = CFrame.new(teleportPosition.Value)

end

part.Touched:Connect(onTouch)

```

Een Vector2 opslaan in een Vector3Value

```

local vector3Value = Instance.new("Vector3Value")

-- Sla een Vector2 op in een Vector3

local vector2 = Vector2.new(42, 70)

vector3Value.Value = Vector3.new(vector2.X, vector2.Y, 0) -- De Z-waarde wordt genegeerd

-- Laad een Vector2 vanuit een Vector3

vector2 = Vector2.new(vector3Value.Value.X, vector3Value.Value.Y)

print(vector2)

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

Vector3Value.Value :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Evenementen

Changed

Vector3Value.Changed (value :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Codevoorbeelden

Hoe Vector3Value.Changed te Gebruiken

```

local value = Instance.new("Vector3Value")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

value.Value = Vector3.new(10, 10, 10)

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

Vector3Value

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
