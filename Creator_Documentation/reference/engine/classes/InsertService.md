<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/InsertService -->

InsertService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/InsertService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [InsertService](/docs/en-us/reference/engine/classes/InsertService)

English

Feedback

Engine Class

InsertService

Not Creatable

Service

---

## Summary

Properties

|

[AllowInsertFreeModels](#AllowInsertFreeModels) :[boolean](/docs/en-us/luau/booleans)

Deprecated

 |
| --- | --- |

Methods

|

[ApproveAssetId](#ApproveAssetId) (assetId :  [number](/docs/en-us/luau/numbers) ) : ()

Deprecated

 |
|

[ApproveAssetVersionId](#ApproveAssetVersionId) (assetVersionId :  [number](/docs/en-us/luau/numbers) ) : ()

Deprecated

 |
|

[CreateMeshPartAsync](#CreateMeshPartAsync) (meshId :  ContentId , collisionFidelity :  [Enum.CollisionFidelity](/docs/en-us/reference/engine/enums/CollisionFidelity) , renderFidelity :  [Enum.RenderFidelity](/docs/en-us/reference/engine/enums/RenderFidelity) ) :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

 |
|

[GetBaseCategories](#GetBaseCategories) () :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[GetBaseSets](#GetBaseSets) () :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[GetCollection](#GetCollection) (categoryId :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[GetFreeDecals](#GetFreeDecals) (searchText :  [string](/docs/en-us/luau/strings) , pageNum :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[GetFreeDecalsAsync](#GetFreeDecalsAsync) (searchText :  [string](/docs/en-us/luau/strings) , pageNum :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetFreeModels](#GetFreeModels) (searchText :  [string](/docs/en-us/luau/strings) , pageNum :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[GetFreeModelsAsync](#GetFreeModelsAsync) (searchText :  [string](/docs/en-us/luau/strings) , pageNum :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetLatestAssetVersionAsync](#GetLatestAssetVersionAsync) (assetId :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[GetUserCategories](#GetUserCategories) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[GetUserSets](#GetUserSets) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[{any}](/docs/en-us/luau/tables#arrays)

Deprecated

 |
|

[Insert](#Insert) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Deprecated

 |
|

[LoadAsset](#LoadAsset) (assetId :  [number](/docs/en-us/luau/numbers) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[loadAsset](#loadAsset) (assetId :  [number](/docs/en-us/luau/numbers) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Deprecated

 |
|

[LoadAssetVersion](#LoadAssetVersion) (assetVersionId :  [number](/docs/en-us/luau/numbers) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

AllowInsertFreeModels

Deprecated

Show details

---

Methods

ApproveAssetId

Deprecated

Show details

---

ApproveAssetVersionId

Deprecated

Show details

---

CreateMeshPartAsync

Yields

Capabilities: Basic

InsertService:CreateMeshPartAsync (

meshId : ContentId , collisionFidelity :[Enum.CollisionFidelity](/docs/en-us/reference/engine/enums/CollisionFidelity) , renderFidelity :[Enum.RenderFidelity](/docs/en-us/reference/engine/enums/RenderFidelity)

) :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

Parameters

|

meshId : ContentId

 |
|

collisionFidelity :[Enum.CollisionFidelity](/docs/en-us/reference/engine/enums/CollisionFidelity)

 |
|

renderFidelity :[Enum.RenderFidelity](/docs/en-us/reference/engine/enums/RenderFidelity)

 |

Returns

[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

Provide feedback

---

GetBaseCategories

Deprecated

Show details

---

GetBaseSets

Deprecated

Show details

---

GetCollection

Deprecated

Show details

---

GetFreeDecals

Deprecated

Show details

---

GetFreeDecalsAsync

Yields

Capabilities: AssetRead

InsertService:GetFreeDecalsAsync (

searchText :[string](/docs/en-us/luau/strings) , pageNum :[number](/docs/en-us/luau/numbers)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

searchText :[string](/docs/en-us/luau/strings)

 |
|

pageNum :[number](/docs/en-us/luau/numbers)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

InsertService:GetFreeDecalsAsync

```

local InsertService = game:GetService("InsertService")

local page = unpack(InsertService:GetFreeDecalsAsync("Cats", 0)) -- Search for "Cats" on Page 1.

for i = 1, page.TotalCount do

	local item = page.Results[i]

	print("Item #" .. i)

	for key, value in pairs(item) do

		print(" " .. key .. ": " .. value)

	end

end

```

Provide feedback

---

GetFreeModels

Deprecated

Show details

---

GetFreeModelsAsync

Yields

Capabilities: AssetRead

InsertService:GetFreeModelsAsync (

searchText :[string](/docs/en-us/luau/strings) , pageNum :[number](/docs/en-us/luau/numbers)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

searchText :[string](/docs/en-us/luau/strings)

 |
|

pageNum :[number](/docs/en-us/luau/numbers)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

InsertService:GetFreeModelsAsync

```

local InsertService = game:GetService("InsertService")

local page = unpack(InsertService:GetFreeModelsAsync("Cats", 0)) -- Search for "Cats" on Page 1.

for i = 1, page.TotalCount do

	local item = page.Results[i]

	print("Item #" .. i)

	for key, value in pairs(item) do

		print(" " .. key .. ": " .. value)

	end

end

```

Provide feedback

---

GetLatestAssetVersionAsync

Yields

Capabilities: AssetRead

InsertService:GetLatestAssetVersionAsync (assetId :[number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

assetId :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetUserCategories

Deprecated

Show details

---

GetUserSets

Deprecated

Show details

---

Insert

Deprecated

Show details

---

LoadAsset

Yields

Capabilities: LoadOwnedAsset

InsertService:LoadAsset (assetId :[number](/docs/en-us/luau/numbers) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Parameters

|

assetId :[number](/docs/en-us/luau/numbers)

 |

Returns

[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Code Samples

InsertService:LoadAsset

```

local InsertService = game:GetService("InsertService")

local ASSET_ID = 82353

local asset = InsertService:LoadAsset(ASSET_ID)

asset.Parent = workspace

```

Provide feedback

---

loadAsset

Deprecated

Show details

---

LoadAssetVersion

Yields

Capabilities: LoadOwnedAsset

InsertService:LoadAssetVersion (assetVersionId :[number](/docs/en-us/luau/numbers) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Parameters

|

assetVersionId :[number](/docs/en-us/luau/numbers)

 |

Returns

[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Code Samples

InsertService:LoadAssetVersion

```

local InsertService = game:GetService("InsertService")

local ASSET_VERSION_ID = 296050499

local asset = InsertService:LoadAssetVersion(ASSET_VERSION_ID)

asset.Parent = game.Workspace

```

Provide feedback

---

Jump to

▼

InsertService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[AllowInsertFreeModels](#AllowInsertFreeModels)

[Methods](#methods)

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

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
