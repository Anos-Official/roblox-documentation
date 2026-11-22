<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StyleBase -->

StyleBase | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StyleBase](/docs/nl-nl/reference/engine/classes/StyleBase)

Nederlands

Feedback

Engine-klasse

StyleBase

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StyleBase)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetStyleRules](#GetStyleRules) () : {[StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule) }

 |
| --- | --- |
|

[InsertStyleRule](#InsertStyleRule) (rule :  [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule) , priority :  [number](/docs/nl-nl/luau/numbers) ? ) : ()

 |
|

[SetStyleRules](#SetStyleRules) (rules :  Instances ) : ()

 |

Evenementen

|

[StyleRulesChanged](#StyleRulesChanged) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule) , [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet)

---

API-referentie

Methoden

GetStyleRules

Mogelijkheden: UI

StyleBase:GetStyleRules () : {[StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule) }

Teruggaves

{[StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule) }

Feedback geven

---

InsertStyleRule

Mogelijkheden: UI

StyleBase:InsertStyleRule (

rule :[StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule) , priority :[number](/docs/nl-nl/luau/numbers) ?

) : ()

Parameters

|

rule :[StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)

 |
|

priority :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

()

Feedback geven

---

SetStyleRules

Mogelijkheden: UI

StyleBase:SetStyleRules (rules : Instances ) : ()

Parameters

|

rules : Instances

 |

Teruggaves

()

Codevoorbeelden

Stijlregels Instellen

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

Feedback geven

---

Evenementen

StyleRulesChanged

Mogelijkheden: UI

StyleBase.StyleRulesChanged () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

Ga naar

▼

StyleBase

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[GetStyleRules()](#GetStyleRules)

[InsertStyleRule()](#InsertStyleRule)

[SetStyleRules()](#SetStyleRules)

[Evenementen](#events)

[StyleRulesChanged](#StyleRulesChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
