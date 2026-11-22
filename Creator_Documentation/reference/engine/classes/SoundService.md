<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/SoundService -->

SoundService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/SoundService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [SoundService](/docs/en-us/reference/engine/classes/SoundService)

English

Feedback

Engine Class

SoundService

Not Creatable

Service

---

## Summary

Properties

|

[AcousticSimulationEnabled](#AcousticSimulationEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[AmbientReverb](#AmbientReverb) :[Enum.ReverbType](/docs/en-us/reference/engine/enums/ReverbType)

 |
|

[CharacterSoundsUseNewApi](#CharacterSoundsUseNewApi) :[Enum.RolloutState](/docs/en-us/reference/engine/enums/RolloutState)

 |
|

[DefaultListenerLocation](#DefaultListenerLocation) :[Enum.ListenerLocation](/docs/en-us/reference/engine/enums/ListenerLocation)

 |
|

[DistanceFactor](#DistanceFactor) :[number](/docs/en-us/luau/numbers)

 |
|

[DopplerScale](#DopplerScale) :[number](/docs/en-us/luau/numbers)

 |
|

[ListenerCFrame](#ListenerCFrame) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[ListenerObject](#ListenerObject) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[ListenerType](#ListenerType) :[Enum.ListenerType](/docs/en-us/reference/engine/enums/ListenerType)

 |
|

[RespectFilteringEnabled](#RespectFilteringEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[RolloffScale](#RolloffScale) :[number](/docs/en-us/luau/numbers)

 |
|

[VolumetricAudio](#VolumetricAudio) :[Enum.VolumetricAudio](/docs/en-us/reference/engine/enums/VolumetricAudio)

 |

Methods

|

[GetListener](#GetListener) () :[Tuple](/docs/en-us/luau/tuples)

 |
|

[GetMixerTime](#GetMixerTime) () :[number](/docs/en-us/luau/numbers)

 |
|

[OpenAttenuationCurveEditor](#OpenAttenuationCurveEditor) (selectedCurveObjects :  Instances ) : ()

 |
|

[OpenDirectionalCurveEditor](#OpenDirectionalCurveEditor) (selectedCurveObjects :  Instances ) : ()

 |
|

[PlayLocalSound](#PlayLocalSound) (sound :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

 |
|

[SetListener](#SetListener) (listenerType :  [Enum.ListenerType](/docs/en-us/reference/engine/enums/ListenerType) , listener :  [Tuple](/docs/en-us/luau/tuples) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Dynamic Reverb System

```

local Players = game:GetService("Players")

local CollectionService = game:GetService("CollectionService")

local SoundService = game:GetService("SoundService")

local localPlayer = Players.LocalPlayer

local reverbTags = {

	["reverb_Cave"] = Enum.ReverbType.Cave,

}

-- collect parts and group them by tag

local parts = {}

for reverbTag, reverbType in pairs(reverbTags) do

	for _, part in pairs(CollectionService:GetTagged(reverbTag)) do

		parts[part] = reverbType

	end

end

-- function to check if a position is within a part's extents

local function positionInPart(part, position)

	local extents = part.Size / 2

	local offset = part.CFrame:PointToObjectSpace(position)

	return offset.x < extents.x and offset.y < extents.y and offset.z < extents.z

end

local reverbType = SoundService.AmbientReverb

while true do

	task.wait()

	if not localPlayer then

		return

	end

	local character = localPlayer.Character

	-- default to no reverb

	local newReverbType = Enum.ReverbType.NoReverb

	if character and character.PrimaryPart then

		local position = character.PrimaryPart.Position

		-- go through all the indexed parts

		for part, type in pairs(parts) do

			-- see if the character is within them

			if positionInPart(part, position) then

				-- if so, pick that reverb type

				newReverbType = type

				break

			end

		end

	end

	-- set the reverb type if it has changed

	if newReverbType ~= reverbType then

		SoundService.AmbientReverb = newReverbType

		reverbType = newReverbType

	end

end

```

---

API Reference

Properties

AcousticSimulationEnabled

Read Parallel

Capabilities: Audio

SoundService.AcousticSimulationEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

AmbientReverb

Read Parallel

Capabilities: Audio

SoundService.AmbientReverb :[Enum.ReverbType](/docs/en-us/reference/engine/enums/ReverbType)

Provide feedback

---

CharacterSoundsUseNewApi

Plugin Security

Read Parallel

Capabilities: Audio

SoundService.CharacterSoundsUseNewApi :[Enum.RolloutState](/docs/en-us/reference/engine/enums/RolloutState)

Provide feedback

---

DefaultListenerLocation

Read Parallel

Capabilities: Audio, PluginOrOpenCloud

SoundService.DefaultListenerLocation :[Enum.ListenerLocation](/docs/en-us/reference/engine/enums/ListenerLocation)

Provide feedback

---

DistanceFactor

Read Parallel

Capabilities: Audio

SoundService.DistanceFactor :[number](/docs/en-us/luau/numbers)

Provide feedback

---

DopplerScale

Read Parallel

Capabilities: Audio

SoundService.DopplerScale :[number](/docs/en-us/luau/numbers)

Provide feedback

---

ListenerCFrame

Read Parallel

Capabilities: Audio

SoundService.ListenerCFrame :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

ListenerObject

Read Parallel

Capabilities: Audio

SoundService.ListenerObject :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

ListenerType

Read Parallel

Capabilities: Audio

SoundService.ListenerType :[Enum.ListenerType](/docs/en-us/reference/engine/enums/ListenerType)

Provide feedback

---

RespectFilteringEnabled

Read Parallel

Capabilities: Audio

SoundService.RespectFilteringEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

RolloffScale

Read Parallel

Capabilities: Audio

SoundService.RolloffScale :[number](/docs/en-us/luau/numbers)

Provide feedback

---

VolumetricAudio

Not Scriptable

Read Parallel

Capabilities: Audio

SoundService.VolumetricAudio :[Enum.VolumetricAudio](/docs/en-us/reference/engine/enums/VolumetricAudio)

Provide feedback

---

Methods

GetListener

Capabilities: Audio

SoundService:GetListener () :[Tuple](/docs/en-us/luau/tuples)

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

GetMixerTime

Capabilities: Audio

SoundService:GetMixerTime () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

OpenAttenuationCurveEditor

Plugin Security

Capabilities: Audio

SoundService:OpenAttenuationCurveEditor (selectedCurveObjects : Instances ) : ()

Parameters

|

selectedCurveObjects : Instances

 |

Returns

()

Provide feedback

---

OpenDirectionalCurveEditor

Plugin Security

Capabilities: Audio

SoundService:OpenDirectionalCurveEditor (selectedCurveObjects : Instances ) : ()

Parameters

|

selectedCurveObjects : Instances

 |

Returns

()

Provide feedback

---

PlayLocalSound

Capabilities: Audio

SoundService:PlayLocalSound (sound :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Parameters

|

sound :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

()

Provide feedback

---

SetListener

Capabilities: Audio

SoundService:SetListener (

listenerType :[Enum.ListenerType](/docs/en-us/reference/engine/enums/ListenerType) , listener :[Tuple](/docs/en-us/luau/tuples)

) : ()

Parameters

|

listenerType :[Enum.ListenerType](/docs/en-us/reference/engine/enums/ListenerType)

 |
|

listener :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

()

Provide feedback

---

Jump to

▼

SoundService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[AcousticSimulationEnabled](#AcousticSimulationEnabled)

[AmbientReverb](#AmbientReverb)

[CharacterSoundsUseNewApi](#CharacterSoundsUseNewApi)

[DefaultListenerLocation](#DefaultListenerLocation)

[DistanceFactor](#DistanceFactor)

[DopplerScale](#DopplerScale)

[ListenerCFrame](#ListenerCFrame)

[ListenerObject](#ListenerObject)

[ListenerType](#ListenerType)

[RespectFilteringEnabled](#RespectFilteringEnabled)

[RolloffScale](#RolloffScale)

[VolumetricAudio](#VolumetricAudio)

[Methods](#methods)

[GetListener()](#GetListener)

[GetMixerTime()](#GetMixerTime)

[OpenAttenuationCurveEditor()](#OpenAttenuationCurveEditor)

[OpenDirectionalCurveEditor()](#OpenDirectionalCurveEditor)

[PlayLocalSound()](#PlayLocalSound)

[SetListener()](#SetListener)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
