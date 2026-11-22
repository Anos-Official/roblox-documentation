<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AnimationClip -->

AnimationClip | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AnimationClip](/docs/nl-nl/reference/engine/classes/AnimationClip)

Nederlands

Feedback

Engine-klasse

AnimationClip

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AnimationClip)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Length](#Length) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[Loop](#Loop) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Priority](#Priority) :[Enum.AnimationPriority](/docs/nl-nl/reference/engine/enums/AnimationPriority)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation) , [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)

---

API-referentie

Eigenschappen

Length

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Animation

AnimationClip.Length :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Loop

Parallel lezen

Mogelijkheden: Animation

AnimationClip.Loop :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Priority

Parallel lezen

Mogelijkheden: Animation

AnimationClip.Priority :[Enum.AnimationPriority](/docs/nl-nl/reference/engine/enums/AnimationPriority)

Codevoorbeelden

KeyframeSequence Instantie

```

-- Maak de sequentie

local keyframeSequence = Instance.new("KeyframeSequence")

keyframeSequence.Loop = false

keyframeSequence.Priority = Enum.AnimationPriority.Action

-- Maak een keyframe

local keyframe = Instance.new("Keyframe")

keyframe.Time = 0

-- Maak voorbeeldposes

local rootPose = Instance.new("Pose")

rootPose.Name = "HumanoidRootPart"

rootPose.Weight = 0

local lowerTorsoPose = Instance.new("Pose")

lowerTorsoPose.Name = "LowerTorso"

lowerTorsoPose.Weight = 1

-- Stel de sequentiehiërarchie in

rootPose:AddSubPose(lowerTorsoPose)

keyframe:AddPose(rootPose)

keyframeSequence:AddKeyframe(keyframe)

-- Maak de sequentie ouder

keyframeSequence.Parent = workspace

```

Feedback geven

---

Ga naar

▼

AnimationClip

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Length](#Length)

[Loop](#Loop)

[Priority](#Priority)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
