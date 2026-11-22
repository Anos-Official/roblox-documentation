<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioStreamReader -->

AudioStreamReader | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioStreamReader.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioStreamReader](/docs/en-us/reference/engine/classes/AudioStreamReader)

English

Feedback

Engine Class

AudioStreamReader

Not Browsable

---

## Summary

Properties

|

[Layout](#Layout) :[Enum.AudioChannelLayout](/docs/en-us/reference/engine/enums/AudioChannelLayout)

 |
| --- | --- |
|

[SampleFormat](#SampleFormat) :[Enum.AudioSampleFormat](/docs/en-us/reference/engine/enums/AudioSampleFormat)

 |
|

[SampleRate](#SampleRate) :[number](/docs/en-us/luau/numbers)

 |
|

[WindowSize](#WindowSize) :[Enum.AudioWindowSize](/docs/en-us/reference/engine/enums/AudioWindowSize)

 |

Methods

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[Peek](#Peek) (into :  [{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

 |
|

[Read](#Read) (into :  [{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Layout

Read Parallel

Capabilities: Audio

AudioStreamReader.Layout :[Enum.AudioChannelLayout](/docs/en-us/reference/engine/enums/AudioChannelLayout)

Provide feedback

---

SampleFormat

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioStreamReader.SampleFormat :[Enum.AudioSampleFormat](/docs/en-us/reference/engine/enums/AudioSampleFormat)

Provide feedback

---

SampleRate

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioStreamReader.SampleRate :[number](/docs/en-us/luau/numbers)

Provide feedback

---

WindowSize

Read Parallel

Capabilities: Audio

AudioStreamReader.WindowSize :[Enum.AudioWindowSize](/docs/en-us/reference/engine/enums/AudioWindowSize)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioStreamReader:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/en-us/luau/strings)

 |

Returns

{[Wire](/docs/en-us/reference/engine/classes/Wire) }

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioStreamReader:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioStreamReader:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

Peek

Write Parallel

Capabilities: Audio

AudioStreamReader:Peek (into :[{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

into :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Read

Write Parallel

Capabilities: Audio

AudioStreamReader:Read (into :[{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

into :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioStreamReader.WiringChanged (

connected :[boolean](/docs/en-us/luau/booleans) , pin :[string](/docs/en-us/luau/strings) , wire :[Wire](/docs/en-us/reference/engine/classes/Wire) , instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/en-us/luau/booleans)

 |
|

pin :[string](/docs/en-us/luau/strings)

 |
|

wire :[Wire](/docs/en-us/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

AudioStreamReader

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Layout](#Layout)

[SampleFormat](#SampleFormat)

[SampleRate](#SampleRate)

[WindowSize](#WindowSize)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[Peek()](#Peek)

[Read()](#Read)

[Events](#events)

[WiringChanged](#WiringChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
