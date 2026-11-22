<!-- Source: https://create.roblox.com/docs/nl-nl/luau/tuples -->

Tuples | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Typen

# Tuples

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een tuple  is een lijst van waarden. Veel [methoden](/docs/nl-nl/luau/functions#methoden)  en [callbacks](/docs/nl-nl/luau/functions#callbacks)  in de [Roblox Engine API](/docs/nl-nl/reference/engine)  accepteren en retourneren meerdere waarden, maar de API Referentie zegt "Tuple" in plaats van die waarden.

## [Parameters](#parameters)[](#parameters)

Als een [methode](/docs/nl-nl/luau/functions#methoden)  of [callback](/docs/nl-nl/luau/functions#callbacks)  een tuple als parameter accepteert, dan accepteert het meerdere waarden. Bijvoorbeeld, de API Referentie toont aan dat de [BindableFunction:Invoke()](/docs/nl-nl/reference/engine/classes/BindableFunction#Invoke)  methode een "Tuple" als parameter accepteert, dus het accepteert meerdere argumenten.

```

BindableFunction:Invoke(1, true, "string", Vector3.new(0, 0, 0))

```

## [Returns](#returns)[](#returns)

Als een [methode](/docs/nl-nl/luau/functions#methoden)  of [callback](/docs/nl-nl/luau/functions#callbacks)  een tuple retourneert, dan retourneert het meerdere waarden. Bijvoorbeeld, de API Referentie toont aan dat de [Players:GetUserThumbnailAsync()](/docs/nl-nl/reference/engine/classes/Players#GetUserThumbnailAsync)  methode een "Tuple" retourneert, dus het retourneert meerdere waarden. De eerste retourwaarde is een Content URL, en de tweede is een [boolean](/docs/nl-nl/luau/booleans) .

```

local Players = game:GetService("Players")

local userId = 156 -- builderman

local thumbType = Enum.ThumbnailType.HeadShot

local thumbSize = Enum.ThumbnailSize.Size420x420

local content, isReady = Players:GetUserThumbnailAsync(userId, thumbType, thumbSize)

print(content, isReady) -- rbxthumb://type=AvatarHeadShot&id=156&w=420&h=420 true

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
