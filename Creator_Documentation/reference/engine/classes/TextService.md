<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/TextService -->

TextService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TextService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [TextService](/docs/en-us/reference/engine/classes/TextService)

English

Feedback

Engine Class

TextService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[FilterAndTranslateStringAsync](#FilterAndTranslateStringAsync) (stringToFilter :  [string](/docs/en-us/luau/strings) , fromUserId :  [number](/docs/en-us/luau/numbers) , targetLocales :  [{any}](/docs/en-us/luau/tables#arrays) , textContext :  [Enum.TextFilterContext](/docs/en-us/reference/engine/enums/TextFilterContext) ) :[TextFilterTranslatedResult](/docs/en-us/reference/engine/classes/TextFilterTranslatedResult)

Deprecated

 |
| --- | --- |
|

[FilterStringAsync](#FilterStringAsync) (stringToFilter :  [string](/docs/en-us/luau/strings) , fromUserId :  [number](/docs/en-us/luau/numbers) , textContext :  [Enum.TextFilterContext](/docs/en-us/reference/engine/enums/TextFilterContext) ) :[TextFilterResult](/docs/en-us/reference/engine/classes/TextFilterResult)

 |
|

[GetFamilyInfoAsync](#GetFamilyInfoAsync) (assetId :  ContentId ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[GetTextBoundsAsync](#GetTextBoundsAsync) (params :  [GetTextBoundsParams](/docs/en-us/reference/engine/classes/GetTextBoundsParams) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[GetTextSize](#GetTextSize) (string :  [string](/docs/en-us/luau/strings) , fontSize :  [number](/docs/en-us/luau/numbers) , font :  [Enum.Font](/docs/en-us/reference/engine/enums/Font) , frameSize :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[GetTextSizeOffsetAsync](#GetTextSizeOffsetAsync) (fontSize :  [number](/docs/en-us/luau/numbers) , font :  [Font](/docs/en-us/reference/engine/datatypes/Font) ) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

FilterAndTranslateStringAsync

Deprecated

Show details

---

FilterStringAsync

Yields

Capabilities: UI

TextService:FilterStringAsync (

stringToFilter :[string](/docs/en-us/luau/strings) , fromUserId :[number](/docs/en-us/luau/numbers) , textContext :[Enum.TextFilterContext](/docs/en-us/reference/engine/enums/TextFilterContext)

) :[TextFilterResult](/docs/en-us/reference/engine/classes/TextFilterResult)

Parameters

|

stringToFilter :[string](/docs/en-us/luau/strings)

 |
|

fromUserId :[number](/docs/en-us/luau/numbers)

 |
|

textContext :[Enum.TextFilterContext](/docs/en-us/reference/engine/enums/TextFilterContext)

Default Value: PrivateChat |

Returns

[TextFilterResult](/docs/en-us/reference/engine/classes/TextFilterResult)

Code Samples

Pet Name Filter Example

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local TextService = game:GetService("TextService")

local Players = game:GetService("Players")

local Remotes = Instance.new("Folder")

Remotes.Name = "PetNamingRemotes"

Remotes.Parent = ReplicatedStorage

local UserNamedPet = Instance.new("RemoteEvent")

UserNamedPet.Name = "UserNamedPet"

UserNamedPet.Parent = Remotes

local SendPetName = Instance.new("RemoteEvent")

SendPetName.Name = "SendPetName"

SendPetName.Parent = Remotes

local RequestAllPetNames = Instance.new("RemoteFunction")

RequestAllPetNames.Name = "RequestAllPetNames"

RequestAllPetNames.Parent = Remotes

local filterResults = {}

local function broadcastPetName(userId)

	local filterResult = filterResults[userId]

	if filterResult then

		for _, player in pairs(Players:GetPlayers()) do

			if player then

				-- spawn a new thread so as to not yield the update

				task.spawn(function()

					-- grab the filtered string for this user

					local toUserId = player.UserId

					local filteredString = filterResult:GetNonChatStringForUserAsync(toUserId)

					filteredString = filteredString or ""

					SendPetName:FireClient(player, userId, filteredString)

				end)

			end

		end

	end

end

UserNamedPet.OnServerEvent:Connect(function(player, petName)

	local fromUserId = player.UserId

	-- pcall to catch errors

	local success, result = pcall(function()

		return TextService:FilterStringAsync(petName, fromUserId)

	end)

	if success then

		filterResults[fromUserId] = result

		broadcastPetName(fromUserId)

	else

		print("Could not filter pet name")

	end

end)

RequestAllPetNames.OnServerInvoke = function(player)

	local toUserId = player.UserId

	local petNames = {}

	-- go through filter results and filter the pet name to be sent

	for fromUserId, filterResult in pairs(filterResults) do

		local filteredString = filterResult:GetNonChatStringForUserAsync(toUserId)

		filteredString = filteredString or ""

		-- need to convert userId to string so it can't be sent via a remote function

		petNames[tostring(fromUserId)] = filteredString

	end

	return petNames

end

Players.PlayerRemoving:Connect(function(oldPlayer)

	local userId = oldPlayer.UserId

	filterResults[userId] = nil

end)

```

Provide feedback

---

GetFamilyInfoAsync

Yields

Capabilities: UI

TextService:GetFamilyInfoAsync (assetId : ContentId ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Parameters

|

assetId : ContentId

 |

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

Get Font Family Information

```

local TextService = game:GetService("TextService")

local familyToCheck = "rbxasset://fonts/families/Arimo.json"

local success, info = pcall(function()

	return TextService:GetFamilyInfoAsync(familyToCheck)

end)

if success then

	print("Name of the font:", info.Name)

	print("Faces:")

	for _, face in info.Faces do

		print("--------")

		print("Name:", face.Name)

		print("Weight:", face.Weight.Name)

		print("Style:", face.Style.Name)

	end

end

```

Provide feedback

---

GetTextBoundsAsync

Yields

Capabilities: UI

TextService:GetTextBoundsAsync (params :[GetTextBoundsParams](/docs/en-us/reference/engine/classes/GetTextBoundsParams) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

params :[GetTextBoundsParams](/docs/en-us/reference/engine/classes/GetTextBoundsParams)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

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

Provide feedback

---

GetTextSize

Capabilities: UI

TextService:GetTextSize (

string :[string](/docs/en-us/luau/strings) , fontSize :[number](/docs/en-us/luau/numbers) , font :[Enum.Font](/docs/en-us/reference/engine/enums/Font) , frameSize :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

string :[string](/docs/en-us/luau/strings)

 |
|

fontSize :[number](/docs/en-us/luau/numbers)

 |
|

font :[Enum.Font](/docs/en-us/reference/engine/enums/Font)

 |
|

frameSize :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Code Samples

Getting Text Size

```

local TextService = game:GetService("TextService")

local function getTextBounds()

	local message = "Hello world!"

	local size = Vector2.new(1, 1)

	local bounds = TextService:GetTextSize(message, 12, "SourceSans", size)

	return bounds

end

print(getTextBounds())

```

Provide feedback

---

GetTextSizeOffsetAsync

Yields

Capabilities: UI

TextService:GetTextSizeOffsetAsync (

fontSize :[number](/docs/en-us/luau/numbers) , font :[Font](/docs/en-us/reference/engine/datatypes/Font)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

fontSize :[number](/docs/en-us/luau/numbers)

 |
|

font :[Font](/docs/en-us/reference/engine/datatypes/Font)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

Get Text Size Offset

```

local TextService = game:GetService("TextService")

local label = script.Parent.TextLabel

-- Get offset adjusted for the player's preferred text size setting

local success, offset = pcall(function()

	return TextService:GetTextSizeOffsetAsync(label.TextSize, label.FontFace)

end)

if success then

	-- Adjust core height of label by adding the offset

	label.Size = UDim2.fromOffset(label.Size.X.Offset, label.Size.Y.Offset + offset)

end

```

Provide feedback

---

Jump to

▼

TextService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[FilterAndTranslateStringAsync()](#FilterAndTranslateStringAsync)

[FilterStringAsync()](#FilterStringAsync)

[GetFamilyInfoAsync()](#GetFamilyInfoAsync)

[GetTextBoundsAsync()](#GetTextBoundsAsync)

[GetTextSize()](#GetTextSize)

[GetTextSizeOffsetAsync()](#GetTextSizeOffsetAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
