<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ServiceProvider -->

ServiceProvider | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ServiceProvider.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ServiceProvider](/docs/reference/engine/classes/ServiceProvider)

English

Feedback

Engine Class

ServiceProvider

Not Creatable

Not Browsable

---

## Summary

Methods

|

[FindService](#FindService) (className :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[GetService](#GetService) (className :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[getService](#getService) (className :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Deprecated

 |
|

[service](#service) (className :  [string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Deprecated

 |

Events

|

[Close](#Close) () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[ServiceAdded](#ServiceAdded) (service :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[ServiceRemoving](#ServiceRemoving) (service :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[DataModel](/docs/reference/engine/classes/DataModel) , [GenericSettings](/docs/reference/engine/classes/GenericSettings)

---

API Reference

Methods

FindService

Write Parallel

ServiceProvider:FindService (className :[string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

className :[string](/docs/luau/strings)

 |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Code Samples

ServiceProvider:FindService

```

print(game:FindService("Part"))

--> nil

print(game:FindService("Workspace"))

--> Workspace

```

Provide feedback

---

GetService

ServiceProvider:GetService (className :[string](/docs/luau/strings) ) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

className :[string](/docs/luau/strings)

 |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Code Samples

ServiceProvider:GetService

```

local BadgeService = game:GetService("BadgeService")

local GameSettings = UserSettings():GetService("UserGameSettings")

print(BadgeService)

print(GameSettings)

```

Provide feedback

---

getService

Deprecated

Show details

---

service

Deprecated

Show details

---

Events

Close

ServiceProvider.Close () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Code Samples

ServiceProvider.Close

```

local function onClose()

	print("The place is closing")

end

game.Close:Connect(onClose)

```

Provide feedback

---

ServiceAdded

ServiceProvider.ServiceAdded (service :[Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

service :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Provide feedback

---

ServiceRemoving

ServiceProvider.ServiceRemoving (service :[Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

service :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

ServiceProvider

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[FindService()](#FindService)

[GetService()](#GetService)

[getService()](#getService)

[service()](#service)

[Events](#events)

[Close](#Close)

[ServiceAdded](#ServiceAdded)

[ServiceRemoving](#ServiceRemoving)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
