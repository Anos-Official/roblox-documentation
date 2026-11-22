<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Controller -->

Controller | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Controller.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Controller](/docs/reference/engine/classes/Controller)

English

Feedback

Engine Class

Controller

Not Creatable

---

## Summary

Methods

|

[BindButton](#BindButton) (button :  [Enum.Button](/docs/reference/engine/enums/Button) , caption :  [string](/docs/luau/strings) ) : ()

 |
| --- | --- |
|

[bindButton](#bindButton) (button :  [Enum.Button](/docs/reference/engine/enums/Button) , caption :  [string](/docs/luau/strings) ) : ()

Deprecated

 |
|

[GetButton](#GetButton) (button :  [Enum.Button](/docs/reference/engine/enums/Button) ) :[boolean](/docs/luau/booleans)

 |
|

[getButton](#getButton) (button :  [Enum.Button](/docs/reference/engine/enums/Button) ) :[boolean](/docs/luau/booleans)

Deprecated

 |
|

[UnbindButton](#UnbindButton) (button :  [Enum.Button](/docs/reference/engine/enums/Button) ) : ()

 |

Events

|

[ButtonChanged](#ButtonChanged) (button :  [Enum.Button](/docs/reference/engine/enums/Button) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[HumanoidController](/docs/reference/engine/classes/HumanoidController) , [SkateboardController](/docs/reference/engine/classes/SkateboardController) , [VehicleController](/docs/reference/engine/classes/VehicleController)

---

API Reference

Methods

BindButton

Controller:BindButton (

button :[Enum.Button](/docs/reference/engine/enums/Button) , caption :[string](/docs/luau/strings)

) : ()

Parameters

|

button :[Enum.Button](/docs/reference/engine/enums/Button)

 |
|

caption :[string](/docs/luau/strings)

 |

Returns

()

Code Samples

Controller:BindButton1

```

local ControllerService = game:GetService("ControllerService")

local humanoidController = ControllerService:FindFirstChildOfClass("HumanoidController")

humanoidController:BindButton(Enum.Button.Dismount, "win!")

```

Provide feedback

---

bindButton

Deprecated

Show details

---

GetButton

Controller:GetButton (button :[Enum.Button](/docs/reference/engine/enums/Button) ) :[boolean](/docs/luau/booleans)

Parameters

|

button :[Enum.Button](/docs/reference/engine/enums/Button)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

getButton

Deprecated

Show details

---

UnbindButton

Controller:UnbindButton (button :[Enum.Button](/docs/reference/engine/enums/Button) ) : ()

Parameters

|

button :[Enum.Button](/docs/reference/engine/enums/Button)

 |

Returns

()

Provide feedback

---

Events

ButtonChanged

Controller.ButtonChanged (button :[Enum.Button](/docs/reference/engine/enums/Button) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

button :[Enum.Button](/docs/reference/engine/enums/Button)

 |

Provide feedback

---

Jump to

▼

Controller

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[BindButton()](#BindButton)

[bindButton()](#bindButton)

[GetButton()](#GetButton)

[getButton()](#getButton)

[UnbindButton()](#UnbindButton)

[Events](#events)

[ButtonChanged](#ButtonChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
