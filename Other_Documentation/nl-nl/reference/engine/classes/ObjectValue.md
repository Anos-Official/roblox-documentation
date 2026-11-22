<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ObjectValue -->

ObjectValue | Documentatie - Roblox Creator Hub

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
9. [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue)

Nederlands

Feedback

Engine-klasse

ObjectValue

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ObjectValue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

ObjectValue Voorbeeld

```

local objectValue = Instance.new("ObjectValue")

objectValue.Name = "MyBaseplateReference"

objectValue.Value = workspace:FindFirstChild("Baseplate")

objectValue.Parent = workspace

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

ObjectValue.Value :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

Evenementen

Changed

ObjectValue.Changed (value :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Codevoorbeelden

ObjectValue Gewijzigd

```

local objectValue = script.Parent.ObjectValue

local part = script.Parent.Part

local function printObject(object)

	print(object:GetFullName())

end

objectValue.Changed:Connect(printObject)

objectValue.Value = part

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

ObjectValue

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
