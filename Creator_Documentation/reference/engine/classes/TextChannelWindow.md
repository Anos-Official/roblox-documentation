<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/TextChannelWindow -->

TextChannelWindow | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TextChannelWindow.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/en-us/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/en-us/reference/engine/classes/GuiBase2d)
10. /
11. [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)
12. /
13. [TextChannelWindow](/docs/en-us/reference/engine/classes/TextChannelWindow)

English

Feedback

Engine Class

TextChannelWindow

---

## Summary

Properties

|

[Target](#Target) :[TextChannel](/docs/en-us/reference/engine/classes/TextChannel)

 |
| --- | --- |
|

[FontFace](#FontFace) :[Font](/docs/en-us/reference/engine/datatypes/Font)

 |
|

[UseDefaultFont](#UseDefaultFont) :[boolean](/docs/en-us/luau/booleans)

 |

Inherited Members

51  inherited from [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)

12  inherited from [GuiBase2d](/docs/en-us/reference/engine/classes/GuiBase2d)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Target

Read Parallel

Capabilities: UI, Chat

TextChannelWindow.Target :[TextChannel](/docs/en-us/reference/engine/classes/TextChannel)

Provide feedback

---

FontFace

Read Parallel

Capabilities: UI, Chat

TextChannelWindow.FontFace :[Font](/docs/en-us/reference/engine/datatypes/Font)

Code Samples

Custom TextChannelWindow Font

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = Players.LocalPlayer:WaitForChild("PlayerGui")

local window = Instance.new("TextChannelWindow")

window.Size = UDim2.fromOffset(400, 300)

window.Target = TextChatService:WaitForChild("TextChannels"):WaitForChild("RBXGeneral")

-- FontFace applies only while UseDefaultFont is false

window.UseDefaultFont = false

window.FontFace = Font.fromName("FredokaOne")

window.Parent = screenGui

```

Provide feedback

---

UseDefaultFont

Read Parallel

Capabilities: UI, Chat

TextChannelWindow.UseDefaultFont :[boolean](/docs/en-us/luau/booleans)

Code Samples

Custom TextChannelWindow Font

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = Players.LocalPlayer:WaitForChild("PlayerGui")

local window = Instance.new("TextChannelWindow")

window.Size = UDim2.fromOffset(400, 300)

window.Target = TextChatService:WaitForChild("TextChannels"):WaitForChild("RBXGeneral")

-- FontFace applies only while UseDefaultFont is false

window.UseDefaultFont = false

window.FontFace = Font.fromName("FredokaOne")

window.Parent = screenGui

```

Provide feedback

---

Jump to

▼

TextChannelWindow

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Target](#Target)

[FontFace](#FontFace)

[UseDefaultFont](#UseDefaultFont)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
