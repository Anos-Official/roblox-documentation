<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/LogService -->

LogService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/LogService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [LogService](/docs/en-us/reference/engine/classes/LogService)

English

Feedback

Engine Class

LogService

Not Creatable

Service

---

## Summary

Methods

|

[ClearOutput](#ClearOutput) () : ()

 |
| --- | --- |
|

[Error](#Error) (message :  [string](/docs/en-us/luau/strings) , context :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[GetLogHistory](#GetLogHistory) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetLogHistoryAsync](#GetLogHistoryAsync) (user :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetLogger](#GetLogger) (name :  [string](/docs/en-us/luau/strings) ) :[Logger](/docs/en-us/reference/engine/classes/Logger)

 |
|

[Info](#Info) (message :  [string](/docs/en-us/luau/strings) , context :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[Log](#Log) (messageType :  [Enum.MessageType](/docs/en-us/reference/engine/enums/MessageType) , message :  [string](/docs/en-us/luau/strings) , context :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[Output](#Output) (message :  [string](/docs/en-us/luau/strings) , context :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[Warn](#Warn) (message :  [string](/docs/en-us/luau/strings) , context :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |

Events

|

[MessageOut](#MessageOut) (message :  [string](/docs/en-us/luau/strings) , messageType :  [Enum.MessageType](/docs/en-us/reference/engine/enums/MessageType) , context :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

ClearOutput

Capabilities: Logging

LogService:ClearOutput () : ()

Returns

()

Provide feedback

---

Error

Capabilities: Logging

LogService:Error (

message :[string](/docs/en-us/luau/strings) , context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/en-us/luau/strings)

 |
|

context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Provide feedback

---

GetLogHistory

Capabilities: Logging

LogService:GetLogHistory () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetLogHistoryAsync

Yields

Capabilities: Logging

LogService:GetLogHistoryAsync (user :[User](/docs/en-us/reference/engine/datatypes/User) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

user :[User](/docs/en-us/reference/engine/datatypes/User)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetLogger

Capabilities: Logging

LogService:GetLogger (name :[string](/docs/en-us/luau/strings) ) :[Logger](/docs/en-us/reference/engine/classes/Logger)

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |

Returns

[Logger](/docs/en-us/reference/engine/classes/Logger)

Provide feedback

---

Info

Capabilities: Logging

LogService:Info (

message :[string](/docs/en-us/luau/strings) , context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/en-us/luau/strings)

 |
|

context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Provide feedback

---

Log

Capabilities: Logging

LogService:Log (

messageType :[Enum.MessageType](/docs/en-us/reference/engine/enums/MessageType) , message :[string](/docs/en-us/luau/strings) , context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

messageType :[Enum.MessageType](/docs/en-us/reference/engine/enums/MessageType)

 |
|

message :[string](/docs/en-us/luau/strings)

 |
|

context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Provide feedback

---

Output

Capabilities: Logging

LogService:Output (

message :[string](/docs/en-us/luau/strings) , context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/en-us/luau/strings)

 |
|

context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Provide feedback

---

Warn

Capabilities: Logging

LogService:Warn (

message :[string](/docs/en-us/luau/strings) , context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/en-us/luau/strings)

 |
|

context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Provide feedback

---

Events

MessageOut

Capabilities: Logging

LogService.MessageOut (

message :[string](/docs/en-us/luau/strings) , messageType :[Enum.MessageType](/docs/en-us/reference/engine/enums/MessageType) , context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

message :[string](/docs/en-us/luau/strings)

 |
|

messageType :[Enum.MessageType](/docs/en-us/reference/engine/enums/MessageType)

 |
|

context :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Code Samples

LogService.MessageOut

```

local LogService = game:GetService("LogService")

local messageLabel = Instance.new("Message")

messageLabel.Parent = workspace

local function onMessageOut(message, messageType)

	messageLabel.Text = "The message was " .. message .. " and the type was " .. tostring(messageType)

end

LogService.MessageOut:Connect(onMessageOut)

```

Provide feedback

---

Jump to

▼

LogService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[ClearOutput()](#ClearOutput)

[Error()](#Error)

[GetLogHistory()](#GetLogHistory)

[GetLogHistoryAsync()](#GetLogHistoryAsync)

[GetLogger()](#GetLogger)

[Info()](#Info)

[Log()](#Log)

[Output()](#Output)

[Warn()](#Warn)

[Events](#events)

[MessageOut](#MessageOut)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
