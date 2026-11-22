<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Hat -->

Hat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Hat.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Accoutrement](/docs/reference/engine/classes/Accoutrement)
8. /
9. [Hat](/docs/reference/engine/classes/Hat)

English

Feedback

Engine Class

Hat

Deprecated

---

## Summary

Inherited Members

5  inherited from [Accoutrement](/docs/reference/engine/classes/Accoutrement)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Manually Position Hats

```

local hat = script.Parent

local character = hat.Parent

hat.Handle.CFrame = character.Head.CFrame * CFrame.new(0, character.Head.Size.Y / 2, 0) * hat.AttachmentPoint:inverse()

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
