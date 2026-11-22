<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PluginMenu -->

PluginMenu | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PluginMenu](/docs/nl-nl/reference/engine/classes/PluginMenu)

Nederlands

Feedback

Engine-klasse

PluginMenu

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PluginMenu)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Icon](#Icon) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[Title](#Title) :[string](/docs/nl-nl/luau/strings)

 |
|

[Visible](#Visible) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[AddAction](#AddAction) (action :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[AddMenu](#AddMenu) (menu :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[AddNewAction](#AddNewAction) (actionId :  [string](/docs/nl-nl/luau/strings) , text :  [string](/docs/nl-nl/luau/strings) , icon :  [string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[AddSeparator](#AddSeparator) () : ()

 |
|

[Clear](#Clear) () : ()

 |
|

[ShowAsync](#ShowAsync) () :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Een PluginMenu en PluginMenuAction maken

```

-- Deze code kan in de Command Bar worden geplakt, maar slechts één keer

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

			print("Geselecteerde Actie:", selectedAction.Text, "met ActionId:", selectedAction.ActionId)

		else

			print("Gebruiker heeft geen actie geselecteerd!")

		end

	end

end

toggle.Changed:Connect(onToggled)

```

---

API-referentie

Eigenschappen

Icon

Niet gerepliceerd

Parallel lezen

PluginMenu.Icon :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Title

Niet gerepliceerd

Parallel lezen

PluginMenu.Title :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Visible

Roblox-scriptbeveiliging

Parallel lezen

PluginMenu.Visible :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

AddAction

Plugin-beveiliging

PluginMenu:AddAction (action :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

action :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Feedback geven

---

AddMenu

Plugin-beveiliging

PluginMenu:AddMenu (menu :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

menu :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Feedback geven

---

AddNewAction

Plugin-beveiliging

PluginMenu:AddNewAction (

actionId :[string](/docs/nl-nl/luau/strings) , text :[string](/docs/nl-nl/luau/strings) , icon :[string](/docs/nl-nl/luau/strings)

) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

actionId :[string](/docs/nl-nl/luau/strings)

 |
|

text :[string](/docs/nl-nl/luau/strings)

 |
|

icon :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

AddSeparator

Plugin-beveiliging

PluginMenu:AddSeparator () : ()

Teruggaves

()

Feedback geven

---

Clear

Plugin-beveiliging

PluginMenu:Clear () : ()

Teruggaves

()

Feedback geven

---

ShowAsync

Opbrengst

Plugin-beveiliging

PluginMenu:ShowAsync () :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

Ga naar

▼

PluginMenu

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Icon](#Icon)

[Title](#Title)

[Visible](#Visible)

[Methoden](#methods)

[AddAction()](#AddAction)

[AddMenu()](#AddMenu)

[AddNewAction()](#AddNewAction)

[AddSeparator()](#AddSeparator)

[Clear()](#Clear)

[ShowAsync()](#ShowAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
