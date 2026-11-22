<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/StyleQuery -->

StyleQuery | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StyleQuery.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [StyleQuery](/docs/en-us/reference/engine/classes/StyleQuery)

English

Feedback

Engine Class

StyleQuery

---

## Summary

Properties

|

[IsActive](#IsActive) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |

Methods

|

[GetCondition](#GetCondition) (name :  [string](/docs/en-us/luau/strings) ) : Variant

 |
|

[GetConditions](#GetConditions) () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[SetCondition](#SetCondition) (name :  [string](/docs/en-us/luau/strings) , value :  Variant ) : ()

 |
|

[SetConditions](#SetConditions) (conditions :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

IsActive

Read Only

Not Replicated

Read Parallel

Capabilities: UI

StyleQuery.IsActive :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Methods

GetCondition

Capabilities: UI

StyleQuery:GetCondition (name :[string](/docs/en-us/luau/strings) ) : Variant

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |

Returns

Variant

Provide feedback

---

GetConditions

Capabilities: UI

StyleQuery:GetConditions () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Provide feedback

---

SetCondition

Capabilities: UI

StyleQuery:SetCondition (

name :[string](/docs/en-us/luau/strings) , value : Variant

) : ()

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |
|

value : Variant

 |

Returns

()

Code Samples

Set Condition

```

local styleQuery = Instance.new("StyleQuery")

styleQuery:SetCondition("MaxSize", Vector2.new(200, math.huge))

```

Provide feedback

---

SetConditions

Capabilities: UI

StyleQuery:SetConditions (conditions :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

Parameters

|

conditions :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Code Samples

Set Conditions

```

local styleQuery = Instance.new("StyleQuery")

styleQuery:SetConditions({

	["AspectRatioRange"] = NumberRange.new(0, 1),

	["MaxSize"] = Vector2.new(200, math.huge),

})

```

Provide feedback

---

Jump to

▼

StyleQuery

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[IsActive](#IsActive)

[Methods](#methods)

[GetCondition()](#GetCondition)

[GetConditions()](#GetConditions)

[SetCondition()](#SetCondition)

[SetConditions()](#SetConditions)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
