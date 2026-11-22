<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/EditableImage -->

EditableImage | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/EditableImage.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)

English

Feedback

Engine Class

EditableImage

Not Creatable

---

## Summary

Properties

|

[Size](#Size) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
| --- | --- |

Methods

|

[Destroy](#Destroy) () : ()

 |
|

[DrawCircle](#DrawCircle) (center :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , radius :  [number](/docs/en-us/luau/numbers) , color :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) , transparency :  [number](/docs/en-us/luau/numbers) , combineType :  [Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , antiAliasing :  [Enum.AntiAliasing](/docs/en-us/reference/engine/enums/AntiAliasing) , alphaBlendType :  [Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[DrawImage](#DrawImage) (position :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , image :  [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , combineType :  [Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , alphaBlendType :  [Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[DrawImageProjected](#DrawImageProjected) (projectionSource :  [Object](/docs/en-us/reference/engine/classes/Object) , projection :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , brushConfig :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[SampleImageProjected](#SampleImageProjected) (projectionSource :  [Object](/docs/en-us/reference/engine/classes/Object) , sourceTexture :  [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , projectionConfig :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , brushConfig :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[DrawImageTransformed](#DrawImageTransformed) (position :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , scale :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , rotation :  [number](/docs/en-us/luau/numbers) , image :  [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ? ) : ()

 |
|

[DrawLine](#DrawLine) (p1 :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , p2 :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , color :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) , transparency :  [number](/docs/en-us/luau/numbers) , combineType :  [Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , antiAliasing :  [Enum.AntiAliasing](/docs/en-us/reference/engine/enums/AntiAliasing) , alphaBlendType :  [Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[DrawRectangle](#DrawRectangle) (position :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , size :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , color :  [Color3](/docs/en-us/reference/engine/datatypes/Color3) , transparency :  [number](/docs/en-us/luau/numbers) , combineType :  [Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , alphaBlendType :  [Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType) ) : ()

 |
|

[ReadPixelsBuffer](#ReadPixelsBuffer) (position :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , size :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) ) :[buffer](/docs/en-us/reference/engine/libraries/buffer)

 |
|

[WritePixelsBuffer](#WritePixelsBuffer) (position :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , size :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , buffer :  [buffer](/docs/en-us/reference/engine/libraries/buffer) ) : ()

 |

Inherited Members

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Size

Read Only

Not Replicated

Read Parallel

Capabilities: DynamicGeneration

EditableImage.Size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Methods

Destroy

Capabilities: DynamicGeneration

EditableImage:Destroy () : ()

Returns

()

Provide feedback

---

DrawCircle

Capabilities: DynamicGeneration

EditableImage:DrawCircle (

center :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , radius :[number](/docs/en-us/luau/numbers) , color :[Color3](/docs/en-us/reference/engine/datatypes/Color3) , transparency :[number](/docs/en-us/luau/numbers) , combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , antiAliasing :[Enum.AntiAliasing](/docs/en-us/reference/engine/enums/AntiAliasing) , alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

center :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

radius :[number](/docs/en-us/luau/numbers)

 |
|

color :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

transparency :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType)

Default Value: Overwrite |
|

antiAliasing :[Enum.AntiAliasing](/docs/en-us/reference/engine/enums/AntiAliasing)

Default Value: Enabled |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

Default Value: Default |

Returns

()

Provide feedback

---

DrawImage

Capabilities: DynamicGeneration

EditableImage:DrawImage (

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , image :[EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

image :[EditableImage](/docs/en-us/reference/engine/classes/EditableImage)

 |
|

combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType)

Default Value: AlphaBlend |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

Default Value: Default |

Returns

()

Provide feedback

---

DrawImageProjected

Capabilities: DynamicGeneration

EditableImage:DrawImageProjected (

projectionSource :[Object](/docs/en-us/reference/engine/classes/Object) , projection :[Dictionary](/docs/en-us/luau/tables#dictionaries) , brushConfig :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

projectionSource :[Object](/docs/en-us/reference/engine/classes/Object)

 |
|

projection :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

brushConfig :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Provide feedback

---

SampleImageProjected

Capabilities: DynamicGeneration

EditableImage:SampleImageProjected (

projectionSource :[Object](/docs/en-us/reference/engine/classes/Object) , sourceTexture :[EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , projectionConfig :[Dictionary](/docs/en-us/luau/tables#dictionaries) , brushConfig :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

projectionSource :[Object](/docs/en-us/reference/engine/classes/Object)

 |
|

sourceTexture :[EditableImage](/docs/en-us/reference/engine/classes/EditableImage)

 |
|

projectionConfig :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

brushConfig :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Provide feedback

---

DrawImageTransformed

Capabilities: DynamicGeneration

EditableImage:DrawImageTransformed (

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , scale :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , rotation :[number](/docs/en-us/luau/numbers) , image :[EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

) : ()

Parameters

|

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

scale :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

rotation :[number](/docs/en-us/luau/numbers)

 |
|

image :[EditableImage](/docs/en-us/reference/engine/classes/EditableImage)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

 |

Returns

()

Code Samples

EditableImage:DrawImageTransformed()

```

local AssetService = game:GetService("AssetService")

-- Example of drawing a rotated and scaled image onto another EditableImage

local srcImage = AssetService:CreateEditableImage({ Size = Vector2.new(256, 256) })

local dstImage = AssetService:CreateEditableImage({ Size = Vector2.new(512, 512) })

-- Drawing with a rotation of 45 degrees, scaling by 2x, and placing at (100, 100)

dstImage:DrawImageTransformed(

	Vector2.new(100, 100), -- Position

	Vector2.new(2, 2), -- Scale

	45, -- Rotation (degrees)

	srcImage, -- Source image

	{

		CombineType = Enum.ImageCombineType.AlphaBlend, -- Optional, default is AlphaBlend

		SamplingMode = Enum.ResamplerMode.Default, -- Optional, default is Default

		PivotPoint = srcImage.Size / 2, -- Optional, default is center of the source image

	}

)

```

EditableImage:DrawImageTransformed() - Crop

```

local AssetService = game:GetService("AssetService")

-- Source image

local srcImage = AssetService:CreateEditableImageAsync(Content.fromUri(assetUri))

-- Crop area defined by offset and size

local cropOffset = Vector2.new(50, 50)

local cropSize = Vector2.new(100, 100)

-- Destination image with size of the crop area

local dstImage = AssetService:CreateEditableImage({ Size = cropSize })

-- Position (top-left corner)

local position = Vector2.new(0, 0)

-- Scale factors (no scaling)

local scale = Vector2.new(1, 1)

-- Rotation angle (no rotation)

local rotation = 0

-- Draw the source image onto the destination image with adjusted pivot to crop the image

dstImage:DrawImageTransformed(position, scale, rotation, srcImage, {

	CombineType = Enum.ImageCombineType.Overwrite,

	PivotPoint = cropOffset, -- Set pivot point to cropOffset to start drawing from there

})

```

Provide feedback

---

DrawLine

Capabilities: DynamicGeneration

EditableImage:DrawLine (

p1 :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , p2 :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , color :[Color3](/docs/en-us/reference/engine/datatypes/Color3) , transparency :[number](/docs/en-us/luau/numbers) , combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , antiAliasing :[Enum.AntiAliasing](/docs/en-us/reference/engine/enums/AntiAliasing) , alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

p1 :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

p2 :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

color :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

transparency :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType)

Default Value: Overwrite |
|

antiAliasing :[Enum.AntiAliasing](/docs/en-us/reference/engine/enums/AntiAliasing)

Default Value: Enabled |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

Default Value: Default |

Returns

()

Provide feedback

---

DrawRectangle

Capabilities: DynamicGeneration

EditableImage:DrawRectangle (

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , color :[Color3](/docs/en-us/reference/engine/datatypes/Color3) , transparency :[number](/docs/en-us/luau/numbers) , combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType) , alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

) : ()

Parameters

|

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

color :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

transparency :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

combineType :[Enum.ImageCombineType](/docs/en-us/reference/engine/enums/ImageCombineType)

Default Value: Overwrite |
|

alphaBlendType :[Enum.ImageAlphaType](/docs/en-us/reference/engine/enums/ImageAlphaType)

Default Value: Default |

Returns

()

Provide feedback

---

ReadPixelsBuffer

Write Parallel

Capabilities: DynamicGeneration

EditableImage:ReadPixelsBuffer (

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

) :[buffer](/docs/en-us/reference/engine/libraries/buffer)

Parameters

|

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |

Returns

[buffer](/docs/en-us/reference/engine/libraries/buffer)

Code Samples

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

Provide feedback

---

WritePixelsBuffer

Capabilities: DynamicGeneration

EditableImage:WritePixelsBuffer (

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , buffer :[buffer](/docs/en-us/reference/engine/libraries/buffer)

) : ()

Parameters

|

position :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

size :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

buffer :[buffer](/docs/en-us/reference/engine/libraries/buffer)

 |

Returns

()

Code Samples

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

	-- Set alpha to 255 to make all pixels fully opaque.

	buffer.writeu8(pixelsBuffer, pixelIndex + 3, 255)

end

editableImage:WritePixelsBuffer(Vector2.zero, editableImage.Size, pixelsBuffer)

```

Provide feedback

---

Jump to

▼

EditableImage

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Size](#Size)

[Methods](#methods)

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

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
