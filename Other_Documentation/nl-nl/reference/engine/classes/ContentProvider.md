<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ContentProvider -->

ContentProvider | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ContentProvider](/docs/nl-nl/reference/engine/classes/ContentProvider)

Nederlands

Feedback

Engine-klasse

ContentProvider

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ContentProvider)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[BaseUrl](#BaseUrl) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[RequestQueueSize](#RequestQueueSize) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GetAssetFetchStatus](#GetAssetFetchStatus) (contentId :  ContentId ) :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

 |
|

[GetAssetFetchStatusChangedSignal](#GetAssetFetchStatusChangedSignal) (contentId :  ContentId ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[ListEncryptedAssets](#ListEncryptedAssets) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[Preload](#Preload) (contentId :  ContentId ) : ()

Verouderd

 |
|

[PreloadAsync](#PreloadAsync) (contentIdList :  [{any}](/docs/nl-nl/luau/tables#arrays) , callbackFunction :  [function](/docs/nl-nl/luau/functions) ) : ()

 |
|

[RegisterDefaultEncryptionKey](#RegisterDefaultEncryptionKey) (encryptionKey :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[RegisterDefaultSessionKey](#RegisterDefaultSessionKey) (sessionKey :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[RegisterEncryptedAsset](#RegisterEncryptedAsset) (assetId :  ContentId , encryptionKey :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[RegisterSessionEncryptedAsset](#RegisterSessionEncryptedAsset) (contentId :  ContentId , sessionKey :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[UnregisterDefaultEncryptionKey](#UnregisterDefaultEncryptionKey) () : ()

 |
|

[UnregisterEncryptedAsset](#UnregisterEncryptedAsset) (assetId :  ContentId ) : ()

 |

Evenementen

|

[AssetFetchFailed](#AssetFetchFailed) (assetId :  ContentId ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

InhoudProvider

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

print("Alle assets zijn geladen.")

```

---

API-referentie

Eigenschappen

BaseUrl

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: AssetManagement

ContentProvider.BaseUrl :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

RequestQueueSize

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: AssetManagement

ContentProvider.RequestQueueSize :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

InhoudProvider Laadbalk

```

local ContentProvider = game:GetService("ContentProvider")

local Players = game:GetService("Players")

local localPlayer = Players.LocalPlayer

local playerGui = localPlayer:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = playerGui

-- maak een basis laadbalk

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

	ContentProvider:PreloadAsync({ asset }) -- 1 tegelijk, yield

	local progress = i / #assets

	bar.Size = UDim2.new(progress, 0, 1, 0)

end

print("laden voltooid")

```

Feedback geven

---

Methoden

GetAssetFetchStatus

Mogelijkheden: AssetManagement

ContentProvider:GetAssetFetchStatus (contentId : ContentId ) :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

Parameters

|

contentId : ContentId

 |

Teruggaves

[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

Codevoorbeelden

Monitoring AssetFetchStatus

```

local ContentProvider = game:GetService("ContentProvider")

-- Een voorbeeld asset om te laden

local ASSET_ID = "rbxassetid://9120386436"

local exampleAsset = Instance.new("Sound")

exampleAsset.SoundId = ASSET_ID

-- Geef de huidige AssetFetchStatus van de asset weer

local initialAssetFetchStatus = ContentProvider:GetAssetFetchStatus(ASSET_ID)

print("Initiële AssetFetchStatus:", initialAssetFetchStatus)

-- Luister naar updates

local assetFetchStatusChangedSignal = ContentProvider:GetAssetFetchStatusChangedSignal(ASSET_ID)

local function onAssetFetchStatusChanged(newAssetFetchStatus: Enum.AssetFetchStatus)

	print(`Nieuwe AssetFetchStatus: {newAssetFetchStatus}`)

end

assetFetchStatusChangedSignal:Connect(onAssetFetchStatusChanged)

-- Trigger de asset om voor te laden

local function onAssetRequestComplete(contentId: string, assetFetchStatus: Enum.AssetFetchStatus)

	print(`Voorlaadstatus {contentId}: {assetFetchStatus.Name}`)

end

ContentProvider:PreloadAsync({ exampleAsset }, onAssetRequestComplete)

```

Feedback geven

---

GetAssetFetchStatusChangedSignal

Mogelijkheden: AssetManagement

ContentProvider:GetAssetFetchStatusChangedSignal (contentId : ContentId ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

contentId : ContentId

 |

Teruggaves

[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

Monitoring AssetFetchStatus

```

local ContentProvider = game:GetService("ContentProvider")

-- Een voorbeeld asset om te laden

local ASSET_ID = "rbxassetid://9120386436"

local exampleAsset = Instance.new("Sound")

exampleAsset.SoundId = ASSET_ID

-- Geef de huidige AssetFetchStatus van de asset weer

local initialAssetFetchStatus = ContentProvider:GetAssetFetchStatus(ASSET_ID)

print("Initiële AssetFetchStatus:", initialAssetFetchStatus)

-- Luister naar updates

local assetFetchStatusChangedSignal = ContentProvider:GetAssetFetchStatusChangedSignal(ASSET_ID)

local function onAssetFetchStatusChanged(newAssetFetchStatus: Enum.AssetFetchStatus)

	print(`Nieuwe AssetFetchStatus: {newAssetFetchStatus}`)

end

assetFetchStatusChangedSignal:Connect(onAssetFetchStatusChanged)

-- Trigger de asset om voor te laden

local function onAssetRequestComplete(contentId: string, assetFetchStatus: Enum.AssetFetchStatus)

	print(`Voorlaadstatus {contentId}: {assetFetchStatus.Name}`)

end

ContentProvider:PreloadAsync({ exampleAsset }, onAssetRequestComplete)

```

Feedback geven

---

ListEncryptedAssets

Mogelijkheden: AssetManagement

ContentProvider:ListEncryptedAssets () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Preload

Verouderd

Details weergeven

---

PreloadAsync

Opbrengst

Mogelijkheden: AssetManagement

ContentProvider:PreloadAsync (

contentIdList :[{any}](/docs/nl-nl/luau/tables#arrays) , callbackFunction :[function](/docs/nl-nl/luau/functions)

) : ()

Parameters

|

contentIdList :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

callbackFunction :[function](/docs/nl-nl/luau/functions)

Standaardwaarde: nil |

Teruggaves

()

Codevoorbeelden

Vooraf laden van middelen

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

-- Dit zal worden aangeroepen wanneer elk middel is opgelost

local callback = function(assetId, assetFetchStatus)

	print("PreloadAsync() heeft middel ID opgelost:", assetId)

	print("PreloadAsync() eindstatus van AssetFetchStatus:", assetFetchStatus)

end

-- Laad de inhoud vooraf en meet de tijd

local startTime = os.clock()

ContentProvider:PreloadAsync(assets, callback)

local deltaTime = os.clock() - startTime

print(("Vooraf laden voltooid, duurde %.2f seconden"):format(deltaTime))

```

Feedback geven

---

RegisterDefaultEncryptionKey

Mogelijkheden: AssetManagement

ContentProvider:RegisterDefaultEncryptionKey (encryptionKey :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

encryptionKey :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

RegisterDefaultSessionKey

Mogelijkheden: AssetManagement

ContentProvider:RegisterDefaultSessionKey (sessionKey :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

sessionKey :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

RegisterEncryptedAsset

Mogelijkheden: AssetManagement

ContentProvider:RegisterEncryptedAsset (

assetId : ContentId , encryptionKey :[string](/docs/nl-nl/luau/strings)

) : ()

Parameters

|

assetId : ContentId

 |
|

encryptionKey :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

RegisterSessionEncryptedAsset

Mogelijkheden: AssetManagement

ContentProvider:RegisterSessionEncryptedAsset (

contentId : ContentId , sessionKey :[string](/docs/nl-nl/luau/strings)

) : ()

Parameters

|

contentId : ContentId

 |
|

sessionKey :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

UnregisterDefaultEncryptionKey

Mogelijkheden: AssetManagement

ContentProvider:UnregisterDefaultEncryptionKey () : ()

Teruggaves

()

Feedback geven

---

UnregisterEncryptedAsset

Mogelijkheden: AssetManagement

ContentProvider:UnregisterEncryptedAsset (assetId : ContentId ) : ()

Parameters

|

assetId : ContentId

 |

Teruggaves

()

Feedback geven

---

Evenementen

AssetFetchFailed

Mogelijkheden: AssetManagement

ContentProvider.AssetFetchFailed (assetId : ContentId ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

assetId : ContentId

 |

Feedback geven

---

Ga naar

▼

ContentProvider

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[BaseUrl](#BaseUrl)

[RequestQueueSize](#RequestQueueSize)

[Methoden](#methods)

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

[Evenementen](#events)

[AssetFetchFailed](#AssetFetchFailed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
