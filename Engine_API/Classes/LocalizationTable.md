<!-- Source: https://create.roblox.com/docs/reference/engine/classes/LocalizationTable -->

LocalizationTable | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/LocalizationTable.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [LocalizationTable](/docs/reference/engine/classes/LocalizationTable)

English

Feedback

Engine Class

LocalizationTable

---

## Summary

Properties

|

[DevelopmentLanguage](#DevelopmentLanguage) :[string](/docs/luau/strings)

Deprecated

 |
| --- | --- |
|

[Root](#Root) :[Instance](/docs/reference/engine/datatypes/Instance)

Deprecated

 |
|

[SourceLocaleId](#SourceLocaleId) :[string](/docs/luau/strings)

 |

Methods

|

[GetContents](#GetContents) () :[string](/docs/luau/strings)

Deprecated

 |
|

[GetEntries](#GetEntries) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetString](#GetString) (targetLocaleId :  [string](/docs/luau/strings) , key :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Deprecated

 |
|

[GetTranslator](#GetTranslator) (localeId :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[RemoveEntry](#RemoveEntry) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) ) : ()

 |
|

[RemoveEntryValue](#RemoveEntryValue) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) , localeId :  [string](/docs/luau/strings) ) : ()

 |
|

[RemoveKey](#RemoveKey) (key :  [string](/docs/luau/strings) ) : ()

Deprecated

 |
|

[RemoveTargetLocale](#RemoveTargetLocale) (localeId :  [string](/docs/luau/strings) ) : ()

 |
|

[SetContents](#SetContents) (contents :  [string](/docs/luau/strings) ) : ()

Deprecated

 |
|

[SetEntries](#SetEntries) (entries :  Variant ) : ()

 |
|

[SetEntry](#SetEntry) (key :  [string](/docs/luau/strings) , targetLocaleId :  [string](/docs/luau/strings) , text :  [string](/docs/luau/strings) ) : ()

Deprecated

 |
|

[SetEntryContext](#SetEntryContext) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) , newContext :  [string](/docs/luau/strings) ) : ()

 |
|

[SetEntryExample](#SetEntryExample) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) , example :  [string](/docs/luau/strings) ) : ()

 |
|

[SetEntryKey](#SetEntryKey) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) , newKey :  [string](/docs/luau/strings) ) : ()

 |
|

[SetEntrySource](#SetEntrySource) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) , newSource :  [string](/docs/luau/strings) ) : ()

 |
|

[SetEntryValue](#SetEntryValue) (key :  [string](/docs/luau/strings) , source :  [string](/docs/luau/strings) , context :  [string](/docs/luau/strings) , localeId :  [string](/docs/luau/strings) , text :  [string](/docs/luau/strings) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

LocalizationTable

```

local LocalizationService = game:GetService("LocalizationService")

local function createLocalizationTable(entries): LocalizationTable

	local localTable = Instance.new("LocalizationTable")

	localTable.SourceLocaleId = LocalizationService.SystemLocaleId

	localTable:SetEntries(entries)

	return localTable

end

local entries = {

	{

		Key = "Hello_World", -- The 'expressionKey' to be used with GetString

		Values = { -- A dictionary of keys corresponding to IETF language tags, and their translations.

			["ru"] = " !", -- Russian

			["fr"] = "Bonjour le monde!", -- French

			["de"] = "Hallo Welt!", -- German

			["en-US"] = "Hello world!", -- English

			["it"] = "Ciao mondo!", -- Italian

			["pt-BR"] = "Ol Mundo!", -- Portuguese

			["ja"] = "", -- Japanese

			["es"] = "Hola Mundo!", -- Spanish

		},

	},

}

local helloWorldTable = createLocalizationTable(entries)

local translatorEnglish = helloWorldTable:GetTranslator("en-US")

print(translatorEnglish:FormatByKey("Hello_World"))

```

---

API Reference

Properties

DevelopmentLanguage

Deprecated

Show details

---

Root

Deprecated

Show details

---

SourceLocaleId

Read Parallel

Capabilities: Basic

LocalizationTable.SourceLocaleId :[string](/docs/luau/strings)

Provide feedback

---

Methods

GetContents

Deprecated

Show details

---

GetEntries

Capabilities: Basic

LocalizationTable:GetEntries () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Code Samples

Using a LocalizationTable

```

local LocalizationService = game:GetService("LocalizationService")

local localizationTable = LocalizationService:FindFirstChild("LocalizationTable")

local entries = {

	{

		["Key"] = "0001",

		["Source"] = "en-us",

		["Values"] = {

			["0001"] = "Hello Muddah, hello Fadduh.",

			["0002"] = "Here I am at Camp Granada.",

			["0003"] = "Camp is very entertaining.",

			["0004"] = "And they say we'll have some fun if it stops raining.",

		},

	},

}

localizationTable:SetEntries(entries)

local get_results = localizationTable:GetEntries()

for _index, dict in pairs(get_results) do

	for _key, value in pairs(dict["Values"]) do -- Loop through every key, value pair in the dictionary to print our strings

		print(value)

	end

end

```

Provide feedback

---

GetString

Deprecated

Show details

---

GetTranslator

Capabilities: Basic

LocalizationTable:GetTranslator (localeId :[string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

localeId :[string](/docs/luau/strings)

 |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Provide feedback

---

RemoveEntry

Capabilities: Basic

LocalizationTable:RemoveEntry (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

RemoveEntryValue

Capabilities: Basic

LocalizationTable:RemoveEntryValue (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings) , localeId :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |
|

localeId :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

RemoveKey

Deprecated

Show details

---

RemoveTargetLocale

Capabilities: Basic

LocalizationTable:RemoveTargetLocale (localeId :[string](/docs/luau/strings) ) : ()

Parameters

|

localeId :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetContents

Deprecated

Show details

---

SetEntries

Capabilities: Basic

LocalizationTable:SetEntries (entries : Variant ) : ()

Parameters

|

entries : Variant

 |

Returns

()

Provide feedback

---

SetEntry

Deprecated

Show details

---

SetEntryContext

Capabilities: Basic

LocalizationTable:SetEntryContext (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings) , newContext :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |
|

newContext :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetEntryExample

Capabilities: Basic

LocalizationTable:SetEntryExample (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings) , example :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |
|

example :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetEntryKey

Capabilities: Basic

LocalizationTable:SetEntryKey (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings) , newKey :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |
|

newKey :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetEntrySource

Capabilities: Basic

LocalizationTable:SetEntrySource (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings) , newSource :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |
|

newSource :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetEntryValue

Capabilities: Basic

LocalizationTable:SetEntryValue (

key :[string](/docs/luau/strings) , source :[string](/docs/luau/strings) , context :[string](/docs/luau/strings) , localeId :[string](/docs/luau/strings) , text :[string](/docs/luau/strings)

) : ()

Parameters

|

key :[string](/docs/luau/strings)

 |
|

source :[string](/docs/luau/strings)

 |
|

context :[string](/docs/luau/strings)

 |
|

localeId :[string](/docs/luau/strings)

 |
|

text :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

Jump to

▼

LocalizationTable

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[DevelopmentLanguage](#DevelopmentLanguage)

[Root](#Root)

[SourceLocaleId](#SourceLocaleId)

[Methods](#methods)

[GetContents()](#GetContents)

[GetEntries()](#GetEntries)

[GetString()](#GetString)

[GetTranslator()](#GetTranslator)

[RemoveEntry()](#RemoveEntry)

[RemoveEntryValue()](#RemoveEntryValue)

[RemoveKey()](#RemoveKey)

[RemoveTargetLocale()](#RemoveTargetLocale)

[SetContents()](#SetContents)

[SetEntries()](#SetEntries)

[SetEntry()](#SetEntry)

[SetEntryContext()](#SetEntryContext)

[SetEntryExample()](#SetEntryExample)

[SetEntryKey()](#SetEntryKey)

[SetEntrySource()](#SetEntrySource)

[SetEntryValue()](#SetEntryValue)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
