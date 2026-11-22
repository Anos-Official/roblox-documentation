<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TextChannel -->

TextChannel | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)

Nederlands

Feedback

Engine-klasse

TextChannel

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TextChannel)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[DirectChatRequester](#DirectChatRequester) :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |
| --- | --- |

Methoden

|

[AddUserAsync](#AddUserAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[DisplaySystemMessage](#DisplaySystemMessage) (systemMessage :  [string](/docs/nl-nl/luau/strings) , metadata :  [string](/docs/nl-nl/luau/strings) ) :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |
|

[SendAsync](#SendAsync) (message :  [string](/docs/nl-nl/luau/strings) , metadata :  [string](/docs/nl-nl/luau/strings) ) :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |
|

[SetDirectChatRequester](#SetDirectChatRequester) (requester :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) : ()

 |

Evenementen

|

[MessageReceived](#MessageReceived) (incomingMessage :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Callbacks

|

[OnIncomingMessage](#OnIncomingMessage) (message :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[ShouldDeliverCallback](#ShouldDeliverCallback) (message :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) , textSource :  [TextSource](/docs/nl-nl/reference/engine/classes/TextSource) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

DirectChatRequester

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Chat

TextChannel.DirectChatRequester :[Player](/docs/nl-nl/reference/engine/classes/Player)

Feedback geven

---

Methoden

AddUserAsync

Opbrengst

Mogelijkheden: Chat

TextChannel:AddUserAsync (userId :[User](/docs/nl-nl/reference/engine/datatypes/User) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

DisplaySystemMessage

Mogelijkheden: Chat

TextChannel:DisplaySystemMessage (

systemMessage :[string](/docs/nl-nl/luau/strings) , metadata :[string](/docs/nl-nl/luau/strings)

) :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

Parameters

|

systemMessage :[string](/docs/nl-nl/luau/strings)

 |
|

metadata :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

Feedback geven

---

SendAsync

Opbrengst

Mogelijkheden: Chat

TextChannel:SendAsync (

message :[string](/docs/nl-nl/luau/strings) , metadata :[string](/docs/nl-nl/luau/strings)

) :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

metadata :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

Feedback geven

---

SetDirectChatRequester

Mogelijkheden: Chat

TextChannel:SetDirectChatRequester (requester :[Player](/docs/nl-nl/reference/engine/classes/Player) ) : ()

Parameters

|

requester :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Teruggaves

()

Codevoorbeelden

Stel Directe Chat Aanvrager In

```

local function createWhisperChannel(fromPlayer, toPlayer)

  local whisperChannel = Instance.new("TextChannel")

  whisperChannel:SetDirectChatRequester(fromPlayer)

  whisperChannel:AddUserAsync(toPlayer.UserId)

  -- De TextChannel-instantie heeft nu twee TextSource-instanties.

  return whisperChannel

end

```

Feedback geven

---

Evenementen

MessageReceived

Mogelijkheden: Chat

TextChannel.MessageReceived (incomingMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

incomingMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Feedback geven

---

Callbacks

OnIncomingMessage

Mogelijkheden: Chat

TextChannel.OnIncomingMessage (message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

ShouldDeliverCallback

Mogelijkheden: Chat

TextChannel.ShouldDeliverCallback (

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) , textSource :[TextSource](/docs/nl-nl/reference/engine/classes/TextSource)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |
|

textSource :[TextSource](/docs/nl-nl/reference/engine/classes/TextSource)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

Ga naar

▼

TextChannel

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Callbacks](#summary-callbacks)

[Eigenschappen](#properties)

[DirectChatRequester](#DirectChatRequester)

[Methoden](#methods)

[AddUserAsync()](#AddUserAsync)

[DisplaySystemMessage()](#DisplaySystemMessage)

[SendAsync()](#SendAsync)

[SetDirectChatRequester()](#SetDirectChatRequester)

[Evenementen](#events)

[MessageReceived](#MessageReceived)

[Callbacks](#callbacks)

[OnIncomingMessage()](#OnIncomingMessage)

[ShouldDeliverCallback()](#ShouldDeliverCallback)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
