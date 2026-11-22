<!-- Source: https://create.roblox.com/docs/resources/the-mystery-of-duvall-drive/design-dark-soundscapes -->

Design dark soundscapes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/resources/the-mystery-of-duvall-drive/design-dark-soundscapes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Samples and projects](/docs/en-us/samples)
4. /
5. [The Mystery of Duvall Drive](/docs/resources/the-mystery-of-duvall-drive)

# Design dark soundscapes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/resources/the-mystery-of-duvall-drive/design-dark-soundscapes.md)

In order for The Mystery of Duvall Drive to feel authentic and plausible, we made sure that ambience was king at every stage in development. We included scripted audio events, music, character sounds, and point-source audio to support our "grass is always greener" approach, meaning that we always wanted there to be a more intriguing sound in the distance no matter where the player is located in the house so that they would want to further investigate each room. These sounds ranged anywhere from a radio playing music in a bedroom, the kitchen sink dripping, rain hitting the attic roof, or the oscillating ritual orb in the center of the house.

Sound design for a game with horror themes is a balancing act between embedding both realistic and abstract audio. While realistic audio provides a sense of immersion and authenticity to the world, abstract audio drives the player's attention to the otherworldly elements that pull the story forward. Both audio types have their strengths separately, but together they can create a dark soundscape that feels authentic, plausible, and horrifying. In this section, we'll show you how and why we used volumetric audio and nested [SoundGroup](/docs/reference/engine/classes/SoundGroup)  mixing to balance our dark soundscape and bring life to our 3D space.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/overview.png)

## [Volumetric audio](#volumetric-audio)[](#volumetric-audio)

[Volumetric audio](/docs/sound/objects#volumetric)  is the most realistic audio option in Studio to how people perceive sound depending on its distance to their ears. This type of audio allows you to place a [Sound](/docs/reference/engine/classes/Sound)  object on a [BasePart](/docs/reference/engine/classes/BasePart) , then use that [BasePart](/docs/reference/engine/classes/BasePart)  to cover an entire area of where you want that audio to play. It's highly useful for large objects that make sound, such as waterfalls, vehicles, and large cities. When a player is within a [BasePart](/docs/reference/engine/classes/BasePart)  that has a child [Sound](/docs/reference/engine/classes/Sound)  object with volumetric audio enabled, the audio plays all around the player, similar to music in headphones playing at the same volume in each speaker. When the user exits the object, audio gradually decreases in volume and becomes more directional per speaker, moving around the user's head when their listener rotates. This means that if the sound is emitting to the left of your listener, the sound plays louder in your left speaker than your right speaker.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/audio-volume.png) Example of an audio volume that plays intermittent creepy human whispers. This reinforces a dark soundscape, setting the stage for the mood inside the house.

A player's experience with audio is not only dependent on what sounds they can hear, but also which direction  those sounds come from. In the real world, somebody yelling your name from across a field sounds a lot more directional than something like the soft hum of the air conditioning in a room or the reverb in a cave. This is because sound waves are bouncy, and when they hit solid objects like walls, pavement, and trees, they scatter and reflect back to your ears from different directions. In fact, sound waves can even bend around objects like your own head!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/volumetric-audio-immersive.png) In this section of the house, volumetric audio allows you to immerse yourself in the sounds of rain hitting nearby windows, the crackling of a fireplace, and a soft tune being played through an old radio nearby.

Before volumetric audio, you were limited to having your audio emit from a [single point in space](/docs/sound/objects#point-source) , or having it [play back in both headphones like music](/docs/sound/objects#background-audio) . Because we wanted our audio to be as realistic as possible while representing a wide range of sound types, neither of these previous implementations would have been sufficient for creating the immersive world that we wanted to capture in this game. As a result, we used volumetric audio emitters for the vast majority of our sound effects, including the outdoor rain, interior room tones, corrupted zone ambiences, television static, and rain hitting various surfaces. If we were to disable volumetric audio on the project, all of these sounds would collapse down to a single point of emission at their center of mass, and the entire soundscape would shift between the player's ears whenever they rotate their camera. This would make the entire space feel unrealistic and digital, and the sound's movement would be quite jarring and undesirable for the player.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/exterior-audio-hierarchy.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/sound-emitters-hierarchy.png)

Just a few examples of how we used volumetric audio to create our exterior ambience, as well as rain colliding with various materials in the backyard.

Volumetric audio emitters allowed us to control the directionality of our soundscape to give a real sense of movement through the space. Because their influence is spread over a larger area and the audio spreads naturally to both ears, they give the game's overall sound bed, or constant hum of audio activity, a far more predictable and stable volume level. This prevents the game from being silent when the player's character isn't doing anything, and it makes the game feel realistic as there are very few spaces in real life completely void of noise!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/volumetric-audio-emitter-greenhouse.png) We placed a volumetric audio emitter on the greenhouse to add immersive ambient sounds of the raindrops hitting the glass roof and echoing throughout the room.

When adding detail to our outdoor soundscape, it was important to make the rain feel alive instead of a simple looping rain sound effect. One of the ways we achieved this was by adding rain surface sounds to various objects so that you could hear the storm's impact on your immediate surroundings. In this project, there are generic outdoor rain sounds, but also volumetric audio emitters for rain hitting objects like windows, plastic, and rooftops. For example, we added a volumetric audio emitter to a car through the following process to give players the impression that raindrops were impacting the entire surface of the car instead of just a single point on the car's hood:

1.

In the Explorer  window, we selected SoundService .

2.

In the Properties  window, we navigated to the VolumetricAudio  property, then set it to Enabled . This turned on the volumetric sounds behavior for the entire project.

3.

In the viewport, we created a new [Part](/docs/reference/engine/classes/Part)  that matched the size of the car. This defined the entire region we wanted to sound to emit from.

4.

In the Properties  window, we set the following properties for the part to ensure that our part didn't fall through the ground, collide with the car model, or obscure the visibility of the car:

-

[Part.Anchored](/docs/reference/engine/classes/Part#Anchored)  = Enabled

-

[Part.CanCollide](/docs/reference/engine/classes/Part#CanCollide)  = Disabled

-

[Part.Transparency](/docs/reference/engine/classes/Part#Transparency)  = 1

5.

We then added a [Sound](/docs/reference/engine/classes/Sound)  object to the invisible part and set the following properties for the [Sound](/docs/reference/engine/classes/Sound)  object so the raindrop sound started playing when players would load into the game, looped continuously, and became audible when a player was 60 studs away/reached its maximum volume at 15 studs away:

-

[Sound.SoundId](/docs/reference/engine/classes/Sound#SoundId)  = 9178663282

-

[Sound.Playing](/docs/reference/engine/classes/Sound#Playing)  = Enabled

-

[Sound.Looped](/docs/reference/engine/classes/Sound#Looped)  = Enabled

-

[Sound.RollOffMaxDistance](/docs/reference/engine/classes/Sound#RollOffMaxDistance)  = 60

-

[Sound.RollOffMinDistance](/docs/reference/engine/classes/Sound#RollOffMinDistance)  = 15

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/car-part-volume.png) The edges of our part can be seen in white outlining the car.

This process allowed the sound to emit from the entire surface of the invisible part. If the player was inside of the part, the raindrop audio would play all around the player's head. The larger you make your own volumetric audio emitters, the more spread and area the volumetric sound will cover, so experiment with different sizes and shapes for your emitter to get the soundscape you want for your own games!

## [Nested SoundGroup mixing](#nested-soundgroup-mixing)[](#nested-soundgroup-mixing)

As human beings, we like to think we are great multitaskers, but in reality it's quite difficult for us to focus on more than 2 things at once, especially in regards to listening to multiple audio sources! In The Mystery Of Duvall Drive, there could be a dozen sounds playing at any given time, such as ambience, music, footsteps, rain, or UI notifications, but we needed a way to make sure that it didn't feel as though they were all competing for your attention. For this reason, we decided to nest [SoundGroups](/docs/reference/engine/classes/SoundGroup)  in child/parent relationships so we could create an audio mix to ensure both the organization and consistency of the project's sound design.

[Nesting SoundGroups](/docs/sound/groups#nest-soundgroups)  is a new feature that allows you to organize [SoundGroups](/docs/reference/engine/classes/SoundGroup)  together into meaningful categories under a mix tree for further audio functionality, such as being able to fine-tune the volume of many audio sources at once, or apply common audio effects at a lower CPU cost. As we took a very progression-oriented approach to the mix in this project, we wanted sounds that directly contribute to player progression in the puzzles (puzzle and key object interaction audio) to be given priority over sounds that don't contribute to their progression (wind, rain, footsteps, atmosphere audio). By nesting child [SoundGroups](/docs/reference/engine/classes/SoundGroup)  into parent [SoundGroups](/docs/reference/engine/classes/SoundGroup)  of different priority levels, we could then add a [CompressorSoundEffect](/docs/reference/engine/classes/CompressorSoundEffect)  that would lower the volume of low-priority [SoundGroups](/docs/reference/engine/classes/SoundGroup)  in real time whenever audio from high-priority [SoundGroups](/docs/reference/engine/classes/SoundGroup)  started playing. This process is called [ducking](/docs/sound/groups#ducking) .

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/main-audio-mixer.png) A collapsed view of our main audio mixer for this game.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/compressorsoundeffect-properties.png) The Properties window for the CompressorSoundEffect that we added to the low-priority SoundGroup.

The [CompressorSoundEffect](/docs/reference/engine/classes/CompressorSoundEffect)  has five main properties we had to set in order to lower the volume of low-priority audio whenever high-priority audio played:

| Property | | Description |
| --- | --- |
| [CompressorSoundEffect.Threshold](/docs/reference/engine/classes/CompressorSoundEffect#Threshold) | | How sensitive the compressor is to the incoming signal to lower the volume from a [SoundGroup](/docs/reference/engine/classes/SoundGroup) . The lower the number, the less loud the high-priority sound has to be to start taking effect.  |
| [CompressorSoundEffect.Ratio](/docs/reference/engine/classes/CompressorSoundEffect#Ratio) | | How much you want to lower low-priority sounds. A higher number basically means more volume ducking! |
| [CompressorSoundEffect.Attack](/docs/reference/engine/classes/CompressorSoundEffect#Attack)  and [CompressorSoundEffect.Release](/docs/reference/engine/classes/CompressorSoundEffect#Release) | | How quickly the volume reduction fades in and out when activated. There are no hard and fast rules here, tune them to fit your soundscape using your own judgment and ears!  |
| [CompressorSoundEffect.Sidechain](/docs/reference/engine/classes/CompressorSoundEffect#Sidechain) | | Which [SoundGroup](/docs/reference/engine/classes/SoundGroup)  we want to duck the low-priority sounds, as we have placed the compressor on the Low  [SoundGroup](/docs/reference/engine/classes/SoundGroup) . This is what makes the magic happen!  |

For more information on these properties and the whole process of prioritizing audio from different [SoundGroups](/docs/reference/engine/classes/SoundGroup) , see [Nesting SoundGroups](/docs/sound/groups#nest-soundgroups)  and [Ducking](/docs/sound/groups#ducking) .

[Previous](/docs/resources/the-mystery-of-duvall-drive/develop-a-moving-world)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
