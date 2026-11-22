<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Object -->

Object | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)

Nederlands

Feedback

Engine-klasse

Object

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Object)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[ClassName](#ClassName) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[className](#className) :[string](/docs/nl-nl/luau/strings)

Verouderd

 |

Methoden

|

[GetPropertyChangedSignal](#GetPropertyChangedSignal) (property :  [string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[IsA](#IsA) (className :  [string](/docs/nl-nl/luau/strings) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[isA](#isA) (className :  [string](/docs/nl-nl/luau/strings) ) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |

Evenementen

|

[Changed](#Changed) (property :  [string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen door

[Capture](/docs/nl-nl/reference/engine/classes/Capture) , [ConfigSnapshot](/docs/nl-nl/reference/engine/classes/ConfigSnapshot) , [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh) , [Instance](/docs/nl-nl/reference/engine/classes/Instance) , Meer weergeven...

---

API-referentie

Eigenschappen

ClassName

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Object.ClassName :[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Klasse Naam

```

for _, child in workspace:GetChildren() do

    if child.ClassName == "Part" then

        print("Gevonden een Deel")

        -- zal Onderdelen in model vinden, maar GEEN TrussParts, WedgeParts, enz.

    end

end

```

Feedback geven

---

className

Verouderd

Details weergeven

---

Methoden

GetPropertyChangedSignal

Object:GetPropertyChangedSignal (property :[string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

property :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

Oude-naar-Nieuwe Waarden met Veranderd

```

local part = Instance.new("Part")

local currentColor = part.BrickColor

local function onBrickColorChanged()

	local newColor = part.BrickColor

	print("Kleur veranderd van", currentColor.Name, "naar", newColor.Name)

	currentColor = newColor

end

part:GetPropertyChangedSignal("BrickColor"):Connect(onBrickColorChanged)

part.BrickColor = BrickColor.new("Echt rood")

part.BrickColor = BrickColor.new("Echt blauw")

```

Veranderde en GetPropertyChangedSignal

```

local part = Instance.new("Part")

local function onBrickColorChanged()

	print("Mijn kleur is nu " .. part.BrickColor.Name)

end

local function onChanged(property)

	if property == "BrickColor" then

		onBrickColorChanged()

	end

end

part:GetPropertyChangedSignal("BrickColor"):Connect(onBrickColorChanged)

part.Changed:Connect(onChanged)

-- Trigger enkele wijzigingen (omdat we twee keer verbonden zijn,

-- zullen beide deze twee oproepen naar onBrickColorChanged veroorzaken)

part.BrickColor = BrickColor.new("Really red")

part.BrickColor = BrickColor.new("Institutional white")

```

Feedback geven

---

IsA

Parallel schrijven

Object:IsA (className :[string](/docs/nl-nl/luau/strings) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Instance:IsA()

```

local Workspace = game:GetService("Workspace")

print(Workspace:IsA("Workspace")) -- waar

print(Workspace:IsA("BasePart")) -- onwaar

print(Workspace:IsA("Instance")) -- waar

```

Feedback geven

---

isA

Verouderd

Details weergeven

---

Evenementen

Changed

Object.Changed (property :[string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

property :[string](/docs/nl-nl/luau/strings)

 |

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

Verander Detector

```

local object = script.Parent

local function onChanged(property)

	-- Verkrijg de huidige waarde van de eigenschap

	local value = object[property]

	-- Print een bericht dat zegt wat is veranderd

	print(object:GetFullName() .. "." .. property .. " (" .. typeof(value) .. ") veranderd naar " .. tostring(value))

end

object.Changed:Connect(onChanged)

-- Trigger een eenvoudige wijziging in het object (voeg een underscore toe aan de naam)

object.Name = "_" .. object.Name

```

Feedback geven

---

Ga naar

▼

Object

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[ClassName](#ClassName)

[className](#className)

[Methoden](#methods)

[GetPropertyChangedSignal()](#GetPropertyChangedSignal)

[IsA()](#IsA)

[isA()](#isA)

[Evenementen](#events)

[Changed](#Changed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
