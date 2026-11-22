<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Chat -->

Chat | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Chat](/docs/nl-nl/reference/engine/classes/Chat)

Nederlands

Feedback

Engine-klasse

Chat

Verouderd

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Chat)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[BubbleChatEnabled](#BubbleChatEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[LoadDefaultChat](#LoadDefaultChat) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[CanUserChatAsync](#CanUserChatAsync) (userId :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CanUsersChatAsync](#CanUsersChatAsync) (userIdFrom :  [number](/docs/nl-nl/luau/numbers) , userIdTo :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Chat](#Chat) (partOrCharacter :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , message :  [string](/docs/nl-nl/luau/strings) , color :  [Enum.ChatColor](/docs/nl-nl/reference/engine/enums/ChatColor) ) : ()

 |
|

[FilterStringAsync](#FilterStringAsync) (stringToFilter :  [string](/docs/nl-nl/luau/strings) , playerFrom :  [Player](/docs/nl-nl/reference/engine/classes/Player) , playerTo :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[FilterStringForBroadcast](#FilterStringForBroadcast) (stringToFilter :  [string](/docs/nl-nl/luau/strings) , playerFrom :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[FilterStringForPlayerAsync](#FilterStringForPlayerAsync) (stringToFilter :  [string](/docs/nl-nl/luau/strings) , playerToFilterFor :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[string](/docs/nl-nl/luau/strings)

Verouderd

 |
|

[InvokeChatCallback](#InvokeChatCallback) (callbackType :  [Enum.ChatCallbackType](/docs/nl-nl/reference/engine/enums/ChatCallbackType) , callbackArguments :  [Tuple](/docs/nl-nl/luau/tuples) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[RegisterChatCallback](#RegisterChatCallback) (callbackType :  [Enum.ChatCallbackType](/docs/nl-nl/reference/engine/enums/ChatCallbackType) , callbackFunction :  [function](/docs/nl-nl/luau/functions) ) : ()

 |
|

[SetBubbleChatSettings](#SetBubbleChatSettings) (settings :  Variant ) : ()

 |

Evenementen

|

[Chatted](#Chatted) (part :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , message :  [string](/docs/nl-nl/luau/strings) , color :  [Enum.ChatColor](/docs/nl-nl/reference/engine/enums/ChatColor) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

BubbleChatEnabled

Parallel lezen

Mogelijkheden: Chat

Chat.BubbleChatEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

LoadDefaultChat

Parallel lezen

Mogelijkheden: Chat

Chat.LoadDefaultChat :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

CanUserChatAsync

Opbrengst

Mogelijkheden: Chat

Chat:CanUserChatAsync (userId :[number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CanUsersChatAsync

Opbrengst

Mogelijkheden: Chat

Chat:CanUsersChatAsync (

userIdFrom :[number](/docs/nl-nl/luau/numbers) , userIdTo :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userIdFrom :[number](/docs/nl-nl/luau/numbers)

 |
|

userIdTo :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Chat

Mogelijkheden: Chat

Chat:Chat (

partOrCharacter :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , message :[string](/docs/nl-nl/luau/strings) , color :[Enum.ChatColor](/docs/nl-nl/reference/engine/enums/ChatColor)

) : ()

Parameters

|

partOrCharacter :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

message :[string](/docs/nl-nl/luau/strings)

 |
|

color :[Enum.ChatColor](/docs/nl-nl/reference/engine/enums/ChatColor)

Standaardwaarde: Blue |

Teruggaves

()

Codevoorbeelden

Chat:Chat

```

local ChatService = game:GetService("Chat")

local part = Instance.new("Part")

part.Anchored = true

part.Parent = workspace

ChatService:Chat(part, "Geef John de schuld!", "Red")

```

Feedback geven

---

FilterStringAsync

Opbrengst

Mogelijkheden: Chat

Chat:FilterStringAsync (

stringToFilter :[string](/docs/nl-nl/luau/strings) , playerFrom :[Player](/docs/nl-nl/reference/engine/classes/Player) , playerTo :[Player](/docs/nl-nl/reference/engine/classes/Player)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

stringToFilter :[string](/docs/nl-nl/luau/strings)

 |
|

playerFrom :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |
|

playerTo :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

FilterStringForBroadcast

Opbrengst

Mogelijkheden: Chat

Chat:FilterStringForBroadcast (

stringToFilter :[string](/docs/nl-nl/luau/strings) , playerFrom :[Player](/docs/nl-nl/reference/engine/classes/Player)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

stringToFilter :[string](/docs/nl-nl/luau/strings)

 |
|

playerFrom :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Chat:FilterStringForBroadcast

```

local Players = game:GetService("Players")

local Chat = game:GetService("Chat")

local playerFrom = Players.LocalPlayer

local message = "Hallo wereld!"

-- Filter de string en sla het resultaat op in de 'FilteredString' variabele

local filteredString = Chat:FilterStringForBroadcast(message, playerFrom)

print(filteredString)

```

Feedback geven

---

FilterStringForPlayerAsync

Verouderd

Details weergeven

---

InvokeChatCallback

Mogelijkheden: Chat

Chat:InvokeChatCallback (

callbackType :[Enum.ChatCallbackType](/docs/nl-nl/reference/engine/enums/ChatCallbackType) , callbackArguments :[Tuple](/docs/nl-nl/luau/tuples)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

callbackType :[Enum.ChatCallbackType](/docs/nl-nl/reference/engine/enums/ChatCallbackType)

 |
|

callbackArguments :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

RegisterChatCallback

Mogelijkheden: Chat

Chat:RegisterChatCallback (

callbackType :[Enum.ChatCallbackType](/docs/nl-nl/reference/engine/enums/ChatCallbackType) , callbackFunction :[function](/docs/nl-nl/luau/functions)

) : ()

Parameters

|

callbackType :[Enum.ChatCallbackType](/docs/nl-nl/reference/engine/enums/ChatCallbackType)

 |
|

callbackFunction :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

()

Feedback geven

---

SetBubbleChatSettings

Mogelijkheden: Chat

Chat:SetBubbleChatSettings (settings : Variant ) : ()

Parameters

|

settings : Variant

 |

Teruggaves

()

Codevoorbeelden

Pas visuele aspecten aan

```

local ChatService = game:GetService("Chat")

ChatService:SetBubbleChatSettings({

	BackgroundColor3 = Color3.fromRGB(180, 210, 228),

	TextSize = 20,

	Font = Enum.Font.Cartoon,

})

```

Herstel standaardinstellingen

```

local ChatService = game:GetService("Chat")

ChatService:SetBubbleChatSettings({})

```

Feedback geven

---

Evenementen

Chatted

Mogelijkheden: Chat

Chat.Chatted (

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , message :[string](/docs/nl-nl/luau/strings) , color :[Enum.ChatColor](/docs/nl-nl/reference/engine/enums/ChatColor)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

message :[string](/docs/nl-nl/luau/strings)

 |
|

color :[Enum.ChatColor](/docs/nl-nl/reference/engine/enums/ChatColor)

 |

Feedback geven

---

Ga naar

▼

Chat

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[BubbleChatEnabled](#BubbleChatEnabled)

[LoadDefaultChat](#LoadDefaultChat)

[Methoden](#methods)

[CanUserChatAsync()](#CanUserChatAsync)

[CanUsersChatAsync()](#CanUsersChatAsync)

[Chat()](#Chat)

[FilterStringAsync()](#FilterStringAsync)

[FilterStringForBroadcast()](#FilterStringForBroadcast)

[FilterStringForPlayerAsync()](#FilterStringForPlayerAsync)

[InvokeChatCallback()](#InvokeChatCallback)

[RegisterChatCallback()](#RegisterChatCallback)

[SetBubbleChatSettings()](#SetBubbleChatSettings)

[Evenementen](#events)

[Chatted](#Chatted)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
