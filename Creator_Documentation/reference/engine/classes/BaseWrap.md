<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/BaseWrap -->

BaseWrap | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/BaseWrap.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [BaseWrap](/docs/en-us/reference/engine/classes/BaseWrap)

English

Feedback

Engine Class

BaseWrap

Not Creatable

---

## Summary

Properties

|

[CageMeshContent](#CageMeshContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
| --- | --- |
|

[CageMeshId](#CageMeshId) : ContentId

 |
|

[CageOrigin](#CageOrigin) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[CageOriginWorld](#CageOriginWorld) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[HSRAssetId](#HSRAssetId) : ContentId

 |
|

[HSRContent](#HSRContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

[ImportOrigin](#ImportOrigin) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[ImportOriginWorld](#ImportOriginWorld) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer) , [WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer) , [WrapTarget](/docs/en-us/reference/engine/classes/WrapTarget)

---

API Reference

Properties

CageMeshContent

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.CageMeshContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

CageMeshId

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.CageMeshId : ContentId

Provide feedback

---

CageOrigin

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.CageOrigin :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

CageOriginWorld

Read Only

Not Replicated

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.CageOriginWorld :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

HSRAssetId

Roblox Script Security

Roblox Security

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.HSRAssetId : ContentId

Provide feedback

---

HSRContent

Roblox Script Security

Roblox Security

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.HSRContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

ImportOrigin

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.ImportOrigin :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Code Samples

Import Origin

```

local function alignWraps()

	local selectionService = game:GetService("Selection")

	local selectedObjects = selectionService:Get()

	local alignObjects = {}

	for _, obj in selectedObjects do

		if obj:IsA("BaseWrap") then

			--print("Wrap: " .. obj.Name)

			table.insert(alignObjects, obj)

		else

			print("Ignore: " .. obj.Name)

		end

	end

	if #alignObjects < 2 then

		warn("You need to select at least two wraps")

		return

	end

	local anchorWrap = alignObjects[1]

	local worldA_from_Wrap = anchorWrap.ImportOriginWorld

	print("Anchor: " .. anchorWrap.Name)

	for i = 2, #alignObjects do

		local wrapToAlign = alignObjects[i]

		print("Align: " .. wrapToAlign.Name)

		local wrap_from_WorldB = wrapToAlign.ImportOriginWorld:Inverse()

		local worldA_from_WorldB = worldA_from_Wrap * wrap_from_WorldB

		local worldB = wrapToAlign.Parent.CFrame

		-- Note: adjust CFrame of the parent part

		wrapToAlign.Parent.CFrame = (worldB_from_WorldB * worldB)

	end

end

```

Provide feedback

---

ImportOriginWorld

Read Only

Not Replicated

Read Parallel

Capabilities: AvatarAppearance

BaseWrap.ImportOriginWorld :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

Jump to

▼

BaseWrap

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[CageMeshContent](#CageMeshContent)

[CageMeshId](#CageMeshId)

[CageOrigin](#CageOrigin)

[CageOriginWorld](#CageOriginWorld)

[HSRAssetId](#HSRAssetId)

[HSRContent](#HSRContent)

[ImportOrigin](#ImportOrigin)

[ImportOriginWorld](#ImportOriginWorld)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
