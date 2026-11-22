<!-- Source: https://create.roblox.com/docs/nl-nl/chat/examples/custom-text-chat-commands -->

Aangepaste tekstchatopdrachten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)
8. /
9. [Voorbeelden](/docs/nl-nl/chat/examples/simple-custom-frontend-ui)

# Aangepaste tekstchatopdrachten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  heeft ingebouwde chatopdrachten voor veelvoorkomende doeleinden, zoals het dempen van andere spelers en het gebruiken van avatar-emotes. Je kunt ze inschakelen door [CreateDefaultCommands](/docs/nl-nl/reference/engine/classes/TextChatService#CreateDefaultCommands)  in het Eigenschappen -venster van Studio op true  te zetten.

Je kunt ook aangepaste opdrachten toevoegen met [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand) . Gebruikers die een gedefinieerde opdracht in de chatinvoerveld invoeren, activeren een callback die is gedefinieerd door [TextChatCommand.Triggered](/docs/nl-nl/reference/engine/classes/TextChatCommand#Triggered)  om jouw aangepaste acties uit te voeren.

Het volgende voorbeeld laat zien hoe je een chatopdracht kunt maken die spelers in staat stelt om de grootte van hun karakter te vergroten of te verkleinen wanneer ze /super  of /mini  invoeren.

1.

Voeg een [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand) -instantie toe binnen [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

2.

Hernoem het naar SizeCommand .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-TextChatCommand.png)

3.

Stel de [PrimaryAlias](/docs/nl-nl/reference/engine/classes/TextChatCommand#PrimaryAlias) -eigenschap in op /super  en de [SecondaryAlias](/docs/nl-nl/reference/engine/classes/TextChatCommand#SecondaryAlias)  op /mini .

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatCommand-Aliases.png)

4.

Voeg de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  in om een callback te definiëren voor de chatopdracht die de grootte van het karakter schaalt:

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

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
