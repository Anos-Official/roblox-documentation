<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/GetTextBoundsParams -->

GetTextBoundsParams | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/GetTextBoundsParams.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GetTextBoundsParams](/docs/en-us/reference/engine/classes/GetTextBoundsParams)

English

Feedback

Engine Class

GetTextBoundsParams

Not Replicated

---

## Summary

Properties

|

[Font](#Font) :[Font](/docs/en-us/reference/engine/datatypes/Font)

 |
| --- | --- |
|

[RichText](#RichText) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Size](#Size) :[number](/docs/en-us/luau/numbers)

 |
|

[Text](#Text) :[string](/docs/en-us/luau/strings)

 |
|

[Width](#Width) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Measuring Text Size

```

local TextService = game:GetService("TextService")

-- Declare parameters

local params = Instance.new("GetTextBoundsParams")

params.Text = "Hello world!"

params.Font = Font.new("rbxasset://fonts/families/GrenzeGotisch.json", Enum.FontWeight.Thin)

params.Size = 20

params.Width = 200

local success, bounds = pcall(function()

	return TextService:GetTextBoundsAsync(params)

end)

if success then

	print(bounds)

end

```

---

API Reference

Properties

Font

Read Parallel

Capabilities: UI

GetTextBoundsParams.Font :[Font](/docs/en-us/reference/engine/datatypes/Font)

Provide feedback

---

RichText

Read Parallel

Capabilities: UI

GetTextBoundsParams.RichText :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Size

Read Parallel

Capabilities: UI

GetTextBoundsParams.Size :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Text

Read Parallel

Capabilities: UI

GetTextBoundsParams.Text :[string](/docs/en-us/luau/strings)

Provide feedback

---

Width

Read Parallel

Capabilities: UI

GetTextBoundsParams.Width :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

GetTextBoundsParams

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Font](#Font)

[RichText](#RichText)

[Size](#Size)

[Text](#Text)

[Width](#Width)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
