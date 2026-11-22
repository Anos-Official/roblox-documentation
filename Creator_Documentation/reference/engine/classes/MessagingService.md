<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/MessagingService -->

MessagingService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/MessagingService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [MessagingService](/docs/en-us/reference/engine/classes/MessagingService)

English

Feedback

Engine Class

MessagingService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[PublishAsync](#PublishAsync) (topic :  [string](/docs/en-us/luau/strings) , message :  Variant ) : ()

 |
| --- | --- |
|

[SubscribeAsync](#SubscribeAsync) (topic :  [string](/docs/en-us/luau/strings) , callback :  [function](/docs/en-us/luau/functions) ) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

PublishAsync

Yields

Capabilities: ServerCommunication

Cloud API

MessagingService:PublishAsync (

topic :[string](/docs/en-us/luau/strings) , message : Variant

) : ()

Parameters

|

topic :[string](/docs/en-us/luau/strings)

 |
|

message : Variant

 |

Returns

()

Provide feedback

---

SubscribeAsync

Yields

Capabilities: ServerCommunication

MessagingService:SubscribeAsync (

topic :[string](/docs/en-us/luau/strings) , callback :[function](/docs/en-us/luau/functions)

) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

topic :[string](/docs/en-us/luau/strings)

 |
|

callback :[function](/docs/en-us/luau/functions)

 |

Returns

[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Code Samples

Subscribing to Cross Server Messages

```

local MessagingService = game:GetService("MessagingService")

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	--subscribe to the topic

	local topic = "player-" .. player.UserId

	local connection = MessagingService:SubscribeAsync(topic, function(message)

		print("Received message for", player.Name, message.Data)

	end)

	player.AncestryChanged:Connect(function()

		-- unsubscribe from the topic

		connection:Disconnect()

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Provide feedback

---

Jump to

▼

MessagingService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[PublishAsync()](#PublishAsync)

[SubscribeAsync()](#SubscribeAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
