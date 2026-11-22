<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Path -->

Path | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Path.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Path](/docs/reference/engine/classes/Path)

English

Feedback

Engine Class

Path

Not Creatable

Not Replicated

---

## Summary

Properties

|

[Status](#Status) :[Enum.PathStatus](/docs/reference/engine/enums/PathStatus)

 |
| --- | --- |

Methods

|

[CheckOcclusionAsync](#CheckOcclusionAsync) (start :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

Deprecated

 |
|

[ComputeAsync](#ComputeAsync) (start :  [Vector3](/docs/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/reference/engine/datatypes/Vector3) ) : ()

 |
|

[GetPointCoordinates](#GetPointCoordinates) () :[{any}](/docs/luau/tables#arrays)

Deprecated

 |
|

[GetWaypoints](#GetWaypoints) () :[{any}](/docs/luau/tables#arrays)

 |

Events

|

[Blocked](#Blocked) (blockedWaypointIdx :  [number](/docs/luau/numbers) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[Unblocked](#Unblocked) (unblockedWaypointIdx :  [number](/docs/luau/numbers) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Status

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

Path.Status :[Enum.PathStatus](/docs/reference/engine/enums/PathStatus)

Provide feedback

---

Methods

CheckOcclusionAsync

Deprecated

Show details

---

ComputeAsync

Yields

Capabilities: Basic

Path:ComputeAsync (

start :[Vector3](/docs/reference/engine/datatypes/Vector3) , finish :[Vector3](/docs/reference/engine/datatypes/Vector3)

) : ()

Parameters

|

start :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

finish :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |

Returns

()

Provide feedback

---

GetPointCoordinates

Deprecated

Show details

---

GetWaypoints

Capabilities: Basic

Path:GetWaypoints () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Code Samples

Get Path Waypoints

```

local PathfindingService = game:GetService("PathfindingService")

local path = PathfindingService:CreatePath()

local PATH_START = Vector3.new(0, 1, 0)

local PATH_END = Vector3.new(100, 1, 25)

path:ComputeAsync(PATH_START, PATH_END)

if path.Status == Enum.PathStatus.Success then

	local waypoints = path:GetWaypoints()

	for _, waypoint in pairs(waypoints) do

		print(waypoint.Position)

	end

end

```

Provide feedback

---

Events

Blocked

Capabilities: Basic

Path.Blocked (blockedWaypointIdx :[number](/docs/luau/numbers) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

blockedWaypointIdx :[number](/docs/luau/numbers)

 |

Provide feedback

---

Unblocked

Capabilities: Basic

Path.Unblocked (unblockedWaypointIdx :[number](/docs/luau/numbers) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

unblockedWaypointIdx :[number](/docs/luau/numbers)

 |

Provide feedback

---

Jump to

▼

Path

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Status](#Status)

[Methods](#methods)

[CheckOcclusionAsync()](#CheckOcclusionAsync)

[ComputeAsync()](#ComputeAsync)

[GetPointCoordinates()](#GetPointCoordinates)

[GetWaypoints()](#GetWaypoints)

[Events](#events)

[Blocked](#Blocked)

[Unblocked](#Unblocked)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
