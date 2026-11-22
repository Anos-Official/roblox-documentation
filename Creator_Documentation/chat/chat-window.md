<!-- Source: https://create.roblox.com/docs/en-us/chat/chat-window -->

Customize the chat window | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/chat-window.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/en-us/chat/in-experience-text-chat)

# Customize the chat window

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/chat-window.md)

The [in-game text chat](/docs/en-us/chat/in-experience-text-chat)  system, powered by [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) , allows players to easily communicate and socialize with each other in live games. In addition to supporting the default text chat, you can [customize](#chat-window-configuration)  the front‑end user interface.

## [Chat window configuration](#chat-window-configuration)[](#chat-window-configuration)

The overall chat window consists of:

-

Chat window

-

Input bar

-

Channel tabs (optional)

 ![Core components of the text chat window.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Window-Components.jpg)

The channel tabs are disabled by default and each component can be toggled on and off in Studio or through scripting:

Studio Scripting

In the [Explorer](/docs/en-us/studio/explorer)  window, expand the [TextChatService](/docs/en-us/reference/engine/classes/TextChatService)  branch and select [ChatWindowConfiguration](/docs/en-us/reference/engine/classes/ChatWindowConfiguration) , [ChatInputBarConfiguration](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration) , or [ChannelTabsConfiguration](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration) . Then enable or disable the component in the [Properties](/docs/en-us/studio/properties)  window.

![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-Configuration-Objects.png)

When [ChannelTabsConfiguration](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration)  is enabled, each default [TextChannel](/docs/en-us/reference/engine/classes/TextChannel)  appears in a tab as outlined in the following table. In addition, each custom [TextChannel](/docs/en-us/reference/engine/classes/TextChannel)  creates a tab corresponding to the channel's [Name](/docs/en-us/reference/engine/classes/Instance#Name)  property.

| Default channel | | Tab name |
| --- | --- |
| RBXGeneral | | General |
| RBXSystem | | General  (combined into a single tab with RBXGeneral ) |
| RBXTeam | | Team |
| RBXWhisper | | User name of the other player |

### [Window appearance](#window-appearance)[](#window-appearance)

Appearance of the overall chat window is customizable through [ChatWindowConfiguration](/docs/en-us/reference/engine/classes/ChatWindowConfiguration) .

 ![ChatWindowConfiguration instance in Explorer hierarchy.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-ChatWindowConfiguration.png)

| Property | | Description | | Default |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#BackgroundColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  background color of the chat window. | | [25, 27, 29] |
| [BackgroundTransparency](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#BackgroundTransparency) | | Transparency of the chat window's background. | | 0.3 |
| [Enabled](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#Enabled) | | Whether to show the default chat window. Set to false  to hide. | | true |
| [FontFace](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#FontFace) | | [Font](/docs/en-us/reference/engine/datatypes/Font)  of chat window text. | | [BuilderSansMedium](/docs/en-us/reference/engine/enums/Font#BuilderSansMedium) |
| [TextColor3](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#TextColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  of chat window text. | | [255, 255, 255] |
| [TextSize](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#TextSize) | | Size of chat window text. | | 14 |
| [TextStrokeColor3](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#TextStrokeColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  of the stroke for chat window text. | | [0, 0, 0] |
| [TextStrokeTransparency](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#TextStrokeTransparency) | | Transparency of the stroke for chat window text. | | 0.5 |
| [HorizontalAlignment](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#HorizontalAlignment) | | Horizontal alignment of the chat window. | | [Left](/docs/en-us/reference/engine/enums/HorizontalAlignment#Left) |
| [VerticalAlignment](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#VerticalAlignment) | | Vertical alignment of the chat window. | | [Top](/docs/en-us/reference/engine/enums/VerticalAlignment#Top) |
| [HeightScale](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#HeightScale) | | Height scale of the chat window relative to the screen size. | | 1 |
| [WidthScale](/docs/en-us/reference/engine/classes/ChatWindowConfiguration#WidthScale) | | Width scale of the chat window relative to the screen size. | | 1 |

### [Input bar appearance](#input-bar-appearance)[](#input-bar-appearance)

Appearance of the chat input bar is customizable through [ChatInputBarConfiguration](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration) .

 ![ChatInputBarConfiguration instance in Explorer hierarchy.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-ChatInputBarConfiguration.png)

| Property | | Description | | Default |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#BackgroundColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  background color of the chat input bar. | | [25, 27, 29] |
| [BackgroundTransparency](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#BackgroundTransparency) | | Transparency of the chat input bar's background. | | 0.2 |
| [FontFace](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#FontFace) | | [Font](/docs/en-us/reference/engine/datatypes/Font)  of chat input text. | | [BuilderSansMedium](/docs/en-us/reference/engine/enums/Font#BuilderSansMedium) |
| [PlaceholderColor3](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#PlaceholderColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  of placeholder chat input text. | | [178, 178, 178] |
| [TextColor3](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#TextColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  of player-entered chat input text. | | [255, 255, 255] |
| [TextSize](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#TextSize) | | Size of chat input text. | | 14 |
| [TextStrokeColor3](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#TextStrokeColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  stroke color of chat input text. | | [0, 0, 0] |
| [TextStrokeTransparency](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#TextStrokeTransparency) | | Transparency of the stroke for chat input text. | | 0.5 |
| [AutocompleteEnabled](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#AutocompleteEnabled) | | Whether the text chat system shows autocomplete options for emojis and [commands](/docs/en-us/chat/in-experience-text-chat) . Emojis are autocompleted by typing :  followed by non-whitespace characters, while commands are autocompleted by typing / . | | true |
| [KeyboardKeyCode](/docs/en-us/reference/engine/classes/ChatInputBarConfiguration#KeyboardKeyCode) | | Additional key players can press to trigger focusing on the default chat input bar. | | [Slash](/docs/en-us/reference/engine/enums/KeyCode#Slash) |

### [Channel tabs appearance](#channel-tabs-appearance)[](#channel-tabs-appearance)

Appearance of the channel tabs  is customizable through [ChannelTabsConfiguration](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration) .

 ![ChannelTabsConfiguration instance in Explorer hierarchy.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-ChannelTabsConfiguration.png)

| Property | | Description | | Default |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#BackgroundColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  background color of the channel tabs. | | [25, 27, 29] |
| [BackgroundTransparency](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#BackgroundTransparency) | | Transparency of the channel tabs' background. | | 0 |
| [HoverBackgroundColor3](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#HoverBackgroundColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  background color of tabs when hovering over them. | | [125, 125, 125] |
| [FontFace](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#FontFace) | | [Font](/docs/en-us/reference/engine/datatypes/Font)  for the text in channel tabs. | | [BuilderSansBold](/docs/en-us/reference/engine/enums/Font#BuilderSansBold) |
| [TextColor3](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#TextColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  of text in an unselected tab. | | [175, 175, 175] |
| [SelectedTabTextColor3](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#SelectedTabTextColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  of text in a selected tab. | | [255, 255, 255] |
| [TextSize](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#TextSize) | | Size of the text in channel tabs. | | 18 |
| [TextStrokeColor3](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#TextStrokeColor3) | | [Color3](/docs/en-us/reference/engine/datatypes/Color3)  stroke color of the text in channel tabs. | | [0, 0, 0] |
| [TextStrokeTransparency](/docs/en-us/reference/engine/classes/ChannelTabsConfiguration#TextStrokeTransparency) | | Transparency of the stroke for text in channel tabs. | | 1 |

## [Customize messages](#customize-messages)[](#customize-messages)

You can customize the appearance of chat message bodies and prefixes using [ChatWindowMessageProperties](/docs/en-us/reference/engine/classes/ChatWindowMessageProperties)  and [TextChatService.OnChatWindowAdded](/docs/en-us/reference/engine/classes/TextChatService#OnChatWindowAdded)  callbacks without overriding the existing UI. The customization options let you modify the appearance of chat messages to match your game's theme, and you can also sort or highlight messages from different user groups by coloring prefixes or adding [chat tags](/docs/en-us/chat/examples/group-chat-tags) .

[ChatWindowMessageProperties](/docs/en-us/reference/engine/classes/ChatWindowMessageProperties)  and [OnChatWindowAdded](/docs/en-us/reference/engine/classes/TextChatService#OnChatWindowAdded)  only affect the appearance of messages in the chat window. To customize chat bubbles, see [Bubble Chat](/docs/en-us/chat/bubble-chat) .

### [Color user names](#color-user-names)[](#color-user-names)

When a user sends a chat message, their [DisplayName](/docs/en-us/reference/engine/classes/Player#DisplayName)  displays as the prefix portion of the message. By default, each user's name is colored according to their [Player.TeamColor](/docs/en-us/reference/engine/classes/Player#TeamColor)  but you can change the colors of chat names using [ChatWindowMessageProperties](/docs/en-us/reference/engine/classes/ChatWindowMessageProperties)  and [OnChatWindowAdded](/docs/en-us/reference/engine/classes/TextChatService#OnChatWindowAdded) . The following [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  in [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts)  assigns a predetermined color to each user, picking randomly from a table of RGB colors.

 ![Colored user name in the chat window.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-User-Name-Colored.png)

LocalScript - Random User Name Colors

```

local TextChatService = game:GetService("TextChatService")

local chatWindowConfiguration = TextChatService.ChatWindowConfiguration

local nameColors = {

	Color3.fromRGB(255, 0, 0),

	Color3.fromRGB(0, 255, 0),

	Color3.fromRGB(0, 0, 255),

	Color3.fromRGB(255, 255, 0),

}

TextChatService.OnChatWindowAdded = function(message: TextChatMessage)

	local properties = chatWindowConfiguration:DeriveNewMessageProperties()

	local textSource = message.TextSource

	if textSource then

		local index: number = (textSource.UserId % #nameColors) + 1

		local randomColor: Color3 = nameColors[index]

    	properties.PrefixTextProperties = chatWindowConfiguration:DeriveNewMessageProperties()

		properties.PrefixTextProperties.TextColor3 = randomColor

	end

	return properties

end

```

You can also apply color and transparency gradients to color message prefixes using [UIGradient](/docs/en-us/reference/engine/classes/UIGradient) .

 ![Gradient user name in the chat window.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-User-Name-Gradient.png)

Gradient User Name Colors

```

local TextChatService = game:GetService("TextChatService")

local chatWindowConfiguration = TextChatService.ChatWindowConfiguration

local gradient = Instance.new("UIGradient")

gradient.Color = ColorSequence.new{

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),

	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 255, 0)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 0, 255))

}

TextChatService.OnChatWindowAdded = function(message: TextChatMessage)

	local properties = chatWindowConfiguration:DeriveNewMessageProperties()

	local textSource = message.TextSource

	if textSource then

    	properties.PrefixTextProperties = chatWindowConfiguration:DeriveNewMessageProperties()

		gradient:Clone().Parent = properties.PrefixTextProperties

	end

	return properties

end

```

### [Rich text customization](#rich-text-customization)[](#rich-text-customization)

Rich text [font color tags](/docs/en-us/ui/rich-text#supported-tags)  can be used to format chat messages, helpful if you want to apply formatting to very specific parts of the message. Note that rich text does not support gradients, but the following code sample shows how you can move the user name (stored in [TextChatMessage.PrefixText](/docs/en-us/reference/engine/classes/TextChatMessage#PrefixText) ) into the message body and then apply rich text tagging to only the name portion.

 ![Rich text customization of user name in the chat window.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Rich-Text.png)

Rich Text Customization

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local chatWindowConfiguration = TextChatService.ChatWindowConfiguration

local gradient = Instance.new("UIGradient")

gradient.Color = ColorSequence.new{

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),

	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 255, 0)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 0, 255))

}

TextChatService.OnChatWindowAdded = function(message: TextChatMessage)

	local properties = chatWindowConfiguration:DeriveNewMessageProperties()

	if message.TextSource then

		properties.PrefixText = "[VIP]"

		properties.Text = string.format("<font color='#00ffff'>%s</font>", message.PrefixText) .. " " .. message.Text

		properties.PrefixTextProperties = chatWindowConfiguration:DeriveNewMessageProperties()

		gradient:Clone().Parent = properties.PrefixTextProperties

	end

	return properties

end

```

## [Messages from non‑player sources](#messages-from-nonplayer-sources)[](#messages-from-nonplayer-sources)

When [TextChatService.CreateDefaultTextChannels](/docs/en-us/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  is true , one of the default text channels is the RBXSystem  channel. The default chat scripts automatically display system messages in this channel. You can customize the appearance of these messages using the [TextChannel.OnIncomingMessage](/docs/en-us/reference/engine/classes/TextChannel#OnIncomingMessage)  callback.

You might want to customize or alter the system messages that are automatically emitted by the chat system. Since the default system messages are localized for users, you should reference them by [TextChatMessage.Metadata](/docs/en-us/reference/engine/classes/TextChatMessage#Metadata)  in your [text chat callbacks](/docs/en-us/chat/in-experience-text-chat#text-chat-hooks-and-callbacks)  if you wish to customize their appearance. For example, you could use [Metadata](/docs/en-us/reference/engine/classes/TextChatMessage#Metadata)  to identify system messages, error messages, or messages from specific systems in your game.

### [System](#system)[](#system)

To deliver a system message to the local player, such as "speech" from a public address system, call [DisplaySystemMessage()](/docs/en-us/reference/engine/classes/TextChannel#DisplaySystemMessage)  from the default RBXGeneral  channel with a prefix before the player's display name.

Client Script

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local player = Players.LocalPlayer

local generalChannel: TextChannel = TextChatService:WaitForChild("TextChannels").RBXGeneral

local PREFIX = "[Guide] Welcome "

-- Send "system message" to player with their display name appended

generalChannel:DisplaySystemMessage(PREFIX .. player.DisplayName)

```

 ![Image showing a basic system message in the chat window.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-System.jpg)

### [NPC/object](#npcobject)[](#npcobject)

You can also stylize non-player dialogue and add [chat bubbles](/docs/en-us/chat/bubble-chat)  to make it appear like messages are coming from an NPC or object within the 3D world.

Client Script

```

local TextChatService = game:GetService("TextChatService")

local Workspace = game:GetService("Workspace")

local generalChannel: TextChannel = TextChatService:WaitForChild("TextChannels").RBXGeneral

TextChatService.OnIncomingMessage = function(textChatMessage: TextChatMessage)

	local properties = Instance.new("TextChatMessageProperties")

	-- Check for system messages that contain metadata

	if not textChatMessage.TextSource and textChatMessage.Metadata ~= "" then

		-- Add prefix to make message look like it was sent by a player

		properties.PrefixText = string.format("<font color='#%s'>%s: </font>", "#50C999", textChatMessage.Metadata)

		-- Add bubble chat

		TextChatService:DisplayBubble(Workspace.Statue, textChatMessage.Text)

	end

	return properties

end

local message = "Welcome! I will be your guide."

local speakerName = "Ancient Knight"

generalChannel:DisplaySystemMessage(message, speakerName)

```

 ![Image showing a knight statue NPC broadcasting a chat message to the chat window, along with a chat bubble above its head.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-NPC.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
