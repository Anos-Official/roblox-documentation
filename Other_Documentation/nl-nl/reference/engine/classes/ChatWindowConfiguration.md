<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration -->

ChatWindowConfiguration | Documentatie - Roblox Creator Hub

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
9. [ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration)

Nederlands

Feedback

Engine-klasse

ChatWindowConfiguration

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ChatWindowConfiguration)  om deze pagina in het Engels te bekijken.

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

[HeightScale](#HeightScale) :[number](/docs/nl-nl/luau/numbers)

 |
|

[HorizontalAlignment](#HorizontalAlignment) :[Enum.HorizontalAlignment](/docs/nl-nl/reference/engine/enums/HorizontalAlignment)

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
|

[VerticalAlignment](#VerticalAlignment) :[Enum.VerticalAlignment](/docs/nl-nl/reference/engine/enums/VerticalAlignment)

 |
|

[WidthScale](#WidthScale) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[DeriveNewMessageProperties](#DeriveNewMessageProperties) () :[ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties)

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

ChatWindowConfiguration.AbsolutePosition :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

AbsoluteSize

Alleen-lezen

Niet gerepliceerd

Mogelijkheden: Chat

ChatWindowConfiguration.AbsoluteSize :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

BackgroundColor3

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.BackgroundColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

BackgroundTransparency

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.BackgroundTransparency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

FontFace

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.FontFace :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

Feedback geven

---

HeightScale

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.HeightScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

HorizontalAlignment

Mogelijkheden: Chat

ChatWindowConfiguration.HorizontalAlignment :[Enum.HorizontalAlignment](/docs/nl-nl/reference/engine/enums/HorizontalAlignment)

Feedback geven

---

TextColor3

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.TextColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

TextSize

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.TextSize :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TextStrokeColor3

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.TextStrokeColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

TextStrokeTransparency

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.TextStrokeTransparency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

VerticalAlignment

Mogelijkheden: Chat

ChatWindowConfiguration.VerticalAlignment :[Enum.VerticalAlignment](/docs/nl-nl/reference/engine/enums/VerticalAlignment)

Feedback geven

---

WidthScale

Parallel lezen

Mogelijkheden: Chat

ChatWindowConfiguration.WidthScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

DeriveNewMessageProperties

Mogelijkheden: Chat

ChatWindowConfiguration:DeriveNewMessageProperties () :[ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties)

Teruggaves

[ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties)

Codevoorbeelden

CanUsersDirectChatAsync

```

local TextChatService = game:GetService("TextChatService")

local directChatParticipants = TextChatService:CanUsersDirectChatAsync(userId1, { userId2 })

-- Controleer op in aanmerking komende deelnemers

if #directChatParticipants > 0 then

	local directChannel = Instance.new("TextChannel")

	directChannel.Parent = TextChatService

	for _, participant in directChatParticipants do

		directChannel:AddUserAsync(participant)

	end

	return directChannel

end

warn("Kon geen TextChannel maken. Niet genoeg in aanmerking komende gebruikers.")

return nil

```

Afgeleide Nieuwe Bericht Eigenschappen

```

local TextChatService = game:GetService("TextChatService")

local ChatWindowConfiguration = TextChatService.ChatWindowConfiguration

TextChatService.OnChatWindowAdded = function(textChatMessage)

  local properties = ChatWindowConfiguration:DeriveNewMessageProperties()

  if textChatMessage.Metadata == "Belangrijk" then

    properties.TextColor3 = Color3.fromRGB(255, 0, 0)

  end

  return properties

end

```

Feedback geven

---

Ga naar

▼

ChatWindowConfiguration

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

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

[Methoden](#methods)

[DeriveNewMessageProperties()](#DeriveNewMessageProperties)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
