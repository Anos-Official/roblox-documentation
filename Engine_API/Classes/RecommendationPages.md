<!-- Source: https://create.roblox.com/docs/reference/engine/classes/RecommendationPages -->

RecommendationPages | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/RecommendationPages.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/reference/engine/classes/Pages)
8. /
9. [RecommendationPages](/docs/reference/engine/classes/RecommendationPages)

English

Feedback

Engine Class

RecommendationPages

Not Creatable

Not Replicated

---

## Summary

Inherited Members

3  inherited from [Pages](/docs/reference/engine/classes/Pages)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Generate a list of recommended items

```

local RecommendationService = game:GetService("RecommendationService")

-- Define the request for generating a recommendation list

local request: GenerateRecommendationItemListRequest = {

	ConfigName = "MaximizeEngagement",

	LocationId = "Lobby",

	PageSize = 10

    -- NOTE: Uncomment and set CustomContexts.UserId for Server script.

    -- No need to set for Local script.

    -- CustomContexts = {

    --     ["UserId"] = tostring(player.UserId),

    -- }

}

-- Call GenerateItemListAsync to get the recommendation pages

local success, recommendationPages = pcall(function()

    return RecommendationService:GenerateItemListAsync(request)

end)

if success then

	-- Get the current page of recommended items

	local currentPage = recommendationPages:GetCurrentPage()

	for _, item in ipairs(currentPage) do

		print("ItemId: " .. item.ItemId)

		print("  ReferenceId: " .. item.ReferenceId)

		print("  TracingId: " .. item.TracingId)

	end

else

	warn("RecommendationService error: " .. tostring(recommendationPages))

end

--[[ Returned data format for each item in the page

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

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
