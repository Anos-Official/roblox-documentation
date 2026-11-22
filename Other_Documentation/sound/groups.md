<!-- Source: https://create.roblox.com/docs/sound/groups -->

Sound groups | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/sound/groups.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Learn](/docs/en-us/learn)

# Sound groups

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/sound/groups.md)

[SoundGroup](/docs/reference/engine/classes/SoundGroup)  objects are now discouraged in favor of the more robust functionality of audio objects. For more information, see [Audio objects](/docs/audio/objects) .

A [SoundGroup](/docs/reference/engine/classes/SoundGroup)  is an audio mixer  that groups multiple audio objects, such as [Sound](/docs/reference/engine/classes/Sound)  objects or additional [SoundGroups](/docs/reference/engine/classes/SoundGroup) , allowing you to control the volume and dynamic effects properties of multiple audio signals at once. Useful applications include:

-

[Assigning audio](#assign-audio-objects-to-sound-groups)  to SoundEffects  and BackgroundMusic  sound groups so that you can adjust each group's master volume for optimal audio balancing.

-

[Nesting sound groups](#nest-sound-groups)  into meaningful categories under a mix tree.

-

Grouping all sounds that need a specific [dynamic effect](/docs/sound/dynamic-effects) . For example, you can group all sounds inside a cave to a Cave  sound group, then apply a [ReverbSoundEffect](/docs/reference/engine/classes/ReverbSoundEffect)  to simulate the sounds reflecting off of the cave's environment.

When creating [SoundGroups](/docs/reference/engine/classes/SoundGroup) , it's best to keep them all in a single location for organizational purposes as you continue to add and edit audio within your game. The following example stores the new [SoundGroup](/docs/reference/engine/classes/SoundGroup)  under [SoundService](/docs/reference/engine/classes/SoundService) , as this service determines how [Sound](/docs/reference/engine/classes/Sound)  objects play in games.

## [Create sound groups](#create-sound-groups)[](#create-sound-groups)

To create a [SoundGroup](/docs/reference/engine/classes/SoundGroup) :

1.

In the Explorer  window, hover over [SoundService](/docs/reference/engine/classes/SoundService)  and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a [SoundGroup](/docs/reference/engine/classes/SoundGroup) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/SoundService-SoundGroup.png)

3.

Triple-click the new sound group and rename it according to its purpose, such as SoundEffects  or BackgroundMusic .

## [Assign audio objects to sound groups](#assign-audio-objects-to-sound-groups)[](#assign-audio-objects-to-sound-groups)

[SoundGroups](/docs/reference/engine/classes/SoundGroup)  don't have the typical parent-child behavior of other forms of object grouping like [Models](/docs/reference/engine/classes/Model)  and [Folders](/docs/reference/engine/classes/Folder) . Instead, you must assign  each [Sound](/docs/reference/engine/classes/Sound)  object to its applicable [SoundGroup](/docs/reference/engine/classes/SoundGroup)  object, regardless of either object's location in the workspace hierarchy, because where you place the [Sound](/docs/reference/engine/classes/Sound)  object changes where audio emits from, not the [SoundGroup](/docs/reference/engine/classes/SoundGroup)  object itself. For more information, see [sound objects](/docs/sound/objects) .

To assign a [Sound](/docs/reference/engine/classes/Sound)  object to a [SoundGroup](/docs/reference/engine/classes/SoundGroup) :

1.

In the Explorer  window, select a sound object.

2.

In the Properties  window, click the SoundGroup  property field. Your cursor changes.

3.

In the Explorer  window, click on the sound group object you want to assign your sound object to. The sound object's SoundGroup  property updates accordingly.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sound-SoundGroup.png)

## [Nest sound groups](#nest-sound-groups)[](#nest-sound-groups)

You can nest [SoundGroups](/docs/reference/engine/classes/SoundGroup)  together into meaningful categories under a mix tree for organization and scripting purposes. When you're planning the parent-child relationships in your mix, consider the different sound categories in your game, and how important they should be for the listener. For example, player ability sounds are likely much more important to gameplay than environmental sounds. If you group them into separate parent [SoundGroups](/docs/reference/engine/classes/SoundGroup) , you can easily access and [adjust their volume levels](#adjust-volume)  as you add more [Sound](/docs/reference/engine/classes/Sound)  objects to your game.

To nest [SoundGroups](/docs/reference/engine/classes/SoundGroup) :

1.

In the Explorer  window, click-and-drag a sound group over the sound group you want to nest it under. The sound group name becomes translucent, and your cursor changes to a plus icon.

2.

Drop the sound group. It displays as a child of the sound group you nested it under.

## [Adjust volume](#adjust-volume)[](#adjust-volume)

There are two main ways to think about a sound's volume: how loud the sound is by itself, and how loud it is in relation to other sounds. For example, a waterfall sounds loud when you play it by itself, but when you compare it to other sound effects like tires screeching, it likely sounds much quieter. To ensure that each sound plays at the correct volume for your game, you can either [add multipliers](#add-multipliers)  to [SoundGroups](/docs/reference/engine/classes/SoundGroup) , or prioritize audio from one [SoundGroup](/docs/reference/engine/classes/SoundGroup)  over another through the process of [ducking](#ducking) .

### [Add multipliers](#add-multipliers)[](#add-multipliers)

The [Volume](/docs/reference/engine/classes/SoundGroup#Volume)  property of a [SoundGroup](/docs/reference/engine/classes/SoundGroup)  lets you apply a volume multiplier  between 0  and 10  to each of its child audio objects while they retain their relative volumes. This means that if a [Sound](/docs/reference/engine/classes/Sound)  object has a volume of 0.5  and you child it to a [SoundGroup](/docs/reference/engine/classes/SoundGroup)  that has a volume multiplier of 0.5 , the effective volume of the [Sound](/docs/reference/engine/classes/Sound)  object is 0.25 .

This property is useful when you want to test volume changes to different [SoundGroups](/docs/reference/engine/classes/SoundGroup)  without having to manually change the volume of each [Sound](/docs/reference/engine/classes/Sound)  object. For example, if you want to check what it'd sound like to increase the volume of all of your game's music, you can create a Music  [SoundGroup](/docs/reference/engine/classes/SoundGroup)  for every musical [Sound](/docs/reference/engine/classes/Sound)  object or [SoundGroup](/docs/reference/engine/classes/SoundGroup) , then apply a volume multiplier of 2 .

### [Ducking](#ducking)[](#ducking)

You can prioritize audio from one [SoundGroup](/docs/reference/engine/classes/SoundGroup)  over another through the [CompressorSoundEffect](/docs/reference/engine/classes/CompressorSoundEffect) . This dynamic effect allows you to duck , or reduce in volume, [Sound](/docs/reference/engine/classes/Sound)  objects in low-priority [SoundGroups](/docs/reference/engine/classes/SoundGroup)  whenever [Sound](/docs/reference/engine/classes/Sound)  objects in high-priority [SoundGroups](/docs/reference/engine/classes/SoundGroup)  start to play. This allows the listener to concentrate on the specific audio that you want them to pay attention to while not suddenly cutting the audio from low-priority sounds completely. When the high-priority audio finishes playing, low-priority audio returns to its original volume, keeping the listener immersed in your game.

The sounds that you choose to duck depend on the needs of your specific game. For example, one game might benefit from reducing the volume of background music whenever a GUI notification plays, while others might benefit from reducing the volume of GUI notifications whenever dialogue plays. The following reference mix tree prioritizes [Sound](/docs/reference/engine/classes/Sound)  objects in the high-priority GUI Notifications  and Weapons  [SoundGroups](/docs/reference/engine/classes/SoundGroup)  while de-prioritizing [Sound](/docs/reference/engine/classes/Sound)  objects in low-priority 3D  and 2D Ambience  [SoundGroups](/docs/reference/engine/classes/SoundGroup) .

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-groups/Mix-Tree.png)

The [CompressorSoundEffect](/docs/reference/engine/classes/CompressorSoundEffect)  has four main properties you must set in order to duck audio whenever your high priority audio plays:

| Property | | Description |
| --- | --- |
| [Threshold](/docs/reference/engine/classes/CompressorSoundEffect#Threshold) | | The threshold decibel level that Studio applies ducking. You can set this property to any value between -80  (full compression) and 0  (full volume). |
| [Attack](/docs/reference/engine/classes/CompressorSoundEffect#Attack) | | The rate you want audio to duck. You can set this property to any value between 0.001  and 1  second. |
| [Release](/docs/reference/engine/classes/CompressorSoundEffect#Release) | | The rate you want the audio to stop ducking. You can set this property to any value between 0.001  and 1  second. |
| [Ratio](/docs/reference/engine/classes/CompressorSoundEffect#Ratio) | | The ratio of how much ducking you want to occur between the audio object that Studio prioritizes and the audio object that ducks. You can set this property to any value between 1  (no compression) and 50  (fifty times the compression). |

The values of each of these properties are highly dependent on your specific audio. Each source audio has a different volume, and you might only need to duck by a minimal amount in order for your high priority audio to have emphasis in your game.

To prioritize [SoundGroups](/docs/reference/engine/classes/SoundGroup)  through the [CompressorSoundEffect](/docs/reference/engine/classes/CompressorSoundEffect) :

1.

In the Explorer  window, navigate to the SoundGroup you want to duck and insert a CompressorSoundEffect.

1.

Hover over the SoundGroup  and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a CompressorSoundEffect .

2.

Select the CompressorSoundEffect , then navigate to the Properties  window.

3.

Select the SideChain  property. Your cursor changes.

4.

Select the Sound  or SoundGroup  object that you want to prioritize when the compressor applies. The SideChain  property updates accordingly.

5.

In the Threshold property  field, input the decibel level in which you want the ducking to start.

6.

In the Attack  property field, input how quickly you want audio to duck.

7.

In the Release  property field, input how quickly you want the audio to stop ducking.

8.

In the Ratio  property field, input the ratio of how much compression you want to occur between the audio object that ducks and the audio object that Studio prioritizes.

9.

OPTIONAL

 Playtest your game to see if the audio sounds correct. If not, adjust the CompressorSoundEffect  properties accordingly.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
