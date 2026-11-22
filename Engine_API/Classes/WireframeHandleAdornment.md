<!-- Source: https://create.roblox.com/docs/reference/engine/classes/WireframeHandleAdornment -->

WireframeHandleAdornment | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/WireframeHandleAdornment.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/reference/engine/classes/GuiBase)
8. /
9. [GuiBase3d](/docs/reference/engine/classes/GuiBase3d)
10. /
11. [PVAdornment](/docs/reference/engine/classes/PVAdornment)
12. /
13. [HandleAdornment](/docs/reference/engine/classes/HandleAdornment)
14. /
15. [WireframeHandleAdornment](/docs/reference/engine/classes/WireframeHandleAdornment)

English

Feedback

Engine Class

WireframeHandleAdornment

---

## Summary

Properties

|

[Scale](#Scale) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
| --- | --- |
|

[Thickness](#Thickness) :[number](/docs/luau/numbers)

 |

Methods

|

[AddLine](#AddLine) (from :  [Vector3](/docs/reference/engine/datatypes/Vector3) , to :  [Vector3](/docs/reference/engine/datatypes/Vector3) ) : ()

 |
|

[AddLines](#AddLines) (points :  [{any}](/docs/luau/tables#arrays) ) : ()

 |
|

[AddPath](#AddPath) (points :  [{any}](/docs/luau/tables#arrays) , loop :  [boolean](/docs/luau/booleans) ) : ()

 |
|

[AddText](#AddText) (point :  [Vector3](/docs/reference/engine/datatypes/Vector3) , text :  [string](/docs/luau/strings) , size :  [number](/docs/luau/numbers) ) : ()

 |
|

[Clear](#Clear) () : ()

 |

Inherited Members

9  inherited from [HandleAdornment](/docs/reference/engine/classes/HandleAdornment)

1  inherited from [PVAdornment](/docs/reference/engine/classes/PVAdornment)

4  inherited from [GuiBase3d](/docs/reference/engine/classes/GuiBase3d)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Basic Path Wireframe

```

local wireframe = script.Parent

-- Declare four points in a square arrangement

local pathArray = {

	Vector3.new(-10, 10, 0),

	Vector3.new(10, 10, 0),

	Vector3.new(10, -10, 0),

	Vector3.new(-10, -10, 0)

}

-- Apply path to adornment and close it (connect starting and ending points)

wireframe:AddPath(pathArray, true)

```

Multicolor Wireframe

```

local wireframe = script.Parent

wireframe.Color3 = Color3.fromRGB(255, 0, 0) -- Sets next line to red

wireframe:AddLine(Vector3.new(-10, 0, 0), Vector3.new(10, 0, 0))

wireframe.Color3 = Color3.fromRGB(0, 255, 0) -- Sets next line to green

wireframe:AddLine(Vector3.new(0, -10, 0), Vector3.new(0, 10, 0))

wireframe.Color3 = Color3.fromRGB(0, 0, 255) -- Sets next line to blue

wireframe:AddLine(Vector3.new(0, 0, -10), Vector3.new(0, 0, 10))

```

---

API Reference

Properties

Scale

Read Parallel

Capabilities: Basic, UI

WireframeHandleAdornment.Scale :[Vector3](/docs/reference/engine/datatypes/Vector3)

Provide feedback

---

Thickness

Read Parallel

Capabilities: Basic, UI

WireframeHandleAdornment.Thickness :[number](/docs/luau/numbers)

Provide feedback

---

Methods

AddLine

Capabilities: Basic, UI

WireframeHandleAdornment:AddLine (

from :[Vector3](/docs/reference/engine/datatypes/Vector3) , to :[Vector3](/docs/reference/engine/datatypes/Vector3)

) : ()

Parameters

|

from :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

to :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |

Returns

()

Code Samples

Multicolor Wireframe

```

local wireframe = script.Parent

wireframe.Color3 = Color3.fromRGB(255, 0, 0) -- Sets next line to red

wireframe:AddLine(Vector3.new(-10, 0, 0), Vector3.new(10, 0, 0))

wireframe.Color3 = Color3.fromRGB(0, 255, 0) -- Sets next line to green

wireframe:AddLine(Vector3.new(0, -10, 0), Vector3.new(0, 10, 0))

wireframe.Color3 = Color3.fromRGB(0, 0, 255) -- Sets next line to blue

wireframe:AddLine(Vector3.new(0, 0, -10), Vector3.new(0, 0, 10))

```

Provide feedback

---

AddLines

Capabilities: Basic, UI

WireframeHandleAdornment:AddLines (points :[{any}](/docs/luau/tables#arrays) ) : ()

Parameters

|

points :[{any}](/docs/luau/tables#arrays)

 |

Returns

()

Code Samples

Wireframe Lines From Array

```

local wireframe = script.Parent

local linesArray = {

	Vector3.new(-10, 0, 0), -- Starting point of first line

	Vector3.new(10, 0, 0), -- Ending point of first line

	Vector3.new(0, -10, 0), -- Starting point of second line

	Vector3.new(0, 10, 0), -- Ending point of second line

	Vector3.new(0, 0, -10), -- Starting point of third line

	Vector3.new(0, 0, 10) -- Ending point of third line

}

-- Apply path to adornment

wireframe:AddLines(linesArray)

```

Provide feedback

---

AddPath

Capabilities: Basic, UI

WireframeHandleAdornment:AddPath (

points :[{any}](/docs/luau/tables#arrays) , loop :[boolean](/docs/luau/booleans)

) : ()

Parameters

|

points :[{any}](/docs/luau/tables#arrays)

 |
|

loop :[boolean](/docs/luau/booleans)

 |

Returns

()

Code Samples

Basic Path Wireframe

```

local wireframe = script.Parent

-- Declare four points in a square arrangement

local pathArray = {

	Vector3.new(-10, 10, 0),

	Vector3.new(10, 10, 0),

	Vector3.new(10, -10, 0),

	Vector3.new(-10, -10, 0)

}

-- Apply path to adornment and close it (connect starting and ending points)

wireframe:AddPath(pathArray, true)

```

Provide feedback

---

AddText

Capabilities: Basic, UI

WireframeHandleAdornment:AddText (

point :[Vector3](/docs/reference/engine/datatypes/Vector3) , text :[string](/docs/luau/strings) , size :[number](/docs/luau/numbers)

) : ()

Parameters

|

point :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

text :[string](/docs/luau/strings)

 |
|

size :[number](/docs/luau/numbers)

Default Value: 12 |

Returns

()

Provide feedback

---

Clear

Capabilities: Basic, UI

WireframeHandleAdornment:Clear () : ()

Returns

()

Provide feedback

---

Jump to

▼

WireframeHandleAdornment

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Scale](#Scale)

[Thickness](#Thickness)

[Methods](#methods)

[AddLine()](#AddLine)

[AddLines()](#AddLines)

[AddPath()](#AddPath)

[AddText()](#AddText)

[Clear()](#Clear)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
