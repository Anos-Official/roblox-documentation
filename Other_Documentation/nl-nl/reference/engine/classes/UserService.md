<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/UserService -->

UserService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [UserService](/docs/nl-nl/reference/engine/classes/UserService)

Nederlands

Feedback

Engine-klasse

UserService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/UserService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetUserInfosByUserIdsAsync](#GetUserInfosByUserIdsAsync) (userIds :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
| --- | --- |
|

[GetUserFromGlobalUserIdAsync](#GetUserFromGlobalUserIdAsync) (userId :  [number](/docs/nl-nl/luau/numbers) ) :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GetUserInfosByUserIdsAsync

Opbrengst

Mogelijkheden: Basic

UserService:GetUserInfosByUserIdsAsync (userIds :[{any}](/docs/nl-nl/luau/tables#arrays) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

userIds :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Voorbeeld van UserService:GetUserInfosByUserIdsAsync

```

local UserService = game:GetService("UserService")

local success, result = pcall(function()

	return UserService:GetUserInfosByUserIdsAsync({ 156, 1, 735878936 })

end)

if success then

	for _, userInfo in ipairs(result) do

		print("Id:", userInfo.Id)

		print("Gebruikersnaam:", userInfo.Username)

		print("Weergavenaam:", userInfo.DisplayName)

	end

else

	-- Er is een fout opgetreden

end

```

Feedback geven

---

GetUserFromGlobalUserIdAsync

Opbrengst

Mogelijkheden: Basic

UserService:GetUserFromGlobalUserIdAsync (userId :[number](/docs/nl-nl/luau/numbers) ) :[User](/docs/nl-nl/reference/engine/datatypes/User)

Parameters

|

userId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[User](/docs/nl-nl/reference/engine/datatypes/User)

Codevoorbeelden

Haal gebruiker op via globale gebruikers-ID asynchroon

```

local UserService = game:GetService("UserService")

local user = UserService:GetUserFromGlobalUserIdAsync(globalUserId)

print(user.Id)         -- Domein gebruikers-ID voor deze ervaring

print(user.DomainType) -- Enum.DomainType.Experience

print(user.DomainId)   -- Huidige universum-ID

```

Feedback geven

---

Ga naar

▼

UserService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetUserInfosByUserIdsAsync()](#GetUserInfosByUserIdsAsync)

[GetUserFromGlobalUserIdAsync()](#GetUserFromGlobalUserIdAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
