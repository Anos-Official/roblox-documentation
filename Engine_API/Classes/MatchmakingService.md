<!-- Source: https://create.roblox.com/docs/reference/engine/classes/MatchmakingService -->

MatchmakingService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/MatchmakingService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [MatchmakingService](/docs/reference/engine/classes/MatchmakingService)

English

Feedback

Engine Class

MatchmakingService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetServerAttribute](#GetServerAttribute) (name :  [string](/docs/luau/strings) ) :[Tuple](/docs/luau/tuples)

 |
| --- | --- |
|

[InitializeServerAttributesForStudio](#InitializeServerAttributesForStudio) (serverAttributes :  [Dictionary](/docs/luau/tables#dictionaries) ) :[Tuple](/docs/luau/tuples)

 |
|

[SetServerAttribute](#SetServerAttribute) (name :  [string](/docs/luau/strings) , value :  Variant ) :[Tuple](/docs/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

GetServerAttribute

Capabilities: Basic

MatchmakingService:GetServerAttribute (name :[string](/docs/luau/strings) ) :[Tuple](/docs/luau/tuples)

Parameters

|

name :[string](/docs/luau/strings)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

InitializeServerAttributesForStudio

Capabilities: Basic

MatchmakingService:InitializeServerAttributesForStudio (serverAttributes :[Dictionary](/docs/luau/tables#dictionaries) ) :[Tuple](/docs/luau/tuples)

Parameters

|

serverAttributes :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

SetServerAttribute

Capabilities: Basic

MatchmakingService:SetServerAttribute (

name :[string](/docs/luau/strings) , value : Variant

) :[Tuple](/docs/luau/tuples)

Parameters

|

name :[string](/docs/luau/strings)

 |
|

value : Variant

 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

MatchmakingService sample

```

local MatchmakingService = game:GetService("MatchmakingService")

local RunService = game:GetService("RunService")

if RunService:IsStudio() then

	-- Sets up initial attributes and schema for testing

	MatchmakingService:InitializeServerAttributesForStudio({

		Level = "Advanced",

		Elo = 123.456,

		TrainingMode = true

	})

end

-- Retrieves the Level attribute

local currentLevel, errorMessage = MatchmakingService:GetServerAttribute("Level")

if errorMessage then

	warn(errorMessage)

else

	print("Current level: " .. currentLevel)

end

-- Updates the Level attribute value to Advanced

local success, errorMessage = MatchmakingService:SetServerAttribute("Level", "Advanced")

if not success then

	warn("Failed to update server attribute [Level] to [Advanced] due to error: " .. errorMessage)

else

	print("Successfully set [Level] to [Advanced]")

end

```

Provide feedback

---

Jump to

▼

MatchmakingService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetServerAttribute()](#GetServerAttribute)

[InitializeServerAttributesForStudio()](#InitializeServerAttributesForStudio)

[SetServerAttribute()](#SetServerAttribute)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
