<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/InsertService -->

InsertService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [InsertService](/docs/nl-nl/reference/engine/classes/InsertService)

Nederlands

Feedback

Engine-klasse

InsertService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/InsertService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AllowInsertFreeModels](#AllowInsertFreeModels) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
| --- | --- |

Methoden

|

[ApproveAssetId](#ApproveAssetId) (assetId :  [number](/docs/nl-nl/luau/numbers) ) : ()

Verouderd

 |
|

[ApproveAssetVersionId](#ApproveAssetVersionId) (assetVersionId :  [number](/docs/nl-nl/luau/numbers) ) : ()

Verouderd

 |
|

[CreateMeshPartAsync](#CreateMeshPartAsync) (meshId :  ContentId , collisionFidelity :  [Enum.CollisionFidelity](/docs/nl-nl/reference/engine/enums/CollisionFidelity) , renderFidelity :  [Enum.RenderFidelity](/docs/nl-nl/reference/engine/enums/RenderFidelity) ) :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

 |
|

[GetBaseCategories](#GetBaseCategories) () :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetBaseSets](#GetBaseSets) () :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetCollection](#GetCollection) (categoryId :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetFreeDecals](#GetFreeDecals) (searchText :  [string](/docs/nl-nl/luau/strings) , pageNum :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetFreeDecalsAsync](#GetFreeDecalsAsync) (searchText :  [string](/docs/nl-nl/luau/strings) , pageNum :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetFreeModels](#GetFreeModels) (searchText :  [string](/docs/nl-nl/luau/strings) , pageNum :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetFreeModelsAsync](#GetFreeModelsAsync) (searchText :  [string](/docs/nl-nl/luau/strings) , pageNum :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetLatestAssetVersionAsync](#GetLatestAssetVersionAsync) (assetId :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetUserCategories](#GetUserCategories) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetUserSets](#GetUserSets) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[Insert](#Insert) (instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Verouderd

 |
|

[LoadAsset](#LoadAsset) (assetId :  [number](/docs/nl-nl/luau/numbers) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[loadAsset](#loadAsset) (assetId :  [number](/docs/nl-nl/luau/numbers) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
|

[LoadAssetVersion](#LoadAssetVersion) (assetVersionId :  [number](/docs/nl-nl/luau/numbers) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

AllowInsertFreeModels

Verouderd

Details weergeven

---

Methoden

ApproveAssetId

Verouderd

Details weergeven

---

ApproveAssetVersionId

Verouderd

Details weergeven

---

CreateMeshPartAsync

Opbrengst

Mogelijkheden: Basic

InsertService:CreateMeshPartAsync (

meshId : ContentId , collisionFidelity :[Enum.CollisionFidelity](/docs/nl-nl/reference/engine/enums/CollisionFidelity) , renderFidelity :[Enum.RenderFidelity](/docs/nl-nl/reference/engine/enums/RenderFidelity)

) :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

Parameters

|

meshId : ContentId

 |
|

collisionFidelity :[Enum.CollisionFidelity](/docs/nl-nl/reference/engine/enums/CollisionFidelity)

 |
|

renderFidelity :[Enum.RenderFidelity](/docs/nl-nl/reference/engine/enums/RenderFidelity)

 |

Teruggaves

[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

Feedback geven

---

GetBaseCategories

Verouderd

Details weergeven

---

GetBaseSets

Verouderd

Details weergeven

---

GetCollection

Verouderd

Details weergeven

---

GetFreeDecals

Verouderd

Details weergeven

---

GetFreeDecalsAsync

Opbrengst

Mogelijkheden: AssetRead

InsertService:GetFreeDecalsAsync (

searchText :[string](/docs/nl-nl/luau/strings) , pageNum :[number](/docs/nl-nl/luau/numbers)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

searchText :[string](/docs/nl-nl/luau/strings)

 |
|

pageNum :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

InsertService:GetFreeDecalsAsync

```

local InsertService = game:GetService("InsertService")

local page = unpack(InsertService:GetFreeDecalsAsync("Katten", 0)) -- Zoek naar "Katten" op Pagina 1.

for i = 1, page.TotalCount do

	local item = page.Results[i]

	print("Item #" .. i)

	for key, value in pairs(item) do

		print(" " .. key .. ": " .. value)

	end

end

```

Feedback geven

---

GetFreeModels

Verouderd

Details weergeven

---

GetFreeModelsAsync

Opbrengst

Mogelijkheden: AssetRead

InsertService:GetFreeModelsAsync (

searchText :[string](/docs/nl-nl/luau/strings) , pageNum :[number](/docs/nl-nl/luau/numbers)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

searchText :[string](/docs/nl-nl/luau/strings)

 |
|

pageNum :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

InsertService:GetFreeModelsAsync

```

local InsertService = game:GetService("InsertService")

local page = unpack(InsertService:GetFreeModelsAsync("Katten", 0)) -- Zoek naar "Katten" op Pagina 1.

for i = 1, page.TotalCount do

	local item = page.Results[i]

	print("Item #" .. i)

	for key, value in pairs(item) do

		print(" " .. key .. ": " .. value)

	end

end

```

Feedback geven

---

GetLatestAssetVersionAsync

Opbrengst

Mogelijkheden: AssetRead

InsertService:GetLatestAssetVersionAsync (assetId :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

assetId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetUserCategories

Verouderd

Details weergeven

---

GetUserSets

Verouderd

Details weergeven

---

Insert

Verouderd

Details weergeven

---

LoadAsset

Opbrengst

Mogelijkheden: LoadOwnedAsset

InsertService:LoadAsset (assetId :[number](/docs/nl-nl/luau/numbers) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

assetId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

InsertService:LoadAsset

```

local InsertService = game:GetService("InsertService")

local ASSET_ID = 82353

local asset = InsertService:LoadAsset(ASSET_ID)

asset.Parent = workspace

```

Feedback geven

---

loadAsset

Verouderd

Details weergeven

---

LoadAssetVersion

Opbrengst

Mogelijkheden: LoadOwnedAsset

InsertService:LoadAssetVersion (assetVersionId :[number](/docs/nl-nl/luau/numbers) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

assetVersionId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

InsertService:LoadAssetVersion

```

local InsertService = game:GetService("InsertService")

local ASSET_VERSION_ID = 296050499

local asset = InsertService:LoadAssetVersion(ASSET_VERSION_ID)

asset.Parent = game.Workspace

```

Feedback geven

---

Ga naar

▼

InsertService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[AllowInsertFreeModels](#AllowInsertFreeModels)

[Methoden](#methods)

[ApproveAssetId()](#ApproveAssetId)

[ApproveAssetVersionId()](#ApproveAssetVersionId)

[CreateMeshPartAsync()](#CreateMeshPartAsync)

[GetBaseCategories()](#GetBaseCategories)

[GetBaseSets()](#GetBaseSets)

[GetCollection()](#GetCollection)

[GetFreeDecals()](#GetFreeDecals)

[GetFreeDecalsAsync()](#GetFreeDecalsAsync)

[GetFreeModels()](#GetFreeModels)

[GetFreeModelsAsync()](#GetFreeModelsAsync)

[GetLatestAssetVersionAsync()](#GetLatestAssetVersionAsync)

[GetUserCategories()](#GetUserCategories)

[GetUserSets()](#GetUserSets)

[Insert()](#Insert)

[LoadAsset()](#LoadAsset)

[loadAsset()](#loadAsset)

[LoadAssetVersion()](#LoadAssetVersion)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
