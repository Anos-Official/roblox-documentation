<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ModuleScript -->

ModuleScript | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ModuleScript.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [LuaSourceContainer](/docs/en-us/reference/engine/classes/LuaSourceContainer)
8. /
9. [ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript)

English

Feedback

Engine Class

ModuleScript

---

## Summary

Properties

|

[LinkedSource](#LinkedSource) : ContentId

Deprecated

 |
| --- | --- |
|

[Source](#Source) :[string](/docs/en-us/luau/strings)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Simple ModuleScript Example

```

-- Tables store multiple values in one variable

local MyFunctions = {}

-- Add a few functions to the table

function MyFunctions.foo()

	print("Foo!")

end

function MyFunctions.bar()

	print("Bar!")

end

-- ModuleScripts must return exactly one value

return MyFunctions

```

Simple ModuleScript Usage

```

-- The require function is provided a ModuleScript, then runs

-- the code, waiting until it returns a singular value.

local MyFunctions = require(script.Parent.MyFunctions)

-- These are some dummy functions defined in another code sample

MyFunctions.foo()

MyFunctions.bar()

```

---

API Reference

Properties

LinkedSource

Deprecated

Show details

---

Source

Read Parallel

Capabilities: PluginOrOpenCloud

ModuleScript.Source :[string](/docs/en-us/luau/strings)

Provide feedback

---

Jump to

▼

ModuleScript

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[LinkedSource](#LinkedSource)

[Source](#Source)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
