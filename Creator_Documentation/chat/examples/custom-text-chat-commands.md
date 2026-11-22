<!-- Source: https://create.roblox.com/docs/en-us/chat/examples/custom-text-chat-commands -->

Custom text chat commands | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/examples/custom-text-chat-commands.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/en-us/chat/in-experience-text-chat)
8. /
9. [Examples](/docs/en-us/chat/examples/simple-custom-frontend-ui)

# Custom text chat commands

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/examples/custom-text-chat-commands.md)

[TextChatService](/docs/en-us/reference/engine/classes/TextChatService)  has built-in chat commands for common purposes, such as muting other players and using avatar emotes. You can enable them by setting [CreateDefaultCommands](/docs/en-us/reference/engine/classes/TextChatService#CreateDefaultCommands)  to true  in Studio's Properties  window.

You can also add custom commands using [TextChatCommand](/docs/en-us/reference/engine/classes/TextChatCommand) . Users sending a defined command in the chat input bar trigger a callback defined by [TextChatCommand.Triggered](/docs/en-us/reference/engine/classes/TextChatCommand#Triggered)  to perform your customized actions.

The following example shows how to create a chat command that allows players to increase or decrease their character's size when they input /super  or /mini .

1.

Add a [TextChatCommand](/docs/en-us/reference/engine/classes/TextChatCommand)  instance inside [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) .

2.

Rename it to SizeCommand .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-TextChatCommand.png)

3.

Set its [PrimaryAlias](/docs/en-us/reference/engine/classes/TextChatCommand#PrimaryAlias)  property to /super  and its [SecondaryAlias](/docs/en-us/reference/engine/classes/TextChatCommand#SecondaryAlias)  to /mini .

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatCommand-Aliases.png)

4.

Insert the following [Script](/docs/en-us/reference/engine/classes/Script)  inside [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService)  to define a callback for the chat command that scales the character's size:

Script

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local sizeCommand: TextChatCommand = TextChatService:WaitForChild("SizeCommand")

sizeCommand.Triggered:Connect(function(textSource, message)

	local scaleMult = 1

	local messageWords = string.split(message, " ")

	if messageWords[1] == "/super" then

		scaleMult = 2

	elseif messageWords[1] == "/mini" then

		scaleMult = 0.5

	end

	local player = Players:GetPlayerByUserId(textSource.UserId)

	if player then

		local character = player.Character

		if character then

			local humanoid = character:FindFirstChildWhichIsA("Humanoid")

			if humanoid then

				for _, child in humanoid:GetChildren() do

					if child:IsA("NumberValue") then

						child.Value *= scaleMult

					end

				end

			end

		end

	end

end)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
