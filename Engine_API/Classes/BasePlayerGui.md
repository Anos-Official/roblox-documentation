<!-- Source: https://create.roblox.com/docs/reference/engine/classes/BasePlayerGui -->

BasePlayerGui | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/BasePlayerGui.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [BasePlayerGui](/docs/reference/engine/classes/BasePlayerGui)

English

Feedback

Engine Class

BasePlayerGui

Not Creatable

---

## Summary

Methods

|

[GetGuiObjectsAtPosition](#GetGuiObjectsAtPosition) (x :  [number](/docs/luau/numbers) , y :  [number](/docs/luau/numbers) ) : Instances

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[CoreGui](/docs/reference/engine/classes/CoreGui) , [PlayerGui](/docs/reference/engine/classes/PlayerGui) , [StarterGui](/docs/reference/engine/classes/StarterGui)

---

API Reference

Methods

GetGuiObjectsAtPosition

Capabilities: UI

BasePlayerGui:GetGuiObjectsAtPosition (

x :[number](/docs/luau/numbers) , y :[number](/docs/luau/numbers)

) : Instances

Parameters

|

x :[number](/docs/luau/numbers)

 |
|

y :[number](/docs/luau/numbers)

 |

Returns

Instances

Code Samples

Selecting GUIs at a Position

```

local UserInputService = game:GetService("UserInputService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

-- Create a Folder and ScreenGui to contain the highlight Frames

local highlights = Instance.new("Folder")

highlights.Name = "Highlights"

highlights.Parent = playerGui

local highlightsContainer = Instance.new("ScreenGui")

highlightsContainer.Name = "Container"

highlightsContainer.Parent = highlights

highlightsContainer.DisplayOrder = 99999

-- Creates a semi-transparent yellow Frame on top of the gui with the same AbsoluteSize and AbsolutePosition

local function highlightAsFrame(gui)

	local highlight = Instance.new("Frame")

	highlight.Name = "Highlight"

	highlight.Parent = highlightsContainer

	highlight.Size = UDim2.new(0, gui.AbsoluteSize.X, 0, gui.AbsoluteSize.Y)

	highlight.Position = UDim2.new(0, gui.AbsolutePosition.X, 0, gui.AbsolutePosition.Y)

	highlight.BackgroundColor3 = Color3.fromRGB(255, 255, 10) -- Yellow

	highlight.BackgroundTransparency = 0.75

	highlight.BorderSizePixel = 0

	highlight.LayoutOrder = gui.LayoutOrder - 1

end

-- Use GetGuiObjectsAtPosition to get and highlight all GuiObjects at the input's position

local function highlightGui(input, _gameProcessed)

	local pos = input.Position

	local guisAtPosition = playerGui:GetGuiObjectsAtPosition(pos.X, pos.Y)

	highlightsContainer:ClearAllChildren()

	for _, gui in ipairs(guisAtPosition) do

		if gui:IsA("GuiObject") then

			highlightAsFrame(gui)

		end

	end

end

-- Fire highlightGui on InputBegan if input is of type MouseButton1 of Touch

local function InputBegan(input, gameProcessed)

	local inputType = input.UserInputType

	local touch = Enum.UserInputType.Touch

	local mouse1 = Enum.UserInputType.MouseButton1

	if inputType == touch or inputType == mouse1 then

		highlightGui(input, gameProcessed)

	end

end

UserInputService.InputBegan:Connect(InputBegan)

```

Provide feedback

---

Jump to

▼

BasePlayerGui

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetGuiObjectsAtPosition()](#GetGuiObjectsAtPosition)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
