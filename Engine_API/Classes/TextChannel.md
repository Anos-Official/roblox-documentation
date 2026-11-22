<!-- Source: https://create.roblox.com/docs/reference/engine/classes/TextChannel -->

TextChannel | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TextChannel.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [TextChannel](/docs/reference/engine/classes/TextChannel)

English

Feedback

Engine Class

TextChannel

---

## Summary

Properties

|

[DirectChatRequester](#DirectChatRequester) :[Player](/docs/reference/engine/classes/Player)

 |
| --- | --- |

Methods

|

[AddUserAsync](#AddUserAsync) (userId :  [User](/docs/reference/engine/datatypes/User) ) :[Tuple](/docs/luau/tuples)

 |
|

[DisplaySystemMessage](#DisplaySystemMessage) (systemMessage :  [string](/docs/luau/strings) , metadata :  [string](/docs/luau/strings) ) :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

 |
|

[SendAsync](#SendAsync) (message :  [string](/docs/luau/strings) , metadata :  [string](/docs/luau/strings) ) :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

 |
|

[SetDirectChatRequester](#SetDirectChatRequester) (requester :  [Player](/docs/reference/engine/classes/Player) ) : ()

 |

Events

|

[MessageReceived](#MessageReceived) (incomingMessage :  [TextChatMessage](/docs/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Callbacks

|

[OnIncomingMessage](#OnIncomingMessage) (message :  [TextChatMessage](/docs/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/luau/tuples)

 |
|

[ShouldDeliverCallback](#ShouldDeliverCallback) (message :  [TextChatMessage](/docs/reference/engine/classes/TextChatMessage) , textSource :  [TextSource](/docs/reference/engine/classes/TextSource) ) :[Tuple](/docs/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

DirectChatRequester

Read Only

Not Replicated

Read Parallel

Capabilities: Chat

TextChannel.DirectChatRequester :[Player](/docs/reference/engine/classes/Player)

Provide feedback

---

Methods

AddUserAsync

Yields

Capabilities: Chat

TextChannel:AddUserAsync (userId :[User](/docs/reference/engine/datatypes/User) ) :[Tuple](/docs/luau/tuples)

Parameters

|

userId :[User](/docs/reference/engine/datatypes/User)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

DisplaySystemMessage

Capabilities: Chat

TextChannel:DisplaySystemMessage (

systemMessage :[string](/docs/luau/strings) , metadata :[string](/docs/luau/strings)

) :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

Parameters

|

systemMessage :[string](/docs/luau/strings)

 |
|

metadata :[string](/docs/luau/strings)

 |

Returns

[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

Provide feedback

---

SendAsync

Yields

Capabilities: Chat

TextChannel:SendAsync (

message :[string](/docs/luau/strings) , metadata :[string](/docs/luau/strings)

) :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

Parameters

|

message :[string](/docs/luau/strings)

 |
|

metadata :[string](/docs/luau/strings)

 |

Returns

[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

Provide feedback

---

SetDirectChatRequester

Capabilities: Chat

TextChannel:SetDirectChatRequester (requester :[Player](/docs/reference/engine/classes/Player) ) : ()

Parameters

|

requester :[Player](/docs/reference/engine/classes/Player)

 |

Returns

()

Code Samples

Set Direct Chat Requester

```

local function createWhisperChannel(fromPlayer, toPlayer)

  local whisperChannel = Instance.new("TextChannel")

  whisperChannel:SetDirectChatRequester(fromPlayer)

  whisperChannel:AddUserAsync(toPlayer.UserId)

  -- The TextChannel instance now has two TextSource instances.

  return whisperChannel

end

```

Provide feedback

---

Events

MessageReceived

Capabilities: Chat

TextChannel.MessageReceived (incomingMessage :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

incomingMessage :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

 |

Provide feedback

---

Callbacks

OnIncomingMessage

Capabilities: Chat

TextChannel.OnIncomingMessage (message :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

ShouldDeliverCallback

Capabilities: Chat

TextChannel.ShouldDeliverCallback (

message :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage) , textSource :[TextSource](/docs/reference/engine/classes/TextSource)

) :[Tuple](/docs/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/reference/engine/classes/TextChatMessage)

 |
|

textSource :[TextSource](/docs/reference/engine/classes/TextSource)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

Jump to

▼

TextChannel

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Callbacks](#summary-callbacks)

[Properties](#properties)

[DirectChatRequester](#DirectChatRequester)

[Methods](#methods)

[AddUserAsync()](#AddUserAsync)

[DisplaySystemMessage()](#DisplaySystemMessage)

[SendAsync()](#SendAsync)

[SetDirectChatRequester()](#SetDirectChatRequester)

[Events](#events)

[MessageReceived](#MessageReceived)

[Callbacks](#callbacks)

[OnIncomingMessage()](#OnIncomingMessage)

[ShouldDeliverCallback()](#ShouldDeliverCallback)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
