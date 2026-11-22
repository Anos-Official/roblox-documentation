<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/BaseWrap -->

BaseWrap | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [BaseWrap](/docs/nl-nl/reference/engine/classes/BaseWrap)

Nederlands

Feedback

Engine-klasse

BaseWrap

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/BaseWrap)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[CageMeshContent](#CageMeshContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
| --- | --- |
|

[CageMeshId](#CageMeshId) : ContentId

 |
|

[CageOrigin](#CageOrigin) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[CageOriginWorld](#CageOriginWorld) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[HSRAssetId](#HSRAssetId) : ContentId

 |
|

[HSRContent](#HSRContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[ImportOrigin](#ImportOrigin) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[ImportOriginWorld](#ImportOriginWorld) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer) , [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) , [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)

---

API-referentie

Eigenschappen

CageMeshContent

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.CageMeshContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

CageMeshId

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.CageMeshId : ContentId

Feedback geven

---

CageOrigin

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.CageOrigin :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

CageOriginWorld

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.CageOriginWorld :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

HSRAssetId

Roblox-scriptbeveiliging

Roblox Security

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.HSRAssetId : ContentId

Feedback geven

---

HSRContent

Roblox-scriptbeveiliging

Roblox Security

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.HSRContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

ImportOrigin

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.ImportOrigin :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Codevoorbeelden

Import Oorsprong

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

			print("Negeer: " .. obj.Name)

		end

	end

	if #alignObjects < 2 then

		warn("Je moet minstens twee wraps selecteren")

		return

	end

	local anchorWrap = alignObjects[1]

	local worldA_from_Wrap = anchorWrap.ImportOriginWorld

	print("Anker: " .. anchorWrap.Name)

	for i = 2, #alignObjects do

		local wrapToAlign = alignObjects[i]

		print("Align: " .. wrapToAlign.Name)

		local wrap_from_WorldB = wrapToAlign.ImportOriginWorld:Inverse()

		local worldA_from_WorldB = worldA_from_Wrap * wrap_from_WorldB

		local worldB = wrapToAlign.Parent.CFrame

		-- Opmerking: pas CFrame van het bovenliggende onderdeel aan

		wrapToAlign.Parent.CFrame = (worldB_from_WorldB * worldB)

	end

end

```

Feedback geven

---

ImportOriginWorld

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: AvatarAppearance

BaseWrap.ImportOriginWorld :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Ga naar

▼

BaseWrap

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[CageMeshContent](#CageMeshContent)

[CageMeshId](#CageMeshId)

[CageOrigin](#CageOrigin)

[CageOriginWorld](#CageOriginWorld)

[HSRAssetId](#HSRAssetId)

[HSRContent](#HSRContent)

[ImportOrigin](#ImportOrigin)

[ImportOriginWorld](#ImportOriginWorld)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
