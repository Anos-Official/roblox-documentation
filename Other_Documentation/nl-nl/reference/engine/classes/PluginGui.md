<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PluginGui -->

PluginGui | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/nl-nl/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)
10. /
11. [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector)
12. /
13. [PluginGui](/docs/nl-nl/reference/engine/classes/PluginGui)

Nederlands

Feedback

Engine-klasse

PluginGui

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PluginGui)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Title](#Title) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |

Methoden

|

[BindToClose](#BindToClose) (function :  [function](/docs/nl-nl/luau/functions) ) : ()

 |
|

[GetRelativeMousePosition](#GetRelativeMousePosition) () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |

Evenementen

|

[PluginDragDropped](#PluginDragDropped) (dragData :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PluginDragEntered](#PluginDragEntered) (dragData :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PluginDragLeft](#PluginDragLeft) (dragData :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PluginDragMoved](#PluginDragMoved) (dragData :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WindowFocused](#WindowFocused) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WindowFocusReleased](#WindowFocusReleased) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

4  overgenomen van [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector)

12  overgenomen van [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[DockWidgetPluginGui](/docs/nl-nl/reference/engine/classes/DockWidgetPluginGui)

---

API-referentie

Eigenschappen

Title

Parallel lezen

Mogelijkheden: UI

PluginGui.Title :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Methoden

BindToClose

Mogelijkheden: UI

PluginGui:BindToClose (function :[function](/docs/nl-nl/luau/functions) ) : ()

Parameters

|

function :[function](/docs/nl-nl/luau/functions)

Standaardwaarde: nil |

Teruggaves

()

Feedback geven

---

GetRelativeMousePosition

Plugin-beveiliging

Mogelijkheden: UI

PluginGui:GetRelativeMousePosition () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Codevoorbeelden

PluginGui:GetRelativeMousePosition

```

local RunService = game:GetService("RunService")

local widgetInfo = DockWidgetPluginGuiInfo.new(

	Enum.InitialDockState.Float,

	true,

	false, -- Ingeschakelde staat, overschrijven

	200,

	300, -- Grootte

	150,

	150 -- Minimale grootte

)

local testWidget = plugin:CreateDockWidgetPluginGuiAsync("TestWidget", widgetInfo)

function update()

	local v2 = testWidget:GetRelativeMousePosition()

	testWidget.Title = ("(%d, %d)"):format(v2.x, v2.y)

end

RunService.Stepped:Connect(update)

update()

```

Feedback geven

---

Evenementen

PluginDragDropped

Plugin-beveiliging

Mogelijkheden: UI

PluginGui.PluginDragDropped (dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Codevoorbeelden

Plugin Slepen en Neerzetten

```

assert(plugin, "Dit script moet worden uitgevoerd als een Studio-plugin")

local widgetInfo = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 300, 200)

local dragSourceWidget = plugin:CreateDockWidgetPluginGuiAsync("Slepen Bron", widgetInfo)

dragSourceWidget.Title = "Slepen Bron"

local textBox = Instance.new("TextBox")

textBox.Parent = dragSourceWidget

textBox.Size = UDim2.new(1, 0, 0, 32)

textBox.Text = "Hallo, plugin slepen"

local dragButton = Instance.new("TextButton")

dragButton.Size = UDim2.new(1, 0, 1, -32)

dragButton.Position = UDim2.new(0, 0, 0, 32)

dragButton.Text = "Bewerk de tekst hierboven, en begin hier te slepen"

dragButton.Parent = dragSourceWidget

function onMouseButton1Down()

	local dragData = {

		Sender = "SomeDragSource",

		MimeType = "text/plain",

		Data = textBox.Text,

		MouseIcon = "",

		DragIcon = "",

		HotSpot = Vector2.new(0, 0),

	}

	plugin:StartDrag(dragData)

end

dragButton.MouseButton1Down:Connect(onMouseButton1Down)

-- Dit widget zal drops ontvangen

local dragTargetWidget = plugin:CreateDockWidgetPluginGuiAsync("Neerzetten Doel", widgetInfo)

dragTargetWidget.Title = "Neerzetten Doel"

-- Deze TextLabel zal tonen wat er is neergezet

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.Text = "Drop hier..."

textLabel.Parent = dragTargetWidget

local function onDragDrop(dragData)

	if dragData.MimeType == "text/plain" then

		textLabel.Text = dragData.Data

	else

		textLabel.Text = dragData.MimeType

	end

end

dragTargetWidget.PluginDragDropped:Connect(onDragDrop)

dragTargetWidget.PluginDragEntered:Connect(function(_dragData)

	print("PluginDragEntered")

end)

dragTargetWidget.PluginDragLeft:Connect(function(_dragData)

	print("PluginDragLeft")

end)

dragTargetWidget.PluginDragMoved:Connect(function(_dragData)

	print("PluginDragMoved")

end)

```

Feedback geven

---

PluginDragEntered

Plugin-beveiliging

Mogelijkheden: UI

PluginGui.PluginDragEntered (dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Codevoorbeelden

Plugin Slepen en Neerzetten

```

assert(plugin, "Dit script moet worden uitgevoerd als een Studio-plugin")

local widgetInfo = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 300, 200)

local dragSourceWidget = plugin:CreateDockWidgetPluginGuiAsync("Slepen Bron", widgetInfo)

dragSourceWidget.Title = "Slepen Bron"

local textBox = Instance.new("TextBox")

textBox.Parent = dragSourceWidget

textBox.Size = UDim2.new(1, 0, 0, 32)

textBox.Text = "Hallo, plugin slepen"

local dragButton = Instance.new("TextButton")

dragButton.Size = UDim2.new(1, 0, 1, -32)

dragButton.Position = UDim2.new(0, 0, 0, 32)

dragButton.Text = "Bewerk de tekst hierboven, en begin hier te slepen"

dragButton.Parent = dragSourceWidget

function onMouseButton1Down()

	local dragData = {

		Sender = "SomeDragSource",

		MimeType = "text/plain",

		Data = textBox.Text,

		MouseIcon = "",

		DragIcon = "",

		HotSpot = Vector2.new(0, 0),

	}

	plugin:StartDrag(dragData)

end

dragButton.MouseButton1Down:Connect(onMouseButton1Down)

-- Dit widget zal drops ontvangen

local dragTargetWidget = plugin:CreateDockWidgetPluginGuiAsync("Neerzetten Doel", widgetInfo)

dragTargetWidget.Title = "Neerzetten Doel"

-- Deze TextLabel zal tonen wat er is neergezet

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.Text = "Drop hier..."

textLabel.Parent = dragTargetWidget

local function onDragDrop(dragData)

	if dragData.MimeType == "text/plain" then

		textLabel.Text = dragData.Data

	else

		textLabel.Text = dragData.MimeType

	end

end

dragTargetWidget.PluginDragDropped:Connect(onDragDrop)

dragTargetWidget.PluginDragEntered:Connect(function(_dragData)

	print("PluginDragEntered")

end)

dragTargetWidget.PluginDragLeft:Connect(function(_dragData)

	print("PluginDragLeft")

end)

dragTargetWidget.PluginDragMoved:Connect(function(_dragData)

	print("PluginDragMoved")

end)

```

Feedback geven

---

PluginDragLeft

Plugin-beveiliging

Mogelijkheden: UI

PluginGui.PluginDragLeft (dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Codevoorbeelden

Plugin Slepen en Neerzetten

```

assert(plugin, "Dit script moet worden uitgevoerd als een Studio-plugin")

local widgetInfo = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 300, 200)

local dragSourceWidget = plugin:CreateDockWidgetPluginGuiAsync("Slepen Bron", widgetInfo)

dragSourceWidget.Title = "Slepen Bron"

local textBox = Instance.new("TextBox")

textBox.Parent = dragSourceWidget

textBox.Size = UDim2.new(1, 0, 0, 32)

textBox.Text = "Hallo, plugin slepen"

local dragButton = Instance.new("TextButton")

dragButton.Size = UDim2.new(1, 0, 1, -32)

dragButton.Position = UDim2.new(0, 0, 0, 32)

dragButton.Text = "Bewerk de tekst hierboven, en begin hier te slepen"

dragButton.Parent = dragSourceWidget

function onMouseButton1Down()

	local dragData = {

		Sender = "SomeDragSource",

		MimeType = "text/plain",

		Data = textBox.Text,

		MouseIcon = "",

		DragIcon = "",

		HotSpot = Vector2.new(0, 0),

	}

	plugin:StartDrag(dragData)

end

dragButton.MouseButton1Down:Connect(onMouseButton1Down)

-- Dit widget zal drops ontvangen

local dragTargetWidget = plugin:CreateDockWidgetPluginGuiAsync("Neerzetten Doel", widgetInfo)

dragTargetWidget.Title = "Neerzetten Doel"

-- Deze TextLabel zal tonen wat er is neergezet

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.Text = "Drop hier..."

textLabel.Parent = dragTargetWidget

local function onDragDrop(dragData)

	if dragData.MimeType == "text/plain" then

		textLabel.Text = dragData.Data

	else

		textLabel.Text = dragData.MimeType

	end

end

dragTargetWidget.PluginDragDropped:Connect(onDragDrop)

dragTargetWidget.PluginDragEntered:Connect(function(_dragData)

	print("PluginDragEntered")

end)

dragTargetWidget.PluginDragLeft:Connect(function(_dragData)

	print("PluginDragLeft")

end)

dragTargetWidget.PluginDragMoved:Connect(function(_dragData)

	print("PluginDragMoved")

end)

```

Feedback geven

---

PluginDragMoved

Plugin-beveiliging

Mogelijkheden: UI

PluginGui.PluginDragMoved (dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Feedback geven

---

WindowFocused

Plugin-beveiliging

Mogelijkheden: UI

PluginGui.WindowFocused () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

Detecteren van PluginGui Focusstatus

```

local info = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 200, 50, 1, 1)

local widget = plugin:CreateDockWidgetPluginGuiAsync("TestWidget", info)

local function onFocusReleased()

	widget.Title = "Ik ben niet in focus :("

end

local function onFocused()

	widget.Title = "Ik ben in focus :D"

end

widget.WindowFocusReleased:Connect(onFocusReleased)

widget.WindowFocused:Connect(onFocused)

```

Feedback geven

---

WindowFocusReleased

Plugin-beveiliging

Mogelijkheden: UI

PluginGui.WindowFocusReleased () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

Detecteren van PluginGui Focusstatus

```

local info = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 200, 50, 1, 1)

local widget = plugin:CreateDockWidgetPluginGuiAsync("TestWidget", info)

local function onFocusReleased()

	widget.Title = "Ik ben niet in focus :("

end

local function onFocused()

	widget.Title = "Ik ben in focus :D"

end

widget.WindowFocusReleased:Connect(onFocusReleased)

widget.WindowFocused:Connect(onFocused)

```

Feedback geven

---

Ga naar

▼

PluginGui

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Title](#Title)

[Methoden](#methods)

[BindToClose()](#BindToClose)

[GetRelativeMousePosition()](#GetRelativeMousePosition)

[Evenementen](#events)

[PluginDragDropped](#PluginDragDropped)

[PluginDragEntered](#PluginDragEntered)

[PluginDragLeft](#PluginDragLeft)

[PluginDragMoved](#PluginDragMoved)

[WindowFocused](#WindowFocused)

[WindowFocusReleased](#WindowFocusReleased)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
