<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Shirt -->

Shirt | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Shirt.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [CharacterAppearance](/docs/en-us/reference/engine/classes/CharacterAppearance)
8. /
9. [Clothing](/docs/en-us/reference/engine/classes/Clothing)
10. /
11. [Shirt](/docs/en-us/reference/engine/classes/Shirt)

English

Feedback

Engine Class

Shirt

---

## Summary

Properties

|

[ShirtTemplate](#ShirtTemplate) : ContentId

 |
| --- | --- |
|

[ShirtTemplateContent](#ShirtTemplateContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |

Inherited Members

1  inherited from [Clothing](/docs/en-us/reference/engine/classes/Clothing)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Change Shirt / Pants

```

local Players = game:GetService("Players")

local function replaceClothes(player)

	local character = player.Character

	if character then

		-- look for shirts / pants

		local shirt = character:FindFirstChildOfClass("Shirt")

		local pants = character:FindFirstChildOfClass("Pants")

		-- create shirts / pants if they don't exist

		if not shirt then

			shirt = Instance.new("Shirt")

			shirt.Parent = character

		end

		if not pants then

			pants = Instance.new("Pants")

			pants.Parent = character

		end

		-- reset shirt / pants content ids

		shirt.ShirtTemplate = "http://www.roblox.com/asset/?id=83326831"

		pants.PantsTemplate = "http://www.roblox.com/asset/?id=10045638"

	end

end

for _index, player in ipairs(Players:GetPlayers()) do

	replaceClothes(player)

end

```

---

API Reference

Properties

ShirtTemplate

Read Parallel

Capabilities: AvatarAppearance

Shirt.ShirtTemplate : ContentId

Code Samples

Change Shirt / Pants

```

local Players = game:GetService("Players")

local function replaceClothes(player)

	local character = player.Character

	if character then

		-- look for shirts / pants

		local shirt = character:FindFirstChildOfClass("Shirt")

		local pants = character:FindFirstChildOfClass("Pants")

		-- create shirts / pants if they don't exist

		if not shirt then

			shirt = Instance.new("Shirt")

			shirt.Parent = character

		end

		if not pants then

			pants = Instance.new("Pants")

			pants.Parent = character

		end

		-- reset shirt / pants content ids

		shirt.ShirtTemplate = "http://www.roblox.com/asset/?id=83326831"

		pants.PantsTemplate = "http://www.roblox.com/asset/?id=10045638"

	end

end

for _index, player in ipairs(Players:GetPlayers()) do

	replaceClothes(player)

end

```

Provide feedback

---

ShirtTemplateContent

Read Parallel

Capabilities: AvatarAppearance

Shirt.ShirtTemplateContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

Jump to

▼

Shirt

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[ShirtTemplate](#ShirtTemplate)

[ShirtTemplateContent](#ShirtTemplateContent)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
