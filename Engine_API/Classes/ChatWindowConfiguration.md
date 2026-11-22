<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ChatWindowConfiguration -->

ChatWindowConfiguration | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ChatWindowConfiguration.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [TextChatConfigurations](/docs/reference/engine/classes/TextChatConfigurations)
8. /
9. [ChatWindowConfiguration](/docs/reference/engine/classes/ChatWindowConfiguration)

English

Feedback

Engine Class

ChatWindowConfiguration

Not Creatable

---

## Summary

Properties

|

[AbsolutePosition](#AbsolutePosition) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
| --- | --- |
|

[AbsoluteSize](#AbsoluteSize) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[BackgroundColor3](#BackgroundColor3) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[BackgroundTransparency](#BackgroundTransparency) :[number](/docs/luau/numbers)

 |
|

[Enabled](#Enabled) :[boolean](/docs/luau/booleans)

 |
|

[FontFace](#FontFace) :[Font](/docs/reference/engine/datatypes/Font)

 |
|

[HeightScale](#HeightScale) :[number](/docs/luau/numbers)

 |
|

[HorizontalAlignment](#HorizontalAlignment) :[Enum.HorizontalAlignment](/docs/reference/engine/enums/HorizontalAlignment)

 |
|

[TextColor3](#TextColor3) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[TextSize](#TextSize) :[number](/docs/luau/numbers)

 |
|

[TextStrokeColor3](#TextStrokeColor3) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[TextStrokeTransparency](#TextStrokeTransparency) :[number](/docs/luau/numbers)

 |
|

[VerticalAlignment](#VerticalAlignment) :[Enum.VerticalAlignment](/docs/reference/engine/enums/VerticalAlignment)

 |
|

[WidthScale](#WidthScale) :[number](/docs/luau/numbers)

 |

Methods

|

[DeriveNewMessageProperties](#DeriveNewMessageProperties) () :[ChatWindowMessageProperties](/docs/reference/engine/classes/ChatWindowMessageProperties)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

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

ChatWindowConfiguration.AbsolutePosition :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

AbsoluteSize

Read Only

Not Replicated

Capabilities: Chat

ChatWindowConfiguration.AbsoluteSize :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

BackgroundColor3

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.BackgroundColor3 :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

BackgroundTransparency

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.BackgroundTransparency :[number](/docs/luau/numbers)

Provide feedback

---

Enabled

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.Enabled :[boolean](/docs/luau/booleans)

Provide feedback

---

FontFace

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.FontFace :[Font](/docs/reference/engine/datatypes/Font)

Provide feedback

---

HeightScale

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.HeightScale :[number](/docs/luau/numbers)

Provide feedback

---

HorizontalAlignment

Capabilities: Chat

ChatWindowConfiguration.HorizontalAlignment :[Enum.HorizontalAlignment](/docs/reference/engine/enums/HorizontalAlignment)

Provide feedback

---

TextColor3

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.TextColor3 :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

TextSize

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.TextSize :[number](/docs/luau/numbers)

Provide feedback

---

TextStrokeColor3

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.TextStrokeColor3 :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

TextStrokeTransparency

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.TextStrokeTransparency :[number](/docs/luau/numbers)

Provide feedback

---

VerticalAlignment

Capabilities: Chat

ChatWindowConfiguration.VerticalAlignment :[Enum.VerticalAlignment](/docs/reference/engine/enums/VerticalAlignment)

Provide feedback

---

WidthScale

Read Parallel

Capabilities: Chat

ChatWindowConfiguration.WidthScale :[number](/docs/luau/numbers)

Provide feedback

---

Methods

DeriveNewMessageProperties

Capabilities: Chat

ChatWindowConfiguration:DeriveNewMessageProperties () :[ChatWindowMessageProperties](/docs/reference/engine/classes/ChatWindowMessageProperties)

Returns

[ChatWindowMessageProperties](/docs/reference/engine/classes/ChatWindowMessageProperties)

Code Samples

CanUsersDirectChatAsync

```

local TextChatService = game:GetService("TextChatService")

local directChatParticipants = TextChatService:CanUsersDirectChatAsync(userId1, { userId2 })

-- Check for eligible participants

if #directChatParticipants > 0 then

	local directChannel = Instance.new("TextChannel")

	directChannel.Parent = TextChatService

	for _, participant in directChatParticipants do

		directChannel:AddUserAsync(participant)

	end

	return directChannel

end

warn("Could not create TextChannel. Not enough eligible users.")

return nil

```

Derive New Message Properties

```

local TextChatService = game:GetService("TextChatService")

local ChatWindowConfiguration = TextChatService.ChatWindowConfiguration

TextChatService.OnChatWindowAdded = function(textChatMessage)

  local properties = ChatWindowConfiguration:DeriveNewMessageProperties()

  if textChatMessage.Metadata == "Important" then

    properties.TextColor3 = Color3.fromRGB(255, 0, 0)

  end

  return properties

end

```

Provide feedback

---

Jump to

▼

ChatWindowConfiguration

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[AbsolutePosition](#AbsolutePosition)

[AbsoluteSize](#AbsoluteSize)

[BackgroundColor3](#BackgroundColor3)

[BackgroundTransparency](#BackgroundTransparency)

[Enabled](#Enabled)

[FontFace](#FontFace)

[HeightScale](#HeightScale)

[HorizontalAlignment](#HorizontalAlignment)

[TextColor3](#TextColor3)

[TextSize](#TextSize)

[TextStrokeColor3](#TextStrokeColor3)

[TextStrokeTransparency](#TextStrokeTransparency)

[VerticalAlignment](#VerticalAlignment)

[WidthScale](#WidthScale)

[Methods](#methods)

[DeriveNewMessageProperties()](#DeriveNewMessageProperties)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
