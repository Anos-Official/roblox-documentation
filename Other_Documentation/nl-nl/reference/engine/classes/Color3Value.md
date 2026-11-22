<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Color3Value -->

Color3Value | Documentatie - Roblox Creator Hub

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
9. [Color3Value](/docs/nl-nl/reference/engine/classes/Color3Value)

Nederlands

Feedback

Engine-klasse

Color3Value

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Color3Value)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Stel Color3Value in

```

local myColor3Value = script.Parent

myColor3Value.Value = Color3.new(1, 0, 0) -- Rood

-- Je kunt ook de kleur van een BrickColor-waarde opslaan door de Color-eigenschap van BrickColor te benaderen, die een Color3 is:

local someBrickColor = BrickColor.new("Echt rood")

myColor3Value.Value = someBrickColor.Color

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

Color3Value.Value :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

Evenementen

Changed

Color3Value.Changed (value :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |

Codevoorbeelden

Hoe Color3Value.Changed te gebruiken

```

local value = Instance.new("Color3Value")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

value.Value = Color3.fromRGB(50, 50, 50)

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

Color3Value

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
