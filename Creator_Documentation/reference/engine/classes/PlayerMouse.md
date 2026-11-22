<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/PlayerMouse -->

PlayerMouse | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PlayerMouse.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Mouse](/docs/en-us/reference/engine/classes/Mouse)
8. /
9. [PlayerMouse](/docs/en-us/reference/engine/classes/PlayerMouse)

English

Feedback

Engine Class

PlayerMouse

Not Creatable

---

## Summary

Inherited Members

25  inherited from [Mouse](/docs/en-us/reference/engine/classes/Mouse)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

PlayerMouse

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local mouse = player:GetMouse()

local function onMouseMove()

	print("mouse screen position: ", mouse.X, mouse.Y)

end

mouse.Move:Connect(onMouseMove)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
