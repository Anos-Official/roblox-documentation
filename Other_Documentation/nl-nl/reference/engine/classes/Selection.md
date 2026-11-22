<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Selection -->

Selection | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Selection](/docs/nl-nl/reference/engine/classes/Selection)

Nederlands

Feedback

Engine-klasse

Selection

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Selection)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[SelectionThickness](#SelectionThickness) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |

Methoden

|

[Add](#Add) (instancesToAdd :  Instances ) : ()

 |
|

[Get](#Get) () : Instances

 |
|

[Remove](#Remove) (instancesToRemove :  Instances ) : ()

 |
|

[Set](#Set) (selection :  Instances ) : ()

 |

Evenementen

|

[SelectionChanged](#SelectionChanged) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Selectie

```

local Selection = game:GetService("Selection")

for _, object in pairs(Selection:Get()) do

	if object:IsA("BasePart") then

		object.CFrame = object.CFrame * CFrame.Angles(0, math.pi / 2, 0)

	end

end

```

---

API-referentie

Eigenschappen

SelectionThickness

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Selection.SelectionThickness :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

Add

Plugin-beveiliging

Mogelijkheden: Basic

Selection:Add (instancesToAdd : Instances ) : ()

Parameters

|

instancesToAdd : Instances

 |

Teruggaves

()

Feedback geven

---

Get

Plugin-beveiliging

Mogelijkheden: Basic

Selection:Get () : Instances

Teruggaves

Instances

Codevoorbeelden

Selectie

```

local Selection = game:GetService("Selection")

for _, object in pairs(Selection:Get()) do

	if object:IsA("BasePart") then

		object.CFrame = object.CFrame * CFrame.Angles(0, math.pi / 2, 0)

	end

end

```

Selection.SelectionChanged

```

local selection = game:GetService("Selection")

selection.SelectionChanged:Connect(function()

	print("Selectie bevat " .. #selection:Get() .. " items.")

end)

```

Feedback geven

---

Remove

Plugin-beveiliging

Mogelijkheden: Basic

Selection:Remove (instancesToRemove : Instances ) : ()

Parameters

|

instancesToRemove : Instances

 |

Teruggaves

()

Feedback geven

---

Set

Plugin-beveiliging

Mogelijkheden: Basic

Selection:Set (selection : Instances ) : ()

Parameters

|

selection : Instances

 |

Teruggaves

()

Codevoorbeelden

Selectiegroep

```

local Selection = game:GetService("Selection")

local newSelection = {}

for _, object in pairs(workspace:GetDescendants()) do

	if object:IsA("BasePart") and object.BrickColor == BrickColor.new("Bright red") then

		table.insert(newSelection, object)

	end

end

Selection:Set(newSelection)

```

Instellen

```

local selected = Selection:Get()

table.insert(selected, object)

Selection:Set(selected)

```

Feedback geven

---

Evenementen

SelectionChanged

Mogelijkheden: Basic

Selection.SelectionChanged () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

Selection.SelectionChanged

```

local selection = game:GetService("Selection")

selection.SelectionChanged:Connect(function()

	print("Selectie bevat " .. #selection:Get() .. " items.")

end)

```

Feedback geven

---

Ga naar

▼

Selection

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[SelectionThickness](#SelectionThickness)

[Methoden](#methods)

[Add()](#Add)

[Get()](#Get)

[Remove()](#Remove)

[Set()](#Set)

[Evenementen](#events)

[SelectionChanged](#SelectionChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
