<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Animator -->

Animator | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Animator.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Animator](/docs/reference/engine/classes/Animator)

English

Feedback

Engine Class

Animator

---

## Summary

Properties

|

[EvaluationThrottled](#EvaluationThrottled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[PreferLodEnabled](#PreferLodEnabled) :[boolean](/docs/luau/booleans)

 |

Methods

|

[ApplyJointVelocities](#ApplyJointVelocities) (motors :  Variant ) : ()

 |
|

[GetPlayingAnimationTracks](#GetPlayingAnimationTracks) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetTrackByAnimationId](#GetTrackByAnimationId) (animationId :  ContentId ) :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack) ?

 |
|

[LoadAnimation](#LoadAnimation) (animation :  [Animation](/docs/reference/engine/classes/Animation) ) :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack)

 |
|

[StepAnimations](#StepAnimations) (deltaTime :  [number](/docs/luau/numbers) ) : ()

 |

Events

|

[AnimationPlayed](#AnimationPlayed) (animationTrack :  [AnimationTrack](/docs/reference/engine/classes/AnimationTrack) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

EvaluationThrottled

Read Only

Not Replicated

Write Parallel

Capabilities: Animation

Animator.EvaluationThrottled :[boolean](/docs/luau/booleans)

Code Samples

Evaluation Throttled

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

Provide feedback

---

PreferLodEnabled

Read Parallel

Capabilities: Animation

Animator.PreferLodEnabled :[boolean](/docs/luau/booleans)

Provide feedback

---

Methods

ApplyJointVelocities

Capabilities: Animation

Animator:ApplyJointVelocities (motors : Variant ) : ()

Parameters

|

motors : Variant

 |

Returns

()

Provide feedback

---

GetPlayingAnimationTracks

Capabilities: Animation

Simulation Access

Animator:GetPlayingAnimationTracks () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetTrackByAnimationId

Capabilities: Animation

Simulation Access

Animator:GetTrackByAnimationId (animationId : ContentId ) :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack) ?

Parameters

|

animationId : ContentId

 |

Returns

[AnimationTrack](/docs/reference/engine/classes/AnimationTrack) ?

Code Samples

Get Animation Track by ID

```

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local ANIM_ID = "rbxassetid://2515090838"

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

-- Ensure that the character's humanoid contains an Animator object

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Create a new Animation instance and assign an animation asset ID

local kickAnimation = Instance.new("Animation")

kickAnimation.AnimationId = ANIM_ID

-- Load the animation onto the animator

local kickAnimationTrack = animator:LoadAnimation(kickAnimation)

-- Play the animation track after a short delay

task.wait(3)

kickAnimationTrack:Play()

local startTime = tick()

RunService:BindToSimulation(function(deltaTime: number)

	if tick() - startTime > 1 then

		-- Get track by ID and stop its playback

		local kickTrack = animator:GetTrackByAnimationId(ANIM_ID)

		if kickTrack and kickTrack.IsPlaying then

			kickTrack:Stop()

		end

	end

end)

```

Provide feedback

---

LoadAnimation

Capabilities: Animation

Simulation Access

Animator:LoadAnimation (animation :[Animation](/docs/reference/engine/classes/Animation) ) :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack)

Parameters

|

animation :[Animation](/docs/reference/engine/classes/Animation)

 |

Returns

[AnimationTrack](/docs/reference/engine/classes/AnimationTrack)

Provide feedback

---

StepAnimations

Capabilities: Animation, PluginOrOpenCloud

Animator:StepAnimations (deltaTime :[number](/docs/luau/numbers) ) : ()

Parameters

|

deltaTime :[number](/docs/luau/numbers)

 |

Returns

()

Code Samples

Preview Animation in Studio

```

local RunService = game:GetService("RunService")

local function previewAnimation(model, animation)

	-- Find the AnimationController and Animator

	local animationController = model:FindFirstChildOfClass("AnimationController")

	local animator = animationController and animationController:FindFirstChildOfClass("Animator")

	if not animator then return end

	-- Load the Animation to create an AnimationTrack

	local track = animationController:LoadAnimation(animation)

	track:Play()

	-- Preview the animation

	local startTime = tick()

	while (tick() - startTime) < track.Length do

		local step = RunService.Heartbeat:wait()

		animator:StepAnimations(step)

	end

	-- Stop the animation

	track:Stop(0)

	animator:StepAnimations(0)

	-- Reset the joints

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

Provide feedback

---

Events

AnimationPlayed

Capabilities: Animation

Animator.AnimationPlayed (animationTrack :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

animationTrack :[AnimationTrack](/docs/reference/engine/classes/AnimationTrack)

 |

Provide feedback

---

Jump to

▼

Animator

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[EvaluationThrottled](#EvaluationThrottled)

[PreferLodEnabled](#PreferLodEnabled)

[Methods](#methods)

[ApplyJointVelocities()](#ApplyJointVelocities)

[GetPlayingAnimationTracks()](#GetPlayingAnimationTracks)

[GetTrackByAnimationId()](#GetTrackByAnimationId)

[LoadAnimation()](#LoadAnimation)

[StepAnimations()](#StepAnimations)

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
