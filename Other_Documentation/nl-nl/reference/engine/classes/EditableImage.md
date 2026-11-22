<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/EditableImage -->

EditableImage | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)

Nederlands

Feedback

Engine-klasse

EditableImage

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/EditableImage)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Size](#Size) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
| --- | --- |

Methoden

|

[Destroy](#Destroy) () : ()

 |
|

[DrawCircle](#DrawCircle) (center :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , radius :  [number](/docs/nl-nl/luau/numbers) , color :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , transparency :  [number](/docs/nl-nl/luau/numbers) , combineType :  [Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , antiAliasing :  [Enum.AntiAliasing](/docs/nl-nl/reference/engine/enums/AntiAliasing) , alphaBlendType :  [Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[DrawImage](#DrawImage) (position :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , image :  [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , combineType :  [Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , alphaBlendType :  [Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[DrawImageProjected](#DrawImageProjected) (projectionSource :  [Object](/docs/nl-nl/reference/engine/classes/Object) , projection :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , brushConfig :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[SampleImageProjected](#SampleImageProjected) (projectionSource :  [Object](/docs/nl-nl/reference/engine/classes/Object) , sourceTexture :  [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , projectionConfig :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , brushConfig :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[DrawImageTransformed](#DrawImageTransformed) (position :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , scale :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , rotation :  [number](/docs/nl-nl/luau/numbers) , image :  [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ? ) : ()

 |
|

[DrawLine](#DrawLine) (p1 :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , p2 :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , color :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , transparency :  [number](/docs/nl-nl/luau/numbers) , combineType :  [Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , antiAliasing :  [Enum.AntiAliasing](/docs/nl-nl/reference/engine/enums/AntiAliasing) , alphaBlendType :  [Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[DrawRectangle](#DrawRectangle) (position :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , size :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , color :  [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , transparency :  [number](/docs/nl-nl/luau/numbers) , combineType :  [Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , alphaBlendType :  [Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[ReadPixelsBuffer](#ReadPixelsBuffer) (position :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , size :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

[WritePixelsBuffer](#WritePixelsBuffer) (position :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , size :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , buffer :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) : ()

 |

Overgenomen leden

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Size

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: DynamicGeneration

EditableImage.Size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Methoden

Destroy

Mogelijkheden: DynamicGeneration

EditableImage:Destroy () : ()

Teruggaves

()

Feedback geven

---

DrawCircle

Mogelijkheden: DynamicGeneration

EditableImage:DrawCircle (

center :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , radius :[number](/docs/nl-nl/luau/numbers) , color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , transparency :[number](/docs/nl-nl/luau/numbers) , combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , antiAliasing :[Enum.AntiAliasing](/docs/nl-nl/reference/engine/enums/AntiAliasing) , alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

center :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

radius :[number](/docs/nl-nl/luau/numbers)

 |
|

color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

transparency :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType)

Standaardwaarde: Overwrite |
|

antiAliasing :[Enum.AntiAliasing](/docs/nl-nl/reference/engine/enums/AntiAliasing)

Standaardwaarde: Enabled |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

Standaardwaarde: Default |

Teruggaves

()

Feedback geven

---

DrawImage

Mogelijkheden: DynamicGeneration

EditableImage:DrawImage (

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , image :[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

image :[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)

 |
|

combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType)

Standaardwaarde: AlphaBlend |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

Standaardwaarde: Default |

Teruggaves

()

Feedback geven

---

DrawImageProjected

Mogelijkheden: DynamicGeneration

EditableImage:DrawImageProjected (

projectionSource :[Object](/docs/nl-nl/reference/engine/classes/Object) , projection :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) , brushConfig :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

projectionSource :[Object](/docs/nl-nl/reference/engine/classes/Object)

 |
|

projection :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

brushConfig :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Feedback geven

---

SampleImageProjected

Mogelijkheden: DynamicGeneration

EditableImage:SampleImageProjected (

projectionSource :[Object](/docs/nl-nl/reference/engine/classes/Object) , sourceTexture :[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , projectionConfig :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) , brushConfig :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

projectionSource :[Object](/docs/nl-nl/reference/engine/classes/Object)

 |
|

sourceTexture :[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)

 |
|

projectionConfig :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

brushConfig :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Feedback geven

---

DrawImageTransformed

Mogelijkheden: DynamicGeneration

EditableImage:DrawImageTransformed (

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , scale :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , rotation :[number](/docs/nl-nl/luau/numbers) , image :[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

) : ()

Parameters

|

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

scale :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

rotation :[number](/docs/nl-nl/luau/numbers)

 |
|

image :[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

 |

Teruggaves

()

Codevoorbeelden

EditableImage:DrawImageTransformed()

```

local AssetService = game:GetService("AssetService")

-- Voorbeeld van het tekenen van een geroteerde en geschaalde afbeelding op een andere EditableImage

local srcImage = AssetService:CreateEditableImage({ Size = Vector2.new(256, 256) })

local dstImage = AssetService:CreateEditableImage({ Size = Vector2.new(512, 512) })

-- Tekenen met een rotatie van 45 graden, schaling met 2x, en plaatsen op (100, 100)

dstImage:DrawImageTransformed(

	Vector2.new(100, 100), -- Positie

	Vector2.new(2, 2), -- Schaal

	45, -- Rotatie (graden)

	srcImage, -- Bronafbeelding

	{

		CombineType = Enum.ImageCombineType.AlphaBlend, -- Optioneel, standaard is AlphaBlend

		SamplingMode = Enum.ResamplerMode.Default, -- Optioneel, standaard is Default

		PivotPoint = srcImage.Size / 2, -- Optioneel, standaard is het midden van de bronafbeelding

	}

)

```

EditableImage:DrawImageTransformed() - Bijsnijden

```

local AssetService = game:GetService("AssetService")

-- Bronafbeelding

local srcImage = AssetService:CreateEditableImageAsync(Content.fromUri(assetUri))

-- Bijsnijdgebied gedefinieerd door offset en grootte

local cropOffset = Vector2.new(50, 50)

local cropSize = Vector2.new(100, 100)

-- Bestemmingsafbeelding met de grootte van het bijsnijdgebied

local dstImage = AssetService:CreateEditableImage({ Size = cropSize })

-- Positie (linkerbovenhoek)

local position = Vector2.new(0, 0)

-- Schaalfactoren (geen schaling)

local scale = Vector2.new(1, 1)

-- Rotatiehoek (geen rotatie)

local rotation = 0

-- Teken de bronafbeelding op de bestemmingsafbeelding met aangepaste pivot om de afbeelding bij te snijden

dstImage:DrawImageTransformed(position, scale, rotation, srcImage, {

	CombineType = Enum.ImageCombineType.Overwrite,

	PivotPoint = cropOffset, -- Stel het draaipunt in op cropOffset om vanaf daar te beginnen met tekenen

})

```

Feedback geven

---

DrawLine

Mogelijkheden: DynamicGeneration

EditableImage:DrawLine (

p1 :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , p2 :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , transparency :[number](/docs/nl-nl/luau/numbers) , combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , antiAliasing :[Enum.AntiAliasing](/docs/nl-nl/reference/engine/enums/AntiAliasing) , alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

p1 :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

p2 :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

transparency :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType)

Standaardwaarde: Overwrite |
|

antiAliasing :[Enum.AntiAliasing](/docs/nl-nl/reference/engine/enums/AntiAliasing)

Standaardwaarde: Enabled |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

Standaardwaarde: Default |

Teruggaves

()

Feedback geven

---

DrawRectangle

Mogelijkheden: DynamicGeneration

EditableImage:DrawRectangle (

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3) , transparency :[number](/docs/nl-nl/luau/numbers) , combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType) , alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

transparency :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

combineType :[Enum.ImageCombineType](/docs/nl-nl/reference/engine/enums/ImageCombineType)

Standaardwaarde: Overwrite |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/nl-nl/reference/engine/enums/ImageAlphaType)

Standaardwaarde: Default |

Teruggaves

()

Feedback geven

---

ReadPixelsBuffer

Parallel schrijven

Mogelijkheden: DynamicGeneration

EditableImage:ReadPixelsBuffer (

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Codevoorbeelden

EditableImage:ReadPixelsBuffer()

```

local AssetService = game:GetService("AssetService")

local options = { Size = Vector2.new(32, 32) }

local editableImage = AssetService:CreateEditableImage(options)

local pixelsBuffer = editableImage:ReadPixelsBuffer(Vector2.zero, Vector2.new(2, 1))

local color1 =

	Color3.fromRGB(buffer.readu8(pixelsBuffer, 0), buffer.readu8(pixelsBuffer, 1), buffer.readu8(pixelsBuffer, 2))

local transparency1 = (255 - buffer.readu8(pixelsBuffer, 3)) / 255

local color2 =

	Color3.fromRGB(buffer.readu8(pixelsBuffer, 4), buffer.readu8(pixelsBuffer, 5), buffer.readu8(pixelsBuffer, 6))

local transparency2 = (255 - buffer.readu8(pixelsBuffer, 7)) / 255

local averageColor = color1:Lerp(color2, 0.5)

local averageTransparency = (transparency1 + transparency2) / 2

local part = Instance.new("Part")

part.Color = averageColor

part.Transparency = averageTransparency

part.Parent = workspace

```

Feedback geven

---

WritePixelsBuffer

Mogelijkheden: DynamicGeneration

EditableImage:WritePixelsBuffer (

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , buffer :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

) : ()

Parameters

|

position :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

size :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

buffer :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |

Teruggaves

()

Codevoorbeelden

EditableImage:WritePixelsBuffer()

```

local AssetService = game:GetService("AssetService")

local options = { Size = Vector2.new(32, 32) }

local editableImage = AssetService:CreateEditableImage(options)

local pixelsBuffer = editableImage:ReadPixelsBuffer(Vector2.zero, editableImage.Size)

for i = 1, editableImage.Size.X * editableImage.Size.Y do

	local pixelIndex = (i - 1) * 4

	buffer.writeu8(pixelsBuffer, pixelIndex, 255 - buffer.readu8(pixelsBuffer, pixelIndex))

	buffer.writeu8(pixelsBuffer, pixelIndex + 1, 255 - buffer.readu8(pixelsBuffer, pixelIndex + 1))

	buffer.writeu8(pixelsBuffer, pixelIndex + 2, 255 - buffer.readu8(pixelsBuffer, pixelIndex + 2))

	-- Stel alpha in op 255 om alle pixels volledig ondoorzichtig te maken.

	buffer.writeu8(pixelsBuffer, pixelIndex + 3, 255)

end

editableImage:WritePixelsBuffer(Vector2.zero, editableImage.Size, pixelsBuffer)

```

Feedback geven

---

Ga naar

▼

EditableImage

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Size](#Size)

[Methoden](#methods)

[Destroy()](#Destroy)

[DrawCircle()](#DrawCircle)

[DrawImage()](#DrawImage)

[DrawImageProjected()](#DrawImageProjected)

[SampleImageProjected()](#SampleImageProjected)

[DrawImageTransformed()](#DrawImageTransformed)

[DrawLine()](#DrawLine)

[DrawRectangle()](#DrawRectangle)

[ReadPixelsBuffer()](#ReadPixelsBuffer)

[WritePixelsBuffer()](#WritePixelsBuffer)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
