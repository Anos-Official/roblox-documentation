<!-- Source: https://create.roblox.com/docs/reference/engine/classes/PluginMenu -->

PluginMenu | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PluginMenu.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PluginMenu](/docs/reference/engine/classes/PluginMenu)

English

Feedback

Engine Class

PluginMenu

Not Creatable

Not Replicated

---

## Summary

Properties

|

[Icon](#Icon) :[string](/docs/luau/strings)

 |
| --- | --- |
|

[Title](#Title) :[string](/docs/luau/strings)

 |
|

[Visible](#Visible) :[boolean](/docs/luau/booleans)

 |

Methods

|

[AddAction](#AddAction) (action :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
|

[AddMenu](#AddMenu) (menu :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
|

[AddNewAction](#AddNewAction) (actionId :  [string](/docs/luau/strings) , text :  [string](/docs/luau/strings) , icon :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[AddSeparator](#AddSeparator) () : ()

 |
|

[Clear](#Clear) () : ()

 |
|

[ShowAsync](#ShowAsync) () :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Creating a PluginMenu and PluginMenuAction

```

-- This code can be pasted into the Command Bar, but only once

local pluginMenu = plugin:CreatePluginMenu(math.random(), "Test Menu")

pluginMenu.Name = "Test Menu"

pluginMenu:AddNewAction("ActionA", "A", "rbxasset://textures/loading/robloxTiltRed.png")

pluginMenu:AddNewAction("ActionB", "B", "rbxasset://textures/loading/robloxTilt.png")

local subMenu = plugin:CreatePluginMenu(math.random(), "C", "rbxasset://textures/explosion.png")

subMenu.Name = "Sub Menu"

subMenu:AddNewAction("ActionD", "D", "rbxasset://textures/whiteCircle.png")

subMenu:AddNewAction("ActionE", "E", "rbxasset://textures/icon_ROBUX.png")

pluginMenu:AddMenu(subMenu)

pluginMenu:AddSeparator()

pluginMenu:AddNewAction("ActionF", "F", "rbxasset://textures/sparkle.png")

local toggle = Instance.new("BoolValue")

toggle.Name = "TogglePluginMenu"

toggle.Parent = workspace

local function onToggled()

	if toggle.Value then

		toggle.Value = false

		local selectedAction = pluginMenu:ShowAsync()

		if selectedAction then

			print("Selected Action:", selectedAction.Text, "with ActionId:", selectedAction.ActionId)

		else

			print("User did not select an action!")

		end

	end

end

toggle.Changed:Connect(onToggled)

```

---

API Reference

Properties

Icon

Not Replicated

Read Parallel

PluginMenu.Icon :[string](/docs/luau/strings)

Provide feedback

---

Title

Not Replicated

Read Parallel

PluginMenu.Title :[string](/docs/luau/strings)

Provide feedback

---

Visible

Roblox Script Security

Read Parallel

PluginMenu.Visible :[boolean](/docs/luau/booleans)

Provide feedback

---

Methods

AddAction

Plugin Security

PluginMenu:AddAction (action :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

action :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Provide feedback

---

AddMenu

Plugin Security

PluginMenu:AddMenu (menu :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

menu :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Provide feedback

---

AddNewAction

Plugin Security

PluginMenu:AddNewAction (

actionId :[string](/docs/luau/strings) , text :[string](/docs/luau/strings) , icon :[string](/docs/luau/strings)

) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

actionId :[string](/docs/luau/strings)

 |
|

text :[string](/docs/luau/strings)

 |
|

icon :[string](/docs/luau/strings)

 |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Provide feedback

---

AddSeparator

Plugin Security

PluginMenu:AddSeparator () : ()

Returns

()

Provide feedback

---

Clear

Plugin Security

PluginMenu:Clear () : ()

Returns

()

Provide feedback

---

ShowAsync

Yields

Plugin Security

PluginMenu:ShowAsync () :[Instance](/docs/reference/engine/datatypes/Instance)

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Provide feedback

---

Jump to

▼

PluginMenu

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Icon](#Icon)

[Title](#Title)

[Visible](#Visible)

[Methods](#methods)

[AddAction()](#AddAction)

[AddMenu()](#AddMenu)

[AddNewAction()](#AddNewAction)

[AddSeparator()](#AddSeparator)

[Clear()](#Clear)

[ShowAsync()](#ShowAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
