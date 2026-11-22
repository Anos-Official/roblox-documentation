<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Vector3Curve -->

Vector3Curve | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Vector3Curve](/docs/nl-nl/reference/engine/classes/Vector3Curve)

Nederlands

Feedback

Engine-klasse

Vector3Curve

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Vector3Curve)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetValueAtTime](#GetValueAtTime) (time :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
| --- | --- |
|

[X](#X) () :[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

 |
|

[Y](#Y) () :[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

 |
|

[Z](#Z) () :[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Een Vector3Curve maken

```

--- Vector3Curve

local function createVector3Curve()

	local vectorCurve = Instance.new("Vector3Curve")

	local curveX = vectorCurve:X() -- maakt en retourneert een FloatCurve die het X-kanaal animeert

	local curveY = vectorCurve:Y() -- maakt en retourneert een FloatCurve die het Y-kanaal animeert

	-- Het niet instellen van het Z-kanaal laat het Z-kanaal niet geanimeerd.

	-- Een ontbrekende curve of een curve zonder sleutels neemt niet deel aan de animatie

	local key = FloatCurveKey.new(0, 1) -- maakt een sleutel op tijd 0 met waarde 1

	curveX:InsertKey(key)

	curveY:InsertKey(key)

	local key2 = FloatCurveKey.new(1, 2) -- maakt een sleutel op tijd 1 met waarde 2

	curveX:InsertKey(key2)

	curveY:InsertKey(key2)

	return vectorCurve

end

local function testVector3Curve()

	local curve = createVector3Curve()

	-- het monsteren van de curve op een gegeven tijd (retourneert een vector3)

	print(curve:GetValueAtTime(0)) -- retourneert 1, 1, void

	print(curve:GetValueAtTime(0.5)) -- retourneert 1.5, 1.5, void (resultaat van kubieke interpolatie met automatische tangenten)

	curve:X():RemoveKeyAtIndex(1)

	curve:X():RemoveKeyAtIndex(1)

	print(curve:X().Length) -- aantal sleutels = 0

	print(curve:GetValueAtTime(0.5)) -- retourneert void, 1.5, void

end

testVector3Curve()

```

---

API-referentie

Methoden

GetValueAtTime

Mogelijkheden: Basic

Vector3Curve:GetValueAtTime (time :[number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

time :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

X

Mogelijkheden: Basic

Vector3Curve:X () :[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

Teruggaves

[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

Feedback geven

---

Y

Mogelijkheden: Basic

Vector3Curve:Y () :[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

Teruggaves

[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

Feedback geven

---

Z

Mogelijkheden: Basic

Vector3Curve:Z () :[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

Teruggaves

[FloatCurve](/docs/nl-nl/reference/engine/classes/FloatCurve)

Feedback geven

---

Ga naar

▼

Vector3Curve

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetValueAtTime()](#GetValueAtTime)

[X()](#X)

[Y()](#Y)

[Z()](#Z)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
