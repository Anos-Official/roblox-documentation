<!-- Source: https://create.roblox.com/docs/chat/platform-integrated-chat -->

Platform-integrated chat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/platform-integrated-chat.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/chat/in-experience-text-chat)

# Platform-integrated chat

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/platform-integrated-chat.md)

Starting in May 2027, platform-integrated chat will be required for all games. The unsupported APIs will be deprecated, and custom chat will have to use the new [TextChatService](/docs/reference/engine/classes/TextChatService)  features.

When you enable platform-integrated chat, custom chat features must move to Roblox's native systems ([TextChatCommands](/docs/reference/engine/classes/TextChatCommand) , [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow) , [Quick Words](/docs/chat/quick-words) ). Message content is also no longer accessible in code.

Platform-integrated chat  gives every player consistent access to safety tools such as reporting and muting, and lets chat features like [Quick Words](/docs/chat/quick-words)  roll out reliably across all games. It also replaces the current prefix system, so roles associated with users render consistently and are safe for all ages.

Nothing in your game changes until you [enable platform-integrated chat](#enable-platform-integrated-chat)  in Studio. After you enable it:

-

Roblox delivers and renders chat in the default window or a [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  you place in your UI. Custom chat UIs can no longer render messages themselves.

-

Player message text isn't accessible to your code. You can't read, log, or export it. APIs that previously returned message text now return an empty string ("" ) instead of nil , so your scripts keep running but receive no content.

Commands triggered from chat must use [TextChatCommand](/docs/reference/engine/classes/TextChatCommand) .

## [Unsupported APIs](#unsupported-apis)[](#unsupported-apis)

When platform-integrated chat is enabled, the following APIs return ""  (empty string, not nil ) and log a warning:

| Feature | | Unsupported APIs | | What to use instead |
| --- | --- |
| Chat messages and display | | [TextChatMessage.Text](/docs/reference/engine/classes/TextChatMessage#Text) , [TextChatMessage.Translation](/docs/reference/engine/classes/TextChatMessage#Translation) | | Migrate your custom chat GUI to [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow) . Set [Target](/docs/reference/engine/classes/TextChannelWindow#Target)  to a [TextChannel](/docs/reference/engine/classes/TextChannel) . Users can send and receive messages automatically. |
| Chat prefixes | | [TextChatMessage.PrefixText](/docs/reference/engine/classes/TextChatMessage#PrefixText) | | Not supported. If your game requires prefixes, don't enable platform-integrated chat yet. |
| Presets / chat wheels | | [TextChannel:SendAsync()](/docs/reference/engine/classes/TextChannel#SendAsync) | | Use [Quick Words](/docs/chat/quick-words)  creator customization to add relevant phrases to chat. |
| Moderation / admin commands | | [OnIncomingMessage](/docs/reference/engine/classes/TextChatService#OnIncomingMessage) , [Player.Chatted](/docs/reference/engine/classes/Player#Chatted) | | Use [TextChatCommand](/docs/reference/engine/classes/TextChatCommand)  for chat-triggered commands. Use read-only chat to view all chats for moderation during live events. |

## [Enable platform-integrated chat](#enable-platform-integrated-chat)[](#enable-platform-integrated-chat)

To enable platform-integrated chat in Studio:

1.

Open the [Explorer](/docs/studio/explorer)  window.

2.

Select [TextChatService](/docs/reference/engine/classes/TextChatService) .

3.

In the [Properties](/docs/studio/properties)  panel, find [PlatformIntegratedChat](/docs/reference/engine/classes/TextChatService#PlatformIntegratedChat) .

4.

Set it to Enabled .

With the update enabled, the unsupported APIs listed earlier return empty strings and log warnings. You can set the property back to Disabled  at any time to revert.

You can only change this property in Studio, not from a script.

## [Create a TextChannelWindow](#create-a-textchannelwindow)[](#create-a-textchannelwindow)

To create a [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow) :

1.

Create a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  in [StarterGui](/docs/reference/engine/classes/StarterGui) .

2.

Add a [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  instance as a child of the [ScreenGui](/docs/reference/engine/classes/ScreenGui) .

3.

Set the [Size](/docs/reference/engine/classes/GuiObject#Size)  and [Position](/docs/reference/engine/classes/GuiObject#Position)  properties to place the window where you want it.

4.

Set the [Target](/docs/reference/engine/classes/TextChannelWindow#Target)  property to the [TextChannel](/docs/reference/engine/classes/TextChannel)  you want the window to display.

Each [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  binds to a single [TextChannel](/docs/reference/engine/classes/TextChannel) . To show multiple channels together, create a [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  for each channel and apply your own show/hide logic. The Global channel isn't available as a target for a custom window.

The following code sample creates a custom chat window that displays the RBXGeneral  channel:

LocalScript in StarterGui

```

local TextChatService = game:GetService("TextChatService")

local screenGui = Instance.new("ScreenGui")

screenGui.Name = "TextChannelWindowDemo"

screenGui.Parent = script.Parent

local myTextChannelWindow = Instance.new("TextChannelWindow")

myTextChannelWindow.Size = UDim2.new(0, 400, 0, 300)

myTextChannelWindow.Position = UDim2.new(0, 10, 0, 10)

myTextChannelWindow.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

myTextChannelWindow.BackgroundTransparency = 0.5

local targetChannelName = "RBXGeneral"

local targetChannel = TextChatService:WaitForChild("TextChannels"):WaitForChild(targetChannelName)

if targetChannel and targetChannel:IsA("TextChannel") then

	myTextChannelWindow.Target = targetChannel

end

myTextChannelWindow.Parent = screenGui

```

## [Show a custom channel only in its own window](#show-a-custom-channel-only-in-its-own-window)[](#show-a-custom-channel-only-in-its-own-window)

By default, the default chat window renders messages from every [TextChannel](/docs/reference/engine/classes/TextChannel) , so a channel you show in a custom [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  also appears in the default window.

To show a custom channel only in its own window:

1.

In the Explorer, select [ChatWindowConfiguration](/docs/reference/engine/classes/ChatWindowConfiguration)  under [TextChatService](/docs/reference/engine/classes/TextChatService) .

2.

In the Properties  panel, set [TextChannelDisplayMode](/docs/reference/engine/classes/ChatWindowConfiguration#TextChannelDisplayMode)  to DefaultTextChannels .

3.

For each custom channel, create a [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  and set its [Target](/docs/reference/engine/classes/TextChannelWindow#Target)  to that channel.

The following example shows a custom Guild channel that appears only in its own window:

LocalScript in StarterPlayerScripts

```

-- Prerequisite: TextChannelDisplayMode is set to DefaultTextChannels in Studio.

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local playerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

-- Scripts can read the property at runtime, but can't change it.

local config = TextChatService.ChatWindowConfiguration

if config.TextChannelDisplayMode ~= Enum.TextChannelDisplayMode.DefaultTextChannels then

	warn("Guild messages will also appear in the default chat window.")

end

local guildChannel = TextChatService:WaitForChild("TextChannels"):WaitForChild("Guild")

local screenGui = Instance.new("ScreenGui")

screenGui.Name = "GuildChat"

screenGui.Parent = playerGui

local guildWindow = Instance.new("TextChannelWindow")

guildWindow.Size = UDim2.new(0, 400, 0, 300)

guildWindow.Target = guildChannel

guildWindow.Parent = screenGui

```

Keep these behaviors in mind:

-

You can set [TextChannelDisplayMode](/docs/reference/engine/classes/ChatWindowConfiguration#TextChannelDisplayMode)  only in Studio or from a plugin. Scripts can read it at runtime but can't change it.

-

The property exists only on [ChatWindowConfiguration](/docs/reference/engine/classes/ChatWindowConfiguration) . [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  doesn't need it because it already shows a single channel through [Target](/docs/reference/engine/classes/TextChannelWindow#Target) .

-

Channels created at runtime follow the current mode when they appear. Default channels created at runtime, such as Team and Whisper, still appear in the default window.

## [Migrate chat-triggered admin commands](#migrate-chat-triggered-admin-commands)[](#migrate-chat-triggered-admin-commands)

Whether you need to update your admin commands depends on how they are triggered:

-

Commands triggered from chat must use [TextChatCommand](/docs/reference/engine/classes/TextChatCommand) .

-

Command handling that reads raw chat text no longer works. This includes [MessageReceived](/docs/reference/engine/classes/TextChatService#MessageReceived) , [Chatted](/docs/reference/engine/classes/Player#Chatted) , or anything else that inspects [TextChatMessage](/docs/reference/engine/classes/TextChatMessage)  content.

To migrate:

1.

Identify admin commands in your game that currently parse raw chat messages.

2.

Create a [TextChatCommand](/docs/reference/engine/classes/TextChatCommand)  for each command.

3.

Define the command's trigger keyword and callback logic.

4.

Remove any code that reads [Text](/docs/reference/engine/classes/TextChatMessage#Text)  or listens to [Chatted](/docs/reference/engine/classes/Player#Chatted)  for command handling.

For an example, see [Custom text chat commands](/docs/chat/examples/custom-text-chat-commands) .

## [FAQ](#faq)[](#faq)

Will anything change if I do nothing?

Nothing changes in your game unless you set [PlatformIntegratedChat](/docs/reference/engine/classes/TextChatService#PlatformIntegratedChat)  to Enabled .

Does this affect signs, boards, notes, or other in-world text players can write?

No. Policy for those surfaces is unchanged: they can't be used for two-way communication between players, they need rate limiting of at least 1 minute, and they are subject to moderation.

Does this affect comment systems, message boards, or mail in my game?

No. This update covers [TextChatService](/docs/reference/engine/classes/TextChatService)  only.

Can I still record and pull chat logs as a game admin?

No. When [PlatformIntegratedChat](/docs/reference/engine/classes/TextChatService#PlatformIntegratedChat)  is Enabled , no API returns player message content on the client or server. Moderators in your game can still use read-only chat permissions to view chat. Players can also rely on Roblox's abuse reporting and on safety tools such as muting and blocking.

Do I need to change anything if I use the default Roblox chat?

No. If your game uses the default Roblox chat with no customizations, you don't need to take action and shouldn't see a change.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
