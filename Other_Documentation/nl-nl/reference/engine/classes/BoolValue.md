<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/BoolValue -->

BoolValue | Documentatie - Roblox Creator Hub

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
9. [BoolValue](/docs/nl-nl/reference/engine/classes/BoolValue)

Nederlands

Feedback

Engine-klasse

BoolValue

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/BoolValue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [boolean](/docs/nl-nl/luau/booleans) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [boolean](/docs/nl-nl/luau/booleans) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

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

BoolValue.Value :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Evenementen

Changed

BoolValue.Changed (value :[boolean](/docs/nl-nl/luau/booleans) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[boolean](/docs/nl-nl/luau/booleans)

 |

Codevoorbeelden

BoolValue.Changed

```

local boolValue = script.Parent.BoolValue

local function printValue(value)

	print(value)

end

boolValue.Changed:Connect(printValue)

boolValue.Value = true

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

BoolValue

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
