<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/datatypes/Color3 -->

Color3 | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/Color3.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/en-us/reference/engine/datatypes)
2. /
3. [Color3](/docs/en-us/reference/engine/datatypes/Color3)

English

Feedback

Engine Data Type

Color3

---

## Summary

Constructors

|

[new](#new) (red :  [number](/docs/en-us/luau/numbers) , green :  [number](/docs/en-us/luau/numbers) , blue :  [number](/docs/en-us/luau/numbers) )

 |
| --- | --- |
|

[fromRGB](#fromRGB) (red :  [number](/docs/en-us/luau/numbers) , green :  [number](/docs/en-us/luau/numbers) , blue :  [number](/docs/en-us/luau/numbers) )

 |
|

[fromHSV](#fromHSV) (hue :  [number](/docs/en-us/luau/numbers) , saturation :  [number](/docs/en-us/luau/numbers) , value :  [number](/docs/en-us/luau/numbers) )

 |
|

[fromHex](#fromHex) (hex :  [string](/docs/en-us/luau/strings) )

 |

Properties

|

[R](#R) :[number](/docs/en-us/luau/numbers)

 |
|

[G](#G) :[number](/docs/en-us/luau/numbers)

 |
|

[B](#B) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[Lerp](#Lerp) (color :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) , alpha :  [number](/docs/en-us/luau/numbers) ) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[ToHSV](#ToHSV) () :[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers)

 |
|

[ToHex](#ToHex) () :[string](/docs/en-us/luau/strings)

 |
|

[GetLuminance](#GetLuminance) () :[number](/docs/en-us/luau/numbers)

 |
|

[GetContrastRatio](#GetContrastRatio) (other :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) ) :[number](/docs/en-us/luau/numbers)

 |
|

[GetContrastingColor](#GetContrastingColor) (... :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) ) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |

Functions

|

[toHSV](#toHSV) (color :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) ) :[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers)

Deprecated

 |

---

API Reference

Constructors

new

Color3.new (

red :[number](/docs/en-us/luau/numbers) , green :[number](/docs/en-us/luau/numbers) , blue :[number](/docs/en-us/luau/numbers) )

Parameters

|

red :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

green :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

blue :[number](/docs/en-us/luau/numbers)

Default Value: 0 |

Provide feedback

---

fromRGB

Color3.fromRGB (

red :[number](/docs/en-us/luau/numbers) , green :[number](/docs/en-us/luau/numbers) , blue :[number](/docs/en-us/luau/numbers) )

Parameters

|

red :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

green :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

blue :[number](/docs/en-us/luau/numbers)

Default Value: 0 |

Provide feedback

---

fromHSV

Color3.fromHSV (

hue :[number](/docs/en-us/luau/numbers) , saturation :[number](/docs/en-us/luau/numbers) , value :[number](/docs/en-us/luau/numbers) )

Parameters

|

hue :[number](/docs/en-us/luau/numbers)

 |
|

saturation :[number](/docs/en-us/luau/numbers)

 |
|

value :[number](/docs/en-us/luau/numbers)

 |

Provide feedback

---

fromHex

Color3.fromHex (hex :[string](/docs/en-us/luau/strings) )

Parameters

|

hex :[string](/docs/en-us/luau/strings)

 |

Provide feedback

---

Properties

R

Color3.R :[number](/docs/en-us/luau/numbers)

Provide feedback

---

G

Color3.G :[number](/docs/en-us/luau/numbers)

Provide feedback

---

B

Color3.B :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

Lerp

Color3:Lerp (

color :[Color3](/docs/en-us/reference/engine/datatypes/Color3) , alpha :[number](/docs/en-us/luau/numbers)

) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Parameters

|

color :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

alpha :[number](/docs/en-us/luau/numbers)

 |

Returns

[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

ToHSV

Color3:ToHSV () :[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers) , [number](/docs/en-us/luau/numbers) , [number](/docs/en-us/luau/numbers)

Provide feedback

---

ToHex

Color3:ToHex () :[string](/docs/en-us/luau/strings)

Returns

[string](/docs/en-us/luau/strings)

Provide feedback

---

GetLuminance

Color3:GetLuminance () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetContrastRatio

Color3:GetContrastRatio (other :[Color3](/docs/en-us/reference/engine/datatypes/Color3) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

other :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetContrastingColor

Color3:GetContrastingColor (... :[Color3](/docs/en-us/reference/engine/datatypes/Color3) ) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Parameters

|

... :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |

Returns

[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

Functions

toHSV

Deprecated

Show details

---

Jump to

▼

Color3

[Summary](#summary)

[Constructors](#summary-constructors)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Functions](#summary-functions)

[Constructors](#constructors)

[new()](#new)

[fromRGB()](#fromRGB)

[fromHSV()](#fromHSV)

[fromHex()](#fromHex)

[Properties](#properties)

[R](#R)

[G](#G)

[B](#B)

[Methods](#methods)

[Lerp()](#Lerp)

[ToHSV()](#ToHSV)

[ToHex()](#ToHex)

[GetLuminance()](#GetLuminance)

[GetContrastRatio()](#GetContrastRatio)

[GetContrastingColor()](#GetContrastingColor)

[Functions](#functions)

[toHSV()](#toHSV)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
