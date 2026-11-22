<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/SoundService -->

SoundService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)

Nederlands

Feedback

Engine-klasse

SoundService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/SoundService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AcousticSimulationEnabled](#AcousticSimulationEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[AmbientReverb](#AmbientReverb) :[Enum.ReverbType](/docs/nl-nl/reference/engine/enums/ReverbType)

 |
|

[CharacterSoundsUseNewApi](#CharacterSoundsUseNewApi) :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

 |
|

[DefaultListenerLocation](#DefaultListenerLocation) :[Enum.ListenerLocation](/docs/nl-nl/reference/engine/enums/ListenerLocation)

 |
|

[DistanceFactor](#DistanceFactor) :[number](/docs/nl-nl/luau/numbers)

 |
|

[DopplerScale](#DopplerScale) :[number](/docs/nl-nl/luau/numbers)

 |
|

[ListenerCFrame](#ListenerCFrame) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[ListenerObject](#ListenerObject) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[ListenerType](#ListenerType) :[Enum.ListenerType](/docs/nl-nl/reference/engine/enums/ListenerType)

 |
|

[RespectFilteringEnabled](#RespectFilteringEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[RolloffScale](#RolloffScale) :[number](/docs/nl-nl/luau/numbers)

 |
|

[VolumetricAudio](#VolumetricAudio) :[Enum.VolumetricAudio](/docs/nl-nl/reference/engine/enums/VolumetricAudio)

 |

Methoden

|

[GetListener](#GetListener) () :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[GetMixerTime](#GetMixerTime) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[OpenAttenuationCurveEditor](#OpenAttenuationCurveEditor) (selectedCurveObjects :  Instances ) : ()

 |
|

[OpenDirectionalCurveEditor](#OpenDirectionalCurveEditor) (selectedCurveObjects :  Instances ) : ()

 |
|

[PlayLocalSound](#PlayLocalSound) (sound :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[SetListener](#SetListener) (listenerType :  [Enum.ListenerType](/docs/nl-nl/reference/engine/enums/ListenerType) , listener :  [Tuple](/docs/nl-nl/luau/tuples) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Dynamisch Reverb Systeem

```

local Players = game:GetService("Players")

local CollectionService = game:GetService("CollectionService")

local SoundService = game:GetService("SoundService")

local localPlayer = Players.LocalPlayer

local reverbTags = {

	["reverb_Cave"] = Enum.ReverbType.Cave,

}

-- verzamel onderdelen en groepeer ze op tag

local parts = {}

for reverbTag, reverbType in pairs(reverbTags) do

	for _, part in pairs(CollectionService:GetTagged(reverbTag)) do

		parts[part] = reverbType

	end

end

-- functie om te controleren of een positie binnen de afmetingen van een onderdeel ligt

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

	-- standaard naar geen reverb

	local newReverbType = Enum.ReverbType.NoReverb

	if character and character.PrimaryPart then

		local position = character.PrimaryPart.Position

		-- doorloop alle geïndexeerde onderdelen

		for part, type in pairs(parts) do

			-- kijk of het karakter binnen hen is

			if positionInPart(part, position) then

				-- als dat zo is, kies dat reverb-type

				newReverbType = type

				break

			end

		end

	end

	-- stel het reverb-type in als het is veranderd

	if newReverbType ~= reverbType then

		SoundService.AmbientReverb = newReverbType

		reverbType = newReverbType

	end

end

```

---

API-referentie

Eigenschappen

AcousticSimulationEnabled

Parallel lezen

Mogelijkheden: Audio

SoundService.AcousticSimulationEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

AmbientReverb

Parallel lezen

Mogelijkheden: Audio

SoundService.AmbientReverb :[Enum.ReverbType](/docs/nl-nl/reference/engine/enums/ReverbType)

Feedback geven

---

CharacterSoundsUseNewApi

Plugin-beveiliging

Parallel lezen

Mogelijkheden: Audio

SoundService.CharacterSoundsUseNewApi :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

Feedback geven

---

DefaultListenerLocation

Parallel lezen

Mogelijkheden: Audio, PluginOrOpenCloud

SoundService.DefaultListenerLocation :[Enum.ListenerLocation](/docs/nl-nl/reference/engine/enums/ListenerLocation)

Feedback geven

---

DistanceFactor

Parallel lezen

Mogelijkheden: Audio

SoundService.DistanceFactor :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

DopplerScale

Parallel lezen

Mogelijkheden: Audio

SoundService.DopplerScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

ListenerCFrame

Parallel lezen

Mogelijkheden: Audio

SoundService.ListenerCFrame :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Feedback geven

---

ListenerObject

Parallel lezen

Mogelijkheden: Audio

SoundService.ListenerObject :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

ListenerType

Parallel lezen

Mogelijkheden: Audio

SoundService.ListenerType :[Enum.ListenerType](/docs/nl-nl/reference/engine/enums/ListenerType)

Feedback geven

---

RespectFilteringEnabled

Parallel lezen

Mogelijkheden: Audio

SoundService.RespectFilteringEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

RolloffScale

Parallel lezen

Mogelijkheden: Audio

SoundService.RolloffScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

VolumetricAudio

Niet scriptbaar

Parallel lezen

Mogelijkheden: Audio

SoundService.VolumetricAudio :[Enum.VolumetricAudio](/docs/nl-nl/reference/engine/enums/VolumetricAudio)

Feedback geven

---

Methoden

GetListener

Mogelijkheden: Audio

SoundService:GetListener () :[Tuple](/docs/nl-nl/luau/tuples)

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

GetMixerTime

Mogelijkheden: Audio

SoundService:GetMixerTime () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

OpenAttenuationCurveEditor

Plugin-beveiliging

Mogelijkheden: Audio

SoundService:OpenAttenuationCurveEditor (selectedCurveObjects : Instances ) : ()

Parameters

|

selectedCurveObjects : Instances

 |

Teruggaves

()

Feedback geven

---

OpenDirectionalCurveEditor

Plugin-beveiliging

Mogelijkheden: Audio

SoundService:OpenDirectionalCurveEditor (selectedCurveObjects : Instances ) : ()

Parameters

|

selectedCurveObjects : Instances

 |

Teruggaves

()

Feedback geven

---

PlayLocalSound

Mogelijkheden: Audio

SoundService:PlayLocalSound (sound :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

sound :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Feedback geven

---

SetListener

Mogelijkheden: Audio

SoundService:SetListener (

listenerType :[Enum.ListenerType](/docs/nl-nl/reference/engine/enums/ListenerType) , listener :[Tuple](/docs/nl-nl/luau/tuples)

) : ()

Parameters

|

listenerType :[Enum.ListenerType](/docs/nl-nl/reference/engine/enums/ListenerType)

 |
|

listener :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

()

Feedback geven

---

Ga naar

▼

SoundService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

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

[Methoden](#methods)

[GetListener()](#GetListener)

[GetMixerTime()](#GetMixerTime)

[OpenAttenuationCurveEditor()](#OpenAttenuationCurveEditor)

[OpenDirectionalCurveEditor()](#OpenDirectionalCurveEditor)

[PlayLocalSound()](#PlayLocalSound)

[SetListener()](#SetListener)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
