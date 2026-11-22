<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StyleRule -->

StyleRule | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StyleBase](/docs/nl-nl/reference/engine/classes/StyleBase)
8. /
9. [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)

Nederlands

Feedback

Engine-klasse

StyleRule

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StyleRule)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Priority](#Priority) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[Selector](#Selector) :[string](/docs/nl-nl/luau/strings)

 |
|

[SelectorError](#SelectorError) :[string](/docs/nl-nl/luau/strings)

 |

Methoden

|

[GetDefaultPropertyTransition](#GetDefaultPropertyTransition) () : Variant

 |
|

[GetProperties](#GetProperties) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetProperty](#GetProperty) (name :  [string](/docs/nl-nl/luau/strings) ) : Variant

 |
|

[GetPropertyTransitions](#GetPropertyTransitions) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[SetDefaultPropertyTransition](#SetDefaultPropertyTransition) (transitionParams :  Variant ) : ()

 |
|

[SetProperties](#SetProperties) (styleProperties :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[SetProperty](#SetProperty) (name :  [string](/docs/nl-nl/luau/strings) , value :  Variant ) : ()

 |
|

[SetPropertyTransition](#SetPropertyTransition) (property :  [string](/docs/nl-nl/luau/strings) , transitionParams :  Variant ) : ()

 |
|

[SetPropertyTransitions](#SetPropertyTransitions) (properties :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Overgenomen leden

4  overgenomen van [StyleBase](/docs/nl-nl/reference/engine/classes/StyleBase)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Priority

Parallel lezen

Mogelijkheden: UI

StyleRule.Priority :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Selector

Parallel lezen

Mogelijkheden: UI

StyleRule.Selector :[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

UI Klasse Selector

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local screenGui = script.Parent

local coreSheet = Instance.new("StyleSheet")

coreSheet.Parent = ReplicatedStorage

local styleLink = Instance.new("StyleLink")

styleLink.StyleSheet = coreSheet

styleLink.Parent = screenGui

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

-- Klasse selector

rule.Selector = "TextButton"

-- Stel regel eigenschappen in

rule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("335FFF"),

	["TextColor3"] = Color3.fromHex("E1E1E1"),

	["Size"] = UDim2.new(0.15, 0, 0, 40),

	["BorderSizePixel"] = 0,

})

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = screenGui

```

UI Tag Selector

```

local CollectionService = game:GetService("CollectionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local screenGui = script.Parent

local coreSheet = Instance.new("StyleSheet")

coreSheet.Parent = ReplicatedStorage

local styleLink = Instance.new("StyleLink")

styleLink.StyleSheet = coreSheet

styleLink.Parent = screenGui

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

-- Tag selector

rule.Selector = ".ButtonPrimary"

-- Stel regel eigenschappen in

rule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("FF0099"),

	["TextColor3"] = Color3.fromHex("E1E1E1"),

	["Size"] = UDim2.new(0.15, 0, 0, 40),

	["BorderSizePixel"] = 0,

})

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = screenGui

-- Pas tag toe op knop

CollectionService:AddTag(button, "ButtonPrimary")

```

UI Modifier Selector

```

local CollectionService = game:GetService("CollectionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local screenGui = script.Parent

local coreSheet = Instance.new("StyleSheet")

coreSheet.Parent = ReplicatedStorage

local styleLink = Instance.new("StyleLink")

styleLink.StyleSheet = coreSheet

styleLink.Parent = screenGui

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

-- UI component selector

rule.Selector = "Frame.RoundedCorner20::UICorner"

-- Stel regel eigenschap in

rule:SetProperty("CornerRadius", UDim.new(0, 20))

-- Maak frame

local frame = Instance.new("Frame")

frame.Size = UDim2.new(0.4, 0, 0.2, 0)

frame.Parent = screenGui

-- Pas tag toe op frame

CollectionService:AddTag(frame, "RoundedCorner20")

```

UI Stijl Query Selector

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local screenGui = script.Parent

local coreSheet = Instance.new("StyleSheet")

coreSheet.Parent = ReplicatedStorage

local styleLink = Instance.new("StyleLink")

styleLink.StyleSheet = coreSheet

styleLink.Parent = screenGui

local smallRule = Instance.new("StyleRule")

smallRule.Parent = coreSheet

local mediumRule = Instance.new("StyleRule")

mediumRule.Parent = coreSheet

-- Verklaar stijl query selectors

smallRule.Selector = "@Small"

mediumRule.Selector = "@Medium"

-- Stel regel eigenschappen in

smallRule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("FF0099"),

	["Text"] = "Kleine Container",

	["TextColor3"] = Color3.fromHex("E1E1E1"),

	["TextSize"] = 12,

})

mediumRule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("F0F0F0"),

	["Text"] = "Middelgrote Container",

	["TextColor3"] = Color3.fromHex("0022FC"),

	["TextSize"] = 24,

})

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = screenGui

button.Size = UDim2.fromScale(0.5, 0.2)

-- Maak stijl queries met namen die overeenkomen met stijl regel selectors

local mediumSQ = Instance.new("StyleQuery")

mediumSQ.Parent = button

mediumSQ.Name = "Medium"

mediumSQ:SetConditions({

	["MinSize"] = Vector2.new(200, 0),

})

local smallSQ = Instance.new("StyleQuery")

smallSQ.Parent = button

smallSQ.Name = "Small"

smallSQ:SetConditions({

	["MaxSize"] = Vector2.new(200, math.huge),

	["MinSize"] = Vector2.new(0, 0),

})

```

Feedback geven

---

SelectorError

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: UI

StyleRule.SelectorError :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Methoden

GetDefaultPropertyTransition

Mogelijkheden: UI

StyleRule:GetDefaultPropertyTransition () : Variant

Teruggaves

Variant

Feedback geven

---

GetProperties

Mogelijkheden: UI

StyleRule:GetProperties () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Eigenschappen Opvragen

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = Instance.new("StyleSheet")

coreSheet.Name = "CoreSheet"

coreSheet.Parent = ReplicatedStorage

local frameRule = Instance.new("StyleRule")

frameRule.Name = "Frame"

frameRule:SetProperty("AnchorPoint", Vector2.new(0.5, 0))

frameRule:SetProperty("BackgroundColor3", Color3.new(1, 0, 0.25))

frameRule.Parent = coreSheet

-- Verkrijg referentie naar stijlregel

local frameRule = coreSheet.Frame

local props = frameRule:GetProperties()

print(props)

--[[

{

	["AnchorPoint"] = 0.5, 0,

	["BackgroundColor3"] = 1, 0, 0.25

}

]]

```

Feedback geven

---

GetProperty

Mogelijkheden: UI

StyleRule:GetProperty (name :[string](/docs/nl-nl/luau/strings) ) : Variant

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

Variant

Codevoorbeelden

Eigenschap Krijgen

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = Instance.new("StyleSheet")

coreSheet.Name = "CoreSheet"

coreSheet.Parent = ReplicatedStorage

local frameRule = Instance.new("StyleRule")

frameRule.Name = "Frame"

frameRule:SetProperty("AnchorPoint", Vector2.new(0.5, 0))

frameRule.Parent = coreSheet

local prop = frameRule:GetProperty("AnchorPoint")

print(prop) --> 0.5, 0

```

Feedback geven

---

GetPropertyTransitions

Mogelijkheden: UI

StyleRule:GetPropertyTransitions () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

GetPropertyTransitions()

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

-- Verkrijg referentie naar stijlregel

local frameRule = coreSheet.Frame

-- Stel enkele overgangen in

frameRule:SetPropertyTransition("BackgroundColor3", TweenInfo.new(1, Enum.EasingStyle.Linear))

frameRule:SetPropertyTransition("BackgroundTransparency", "$DefaultTransition")

local transitions = frameRule:GetPropertyTransitions()

print(transitions)

```

Feedback geven

---

SetDefaultPropertyTransition

Mogelijkheden: UI

StyleRule:SetDefaultPropertyTransition (transitionParams : Variant ) : ()

Parameters

|

transitionParams : Variant

 |

Teruggaves

()

Feedback geven

---

SetProperties

Mogelijkheden: UI

StyleRule:SetProperties (styleProperties :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

styleProperties :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Feedback geven

---

SetProperty

Mogelijkheden: UI

StyleRule:SetProperty (

name :[string](/docs/nl-nl/luau/strings) , value : Variant

) : ()

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

value : Variant

 |

Teruggaves

()

Feedback geven

---

SetPropertyTransition

Mogelijkheden: UI

StyleRule:SetPropertyTransition (

property :[string](/docs/nl-nl/luau/strings) , transitionParams : Variant

) : ()

Parameters

|

property :[string](/docs/nl-nl/luau/strings)

 |
|

transitionParams : Variant

 |

Teruggaves

()

Codevoorbeelden

SetPropertyTransition()

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

-- Verkrijg referentie naar stijlregel

local frameRule = coreSheet.Frame

-- Stel een lineaire overgang van 1 seconde in op BackgroundColor3

frameRule:SetPropertyTransition("BackgroundColor3", TweenInfo.new(

	1, -- Tijd

	Enum.EasingStyle.Linear -- EasingStyle

))

-- Verwijder de overgang

frameRule:SetPropertyTransition("BackgroundColor3", nil)

```

SetPropertyTransition() Gebruik van Tokens

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

local tokensSheet = ReplicatedStorage:FindFirstChild("Tokens")

-- Stel tokens (attributen) in op het tokens-blad

tokensSheet:SetAttribute("LinearTransition", TweenInfo.new(1, Enum.EasingStyle.Linear))

-- Verkrijg referentie naar stijlregel

local frameRule = coreSheet.Frame

frameRule:SetPropertyTransition("BackgroundColor3", "$LinearTransition")

```

Feedback geven

---

SetPropertyTransitions

Mogelijkheden: UI

StyleRule:SetPropertyTransitions (properties :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

properties :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Codevoorbeelden

SetPropertyTransitions()

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

-- Verkrijg referentie naar stijlregel

local frameRule = coreSheet.Frame

-- Stelt overgangen in voor twee eigenschappen tegelijk

frameRule:SetPropertyTransitions({

  ["BackgroundColor3"] = TweenInfo.new(1, Enum.EasingStyle.Linear),

  ["BackgroundTransparency"] = TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

})

-- Verwijder alle overgangen

frameRule:SetPropertyTransitions({})

```

SetPropertyTransitions() Met Tokens

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

local tokenSheet = ReplicatedStorage:FindFirstChild("Tokens")

-- Stel tokens (attributen) in op het tokenblad

tokenSheet:SetAttribute("LinearTransition", TweenInfo.new(1, Enum.EasingStyle.Linear))

tokenSheet:SetAttribute("QuadTransition", TweenInfo.new(0.25, Enum.EasingStyle.Quad))

-- Verkrijg referentie naar stijlregel

local frameRule = coreSheet.Frame

-- Stel overgangen in voor meerdere eigenschappen tegelijk

frameRule:SetPropertyTransitions({

	["BackgroundColor3"] = "$LinearTransition",

	["BackgroundTransparency"] = "$QuadTransition",

})

```

Feedback geven

---

Ga naar

▼

StyleRule

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Priority](#Priority)

[Selector](#Selector)

[SelectorError](#SelectorError)

[Methoden](#methods)

[GetDefaultPropertyTransition()](#GetDefaultPropertyTransition)

[GetProperties()](#GetProperties)

[GetProperty()](#GetProperty)

[GetPropertyTransitions()](#GetPropertyTransitions)

[SetDefaultPropertyTransition()](#SetDefaultPropertyTransition)

[SetProperties()](#SetProperties)

[SetProperty()](#SetProperty)

[SetPropertyTransition()](#SetPropertyTransition)

[SetPropertyTransitions()](#SetPropertyTransitions)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
