<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ServiceProvider -->

ServiceProvider | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ServiceProvider](/docs/nl-nl/reference/engine/classes/ServiceProvider)

Nederlands

Feedback

Engine-klasse

ServiceProvider

Niet maakbaar

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ServiceProvider)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[FindService](#FindService) (className :  [string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[GetService](#GetService) (className :  [string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[getService](#getService) (className :  [string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
|

[service](#service) (className :  [string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |

Evenementen

|

[Close](#Close) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[ServiceAdded](#ServiceAdded) (service :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[ServiceRemoving](#ServiceRemoving) (service :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[DataModel](/docs/nl-nl/reference/engine/classes/DataModel) , [GenericSettings](/docs/nl-nl/reference/engine/classes/GenericSettings)

---

API-referentie

Methoden

FindService

Parallel schrijven

ServiceProvider:FindService (className :[string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

ServiceProvider:FindService

```

print(game:FindService("Part"))

--> nil

print(game:FindService("Workspace"))

--> Werkruimte

```

Feedback geven

---

GetService

ServiceProvider:GetService (className :[string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

ServiceProvider:GetService

```

local BadgeService = game:GetService("BadgeService")

local GameSettings = UserSettings():GetService("UserGameSettings")

print(BadgeService)

print(GameSettings)

```

Feedback geven

---

getService

Verouderd

Details weergeven

---

service

Verouderd

Details weergeven

---

Evenementen

Close

ServiceProvider.Close () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

ServiceProvider.Close

```

local function onClose()

	print("De plaats sluit")

end

game.Close:Connect(onClose)

```

Feedback geven

---

ServiceAdded

ServiceProvider.ServiceAdded (service :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

service :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

ServiceRemoving

ServiceProvider.ServiceRemoving (service :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

service :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

Ga naar

▼

ServiceProvider

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[FindService()](#FindService)

[GetService()](#GetService)

[getService()](#getService)

[service()](#service)

[Evenementen](#events)

[Close](#Close)

[ServiceAdded](#ServiceAdded)

[ServiceRemoving](#ServiceRemoving)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
