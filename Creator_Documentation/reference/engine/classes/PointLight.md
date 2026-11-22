<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/PointLight -->

PointLight | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PointLight.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Light](/docs/en-us/reference/engine/classes/Light)
8. /
9. [PointLight](/docs/en-us/reference/engine/classes/PointLight)

English

Feedback

Engine Class

PointLight

---

## Summary

Properties

|

[Range](#Range) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |

Inherited Members

4  inherited from [Light](/docs/en-us/reference/engine/classes/Light)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Creating a New Point Light

```

local part = Instance.new("Part")

part.Anchored = true

part.Position = Vector3.new(0, 0, 0)

part.Parent = workspace

local light = Instance.new("PointLight")

light.Color = Color3.new(1, 1, 1)

light.Brightness = 1

light.Range = 16

light.Parent = part

```

---

API Reference

Properties

Range

Read Parallel

Capabilities: Basic

PointLight.Range :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

PointLight

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Range](#Range)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
