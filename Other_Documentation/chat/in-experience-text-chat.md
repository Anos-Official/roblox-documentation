<!-- Source: https://create.roblox.com/docs/chat/in-experience-text-chat -->

Text chat overview | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/in-experience-text-chat.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/chat/in-experience-text-chat)

# Text chat overview

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/in-experience-text-chat.md)

Roblox offers text-based messaging between players in live sessions through [TextChatService](/docs/reference/engine/classes/TextChatService) , a singleton class responsible for managing the overall chat system, including chat message filtering, moderation, and user permissions. This service has its standard functionality and also provides a set of methods and events for extending and customizing chat, such as delivering messages based on [customized requirements](#conditionally-deliver-messages) , adding special permissions or moderation to specific players, and creating [custom commands](/docs/chat/examples/custom-text-chat-commands)  to execute specific actions.

When [platform-integrated chat](/docs/chat/platform-integrated-chat)  is enabled, custom chat must use Roblox's native systems, and message content isn't accessible in code.

## [UI configuration](#ui-configuration)[](#ui-configuration)

[TextChatService](/docs/reference/engine/classes/TextChatService)  provides a default UI that can be customized to fit your game's needs. Disable any of these configurations to hide its associated UI element. If desired, you can also replace these UI elements with custom interfaces:

-

[ChatWindowConfiguration](/docs/reference/engine/classes/ChatWindowConfiguration)

-

[ChatInputBarConfiguration](/docs/reference/engine/classes/ChatInputBarConfiguration)

-

[ChannelTabsConfiguration](/docs/reference/engine/classes/ChannelTabsConfiguration)

-

[BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration)

For more information, see [Chat window](/docs/chat/chat-window)  and [Bubble chat](/docs/chat/bubble-chat) .

## [Channels, messages, and commands](#channels-messages-and-commands)[](#channels-messages-and-commands)

-

[TextChannel](/docs/reference/engine/classes/TextChannel)  — Text channels pass user-sent messages from the client to the server, which then displays them to other users based on permissions. Text channels must be parented to [TextChatService](/docs/reference/engine/classes/TextChatService)  in order to function.

If [TextChatService.CreateDefaultTextChannels](/docs/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  is set to true , the service automatically creates two text channels, RBXGeneral  and RBXSystem . You can manually create additional [TextChannel](/docs/reference/engine/classes/TextChannel)  instances and parent them to [TextChatService](/docs/reference/engine/classes/TextChatService) , as well.

Having multiple [TextChannels](/docs/reference/engine/classes/TextChannel)  with the same name can cause unintended behavior with the default [chat window](/docs/chat/chat-window) .

-

[TextSource](/docs/reference/engine/classes/TextSource)  — A user in a [TextChannel](/docs/reference/engine/classes/TextChannel) . Text sources are directly parented to the [TextChannel](/docs/reference/engine/classes/TextChannel)  when [AddUserAsync()](/docs/reference/engine/classes/TextChannel#AddUserAsync)  is called. Text sources contains detailed permissions of a user in the channel, such as their ability to send messages. If a single user is in multiple text channels, they are associated with multiple text sources.

-

[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  — A message in a text channel. Chat messages contain basic information such as the sender of the message, the original message, the filtered message, and the creation timestamp.

-

[TextChatCommand](/docs/reference/engine/classes/TextChatCommand)  — Lets users invoke specific actions or behaviors by sending messages that match the [PrimaryAlias](/docs/reference/engine/classes/TextChatCommand#PrimaryAlias)  or [SecondaryAlias](/docs/reference/engine/classes/TextChatCommand#SecondaryAlias)  properties. Chat commands must be parented to [TextChatService](/docs/reference/engine/classes/TextChatService)  in order to function.

If [TextChatService.CreateDefaultCommands](/docs/reference/engine/classes/TextChatService#CreateDefaultCommands)  is set to true , default chat commands will be created automatically. You can manually create additional [TextChatCommand](/docs/reference/engine/classes/TextChatCommand)  instances and parent them to [TextChatService](/docs/reference/engine/classes/TextChatService) , as well.

## [Chat flowchart](#chat-flowchart)[](#chat-flowchart)

Text chat uses the [client‑server](/docs/projects/client-server)  model, with a sending client , the server , and receiving clients .

 ![A flowchart for in-game text chat.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Workflow.png)

1.

A player sends a message from their local device, triggering the [TextChannel:SendAsync()](/docs/reference/engine/classes/TextChannel#SendAsync)  method. This method processes the message and determines whether it's a chat command or a regular chat message.

-

If the message is a chat command, it fires the [TextChatCommand.Triggered](/docs/reference/engine/classes/TextChatCommand#Triggered)  event to perform the defined action. No further steps are required.

-

If the message is a regular chat message, it fires the [TextChatService.SendingMessage](/docs/reference/engine/classes/TextChatService#SendingMessage)  event to display the message to the sender on the sending client. At the same time, [TextChannel:SendAsync()](/docs/reference/engine/classes/TextChannel#SendAsync)  passes the message to the server.

2.

The server fires [TextChannel.ShouldDeliverCallback](/docs/reference/engine/classes/TextChannel#ShouldDeliverCallback)  to determine whether to deliver the message to other players based on permissions and Roblox community filtering requirements.

3.

If [TextChannel.ShouldDeliverCallback](/docs/reference/engine/classes/TextChannel#ShouldDeliverCallback)  determines that message is eligible to deliver to other players, the server applies any filters and fires [TextChannel.OnIncomingMessage](/docs/reference/engine/classes/TextChannel#OnIncomingMessage)  twice:

1.

The first time is on the sending client and signals that the server is processing the message through the [TextChatService.MessageReceived](/docs/reference/engine/classes/TextChatService#MessageReceived)  event. This event replaces the local message on the sending client with the processed message from the server. The message is identical if the original didn't require filtering.

2.

The second time is on the receiving clients, which triggers the [TextChatService.MessageReceived](/docs/reference/engine/classes/TextChatService#MessageReceived)  event to display the message to other players.

## [Text chat hooks and callbacks](#text-chat-hooks-and-callbacks)[](#text-chat-hooks-and-callbacks)

The [TextChatService](/docs/reference/engine/classes/TextChatService)  API encourages a clear separation on the appearance and delivery of chat messages. Multiple instances of the text chat system provide hooks and callbacks to format in centralized, clear locations.

All callbacks are expected to be non-yielding functions. Yielding or waiting for a response in a callback blocks the chat system and can cause unexpected behavior.

 ![A flowchart of the TextChatService callbacks order](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-Callbacks.png)

| Callback | | Return Value |
| --- | --- |
| [TextChannel.ShouldDeliverCallback](/docs/reference/engine/classes/TextChannel#ShouldDeliverCallback) | | boolean |
| [TextChatService.OnIncomingMessage](/docs/reference/engine/classes/TextChatService#OnIncomingMessage) | | [TextChatMessageProperties](/docs/reference/engine/classes/TextChatMessageProperties) |
| [TextChannel.OnIncomingMessage](/docs/reference/engine/classes/TextChannel#OnIncomingMessage) | | [TextChatMessageProperties](/docs/reference/engine/classes/TextChatMessageProperties) |
| [TextChatService.OnBubbleAdded](/docs/reference/engine/classes/TextChatService#OnBubbleAdded) | | [BubbleChatMessageProperties](/docs/reference/engine/classes/BubbleChatMessageProperties) |
| [TextChatService.OnChatWindowAdded](/docs/reference/engine/classes/TextChatService#OnChatWindowAdded) | | [ChatWindowMessageProperties](/docs/reference/engine/classes/ChatWindowMessageProperties) |

### [Conditionally deliver messages](#conditionally-deliver-messages)[](#conditionally-deliver-messages)

The [TextChannel.ShouldDeliverCallback](/docs/reference/engine/classes/TextChannel#ShouldDeliverCallback)  callback should be defined on the server only. The callback is fired for each [TextSource](/docs/reference/engine/classes/TextSource)  child of the text channel when a message is sent to determine whether the message should be delivered. This callback can be used to implement custom message delivery logic that may depend on additional gameplay context, such as:

-

[Proximity-based chat](/docs/chat/examples/proximity-chat)  where users can only send messages to those close to them.

-

Preventing users with certain attributes from sending messages to others.

### [Customize message display](#customize-message-display)[](#customize-message-display)

The default [TextChatService](/docs/reference/engine/classes/TextChatService)  UI relies on [rich text](/docs/ui/rich-text)  to format and customize how messages are displayed. You can use the following callbacks to format messages before they are displayed to users, for example to add colors or [chat tags](/docs/chat/examples/group-chat-tags)  to user names or format message content.

The following callbacks are called on every [TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  that is about to be displayed, which lets you customize chat window appearance based on the [TextChannel](/docs/reference/engine/classes/TextChannel) , [TextSource](/docs/reference/engine/classes/TextSource) , or [TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  content. When a client sends a message, these callbacks are called once when the message is sent to the server and the [TextChatMessage.Status](/docs/reference/engine/classes/TextChatMessage#Status)  value will be [Enum.TextChatMessageStatus.Sending](/docs/reference/engine/enums/TextChatMessageStatus#Sending) . Once the message is received by the server and is being delivered to other users, the sender client receives the message again with an updated [Enum.TextChatMessageStatus](/docs/reference/engine/enums/TextChatMessageStatus)  value.

-

[TextChatService.OnIncomingMessage](/docs/reference/engine/classes/TextChatService#OnIncomingMessage)  — This callback should be defined on the client only. The callback is fired when a message is received, either from the server or if the local client has just sent a message. The callback is called on every [TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  received from all [TextChannel](/docs/reference/engine/classes/TextChannel)  instances and is the first to process the message before it is displayed to the user.

-

[TextChannel.OnIncomingMessage](/docs/reference/engine/classes/TextChannel#OnIncomingMessage)  — This callback should be defined on the client only. The callback is fired when a message is received from the server. The callback is called on every [TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  received from the [TextChannel](/docs/reference/engine/classes/TextChannel) . Default [TextChannel](/docs/reference/engine/classes/TextChannel)  instances created from [TextChatService.CreateDefaultTextChannels](/docs/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  have this callback defined and can be overwritten.

-

[TextChatService.OnBubbleAdded](/docs/reference/engine/classes/TextChatService#OnBubbleAdded)  — This callback should be defined on the client only. Use it to customize the appearance of chat bubbles independent of the appearance of the message in the chat window UI.

-

[TextChatService.OnChatWindowAdded](/docs/reference/engine/classes/TextChatService#OnChatWindowAdded)  — This callback should be defined on the client only. Use it to customize the appearance of chat messages in the chat window UI independent of the appearance of the message in chat bubbles.

## [Migrate from legacy chat](#migrate-from-legacy-chat)[](#migrate-from-legacy-chat)

This section assists you in migrating from the legacy chat system by providing alternative methods for implementing common chat functionalities and behaviors using [TextChatService](/docs/reference/engine/classes/TextChatService) .

1.

In the [Explorer](/docs/studio/explorer)  window, select [TextChatService](/docs/reference/engine/classes/TextChatService) .

2.

In the [Properties](/docs/studio/properties)  window, find the [ChatVersion](/docs/reference/engine/classes/TextChatService#ChatVersion)  dropdown and select [TextChatService](/docs/reference/engine/enums/ChatVersion) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/TextChatService-ChatVersion-TextChatService.png)

### [Basic functionalities](#basic-functionalities)[](#basic-functionalities)

Though both systems share the same basic chat functionalities, [TextChatService](/docs/reference/engine/classes/TextChatService)  implementations are in general more sustainable and easier to iterate on.

| Functionality | | Legacy chat | | TextChatService | | Differences |
| Send a chat message | | [Players:Chat()](/docs/reference/engine/classes/Players#Chat) | | [TextChannel:SendAsync()](/docs/reference/engine/classes/TextChannel#SendAsync) | | The [SendAsync()](/docs/reference/engine/classes/TextChannel#SendAsync)  method supports more advanced chat features, such as rich text formatting and message priority. It also includes built-in filtering to help prevent inappropriate messages from being sent. |
| Implement messaging callbacks | | [Chat:InvokeChatCallback()](/docs/reference/engine/classes/Chat#InvokeChatCallback)
[Chat:RegisterChatCallback()](/docs/reference/engine/classes/Chat#RegisterChatCallback) | | [TextChatService.SendingMessage](/docs/reference/engine/classes/TextChatService#SendingMessage)
[TextChatService.OnIncomingMessage](/docs/reference/engine/classes/TextChatService#OnIncomingMessage) | | The legacy chat system binds a function to chat system events for delivering messages. The two methods of TextChatService  offer better flexibility and customization. |
| Add custom chat commands | | ChatService/ChatCommand  module | | [TextChatCommand](/docs/reference/engine/classes/TextChatCommand) | | TextChatService  has a dedicated class for text commands rather than using a legacy chat module. |
| Display a system message | | [StarterGui:SetCore()](/docs/reference/engine/classes/StarterGui#SetCore)  using ChatMakeSystemMessage | | [TextChannel:DisplaySystemMessage()](/docs/reference/engine/classes/TextChannel#DisplaySystemMessage) | | The [TextChannel.OnIncomingMessage](/docs/reference/engine/classes/TextChannel#OnIncomingMessage)  callback can return a [TextChatMessageProperties](/docs/reference/engine/classes/TextChatMessageProperties)  instance to customize the message appearance. |
| Disable chat | | ChatWindow/ChatSettings  module for hiding the chat window | | [ChatWindowConfiguration.Enabled](/docs/reference/engine/classes/ChatWindowConfiguration#Enabled) | |  |

### [Message filtering](#message-filtering)[](#message-filtering)

[TextChatService](/docs/reference/engine/classes/TextChatService)  automatically filters chat messages based on each player's account information, so you don't need to manually implement text filtering for all kinds of chat messages.

| Functionality | | Legacy chat | | TextChatService |
| Filter chat message for individual player | | [Chat:FilterStringAsync()](/docs/reference/engine/classes/Chat#FilterStringAsync) | | Automatic |
| Filter broadcasting messages | | [Chat:FilterStringForBroadcast()](/docs/reference/engine/classes/Chat#FilterStringForBroadcast) | | Automatic |

### [Window and bubble chat](#window-and-bubble-chat)[](#window-and-bubble-chat)

Both the [chat window](/docs/chat/chat-window)  and [bubble chat](/docs/chat/bubble-chat)  behavior and customization options of [TextChatService](/docs/reference/engine/classes/TextChatService)  are identical to those of the legacy chat system. As the legacy chat system only allows customization using chat modules or the [Players](/docs/reference/engine/classes/Players)  container, the service provides dedicated classes ([ChatWindowConfiguration](/docs/reference/engine/classes/ChatWindowConfiguration)  and [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration) ) to manage all chat window and bubble chat properties. Additionally, you can easily adjust and preview your bubble chat appearance and behavior properties using Studio settings instead of having to script them all.

| Functionality | | Legacy chat | | TextChatService |
| Enable Chat Window | | [Chat.LoadDefaultChat](/docs/reference/engine/classes/Chat#LoadDefaultChat)
[Players.ClassicChat](/docs/reference/engine/classes/Players#ClassicChat) | | [ChatWindowConfiguration.Enabled](/docs/reference/engine/classes/ChatWindowConfiguration#Enabled) |
| Enable Bubble Chat | | [Chat.BubbleChatEnabled](/docs/reference/engine/classes/Chat#BubbleChatEnabled)
[Players.BubbleChat](/docs/reference/engine/classes/Players#BubbleChat) | | [BubbleChatConfiguration.Enabled](/docs/reference/engine/classes/BubbleChatConfiguration#Enabled) |
| Set Chat Window Properties | | [Players:SetChatStyle()](/docs/reference/engine/classes/Players#SetChatStyle) | | [ChatWindowConfiguration](/docs/reference/engine/classes/ChatWindowConfiguration) |
| Set Bubble Chat Properties | | [Chat:SetBubbleChatSettings()](/docs/reference/engine/classes/Chat#SetBubbleChatSettings)
[Chat.BubbleChatSettingsChanged()](/docs/reference/engine/classes/Chat#BubbleChatSettingsChanged)
[Players.BubbleChat](/docs/reference/engine/classes/Players#BubbleChat)
[Players:SetChatStyle()](/docs/reference/engine/classes/Players#SetChatStyle) | | [BubbleChatConfiguration](/docs/reference/engine/classes/BubbleChatConfiguration) |
| Enable NPC Bubbles | | [Chat:Chat()](/docs/reference/engine/classes/Chat#Chat) | | [TextChatService:DisplayBubble()](/docs/reference/engine/classes/TextChatService#DisplayBubble) |

### [Migrate speaker "extra data"](#migrate-speaker-extra-data)[](#migrate-speaker-extra-data)

The legacy Lua chat system allowed developers to use SetExtraData  on the Speaker  class. This data was used to format the name color, chat color, or to apply name tags for a given speaker.

Legacy Chat System SetExtraData

```

-- An example of setting extra data on a speaker in the legacy chat system

ChatService.SpeakerAdded:Connect(function(playerName)

	local speaker = ChatService:GetSpeaker(playerName)

	speaker:SetExtraData("NameColor", Color3.fromRGB(255, 255, 55))

	speaker:SetExtraData("ChatColor", Color3.fromRGB(212, 175, 55))

	speaker:SetExtraData("Tags", {{TagText = "YourTagName", TagColor = Color3.fromRGB(0, 255, 0)}, {TagText = "OtherTagName", TagColor = Color3.fromRGB(255, 0, 0)}})

end)

```

[TextChatService](/docs/reference/engine/classes/TextChatService)  does not have a direct equivalent to SetExtraData . Instead, use [callbacks](#text-chat-hooks-and-callbacks)  such as [OnWindowAdded](/docs/reference/engine/classes/TextChatService#OnWindowAdded)  to customize the appearance of messages using rich text based on the [TextSource](/docs/reference/engine/classes/TextSource)  of the message.

The following is an example of emulating legacy Lua chat's "extra data" by accessing attributes on [Player](/docs/reference/engine/classes/Player)  objects:

TextChatService SetAttributes

```

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

	player:SetAttribute("NameColor", Color3.fromRGB(255, 255, 55))

	player:SetAttribute("ChatColor", Color3.fromRGB(212, 175, 55))

	player:SetAttribute("isYourTag", true)

	player:SetAttribute("isOtherTag", true)

end)

```

Then you can use the [OnChatWindowAdded](/docs/reference/engine/classes/TextChatService#OnChatWindowAdded)  callback to customize the appearance of the chat window based on the attributes set on the player:

TextChatService OnChatWindowAdded

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

TextChatService.OnChatWindowAdded = function(textChatMessage)

	local textSource = textChatMessage.TextSource

	if textSource then

		local player = Players:GetPlayerByUserId(textSource.UserId)

		if player then

			local overrideProperties = TextChatService.ChatWindowConfiguration:DeriveNewMessageProperties()

			overrideProperties.PrefixText = textChatMessage.PrefixText

			overrideProperties.Text = textChatMessage.Text

			local nameColor = player:GetAttribute("NameColor")

			if nameColor and typeof(nameColor) == "Color3" then

				overrideProperties.PrefixTextProperties.TextColor3 = nameColor

			end

			local chatColor = player:GetAttribute("ChatColor")

			if chatColor and typeof(chatColor) == "Color3" then

				overrideProperties.TextColor3 = chatColor

			end

			local isYourTag = player:GetAttribute("isYourTag")

			if isYourTag == true then

				overrideProperties.PrefixText = `<font color='rgb(0, 255, 0)'>[YourTag]</font> {overrideProperties.PrefixText}`

			end

			local isOtherTag = player:GetAttribute("isOtherTag")

			if isOtherTag == true then

				overrideProperties.PrefixText = `<font color='rgb(255, 0, 0)'>[OtherTag]</font> {overrideProperties.PrefixText}`

			end

			return overrideProperties

		end

	end

	return nil

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
