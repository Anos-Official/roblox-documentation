<!-- Source: https://create.roblox.com/docs/luau/tuples -->

Tuples | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/tuples.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. [Luau reference](/docs/luau)
8. /
9. Types

# Tuples

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/tuples.md)

A tuple  is a list of values. Many [methods](/docs/luau/functions#methods)  and [callbacks](/docs/luau/functions#callbacks)  in the [Roblox Engine API](/docs/reference/engine)  accept and return multiple values, but the API Reference says "Tuple" instead of those values.

## [Parameters](#parameters)[](#parameters)

If a [method](/docs/luau/functions#methods)  or [callback](/docs/luau/functions#callbacks)  accepts a tuple as a parameter, then it accepts multiple values. For example, the API Reference shows that the [BindableFunction:Invoke()](/docs/reference/engine/classes/BindableFunction#Invoke)  method accepts a "Tuple" as a parameter, so it accepts multiple arguments.

```

BindableFunction:Invoke(1, true, "string", Vector3.new(0, 0, 0))

```

## [Returns](#returns)[](#returns)

If a [method](/docs/luau/functions#methods)  or [callback](/docs/luau/functions#callbacks)  returns a tuple, then it returns multiple values. For example, the API Reference shows that the [Players:GetUserThumbnailAsync()](/docs/reference/engine/classes/Players#GetUserThumbnailAsync)  method returns a "Tuple", so it returns multiple values. The first return value is a Content URL, and the second is a [boolean](/docs/luau/booleans) .

```

local Players = game:GetService("Players")

local userId = 156 -- builderman

local thumbType = Enum.ThumbnailType.HeadShot

local thumbSize = Enum.ThumbnailSize.Size420x420

local content, isReady = Players:GetUserThumbnailAsync(userId, thumbType, thumbSize)

print(content, isReady) -- rbxthumb://type=AvatarHeadShot&id=156&w=420&h=420 true

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
