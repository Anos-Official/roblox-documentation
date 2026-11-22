<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PluginToolbarButton -->

PluginToolbarButton | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PluginToolbarButton](/docs/nl-nl/reference/engine/classes/PluginToolbarButton)

Nederlands

Feedback

Engine-klasse

PluginToolbarButton

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PluginToolbarButton)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[ClickableWhenViewportHidden](#ClickableWhenViewportHidden) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Icon](#Icon) : ContentId

 |
|

[IconContent](#IconContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |

Methoden

|

[SetActive](#SetActive) (active :  [boolean](/docs/nl-nl/luau/booleans) ) : ()

 |

Evenementen

|

[Click](#Click) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

ClickableWhenViewportHidden

Niet gerepliceerd

Parallel lezen

PluginToolbarButton.ClickableWhenViewportHidden :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Enabled

Niet gerepliceerd

Parallel lezen

PluginToolbarButton.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

BrickColor Randomizer Plugin

```

assert(plugin, "Dit script moet als een plugin worden uitgevoerd")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Onderdelen")

local pluginToolbarButton = toolbar:CreateButton(

	"Kleuren Randomiseren",

	"Klik op deze knop om willekeurige kleuren toe te wijzen aan geselecteerde onderdelen",

	"rbxassetid://5325741572" -- Een regenboog

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

Feedback geven

---

Icon

Niet gerepliceerd

Parallel lezen

PluginToolbarButton.Icon : ContentId

Feedback geven

---

IconContent

Niet gerepliceerd

Plugin-beveiliging

Parallel lezen

PluginToolbarButton.IconContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

Methoden

SetActive

Plugin-beveiliging

PluginToolbarButton:SetActive (active :[boolean](/docs/nl-nl/luau/booleans) ) : ()

Parameters

|

active :[boolean](/docs/nl-nl/luau/booleans)

 |

Teruggaves

()

Feedback geven

---

Evenementen

Click

Plugin-beveiliging

PluginToolbarButton.Click () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

PluginToolbarButton.Click

```

assert(plugin, "Dit script moet als een plugin worden uitgevoerd")

local toolbar = plugin:CreateToolbar("Hallo Wereld Plugin Toolbar")

local pluginToolbarButton =

	toolbar:CreateButton("Print Hallo Wereld", "Klik op deze knop om Hallo Wereld te printen!", "rbxassetid://133293265")

local function onClick()

	print("Hallo, wereld")

end

pluginToolbarButton.Click:Connect(onClick)

```

Feedback geven

---

Ga naar

▼

PluginToolbarButton

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[ClickableWhenViewportHidden](#ClickableWhenViewportHidden)

[Enabled](#Enabled)

[Icon](#Icon)

[IconContent](#IconContent)

[Methoden](#methods)

[SetActive()](#SetActive)

[Evenementen](#events)

[Click](#Click)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
