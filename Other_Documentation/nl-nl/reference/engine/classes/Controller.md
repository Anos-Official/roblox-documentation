<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Controller -->

Controller | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Controller](/docs/nl-nl/reference/engine/classes/Controller)

Nederlands

Feedback

Engine-klasse

Controller

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Controller)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[BindButton](#BindButton) (button :  [Enum.Button](/docs/nl-nl/reference/engine/enums/Button) , caption :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
| --- | --- |
|

[bindButton](#bindButton) (button :  [Enum.Button](/docs/nl-nl/reference/engine/enums/Button) , caption :  [string](/docs/nl-nl/luau/strings) ) : ()

Verouderd

 |
|

[GetButton](#GetButton) (button :  [Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[getButton](#getButton) (button :  [Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[UnbindButton](#UnbindButton) (button :  [Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) : ()

 |

Evenementen

|

[ButtonChanged](#ButtonChanged) (button :  [Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[HumanoidController](/docs/nl-nl/reference/engine/classes/HumanoidController) , [SkateboardController](/docs/nl-nl/reference/engine/classes/SkateboardController) , [VehicleController](/docs/nl-nl/reference/engine/classes/VehicleController)

---

API-referentie

Methoden

BindButton

Controller:BindButton (

button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button) , caption :[string](/docs/nl-nl/luau/strings)

) : ()

Parameters

|

button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button)

 |
|

caption :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Codevoorbeelden

Controller:BindButton1

```

local ControllerService = game:GetService("ControllerService")

local humanoidController = ControllerService:FindFirstChildOfClass("HumanoidController")

humanoidController:BindButton(Enum.Button.Dismount, "win!")

```

Feedback geven

---

bindButton

Verouderd

Details weergeven

---

GetButton

Controller:GetButton (button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

getButton

Verouderd

Details weergeven

---

UnbindButton

Controller:UnbindButton (button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) : ()

Parameters

|

button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button)

 |

Teruggaves

()

Feedback geven

---

Evenementen

ButtonChanged

Controller.ButtonChanged (button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

button :[Enum.Button](/docs/nl-nl/reference/engine/enums/Button)

 |

Feedback geven

---

Ga naar

▼

Controller

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[BindButton()](#BindButton)

[bindButton()](#bindButton)

[GetButton()](#GetButton)

[getButton()](#getButton)

[UnbindButton()](#UnbindButton)

[Evenementen](#events)

[ButtonChanged](#ButtonChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
