<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration -->

ChatInputBarConfiguration | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TextChatConfigurations](/docs/nl-nl/reference/engine/classes/TextChatConfigurations)
8. /
9. [ChatInputBarConfiguration](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration)

Nederlands

Feedback

Engine-klasse

ChatInputBarConfiguration

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AbsolutePosition](#AbsolutePosition) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
| --- | --- |
|

[AbsoluteSize](#AbsoluteSize) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[AutocompleteEnabled](#AutocompleteEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[BackgroundColor3](#BackgroundColor3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[BackgroundTransparency](#BackgroundTransparency) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[FontFace](#FontFace) :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

 |
|

[IsFocused](#IsFocused) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[KeyboardKeyCode](#KeyboardKeyCode) :[Enum.KeyCode](/docs/nl-nl/reference/engine/enums/KeyCode)

 |
|

[PlaceholderColor3](#PlaceholderColor3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[TargetTextChannel](#TargetTextChannel) :[TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)

 |
|

[TextBox](#TextBox) :[TextBox](/docs/nl-nl/reference/engine/classes/TextBox)

 |
|

[TextColor3](#TextColor3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[TextSize](#TextSize) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TextStrokeColor3](#TextStrokeColor3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[TextStrokeTransparency](#TextStrokeTransparency) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Krijg Totale Chat UI Grenzen

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

	-- Bereken de unie van beide rechthoeken om totale chat UI grenzen te krijgen.

	-- De gerapporteerde waarden omvatten niet de decoratieve afschuin aan de boven

	-- en onderrand van het chatvenster.

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

-- Wacht tot de chat UI is geïnitialiseerd en rapporteer absolute waarden

task.wait(2)

local position, size = getTotalChatBounds()

print("Totale chat UI positie:", position)

print("Totale chat UI grootte:", size)

-- Overlay een semi-transparante frame om de grenzen visueel te verifiëren

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

API-referentie

Eigenschappen

AbsolutePosition

Alleen-lezen

Niet gerepliceerd

Mogelijkheden: Chat

ChatInputBarConfiguration.AbsolutePosition :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

AbsoluteSize

Alleen-lezen

Niet gerepliceerd

Mogelijkheden: Chat

ChatInputBarConfiguration.AbsoluteSize :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

AutocompleteEnabled

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.AutocompleteEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

BackgroundColor3

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.BackgroundColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

BackgroundTransparency

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.BackgroundTransparency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

FontFace

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.FontFace :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

Feedback geven

---

IsFocused

Alleen-lezen

Niet gerepliceerd

Mogelijkheden: Chat

ChatInputBarConfiguration.IsFocused :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Typen Indicator Bubble

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local ChatInputBarConfiguration = TextChatService:FindFirstChildOfClass("ChatInputBarConfiguration")

local BubbleChatConfiguration = TextChatService:FindFirstChildOfClass("BubbleChatConfiguration")

local LocalPlayer = Players.LocalPlayer

local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()

-- Stel de TextLabel in

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.fromScale(1, 1)

textLabel.Text = ". . ."

textLabel.BackgroundColor3 = BubbleChatConfiguration.BackgroundColor3

textLabel.BorderColor3 = BubbleChatConfiguration.BackgroundColor3

textLabel.BackgroundTransparency = BubbleChatConfiguration.BackgroundTransparency

textLabel.TextColor3 = BubbleChatConfiguration.TextColor3

textLabel.FontFace = BubbleChatConfiguration.FontFace

textLabel.TextSize = BubbleChatConfiguration.TextSize

-- Voeg een UICorner toe aan de TextLabel voor afgeronde hoeken

local uiCorner = Instance.new("UICorner")

uiCorner.CornerRadius = UDim.new(0, 12)

uiCorner.Parent = textLabel

-- Stel de Billboard in

local typingIndicatorBillboard = Instance.new("BillboardGui")

typingIndicatorBillboard.Enabled = false

typingIndicatorBillboard.Size = UDim2.fromScale(1, 1)

typingIndicatorBillboard.StudsOffsetWorldSpace = Vector3.new(-0, 4, 0)

typingIndicatorBillboard.Adornee = Character

textLabel.Parent = typingIndicatorBillboard

typingIndicatorBillboard.Parent = LocalPlayer:FindFirstChildOfClass("PlayerGui")

ChatInputBarConfiguration:GetPropertyChangedSignal("IsFocused"):Connect(function()

	-- Schakel de typen indicator in wanneer de invoerbalk gefocust is en schakel deze anders uit

	typingIndicatorBillboard.Enabled = ChatInputBarConfiguration.IsFocused

end)

```

Feedback geven

---

KeyboardKeyCode

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.KeyboardKeyCode :[Enum.KeyCode](/docs/nl-nl/reference/engine/enums/KeyCode)

Feedback geven

---

PlaceholderColor3

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.PlaceholderColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

TargetTextChannel

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.TargetTextChannel :[TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)

Feedback geven

---

TextBox

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.TextBox :[TextBox](/docs/nl-nl/reference/engine/classes/TextBox)

Feedback geven

---

TextColor3

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.TextColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

TextSize

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.TextSize :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TextStrokeColor3

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.TextStrokeColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

TextStrokeTransparency

Parallel lezen

Mogelijkheden: Chat

ChatInputBarConfiguration.TextStrokeTransparency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

ChatInputBarConfiguration

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

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

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
