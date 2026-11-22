<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/IntValue -->

IntValue | Documentatie - Roblox Creator Hub

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
9. [IntValue](/docs/nl-nl/reference/engine/classes/IntValue)

Nederlands

Feedback

Engine-klasse

IntValue

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/IntValue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

IntValue.Value :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Evenementen

Changed

IntValue.Changed (value :[number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[number](/docs/nl-nl/luau/numbers)

 |

Codevoorbeelden

Hoe IntValue.Changed te gebruiken

```

local value = Instance.new("IntValue")

value.Parent = workspace

local function onValueChanged(newValue)

	print(newValue)

end

value.Changed:Connect(onValueChanged)

value.Value = 20

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

IntValue

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
