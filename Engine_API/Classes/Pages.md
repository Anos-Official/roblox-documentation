<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Pages -->

Pages | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Pages.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/reference/engine/classes/Pages)

English

Feedback

Engine Class

Pages

Not Creatable

Not Replicated

---

## Summary

Properties

|

[IsFinished](#IsFinished) :[boolean](/docs/luau/booleans)

 |
| --- | --- |

Methods

|

[AdvanceToNextPageAsync](#AdvanceToNextPageAsync) () : ()

 |
|

[GetCurrentPage](#GetCurrentPage) () :[{any}](/docs/luau/tables#arrays)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[AudioPages](/docs/reference/engine/classes/AudioPages) , [BanHistoryPages](/docs/reference/engine/classes/BanHistoryPages) , [CapturesPages](/docs/reference/engine/classes/CapturesPages) , [CatalogPages](/docs/reference/engine/classes/CatalogPages) , [DataStoreKeyPages](/docs/reference/engine/classes/DataStoreKeyPages) , Show more...

Code Samples

Pages Iterator

```

-- Reformat pages as tables

local function pagesToTable(pages)

	local items = {}

	while true do

		table.insert(items, pages:GetCurrentPage())

		if pages.IsFinished then

			break

		end

		pages:AdvanceToNextPageAsync()

	end

	return items

end

local function iterPageItems(pages)

	local contents = pagesToTable(pages)

	-- Track the current page number starting at 1

	local pageNum = 1

	-- Get last page number so we don't iterate over it

	local lastPageNum = #contents

	-- for resumes this coroutine until there's nothing to go through

	return coroutine.wrap(function()

		-- Loop until page number is greater than last page number

		while pageNum <= lastPageNum do

			-- Go through all the entries of the current page

			for _, item in ipairs(contents[pageNum]) do

				-- Pause loop to let developer handle entry and page number

				coroutine.yield(item, pageNum)

			end

			pageNum += 1

		end

	end)

end

-- Using the iterPageItems function to iterate through the pages of a catalog search

local AvatarEditorService = game:GetService("AvatarEditorService")

local parameters = CatalogSearchParams.new()

parameters.SearchKeyword = "Hair"

local catalogPages = AvatarEditorService:SearchCatalogAsync(parameters)

for item, pageNumber in iterPageItems(catalogPages) do

	print(item, pageNumber)

end

```

---

API Reference

Properties

IsFinished

Read Only

Not Replicated

Read Parallel

Pages.IsFinished :[boolean](/docs/luau/booleans)

Provide feedback

---

Methods

AdvanceToNextPageAsync

Yields

Pages:AdvanceToNextPageAsync () : ()

Returns

()

Provide feedback

---

GetCurrentPage

Pages:GetCurrentPage () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

Jump to

▼

Pages

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[IsFinished](#IsFinished)

[Methods](#methods)

[AdvanceToNextPageAsync()](#AdvanceToNextPageAsync)

[GetCurrentPage()](#GetCurrentPage)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
