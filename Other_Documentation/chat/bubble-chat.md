<!-- Source: https://create.roblox.com/docs/chat/bubble-chat -->

Customize bubble chat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/bubble-chat.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/chat/in-experience-text-chat)

# Customize bubble chat

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/bubble-chat.md)

With [TextChatService](/docs/chat/in-experience-text-chat) , you can use bubble chat to display customizable speech chat bubbles above user avatars and NPCs. Bubble chat can make your game more visually immersive and help users easily identify messages and their speakers in a contextually relevant manner. This feature is especially useful for games where users need to focus on the content in the meantime communicating with others in a less obtrusive way.

## [Enable bubble chat](#enable-bubble-chat)[](#enable-bubble-chat)

To enable bubble chat in your game:

1.

In the Explorer  window, select [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration)  under [TextChatService](/docs/reference/engine/classes/TextChatService) .

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-BubbleChatConfiguration.png)

2.

In the Properties  window, check the [BubbleChatConfiguration.Enabled](/docs/reference/engine/classes/BubbleChatConfiguration#Enabled)  checkbox.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-BubbleChatConfiguration-Enabled.png)

## [Bubble customization](#bubble-customization)[](#bubble-customization)

After enabling bubble chat, you can customize the appearance and behavior of your chat bubbles to match your game's theme. Use the Properties  window of [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration)  for [basic](#basic-customization)  changes like text color and spacing, or implement [advanced](#advanced-customization)  customization for bubble background images and other visual adjustments.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-BubbleChatConfiguration.png)

Alternatively, add a [LocalScript](/docs/reference/engine/classes/LocalScript)  in [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts)  with all your customization settings. This allows the engine to apply your customizations during runtime, overriding the settings in Studio. It's useful for adding special effects to chat bubbles when users trigger certain events or conditions.

### [Basic customization](#basic-customization)[](#basic-customization)

The following table shows common bubble chat customization properties. For a full list of customization properties, see [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration) .

Appearance Behavior

| Property | | Description | | Default |
| --- | --- |
| [BackgroundColor3](/docs/reference/engine/classes/BubbleChatConfiguration#BackgroundColor3) | | Background color of bubbles in [Color3](/docs/reference/engine/datatypes/Color3) . | | [250, 250, 250] |
| [FontFace](/docs/reference/engine/classes/BubbleChatConfiguration#FontFace) | | [Font](/docs/reference/engine/datatypes/Font)  of the bubble text. | | [BuilderSansMedium](/docs/reference/engine/enums/Font#BuilderSansMedium) |
| [TextColor3](/docs/reference/engine/classes/BubbleChatConfiguration#TextColor3) | | Color of bubble text in [Color3](/docs/reference/engine/datatypes/Color3) . | | [57, 59, 61] |
| [TextSize](/docs/reference/engine/classes/BubbleChatConfiguration#TextSize) | | Size of bubble text. | | 16 |

### [Advanced customization](#advanced-customization)[](#advanced-customization)

For advanced customization of your bubble, add UI objects representing certain aspects of the bubble appearance as children under [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration) , including:

-

[ImageLabel](/docs/reference/engine/classes/ImageLabel)  for background image settings.

-

[UIGradient](/docs/reference/engine/classes/UIGradient)  for background gradient settings.

-

[UICorner](/docs/reference/engine/classes/UICorner)  for the corner shape of bubbles.

-

[UIPadding](/docs/reference/engine/classes/UIPadding)  for the padding space between the text and bubble edges, relative to the parent's normal size.

After adding these objects, you can modify properties of these objects applicable to chat bubbles for advanced bubble customization. The following example [LocalScript](/docs/reference/engine/classes/LocalScript)  adds a background image and sharp corners to bubbles:

Advanced Bubble Customization

```

local TextChatService = game:GetService("TextChatService")

local bubbleChatConfiguration = TextChatService.BubbleChatConfiguration

bubbleChatConfiguration.TailVisible = false

bubbleChatConfiguration.TextColor3 = Color3.fromRGB(220, 50, 50)

bubbleChatConfiguration.FontFace = Font.fromEnum(Enum.Font.LuckiestGuy)

local bubbleUICorner = bubbleChatConfiguration:FindFirstChildOfClass("UICorner")

if not bubbleUICorner then

	bubbleUICorner = Instance.new("UICorner")

	bubbleUICorner.Parent = bubbleChatConfiguration

end

bubbleUICorner.CornerRadius = UDim.new(0, 0)

local bubbleUIPadding = bubbleChatConfiguration:FindFirstChildOfClass("UIPadding")

if not bubbleUIPadding then

	bubbleUIPadding = Instance.new("UIPadding")

	bubbleUIPadding.Parent = bubbleChatConfiguration

end

bubbleUIPadding.PaddingTop = UDim.new(0, 20)

bubbleUIPadding.PaddingRight = UDim.new(0, 10)

bubbleUIPadding.PaddingBottom = UDim.new(0, 15)

bubbleUIPadding.PaddingLeft = UDim.new(0, 10)

local bubbleImageLabel = bubbleChatConfiguration:FindFirstChildOfClass("ImageLabel")

if not bubbleImageLabel then

	bubbleImageLabel = Instance.new("ImageLabel")

	bubbleImageLabel.Parent = bubbleChatConfiguration

end

bubbleImageLabel.Image = "rbxassetid://109157529833093"

bubbleImageLabel.ScaleType = Enum.ScaleType.Slice

bubbleImageLabel.SliceCenter = Rect.new(40, 40, 320, 120)

bubbleImageLabel.SliceScale = 0.5

```

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Advanced-Bubble.png)

The following tables outline the available [GuiObject](/docs/reference/engine/classes/GuiObject)  and [appearance modifier](/docs/ui/appearance-modifiers)  children along with their valid customization properties:

ImageLabel UIGradient UICorner UIPadding

| Property | | Description | | Default |
| [Image](/docs/reference/engine/classes/ImageLabel#Image) | | Asset ID of the bubble background image. | |  |
| [ImageColor3](/docs/reference/engine/classes/ImageLabel#ImageColor3) | | Color tint of the bubble background image in [Color3](/docs/reference/engine/datatypes/Color3) . | | [255, 255, 255] |
| [ImageRectOffset](/docs/reference/engine/classes/ImageLabel#ImageRectOffset) | | Offset of the image area to be displayed from the top-left in pixels. | | (0, 0) |
| [ImageRectSize](/docs/reference/engine/classes/ImageLabel#ImageRectSize) | | Size of the image area to be displayed in pixels. To display the entire image, set either dimension to 0 . | | (0, 0) |
| [ScaleType](/docs/reference/engine/classes/ImageLabel#ScaleType) | | The scale type for rendering the image when its size is different from the absolute size of the bubble. | | [Stretch](/docs/reference/engine/enums/ScaleType) |
| [SliceCenter](/docs/reference/engine/classes/ImageLabel#SliceCenter) | | Slice boundaries of the image if the image is a 9-sliced image. Only applicable when you set [ScaleType](/docs/reference/engine/classes/ImageLabel#ScaleType)  as [Slice](/docs/reference/engine/enums/ScaleType) .  | | (0, 0, 0, 0) |
| [SliceScale](/docs/reference/engine/classes/ImageLabel#SliceScale) | | Scale ratio of slice edges if the image is a 9-sliced image. Only applicable when you set [ScaleType](/docs/reference/engine/classes/ImageLabel#ScaleType)  as [Slice](/docs/reference/engine/enums/ScaleType) . | | 1 |
| [TileSize](/docs/reference/engine/classes/ImageLabel#TileSize) | | Tiling size of the image. Only applicable when you set [ScaleType](/docs/reference/engine/classes/ImageLabel#ScaleType)  as [Tile](/docs/reference/engine/enums/ScaleType) . | | (1, 0, 1, 0) |

## [Per-bubble customization](#per-bubble-customization)[](#per-bubble-customization)

You can individually style and modify chat bubble behaviors based on specific conditions in order to override your general settings. For example, you can use chat bubbles to differentiate NPCs and users, highlight critical health status, and apply special effects to messages with pre-defined keywords.

To set per-bubble customization, add a client-side [LocalScript](/docs/reference/engine/classes/LocalScript)  using [BubbleChatMessageProperties](/docs/reference/engine/classes/BubbleChatMessageProperties) , which overrides matching properties of [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration) , and the [TextChatService.OnBubbleAdded](/docs/reference/engine/classes/TextChatService#OnBubbleAdded)  callback to specify how to customize each bubble. The callback supplies you with the [TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  property as well as the adornee, so you can apply the customization based on attributes associated with users, the chat text content, user character properties, and any special conditions you want to define.

The following basic customization properties are available for per-bubble customization:

| Property | | Description | | Default |
| [BackgroundColor3](/docs/reference/engine/classes/BubbleChatConfiguration#BackgroundColor3) | | Background color of bubbles in [Color3](/docs/reference/engine/datatypes/Color3) . | | (250, 250, 250) |
| [BackgroundTransparency](/docs/reference/engine/classes/BubbleChatConfiguration#BackgroundTransparency) | | Background transparency of bubbles. | | 0.1 |
| [FontFace](/docs/reference/engine/classes/BubbleChatConfiguration#FontFace) | | [Font](/docs/reference/engine/datatypes/Font)  of the bubble text. | | [BuilderSansMedium](/docs/reference/engine/enums/Font#BuilderSansMedium) |
| [TextColor3](/docs/reference/engine/classes/BubbleChatConfiguration#TextColor3) | | Color of bubble text in [Color3](/docs/reference/engine/datatypes/Color3) . | | [57, 59, 61] |
| [TextSize](/docs/reference/engine/classes/BubbleChatConfiguration#TextSize) | | Size of bubble text. | | 16 |

The following example adds special appearance to VIP users' chat bubbles by checking if a chat message sender has the IsVIP  attribute:

VIP Bubbles

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

-- Event handler for when a new chat bubble is added to the game

TextChatService.OnBubbleAdded = function(message: TextChatMessage, adornee: Instance)

	-- Check if the chat message has a TextSource (sender) associated with it

	if message.TextSource then

		-- Create a new BubbleChatMessageProperties instance to customize the chat bubble

		local bubbleProperties = Instance.new("BubbleChatMessageProperties")

		-- Get the user who sent the chat message based on their UserId

		local player = Players:GetPlayerByUserId(message.TextSource.UserId)

		if player:GetAttribute("IsVIP") then

			-- If the player is a VIP, customize the chat bubble properties

			bubbleProperties.TextColor3 = Color3.fromHex("#F5CD30")

			bubbleProperties.BackgroundColor3 = Color3.fromRGB(25, 27, 29)

			bubbleProperties.FontFace = Font.fromEnum(Enum.Font.PermanentMarker)

		end

		return bubbleProperties

	end

end

```

All advanced customization options are available for per-bubble customization. Similar to advanced customization for general bubbles, add instances that you want to customize as children of [BubbleChatMessageProperties](/docs/reference/engine/classes/BubbleChatMessageProperties) . The following example adds a special gradient effect along with other properties to chat bubbles of users with low health status by checking the [Humanoid.Health](/docs/reference/engine/classes/Humanoid#Health)  property of chat message senders' characters:

Low Health Bubbles

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

-- Event handler for when a new chat bubble is added to the game

TextChatService.OnBubbleAdded = function(message: TextChatMessage, adornee: Instance)

	-- Check if the chat message has a TextSource (sender) associated with it

	if message.TextSource then

		-- Get the user who sent the chat message by using their UserId

		local player = Players:GetPlayerByUserId(message.TextSource.UserId)

		-- Find the humanoid in the user's character

		local humanoid = player.Character:FindFirstChildWhichIsA("Humanoid")

		if humanoid and humanoid.Health < 25 then

			-- Create a new BubbleChatMessageProperties instance to customize the chat bubble

			local bubbleProperties :BubbleChatMessageProperties = Instance.new("BubbleChatMessageProperties")

			-- Customize the chat bubble properties for low health condition

			bubbleProperties.BackgroundColor3 = Color3.fromRGB(245, 245, 245)

			bubbleProperties.TextColor3 = Color3.fromRGB(234, 51, 96)

			bubbleProperties.TextSize = 20

			bubbleProperties.FontFace = Font.fromEnum(Enum.Font.DenkOne)

			-- Add a UIGradient as a child to customize the gradient

			local uiGradient : UIGradient = Instance.new("UIGradient")

			uiGradient.Color = ColorSequence.new(Color3.fromRGB(110, 4, 0), Color3.fromRGB(0, 0, 0))

			uiGradient.Rotation = 90

			uiGradient.Parent = bubbleProperties

			return bubbleProperties

		end

	end

end

```

## [Manually display bubbles](#manually-display-bubbles)[](#manually-display-bubbles)

You might want to display a chat bubble when players haven't sent a message, such as with NPCs. Use the [TextChatService:DisplayBubble()](/docs/reference/engine/classes/TextChatService#DisplayBubble)  method to manually display a chat bubble.

Customization of these bubbles is the same as the customization of the bubbles that are automatically displayed when Players send messages through TextChannels using the [[TextChatService.OnBubbleAdded](/docs/reference/engine/classes/TextChatService#OnBubbleAdded)  callback](#per-bubble-customization) .

To generate speech or other text using an LLM, see the [TextGenerator](/docs/reference/engine/classes/TextGenerator)  class.

### [NPC bubbles](#npc-bubbles)[](#npc-bubbles)

Display chat bubbles for non-player characters (NPCs) by calling [TextChatService:DisplayBubble(character, message)](/docs/reference/engine/classes/TextChatService#DisplayBubble) , with the NPC character and the message as parameters. These bubbles are customizable using the [TextChatService.OnBubbleAdded](/docs/reference/engine/classes/TextChatService#OnBubbleAdded)  callback just like any other chat bubble.

[TextChatService:DisplayBubble()](/docs/reference/engine/classes/TextChatService#DisplayBubble)  only works on client-side scripts, so be sure to use a [Script](/docs/reference/engine/classes/Script)  with [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  set to [Enum.RunContext.Client](/docs/reference/engine/enums/RunContext#Client) , or a [LocalScript](/docs/reference/engine/classes/LocalScript)  in an [appropriate container](/docs/projects/data-model#client) , such as [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts) . If you attach a [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)  to an NPC, a script for displaying a chat bubble might look like this:

```

local TextChatService = game:GetService("TextChatService")

local Workspace = game:GetService("Workspace")

local prompt = Workspace.SomeNPC.ProximityPrompt

local head = prompt.Parent:WaitForChild("Head")

prompt.Triggered:Connect(function()

	TextChatService:DisplayBubble(head, "Hello world!")

end)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
