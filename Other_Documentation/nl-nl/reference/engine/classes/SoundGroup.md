<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/SoundGroup -->

SoundGroup | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)

Nederlands

Feedback

Engine-klasse

SoundGroup

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/SoundGroup)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Volume](#Volume) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Volume

Parallel lezen

Mogelijkheden: LegacySound

SoundGroup.Volume :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Geluidsgroepen

```

local SoundService = game:GetService("SoundService")

-- maak een geluidsgroep aan

local soundGroup = Instance.new("SoundGroup")

soundGroup.Parent = SoundService

-- maak een geluid aan

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://9120386436"

sound.Looped = true

sound.PlaybackSpeed = 2

sound.SoundGroup = soundGroup

sound.Parent = workspace

-- speel het geluid af

sound:Play()

task.wait(10)

-- verander het volume

soundGroup.Volume = 0.1

task.wait(3)

-- herstel het volume

soundGroup.Volume = 0.5

task.wait(4)

-- voeg een geluidseffect toe

local reverb = Instance.new("ReverbSoundEffect")

reverb.Parent = soundGroup

```

Feedback geven

---

Ga naar

▼

SoundGroup

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Volume](#Volume)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
