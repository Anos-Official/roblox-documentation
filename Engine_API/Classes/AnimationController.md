<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AnimationController -->

AnimationController | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AnimationController.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AnimationController](/docs/reference/engine/classes/AnimationController)

English

Feedback

Engine Class

AnimationController

---

## Summary

Methods

|

[GetPlayingAnimationTracks](#GetPlayingAnimationTracks) () :[{any}](/docs/luau/tables#arrays)

Deprecated

 |
| --- | --- |
|

[LoadAnimation](#LoadAnimation) (animation :  [Animation](/docs/reference/engine/classes/Animation) ) :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack)

Deprecated

 |

Events

|

[AnimationPlayed](#AnimationPlayed) (animationTrack :  [AnimationTrack](/docs/reference/engine/classes/AnimationTrack) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Using an AnimationController to animation non-player objects

```

local InsertService = game:GetService("InsertService")

-- Load a model for demonstration

local npcModel = InsertService:LoadAsset(516159357):GetChildren()[1]

npcModel.Name = "NPC"

npcModel.PrimaryPart.Anchored = true

npcModel:SetPrimaryPartCFrame(CFrame.new(0, 5, 0))

npcModel.Parent = workspace

-- Replace the humanoid with an animationcontroller

local humanoid = npcModel:FindFirstChildOfClass("Humanoid")

humanoid:Destroy()

local animationController = Instance.new("AnimationController")

animationController.Parent = npcModel

-- Create and load an animation

local animation = Instance.new("Animation")

animation.AnimationId = "http://www.roblox.com/asset/?id=507771019" -- Roblox dance emote

local animationTrack = animationController:LoadAnimation(animation)

-- Play the animation

animationTrack:Play()

```

---

API Reference

Methods

GetPlayingAnimationTracks

Deprecated

Show details

---

LoadAnimation

Deprecated

Show details

---

Events

AnimationPlayed

Deprecated

Show details

---

Jump to

▼

AnimationController

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[GetPlayingAnimationTracks()](#GetPlayingAnimationTracks)

[LoadAnimation()](#LoadAnimation)

[Events](#events)

[AnimationPlayed](#AnimationPlayed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
