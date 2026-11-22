<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/StyleBase -->

StyleBase | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StyleBase.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [StyleBase](/docs/en-us/reference/engine/classes/StyleBase)

English

Feedback

Engine Class

StyleBase

Not Creatable

---

## Summary

Methods

|

[GetStyleRules](#GetStyleRules) () : {[StyleRule](/docs/en-us/reference/engine/classes/StyleRule) }

 |
| --- | --- |
|

[InsertStyleRule](#InsertStyleRule) (rule :  [StyleRule](/docs/en-us/reference/engine/classes/StyleRule) , priority :  [number](/docs/en-us/luau/numbers) ? ) : ()

 |
|

[SetStyleRules](#SetStyleRules) (rules :  Instances ) : ()

 |

Events

|

[StyleRulesChanged](#StyleRulesChanged) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[StyleRule](/docs/en-us/reference/engine/classes/StyleRule) , [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet)

---

API Reference

Methods

GetStyleRules

Capabilities: UI

StyleBase:GetStyleRules () : {[StyleRule](/docs/en-us/reference/engine/classes/StyleRule) }

Returns

{[StyleRule](/docs/en-us/reference/engine/classes/StyleRule) }

Provide feedback

---

InsertStyleRule

Capabilities: UI

StyleBase:InsertStyleRule (

rule :[StyleRule](/docs/en-us/reference/engine/classes/StyleRule) , priority :[number](/docs/en-us/luau/numbers) ?

) : ()

Parameters

|

rule :[StyleRule](/docs/en-us/reference/engine/classes/StyleRule)

 |
|

priority :[number](/docs/en-us/luau/numbers) ?

 |

Returns

()

Provide feedback

---

SetStyleRules

Capabilities: UI

StyleBase:SetStyleRules (rules : Instances ) : ()

Parameters

|

rules : Instances

 |

Returns

()

Code Samples

Set Style Rules

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = Instance.new("StyleSheet")

coreSheet.Name = "CoreSheet"

coreSheet.Parent = ReplicatedStorage

local styleRuleA = Instance.new("StyleRule")

styleRuleA.Selector = "Frame"

styleRuleA:SetProperty("BackgroundColor3", Color3.new(1, 0, 0))

local styleRuleB = Instance.new("StyleRule")

styleRuleB.Selector = "Frame"

styleRuleB:SetProperty("BackgroundColor3", Color3.new(0, 1, 0))

coreSheet:SetStyleRules({ styleRuleA, styleRuleB })

```

Provide feedback

---

Events

StyleRulesChanged

Capabilities: UI

StyleBase.StyleRulesChanged () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Jump to

▼

StyleBase

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[GetStyleRules()](#GetStyleRules)

[InsertStyleRule()](#InsertStyleRule)

[SetStyleRules()](#SetStyleRules)

[Events](#events)

[StyleRulesChanged](#StyleRulesChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
