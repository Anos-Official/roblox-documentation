<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/WireframeHandleAdornment -->

WireframeHandleAdornment | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/nl-nl/reference/engine/classes/GuiBase)
8. /
9. [GuiBase3d](/docs/nl-nl/reference/engine/classes/GuiBase3d)
10. /
11. [PVAdornment](/docs/nl-nl/reference/engine/classes/PVAdornment)
12. /
13. [HandleAdornment](/docs/nl-nl/reference/engine/classes/HandleAdornment)
14. /
15. [WireframeHandleAdornment](/docs/nl-nl/reference/engine/classes/WireframeHandleAdornment)

Nederlands

Feedback

Engine-klasse

WireframeHandleAdornment

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/WireframeHandleAdornment)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Scale](#Scale) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
| --- | --- |
|

[Thickness](#Thickness) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[AddLine](#AddLine) (from :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , to :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) : ()

 |
|

[AddLines](#AddLines) (points :  [{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

 |
|

[AddPath](#AddPath) (points :  [{any}](/docs/nl-nl/luau/tables#arrays) , loop :  [boolean](/docs/nl-nl/luau/booleans) ) : ()

 |
|

[AddText](#AddText) (point :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , text :  [string](/docs/nl-nl/luau/strings) , size :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
|

[Clear](#Clear) () : ()

 |

Overgenomen leden

9  overgenomen van [HandleAdornment](/docs/nl-nl/reference/engine/classes/HandleAdornment)

1  overgenomen van [PVAdornment](/docs/nl-nl/reference/engine/classes/PVAdornment)

4  overgenomen van [GuiBase3d](/docs/nl-nl/reference/engine/classes/GuiBase3d)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Basis Pad Draadmodel

```

local wireframe = script.Parent

-- Verklaar vier punten in een vierkante opstelling

local pathArray = {

	Vector3.new(-10, 10, 0),

	Vector3.new(10, 10, 0),

	Vector3.new(10, -10, 0),

	Vector3.new(-10, -10, 0)

}

-- Pas pad toe op versiering en sluit het (verbind begin- en eindpunten)

wireframe:AddPath(pathArray, true)

```

Multicolor Draadframe

```

local wireframe = script.Parent

wireframe.Color3 = Color3.fromRGB(255, 0, 0) -- Zet de volgende lijn op rood

wireframe:AddLine(Vector3.new(-10, 0, 0), Vector3.new(10, 0, 0))

wireframe.Color3 = Color3.fromRGB(0, 255, 0) -- Zet de volgende lijn op groen

wireframe:AddLine(Vector3.new(0, -10, 0), Vector3.new(0, 10, 0))

wireframe.Color3 = Color3.fromRGB(0, 0, 255) -- Zet de volgende lijn op blauw

wireframe:AddLine(Vector3.new(0, 0, -10), Vector3.new(0, 0, 10))

```

---

API-referentie

Eigenschappen

Scale

Parallel lezen

Mogelijkheden: Basic, UI

WireframeHandleAdornment.Scale :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Thickness

Parallel lezen

Mogelijkheden: Basic, UI

WireframeHandleAdornment.Thickness :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

AddLine

Mogelijkheden: Basic, UI

WireframeHandleAdornment:AddLine (

from :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , to :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

) : ()

Parameters

|

from :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

to :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Teruggaves

()

Codevoorbeelden

Multicolor Draadframe

```

local wireframe = script.Parent

wireframe.Color3 = Color3.fromRGB(255, 0, 0) -- Zet de volgende lijn op rood

wireframe:AddLine(Vector3.new(-10, 0, 0), Vector3.new(10, 0, 0))

wireframe.Color3 = Color3.fromRGB(0, 255, 0) -- Zet de volgende lijn op groen

wireframe:AddLine(Vector3.new(0, -10, 0), Vector3.new(0, 10, 0))

wireframe.Color3 = Color3.fromRGB(0, 0, 255) -- Zet de volgende lijn op blauw

wireframe:AddLine(Vector3.new(0, 0, -10), Vector3.new(0, 0, 10))

```

Feedback geven

---

AddLines

Mogelijkheden: Basic, UI

WireframeHandleAdornment:AddLines (points :[{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

Parameters

|

points :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

()

Codevoorbeelden

Draadmodel Lijnen Van Array

```

local wireframe = script.Parent

local linesArray = {

	Vector3.new(-10, 0, 0), -- Beginpunt van de eerste lijn

	Vector3.new(10, 0, 0), -- Eindpunt van de eerste lijn

	Vector3.new(0, -10, 0), -- Beginpunt van de tweede lijn

	Vector3.new(0, 10, 0), -- Eindpunt van de tweede lijn

	Vector3.new(0, 0, -10), -- Beginpunt van de derde lijn

	Vector3.new(0, 0, 10) -- Eindpunt van de derde lijn

}

-- Pas pad toe op versiering

wireframe:AddLines(linesArray)

```

Feedback geven

---

AddPath

Mogelijkheden: Basic, UI

WireframeHandleAdornment:AddPath (

points :[{any}](/docs/nl-nl/luau/tables#arrays) , loop :[boolean](/docs/nl-nl/luau/booleans)

) : ()

Parameters

|

points :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

loop :[boolean](/docs/nl-nl/luau/booleans)

 |

Teruggaves

()

Codevoorbeelden

Basis Pad Draadmodel

```

local wireframe = script.Parent

-- Verklaar vier punten in een vierkante opstelling

local pathArray = {

	Vector3.new(-10, 10, 0),

	Vector3.new(10, 10, 0),

	Vector3.new(10, -10, 0),

	Vector3.new(-10, -10, 0)

}

-- Pas pad toe op versiering en sluit het (verbind begin- en eindpunten)

wireframe:AddPath(pathArray, true)

```

Feedback geven

---

AddText

Mogelijkheden: Basic, UI

WireframeHandleAdornment:AddText (

point :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , text :[string](/docs/nl-nl/luau/strings) , size :[number](/docs/nl-nl/luau/numbers)

) : ()

Parameters

|

point :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

text :[string](/docs/nl-nl/luau/strings)

 |
|

size :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 12 |

Teruggaves

()

Feedback geven

---

Clear

Mogelijkheden: Basic, UI

WireframeHandleAdornment:Clear () : ()

Teruggaves

()

Feedback geven

---

Ga naar

▼

WireframeHandleAdornment

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Scale](#Scale)

[Thickness](#Thickness)

[Methoden](#methods)

[AddLine()](#AddLine)

[AddLines()](#AddLines)

[AddPath()](#AddPath)

[AddText()](#AddText)

[Clear()](#Clear)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
