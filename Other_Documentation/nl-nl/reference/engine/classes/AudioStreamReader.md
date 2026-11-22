<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioStreamReader -->

AudioStreamReader | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioStreamReader](/docs/nl-nl/reference/engine/classes/AudioStreamReader)

Nederlands

Feedback

Engine-klasse

AudioStreamReader

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioStreamReader)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Layout](#Layout) :[Enum.AudioChannelLayout](/docs/nl-nl/reference/engine/enums/AudioChannelLayout)

 |
| --- | --- |
|

[SampleFormat](#SampleFormat) :[Enum.AudioSampleFormat](/docs/nl-nl/reference/engine/enums/AudioSampleFormat)

 |
|

[SampleRate](#SampleRate) :[number](/docs/nl-nl/luau/numbers)

 |
|

[WindowSize](#WindowSize) :[Enum.AudioWindowSize](/docs/nl-nl/reference/engine/enums/AudioWindowSize)

 |

Methoden

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[Peek](#Peek) (into :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Read](#Read) (into :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

 |

Evenementen

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Layout

Parallel lezen

Mogelijkheden: Audio

AudioStreamReader.Layout :[Enum.AudioChannelLayout](/docs/nl-nl/reference/engine/enums/AudioChannelLayout)

Feedback geven

---

SampleFormat

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioStreamReader.SampleFormat :[Enum.AudioSampleFormat](/docs/nl-nl/reference/engine/enums/AudioSampleFormat)

Feedback geven

---

SampleRate

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioStreamReader.SampleRate :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

WindowSize

Parallel lezen

Mogelijkheden: Audio

AudioStreamReader.WindowSize :[Enum.AudioWindowSize](/docs/nl-nl/reference/engine/enums/AudioWindowSize)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioStreamReader:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetInputPins

Mogelijkheden: Audio

AudioStreamReader:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioStreamReader:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Peek

Parallel schrijven

Mogelijkheden: Audio

AudioStreamReader:Peek (into :[{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

into :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Read

Parallel schrijven

Mogelijkheden: Audio

AudioStreamReader:Read (into :[{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

into :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioStreamReader.WiringChanged (

connected :[boolean](/docs/nl-nl/luau/booleans) , pin :[string](/docs/nl-nl/luau/strings) , wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/nl-nl/luau/booleans)

 |
|

pin :[string](/docs/nl-nl/luau/strings)

 |
|

wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

Ga naar

▼

AudioStreamReader

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Layout](#Layout)

[SampleFormat](#SampleFormat)

[SampleRate](#SampleRate)

[WindowSize](#WindowSize)

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[Peek()](#Peek)

[Read()](#Read)

[Evenementen](#events)

[WiringChanged](#WiringChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
