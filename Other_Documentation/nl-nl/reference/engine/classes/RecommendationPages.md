<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/RecommendationPages -->

RecommendationPages | Documentatie - Roblox Creator Hub

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
9. [RecommendationPages](/docs/nl-nl/reference/engine/classes/RecommendationPages)

Nederlands

Feedback

Engine-klasse

RecommendationPages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/RecommendationPages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

3  overgenomen van [Pages](/docs/nl-nl/reference/engine/classes/Pages)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Genereer een lijst met aanbevolen items

```

local RecommendationService = game:GetService("RecommendationService")

-- Definieer het verzoek voor het genereren van een aanbevelingslijst

local request: GenerateRecommendationItemListRequest = {

	ConfigName = "MaximizeEngagement",

	LocationId = "Lobby",

	PageSize = 10

    -- OPMERKING: Verwijder de opmerkingen en stel CustomContexts.UserId in voor Server-script.

    -- Niet nodig om in te stellen voor Local-script.

    -- CustomContexts = {

    --     ["UserId"] = tostring(player.UserId),

    -- }

}

-- Roep GenerateItemListAsync aan om de aanbevelingspagina's te krijgen

local success, recommendationPages = pcall(function()

    return RecommendationService:GenerateItemListAsync(request)

end)

if success then

	-- Verkrijg de huidige pagina van aanbevolen items

	local currentPage = recommendationPages:GetCurrentPage()

	for _, item in ipairs(currentPage) do

		print("ItemId: " .. item.ItemId)

		print("  ReferenceId: " .. item.ReferenceId)

		print("  TracingId: " .. item.TracingId)

	end

else

	warn("RecommendationService fout: " .. tostring(recommendationPages))

end

--[[ Gegevensformaat dat wordt geretourneerd voor elk item op de pagina

{

    "ItemId": string,

    "ReferenceId": string,

    "TracingId": string,

    "Creator": {

        "CreatorId": number,

        "CreatorType": Enum.CreatorType,

    }?,

    "Attributes": {

        {

            "AssetId": number?,

            "Text": string?,

            "Description": string?,

            "SeekStartTime": number?,

            "SeekEndTime": number?,

            "TrimStartTime": number?,

            "TrimEndTime": number?

        }

    }?,

    "CustomTags": { string }?

}

--]]

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
