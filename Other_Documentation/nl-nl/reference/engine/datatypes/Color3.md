<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/Color3 -->

Color3 | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Nederlands

Feedback

Engine-gegevenstype

Color3

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/Color3)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Constructors

|

[new](#new) (red :  [number](/docs/nl-nl/luau/numbers) , green :  [number](/docs/nl-nl/luau/numbers) , blue :  [number](/docs/nl-nl/luau/numbers) )

 |
| --- | --- |
|

[fromRGB](#fromRGB) (red :  [number](/docs/nl-nl/luau/numbers) , green :  [number](/docs/nl-nl/luau/numbers) , blue :  [number](/docs/nl-nl/luau/numbers) )

 |
|

[fromHSV](#fromHSV) (hue :  [number](/docs/nl-nl/luau/numbers) , saturation :  [number](/docs/nl-nl/luau/numbers) , value :  [number](/docs/nl-nl/luau/numbers) )

 |
|

[fromHex](#fromHex) (hex :  [string](/docs/nl-nl/luau/strings) )

 |

Eigenschappen

|

[R](#R) :[number](/docs/nl-nl/luau/numbers)

 |
|

[G](#G) :[number](/docs/nl-nl/luau/numbers)

 |
|

[B](#B) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[Lerp](#Lerp) (color :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , alpha :  [number](/docs/nl-nl/luau/numbers) ) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[ToHSV](#ToHSV) () :[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers)

 |
|

[ToHex](#ToHex) () :[string](/docs/nl-nl/luau/strings)

 |
|

[GetLuminance](#GetLuminance) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetContrastRatio](#GetContrastRatio) (other :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetContrastingColor](#GetContrastingColor) (... :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |

Functies

|

[toHSV](#toHSV) (color :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers)

Verouderd

 |

---

API-referentie

Constructors

new

Color3.new (

red :[number](/docs/nl-nl/luau/numbers) , green :[number](/docs/nl-nl/luau/numbers) , blue :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

red :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

green :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

blue :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Feedback geven

---

fromRGB

Color3.fromRGB (

red :[number](/docs/nl-nl/luau/numbers) , green :[number](/docs/nl-nl/luau/numbers) , blue :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

red :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

green :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

blue :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Feedback geven

---

fromHSV

Color3.fromHSV (

hue :[number](/docs/nl-nl/luau/numbers) , saturation :[number](/docs/nl-nl/luau/numbers) , value :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

hue :[number](/docs/nl-nl/luau/numbers)

 |
|

saturation :[number](/docs/nl-nl/luau/numbers)

 |
|

value :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

fromHex

Color3.fromHex (hex :[string](/docs/nl-nl/luau/strings) )

Parameters

|

hex :[string](/docs/nl-nl/luau/strings)

 |

Feedback geven

---

Eigenschappen

R

Color3.R :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

G

Color3.G :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

B

Color3.B :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

Lerp

Color3:Lerp (

color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , alpha :[number](/docs/nl-nl/luau/numbers)

) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Parameters

|

color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

alpha :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

ToHSV

Color3:ToHSV () :[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers) , [number](/docs/nl-nl/luau/numbers) , [number](/docs/nl-nl/luau/numbers)

Feedback geven

---

ToHex

Color3:ToHex () :[string](/docs/nl-nl/luau/strings)

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

GetLuminance

Color3:GetLuminance () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetContrastRatio

Color3:GetContrastRatio (other :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

other :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetContrastingColor

Color3:GetContrastingColor (... :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) ) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Parameters

|

... :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |

Teruggaves

[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

Functies

toHSV

Verouderd

Details weergeven

---

Ga naar

▼

Color3

[Samenvatting](#summary)

[Constructors](#summary-constructors)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Functies](#summary-functions)

[Constructors](#constructors)

[new()](#new)

[fromRGB()](#fromRGB)

[fromHSV()](#fromHSV)

[fromHex()](#fromHex)

[Eigenschappen](#properties)

[R](#R)

[G](#G)

[B](#B)

[Methoden](#methods)

[Lerp()](#Lerp)

[ToHSV()](#ToHSV)

[ToHex()](#ToHex)

[GetLuminance()](#GetLuminance)

[GetContrastRatio()](#GetContrastRatio)

[GetContrastingColor()](#GetContrastingColor)

[Functies](#functions)

[toHSV()](#toHSV)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
