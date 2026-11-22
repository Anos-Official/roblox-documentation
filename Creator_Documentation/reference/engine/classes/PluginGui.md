<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/PluginGui -->

PluginGui | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PluginGui.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/en-us/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/en-us/reference/engine/classes/GuiBase2d)
10. /
11. [LayerCollector](/docs/en-us/reference/engine/classes/LayerCollector)
12. /
13. [PluginGui](/docs/en-us/reference/engine/classes/PluginGui)

English

Feedback

Engine Class

PluginGui

Not Creatable

Not Replicated

---

## Summary

Properties

|

[Title](#Title) :[string](/docs/en-us/luau/strings)

 |
| --- | --- |

Methods

|

[BindToClose](#BindToClose) (function :  [function](/docs/en-us/luau/functions) ) : ()

 |
|

[GetRelativeMousePosition](#GetRelativeMousePosition) () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |

Events

|

[PluginDragDropped](#PluginDragDropped) (dragData :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PluginDragEntered](#PluginDragEntered) (dragData :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PluginDragLeft](#PluginDragLeft) (dragData :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PluginDragMoved](#PluginDragMoved) (dragData :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WindowFocused](#WindowFocused) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WindowFocusReleased](#WindowFocusReleased) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

4  inherited from [LayerCollector](/docs/en-us/reference/engine/classes/LayerCollector)

12  inherited from [GuiBase2d](/docs/en-us/reference/engine/classes/GuiBase2d)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[DockWidgetPluginGui](/docs/en-us/reference/engine/classes/DockWidgetPluginGui)

---

API Reference

Properties

Title

Read Parallel

Capabilities: UI

PluginGui.Title :[string](/docs/en-us/luau/strings)

Provide feedback

---

Methods

BindToClose

Capabilities: UI

PluginGui:BindToClose (function :[function](/docs/en-us/luau/functions) ) : ()

Parameters

|

function :[function](/docs/en-us/luau/functions)

Default Value: nil |

Returns

()

Provide feedback

---

GetRelativeMousePosition

Plugin Security

Capabilities: UI

PluginGui:GetRelativeMousePosition () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Code Samples

PluginGui:GetRelativeMousePosition

```

local RunService = game:GetService("RunService")

local widgetInfo = DockWidgetPluginGuiInfo.new(

	Enum.InitialDockState.Float,

	true,

	false, -- Enabled state, override

	200,

	300, -- Size

	150,

	150 -- Minimum size

)

local testWidget = plugin:CreateDockWidgetPluginGuiAsync("TestWidget", widgetInfo)

function update()

	local v2 = testWidget:GetRelativeMousePosition()

	testWidget.Title = ("(%d, %d)"):format(v2.x, v2.y)

end

RunService.Stepped:Connect(update)

update()

```

Provide feedback

---

Events

PluginDragDropped

Plugin Security

Capabilities: UI

PluginGui.PluginDragDropped (dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Code Samples

Plugin Drag and Drop

```

assert(plugin, "This script must be run as a Studio plugin")

local widgetInfo = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 300, 200)

local dragSourceWidget = plugin:CreateDockWidgetPluginGuiAsync("Drag Source", widgetInfo)

dragSourceWidget.Title = "Drag Source"

local textBox = Instance.new("TextBox")

textBox.Parent = dragSourceWidget

textBox.Size = UDim2.new(1, 0, 0, 32)

textBox.Text = "Hello, plugin drags"

local dragButton = Instance.new("TextButton")

dragButton.Size = UDim2.new(1, 0, 1, -32)

dragButton.Position = UDim2.new(0, 0, 0, 32)

dragButton.Text = "Edit the text above, then start drag here"

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

-- This widget will receive drops

local dragTargetWidget = plugin:CreateDockWidgetPluginGuiAsync("Drop Target", widgetInfo)

dragTargetWidget.Title = "Drop Target"

-- This TextLabel will display what was dropped

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.Text = "Drop here..."

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

Provide feedback

---

PluginDragEntered

Plugin Security

Capabilities: UI

PluginGui.PluginDragEntered (dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Code Samples

Plugin Drag and Drop

```

assert(plugin, "This script must be run as a Studio plugin")

local widgetInfo = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 300, 200)

local dragSourceWidget = plugin:CreateDockWidgetPluginGuiAsync("Drag Source", widgetInfo)

dragSourceWidget.Title = "Drag Source"

local textBox = Instance.new("TextBox")

textBox.Parent = dragSourceWidget

textBox.Size = UDim2.new(1, 0, 0, 32)

textBox.Text = "Hello, plugin drags"

local dragButton = Instance.new("TextButton")

dragButton.Size = UDim2.new(1, 0, 1, -32)

dragButton.Position = UDim2.new(0, 0, 0, 32)

dragButton.Text = "Edit the text above, then start drag here"

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

-- This widget will receive drops

local dragTargetWidget = plugin:CreateDockWidgetPluginGuiAsync("Drop Target", widgetInfo)

dragTargetWidget.Title = "Drop Target"

-- This TextLabel will display what was dropped

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.Text = "Drop here..."

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

Provide feedback

---

PluginDragLeft

Plugin Security

Capabilities: UI

PluginGui.PluginDragLeft (dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Code Samples

Plugin Drag and Drop

```

assert(plugin, "This script must be run as a Studio plugin")

local widgetInfo = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 300, 200)

local dragSourceWidget = plugin:CreateDockWidgetPluginGuiAsync("Drag Source", widgetInfo)

dragSourceWidget.Title = "Drag Source"

local textBox = Instance.new("TextBox")

textBox.Parent = dragSourceWidget

textBox.Size = UDim2.new(1, 0, 0, 32)

textBox.Text = "Hello, plugin drags"

local dragButton = Instance.new("TextButton")

dragButton.Size = UDim2.new(1, 0, 1, -32)

dragButton.Position = UDim2.new(0, 0, 0, 32)

dragButton.Text = "Edit the text above, then start drag here"

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

-- This widget will receive drops

local dragTargetWidget = plugin:CreateDockWidgetPluginGuiAsync("Drop Target", widgetInfo)

dragTargetWidget.Title = "Drop Target"

-- This TextLabel will display what was dropped

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.Text = "Drop here..."

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

Provide feedback

---

PluginDragMoved

Plugin Security

Capabilities: UI

PluginGui.PluginDragMoved (dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

dragData :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Provide feedback

---

WindowFocused

Plugin Security

Capabilities: UI

PluginGui.WindowFocused () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Detecting PluginGui Focus State

```

local info = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 200, 50, 1, 1)

local widget = plugin:CreateDockWidgetPluginGuiAsync("TestWidget", info)

local function onFocusReleased()

	widget.Title = "I'm not in focus :("

end

local function onFocused()

	widget.Title = "I'm in focus :D"

end

widget.WindowFocusReleased:Connect(onFocusReleased)

widget.WindowFocused:Connect(onFocused)

```

Provide feedback

---

WindowFocusReleased

Plugin Security

Capabilities: UI

PluginGui.WindowFocusReleased () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Detecting PluginGui Focus State

```

local info = DockWidgetPluginGuiInfo.new(Enum.InitialDockState.Float, true, true, 200, 50, 1, 1)

local widget = plugin:CreateDockWidgetPluginGuiAsync("TestWidget", info)

local function onFocusReleased()

	widget.Title = "I'm not in focus :("

end

local function onFocused()

	widget.Title = "I'm in focus :D"

end

widget.WindowFocusReleased:Connect(onFocusReleased)

widget.WindowFocused:Connect(onFocused)

```

Provide feedback

---

Jump to

▼

PluginGui

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Title](#Title)

[Methods](#methods)

[BindToClose()](#BindToClose)

[GetRelativeMousePosition()](#GetRelativeMousePosition)

[Events](#events)

[PluginDragDropped](#PluginDragDropped)

[PluginDragEntered](#PluginDragEntered)

[PluginDragLeft](#PluginDragLeft)

[PluginDragMoved](#PluginDragMoved)

[WindowFocused](#WindowFocused)

[WindowFocusReleased](#WindowFocusReleased)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
