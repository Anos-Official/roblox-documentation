<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/BadgeService -->

BadgeService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [BadgeService](/docs/nl-nl/reference/engine/classes/BadgeService)

Nederlands

Feedback

Engine-klasse

BadgeService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/BadgeService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[AwardBadge](#AwardBadge) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
| --- | --- |
|

[AwardBadgeAsync](#AwardBadgeAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CheckUserBadgesAsync](#CheckUserBadgesAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , badgeIds :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetBadgeInfoAsync](#GetBadgeInfoAsync) (badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetUserBadgesAsync](#GetUserBadgesAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , badgeIds :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[IsDisabled](#IsDisabled) (badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[IsLegal](#IsLegal) (badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[UserHasBadge](#UserHasBadge) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[UserHasBadgeAsync](#UserHasBadgeAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , badgeId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

AwardBadge

Verouderd

Details weergeven

---

AwardBadgeAsync

Opbrengst

Mogelijkheden: AssetManagement

BadgeService:AwardBadgeAsync (

userId :[User](/docs/nl-nl/reference/engine/datatypes/User) , badgeId :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

badgeId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Een Badge Toekennen

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local BADGE_ID = 0

local function awardBadge(player, badgeId)

	-- Haal badge-informatie op

	local success, badgeInfo = pcall(function()

		return BadgeService:GetBadgeInfoAsync(badgeId)

	end)

	if success then

		-- Bevestig dat de badge kan worden toegekend

		if badgeInfo.IsEnabled then

			-- Ken badge toe

			local awarded, errorMessage = pcall(BadgeService.AwardBadgeAsync, BadgeService, player.UserId, badgeId)

			if not awarded then

				warn("Fout bij het toekennen van de badge:", errorMessage)

			end

		end

	else

		warn("Fout bij het ophalen van badge-informatie: " .. badgeInfo)

	end

end

local function onPlayerAdded(player)

	awardBadge(player, BADGE_ID)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Feedback geven

---

CheckUserBadgesAsync

Opbrengst

Mogelijkheden: AssetManagement

BadgeService:CheckUserBadgesAsync (

userId :[User](/docs/nl-nl/reference/engine/datatypes/User) , badgeIds :[{any}](/docs/nl-nl/luau/tables#arrays)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

badgeIds :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Controle van Verworven Badges in Batch

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local badgeIds = { 0000000000, 1111111111, 2222222222 } -- Verander dit in een lijst van jouw badge-ID's

local function onPlayerAdded(player)

	-- Controleer of de speler een van de badges heeft

	local success, result = pcall(function()

		return BadgeService:CheckUserBadgesAsync(player.UserId, badgeIds)

	end)

	-- Als er een fout is, geef een waarschuwing en verlaat de functie

	if not success then

		warn("Fout bij het controleren of speler", player.Name, "badges heeft:", result)

		return

	end

	local ownedBadgeIds = result

	if #ownedBadgeIds == 0 then

		print(player.Name, "heeft geen van de badges")

	else

		print(player.Name, "heeft de volgende badges:", table.concat(ownedBadgeIds, ", "))

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Feedback geven

---

GetBadgeInfoAsync

Opbrengst

Mogelijkheden: AssetManagement

BadgeService:GetBadgeInfoAsync (badgeId :[number](/docs/nl-nl/luau/numbers) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

badgeId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Badge-informatie ophalen

```

local BadgeService = game:GetService("BadgeService")

-- Haal badge-informatie op

local success, result = pcall(function()

	return BadgeService:GetBadgeInfoAsync(00000000) -- Verander dit naar de gewenste badge-ID

end)

-- Geef de informatie weer

if success then

	print("Badge:", result.Name)

	print("Ingeschakeld:", result.IsEnabled)

	print("Beschrijving:", result.Description)

	print("Pictogram:", "rbxassetid://" .. result.IconImageId)

else

	warn("Fout bij het ophalen van badge-informatie:", result)

end

```

Feedback geven

---

GetUserBadgesAsync

Opbrengst

Mogelijkheden: AssetManagement

BadgeService:GetUserBadgesAsync (

userId :[User](/docs/nl-nl/reference/engine/datatypes/User) , badgeIds :[{any}](/docs/nl-nl/luau/tables#arrays)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

badgeIds :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Verkregen Badges en Toekenningsdata

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local badgeIds = { 0000000000, 1111111111, 2222222222 } -- Wijzig dit in een lijst van jouw badge-ID's

local function onPlayerAdded(player)

	-- Verkrijg welke van de badges de speler bezit, samen met wanneer elke is toegekend

	local success, result = pcall(function()

		return BadgeService:GetUserBadgesAsync(player.UserId, badgeIds)

	end)

	-- Als er een fout is, geef een waarschuwing en verlaat de functie

	if not success then

		warn("Fout bij het verkrijgen van badges voor speler", player.Name, ":", result)

		return

	end

	local ownedBadges = result

	if #ownedBadges == 0 then

		print(player.Name, "heeft geen van de badges")

	else

		for _, badge in ownedBadges do

			print(player.Name, "werd de badge toegekend", badge.BadgeId, "op", badge.AwardedDate:ToIsoDate())

		end

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Feedback geven

---

IsDisabled

Verouderd

Details weergeven

---

IsLegal

Verouderd

Details weergeven

---

UserHasBadge

Verouderd

Details weergeven

---

UserHasBadgeAsync

Opbrengst

Mogelijkheden: AssetManagement

BadgeService:UserHasBadgeAsync (

userId :[User](/docs/nl-nl/reference/engine/datatypes/User) , badgeId :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

badgeId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Controle van Verdiende Badges

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local badgeId = 00000000 -- Verander dit naar je badge-ID

local function onPlayerAdded(player)

	-- Controleer of de speler de badge heeft

	local success, hasBadge = pcall(function()

		return BadgeService:UserHasBadgeAsync(player.UserId, badgeId)

	end)

	-- Als er een fout is, geef een waarschuwing en verlaat de functie

	if not success then

		warn("Fout bij het controleren of de speler de badge heeft!")

		return

	end

	if hasBadge then

		-- Behandel het bezit van de badge door de speler zoals nodig

		print(player.Name, "heeft badge", badgeId)

	end

end

-- Verbind "PlayerAdded"-evenementen met de "onPlayerAdded()"-functie

Players.PlayerAdded:Connect(onPlayerAdded)

```

Feedback geven

---

Ga naar

▼

BadgeService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[AwardBadge()](#AwardBadge)

[AwardBadgeAsync()](#AwardBadgeAsync)

[CheckUserBadgesAsync()](#CheckUserBadgesAsync)

[GetBadgeInfoAsync()](#GetBadgeInfoAsync)

[GetUserBadgesAsync()](#GetUserBadgesAsync)

[IsDisabled()](#IsDisabled)

[IsLegal()](#IsLegal)

[UserHasBadge()](#UserHasBadge)

[UserHasBadgeAsync()](#UserHasBadgeAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
