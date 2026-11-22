<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ContentProvider -->

ContentProvider | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ContentProvider.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ContentProvider](/docs/en-us/reference/engine/classes/ContentProvider)

English

Feedback

Engine Class

ContentProvider

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[BaseUrl](#BaseUrl) :[string](/docs/en-us/luau/strings)

 |
| --- | --- |
|

[RequestQueueSize](#RequestQueueSize) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[GetAssetFetchStatus](#GetAssetFetchStatus) (contentId :  ContentId ) :[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

 |
|

[GetAssetFetchStatusChangedSignal](#GetAssetFetchStatusChangedSignal) (contentId :  ContentId ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[ListEncryptedAssets](#ListEncryptedAssets) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[Preload](#Preload) (contentId :  ContentId ) : ()

Deprecated

 |
|

[PreloadAsync](#PreloadAsync) (contentIdList :  [{any}](/docs/en-us/luau/tables#arrays) , callbackFunction :  [function](/docs/en-us/luau/functions) ) : ()

 |
|

[RegisterDefaultEncryptionKey](#RegisterDefaultEncryptionKey) (encryptionKey :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[RegisterDefaultSessionKey](#RegisterDefaultSessionKey) (sessionKey :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[RegisterEncryptedAsset](#RegisterEncryptedAsset) (assetId :  ContentId , encryptionKey :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[RegisterSessionEncryptedAsset](#RegisterSessionEncryptedAsset) (contentId :  ContentId , sessionKey :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[UnregisterDefaultEncryptionKey](#UnregisterDefaultEncryptionKey) () : ()

 |
|

[UnregisterEncryptedAsset](#UnregisterEncryptedAsset) (assetId :  ContentId ) : ()

 |

Events

|

[AssetFetchFailed](#AssetFetchFailed) (assetId :  ContentId ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

ContentProvider

```

local ContentProvider = game:GetService("ContentProvider")

local LOGO_ID = "rbxassetid://658743164"

local PAGE_TURN_ID = "rbxassetid://12222076"

local decal = Instance.new("Decal")

decal.ColorMapContent =  Content.fromUri(LOGO_ID)

local sound = Instance.new("Sound")

sound.SoundId = PAGE_TURN_ID

local assets = { decal, sound }

ContentProvider:PreloadAsync(assets)

print("All assets loaded.")

```

---

API Reference

Properties

BaseUrl

Read Only

Not Replicated

Read Parallel

Capabilities: AssetManagement

ContentProvider.BaseUrl :[string](/docs/en-us/luau/strings)

Provide feedback

---

RequestQueueSize

Read Only

Not Replicated

Read Parallel

Capabilities: AssetManagement

ContentProvider.RequestQueueSize :[number](/docs/en-us/luau/numbers)

Code Samples

ContentProvider Loading Bar

```

local ContentProvider = game:GetService("ContentProvider")

local Players = game:GetService("Players")

local localPlayer = Players.LocalPlayer

local playerGui = localPlayer:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = playerGui

-- create a basic loading bar

local frame = Instance.new("Frame")

frame.Size = UDim2.new(0.5, 0, 0.1, 0)

frame.Position = UDim2.new(0.5, 0, 0.5, 0)

frame.AnchorPoint = Vector2.new(0.5, 0.5)

frame.Parent = screenGui

local bar = Instance.new("Frame")

bar.Size = UDim2.new(0, 0, 1, 0)

bar.Position = UDim2.new(0, 0, 0, 0)

bar.BackgroundColor3 = Color3.new(0, 0, 1)

bar.Parent = frame

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://9120386436"

local sound2 = Instance.new("Sound")

sound2.SoundId = "rbxassetid://9120385974"

local assets = {

	sound,

	sound2,

}

task.wait(3)

for i = 1, #assets do

	local asset = assets[i]

	ContentProvider:PreloadAsync({ asset }) -- 1 at a time, yields

	local progress = i / #assets

	bar.Size = UDim2.new(progress, 0, 1, 0)

end

print("loading done")

```

Provide feedback

---

Methods

GetAssetFetchStatus

Capabilities: AssetManagement

ContentProvider:GetAssetFetchStatus (contentId : ContentId ) :[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

Parameters

|

contentId : ContentId

 |

Returns

[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

Code Samples

Monitoring AssetFetchStatus

```

local ContentProvider = game:GetService("ContentProvider")

-- An example asset to load

local ASSET_ID = "rbxassetid://9120386436"

local exampleAsset = Instance.new("Sound")

exampleAsset.SoundId = ASSET_ID

-- Output the current AssetFetchStatus of the asset

local initialAssetFetchStatus = ContentProvider:GetAssetFetchStatus(ASSET_ID)

print("Initial AssetFetchStatus:", initialAssetFetchStatus)

-- Listen for updates

local assetFetchStatusChangedSignal = ContentProvider:GetAssetFetchStatusChangedSignal(ASSET_ID)

local function onAssetFetchStatusChanged(newAssetFetchStatus: Enum.AssetFetchStatus)

	print(`New AssetFetchStatus: {newAssetFetchStatus}`)

end

assetFetchStatusChangedSignal:Connect(onAssetFetchStatusChanged)

-- Trigger the asset to preload

local function onAssetRequestComplete(contentId: string, assetFetchStatus: Enum.AssetFetchStatus)

	print(`Preload status {contentId}: {assetFetchStatus.Name}`)

end

ContentProvider:PreloadAsync({ exampleAsset }, onAssetRequestComplete)

```

Provide feedback

---

GetAssetFetchStatusChangedSignal

Capabilities: AssetManagement

ContentProvider:GetAssetFetchStatusChangedSignal (contentId : ContentId ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

contentId : ContentId

 |

Returns

[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Monitoring AssetFetchStatus

```

local ContentProvider = game:GetService("ContentProvider")

-- An example asset to load

local ASSET_ID = "rbxassetid://9120386436"

local exampleAsset = Instance.new("Sound")

exampleAsset.SoundId = ASSET_ID

-- Output the current AssetFetchStatus of the asset

local initialAssetFetchStatus = ContentProvider:GetAssetFetchStatus(ASSET_ID)

print("Initial AssetFetchStatus:", initialAssetFetchStatus)

-- Listen for updates

local assetFetchStatusChangedSignal = ContentProvider:GetAssetFetchStatusChangedSignal(ASSET_ID)

local function onAssetFetchStatusChanged(newAssetFetchStatus: Enum.AssetFetchStatus)

	print(`New AssetFetchStatus: {newAssetFetchStatus}`)

end

assetFetchStatusChangedSignal:Connect(onAssetFetchStatusChanged)

-- Trigger the asset to preload

local function onAssetRequestComplete(contentId: string, assetFetchStatus: Enum.AssetFetchStatus)

	print(`Preload status {contentId}: {assetFetchStatus.Name}`)

end

ContentProvider:PreloadAsync({ exampleAsset }, onAssetRequestComplete)

```

Provide feedback

---

ListEncryptedAssets

Capabilities: AssetManagement

ContentProvider:ListEncryptedAssets () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

Preload

Deprecated

Show details

---

PreloadAsync

Yields

Capabilities: AssetManagement

ContentProvider:PreloadAsync (

contentIdList :[{any}](/docs/en-us/luau/tables#arrays) , callbackFunction :[function](/docs/en-us/luau/functions)

) : ()

Parameters

|

contentIdList :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

callbackFunction :[function](/docs/en-us/luau/functions)

Default Value: nil |

Returns

()

Code Samples

Preloading Assets

```

local ContentProvider = game:GetService("ContentProvider")

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://9120386436"

local decal = Instance.new("Decal")

decal.ColorMapContent = Content.fromUri("rbxassetid://5447528495")

local assets = {

	decal,

	sound,

}

-- This will be hit as each asset resolves

local callback = function(assetId, assetFetchStatus)

	print("PreloadAsync() resolved asset ID:", assetId)

	print("PreloadAsync() final AssetFetchStatus:", assetFetchStatus)

end

-- Preload the content and time it

local startTime = os.clock()

ContentProvider:PreloadAsync(assets, callback)

local deltaTime = os.clock() - startTime

print(("Preloading complete, took %.2f seconds"):format(deltaTime))

```

Provide feedback

---

RegisterDefaultEncryptionKey

Capabilities: AssetManagement

ContentProvider:RegisterDefaultEncryptionKey (encryptionKey :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

encryptionKey :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

RegisterDefaultSessionKey

Capabilities: AssetManagement

ContentProvider:RegisterDefaultSessionKey (sessionKey :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

sessionKey :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

RegisterEncryptedAsset

Capabilities: AssetManagement

ContentProvider:RegisterEncryptedAsset (

assetId : ContentId , encryptionKey :[string](/docs/en-us/luau/strings)

) : ()

Parameters

|

assetId : ContentId

 |
|

encryptionKey :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

RegisterSessionEncryptedAsset

Capabilities: AssetManagement

ContentProvider:RegisterSessionEncryptedAsset (

contentId : ContentId , sessionKey :[string](/docs/en-us/luau/strings)

) : ()

Parameters

|

contentId : ContentId

 |
|

sessionKey :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

UnregisterDefaultEncryptionKey

Capabilities: AssetManagement

ContentProvider:UnregisterDefaultEncryptionKey () : ()

Returns

()

Provide feedback

---

UnregisterEncryptedAsset

Capabilities: AssetManagement

ContentProvider:UnregisterEncryptedAsset (assetId : ContentId ) : ()

Parameters

|

assetId : ContentId

 |

Returns

()

Provide feedback

---

Events

AssetFetchFailed

Capabilities: AssetManagement

ContentProvider.AssetFetchFailed (assetId : ContentId ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

assetId : ContentId

 |

Provide feedback

---

Jump to

▼

ContentProvider

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[BaseUrl](#BaseUrl)

[RequestQueueSize](#RequestQueueSize)

[Methods](#methods)

[GetAssetFetchStatus()](#GetAssetFetchStatus)

[GetAssetFetchStatusChangedSignal()](#GetAssetFetchStatusChangedSignal)

[ListEncryptedAssets()](#ListEncryptedAssets)

[Preload()](#Preload)

[PreloadAsync()](#PreloadAsync)

[RegisterDefaultEncryptionKey()](#RegisterDefaultEncryptionKey)

[RegisterDefaultSessionKey()](#RegisterDefaultSessionKey)

[RegisterEncryptedAsset()](#RegisterEncryptedAsset)

[RegisterSessionEncryptedAsset()](#RegisterSessionEncryptedAsset)

[UnregisterDefaultEncryptionKey()](#UnregisterDefaultEncryptionKey)

[UnregisterEncryptedAsset()](#UnregisterEncryptedAsset)

[Events](#events)

[AssetFetchFailed](#AssetFetchFailed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
