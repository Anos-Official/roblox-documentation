<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ShirtGraphic -->

ShirtGraphic | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ShirtGraphic.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [CharacterAppearance](/docs/en-us/reference/engine/classes/CharacterAppearance)
8. /
9. [ShirtGraphic](/docs/en-us/reference/engine/classes/ShirtGraphic)

English

Feedback

Engine Class

ShirtGraphic

---

## Summary

Properties

|

[Color3](#Color3) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
| --- | --- |
|

[Graphic](#Graphic) : ContentId

 |
|

[TextureContent](#TextureContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Color3

Read Parallel

Capabilities: AvatarAppearance

ShirtGraphic.Color3 :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

Graphic

Read Parallel

Capabilities: AvatarAppearance

ShirtGraphic.Graphic : ContentId

Code Samples

Graphic

```

local InsertService = game:GetService("InsertService")

local Workspace = game:GetService("Workspace")

local webURL = "https://www.roblox.com/catalog/2591161/Sword-Fight-on-the-Heights-Ring-of-Fire-T-Shirt"

local assetId = tonumber(string.match(webURL, "%d+") or 0)  -- Extract the number

local success, model = pcall(function()

	return InsertService:LoadAsset(assetId)

end)

if success then

	model.Parent = Workspace

end

```

Provide feedback

---

TextureContent

Read Parallel

Capabilities: AvatarAppearance

ShirtGraphic.TextureContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

Jump to

▼

ShirtGraphic

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Color3](#Color3)

[Graphic](#Graphic)

[TextureContent](#TextureContent)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
