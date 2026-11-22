<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/FriendPages -->

FriendPages | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/nl-nl/reference/engine/classes/Pages)
8. /
9. [FriendPages](/docs/nl-nl/reference/engine/classes/FriendPages)

Nederlands

Feedback

Engine-klasse

FriendPages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/FriendPages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

3  overgenomen van [Pages](/docs/nl-nl/reference/engine/classes/Pages)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Print Roblox Vrienden

```

local Players = game:GetService("Players")

local USERNAME = "Cozecant"

-- Eerst, haal de gebruikers-ID van de speler op

local userId = Players:GetUserIdFromNameAsync(USERNAME)

-- Vervolgens, haal een FriendPages-object op voor hun vrienden

local friendPages = Players:GetFriendsAsync(userId)

-- Loop door de pagina's en verzamel de gebruikersnaam van elke vriend. Elke pagina-invoer is

-- een tabel met informatie over de vriend, inclusief Gebruikersnaam.

local usernames = {}

while true do

	for _, friend in ipairs(friendPages:GetCurrentPage()) do

		table.insert(usernames, friend.Username)

	end

	if friendPages.IsFinished then

		break

	end

	friendPages:AdvanceToNextPageAsync()

end

print("Vrienden van " .. USERNAME .. ": " .. table.concat(usernames, ", "))

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
