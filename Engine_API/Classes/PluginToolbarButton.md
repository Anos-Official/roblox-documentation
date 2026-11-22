<!-- Source: https://create.roblox.com/docs/reference/engine/classes/PluginToolbarButton -->

PluginToolbarButton | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PluginToolbarButton.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PluginToolbarButton](/docs/reference/engine/classes/PluginToolbarButton)

English

Feedback

Engine Class

PluginToolbarButton

Not Creatable

---

## Summary

Properties

|

[ClickableWhenViewportHidden](#ClickableWhenViewportHidden) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/luau/booleans)

 |
|

[Icon](#Icon) : ContentId

 |
|

[IconContent](#IconContent) :[Content](/docs/reference/engine/datatypes/Content)

 |

Methods

|

[SetActive](#SetActive) (active :  [boolean](/docs/luau/booleans) ) : ()

 |

Events

|

[Click](#Click) () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

ClickableWhenViewportHidden

Not Replicated

Read Parallel

PluginToolbarButton.ClickableWhenViewportHidden :[boolean](/docs/luau/booleans)

Provide feedback

---

Enabled

Not Replicated

Read Parallel

PluginToolbarButton.Enabled :[boolean](/docs/luau/booleans)

Code Samples

BrickColor Randomizer Plugin

```

assert(plugin, "This script must be run as a plugin")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Parts")

local pluginToolbarButton = toolbar:CreateButton(

	"Randomize Colors",

	"Click this button to assign random colors to selected parts",

	"rbxassetid://5325741572" -- A rainbow

)

local function onClick()

	local selection = Selection:Get()

	for _, object in pairs(selection) do

		if object:IsA("BasePart") then

			object.BrickColor = BrickColor.random()

		end

	end

end

pluginToolbarButton.Click:Connect(onClick)

local function doesSelectionContainAPart()

	local selection = Selection:Get()

	for _, object in pairs(selection) do

		if object:IsA("BasePart") then

			return true

		end

	end

	return false

end

local function onSelectionChanged()

	pluginToolbarButton.Enabled = doesSelectionContainAPart()

end

Selection.SelectionChanged:Connect(onSelectionChanged)

onSelectionChanged()

```

Provide feedback

---

Icon

Not Replicated

Read Parallel

PluginToolbarButton.Icon : ContentId

Provide feedback

---

IconContent

Not Replicated

Plugin Security

Read Parallel

PluginToolbarButton.IconContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

Methods

SetActive

Plugin Security

PluginToolbarButton:SetActive (active :[boolean](/docs/luau/booleans) ) : ()

Parameters

|

active :[boolean](/docs/luau/booleans)

 |

Returns

()

Provide feedback

---

Events

Click

Plugin Security

PluginToolbarButton.Click () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Code Samples

PluginToolbarButton.Click

```

assert(plugin, "This script must be run as a plugin")

local toolbar = plugin:CreateToolbar("Hello World Plugin Toolbar")

local pluginToolbarButton =

	toolbar:CreateButton("Print Hello World", "Click this button to print Hello World!", "rbxassetid://133293265")

local function onClick()

	print("Hello, world")

end

pluginToolbarButton.Click:Connect(onClick)

```

Provide feedback

---

Jump to

▼

PluginToolbarButton

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[ClickableWhenViewportHidden](#ClickableWhenViewportHidden)

[Enabled](#Enabled)

[Icon](#Icon)

[IconContent](#IconContent)

[Methods](#methods)

[SetActive()](#SetActive)

[Events](#events)

[Click](#Click)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
