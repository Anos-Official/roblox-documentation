<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioPages -->

AudioPages | Documentatie - Roblox Creator Hub

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
9. [AudioPages](/docs/nl-nl/reference/engine/classes/AudioPages)

Nederlands

Feedback

Engine-klasse

AudioPages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioPages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

3  overgenomen van [Pages](/docs/nl-nl/reference/engine/classes/Pages)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Muziek Zoek Titels Krijgen

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

	warn("AssetService fout: " .. result)

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

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
