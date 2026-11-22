<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/KeyframeSequenceProvider -->

KeyframeSequenceProvider | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/KeyframeSequenceProvider.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [KeyframeSequenceProvider](/docs/en-us/reference/engine/classes/KeyframeSequenceProvider)

English

Feedback

Engine Class

KeyframeSequenceProvider

Deprecated

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetAnimations](#GetAnimations) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Deprecated

 |
| --- | --- |
|

[GetAnimationsAsync](#GetAnimationsAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[GetKeyframeSequence](#GetKeyframeSequence) (assetId :  ContentId ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Deprecated

 |
|

[GetKeyframeSequenceAsync](#GetKeyframeSequenceAsync) (assetId :  ContentId ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[GetKeyframeSequenceById](#GetKeyframeSequenceById) (assetId :  [number](/docs/en-us/luau/numbers) , useCache :  [boolean](/docs/en-us/luau/booleans) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Deprecated

 |
|

[RegisterActiveKeyframeSequence](#RegisterActiveKeyframeSequence) (keyframeSequence :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ContentId

 |
|

[RegisterKeyframeSequence](#RegisterKeyframeSequence) (keyframeSequence :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ContentId

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Create temporary animation

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local function createPreviewAnimation(keyframeSequence)

	local hashId = KeyframeSequenceProvider:RegisterKeyframeSequence(keyframeSequence)

	local Animation = Instance.new("Animation")

	Animation.AnimationId = hashId

	return Animation

end

local keyframeSequence = Instance.new("KeyframeSequence")

local animation = createPreviewAnimation(keyframeSequence)

print(animation)

```

---

API Reference

Methods

GetAnimations

Deprecated

Show details

---

GetAnimationsAsync

Yields

Capabilities: Animation

KeyframeSequenceProvider:GetAnimationsAsync (userId :[User](/docs/en-us/reference/engine/datatypes/User) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |

Returns

[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Code Samples

KeyframeSequenceProvider GetAnimationsAsync

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local USER_ID = 0 -- Insert your UserId here

local function extractPages(pagesObject)

	local array = {}

	while true do

		local thisPage = pagesObject:GetCurrentPage()

		for _, v in pairs(thisPage) do

			table.insert(array, v)

		end

		if pagesObject.IsFinished then

			break

		end

		pagesObject:AdvanceToNextPageAsync()

	end

	return array

end

local inventoryPages = KeyframeSequenceProvider:GetAnimationsAsync(USER_ID)

local animationIds = extractPages(inventoryPages)

for _, id in pairs(animationIds) do

	print(id)

end

print("total: ", #animationIds)

```

Provide feedback

---

GetKeyframeSequence

Deprecated

Show details

---

GetKeyframeSequenceAsync

Yields

Capabilities: Animation

KeyframeSequenceProvider:GetKeyframeSequenceAsync (assetId : ContentId ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Parameters

|

assetId : ContentId

 |

Returns

[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Code Samples

Getting an animation's KeyframeSequence

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local ANIMATION_ID = "rbxassetid://507771019"

-- Get the keyframe sequence for the asset

local keyframeSequence

local success, err = pcall(function()

	keyframeSequence = KeyframeSequenceProvider:GetKeyframeSequenceAsync(ANIMATION_ID)

end)

if success then

	-- Iterate over each keyframe and print its time value

	local keyframeTable = keyframeSequence:GetKeyframes()

	for key, value in keyframeTable do

		print(`The time of keyframe number {key} is: {value.Time}`)

	end

else

	print(`Error getting KeyframeSequence: {err}`)

end

```

Provide feedback

---

GetKeyframeSequenceById

Deprecated

Show details

---

RegisterActiveKeyframeSequence

Capabilities: Animation

KeyframeSequenceProvider:RegisterActiveKeyframeSequence (keyframeSequence :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ContentId

Parameters

|

keyframeSequence :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

ContentId

Code Samples

Create temporary animation

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local function createPreviewAnimation(keyframeSequence)

	local hashId = KeyframeSequenceProvider:RegisterKeyframeSequence(keyframeSequence)

	local Animation = Instance.new("Animation")

	Animation.AnimationId = hashId

	return Animation

end

local keyframeSequence = Instance.new("KeyframeSequence")

local animation = createPreviewAnimation(keyframeSequence)

print(animation)

```

Provide feedback

---

RegisterKeyframeSequence

Capabilities: Animation

KeyframeSequenceProvider:RegisterKeyframeSequence (keyframeSequence :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ContentId

Parameters

|

keyframeSequence :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

ContentId

Code Samples

KeyframeSequenceProvider:RegisterKeyframeSequence

```

local KeyframeSequenceProvider = game:GetService("KeyframeSequenceProvider")

local asset = KeyframeSequenceProvider:RegisterKeyframeSequence(workspace.KeyframeSequence)

local animation = Instance.new("Animation")

animation.Name = "TestAnimation"

animation.AnimationId = asset

animation.Parent = workspace

```

Provide feedback

---

Jump to

▼

KeyframeSequenceProvider

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetAnimations()](#GetAnimations)

[GetAnimationsAsync()](#GetAnimationsAsync)

[GetKeyframeSequence()](#GetKeyframeSequence)

[GetKeyframeSequenceAsync()](#GetKeyframeSequenceAsync)

[GetKeyframeSequenceById()](#GetKeyframeSequenceById)

[RegisterActiveKeyframeSequence()](#RegisterActiveKeyframeSequence)

[RegisterKeyframeSequence()](#RegisterKeyframeSequence)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
