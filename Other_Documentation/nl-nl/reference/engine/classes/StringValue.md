<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StringValue -->

StringValue | Documentatie - Roblox Creator Hub

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
9. [StringValue](/docs/nl-nl/reference/engine/classes/StringValue)

Nederlands

Feedback

Engine-klasse

StringValue

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StringValue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Veranderde Evenement

```

-- Demonstreer het Changed evenement door een Part te maken

local part = Instance.new("Part")

part.Changed:Connect(print)

-- Dit activeert Changed met "Transparency"

part.Transparency = 0.5

-- Evenzo, dit activeert Changed met "Number"

part.Name = "SomePart"

-- Aangezien het veranderen van BrickColor ook andere

-- eigenschappen tegelijkertijd zal veranderen, activeert deze regel Changed

-- met "BrickColor", "Color3" en "Color3uint16".

part.BrickColor = BrickColor.Red()

-- Een NumberValue houdt een double-precision floating-point nummer

local vNumber = Instance.new("NumberValue")

vNumber.Changed:Connect(print)

-- Dit activeert Changed met 123.456 (niet "Value")

vNumber.Value = 123.456

-- Dit activeert niet Changed

vNumber.Name = "SomeNumber"

-- Een StringValue slaat één string op

local vString = Instance.new("StringValue")

vString.Changed:Connect(print)

-- Dit activeert Changed met "Hello" (niet "Value")

vString.Value = "Hello"

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

StringValue.Value :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Evenementen

Changed

StringValue.Changed (value :[string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[string](/docs/nl-nl/luau/strings)

 |

Codevoorbeelden

Hoe StringValue.Changed te gebruiken

```

local value = Instance.new("StringValue")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

value.Value = "Hallo wereld!"

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

StringValue

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
