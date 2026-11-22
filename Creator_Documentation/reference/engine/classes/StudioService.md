<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/StudioService -->

StudioService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StudioService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [StudioService](/docs/en-us/reference/engine/classes/StudioService)

English

Feedback

Engine Class

StudioService

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[ActiveScript](#ActiveScript) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[DraggerSolveConstraints](#DraggerSolveConstraints) :[boolean](/docs/en-us/luau/booleans)

 |
|

[DrawConstraintsOnTop](#DrawConstraintsOnTop) :[boolean](/docs/en-us/luau/booleans)

Deprecated

 |
|

[GridSize](#GridSize) :[number](/docs/en-us/luau/numbers)

 |
|

[RotateIncrement](#RotateIncrement) :[number](/docs/en-us/luau/numbers)

 |
|

[Secrets](#Secrets) :[string](/docs/en-us/luau/strings)

 |
|

[ShowConstraintDetails](#ShowConstraintDetails) :[boolean](/docs/en-us/luau/booleans)

 |
|

[ShowWeldDetails](#ShowWeldDetails) :[boolean](/docs/en-us/luau/booleans)

 |
|

[StudioLocaleId](#StudioLocaleId) :[string](/docs/en-us/luau/strings)

 |
|

[UseLocalSpace](#UseLocalSpace) :[boolean](/docs/en-us/luau/booleans)

 |

Methods

|

[GetClassIcon](#GetClassIcon) (className :  [string](/docs/en-us/luau/strings) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[GetUserId](#GetUserId) () :[number](/docs/en-us/luau/numbers)

 |
|

[PromptImportFile](#PromptImportFile) (fileTypeFilter :  [{any}](/docs/en-us/luau/tables#arrays) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Deprecated

 |
|

[PromptImportFileAsync](#PromptImportFileAsync) (fileTypeFilter :  [{any}](/docs/en-us/luau/tables#arrays) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[PromptImportFiles](#PromptImportFiles) (fileTypeFilter :  [{any}](/docs/en-us/luau/tables#arrays) ) : Instances

Deprecated

 |
|

[PromptImportFilesAsync](#PromptImportFilesAsync) (fileTypeFilter :  [{any}](/docs/en-us/luau/tables#arrays) ) : Instances

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

ActiveScript

Read Only

Not Replicated

Read Parallel

StudioService.ActiveScript :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Code Samples

Active Script

```

local StudioService = game:GetService("StudioService")

local startTime = os.time()

local activeScript

local function onActiveScriptChanged()

  local newActiveScript = StudioService.ActiveScript

	if activeScript and newActiveScript ~= activeScript then

		local deltaTime = os.time() - startTime

		print(("You edited %s for %d:%2.d"):format(activeScript.Name, deltaTime // 60, deltaTime % 60))

	end

	startTime = os.time()

	activeScript = newActiveScript

end

StudioService:GetPropertyChangedSignal("ActiveScript"):Connect(onActiveScriptChanged)

```

Provide feedback

---

DraggerSolveConstraints

Read Only

Not Replicated

Read Parallel

StudioService.DraggerSolveConstraints :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

DrawConstraintsOnTop

Deprecated

Show details

---

GridSize

Read Only

Not Replicated

Read Parallel

StudioService.GridSize :[number](/docs/en-us/luau/numbers)

Provide feedback

---

RotateIncrement

Read Only

Not Replicated

Read Parallel

StudioService.RotateIncrement :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Secrets

Roblox Script Security

Read Parallel

StudioService.Secrets :[string](/docs/en-us/luau/strings)

Provide feedback

---

ShowConstraintDetails

Read Only

Not Replicated

Read Parallel

StudioService.ShowConstraintDetails :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

ShowWeldDetails

Read Only

Not Replicated

Roblox Script Security

Read Parallel

StudioService.ShowWeldDetails :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

StudioLocaleId

Read Only

Not Replicated

Read Parallel

StudioService.StudioLocaleId :[string](/docs/en-us/luau/strings)

Code Samples

Studio Locale Id

```

local locale = game:GetService("StudioService").StudioLocaleId

if locale == "en_US" then

	print("Howdy, ya'll")

elseif locale == "en_GB" then

	print("'Ello, gov'na")

elseif locale:sub(1, 2) == "en" then

	print("Hello")

elseif locale == "fr_FR" then

	print("Bonjour")

end

```

Provide feedback

---

UseLocalSpace

Not Replicated

Read Parallel

StudioService.UseLocalSpace :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Methods

GetClassIcon

Plugin Security

StudioService:GetClassIcon (className :[string](/docs/en-us/luau/strings) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Parameters

|

className :[string](/docs/en-us/luau/strings)

 |

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Provide feedback

---

GetUserId

Plugin Security

StudioService:GetUserId () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

StudioService:GetUserId

```

-- Can only be used in a plugin

local StudioService = game:GetService("StudioService")

local Players = game:GetService("Players")

local loggedInUserId = StudioService:GetUserId()

local loggedInUserName = Players:GetNameFromUserIdAsync(loggedInUserId)

print("Hello,", loggedInUserName)

```

Provide feedback

---

PromptImportFile

Deprecated

Show details

---

PromptImportFileAsync

Yields

Plugin Security

StudioService:PromptImportFileAsync (fileTypeFilter :[{any}](/docs/en-us/luau/tables#arrays) ) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Parameters

|

fileTypeFilter :[{any}](/docs/en-us/luau/tables#arrays)

Default Value: {} |

Returns

[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

PromptImportFiles

Deprecated

Show details

---

PromptImportFilesAsync

Yields

Plugin Security

StudioService:PromptImportFilesAsync (fileTypeFilter :[{any}](/docs/en-us/luau/tables#arrays) ) : Instances

Parameters

|

fileTypeFilter :[{any}](/docs/en-us/luau/tables#arrays)

Default Value: {} |

Returns

Instances

Provide feedback

---

Jump to

▼

StudioService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[ActiveScript](#ActiveScript)

[DraggerSolveConstraints](#DraggerSolveConstraints)

[DrawConstraintsOnTop](#DrawConstraintsOnTop)

[GridSize](#GridSize)

[RotateIncrement](#RotateIncrement)

[Secrets](#Secrets)

[ShowConstraintDetails](#ShowConstraintDetails)

[ShowWeldDetails](#ShowWeldDetails)

[StudioLocaleId](#StudioLocaleId)

[UseLocalSpace](#UseLocalSpace)

[Methods](#methods)

[GetClassIcon()](#GetClassIcon)

[GetUserId()](#GetUserId)

[PromptImportFile()](#PromptImportFile)

[PromptImportFileAsync()](#PromptImportFileAsync)

[PromptImportFiles()](#PromptImportFiles)

[PromptImportFilesAsync()](#PromptImportFilesAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
