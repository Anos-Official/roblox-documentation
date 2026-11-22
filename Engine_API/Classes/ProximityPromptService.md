<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ProximityPromptService -->

ProximityPromptService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ProximityPromptService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ProximityPromptService](/docs/reference/engine/classes/ProximityPromptService)

English

Feedback

Engine Class

ProximityPromptService

Service

Not Browsable

---

## Summary

Properties

|

[Enabled](#Enabled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[MaxIndicatorsVisible](#MaxIndicatorsVisible) :[number](/docs/luau/numbers)

 |
|

[MaxPromptsVisible](#MaxPromptsVisible) :[number](/docs/luau/numbers)

 |

Events

|

[IndicatorHidden](#IndicatorHidden) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[IndicatorShown](#IndicatorShown) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptButtonHoldBegan](#PromptButtonHoldBegan) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptButtonHoldEnded](#PromptButtonHoldEnded) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptHidden](#PromptHidden) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptShown](#PromptShown) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , inputType :  [Enum.ProximityPromptInputType](/docs/reference/engine/enums/ProximityPromptInputType) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptTriggered](#PromptTriggered) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptTriggerEnded](#PromptTriggerEnded) (prompt :  [ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Enabled

Read Parallel

Capabilities: Input

ProximityPromptService.Enabled :[boolean](/docs/luau/booleans)

Code Samples

Enabled

```

local ProximityPromptService = game:GetService("ProximityPromptService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local enablePrompts = Instance.new("BindableEvent")

enablePrompts.Name = "EnablePrompts"

enablePrompts.Parent = ReplicatedStorage

-- Connect to the BindableEvent and fire from another script controlling experience logic

enablePrompts.Event:Connect(function(enabled)

	ProximityPromptService.Enabled = enabled

end)

```

Provide feedback

---

MaxIndicatorsVisible

Read Parallel

Capabilities: Input

ProximityPromptService.MaxIndicatorsVisible :[number](/docs/luau/numbers)

Provide feedback

---

MaxPromptsVisible

Read Parallel

Capabilities: Input

ProximityPromptService.MaxPromptsVisible :[number](/docs/luau/numbers)

Provide feedback

---

Events

IndicatorHidden

Capabilities: Input

ProximityPromptService.IndicatorHidden (prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |

Provide feedback

---

IndicatorShown

Capabilities: Input

ProximityPromptService.IndicatorShown (prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |

Provide feedback

---

PromptButtonHoldBegan

Capabilities: Input

ProximityPromptService.PromptButtonHoldBegan (

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

 |

Provide feedback

---

PromptButtonHoldEnded

Capabilities: Input

ProximityPromptService.PromptButtonHoldEnded (

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

 |

Provide feedback

---

PromptHidden

Capabilities: Input

ProximityPromptService.PromptHidden (prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |

Provide feedback

---

PromptShown

Capabilities: Input

ProximityPromptService.PromptShown (

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , inputType :[Enum.ProximityPromptInputType](/docs/reference/engine/enums/ProximityPromptInputType)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |
|

inputType :[Enum.ProximityPromptInputType](/docs/reference/engine/enums/ProximityPromptInputType)

 |

Provide feedback

---

PromptTriggered

Capabilities: Input

ProximityPromptService.PromptTriggered (

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

 |

Provide feedback

---

PromptTriggerEnded

Capabilities: Input

ProximityPromptService.PromptTriggerEnded (

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/reference/engine/classes/Player)

 |

Provide feedback

---

Jump to

▼

ProximityPromptService

[Summary](#summary)

[Properties](#summary-properties)

[Events](#summary-events)

[Properties](#properties)

[Enabled](#Enabled)

[MaxIndicatorsVisible](#MaxIndicatorsVisible)

[MaxPromptsVisible](#MaxPromptsVisible)

[Events](#events)

[IndicatorHidden](#IndicatorHidden)

[IndicatorShown](#IndicatorShown)

[PromptButtonHoldBegan](#PromptButtonHoldBegan)

[PromptButtonHoldEnded](#PromptButtonHoldEnded)

[PromptHidden](#PromptHidden)

[PromptShown](#PromptShown)

[PromptTriggered](#PromptTriggered)

[PromptTriggerEnded](#PromptTriggerEnded)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
