<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ExperienceNotificationService -->

ExperienceNotificationService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ExperienceNotificationService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ExperienceNotificationService](/docs/en-us/reference/engine/classes/ExperienceNotificationService)

English

Feedback

Engine Class

ExperienceNotificationService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[CanPromptOptInAsync](#CanPromptOptInAsync) () :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[PromptOptIn](#PromptOptIn) () : ()

 |

Events

|

[OptInPromptClosed](#OptInPromptClosed) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

CanPromptOptInAsync

Yields

Capabilities: Players, Social

ExperienceNotificationService:CanPromptOptInAsync () :[boolean](/docs/en-us/luau/booleans)

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

LocalScript - Notification Permission Prompt Implementation

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Function to check whether the player can be prompted to enable notifications

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Listen to opt-in prompt closed event

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt closed")

end)

```

Provide feedback

---

PromptOptIn

Capabilities: Players, Social

ExperienceNotificationService:PromptOptIn () : ()

Returns

()

Code Samples

LocalScript - Notification Permission Prompt Implementation

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Function to check whether the player can be prompted to enable notifications

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Listen to opt-in prompt closed event

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt closed")

end)

```

Provide feedback

---

Events

OptInPromptClosed

Capabilities: Players, Social

ExperienceNotificationService.OptInPromptClosed () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

LocalScript - Notification Permission Prompt Implementation

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Function to check whether the player can be prompted to enable notifications

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Listen to opt-in prompt closed event

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt closed")

end)

```

Provide feedback

---

Jump to

▼

ExperienceNotificationService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[CanPromptOptInAsync()](#CanPromptOptInAsync)

[PromptOptIn()](#PromptOptIn)

[Events](#events)

[OptInPromptClosed](#OptInPromptClosed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
