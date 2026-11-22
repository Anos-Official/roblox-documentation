<!-- Source: https://create.roblox.com/docs/reference/engine/classes/TextGenerator -->

TextGenerator | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TextGenerator.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [TextGenerator](/docs/reference/engine/classes/TextGenerator)

English

Feedback

Engine Class

TextGenerator

---

## Summary

Properties

|

[Seed](#Seed) :[number](/docs/luau/numbers)

 |
| --- | --- |
|

[SystemPrompt](#SystemPrompt) :[string](/docs/luau/strings)

 |
|

[Temperature](#Temperature) :[number](/docs/luau/numbers)

 |
|

[TopP](#TopP) :[number](/docs/luau/numbers)

 |

Methods

|

[GenerateTextAsync](#GenerateTextAsync) (request :  [Dictionary](/docs/luau/tables#dictionaries) ) :[Dictionary](/docs/luau/tables#dictionaries)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Generate Text

```

local Workspace = game:GetService("Workspace")

local textGenerator = Instance.new("TextGenerator")

textGenerator.Parent = Workspace

textGenerator.SystemPrompt = "You are a helpful NPC in a virtual world."

textGenerator.Temperature = 0.8

textGenerator.TopP = 0.6

textGenerator.Seed = 7

local function getResponse(userInput)

	local request = {

		UserPrompt = userInput,

		MaxTokens = 50

	}

	local success, response = pcall(function()

		return textGenerator:GenerateTextAsync(request)

	end)

	if success then

		if response then

			print("Generated Text: " .. response.GeneratedText)

			print("Context Token: " .. response.ContextToken)

			print("Model: " .. response.Model)

			return response

		end

	else

		warn("Text generation failed: " .. tostring(response))

	end

	return nil

end

getResponse("Tell me something cool.")

```

---

API Reference

Properties

Seed

Read Parallel

Capabilities: Basic

TextGenerator.Seed :[number](/docs/luau/numbers)

Provide feedback

---

SystemPrompt

Read Parallel

Capabilities: Basic

TextGenerator.SystemPrompt :[string](/docs/luau/strings)

Provide feedback

---

Temperature

Read Parallel

Capabilities: Basic

TextGenerator.Temperature :[number](/docs/luau/numbers)

Provide feedback

---

TopP

Read Parallel

Capabilities: Basic

TextGenerator.TopP :[number](/docs/luau/numbers)

Provide feedback

---

Methods

GenerateTextAsync

Yields

Capabilities: Basic

TextGenerator:GenerateTextAsync (request :[Dictionary](/docs/luau/tables#dictionaries) ) :[Dictionary](/docs/luau/tables#dictionaries)

Parameters

|

request :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Provide feedback

---

Jump to

▼

TextGenerator

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Seed](#Seed)

[SystemPrompt](#SystemPrompt)

[Temperature](#Temperature)

[TopP](#TopP)

[Methods](#methods)

[GenerateTextAsync()](#GenerateTextAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
