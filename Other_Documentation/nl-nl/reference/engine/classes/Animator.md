<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Animator -->

Animator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Animator](/docs/nl-nl/reference/engine/classes/Animator)

Nederlands

Feedback

Engine-klasse

Animator

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Animator)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[EvaluationThrottled](#EvaluationThrottled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[PreferLodEnabled](#PreferLodEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[ApplyJointVelocities](#ApplyJointVelocities) (motors :  Variant ) : ()

 |
|

[GetPlayingAnimationTracks](#GetPlayingAnimationTracks) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetTrackByAnimationId](#GetTrackByAnimationId) (animationId :  ContentId ) :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ?

 |
|

[LoadAnimation](#LoadAnimation) (animation :  [Animation](/docs/nl-nl/reference/engine/classes/Animation) ) :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)

 |
|

[StepAnimations](#StepAnimations) (deltaTime :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |

Evenementen

|

[AnimationPlayed](#AnimationPlayed) (animationTrack :  [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

EvaluationThrottled

Alleen-lezen

Niet gerepliceerd

Parallel schrijven

Mogelijkheden: Animation

Animator.EvaluationThrottled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Evaluatie Beperkt

```

local RunService = game:GetService("RunService")

local Workspace = game:GetService("Workspace")

local animationController = Instance.new("AnimationController")

local animator = Instance.new("Animator")

animator.Parent = animationController

animationController.Parent = Workspace

local neck = Instance.new("Motor6D")

local function computeNeckRotation()

    return CFrame.Angles(0, 0.01, 0)

end

RunService.PreSimulation:Connect(function()

    if not animator.EvaluationThrottled then

        neck.Transform = computeNeckRotation() * neck.Transform

    end

end)

```

Feedback geven

---

PreferLodEnabled

Parallel lezen

Mogelijkheden: Animation

Animator.PreferLodEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

ApplyJointVelocities

Mogelijkheden: Animation

Animator:ApplyJointVelocities (motors : Variant ) : ()

Parameters

|

motors : Variant

 |

Teruggaves

()

Feedback geven

---

GetPlayingAnimationTracks

Mogelijkheden: Animation

Toegang tot simulatie

Animator:GetPlayingAnimationTracks () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetTrackByAnimationId

Mogelijkheden: Animation

Toegang tot simulatie

Animator:GetTrackByAnimationId (animationId : ContentId ) :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ?

Parameters

|

animationId : ContentId

 |

Teruggaves

[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ?

Codevoorbeelden

Krijg Animatie Track op ID

```

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local ANIM_ID = "rbxassetid://2515090838"

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

-- Zorg ervoor dat het humanoid van het personage een Animator object bevat

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Maak een nieuwe Animatie instantie en wijs een animatie asset ID toe

local kickAnimation = Instance.new("Animation")

kickAnimation.AnimationId = ANIM_ID

-- Laad de animatie op de animator

local kickAnimationTrack = animator:LoadAnimation(kickAnimation)

-- Speel de animatie track af na een korte vertraging

task.wait(3)

kickAnimationTrack:Play()

local startTime = tick()

RunService:BindToSimulation(function(deltaTime: number)

	if tick() - startTime > 1 then

		-- Krijg track op ID en stop de afspelen

		local kickTrack = animator:GetTrackByAnimationId(ANIM_ID)

		if kickTrack and kickTrack.IsPlaying then

			kickTrack:Stop()

		end

	end

end)

```

Feedback geven

---

LoadAnimation

Mogelijkheden: Animation

Toegang tot simulatie

Animator:LoadAnimation (animation :[Animation](/docs/nl-nl/reference/engine/classes/Animation) ) :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)

Parameters

|

animation :[Animation](/docs/nl-nl/reference/engine/classes/Animation)

 |

Teruggaves

[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)

Feedback geven

---

StepAnimations

Mogelijkheden: Animation, PluginOrOpenCloud

Animator:StepAnimations (deltaTime :[number](/docs/nl-nl/luau/numbers) ) : ()

Parameters

|

deltaTime :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Codevoorbeelden

Voorbeeldanimatie in Studio

```

local RunService = game:GetService("RunService")

local function previewAnimation(model, animation)

	-- Zoek de AnimationController en Animator

	local animationController = model:FindFirstChildOfClass("AnimationController")

	local animator = animationController and animationController:FindFirstChildOfClass("Animator")

	if not animator then return end

	-- Laad de animatie om een AnimationTrack te creëren

	local track = animationController:LoadAnimation(animation)

	track:Play()

	-- Preview de animatie

	local startTime = tick()

	while (tick() - startTime) < track.Length do

		local step = RunService.Heartbeat:wait()

		animator:StepAnimations(step)

	end

	-- Stop de animatie

	track:Stop(0)

	animator:StepAnimations(0)

	-- Reset de gewrichten

	for _, descendant in pairs(model:GetDescendants()) do

		if descendant:IsA("Motor6D") then

			local joint = descendant

			joint.CurrentAngle = 0

			joint.Transform = CFrame.new()

		end

	end

end

local character = script.Parent

local animation = Instance.new("Animation")

animation.AnimationId = "rbxassetid://507765644"

previewAnimation(character, animation)

```

Feedback geven

---

Evenementen

AnimationPlayed

Mogelijkheden: Animation

Animator.AnimationPlayed (animationTrack :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

animationTrack :[AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)

 |

Feedback geven

---

Ga naar

▼

Animator

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[EvaluationThrottled](#EvaluationThrottled)

[PreferLodEnabled](#PreferLodEnabled)

[Methoden](#methods)

[ApplyJointVelocities()](#ApplyJointVelocities)

[GetPlayingAnimationTracks()](#GetPlayingAnimationTracks)

[GetTrackByAnimationId()](#GetTrackByAnimationId)

[LoadAnimation()](#LoadAnimation)

[StepAnimations()](#StepAnimations)

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
