<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/SharedTableRegistry -->

SharedTableRegistry | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/SharedTableRegistry.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [SharedTableRegistry](/docs/en-us/reference/engine/classes/SharedTableRegistry)

English

Feedback

Engine Class

SharedTableRegistry

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetSharedTable](#GetSharedTable) (name :  [string](/docs/en-us/luau/strings) ) :[SharedTable](/docs/en-us/reference/engine/datatypes/SharedTable)

 |
| --- | --- |
|

[SetSharedTable](#SetSharedTable) (name :  [string](/docs/en-us/luau/strings) , st :  [SharedTable](/docs/en-us/reference/engine/datatypes/SharedTable) ? ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

GetSharedTable

Write Parallel

Capabilities: ScriptGlobals

SharedTableRegistry:GetSharedTable (name :[string](/docs/en-us/luau/strings) ) :[SharedTable](/docs/en-us/reference/engine/datatypes/SharedTable)

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |

Returns

[SharedTable](/docs/en-us/reference/engine/datatypes/SharedTable)

Code Samples

Get Shared Table

```

local SharedTableRegistry = game:GetService("SharedTableRegistry")

local st = SharedTableRegistry:GetSharedTable("MyData")

```

Provide feedback

---

SetSharedTable

Write Parallel

Capabilities: ScriptGlobals

SharedTableRegistry:SetSharedTable (

name :[string](/docs/en-us/luau/strings) , st :[SharedTable](/docs/en-us/reference/engine/datatypes/SharedTable) ?

) : ()

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |
|

st :[SharedTable](/docs/en-us/reference/engine/datatypes/SharedTable) ?

 |

Returns

()

Code Samples

Set Shared Table

```

local SharedTableRegistry = game:GetService("SharedTableRegistry")

-- Register a SharedTable with the name "MyData":

local st = SharedTable.new({1, 2, 3})

SharedTableRegistry:SetSharedTable("MyData", st)

-- Unregister the SharedTable with the name "MyData":

SharedTableRegistry:SetSharedTable("MyData", nil)

```

Provide feedback

---

Jump to

▼

SharedTableRegistry

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetSharedTable()](#GetSharedTable)

[SetSharedTable()](#SetSharedTable)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
