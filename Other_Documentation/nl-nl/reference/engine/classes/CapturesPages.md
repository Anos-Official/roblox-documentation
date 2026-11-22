<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/CapturesPages -->

CapturesPages | Documentatie - Roblox Creator Hub

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
9. [CapturesPages](/docs/nl-nl/reference/engine/classes/CapturesPages)

Nederlands

Feedback

Engine-klasse

CapturesPages

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/CapturesPages)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

3  overgenomen van [Pages](/docs/nl-nl/reference/engine/classes/Pages)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Lees captures uit de galerij en doorloop pagina's

```

local CaptureService = game:GetService("CaptureService")

local function readCapturesFromGallery()

	local allCaptures = {}

	local capturesPages

	local success, result = pcall(function()

		local readResult, pages = CaptureService:ReadCapturesFromGalleryAsync({}, false)

		if readResult == Enum.ReadCapturesFromGalleryResult.Success then

			capturesPages = pages

		end

		return readResult

	end)

	if not success or result ~= Enum.ReadCapturesFromGalleryResult.Success then

		-- Waarschijnlijk een machtigingsfout, zie CaptureService:PromptCaptureGalleryPermissionAsync()

		warn("Kon de initiële captures niet ophalen: " .. result.Name)

		return

	end

	-- Doorloop de huidige pagina

	local currentPage = capturesPages:GetCurrentPage()

	for _, capture in currentPage do

		table.insert(allCaptures, capture)

	end

	-- Ga door naar de volgende pagina totdat deze is voltooid

	while not capturesPages.IsFinished do

		local advanceToNextPageSuccess, _ = pcall(function()

			capturesPages:AdvanceToNextPageAsync()

		end)

		if not advanceToNextPageSuccess then

			return

		end

		currentPage = capturesPages:GetCurrentPage()

		for _, capture in currentPage do

			table.insert(allCaptures, capture)

		end

	end

	return allCaptures

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
