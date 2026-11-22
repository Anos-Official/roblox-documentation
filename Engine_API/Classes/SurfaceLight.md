<!-- Source: https://create.roblox.com/docs/reference/engine/classes/SurfaceLight -->

SurfaceLight | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/SurfaceLight.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Light](/docs/reference/engine/classes/Light)
8. /
9. [SurfaceLight](/docs/reference/engine/classes/SurfaceLight)

English

Feedback

Engine Class

SurfaceLight

---

## Summary

Properties

|

[Angle](#Angle) :[number](/docs/luau/numbers)

 |
| --- | --- |
|

[Face](#Face) :[Enum.NormalId](/docs/reference/engine/enums/NormalId)

 |
|

[Range](#Range) :[number](/docs/luau/numbers)

 |

Inherited Members

4  inherited from [Light](/docs/reference/engine/classes/Light)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Creating a New Surface Light

```

local part = Instance.new("Part")

part.Anchored = true

part.Position = Vector3.new(0, 0, 0)

part.Parent = workspace

local light = Instance.new("SurfaceLight")

light.Color = Color3.fromRGB(255, 255, 255)

light.Brightness = 1

light.Range = 16

light.Parent = part

```

---

API Reference

Properties

Angle

Read Parallel

Capabilities: Basic

SurfaceLight.Angle :[number](/docs/luau/numbers)

Provide feedback

---

Face

Read Parallel

Capabilities: Basic

SurfaceLight.Face :[Enum.NormalId](/docs/reference/engine/enums/NormalId)

Provide feedback

---

Range

Read Parallel

Capabilities: Basic

SurfaceLight.Range :[number](/docs/luau/numbers)

Provide feedback

---

Jump to

▼

SurfaceLight

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Angle](#Angle)

[Face](#Face)

[Range](#Range)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
