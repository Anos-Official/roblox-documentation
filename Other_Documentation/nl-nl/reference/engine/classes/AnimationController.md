<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AnimationController -->

AnimationController | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AnimationController](/docs/nl-nl/reference/engine/classes/AnimationController)

Nederlands

Feedback

Engine-klasse

AnimationController

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AnimationController)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetPlayingAnimationTracks](#GetPlayingAnimationTracks) () :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
| --- | --- |
|

[LoadAnimation](#LoadAnimation) (animation :  [Animation](/docs/nl-nl/reference/engine/classes/Animation) ) :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)

Verouderd

 |

Evenementen

|

[AnimationPlayed](#AnimationPlayed) (animationTrack :  [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Een AnimationController gebruiken om niet-spelerobjecten te animeren

```

local InsertService = game:GetService("InsertService")

-- Laad een model voor demonstratie

local npcModel = InsertService:LoadAsset(516159357):GetChildren()[1]

npcModel.Name = "NPC"

npcModel.PrimaryPart.Anchored = true

npcModel:SetPrimaryPartCFrame(CFrame.new(0, 5, 0))

npcModel.Parent = workspace

-- Vervang de humanoid door een animationcontroller

local humanoid = npcModel:FindFirstChildOfClass("Humanoid")

humanoid:Destroy()

local animationController = Instance.new("AnimationController")

animationController.Parent = npcModel

-- Maak en laad een animatie

local animation = Instance.new("Animation")

animation.AnimationId = "http://www.roblox.com/asset/?id=507771019" -- Roblox dansemote

local animationTrack = animationController:LoadAnimation(animation)

-- Speel de animatie af

animationTrack:Play()

```

---

API-referentie

Methoden

GetPlayingAnimationTracks

Verouderd

Details weergeven

---

LoadAnimation

Verouderd

Details weergeven

---

Evenementen

AnimationPlayed

Verouderd

Details weergeven

---

Ga naar

▼

AnimationController

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[GetPlayingAnimationTracks()](#GetPlayingAnimationTracks)

[LoadAnimation()](#LoadAnimation)

[Evenementen](#events)

[AnimationPlayed](#AnimationPlayed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
