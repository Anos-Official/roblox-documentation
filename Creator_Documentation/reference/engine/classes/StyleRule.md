<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/StyleRule -->

StyleRule | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StyleRule.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [StyleBase](/docs/en-us/reference/engine/classes/StyleBase)
8. /
9. [StyleRule](/docs/en-us/reference/engine/classes/StyleRule)

English

Feedback

Engine Class

StyleRule

---

## Summary

Properties

|

[Priority](#Priority) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |
|

[Selector](#Selector) :[string](/docs/en-us/luau/strings)

 |
|

[SelectorError](#SelectorError) :[string](/docs/en-us/luau/strings)

 |

Methods

|

[GetDefaultPropertyTransition](#GetDefaultPropertyTransition) () : Variant

 |
|

[GetProperties](#GetProperties) () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[GetProperty](#GetProperty) (name :  [string](/docs/en-us/luau/strings) ) : Variant

 |
|

[GetPropertyTransitions](#GetPropertyTransitions) () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[SetDefaultPropertyTransition](#SetDefaultPropertyTransition) (transitionParams :  Variant ) : ()

 |
|

[SetProperties](#SetProperties) (styleProperties :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[SetProperty](#SetProperty) (name :  [string](/docs/en-us/luau/strings) , value :  Variant ) : ()

 |
|

[SetPropertyTransition](#SetPropertyTransition) (property :  [string](/docs/en-us/luau/strings) , transitionParams :  Variant ) : ()

 |
|

[SetPropertyTransitions](#SetPropertyTransitions) (properties :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |

Inherited Members

4  inherited from [StyleBase](/docs/en-us/reference/engine/classes/StyleBase)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Priority

Read Parallel

Capabilities: UI

StyleRule.Priority :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Selector

Read Parallel

Capabilities: UI

StyleRule.Selector :[string](/docs/en-us/luau/strings)

Code Samples

UI Class Selector

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

-- Class selector

rule.Selector = "TextButton"

-- Set rule properties

rule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("335FFF"),

	["TextColor3"] = Color3.fromHex("E1E1E1"),

	["Size"] = UDim2.new(0.15, 0, 0, 40),

	["BorderSizePixel"] = 0,

})

local button = Instance.new("TextButton")

button.Text = "Main Menu"

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

-- Set rule properties

rule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("FF0099"),

	["TextColor3"] = Color3.fromHex("E1E1E1"),

	["Size"] = UDim2.new(0.15, 0, 0, 40),

	["BorderSizePixel"] = 0,

})

local button = Instance.new("TextButton")

button.Text = "Main Menu"

button.Parent = screenGui

-- Apply tag to button

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

-- Set rule property

rule:SetProperty("CornerRadius", UDim.new(0, 20))

-- Create frame

local frame = Instance.new("Frame")

frame.Size = UDim2.new(0.4, 0, 0.2, 0)

frame.Parent = screenGui

-- Apply tag to frame

CollectionService:AddTag(frame, "RoundedCorner20")

```

UI Style Query Selector

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

-- Declare style query selectors

smallRule.Selector = "@Small"

mediumRule.Selector = "@Medium"

-- Set rule properties

smallRule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("FF0099"),

	["Text"] = "Small Container",

	["TextColor3"] = Color3.fromHex("E1E1E1"),

	["TextSize"] = 12,

})

mediumRule:SetProperties({

	["BackgroundColor3"] = Color3.fromHex("F0F0F0"),

	["Text"] = "Medium Container",

	["TextColor3"] = Color3.fromHex("0022FC"),

	["TextSize"] = 24,

})

local button = Instance.new("TextButton")

button.Text = "Main Menu"

button.Parent = screenGui

button.Size = UDim2.fromScale(0.5, 0.2)

-- Create style queries with names matching style rule selectors

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

Provide feedback

---

SelectorError

Read Only

Not Replicated

Read Parallel

Capabilities: UI

StyleRule.SelectorError :[string](/docs/en-us/luau/strings)

Provide feedback

---

Methods

GetDefaultPropertyTransition

Capabilities: UI

StyleRule:GetDefaultPropertyTransition () : Variant

Returns

Variant

Provide feedback

---

GetProperties

Capabilities: UI

StyleRule:GetProperties () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

Get Properties

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

-- Get reference to style rule

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

Provide feedback

---

GetProperty

Capabilities: UI

StyleRule:GetProperty (name :[string](/docs/en-us/luau/strings) ) : Variant

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |

Returns

Variant

Code Samples

Get Property

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

Provide feedback

---

GetPropertyTransitions

Capabilities: UI

StyleRule:GetPropertyTransitions () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

GetPropertyTransitions()

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

-- Get reference to style rule

local frameRule = coreSheet.Frame

-- Set some transitions

frameRule:SetPropertyTransition("BackgroundColor3", TweenInfo.new(1, Enum.EasingStyle.Linear))

frameRule:SetPropertyTransition("BackgroundTransparency", "$DefaultTransition")

local transitions = frameRule:GetPropertyTransitions()

print(transitions)

```

Provide feedback

---

SetDefaultPropertyTransition

Capabilities: UI

StyleRule:SetDefaultPropertyTransition (transitionParams : Variant ) : ()

Parameters

|

transitionParams : Variant

 |

Returns

()

Provide feedback

---

SetProperties

Capabilities: UI

StyleRule:SetProperties (styleProperties :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

Parameters

|

styleProperties :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Provide feedback

---

SetProperty

Capabilities: UI

StyleRule:SetProperty (

name :[string](/docs/en-us/luau/strings) , value : Variant

) : ()

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |
|

value : Variant

 |

Returns

()

Provide feedback

---

SetPropertyTransition

Capabilities: UI

StyleRule:SetPropertyTransition (

property :[string](/docs/en-us/luau/strings) , transitionParams : Variant

) : ()

Parameters

|

property :[string](/docs/en-us/luau/strings)

 |
|

transitionParams : Variant

 |

Returns

()

Code Samples

SetPropertyTransition()

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

-- Get reference to style rule

local frameRule = coreSheet.Frame

-- Set a 1-second linear transition on BackgroundColor3

frameRule:SetPropertyTransition("BackgroundColor3", TweenInfo.new(

	1, -- Time

	Enum.EasingStyle.Linear -- EasingStyle

))

-- Remove the transition

frameRule:SetPropertyTransition("BackgroundColor3", nil)

```

SetPropertyTransition() Using Tokens

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

local tokensSheet = ReplicatedStorage:FindFirstChild("Tokens")

-- Set tokens (attributes) on tokens sheet

tokensSheet:SetAttribute("LinearTransition", TweenInfo.new(1, Enum.EasingStyle.Linear))

-- Get reference to style rule

local frameRule = coreSheet.Frame

frameRule:SetPropertyTransition("BackgroundColor3", "$LinearTransition")

```

Provide feedback

---

SetPropertyTransitions

Capabilities: UI

StyleRule:SetPropertyTransitions (properties :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

Parameters

|

properties :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Code Samples

SetPropertyTransitions()

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

-- Get reference to style rule

local frameRule = coreSheet.Frame

-- Sets transitions for two properties at once

frameRule:SetPropertyTransitions({

  ["BackgroundColor3"] = TweenInfo.new(1, Enum.EasingStyle.Linear),

  ["BackgroundTransparency"] = TweenInfo.new(0.25, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),

})

-- Remove all transitions

frameRule:SetPropertyTransitions({})

```

SetPropertyTransitions() Using Tokens

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChild("CoreSheet")

local tokenSheet = ReplicatedStorage:FindFirstChild("Tokens")

-- Set tokens (attributes) on token sheet

tokenSheet:SetAttribute("LinearTransition", TweenInfo.new(1, Enum.EasingStyle.Linear))

tokenSheet:SetAttribute("QuadTransition", TweenInfo.new(0.25, Enum.EasingStyle.Quad))

-- Get reference to style rule

local frameRule = coreSheet.Frame

-- Set transitions for multiple properties at once

frameRule:SetPropertyTransitions({

	["BackgroundColor3"] = "$LinearTransition",

	["BackgroundTransparency"] = "$QuadTransition",

})

```

Provide feedback

---

Jump to

▼

StyleRule

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Priority](#Priority)

[Selector](#Selector)

[SelectorError](#SelectorError)

[Methods](#methods)

[GetDefaultPropertyTransition()](#GetDefaultPropertyTransition)

[GetProperties()](#GetProperties)

[GetProperty()](#GetProperty)

[GetPropertyTransitions()](#GetPropertyTransitions)

[SetDefaultPropertyTransition()](#SetDefaultPropertyTransition)

[SetProperties()](#SetProperties)

[SetProperty()](#SetProperty)

[SetPropertyTransition()](#SetPropertyTransition)

[SetPropertyTransitions()](#SetPropertyTransitions)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
