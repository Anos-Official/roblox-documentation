<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Chat -->

Chat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Chat.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Chat](/docs/reference/engine/classes/Chat)

English

Feedback

Engine Class

Chat

Deprecated

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[BubbleChatEnabled](#BubbleChatEnabled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[LoadDefaultChat](#LoadDefaultChat) :[boolean](/docs/luau/booleans)

 |

Methods

|

[CanUserChatAsync](#CanUserChatAsync) (userId :  [number](/docs/luau/numbers) ) :[boolean](/docs/luau/booleans)

 |
|

[CanUsersChatAsync](#CanUsersChatAsync) (userIdFrom :  [number](/docs/luau/numbers) , userIdTo :  [number](/docs/luau/numbers) ) :[boolean](/docs/luau/booleans)

 |
|

[Chat](#Chat) (partOrCharacter :  [Instance](/docs/reference/engine/datatypes/Instance) , message :  [string](/docs/luau/strings) , color :  [Enum.ChatColor](/docs/reference/engine/enums/ChatColor) ) : ()

 |
|

[FilterStringAsync](#FilterStringAsync) (stringToFilter :  [string](/docs/luau/strings) , playerFrom :  [Player](/docs/reference/engine/classes/Player) , playerTo :  [Player](/docs/reference/engine/classes/Player) ) :[string](/docs/luau/strings)

 |
|

[FilterStringForBroadcast](#FilterStringForBroadcast) (stringToFilter :  [string](/docs/luau/strings) , playerFrom :  [Player](/docs/reference/engine/classes/Player) ) :[string](/docs/luau/strings)

 |
|

[FilterStringForPlayerAsync](#FilterStringForPlayerAsync) (stringToFilter :  [string](/docs/luau/strings) , playerToFilterFor :  [Player](/docs/reference/engine/classes/Player) ) :[string](/docs/luau/strings)

Deprecated

 |
|

[InvokeChatCallback](#InvokeChatCallback) (callbackType :  [Enum.ChatCallbackType](/docs/reference/engine/enums/ChatCallbackType) , callbackArguments :  [Tuple](/docs/luau/tuples) ) :[Tuple](/docs/luau/tuples)

 |
|

[RegisterChatCallback](#RegisterChatCallback) (callbackType :  [Enum.ChatCallbackType](/docs/reference/engine/enums/ChatCallbackType) , callbackFunction :  [function](/docs/luau/functions) ) : ()

 |
|

[SetBubbleChatSettings](#SetBubbleChatSettings) (settings :  Variant ) : ()

 |

Events

|

[Chatted](#Chatted) (part :  [Instance](/docs/reference/engine/datatypes/Instance) , message :  [string](/docs/luau/strings) , color :  [Enum.ChatColor](/docs/reference/engine/enums/ChatColor) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

BubbleChatEnabled

Read Parallel

Capabilities: Chat

Chat.BubbleChatEnabled :[boolean](/docs/luau/booleans)

Provide feedback

---

LoadDefaultChat

Read Parallel

Capabilities: Chat

Chat.LoadDefaultChat :[boolean](/docs/luau/booleans)

Provide feedback

---

Methods

CanUserChatAsync

Yields

Capabilities: Chat

Chat:CanUserChatAsync (userId :[number](/docs/luau/numbers) ) :[boolean](/docs/luau/booleans)

Parameters

|

userId :[number](/docs/luau/numbers)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

CanUsersChatAsync

Yields

Capabilities: Chat

Chat:CanUsersChatAsync (

userIdFrom :[number](/docs/luau/numbers) , userIdTo :[number](/docs/luau/numbers)

) :[boolean](/docs/luau/booleans)

Parameters

|

userIdFrom :[number](/docs/luau/numbers)

 |
|

userIdTo :[number](/docs/luau/numbers)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

Chat

Capabilities: Chat

Chat:Chat (

partOrCharacter :[Instance](/docs/reference/engine/datatypes/Instance) , message :[string](/docs/luau/strings) , color :[Enum.ChatColor](/docs/reference/engine/enums/ChatColor)

) : ()

Parameters

|

partOrCharacter :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

message :[string](/docs/luau/strings)

 |
|

color :[Enum.ChatColor](/docs/reference/engine/enums/ChatColor)

Default Value: Blue |

Returns

()

Code Samples

Chat:Chat

```

local ChatService = game:GetService("Chat")

local part = Instance.new("Part")

part.Anchored = true

part.Parent = workspace

ChatService:Chat(part, "Blame John!", "Red")

```

Provide feedback

---

FilterStringAsync

Yields

Capabilities: Chat

Chat:FilterStringAsync (

stringToFilter :[string](/docs/luau/strings) , playerFrom :[Player](/docs/reference/engine/classes/Player) , playerTo :[Player](/docs/reference/engine/classes/Player)

) :[string](/docs/luau/strings)

Parameters

|

stringToFilter :[string](/docs/luau/strings)

 |
|

playerFrom :[Player](/docs/reference/engine/classes/Player)

 |
|

playerTo :[Player](/docs/reference/engine/classes/Player)

 |

Returns

[string](/docs/luau/strings)

Provide feedback

---

FilterStringForBroadcast

Yields

Capabilities: Chat

Chat:FilterStringForBroadcast (

stringToFilter :[string](/docs/luau/strings) , playerFrom :[Player](/docs/reference/engine/classes/Player)

) :[string](/docs/luau/strings)

Parameters

|

stringToFilter :[string](/docs/luau/strings)

 |
|

playerFrom :[Player](/docs/reference/engine/classes/Player)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Chat:FilterStringForBroadcast

```

local Players = game:GetService("Players")

local Chat = game:GetService("Chat")

local playerFrom = Players.LocalPlayer

local message = "Hello world!"

-- Filter the string and store the result in the 'FilteredString' variable

local filteredString = Chat:FilterStringForBroadcast(message, playerFrom)

print(filteredString)

```

Provide feedback

---

FilterStringForPlayerAsync

Deprecated

Show details

---

InvokeChatCallback

Capabilities: Chat

Chat:InvokeChatCallback (

callbackType :[Enum.ChatCallbackType](/docs/reference/engine/enums/ChatCallbackType) , callbackArguments :[Tuple](/docs/luau/tuples)

) :[Tuple](/docs/luau/tuples)

Parameters

|

callbackType :[Enum.ChatCallbackType](/docs/reference/engine/enums/ChatCallbackType)

 |
|

callbackArguments :[Tuple](/docs/luau/tuples)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

RegisterChatCallback

Capabilities: Chat

Chat:RegisterChatCallback (

callbackType :[Enum.ChatCallbackType](/docs/reference/engine/enums/ChatCallbackType) , callbackFunction :[function](/docs/luau/functions)

) : ()

Parameters

|

callbackType :[Enum.ChatCallbackType](/docs/reference/engine/enums/ChatCallbackType)

 |
|

callbackFunction :[function](/docs/luau/functions)

 |

Returns

()

Provide feedback

---

SetBubbleChatSettings

Capabilities: Chat

Chat:SetBubbleChatSettings (settings : Variant ) : ()

Parameters

|

settings : Variant

 |

Returns

()

Code Samples

Customize visual aspects

```

local ChatService = game:GetService("Chat")

ChatService:SetBubbleChatSettings({

	BackgroundColor3 = Color3.fromRGB(180, 210, 228),

	TextSize = 20,

	Font = Enum.Font.Cartoon,

})

```

Restore default settings

```

local ChatService = game:GetService("Chat")

ChatService:SetBubbleChatSettings({})

```

Provide feedback

---

Events

Chatted

Capabilities: Chat

Chat.Chatted (

part :[Instance](/docs/reference/engine/datatypes/Instance) , message :[string](/docs/luau/strings) , color :[Enum.ChatColor](/docs/reference/engine/enums/ChatColor)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

part :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

message :[string](/docs/luau/strings)

 |
|

color :[Enum.ChatColor](/docs/reference/engine/enums/ChatColor)

 |

Provide feedback

---

Jump to

▼

Chat

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[BubbleChatEnabled](#BubbleChatEnabled)

[LoadDefaultChat](#LoadDefaultChat)

[Methods](#methods)

[CanUserChatAsync()](#CanUserChatAsync)

[CanUsersChatAsync()](#CanUsersChatAsync)

[Chat()](#Chat)

[FilterStringAsync()](#FilterStringAsync)

[FilterStringForBroadcast()](#FilterStringForBroadcast)

[FilterStringForPlayerAsync()](#FilterStringForPlayerAsync)

[InvokeChatCallback()](#InvokeChatCallback)

[RegisterChatCallback()](#RegisterChatCallback)

[SetBubbleChatSettings()](#SetBubbleChatSettings)

[Events](#events)

[Chatted](#Chatted)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
