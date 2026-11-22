<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Translator -->

Translator | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Translator.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Translator](/docs/reference/engine/classes/Translator)

English

Feedback

Engine Class

Translator

Not Creatable

Not Replicated

---

## Summary

Properties

|

[LocaleId](#LocaleId) :[string](/docs/luau/strings)

 |
| --- | --- |

Methods

|

[FormatByKey](#FormatByKey) (key :  [string](/docs/luau/strings) , args :  Variant ) :[string](/docs/luau/strings)

 |
|

[Translate](#Translate) (context :  [Instance](/docs/reference/engine/datatypes/Instance) , text :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

LocaleId

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

Translator.LocaleId :[string](/docs/luau/strings)

Provide feedback

---

Methods

FormatByKey

Capabilities: Basic

Translator:FormatByKey (

key :[string](/docs/luau/strings) , args : Variant

) :[string](/docs/luau/strings)

Parameters

|

key :[string](/docs/luau/strings)

 |
|

args : Variant

 |

Returns

[string](/docs/luau/strings)

Provide feedback

---

Translate

Capabilities: Basic

Translator:Translate (

context :[Instance](/docs/reference/engine/datatypes/Instance) , text :[string](/docs/luau/strings)

) :[string](/docs/luau/strings)

Parameters

|

context :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

text :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Translate

```

local Players = game:GetService("Players")

local LocalizationService = game:GetService("LocalizationService")

local success, translator = pcall(function()

	return LocalizationService:GetTranslatorForPlayerAsync(Players.LocalPlayer)

end)

if success then

	local trans = translator:Translate(workspace.ComputerScreen.SurfaceGui.TextLabel, "Screen")

	print(trans)

else

	warn("Cannot load translator for player!")

end

```

Provide feedback

---

Jump to

▼

Translator

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[LocaleId](#LocaleId)

[Methods](#methods)

[FormatByKey()](#FormatByKey)

[Translate()](#Translate)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
