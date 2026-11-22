<!-- Source: https://create.roblox.com/docs/chat/examples/simple-custom-frontend-ui -->

Custom text chat UI | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/examples/simple-custom-frontend-ui.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/chat/in-experience-text-chat)
8. /
9. [Examples](/docs/chat/examples/simple-custom-frontend-ui)

# Custom text chat UI

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/examples/simple-custom-frontend-ui.md)

When [platform-integrated chat](/docs/chat/platform-integrated-chat)  is enabled, custom UIs can no longer render player message text themselves. Use [TextChannelWindow](/docs/reference/engine/classes/TextChannelWindow)  instead of reading [Text](/docs/reference/engine/classes/TextChatMessage#Text)  or listening to [MessageReceived](/docs/reference/engine/classes/TextChatService#MessageReceived)  for display.

This example shows how to use the [TextChatService](/docs/reference/engine/classes/TextChatService)  class to design your own frontend. It reuses the default text channels from [CreateDefaultTextChannels](/docs/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  and is very simple compared to the default UI.

1.

Disable the default UI that comes with the [TextChatService](/docs/reference/engine/classes/TextChatService)  by setting the [ChatWindowConfiguration.Enabled](/docs/reference/engine/classes/ChatWindowConfiguration#Enabled)  and [ChatInputBarConfiguration.Enabled](/docs/reference/engine/classes/ChatInputBarConfiguration#Enabled)  properties to false  in Studio's Properties  window.

2.

Create a replacement for the chat input bar. This is the text box that emits messages when the user presses Enter .

1.

Create a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  and parent it to [StarterGui](/docs/reference/engine/classes/StarterGui) .

2.

Create a [TextBox](/docs/reference/engine/classes/TextBox)  and parent it to the new [ScreenGui](/docs/reference/engine/classes/ScreenGui) , then [reposition](/docs/ui/position-and-size#position)  and [resize](/docs/ui/position-and-size#size)  it as desired.

3.

Create a [LocalScript](/docs/reference/engine/classes/LocalScript)  and parent it to the new [TextBox](/docs/reference/engine/classes/TextBox) .

4.

Add the following code to the [LocalScript](/docs/reference/engine/classes/LocalScript) :

Client

```

local TextChatService = game:GetService("TextChatService")

-- RBXGeneral is the default public channel

local RBXGeneral = TextChatService:FindFirstChild("TextChannels"):WaitForChild("RBXGeneral")

local textBox = script.Parent

textBox.FocusLost:Connect(function(enterPressed)

	local text = textBox.Text

	if enterPressed and #text > 0 then

		local success, response = pcall(function()

			return RBXGeneral:SendAsync(textBox.Text)

		end)

		if not success then

			RBXGeneral:DisplaySystemMessage("Failed to send message")

		end

		-- Users expect the input box to be cleared after sending a message

		textBox.Text = ""

	end

end)

```

3.

Create a replacement for the chat window. This is the [ScrollingFrame](/docs/reference/engine/classes/ScrollingFrame)  that displays messages as they are received from [TextChatService.MessageReceived](/docs/reference/engine/classes/TextChatService#MessageReceived) . This step also creates a [UIListLayout](/docs/reference/engine/classes/UIListLayout)  to automatically layout the messages.

1.

Create another new [ScreenGui](/docs/reference/engine/classes/ScreenGui)  and parent it to [StarterGui](/docs/reference/engine/classes/StarterGui) .

2.

Create a [ScrollingFrame](/docs/reference/engine/classes/ScrollingFrame)  and parent it to the ScreenGui , then [reposition](/docs/ui/position-and-size#position)  and [resize](/docs/ui/position-and-size#size)  it as desired.

3.

Create a [UIListLayout](/docs/reference/engine/classes/UIListLayout)  and parent it to the [ScrollingFrame](/docs/reference/engine/classes/ScrollingFrame) .

4.

Create a [LocalScript](/docs/reference/engine/classes/LocalScript)  and parent it to the [ScrollingFrame](/docs/reference/engine/classes/ScrollingFrame) .

5.

Add the following code to the [LocalScript](/docs/reference/engine/classes/LocalScript) :

Client

```

local TextChatService = game:GetService("TextChatService")

-- Function to create a new text label for each message received

local function addMessageGui(textChatMessage: TextChatMessage)

	local isOutgoingMessage = textChatMessage.Status == Enum.TextChatMessageStatus.Sending

	local parent = script.Parent

	local originalLabel = parent:FindFirstChild(textChatMessage.MessageId)

	if originalLabel then

		originalLabel.Text = textChatMessage.Text

		originalLabel.BackgroundTransparency = if isOutgoingMessage then 0.5 else 0

	else

		local textLabel = Instance.new("TextLabel")

		textLabel.BorderSizePixel = 0

		textLabel.Font = Enum.Font.BuilderSans

		textLabel.TextSize = 18

		textLabel.TextXAlignment = Enum.TextXAlignment.Left

		textLabel.BackgroundTransparency = if isOutgoingMessage then 0.5 else 0

		textLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)

		textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

		textLabel.Name = textChatMessage.MessageId

		textLabel.AutomaticSize = Enum.AutomaticSize.XY

		textLabel.Text = textChatMessage.Text

		textLabel.Parent = parent

	end

end

-- Start listening for incoming messages

TextChatService.MessageReceived:Connect(addMessageGui)

```

When using the [TextChatService.MessageReceived](/docs/reference/engine/classes/TextChatService#MessageReceived)  event, it's important to check if the message already exists in the chat window. This event is called once when sending and once when the message is received from the server.

4.

Test your game by sending messages in the chat input bar. You should see the messages appear in the chat window. You can then expand on this example by adding features such as focusing the [TextBox](/docs/reference/engine/classes/TextBox)  when a key is pressed or adding [chat tags](/docs/chat/examples/group-chat-tags) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
