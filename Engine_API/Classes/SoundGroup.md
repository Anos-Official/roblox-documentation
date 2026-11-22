<!-- Source: https://create.roblox.com/docs/reference/engine/classes/SoundGroup -->

SoundGroup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/SoundGroup.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [SoundGroup](/docs/reference/engine/classes/SoundGroup)

English

Feedback

Engine Class

SoundGroup

---

## Summary

Properties

|

[Volume](#Volume) :[number](/docs/luau/numbers)

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Volume

Read Parallel

Capabilities: LegacySound

SoundGroup.Volume :[number](/docs/luau/numbers)

Code Samples

SoundGroups

```

local SoundService = game:GetService("SoundService")

-- create a sound group

local soundGroup = Instance.new("SoundGroup")

soundGroup.Parent = SoundService

-- create a sound

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://9120386436"

sound.Looped = true

sound.PlaybackSpeed = 2

sound.SoundGroup = soundGroup

sound.Parent = workspace

-- play the sound

sound:Play()

task.wait(10)

-- change the volume

soundGroup.Volume = 0.1

task.wait(3)

-- return the volume

soundGroup.Volume = 0.5

task.wait(4)

-- add a sound effect

local reverb = Instance.new("ReverbSoundEffect")

reverb.Parent = soundGroup

```

Provide feedback

---

Jump to

▼

SoundGroup

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Volume](#Volume)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
