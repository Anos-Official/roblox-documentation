<!-- Source: https://create.roblox.com/docs/nl-nl/chat/examples/group-chat-tags -->

Chat-tags toewijzen | Documentatie - Roblox Creator Hub

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

# Chat-tags toewijzen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit voorbeeld demonstreert hoe je chat-tags  aan spelers kunt toewijzen op basis van hun lidmaatschap in een [groep](/docs/nl-nl/projects/groups) . Chat-tags zijn een manier om een speler visueel te identificeren in het chatvenster en zijn nuttig om de rol of status van een speler aan te geven.

 ![VIP chat-tag toegevoegd aan de gebruikersnaam in het chatvenster.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Tag-VIP.png)

Omdat [tekstchat-callbacks](/docs/nl-nl/chat/in-experience-text-chat#text-chat-hooks-and-callbacks)  een niet-blokkerende callback verwachten, wordt het niet aanbevolen om de groepslidmaatschapsstatus van een speler op te vragen in de [TextChatService.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#OnIncomingMessage)  callback, omdat dit het chatsysteem kan laten vastlopen of onresponsief kan maken.

Stel in plaats daarvan een [attribuut](/docs/nl-nl/studio/properties#instance-attributes)  in voor een speler wanneer deze de server betreedt. Het instellen van een attribuut stelt je in staat om de status van de speler in andere delen van je game te hergebruiken, zoals het toestaan van toegang tot bepaalde gebieden of het bieden van bonuservaringen.

1.

Maak een [Script](/docs/nl-nl/reference/engine/classes/Script)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  en voeg de volgende code toe:

Server

```

local Players = game:GetService("Players")

-- Vervang 123456 door de groeps-ID die je wilt controleren

local groupID = 123456

Players.PlayerAdded:Connect(function(player)

	local success, isInGroup = pcall(function()

		return player:IsInGroupAsync(groupID)

	end)

	if success and isInGroup then

		player:SetAttribute("IsVIP", true)

	else

		player:SetAttribute("IsVIP", false)

	end

end)

```

2.

Maak een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  ⟩ [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  en voeg de volgende code toe om een [VIP]  tag in het chatvenster weer te geven:

Client

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

TextChatService.OnIncomingMessage = function(message: TextChatMessage)

	local textSource = message.TextSource

	if textSource then

		local player = Players:GetPlayerByUserId(textSource.UserId)

		if player then

			if player:GetAttribute("IsVIP") == true then

				local overrideProperties = Instance.new("TextChatMessageProperties")

				overrideProperties.PrefixText = "[VIP] " .. message.PrefixText

				return overrideProperties

			end

		end

	end

	return nil

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
