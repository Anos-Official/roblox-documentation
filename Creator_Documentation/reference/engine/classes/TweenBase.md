<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/TweenBase -->

TweenBase | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TweenBase.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [TweenBase](/docs/en-us/reference/engine/classes/TweenBase)

English

Feedback

Engine Class

TweenBase

Not Creatable

Not Browsable

---

## Summary

Properties

|

[PlaybackState](#PlaybackState) :[Enum.PlaybackState](/docs/en-us/reference/engine/enums/PlaybackState)

 |
| --- | --- |

Methods

|

[Cancel](#Cancel) () : ()

 |
|

[Pause](#Pause) () : ()

 |
|

[Play](#Play) () : ()

 |

Events

|

[Completed](#Completed) (playbackState :  [Enum.PlaybackState](/docs/en-us/reference/engine/enums/PlaybackState) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[Tween](/docs/en-us/reference/engine/classes/Tween)

---

API Reference

Properties

PlaybackState

Read Only

Not Replicated

Read Parallel

TweenBase.PlaybackState :[Enum.PlaybackState](/docs/en-us/reference/engine/enums/PlaybackState)

Code Samples

Tween PlaybackState

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local goal = {}

goal.Orientation = Vector3.new(0, 90, 0)

local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut, 2, true, 0.5)

local tween = TweenService:Create(part, tweenInfo, goal)

local function onPlaybackChanged()

	print("Tween status has changed to:", tween.PlaybackState)

end

local playbackChanged = tween:GetPropertyChangedSignal("PlaybackState")

playbackChanged:Connect(onPlaybackChanged)

tween:Play()

```

Provide feedback

---

Methods

Cancel

TweenBase:Cancel () : ()

Returns

()

Code Samples

Tween Cancel

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(0, 50, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

task.wait(2.5)

tween:Cancel()

local playTick = tick()

tween:Play()

tween.Completed:Wait()

local timeTaken = tick() - playTick

print("Tween took " .. tostring(timeTaken) .. " secs to complete")

-- The tween will take 5 seconds to complete as the tween variables have been reset by tween:Cancel()

```

Provide feedback

---

Pause

TweenBase:Pause () : ()

Returns

()

Code Samples

Pausing a Tween

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.BrickColor = BrickColor.new("Bright green")

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(50, 10, 0)

local tweenInfo = TweenInfo.new(10, Enum.EasingStyle.Linear)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

task.wait(3)

part.BrickColor = BrickColor.new("Bright red")

tween:Pause()

task.wait(2)

part.BrickColor = BrickColor.new("Bright green")

tween:Play()

```

Provide feedback

---

Play

TweenBase:Play () : ()

Returns

()

Code Samples

Tween Creation

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Color = Color3.new(1, 0, 0)

part.Anchored = true

part.Parent = game.Workspace

local goal = {}

goal.Position = Vector3.new(10, 10, 0)

goal.Color = Color3.new(0, 1, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

```

Tween Conflict

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = game.Workspace

local tweenInfo = TweenInfo.new(5)

-- create two conflicting tweens (both trying to animate part.Position)

local tween1 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 10, 20) })

local tween2 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

-- listen for their completion status

tween1.Completed:Connect(function(playbackState)

	print("tween1: " .. tostring(playbackState))

end)

tween2.Completed:Connect(function(playbackState)

	print("tween2: " .. tostring(playbackState))

end)

-- try to play them both

tween1:Play()

tween2:Play()

```

Provide feedback

---

Events

Completed

TweenBase.Completed (playbackState :[Enum.PlaybackState](/docs/en-us/reference/engine/enums/PlaybackState) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playbackState :[Enum.PlaybackState](/docs/en-us/reference/engine/enums/PlaybackState)

 |

Code Samples

Tween Completed

```

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local SLOW_DURATION = 10

local function slowCharacter(humanoid)

	local goal = {}

	goal.WalkSpeed = 0

	local tweenInfo = TweenInfo.new(SLOW_DURATION)

	local tweenSpeed = TweenService:Create(humanoid, tweenInfo, goal)

	tweenSpeed:Play()

	return tweenSpeed

end

local function onCharacterAdded(character)

	local humanoid = character:WaitForChild("Humanoid")

	local initialSpeed = humanoid.WalkSpeed

	local tweenSpeed = slowCharacter(humanoid)

	tweenSpeed.Completed:Wait()

	humanoid.WalkSpeed = initialSpeed

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Tween Conflict

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = game.Workspace

local tweenInfo = TweenInfo.new(5)

-- create two conflicting tweens (both trying to animate part.Position)

local tween1 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 10, 20) })

local tween2 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

-- listen for their completion status

tween1.Completed:Connect(function(playbackState)

	print("tween1: " .. tostring(playbackState))

end)

tween2.Completed:Connect(function(playbackState)

	print("tween2: " .. tostring(playbackState))

end)

-- try to play them both

tween1:Play()

tween2:Play()

```

Verifying a Tween has Completed

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 50, 0)

part.Anchored = true

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(0, 0, 0)

local tweenInfo = TweenInfo.new(3)

local tween = TweenService:Create(part, tweenInfo, goal)

local function onTweenCompleted(playbackState)

	if playbackState == Enum.PlaybackState.Completed then

		local explosion = Instance.new("Explosion")

		explosion.Position = part.Position

		explosion.Parent = workspace

		part:Destroy()

		task.delay(2, function()

			if explosion then

				explosion:Destroy()

			end

		end)

	end

end

tween.Completed:Connect(onTweenCompleted)

tween:Play()

```

Provide feedback

---

Jump to

▼

TweenBase

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[PlaybackState](#PlaybackState)

[Methods](#methods)

[Cancel()](#Cancel)

[Pause()](#Pause)

[Play()](#Play)

[Events](#events)

[Completed](#Completed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
