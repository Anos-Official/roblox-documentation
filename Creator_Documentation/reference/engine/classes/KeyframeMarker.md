<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/KeyframeMarker -->

KeyframeMarker | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/KeyframeMarker.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [KeyframeMarker](/docs/en-us/reference/engine/classes/KeyframeMarker)

English

Feedback

Engine Class

KeyframeMarker

---

## Summary

Properties

|

[Value](#Value) :[string](/docs/en-us/luau/strings)

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Get Keyframe Markers Attached to a Keyframe

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker1 = Instance.new("KeyframeMarker")

marker1.Name = "FootStep"

marker1.Value = 100

local marker2 = Instance.new("KeyframeMarker")

marker2.Name = "Wave"

marker2.Value = 100

keyframe:AddMarker(marker1) --marker.Parent = keyframe

keyframe:AddMarker(marker2) --marker.Parent = keyframe

local markers = keyframe:GetMarkers()

for _, marker in pairs(markers) do

	print(marker.Name)

end

```

Listening to Keyframe Markers

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.Character:Wait()

local humanoid = character:WaitForChild("Humanoid")

-- Create new "Animation" instance

local kickAnimation = Instance.new("Animation")

-- Set its "AnimationId" to the corresponding animation asset ID

kickAnimation.AnimationId = "rbxassetid://2515090838"

-- Load animation onto the humanoid

local kickAnimationTrack = humanoid:LoadAnimation(kickAnimation)

-- Play animation track

kickAnimationTrack:Play()

-- If a named event was defined for the animation, connect it to "GetMarkerReachedSignal()"

kickAnimationTrack:GetMarkerReachedSignal("KickEnd"):Connect(function(paramString)

	print(paramString)

end)

```

---

API Reference

Properties

Value

Read Parallel

Capabilities: Animation

KeyframeMarker.Value :[string](/docs/en-us/luau/strings)

Code Samples

Get Keyframe Markers Attached to a Keyframe

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker1 = Instance.new("KeyframeMarker")

marker1.Name = "FootStep"

marker1.Value = 100

local marker2 = Instance.new("KeyframeMarker")

marker2.Name = "Wave"

marker2.Value = 100

keyframe:AddMarker(marker1) --marker.Parent = keyframe

keyframe:AddMarker(marker2) --marker.Parent = keyframe

local markers = keyframe:GetMarkers()

for _, marker in pairs(markers) do

	print(marker.Name)

end

```

Add Marker/Remove Marker

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker = Instance.new("KeyframeMarker")

marker.Name = "FootStep"

marker.Value = 100

keyframe:AddMarker(marker) --marker.Parent = keyframe

task.wait(2)

keyframe:RemoveMarker(marker) --marker.Parent = nil

```

Provide feedback

---

Jump to

▼

KeyframeMarker

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Value](#Value)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
