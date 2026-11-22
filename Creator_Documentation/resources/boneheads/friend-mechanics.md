<!-- Source: https://create.roblox.com/docs/en-us/resources/boneheads/friend-mechanics.md -->

---
title: "Friend co-op mechanics"
url: /docs/en-us/resources/boneheads/friend-mechanics
last_updated: 2026-11-20T18:47:28Z
description: "Explains how Boneheads designs for chaotic co-op play with stealable objects, throwable heads and clothing, group puzzles, voice effects, and fall recovery."
---

# Friend co-op mechanics

[**Boneheads**](https://github.com/Roblox/resources/tree/main/experiences/boneheads) is a "friend co-op" game featuring loose physics and clumsy controls, where a lot of the fun comes from players interfering with each other. Its systems let players steal held objects, knock off and exchange heads, trade layered clothing, stand in for each other on puzzles, and talk through voice effects.

## Shared objects to steal, throw, and wear

The head on each skeleton is a separate, carryable object. A head on its owner's shoulders can't be directly taken off by another player, but it can be knocked off if they're hit by a thrown prop. Once loose, the head is available for anyone to pick up, throw, or wear. Players can also steal an object directly from another player's hands when no free carryable is within reach.

_Stealing mechanics in action, with a 1-second cooldown to prevent immediate steal‑backs._

A shared collision module inside `ReplicatedStorage/Systems/Collision` reports impacts to both the knock‑off and sound systems, with each listener applying its own speed threshold and cooldown. This extends a single physical event to every carryable without making each carryable implement specific behaviors itself.

## Heads as the focal point

Character heads remain the visual and audible focus, even if a head leaves its owner's body. The owner's camera follows its head, including after a respawn, and voice chat is emitted from the head model (with matching jaw movement) so that the owner's voice comes from the head's position. Similarly, [chat bubbles](/docs/en-us/chat/bubble-chat.md) appear above the head instead of the body.

## Puzzles designed for groups

[Puzzle mechanisms](/docs/en-us/resources/boneheads/puzzle-mechanics.md) coordinate through a replicated `_activated` [attribute](/docs/en-us/studio/properties.md#instance-attributes) instead of calling each other directly. The following mechanisms are designed for groups:

###### Pressure Plates

_Pressure plates activate when any unanchored object touches them, including a character. A player can throw an object onto a plate instead of standing on it._

###### Counter Gates

_Counter gates count active inputs, displaying the current and required totals. A downstream door or bridge can use the counter's state as an input._

###### Player Counters

_Player counters activate when every player currently in the server stands in the zone. After activation, the counter remains active even if a player leaves._

## Voice effects by zone

Locally on each client, every player's voice passes through a chain of [audio effects](/docs/en-us/audio/effects.md) before it reaches their head: [pitch shift](/docs/en-us/audio/effects.md#pitch-shift), [chorus](/docs/en-us/audio/effects.md#chorus), [flanger](/docs/en-us/audio/effects.md#flanger), [distortion](/docs/en-us/audio/effects.md#distortion), [equalizer](/docs/en-us/audio/effects.md#equalizer), [echo](/docs/en-us/audio/effects.md#echo), and [reverb](/docs/en-us/audio/effects.md#reverb).

A few invisible parts tagged as `VoiceZone` are placed around the dungeon and each carries a `VoicePreset` attribute. Every `0.4` seconds, the client checks whether another character's `Class.Humanoid.RootPart` is inside a zone box and applies that zone's preset to their voice.

| Preset | Sound | Example |
| --- | --- | --- |
| `Helium` | Pitch raised by about 70%. | |
| `DeepMonster` | Lowered pitch, boosted bass, and light reverb. | |
| `WalkieTalkie` | Narrow midrange, distortion, and a flanger. | |
| `AlienHivemind` | Raised pitch with a fast flanger and a short echo. | |
| `CaveEcho` | Long reverb. | |
| `Robot` | Slightly raised pitch, narrow midrange, and distortion. | |
| `MountainYodel` | A short echo without reverb. | |