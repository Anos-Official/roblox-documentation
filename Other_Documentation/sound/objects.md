<!-- Source: https://create.roblox.com/docs/sound/objects -->

Sound objects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/sound/objects.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Learn](/docs/en-us/learn)

# Sound objects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/sound/objects.md)

There is a newer set of [audio objects](/docs/audio/objects)  that offer more control and address robust use cases. For more information, see [Audio](/docs/audio) .

Audio playback occurs through [Sound](/docs/reference/engine/classes/Sound)  objects which emit audio within a game. Roblox assigns each [audio asset](/docs/audio/assets)  a unique ID that you can assign to [Sound](/docs/reference/engine/classes/Sound)  objects to play a specific sound effect or music track. You can either set this audio to play automatically at runtime, or trigger it to [play from scripts](#script-sound-objects) .

To modify playback of multiple [Sound](/docs/reference/engine/classes/Sound)  objects, you can assign them to a [sound group](/docs/sound/groups)  and control the entire group's volume, as well as apply [dynamic effects](/docs/sound/dynamic-effects) .

## [Create sound objects](#create-sound-objects)[](#create-sound-objects)

There are three locations you can create a [Sound](/docs/reference/engine/classes/Sound)  object, and each location determines how audio emits and volume changes in relation to the user's position within the game.

| Location | | How audio emits | | How volume changes |
| --- | --- |
| Child of a block, sphere, or cylinder [BasePart](/docs/reference/engine/classes/BasePart) . | | Audio emits outward from the entire surface of the part. | | Volume changes depending on the distance between the user's sound listener and the position of the part, as well as its size. |
| Child of an [Attachment](/docs/reference/engine/classes/Attachment) , [MeshPart](/docs/reference/engine/classes/MeshPart) , [TrussPart](/docs/reference/engine/classes/TrussPart) , [WedgePart](/docs/reference/engine/classes/WedgePart) , or [CornerWedgePart](/docs/reference/engine/classes/CornerWedgePart) . | | Audio emits outward from the single attachment point or part center. | | Volume changes depending on the distance between the user's sound listener and the attachment/part position. |
| Within [SoundService](/docs/reference/engine/classes/SoundService)  or [Workspace](/docs/reference/engine/classes/Workspace) . | | Audio emits throughout the game. | | Volume and pan position remain the same regardless of the user's sound listener position or rotation. |

### [Positional audio](#positional-audio)[](#positional-audio)

Positional audio is audio that users can only hear near a specific position within the game. There are two types of positional audio you can utilize: volumetric and point source.

#### [Volumetric](#volumetric)[](#volumetric)

Volumetric audio is the most realistic audio option, as it dynamically changes depending on the user's position to the audio source. For example, if the user is within a [BasePart](/docs/reference/engine/classes/BasePart)  with a child [Sound](/docs/reference/engine/classes/Sound)  object, audio plays all around the user, similar to music in headphones playing at the same volume in each speaker. When the user exits the part, audio gradually decreases in volume and becomes more directional per speaker, moving around the user's head when their listener rotates. For information on the properties that control how loud your audio is at different distances from the part, see [RollOffMinDistance and RollOffMaxDistance](#rolloffmindistance-and-rolloffmaxdistance) .

The size of the [BasePart](/docs/reference/engine/classes/BasePart)  also affects the audio's volume, as larger [BaseParts](/docs/reference/engine/classes/BasePart)  produce a wider area in which users can hear the audio and when a user navigates away from a large [BasePart](/docs/reference/engine/classes/BasePart) , volume decreases slower. The following example displays a [BasePart](/docs/reference/engine/classes/BasePart)  that is the size of a city with a [Sound](/docs/reference/engine/classes/Sound)  object playing ambient audio. Users A and B experience the audio differently: user B is closer to the large [BasePart](/docs/reference/engine/classes/BasePart) , and they mostly hear the audio around the same loudness in both speakers. Conversely, user A is further away from the city, so the audio they hear is quieter and more directional than user B, playing at differing loudness in each of their speakers.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/Volumetric-Sound-Diagram.jpg)

Volumetric audio is useful for any audio that needs to be immersive around a user and change dynamically depending on the user's position, such as a concert stage or ambience zones like rainfall. When you experiment with placing a [Sound](/docs/reference/engine/classes/Sound)  object on [BaseParts](/docs/reference/engine/classes/BasePart)  of different sizes and positions from users, you can hear how immersive volumetric audio can be.

To create a [Sound](/docs/reference/engine/classes/Sound)  object for volumetric audio:

1.

In the Explorer  window, select SoundService .

2.

In the Properties  window, navigate to the VolumetricAudio  property, then set it to Enabled .

3.

In the Explorer  window, hover over a [BasePart](/docs/reference/engine/classes/BasePart) , then click the ⊕ button. A contextual menu displays.

4.

From the menu, insert a Sound .

5.

In the Properties  window, navigate to the SoundId  property and input a valid [audio asset ID](/docs/audio/assets) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sound-SoundId.png)

6.

OPTIONAL

 If you want the audio to start playing when the game begins, enable the Playing  property.

#### [Point source](#point-source)[](#point-source)

Contrary to volumetric audio, point source audio only emits from a single point source. This type of audio is useful for explosions, impact noises, electronic devices, and dialogue.

To create a [Sound](/docs/reference/engine/classes/Sound)  object for point source audio:

1.

In the Explorer  window, hover over an attachment, truss, wedge, or corner wedge, then click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a Sound .

3.

In the Properties  window, navigate to the SoundId  property and input a valid [audio asset ID](/docs/audio/assets) .

4.

OPTIONAL

 If you want the audio to start playing when the game begins, enable the Playing  property.

### [Background audio](#background-audio)[](#background-audio)

Background audio plays at the same volume no matter where the user travels within your game. This type of audio is useful for music that you want to play for users, especially when you want to create a soundtrack of multiple audio files.

It's best to keep all [Sound](/docs/reference/engine/classes/Sound)  objects for background audio in a single location of the Workspace for organization purposes as you continue to add and edit audio within your game. The following example stores the new [Sound](/docs/reference/engine/classes/Sound)  object under the [SoundService](/docs/reference/engine/classes/SoundService)  container, as this service determines how [Sound](/docs/reference/engine/classes/Sound)  objects play in games.

To create a [Sound](/docs/reference/engine/classes/Sound)  object for background audio:

1.

In the Explorer  window, hover over SoundService , then click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a Sound .

3.

In the Properties  window, navigate to the SoundId  property and input a valid [audio asset ID](/docs/audio/assets) .

4.

OPTIONAL

 If you want the audio to start playing when the game begins, enable the Playing  property.

5.

OPTIONAL

 If this [Sound](/docs/reference/engine/classes/Sound)  object is the only track you want to play in the place, enable its Looped  property.

## [Customize sound objects](#customize-sound-objects)[](#customize-sound-objects)

[Sound](/docs/reference/engine/classes/Sound)  object properties work together to influence how users experience your audio, such as:

-

How loud they hear specific audio individually and in relation to one another ([Volume](#volume) ).

-

How they perceive volume when they move away from the audio source ([RollOffMinDistance](#rolloffmindistance-and-rolloffmaxdistance) , [RollOffMaxDistance](#rolloffmindistance-and-rolloffmaxdistance) , and [RollOffMode](#rolloffmode) )

-

What part of the audio they can listen to ([TimePosition](#timeposition) ).

-

How fast and at what pitch they hear it ([PlaybackSpeed](#playbackspeed) ).

-

If the audio automatically replays upon completion ([Looped](#looped) ).

### [Volume](#volume)[](#volume)

The [Volume](/docs/reference/engine/classes/Sound#Volume)  property allows you to set the volume of your audio anywhere from 0  (silence) to 10  (booming). If you want to change the volume of multiple [Sound](/docs/reference/engine/classes/Sound)  objects at once, parent them under a [sound group](/docs/sound/groups) .

If your source audio is sufficiently loud, you likely don't need to increase the volume to more than 2 , as this property is multiplicative. For example: a [Volume](/docs/reference/engine/classes/Sound#Volume)  value of 4  is four times as loud than a [Volume](/docs/reference/engine/classes/Sound#Volume)  value of 1 , so if your source audio was already loud, the audio might become overwhelming to users.

### [RollOffMinDistance and RollOffMaxDistance](#rolloffmindistance-and-rolloffmaxdistance)[](#rolloffmindistance-and-rolloffmaxdistance)

[RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  and [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  determine the range of how a user perceives volume from positional audio. For volumetric audio, [RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  is the minimum distance in studs that audio begins to decrease in volume when the client's listener moves away  from the parent [BasePart](/docs/reference/engine/classes/BasePart) , and [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  property is the maximum distance in studs that a client's listener can hear audio from the surface of the object.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/Sound-Volumetric-RollOff.jpg)

For point source audio, [RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  and [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  work similarly to volumetric audio, but the roll off distance these properties control doesn't surround the object, it only influences the distance outward from the point source.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/Sound-Point-RollOff.jpg)

### [RollOffMode](#rolloffmode)[](#rolloffmode)

The [RollOffMode](/docs/reference/engine/classes/Sound#RollOffMode)  property allows you to decide how audio fades as the distance between the user's listener and the [Sound](/docs/reference/engine/classes/Sound)  object's parent increases. You can set this property to one of four values of the [Enum.RollOffMode](/docs/reference/engine/enums/RollOffMode)  enum.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/RollOffMode-Chart.png)

| RollOffMode | | Description |
| Inverse  (default) | | Volume initially fades abruptly from [RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance) , but volume fading becomes more gradual the closer a user is to reaching the [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance) . Once they reach the [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance) , the audio falls silent. |
| Linear | | Volume fades linearly between [RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  and [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance) . Once a user reaches the [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance) , the audio falls silent. |
| InverseTapered | | Volume follows the inverse model when close to [RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  and the linear square model when a user is close to [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance) . Audio approaches silence at the maximum distance point. |
| LinearSquare | | Volume fades between [RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  and [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  with a linear squared relationship. Audio approaches silence at the maximum distance point. |

For most Inverse  and Linear  [RollOffMode](/docs/reference/engine/classes/Sound#RollOffMode)  types, low [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  values cause audio to abruptly cut off when the listener reaches the [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance) . If you want your audio to gradually decrease in volume, set a higher [RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  value.

### [PlaybackSpeed](#playbackspeed)[](#playbackspeed)

The [PlaybackSpeed](/docs/reference/engine/classes/Sound#PlaybackSpeed)  property allows you to determine the speed your audio plays. For example, if you set the [PlaybackSpeed](/docs/reference/engine/classes/Sound#PlaybackSpeed)  to a value of 2 , your audio plays twice as fast and one octave higher in pitch. Similarly, if you set it to a value of 0.5 , your audio plays twice as slow and one octave lower in pitch.

|  | |  | |  |
| [PlaybackSpeed](/docs/reference/engine/classes/Sound#PlaybackSpeed)  = 0.5 | | [PlaybackSpeed](/docs/reference/engine/classes/Sound#PlaybackSpeed)  = 1.0 | | [PlaybackSpeed](/docs/reference/engine/classes/Sound#PlaybackSpeed)  = 2.0 |

### [TimePosition](#timeposition)[](#timeposition)

The [TimePosition](/docs/reference/engine/classes/Sound#TimePosition)  property displays, in seconds, what position within the audio sample a user is currently hearing. This property is useful for either only playing a section of the audio sample, or triggering an event to occur once audio reaches a specific position. For example, the following code sample causes a particle emitter to emit a white ring particle above a part within a limited time range of an audio track.

```

local RunService = game:GetService("RunService")

local Workspace = game:GetService("Workspace")

-- Create a new part

local part = Instance.new("Part")

part.Anchored = true

part.Color = Color3.new(0.75, 0.2, 0.5)

part.Size = Vector3.new(2, 1, 2)

part.Material = Enum.Material.Neon

part.Position = Vector3.new(0, 4, 0)

part.Parent = Workspace

-- Create an attachment on the part

local attachment = Instance.new("Attachment")

attachment.Position = Vector3.new(0, 0.5, 0)

attachment.Parent = part

-- Create a particle emitter on the attachment

local emitter = Instance.new("ParticleEmitter")

emitter.Rate = 5

emitter.Lifetime = NumberRange.new(1.5, 1.5)

emitter.Texture = "rbxassetid://1266170131"

emitter.Speed = NumberRange.new(1, 1)

emitter.Size = NumberSequence.new{NumberSequenceKeypoint.new(0, 1), NumberSequenceKeypoint.new(1, 6)}

emitter.Transparency = NumberSequence.new{NumberSequenceKeypoint.new(0, 1), NumberSequenceKeypoint.new(0.25, 0), NumberSequenceKeypoint.new(1, 1)}

emitter.Orientation = Enum.ParticleOrientation.VelocityPerpendicular

emitter.Parent = attachment

-- Create a sound on the attachment

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://1835405646"

sound.Parent = attachment

-- Play the sound

sound:Play()

-- Start checking if emitter should be enabled

RunService.Heartbeat:Connect(function()

	-- Enable the emitter within a time range of the audio; otherwise disable it

	emitter.Enabled = sound.TimePosition >= 5 and sound.TimePosition < 20

end)

```

### [Looped](#looped)[](#looped)

The [Looped](/docs/reference/engine/classes/Sound#Looped)  property allows you to repeat audio after it has finished playing. When set to true , the [Sound](/docs/reference/engine/classes/Sound)  object's audio plays again. This is useful to apply to [background audio](#background-audio)  to ensure your game never has abrupt silence.

## [Script sound objects](#script-sound-objects)[](#script-sound-objects)

### [Play audio contextually](#play-audio-contextually)[](#play-audio-contextually)

Aside from auto-playing audio through the [Sound](/docs/reference/engine/classes/Sound)  object's [Playing](/docs/reference/engine/classes/Sound#Playing)  property, you can play audio contextually from a [LocalScript](/docs/reference/engine/classes/LocalScript)  by calling [Play()](/docs/reference/engine/classes/Sound#Play)  on the corresponding [Sound](/docs/reference/engine/classes/Sound)  object. For example:

```

local Workspace = game:GetService("Workspace")

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://9120386436"

sound.Looped = true

sound.Parent = Workspace

sound:Play()

```

Alternatively, if the place will feature multiple tracks, you can play a specific track from a client script:

```

local SoundService = game:GetService("SoundService")

local musicTrack = SoundService:FindFirstChild("LucidDream")

if musicTrack not musicTrack.IsPlaying then

	musicTrack:Play()

end

```

### [Play interface audio](#play-interface-audio)[](#play-interface-audio)

You can play interface audio for [GuiObjects](/docs/reference/engine/classes/GuiObject)  such as [buttons](/docs/ui/buttons)  by hooking up a [Sound](/docs/reference/engine/classes/Sound)  object to the [Activated](/docs/reference/engine/classes/GuiButton#Activated)  event listener. This lets you provide auditory feedback to users, such as when they hover over or press it.

To play a [Sound](/docs/reference/engine/classes/Sound)  object's audio when a user activates a [TextButton](/docs/reference/engine/classes/TextButton)  or [ImageButton](/docs/reference/engine/classes/ImageButton) :

1.

In the [Explorer](/docs/studio/explorer)  window, hover over the [TextButton](/docs/reference/engine/classes/TextButton)  or [ImageButton](/docs/reference/engine/classes/ImageButton) , then click the ⊕ button. A contextual menu displays.

2.

From the menu, insert either a [LocalScript](/docs/reference/engine/classes/LocalScript)  or a [Script](/docs/reference/engine/classes/Script)  with [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  set to [Enum.RunContext.Client](/docs/reference/engine/enums/RunContext#Client) .

3.

Paste the following code into the script, then replace SOUND_NAME  with the name of a [Sound](/docs/reference/engine/classes/Sound)  object located inside the [SoundService](/docs/reference/engine/classes/SoundService)  container.

```

local SoundService = game:GetService("SoundService")

local button = script.Parent

local sound = SoundService:FindFirstChild("SOUND_NAME")

if not sound.isLoaded then

	sound.Loaded:Wait()

end

local function onButtonActivated()

	if sound and not sound.IsPlaying then

		sound:Play()

	end

end

button.Activated:Connect(onButtonActivated)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
