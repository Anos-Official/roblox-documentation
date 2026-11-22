<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioDeviceInput -->

AudioDeviceInput | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioDeviceInput.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioDeviceInput](/docs/en-us/reference/engine/classes/AudioDeviceInput)

English

Feedback

Engine Class

AudioDeviceInput

---

## Summary

Properties

|

[AccessType](#AccessType) :[Enum.AccessModifierType](/docs/en-us/reference/engine/enums/AccessModifierType)

 |
| --- | --- |
|

[Active](#Active) :[boolean](/docs/en-us/luau/booleans)

 |
|

[IsReady](#IsReady) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Muted](#Muted) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Player](#Player) :[Player](/docs/en-us/reference/engine/classes/Player)

 |
|

[Volume](#Volume) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetUserIdAccessList](#GetUserIdAccessList) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[SetUserIdAccessList](#SetUserIdAccessList) (userIds :  [{any}](/docs/en-us/luau/tables#arrays) ) : ()

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

AccessType

Read Parallel

Capabilities: Audio, Input

AudioDeviceInput.AccessType :[Enum.AccessModifierType](/docs/en-us/reference/engine/enums/AccessModifierType)

Provide feedback

---

Active

Roblox Script Security

Read Parallel

Capabilities: Audio, Input

AudioDeviceInput.Active :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

IsReady

Read Only

Not Replicated

Roblox Script Security

Read Parallel

Capabilities: Audio, Input

AudioDeviceInput.IsReady :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Muted

Read Parallel

Capabilities: Audio, Input

AudioDeviceInput.Muted :[boolean](/docs/en-us/luau/booleans)

Code Samples

Push-to-talk

```

local players = game:GetService("Players")

local userInput = game:GetService("UserInputService")

local audioIn: AudioDeviceInput = players.LocalPlayer:WaitForChild("AudioDeviceInput")

audioIn.Muted = true

local pushToTalkKey = Enum.KeyCode.V

userInput.InputBegan:Connect(function(input: InputObject)

	if input.KeyCode == pushToTalkKey then

		audioIn.Muted = false

	end

end)

userInput.InputEnded:Connect(function(input: InputObject)

	if input.KeyCode == pushToTalkKey then

		audioIn.Muted = true

	end

end)

```

Provide feedback

---

Player

Read Parallel

Capabilities: Audio, Input, Players

AudioDeviceInput.Player :[Player](/docs/en-us/reference/engine/classes/Player)

Provide feedback

---

Volume

Read Parallel

Capabilities: Audio, Input

AudioDeviceInput.Volume :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio, Input

AudioDeviceInput:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/en-us/luau/strings)

 |

Returns

{[Wire](/docs/en-us/reference/engine/classes/Wire) }

Provide feedback

---

GetInputPins

Capabilities: Audio, Input

AudioDeviceInput:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio, Input

AudioDeviceInput:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetUserIdAccessList

Capabilities: Audio, Input

AudioDeviceInput:GetUserIdAccessList () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

SetUserIdAccessList

Capabilities: Audio, Input

AudioDeviceInput:SetUserIdAccessList (userIds :[{any}](/docs/en-us/luau/tables#arrays) ) : ()

Parameters

|

userIds :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

()

Provide feedback

---

Events

WiringChanged

Capabilities: Audio, Input

AudioDeviceInput.WiringChanged (

connected :[boolean](/docs/en-us/luau/booleans) , pin :[string](/docs/en-us/luau/strings) , wire :[Wire](/docs/en-us/reference/engine/classes/Wire) , instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/en-us/luau/booleans)

 |
|

pin :[string](/docs/en-us/luau/strings)

 |
|

wire :[Wire](/docs/en-us/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

AudioDeviceInput

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AccessType](#AccessType)

[Active](#Active)

[IsReady](#IsReady)

[Muted](#Muted)

[Player](#Player)

[Volume](#Volume)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetUserIdAccessList()](#GetUserIdAccessList)

[SetUserIdAccessList()](#SetUserIdAccessList)

[Events](#events)

[WiringChanged](#WiringChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
