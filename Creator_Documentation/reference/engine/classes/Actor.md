<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Actor -->

Actor | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Actor.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/en-us/reference/engine/classes/PVInstance)
8. /
9. [Model](/docs/en-us/reference/engine/classes/Model)
10. /
11. [Actor](/docs/en-us/reference/engine/classes/Actor)

English

Feedback

Engine Class

Actor

---

## Summary

Methods

|

[BindToMessage](#BindToMessage) (topic :  [string](/docs/en-us/luau/strings) , function :  [function](/docs/en-us/luau/functions) ) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

 |
| --- | --- |
|

[BindToMessageParallel](#BindToMessageParallel) (topic :  [string](/docs/en-us/luau/strings) , function :  [function](/docs/en-us/luau/functions) ) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

 |
|

[SendMessage](#SendMessage) (topic :  [string](/docs/en-us/luau/strings) , message :  [Tuple](/docs/en-us/luau/tuples) ) : ()

 |

Inherited Members

26  inherited from [Model](/docs/en-us/reference/engine/classes/Model)

4  inherited from [PVInstance](/docs/en-us/reference/engine/classes/PVInstance)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

BindToMessage

Write Parallel

Capabilities: Basic

Actor:BindToMessage (

topic :[string](/docs/en-us/luau/strings) , function :[function](/docs/en-us/luau/functions)

) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

topic :[string](/docs/en-us/luau/strings)

 |
|

function :[function](/docs/en-us/luau/functions)

 |

Returns

[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Code Samples

Bind To Message

```

local actor = script:GetActor()

-- Print out a message when a greeting message is sent to the Actor

-- this script is a descendant of.

local connection = actor:BindToMessage("Greeting", function(message)

  print("Received Greeting Message:", message)

end)

```

Provide feedback

---

BindToMessageParallel

Write Parallel

Capabilities: Basic

Actor:BindToMessageParallel (

topic :[string](/docs/en-us/luau/strings) , function :[function](/docs/en-us/luau/functions)

) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

topic :[string](/docs/en-us/luau/strings)

 |
|

function :[function](/docs/en-us/luau/functions)

 |

Returns

[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Code Samples

Bind To Message Parallel

```

local actor = script:GetActor()

-- Print out a message when a greeting message is sent to the Actor

-- this script is a descendant of.

local connection = actor:BindToMessageParallel("Greeting", function(message)

  print("Received Greeting Message:", message)

end)

```

Provide feedback

---

SendMessage

Write Parallel

Capabilities: Basic

Actor:SendMessage (

topic :[string](/docs/en-us/luau/strings) , message :[Tuple](/docs/en-us/luau/tuples)

) : ()

Parameters

|

topic :[string](/docs/en-us/luau/strings)

 |
|

message :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

()

Code Samples

Send Message

```

local actor = script:GetActor()

actor:SendMessage("Greeting", "Hello World")

```

Provide feedback

---

Jump to

▼

Actor

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[BindToMessage()](#BindToMessage)

[BindToMessageParallel()](#BindToMessageParallel)

[SendMessage()](#SendMessage)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
