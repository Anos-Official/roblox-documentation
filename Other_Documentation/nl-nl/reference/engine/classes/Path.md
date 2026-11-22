<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Path -->

Path | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Path](/docs/nl-nl/reference/engine/classes/Path)

Nederlands

Feedback

Engine-klasse

Path

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Path)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Status](#Status) :[Enum.PathStatus](/docs/nl-nl/reference/engine/enums/PathStatus)

 |
| --- | --- |

Methoden

|

[CheckOcclusionAsync](#CheckOcclusionAsync) (start :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[ComputeAsync](#ComputeAsync) (start :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) : ()

 |
|

[GetPointCoordinates](#GetPointCoordinates) () :[{any}](/docs/nl-nl/luau/tables#arrays)

Verouderd

 |
|

[GetWaypoints](#GetWaypoints) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Evenementen

|

[Blocked](#Blocked) (blockedWaypointIdx :  [number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[Unblocked](#Unblocked) (unblockedWaypointIdx :  [number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Status

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Path.Status :[Enum.PathStatus](/docs/nl-nl/reference/engine/enums/PathStatus)

Feedback geven

---

Methoden

CheckOcclusionAsync

Verouderd

Details weergeven

---

ComputeAsync

Opbrengst

Mogelijkheden: Basic

Path:ComputeAsync (

start :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , finish :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

) : ()

Parameters

|

start :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

finish :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Teruggaves

()

Feedback geven

---

GetPointCoordinates

Verouderd

Details weergeven

---

GetWaypoints

Mogelijkheden: Basic

Path:GetWaypoints () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Krijg Pad Wegpunten

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

Feedback geven

---

Evenementen

Blocked

Mogelijkheden: Basic

Path.Blocked (blockedWaypointIdx :[number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

blockedWaypointIdx :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

Unblocked

Mogelijkheden: Basic

Path.Unblocked (unblockedWaypointIdx :[number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

unblockedWaypointIdx :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

Ga naar

▼

Path

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Status](#Status)

[Methoden](#methods)

[CheckOcclusionAsync()](#CheckOcclusionAsync)

[ComputeAsync()](#ComputeAsync)

[GetPointCoordinates()](#GetPointCoordinates)

[GetWaypoints()](#GetWaypoints)

[Evenementen](#events)

[Blocked](#Blocked)

[Unblocked](#Unblocked)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
