<!-- Source: https://create.roblox.com/docs/audio/effects -->

Audio effects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/audio/effects.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Audio](/docs/audio)

# Audio effects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/audio/effects.md)

Audio effects non-destructively modify or enhance audio streams. You can apply these effects to make your audio more immersive within your game, such as using an [AudioEqualizer](/docs/reference/engine/classes/AudioEqualizer)  object to make rain sound muffled, [AudioCompressor](/docs/reference/engine/classes/AudioCompressor)  object to control a sound's maximum volume, or [AudioReverb](/docs/reference/engine/classes/AudioReverb)  to add more realistic reflections of sound in interior spaces.

## [Apply audio effects](#apply-audio-effects)[](#apply-audio-effects)

You can apply audio effects to your audio streams by wiring up the effect within your 2D audio or 3D audio setup before it reaches the player's ears. For example, to review the setup instructions in [Audio objects](/docs/audio/objects#2d-audio) , 2D audio requires an audio player to produce the stream, a physical hardware device like a speaker or headphones, and a wire to carry the audio stream from the audio player to the output device.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/2D-Audio-Diagram.png)

If you keep this setup the way it is, the audio stream from the asset ID plays as it was originally recorded. However, if you want to apply an audio effect to this audio stream, you must introduce the audio effect in the middle of the configuration so that the audio stream transmits through the effect before it transmits to the output device.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Single.png)

Roblox's modular audio objects also allow you to wire multiple audio players through an audio effect, meaning that you don't have to have multiple audio effect objects with the same settings. This provides a lot of flexibility in how you customize multiple audio sources at once.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Multiple.png)

In addition, you can apply multiple audio effects to the same audio stream to further customize your audio. As the audio stream transmits from the audio player to the device output, it's important to note that the order of the audio effects impacts the custom sound. For example, if you were to apply an [AudioChorus](/docs/reference/engine/classes/AudioChorus)  effect first, then an [AudioDistortion](/docs/reference/engine/classes/AudioDistortion)  effect second, your custom sound may sound different from a configuration that applies the [AudioDistortion](/docs/reference/engine/classes/AudioDistortion)  effect before the [AudioChorus](/docs/reference/engine/classes/AudioChorus)  effect.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Layered.png)

Each audio effect you apply has additional properties you can adjust until you achieve the type of sound you desire. For more information on these properties, see each audio effect's API page.

## [Types](#types)[](#types)

### [Equalizer](#equalizer)[](#equalizer)

[AudioEqualizer](/docs/reference/engine/classes/AudioEqualizer)  allows for control of the volume of various frequency ranges. This audio effect is useful to highlight or minimize particular elements of audio, such as muffling all audio in your game when a player goes underwater.

Without [AudioEqualizer](/docs/reference/engine/classes/AudioEqualizer)  effect

With [AudioEqualizer](/docs/reference/engine/classes/AudioEqualizer)  effect

### [Compressor](#compressor)[](#compressor)

[AudioCompressor](/docs/reference/engine/classes/AudioCompressor)  reduces the dynamic range of audio by lowering the volume of the highest parts of a source while at the same time raising the overall volume. This audio effect is useful to set a consistent volume for players to hear even if you record audio while whispering or speaking loudly. You can also use this dynamic effect to prioritize audio streams over another through the process of ducking.

Without [AudioCompressor](/docs/reference/engine/classes/AudioCompressor)  effect

With [AudioCompressor](/docs/reference/engine/classes/AudioCompressor)  effect

### [Reverb](#reverb)[](#reverb)

[AudioReverb](/docs/reference/engine/classes/AudioReverb)  simulates the effect of sounds bouncing off of several surfaces. This audio effect is useful to simulate more realistic reflections of sounds in interior spaces, such as bouncing a basketball inside a gymnasium, or playing rock music in a stadium.

Without [AudioReverb](/docs/reference/engine/classes/AudioReverb)  effect

With [AudioReverb](/docs/reference/engine/classes/AudioReverb)  effect

### [Chorus](#chorus)[](#chorus)

[AudioChorus](/docs/reference/engine/classes/AudioChorus)  simulates the effect of multiple vocals or instruments playing simultaneously by taking the original sound and overlaying copies, each with slight variations in pitch. This audio effect is useful for simulating a robotic or futuristic quality to your audio.

Without [AudioChorus](/docs/reference/engine/classes/AudioChorus)  effect

With [AudioChorus](/docs/reference/engine/classes/AudioChorus)  effect

### [Distortion](#distortion)[](#distortion)

[AudioDistortion](/docs/reference/engine/classes/AudioDistortion)  simulates the effect that would occur when overdriving older style audio equipment. This audio effect causes clipping in the sound and adds a general "fuzziness," which is useful for either adding intensity and character to musical instruments.

Without [AudioDistortion](/docs/reference/engine/classes/AudioDistortion)  effect

With [AudioDistortion](/docs/reference/engine/classes/AudioDistortion)  effect

### [Echo](#echo)[](#echo)

[AudioEcho](/docs/reference/engine/classes/AudioEcho)  causes a sound to repeat on a delay with diminishing volume, simulating the real effect of an echo that bounces off of hard surfaces, such as walls and caves.

Without [AudioEcho](/docs/reference/engine/classes/AudioEcho)  effect

With [AudioEcho](/docs/reference/engine/classes/AudioEcho)  effect

### [Flanger](#flanger)[](#flanger)

[AudioFlanger](/docs/reference/engine/classes/AudioFlanger)  creates a sweeping or whooshing effect by copying the original audio signal and playing it slightly offset and modulated on top of the original. This audio effect is useful for adding strange, otherworldly digital quality to your audio. For example, you can use it on an air conditioner recording to make a sci‑fi spaceship engine rumble.

Without [AudioFlanger](/docs/reference/engine/classes/AudioFlanger)  effect

With [AudioFlanger](/docs/reference/engine/classes/AudioFlanger)  effect

### [Pitch Shift](#pitch-shift)[](#pitch-shift)

[AudioPitchShifter](/docs/reference/engine/classes/AudioPitchShifter)  raises or lowers pitch without changing the playback speed. This audio effect is useful for changing the scale of your sounds. You can use it to make small sounds feel huge by pitching them down or conversely pitch sounds up to make an explosion sound more like a balloon pop.

Without [AudioPitchShifter](/docs/reference/engine/classes/AudioPitchShifter)  effect

With [AudioPitchShifter](/docs/reference/engine/classes/AudioPitchShifter)  effect

### [Tremolo](#tremolo)[](#tremolo)

[AudioTremolo](/docs/reference/engine/classes/AudioTremolo)  creates a trembling effect on a sound by varying its volume up and down. This dynamic effect is useful to transform instrument sounds into a wavy, dreamlike quality, or to create swells and dips in weather‑related audio.

Without [AudioTremolo](/docs/reference/engine/classes/AudioTremolo)  effect

With [AudioTremolo](/docs/reference/engine/classes/AudioTremolo)  effect

### [Fader](#fader)[](#fader)

The [AudioFader](/docs/reference/engine/classes/AudioFader)  adjusts the volume of audio streams to be either higher or lower. This audio effect is useful to control the volume and audio effects properties of multiple audio streams at once.

### [Analyzer](#analyzer)[](#analyzer)

The [AudioAnalyzer](/docs/reference/engine/classes/AudioAnalyzer)  analyzes volume and frequency contents. This audio effect is useful for getting information to understanding how your audio is working together, both in volume and frequency content.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
