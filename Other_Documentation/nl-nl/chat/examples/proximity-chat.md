<!-- Source: https://create.roblox.com/docs/nl-nl/chat/examples/proximity-chat -->

Nabijheidsgebaseerde chat | Documentatie - Roblox Creator Hub

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

# Nabijheidsgebaseerde chat

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit voorbeeld laat zien hoe je een exclusieve chat kunt implementeren voor gebruikers die dicht bij elkaar zijn in de 3D-wereld. Het breidt de callback uit met een functie die [TextSource](/docs/nl-nl/reference/engine/classes/TextSource)  gebruikt om de locaties van een gebruiker te identificeren die een potentiële ontvanger van een bericht zou kunnen zijn. Als deze functie false  retourneert, betekent dit dat de gebruiker verder weg is dan het vooraf ingestelde geldige bereik van de berichtsender, zodat het systeem het bericht niet aan die gebruiker levert.

Voeg het volgende toe aan een [Script](/docs/nl-nl/reference/engine/classes/Script)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) :

Server

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

-- Verkrijg het chatkanaal voor nabijheidsgebaseerde chat

-- Je kunt dit algemene kanaal vervangen door een speciaal kanaal

local generalChannel: TextChannel = TextChatService:WaitForChild("TextChannels").RBXGeneral

-- Functie om de positie van het karakter van een gebruiker te krijgen

local function getPositionFromUserId(userId: number)

	-- Verkrijg de speler die is gekoppeld aan de gegeven gebruikers-ID

	local targetPlayer = Players:GetPlayerByUserId(userId)

	-- Als de speler bestaat, verkrijg dan de positie van hun karakter

	if targetPlayer then

		local targetCharacter = targetPlayer.Character

		if targetCharacter then

			return targetCharacter:GetPivot().Position

		end

	end

	-- Geef een standaardpositie terug als de speler of het karakter niet kan worden gevonden

	return Vector3.zero

end

-- Stel de callback in voor het algemene kanaal om de berichtlevering te controleren

generalChannel.ShouldDeliverCallback = function(textChatMessage: TextChatMessage, targetTextSource: TextSource)

	-- Verkrijg de posities van de berichtsender en de doelwit

	local sourcePos = getPositionFromUserId(textChatMessage.TextSource.UserId)

	local targetPos = getPositionFromUserId(targetTextSource.UserId)

	-- Lever het bericht als de afstand tussen sender en doelwit minder is dan 50 eenheden

	return (targetPos - sourcePos).Magnitude < 50

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
