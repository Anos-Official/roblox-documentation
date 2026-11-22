<!-- Source: https://create.roblox.com/docs/parts/textures-decals -->

Textures and decals | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts/textures-decals.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Parts](/docs/parts)

# Textures and decals

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/textures-decals.md)

A [Texture](/docs/reference/engine/classes/Texture)  is an image you can place on any face of a [part](/docs/parts)  or [union](/docs/parts/solid-modeling)  that repeats  both horizontally and vertically on the size of the surface. In contrast, a [Decal](/docs/reference/engine/classes/Decal)  is an image that stretches  to fit the area of a part or union's surface. After you add a [Texture](/docs/reference/engine/classes/Texture)  or [Decal](/docs/reference/engine/classes/Decal)  object to a part or union, you can:

-

Change the texture or decal [Color3](/docs/reference/engine/classes/Decal#Color3)  property to set a color tint using RGB color codes.

-

Change the texture or decal [Transparency](/docs/reference/engine/classes/Decal#Transparency)  property to a value between the default of 0  (fully visible) and 1  (invisible).

-

For a texture, set its [scale](#scale-textures)  and [offset](#offset-textures) .

![An example texture image of a light blue hexagon on top of a dark blue background.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Decal-Texture-Sample-2.png) Texture image

![The same texture repeated eight times on a block part.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-On-Surface.jpg) Texture applied to a part (repeating)

![An example decal image of a light purple hexagon on top of a dark purple background.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Decal-Texture-Sample-1.png) Decal image

![The same decal stretched on a block part.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Decal-On-Surface.jpg) Decal applied to a part (stretched)

## [Create textures or decals](#create-textures-or-decals)[](#create-textures-or-decals)

To create a texture or decal, you must add either a [Texture](/docs/reference/engine/classes/Texture)  or [Decal](/docs/reference/engine/classes/Decal)  object to a part or union. You can [import](/docs/projects/assets/manager#asset-import)  images for textures and decals to Studio for use between games, and [distribute](/docs/production/creator-store)  them to the [Creator Store](/docs/production/creator-store) . Once you import the image, Studio assigns it a unique asset ID.

Every texture or decal image that you create and import to Roblox must adhere to the [Community Rules](https://en.help.roblox.com/hc/articles/203313410)  and [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) .

To add a texture or decal to a [part](/docs/parts)  or [union](/docs/parts/solid-modeling) :

1.

In the [Explorer](/docs/studio/explorer)  window, add a [Texture](/docs/reference/engine/classes/Texture)  or [Decal](/docs/reference/engine/classes/Decal)  to the part or union. An empty texture or decal object displays on the part or union with orange outlining.

2.

In the [Properties](/docs/studio/properties)  window, navigate to the [Face](/docs/reference/engine/classes/FaceInstance#Face)  property and choose a face ([Top](/docs/reference/engine/enums/NormalId) , [Bottom](/docs/reference/engine/enums/NormalId) , [Front](/docs/reference/engine/enums/NormalId) , [Back](/docs/reference/engine/enums/NormalId) , [Left](/docs/reference/engine/enums/NormalId) , or [Right](/docs/reference/engine/enums/NormalId) ).

-

OPTIONAL

 To assist in choosing the correct face, right-click the part/union and select Show Orientation Indicator . This displays a circle 🅕 , a blue line attached to the object's front face, and a green arrow that points in the direction of the object's top face.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Orientation-Indicator.jpg)

3.

Select the [ColorMapContent](/docs/reference/engine/classes/Decal#ColorMapContent)  property and apply an image through any of the following methods:

-

Select any texture or decal you've uploaded previously.

-

Enter an [asset ID](/docs/projects/assets)  into the field.

4.

OPTIONAL

 Set a color tint by clicking the small box to the left of the [Color3](/docs/reference/engine/classes/Decal#Color3)  property or by entering a RGB color code.

![A close of view of the Color3 property with the small color box highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Appearance-Color3-Picker.png)

![A close of view of the Color3 property with the RGB code highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Appearance-Color3-RGB-Entry.png)

![A block part with a repeating blue hexagon texture on its top face.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-On-Surface.jpg)[Color3](/docs/reference/engine/classes/Decal#Color3) : [255, 255, 255]

![The same block part with a repeating hexagon texture on its top face, but the hexagons are pink against on dark purple background.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Color3-255-0-100.jpg)[Color3](/docs/reference/engine/classes/Decal#Color3) : [255, 0, 100]

5.

OPTIONAL

 Set the [Transparency](/docs/reference/engine/classes/Decal#Transparency)  property to any value between the default of 0  (fully visible) and 1  (invisible).

![A block part with a repeating blue hexagon texture on its top face.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-On-Surface.jpg)[Transparency](/docs/reference/engine/classes/Decal#Transparency) : 0

![The same block part with a repeating hexagon texture on its top face, but the hexagons are semi-transparent.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Transparency-0.4.jpg)[Transparency](/docs/reference/engine/classes/Decal#Transparency) : 0.6

## [Customize textures](#customize-textures)[](#customize-textures)

Unlike decals, textures  provide further functionality to scale, offset, and animate the source image.

### [Scale textures](#scale-textures)[](#scale-textures)

The size of the part doesn't affect the texture. Instead, scaling a part only increases or decreases the number of times the texture repeats.

The [StudsPerTileU](/docs/reference/engine/classes/Texture#StudsPerTileU)  and [StudsPerTileV](/docs/reference/engine/classes/Texture#StudsPerTileV)  properties determine the size of each "tile" in studs. [StudsPerTileU](/docs/reference/engine/classes/Texture#StudsPerTileU)  determines the texture's horizontal size while [StudsPerTileV](/docs/reference/engine/classes/Texture#StudsPerTileV)  determines the texture's vertical size.

StudsPerTileU & StudsPerTileV = 2 StudsPerTileU & StudsPerTileV = 4

![Texture on a surface of 8x6 studs with size of each tile in 2x2.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Sample-Scale-1.png)

### [Offset textures](#offset-textures)[](#offset-textures)

If you want more control over a texture's position, offset the texture by adjusting the [OffsetStudsU](/docs/reference/engine/classes/Texture#OffsetStudsU)  (horizontal) and [OffsetStudsV](/docs/reference/engine/classes/Texture#OffsetStudsV)  (vertical) properties. This is also helpful for [animation](#animate-textures) .

OffsetStudsU & OffsetStudsV = 0 OffsetStudsU & OffsetStudsV = 0.5

![2x2 texture on a surface of 8x6 studs with no offset.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Sample-Offset-1.png)

### [Animate textures](#animate-textures)[](#animate-textures)

Using [TweenService](/docs/reference/engine/classes/TweenService) , you can tween texture properties like [OffsetStudsU](/docs/reference/engine/classes/Texture#OffsetStudsU)  and [StudsPerTileV](/docs/reference/engine/classes/Texture#StudsPerTileV)  to achieve animated surfaces. For example, if you apply two fog textures to one container and animate them with the following script, you can achieve the appearance of a layered moving fog.

Two animated textures near the floor to simulate a moving fog effect

```

local TweenService = game:GetService("TweenService")

local texture1 = script.Parent.Texture1

local texture2 = script.Parent.Texture2

local tweenInfo1 = TweenInfo.new(8, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut, -1)

local tween1 = TweenService:Create(texture1, tweenInfo1, {OffsetStudsV=50})

local tweenInfo2 = TweenInfo.new(7, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut, -1, true)

local tween2 = TweenService:Create(texture2, tweenInfo2, {OffsetStudsU=50, StudsPerTileU=55, StudsPerTileV=45})

tween1:Play()

tween2:Play()

```

## [Texture streaming](#texture-streaming)[](#texture-streaming)

Texture streaming  dynamically loads textures based on distance and camera view, which lets you use textures more freely without worrying about scaling across devices. The engine loads baseline-quality textures first, in order of importance, and then progressively raises the quality of each texture up to the memory available on the device. Texture streaming is enabled automatically, so you don't have to take any action to benefit from it.

![A visualization showing a game with and without texture streaming.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/texture-streaming.webp) The same scene with and without texture streaming

### [Benefits](#benefits)[](#benefits)

-

Faster perceived load times and smaller downloads : Textures appear almost immediately at a baseline quality, and the engine downloads only the detail it needs, compressing it both in transit and on the local disk cache.

-

Higher quality where it matters : The engine continuously estimates how important each object is, such as by how much screen space it occupies, and uses the memory budget on those textures so that the most prominent objects get the highest detail.

-

Fewer out-of-memory crashes : Because the engine stays within a memory budget and can lower texture quality when memory runs low, players are much less likely to crash from texture memory spikes.

Texture streaming works with [MeshPart](/docs/reference/engine/classes/MeshPart)  (skinned and unskinned), [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance) , [Texture](/docs/reference/engine/classes/Texture) , [Decal](/docs/reference/engine/classes/Decal) , [MaterialVariant](/docs/reference/engine/classes/MaterialVariant) , [Beam](/docs/reference/engine/classes/Beam) , [ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter) , and the base materials applied to [PartOperation](/docs/reference/engine/classes/PartOperation)  and [BasePart](/docs/reference/engine/classes/BasePart)  instances.

### [Best practices](#best-practices)[](#best-practices)

-

Favor unique, individual textures over texture atlases unless the atlas is applied to batchable parts; requesting a high resolution for one texture in an atlas streams in the entire atlas at that resolution.

-

Use near-uniform texel density in your UV-mapped meshes so that the engine can select the best resolution for each texture.

-

Continue to manage texture memory carefully for instance types that texture streaming doesn't support yet.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
