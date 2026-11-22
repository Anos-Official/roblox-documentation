<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Logger -->

Logger | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Logger](/docs/nl-nl/reference/engine/classes/Logger)

Nederlands

Feedback

Engine-klasse

Logger

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Logger)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Name](#Name) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[FullPath](#FullPath) :[string](/docs/nl-nl/luau/strings)

 |

Methoden

|

[GetLogger](#GetLogger) (name :  [string](/docs/nl-nl/luau/strings) ) :[Logger](/docs/nl-nl/reference/engine/classes/Logger)

 |
|

[Output](#Output) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Info](#Info) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Warn](#Warn) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Error](#Error) (message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[Log](#Log) (messageType :  [Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType) , message :  [string](/docs/nl-nl/luau/strings) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Evenementen

|

[MessageOut](#MessageOut) (message :  [string](/docs/nl-nl/luau/strings) , messageType :  [Enum.MessageType](/docs/nl-nl/reference/engine/enums/MessageType) , context :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Name

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Logging

Logger.Name :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

FullPath

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Logging

Logger.FullPath :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Methoden

GetLogger

Mogelijkheden: Logging

Logger:GetLogger (name :[string](/docs/nl-nl/luau/strings) ) :[Logger](/docs/nl-nl/reference/engine/classes/Logger)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Logger](/docs/nl-nl/reference/engine/classes/Logger)

Feedback geven

---

Output

Mogelijkheden: Logging

Logger:Output (

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

Info

Mogelijkheden: Logging

Logger:Info (

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

Logger:Warn (

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

Error

Mogelijkheden: Logging

Logger:Error (

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

Logger:Log (

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

Evenementen

MessageOut

Mogelijkheden: Logging

Logger.MessageOut (

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

Feedback geven

---

Ga naar

▼

Logger

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Name](#Name)

[FullPath](#FullPath)

[Methoden](#methods)

[GetLogger()](#GetLogger)

[Output()](#Output)

[Info()](#Info)

[Warn()](#Warn)

[Error()](#Error)

[Log()](#Log)

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
