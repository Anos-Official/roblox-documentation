<!-- Source: https://create.roblox.com/docs/reference/engine/classes/PluginToolbar -->

PluginToolbar | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PluginToolbar.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PluginToolbar](/docs/reference/engine/classes/PluginToolbar)

English

Feedback

Engine Class

PluginToolbar

Not Creatable

---

## Summary

Methods

|

[CreateButton](#CreateButton) (buttonId :  [string](/docs/luau/strings) , tooltip :  [string](/docs/luau/strings) , iconname :  [string](/docs/luau/strings) , text :  [string](/docs/luau/strings) ) :[PluginToolbarButton](/docs/reference/engine/classes/PluginToolbarButton)

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

CreateButton

Plugin Security

PluginToolbar:CreateButton (

buttonId :[string](/docs/luau/strings) , tooltip :[string](/docs/luau/strings) , iconname :[string](/docs/luau/strings) , text :[string](/docs/luau/strings)

) :[PluginToolbarButton](/docs/reference/engine/classes/PluginToolbarButton)

Parameters

|

buttonId :[string](/docs/luau/strings)

 |
|

tooltip :[string](/docs/luau/strings)

 |
|

iconname :[string](/docs/luau/strings)

 |
|

text :[string](/docs/luau/strings)

 |

Returns

[PluginToolbarButton](/docs/reference/engine/classes/PluginToolbarButton)

Code Samples

Adding a Plugin Toolbar Button

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Create a new toolbar section and Plugins menu folder titled "Custom"

local toolbar = plugin:CreateToolbar("Custom")

-- Add a toolbar button labeled "Empty Script"

local newScriptButton = toolbar:CreateButton("Empty Script", "Create an empty script", "rbxassetid://14978048121")

-- Make button clickable even if 3D viewport is hidden

newScriptButton.ClickableWhenViewportHidden = true

local function onPluginButtonClicked()

	local newScript = Instance.new("Script")

	newScript.Source = ""

	newScript.Parent = ServerScriptService

end

newScriptButton.Click:Connect(onPluginButtonClicked)

```

Provide feedback

---

Jump to

▼

PluginToolbar

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[CreateButton()](#CreateButton)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
