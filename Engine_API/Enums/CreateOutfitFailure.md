<!-- Source: https://create.roblox.com/docs/reference/engine/enums/CreateOutfitFailure -->

CreateOutfitFailure | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/enums/CreateOutfitFailure.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Enums](/docs/reference/engine/enums)
2. /
3. [CreateOutfitFailure](/docs/reference/engine/enums/CreateOutfitFailure)

English

Feedback

Engine Enum

CreateOutfitFailure

---

## Summary

Items

| Name | | Value | | Summary |
| --- | --- |
| InvalidName | | 1 | |  |
| OutfitLimitReached | | 2 | |  |
| Other | | 3 | |  |

---

## Usage

#### Code Samples

Handling Outfit Creation Results

```

local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService.PromptCreateOutfitCompleted:Connect(function(result, failureType)

	if result == Enum.AvatarPromptResult.Success then

		-- Outfit was created

	elseif result == Enum.AvatarPromptResult.PermissionDenied then

		-- User declined the prompt; ignore failureType

	else -- Enum.AvatarPromptResult.Failed

		if failureType == Enum.CreateOutfitFailure.OutfitLimitReached then

			-- Tell the user they hit the outfit cap

		elseif failureType == Enum.CreateOutfitFailure.InvalidName then

			-- Tell the user to pick a different name

		else -- Enum.CreateOutfitFailure.Other

			-- Generic failure; retry or show a generic error

		end

	end

end)

```

Jump to

▼

CreateOutfitFailure

[Summary](#summary)

[Usage](#usage)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
