<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/LogService -->

LogService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [LogService](/docs/nl-nl/reference/engine/classes/LogService)

Nederlands

Feedback

Engine-klasse

LogService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/LogService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[ClearOutput](#ClearOutput) () : ()

 |
| --- | --- |
|

[Error](#Error) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[GetLogHistory](#GetLogHistory) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetLogHistoryAsync](#GetLogHistoryAsync) (user :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetLogger](#GetLogger) (name :  [string](/docs/nl-nl/luau/strings) ) :[Logger](/docs/nl-nl/reference/engine/classes/Logger)

 |
|

[Info](#Info) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Log](#Log) (messageType :  [Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType) , message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Output](#Output) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Warn](#Warn) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Evenementen

|

[MessageOut](#MessageOut) (message :  [string](/docs/nl-nl/luau/strings) , messageType :  [Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

ClearOutput

Mogelijkheden: Logging

LogService:ClearOutput () : ()

Teruggaves

()

Feedback geven

---

Error

Mogelijkheden: Logging

LogService:Error (

message :[string](/docs/nl-nl/luau/strings) , context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Feedback geven

---

GetLogHistory

Mogelijkheden: Logging

LogService:GetLogHistory () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetLogHistoryAsync

Opbrengst

Mogelijkheden: Logging

LogService:GetLogHistoryAsync (user :[User](/docs/nl-nl/reference/engine/datatypes/User) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

user :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetLogger

Mogelijkheden: Logging

LogService:GetLogger (name :[string](/docs/nl-nl/luau/strings) ) :[Logger](/docs/nl-nl/reference/engine/classes/Logger)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Logger](/docs/nl-nl/reference/engine/classes/Logger)

Feedback geven

---

Info

Mogelijkheden: Logging

LogService:Info (

message :[string](/docs/nl-nl/luau/strings) , context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Feedback geven

---

Log

Mogelijkheden: Logging

LogService:Log (

messageType :[Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType) , message :[string](/docs/nl-nl/luau/strings) , context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

messageType :[Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType)

 |
|

message :[string](/docs/nl-nl/luau/strings)

 |
|

context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Feedback geven

---

Output

Mogelijkheden: Logging

LogService:Output (

message :[string](/docs/nl-nl/luau/strings) , context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Feedback geven

---

Warn

Mogelijkheden: Logging

LogService:Warn (

message :[string](/docs/nl-nl/luau/strings) , context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Feedback geven

---

Evenementen

MessageOut

Mogelijkheden: Logging

LogService.MessageOut (

message :[string](/docs/nl-nl/luau/strings) , messageType :[Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType) , context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

messageType :[Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType)

 |
|

context :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Codevoorbeelden

LogService.MessageOut

```

local LogService = game:GetService("LogService")

local messageLabel = Instance.new("Message")

messageLabel.Parent = workspace

local function onMessageOut(message, messageType)

	messageLabel.Text = "Het bericht was " .. message .. " en het type was " .. tostring(messageType)

end

LogService.MessageOut:Connect(onMessageOut)

```

Feedback geven

---

Ga naar

▼

LogService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[ClearOutput()](#ClearOutput)

[Error()](#Error)

[GetLogHistory()](#GetLogHistory)

[GetLogHistoryAsync()](#GetLogHistoryAsync)

[GetLogger()](#GetLogger)

[Info()](#Info)

[Log()](#Log)

[Output()](#Output)

[Warn()](#Warn)

[Evenementen](#events)

[MessageOut](#MessageOut)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
