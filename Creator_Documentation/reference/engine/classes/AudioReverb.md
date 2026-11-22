<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioReverb -->

AudioReverb | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioReverb.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioReverb](/docs/en-us/reference/engine/classes/AudioReverb)

English

Feedback

Engine Class

AudioReverb

---

## Summary

Properties

|

[Bypass](#Bypass) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[DecayRatio](#DecayRatio) :[number](/docs/en-us/luau/numbers)

 |
|

[DecayTime](#DecayTime) :[number](/docs/en-us/luau/numbers)

 |
|

[Density](#Density) :[number](/docs/en-us/luau/numbers)

 |
|

[Diffusion](#Diffusion) :[number](/docs/en-us/luau/numbers)

 |
|

[DryLevel](#DryLevel) :[number](/docs/en-us/luau/numbers)

 |
|

[EarlyDelayTime](#EarlyDelayTime) :[number](/docs/en-us/luau/numbers)

 |
|

[HighCutFrequency](#HighCutFrequency) :[number](/docs/en-us/luau/numbers)

 |
|

[LateDelayTime](#LateDelayTime) :[number](/docs/en-us/luau/numbers)

 |
|

[LowShelfFrequency](#LowShelfFrequency) :[number](/docs/en-us/luau/numbers)

 |
|

[LowShelfGain](#LowShelfGain) :[number](/docs/en-us/luau/numbers)

 |
|

[ReferenceFrequency](#ReferenceFrequency) :[number](/docs/en-us/luau/numbers)

 |
|

[WetLevel](#WetLevel) :[number](/docs/en-us/luau/numbers)

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

Bypass

Read Parallel

Capabilities: Audio

AudioReverb.Bypass :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

DecayRatio

Read Parallel

Capabilities: Audio

AudioReverb.DecayRatio :[number](/docs/en-us/luau/numbers)

Provide feedback

---

DecayTime

Read Parallel

Capabilities: Audio

AudioReverb.DecayTime :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Density

Read Parallel

Capabilities: Audio

AudioReverb.Density :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Diffusion

Read Parallel

Capabilities: Audio

AudioReverb.Diffusion :[number](/docs/en-us/luau/numbers)

Provide feedback

---

DryLevel

Read Parallel

Capabilities: Audio

AudioReverb.DryLevel :[number](/docs/en-us/luau/numbers)

Provide feedback

---

EarlyDelayTime

Read Parallel

Capabilities: Audio

AudioReverb.EarlyDelayTime :[number](/docs/en-us/luau/numbers)

Provide feedback

---

HighCutFrequency

Read Parallel

Capabilities: Audio

AudioReverb.HighCutFrequency :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LateDelayTime

Read Parallel

Capabilities: Audio

AudioReverb.LateDelayTime :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LowShelfFrequency

Read Parallel

Capabilities: Audio

AudioReverb.LowShelfFrequency :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LowShelfGain

Read Parallel

Capabilities: Audio

AudioReverb.LowShelfGain :[number](/docs/en-us/luau/numbers)

Provide feedback

---

ReferenceFrequency

Read Parallel

Capabilities: Audio

AudioReverb.ReferenceFrequency :[number](/docs/en-us/luau/numbers)

Provide feedback

---

WetLevel

Read Parallel

Capabilities: Audio

AudioReverb.WetLevel :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioReverb:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

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

AudioReverb:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioReverb:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioReverb.WiringChanged (

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

AudioReverb

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Bypass](#Bypass)

[DecayRatio](#DecayRatio)

[DecayTime](#DecayTime)

[Density](#Density)

[Diffusion](#Diffusion)

[DryLevel](#DryLevel)

[EarlyDelayTime](#EarlyDelayTime)

[HighCutFrequency](#HighCutFrequency)

[LateDelayTime](#LateDelayTime)

[LowShelfFrequency](#LowShelfFrequency)

[LowShelfGain](#LowShelfGain)

[ReferenceFrequency](#ReferenceFrequency)

[WetLevel](#WetLevel)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

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
