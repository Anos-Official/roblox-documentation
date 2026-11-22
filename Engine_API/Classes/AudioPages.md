<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioPages -->

AudioPages | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioPages.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/reference/engine/classes/Pages)
8. /
9. [AudioPages](/docs/reference/engine/classes/AudioPages)

English

Feedback

Engine Class

AudioPages

Not Creatable

Not Replicated

---

## Summary

Inherited Members

3  inherited from [Pages](/docs/reference/engine/classes/Pages)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Getting Music Search Titles

```

local AssetService = game:GetService("AssetService")

local audioSearchParams = Instance.new("AudioSearchParams")

audioSearchParams.SearchKeyword = "happy"

local success, result = pcall(function()

	return AssetService:SearchAudioAsync(audioSearchParams)

end)

if success then

	local currentPage = result:GetCurrentPage()

	for _, audio in currentPage do

		print(audio.Title)

	end

else

	warn("AssetService error: " .. result)

end

--[[ Returned data format

{

    "AudioType": string,

    "Artist": string,

    "Title": string,

    "Tags": {

        "string"

    },

    "Id": number,

    "IsEndorsed": boolean,

    "Description": string,

    "Duration": number,

    "CreateTime": string,

    "UpdateTime": string,

    "Creator": {

        "Id": number,

        "Name": string,

        "Type": number,

        "IsVerifiedCreator": boolean

    }

}

--]]

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
