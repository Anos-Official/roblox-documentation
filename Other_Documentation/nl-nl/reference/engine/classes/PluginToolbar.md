<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PluginToolbar -->

PluginToolbar | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PluginToolbar](/docs/nl-nl/reference/engine/classes/PluginToolbar)

Nederlands

Feedback

Engine-klasse

PluginToolbar

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PluginToolbar)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CreateButton](#CreateButton) (buttonId :  [string](/docs/nl-nl/luau/strings) , tooltip :  [string](/docs/nl-nl/luau/strings) , iconname :  [string](/docs/nl-nl/luau/strings) , text :  [string](/docs/nl-nl/luau/strings) ) :[PluginToolbarButton](/docs/nl-nl/reference/engine/classes/PluginToolbarButton)

 |
| --- | --- |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

CreateButton

Plugin-beveiliging

PluginToolbar:CreateButton (

buttonId :[string](/docs/nl-nl/luau/strings) , tooltip :[string](/docs/nl-nl/luau/strings) , iconname :[string](/docs/nl-nl/luau/strings) , text :[string](/docs/nl-nl/luau/strings)

) :[PluginToolbarButton](/docs/nl-nl/reference/engine/classes/PluginToolbarButton)

Parameters

|

buttonId :[string](/docs/nl-nl/luau/strings)

 |
|

tooltip :[string](/docs/nl-nl/luau/strings)

 |
|

iconname :[string](/docs/nl-nl/luau/strings)

 |
|

text :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[PluginToolbarButton](/docs/nl-nl/reference/engine/classes/PluginToolbarButton)

Codevoorbeelden

Een Plugin Toolbar Knop Toevoegen

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Maak een nieuwe werkbalksectie en Plugins menu map met de titel "Aangepast"

local toolbar = plugin:CreateToolbar("Custom")

-- Voeg een werkbalkknop toe met het label "Leeg Script"

local newScriptButton = toolbar:CreateButton("Empty Script", "Maak een leeg script", "rbxassetid://14978048121")

-- Maak de knop klikbaar, zelfs als de 3D-weergave verborgen is

newScriptButton.ClickableWhenViewportHidden = true

local function onPluginButtonClicked()

	local newScript = Instance.new("Script")

	newScript.Source = ""

	newScript.Parent = ServerScriptService

end

newScriptButton.Click:Connect(onPluginButtonClicked)

```

Feedback geven

---

Ga naar

▼

PluginToolbar

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[CreateButton()](#CreateButton)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
