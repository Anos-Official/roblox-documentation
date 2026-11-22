<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ChatInputBarConfiguration -->

ChatInputBarConfiguration | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ChatInputBarConfiguration.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [TextChatConfigurations](/docs/en-us/reference/engine/classes/TextChatConfigurations)
8. /
9. [ChatInputBarConfiguration](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration)

English

Feedback

Engine Class

ChatInputBarConfiguration

Not Creatable

---

## Summary

Properties

|

[AbsolutePosition](#AbsolutePosition) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
| --- | --- |
|

[AbsoluteSize](#AbsoluteSize) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[AutocompleteEnabled](#AutocompleteEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[BackgroundColor3](#BackgroundColor3) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[BackgroundTransparency](#BackgroundTransparency) :[number](/docs/en-us/luau/numbers)

 |
|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[FontFace](#FontFace) :[Font](/docs/en-us/reference/engine/datatypes/Font)

 |
|

[IsFocused](#IsFocused) :[boolean](/docs/en-us/luau/booleans)

 |
|

[KeyboardKeyCode](#KeyboardKeyCode) :[Enum.KeyCode](/docs/en-us/reference/engine/enums/KeyCode)

 |
|

[PlaceholderColor3](#PlaceholderColor3) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[TargetTextChannel](#TargetTextChannel) :[TextChannel](/docs/en-us/reference/engine/classes/TextChannel)

 |
|

[TextBox](#TextBox) :[TextBox](/docs/en-us/reference/engine/classes/TextBox)

 |
|

[TextColor3](#TextColor3) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[TextSize](#TextSize) :[number](/docs/en-us/luau/numbers)

 |
|

[TextStrokeColor3](#TextStrokeColor3) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[TextStrokeTransparency](#TextStrokeTransparency) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Get Total Chat UI Bounds

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local windowConfig = TextChatService.ChatWindowConfiguration

local inputBarConfig = TextChatService.ChatInputBarConfiguration

local function getTotalChatBounds()

	local windowPos = windowConfig.AbsolutePosition

	local windowSize = windowConfig.AbsoluteSize

	local inputPos = inputBarConfig.AbsolutePosition

	local inputSize = inputBarConfig.AbsoluteSize

	-- Compute the union of both rectangles to get total chat UI bounds.

	-- The reported values do not include the decorative bevel at the top

	-- and bottom edges of the chat window.

	local topLeft = Vector2.new(

		math.min(windowPos.X, inputPos.X),

		math.min(windowPos.Y, inputPos.Y)

	)

	local bottomRight = Vector2.new(

		math.max(windowPos.X + windowSize.X, inputPos.X + inputSize.X),

		math.max(windowPos.Y + windowSize.Y, inputPos.Y + inputSize.Y)

	)

	return topLeft, bottomRight - topLeft

end

-- Wait for chat UI to initialize and report absolute values

task.wait(2)

local position, size = getTotalChatBounds()

print("Total chat UI position:", position)

print("Total chat UI size:", size)

-- Overlay a semi-transparent frame to visually verify the bounds

local screenGui = Instance.new("ScreenGui")

screenGui.Name = "ChatBoundsDebug"

screenGui.DisplayOrder = 100

screenGui.Parent = playerGui

local frame = Instance.new("Frame")

frame.Position = UDim2.fromOffset(position.X, position.Y)

frame.Size = UDim2.fromOffset(size.X, size.Y)

frame.BackgroundColor3 = Color3.fromRGB(255, 0, 0)

frame.BackgroundTransparency = 0.5

frame.BorderSizePixel = 2

frame.BorderColor3 = Color3.fromRGB(255, 0, 0)

frame.Parent = screenGui

```

---

API Reference

Properties

AbsolutePosition

Read Only

Not Replicated

Capabilities: Chat

ChatInputBarConfiguration.AbsolutePosition :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

AbsoluteSize

Read Only

Not Replicated

Capabilities: Chat

ChatInputBarConfiguration.AbsoluteSize :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

AutocompleteEnabled

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.AutocompleteEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

BackgroundColor3

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.BackgroundColor3 :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

BackgroundTransparency

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.BackgroundTransparency :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Enabled

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

FontFace

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.FontFace :[Font](/docs/en-us/reference/engine/datatypes/Font)

Provide feedback

---

IsFocused

Read Only

Not Replicated

Capabilities: Chat

ChatInputBarConfiguration.IsFocused :[boolean](/docs/en-us/luau/booleans)

Code Samples

Typing Indicator Bubble

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local ChatInputBarConfiguration = TextChatService:FindFirstChildOfClass("ChatInputBarConfiguration")

local BubbleChatConfiguration = TextChatService:FindFirstChildOfClass("BubbleChatConfiguration")

local LocalPlayer = Players.LocalPlayer

local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()

-- Set up TextLabel

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.fromScale(1, 1)

textLabel.Text = ". . ."

textLabel.BackgroundColor3 = BubbleChatConfiguration.BackgroundColor3

textLabel.BorderColor3 = BubbleChatConfiguration.BackgroundColor3

textLabel.BackgroundTransparency = BubbleChatConfiguration.BackgroundTransparency

textLabel.TextColor3 = BubbleChatConfiguration.TextColor3

textLabel.FontFace = BubbleChatConfiguration.FontFace

textLabel.TextSize = BubbleChatConfiguration.TextSize

-- Parent a UICorner to the TextLabel to have rounded corners

local uiCorner = Instance.new("UICorner")

uiCorner.CornerRadius = UDim.new(0, 12)

uiCorner.Parent = textLabel

-- Set up Billboard

local typingIndicatorBillboard = Instance.new("BillboardGui")

typingIndicatorBillboard.Enabled = false

typingIndicatorBillboard.Size = UDim2.fromScale(1, 1)

typingIndicatorBillboard.StudsOffsetWorldSpace = Vector3.new(-0, 4, 0)

typingIndicatorBillboard.Adornee = Character

textLabel.Parent = typingIndicatorBillboard

typingIndicatorBillboard.Parent = LocalPlayer:FindFirstChildOfClass("PlayerGui")

ChatInputBarConfiguration:GetPropertyChangedSignal("IsFocused"):Connect(function()

	-- Enable the typing indicator when the input bar is focused and disable otherwise

	typingIndicatorBillboard.Enabled = ChatInputBarConfiguration.IsFocused

end)

```

Provide feedback

---

KeyboardKeyCode

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.KeyboardKeyCode :[Enum.KeyCode](/docs/en-us/reference/engine/enums/KeyCode)

Provide feedback

---

PlaceholderColor3

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.PlaceholderColor3 :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

TargetTextChannel

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.TargetTextChannel :[TextChannel](/docs/en-us/reference/engine/classes/TextChannel)

Provide feedback

---

TextBox

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.TextBox :[TextBox](/docs/en-us/reference/engine/classes/TextBox)

Provide feedback

---

TextColor3

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.TextColor3 :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

TextSize

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.TextSize :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TextStrokeColor3

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.TextStrokeColor3 :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

TextStrokeTransparency

Read Parallel

Capabilities: Chat

ChatInputBarConfiguration.TextStrokeTransparency :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

ChatInputBarConfiguration

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[AbsolutePosition](#AbsolutePosition)

[AbsoluteSize](#AbsoluteSize)

[AutocompleteEnabled](#AutocompleteEnabled)

[BackgroundColor3](#BackgroundColor3)

[BackgroundTransparency](#BackgroundTransparency)

[Enabled](#Enabled)

[FontFace](#FontFace)

[IsFocused](#IsFocused)

[KeyboardKeyCode](#KeyboardKeyCode)

[PlaceholderColor3](#PlaceholderColor3)

[TargetTextChannel](#TargetTextChannel)

[TextBox](#TextBox)

[TextColor3](#TextColor3)

[TextSize](#TextSize)

[TextStrokeColor3](#TextStrokeColor3)

[TextStrokeTransparency](#TextStrokeTransparency)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
