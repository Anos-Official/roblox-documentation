<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ProximityPromptService -->

ProximityPromptService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ProximityPromptService](/docs/nl-nl/reference/engine/classes/ProximityPromptService)

Nederlands

Feedback

Engine-klasse

ProximityPromptService

Service

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ProximityPromptService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[MaxIndicatorsVisible](#MaxIndicatorsVisible) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MaxPromptsVisible](#MaxPromptsVisible) :[number](/docs/nl-nl/luau/numbers)

 |

Evenementen

|

[IndicatorHidden](#IndicatorHidden) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[IndicatorShown](#IndicatorShown) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptButtonHoldBegan](#PromptButtonHoldBegan) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptButtonHoldEnded](#PromptButtonHoldEnded) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptHidden](#PromptHidden) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptShown](#PromptShown) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , inputType :  [Enum.ProximityPromptInputType](/docs/nl-nl/reference/engine/enums/ProximityPromptInputType) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptTriggered](#PromptTriggered) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PromptTriggerEnded](#PromptTriggerEnded) (prompt :  [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Enabled

Parallel lezen

Mogelijkheden: Input

ProximityPromptService.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Ingeschakeld

```

local ProximityPromptService = game:GetService("ProximityPromptService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local enablePrompts = Instance.new("BindableEvent")

enablePrompts.Name = "EnablePrompts"

enablePrompts.Parent = ReplicatedStorage

-- Verbind met de BindableEvent en activeer vanuit een ander script dat de ervaring logica beheert

enablePrompts.Event:Connect(function(enabled)

	ProximityPromptService.Enabled = enabled

end)

```

Feedback geven

---

MaxIndicatorsVisible

Parallel lezen

Mogelijkheden: Input

ProximityPromptService.MaxIndicatorsVisible :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MaxPromptsVisible

Parallel lezen

Mogelijkheden: Input

ProximityPromptService.MaxPromptsVisible :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Evenementen

IndicatorHidden

Mogelijkheden: Input

ProximityPromptService.IndicatorHidden (prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |

Feedback geven

---

IndicatorShown

Mogelijkheden: Input

ProximityPromptService.IndicatorShown (prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |

Feedback geven

---

PromptButtonHoldBegan

Mogelijkheden: Input

ProximityPromptService.PromptButtonHoldBegan (

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Feedback geven

---

PromptButtonHoldEnded

Mogelijkheden: Input

ProximityPromptService.PromptButtonHoldEnded (

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Feedback geven

---

PromptHidden

Mogelijkheden: Input

ProximityPromptService.PromptHidden (prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |

Feedback geven

---

PromptShown

Mogelijkheden: Input

ProximityPromptService.PromptShown (

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , inputType :[Enum.ProximityPromptInputType](/docs/nl-nl/reference/engine/enums/ProximityPromptInputType)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |
|

inputType :[Enum.ProximityPromptInputType](/docs/nl-nl/reference/engine/enums/ProximityPromptInputType)

 |

Feedback geven

---

PromptTriggered

Mogelijkheden: Input

ProximityPromptService.PromptTriggered (

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Feedback geven

---

PromptTriggerEnded

Mogelijkheden: Input

ProximityPromptService.PromptTriggerEnded (

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

prompt :[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)

 |
|

playerWhoTriggered :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Feedback geven

---

Ga naar

▼

ProximityPromptService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Enabled](#Enabled)

[MaxIndicatorsVisible](#MaxIndicatorsVisible)

[MaxPromptsVisible](#MaxPromptsVisible)

[Evenementen](#events)

[IndicatorHidden](#IndicatorHidden)

[IndicatorShown](#IndicatorShown)

[PromptButtonHoldBegan](#PromptButtonHoldBegan)

[PromptButtonHoldEnded](#PromptButtonHoldEnded)

[PromptHidden](#PromptHidden)

[PromptShown](#PromptShown)

[PromptTriggered](#PromptTriggered)

[PromptTriggerEnded](#PromptTriggerEnded)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
