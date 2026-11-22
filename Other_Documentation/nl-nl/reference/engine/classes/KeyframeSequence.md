<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/KeyframeSequence -->

KeyframeSequence | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AnimationClip](/docs/nl-nl/reference/engine/classes/AnimationClip)
8. /
9. [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)

Nederlands

Feedback

Engine-klasse

KeyframeSequence

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/KeyframeSequence)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AuthoredHipHeight](#AuthoredHipHeight) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |

Methoden

|

[AddKeyframe](#AddKeyframe) (keyframe :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
|

[GetKeyframes](#GetKeyframes) () : {[Keyframe](/docs/nl-nl/reference/engine/classes/Keyframe) }

 |
|

[RemoveKeyframe](#RemoveKeyframe) (keyframe :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |

Overgenomen leden

3  overgenomen van [AnimationClip](/docs/nl-nl/reference/engine/classes/AnimationClip)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Krijg de lengte van KeyframeSequence

```

local function getSequenceLength(keyframeSequence)

	local length = 0

	for _, keyframe in pairs(keyframeSequence:GetKeyframes()) do

		if keyframe.Time > length then

			length = keyframe.Time

		end

	end

	return length

end

local keyframeSequence = Instance.new("KeyframeSequence")

getSequenceLength(keyframeSequence)

```

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

---

API-referentie

Eigenschappen

AuthoredHipHeight

Verborgen

Plugin-beveiliging

Parallel lezen

Mogelijkheden: Animation

KeyframeSequence.AuthoredHipHeight :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

AddKeyframe

Mogelijkheden: Animation

KeyframeSequence:AddKeyframe (keyframe :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

keyframe :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

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

GetKeyframes

Mogelijkheden: Animation

KeyframeSequence:GetKeyframes () : {[Keyframe](/docs/nl-nl/reference/engine/classes/Keyframe) }

Teruggaves

{[Keyframe](/docs/nl-nl/reference/engine/classes/Keyframe) }

Codevoorbeelden

Krijg de lengte van KeyframeSequence

```

local function getSequenceLength(keyframeSequence)

	local length = 0

	for _, keyframe in pairs(keyframeSequence:GetKeyframes()) do

		if keyframe.Time > length then

			length = keyframe.Time

		end

	end

	return length

end

local keyframeSequence = Instance.new("KeyframeSequence")

getSequenceLength(keyframeSequence)

```

Feedback geven

---

RemoveKeyframe

Mogelijkheden: Animation

KeyframeSequence:RemoveKeyframe (keyframe :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

keyframe :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Codevoorbeelden

KeyframeSequence VerwijderKeyframe

```

local keyframeSequence = Instance.new("KeyframeSequence")

keyframeSequence.Parent = workspace

local keyframe = Instance.new("Keyframe")

keyframeSequence:AddKeyframe(keyframe)

task.wait(2)

keyframeSequence:RemoveKeyframe(keyframe)

```

Feedback geven

---

Ga naar

▼

KeyframeSequence

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[AuthoredHipHeight](#AuthoredHipHeight)

[Methoden](#methods)

[AddKeyframe()](#AddKeyframe)

[GetKeyframes()](#GetKeyframes)

[RemoveKeyframe()](#RemoveKeyframe)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
