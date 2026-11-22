<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/CFrameValue -->

CFrameValue | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/nl-nl/reference/engine/classes/ValueBase)
8. /
9. [CFrameValue](/docs/nl-nl/reference/engine/classes/CFrameValue)

Nederlands

Feedback

Engine-klasse

CFrameValue

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/CFrameValue)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
| --- | --- |

Evenementen

|

[Changed](#Changed) (value :  [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Bewaar de CFrame van de Camera

```

-- Maak een CFrame aan die de huidige positie/oriëntatie van de camera opslaat

local vSnapshot = Instance.new("CFrameValue")

vSnapshot.Value = workspace.CurrentCamera.CFrame

vSnapshot.Name = "Snapshot"

vSnapshot.Parent = workspace

-- Later kunnen we de CFrame weer in de camera laden

workspace.CurrentCamera.CFrame = vSnapshot.Value

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Toegang tot simulatie

CFrameValue.Value :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

Evenementen

Changed

CFrameValue.Changed (value :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |

Codevoorbeelden

CFrameValue.Changed

```

local cframeValue = script.Parent.CFrameValue

cframeValue.Changed:Connect(print)

cframeValue.Value = CFrame.new(1, 2, 3)

```

Feedback geven

---

changed

Verouderd

Details weergeven

---

Ga naar

▼

CFrameValue

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Value](#Value)

[Evenementen](#events)

[Changed](#Changed)

[changed](#changed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
