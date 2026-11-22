<!-- Source: https://create.roblox.com/docs/reference/engine/classes/LocalizationService -->

LocalizationService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/LocalizationService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [LocalizationService](/docs/reference/engine/classes/LocalizationService)

English

Feedback

Engine Class

LocalizationService

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[RobloxLocaleId](#RobloxLocaleId) :[string](/docs/luau/strings)

 |
| --- | --- |
|

[SystemLocaleId](#SystemLocaleId) :[string](/docs/luau/strings)

 |

Methods

|

[GetCorescriptLocalizations](#GetCorescriptLocalizations) () : Instances

 |
|

[GetCountryRegionForPlayerAsync](#GetCountryRegionForPlayerAsync) (player :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[string](/docs/luau/strings)

 |
|

[GetTableEntries](#GetTableEntries) (instance :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[{any}](/docs/luau/tables#arrays)

 |
|

[GetTranslatorForLocaleAsync](#GetTranslatorForLocaleAsync) (locale :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[GetTranslatorForPlayer](#GetTranslatorForPlayer) (player :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Deprecated

 |
|

[GetTranslatorForPlayerAsync](#GetTranslatorForPlayerAsync) (player :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

RobloxLocaleId

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

LocalizationService.RobloxLocaleId :[string](/docs/luau/strings)

Provide feedback

---

SystemLocaleId

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

LocalizationService.SystemLocaleId :[string](/docs/luau/strings)

Provide feedback

---

Methods

GetCorescriptLocalizations

Capabilities: Basic

LocalizationService:GetCorescriptLocalizations () : Instances

Returns

Instances

Provide feedback

---

GetCountryRegionForPlayerAsync

Yields

Capabilities: Basic

LocalizationService:GetCountryRegionForPlayerAsync (player :[Instance](/docs/reference/engine/datatypes/Instance) ) :[string](/docs/luau/strings)

Parameters

|

player :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Getting Country/Region Code for a Player

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local result, code = pcall(LocalizationService.GetCountryRegionForPlayerAsync, LocalizationService, player)

if result and code == "CA" then

	print("Hello, friend from Canada!")

else

	print("GetCountryRegionForPlayerAsync failed: " .. code)

end

```

Provide feedback

---

GetTableEntries

Capabilities: Basic

LocalizationService:GetTableEntries (instance :[Instance](/docs/reference/engine/datatypes/Instance) ) :[{any}](/docs/luau/tables#arrays)

Parameters

|

instance :[Instance](/docs/reference/engine/datatypes/Instance)

Default Value: nil |

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetTranslatorForLocaleAsync

Yields

Capabilities: Basic

LocalizationService:GetTranslatorForLocaleAsync (locale :[string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

locale :[string](/docs/luau/strings)

 |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Code Samples

Getting and Using a Translator for a Locale

```

local LocalizationService = game:GetService("LocalizationService")

local textLabel = script.Parent

local success, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("fr")

end)

if success then

	local result = translator:Translate(textLabel, "Hello World!")

	print("Hello in French: " .. result)

else

	print("GetTranslatorForLocaleAsync failed: " .. translator)

end

```

Provide feedback

---

GetTranslatorForPlayer

Deprecated

Show details

---

GetTranslatorForPlayerAsync

Yields

Capabilities: Basic

LocalizationService:GetTranslatorForPlayerAsync (player :[Instance](/docs/reference/engine/datatypes/Instance) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

player :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Code Samples

Getting and Using a Translator for a Player

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local textLabel = script.Parent

local success, translator = pcall(function()

	return LocalizationService:GetTranslatorForPlayerAsync(Players.LocalPlayer)

end)

if success then

	local result = translator:Translate(textLabel, "Hello World!")

	print(result)

else

	print("GetTranslatorForPlayerAsync failed: " .. translator)

end

```

Provide feedback

---

Jump to

▼

LocalizationService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[RobloxLocaleId](#RobloxLocaleId)

[SystemLocaleId](#SystemLocaleId)

[Methods](#methods)

[GetCorescriptLocalizations()](#GetCorescriptLocalizations)

[GetCountryRegionForPlayerAsync()](#GetCountryRegionForPlayerAsync)

[GetTableEntries()](#GetTableEntries)

[GetTranslatorForLocaleAsync()](#GetTranslatorForLocaleAsync)

[GetTranslatorForPlayer()](#GetTranslatorForPlayer)

[GetTranslatorForPlayerAsync()](#GetTranslatorForPlayerAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
