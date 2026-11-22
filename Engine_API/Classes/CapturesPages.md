<!-- Source: https://create.roblox.com/docs/reference/engine/classes/CapturesPages -->

CapturesPages | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/CapturesPages.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/reference/engine/classes/Pages)
8. /
9. [CapturesPages](/docs/reference/engine/classes/CapturesPages)

English

Feedback

Engine Class

CapturesPages

Not Creatable

Not Replicated

---

## Summary

Inherited Members

3  inherited from [Pages](/docs/reference/engine/classes/Pages)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Read captures from gallery and iterate over pages

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

		-- Likely a permissions error, see CaptureService:PromptCaptureGalleryPermissionAsync()

		warn("Failed to fetch initial captures: " .. result.Name)

		return

	end

	-- Iterate through current page

	local currentPage = capturesPages:GetCurrentPage()

	for _, capture in currentPage do

		table.insert(allCaptures, capture)

	end

	-- Advance to next page until finished

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

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
