<!-- Source: https://create.roblox.com/docs/effects/light-sources -->

Light sources | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/effects/light-sources.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Effects](/docs/effects)

# Light sources

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/effects/light-sources.md)

Local light sources simulate realistic lighting from objects such as lamps, torches, spotlights, and TV screens. By using the different types of light sources instead of just general global lighting through the [Lighting](/docs/reference/engine/classes/Lighting)  service, you can create immersive environments such as cyberpunk cities, traditional light festivals, and moody detective scenes.

 ![A far out view of a diner bulding in the middle of a nighttime city. The diner is utilizing several local light sources.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Showcase.jpg)

The [LightingStyle](/docs/reference/engine/classes/Lighting#LightingStyle)  property, modifiable only in the [Properties](/docs/studio/properties)  window for the global [Lighting](/docs/reference/engine/classes/Lighting)  object, sets your game's lighting style. For more information, see [Appearance](/docs/environment/lighting#appearance) .

To view light guides  that indicate the color and field of effect from light sources, such as the angle of light emission from the cone's apex of a [SpotLight](/docs/reference/engine/classes/SpotLight) , open [Studio Settings](/docs/studio/setup#customization)  and toggle on Show Light Guides .

## [Light types](#light-types)[](#light-types)

Local light sources include [PointLight](#pointlight) , [SpotLight](#spotlight) , and [SurfaceLight](#surfacelight) . Each [shares various properties](#shared-properties)  from the [Light](/docs/reference/engine/classes/Light)  class, including [Color](/docs/reference/engine/classes/Light#Color) , [Brightness](/docs/reference/engine/classes/Light#Brightness) , and [Shadows](/docs/reference/engine/classes/Light#Shadows) .

### [PointLight](#pointlight)[](#pointlight)

A [PointLight](/docs/reference/engine/classes/PointLight)  emits light spherically from a single point. This object is ideal for non-directional  lights like bulbs, torches, and fireballs.

To create a point light in Studio, insert a [PointLight](/docs/reference/engine/classes/PointLight)  into an [Attachment](/docs/reference/engine/classes/Attachment)  or a [BasePart](/docs/reference/engine/classes/BasePart)  ([Attachment](/docs/reference/engine/classes/Attachment)  is recommended for point‑specific light emission). Then adjust the object's [Range](/docs/reference/engine/classes/PointLight#Range)  as well as [shared properties](#shared-properties)  like [Brightness](/docs/reference/engine/classes/PointLight#Brightness)  and [Color](/docs/reference/engine/classes/PointLight#Color) .

#### [Range](#range)[](#range)

A point light's [Range](/docs/reference/engine/classes/PointLight#Range)  property defines the radial distance of illumination from the light's position, measured in studs.

8 12

![A street lamp point light with a small range.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/PointLight-Range-8.jpg)

### [SpotLight](#spotlight)[](#spotlight)

A [SpotLight](/docs/reference/engine/classes/SpotLight)  emits light in the shape of a cone with a spherical base. This object is ideal for directional lights like street lamps, flashlights, and headlights.

To create a spotlight in Studio, insert a [SpotLight](/docs/reference/engine/classes/SpotLight)  into an [Attachment](/docs/reference/engine/classes/Attachment)  or a [BasePart](/docs/reference/engine/classes/BasePart)  and set its [Face](/docs/reference/engine/classes/SpotLight#Face)  property to specify which direction light emits from. Then adjust the [Angle](/docs/reference/engine/classes/SpotLight#Angle)  and [Range](/docs/reference/engine/classes/SpotLight#Range) , as well as [shared properties](#shared-properties)  like [Brightness](/docs/reference/engine/classes/SpotLight#Brightness)  and [Color](/docs/reference/engine/classes/SpotLight#Color) .

#### [Face](#face)[](#face)

A spotlight's [Face](/docs/reference/engine/classes/SpotLight#Face)  property determines which face/axis light emits from, as shown from the following streetlamp's glowing light part:

Bottom Left

![A street lamp spotlight that emits light from its bottom face.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SpotLight-Face-Bottom.jpg)

#### [Angle](#angle)[](#angle)

A spotlight's [Angle](/docs/reference/engine/classes/SpotLight#Angle)  property defines the angle of light emission from the cone's apex. The maximum value is 180  which illuminates a full half sphere from the apex.

30 75

![A street lamp spotlight with a 30 degree angle of emission.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SpotLight-Angle-30.jpg)

### [SurfaceLight](#surfacelight)[](#surfacelight)

A [SurfaceLight](/docs/reference/engine/classes/SurfaceLight)  emits light from the face of a [BasePart](/docs/reference/engine/classes/BasePart) . This object is ideal for lighting from computer screens, billboards, signs, and fluorescent panels.

To create a surface light in Studio, insert a [SurfaceLight](/docs/reference/engine/classes/SurfaceLight)  into a [BasePart](/docs/reference/engine/classes/BasePart)  and set its [Face](/docs/reference/engine/classes/SurfaceLight#Face)  property to specify which surface light emits from. Then adjust the [Angle](/docs/reference/engine/classes/SurfaceLight#Angle)  and [Range](/docs/reference/engine/classes/SurfaceLight#Range) , as well as [shared properties](#shared-properties)  like [Brightness](/docs/reference/engine/classes/SurfaceLight#Brightness)  and [Color](/docs/reference/engine/classes/SurfaceLight#Color) .

#### [Face](#face-1)[](#face-1)

A surface light's [Face](/docs/reference/engine/classes/SurfaceLight#Face)  property determines the face of the [BasePart](/docs/reference/engine/classes/BasePart)  from which light emanates. Notice that light emits from the entire surface, not just a point on the surface.

Bottom Right

![A sign surface light that emits light from its bottom face.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SurfaceLight-Face-Bottom.jpg)

#### [Angle](#angle-1)[](#angle-1)

A surface light's [Angle](/docs/reference/engine/classes/SurfaceLight#Angle)  property defines the angle of light emission from the part's surface. An angle of 0  means that light travels directly outward from the surface while an angle of 180  means light travels outward perpendicular to the surface.

0 60

![A sign surface light with a 0 degree angle of emission.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SurfaceLight-Angle-0.jpg)

## [Shared properties](#shared-properties)[](#shared-properties)

All light sources share various properties from the [Light](/docs/reference/engine/classes/Light)  class, including [color](#color) , [brightness](#brightness) , and [shadows](#shadows) .

### [Color](#color)[](#color)

The [Color](/docs/reference/engine/classes/Light#Color)  property sets the [Color3](/docs/reference/engine/datatypes/Color3)  value of the emitted light.

[255, 100, 50] [0, 255, 125] [75, 150, 255]

![A torch that emits red light.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Light-Color-255-100-50.jpg)

### [Brightness](#brightness)[](#brightness)

The [Brightness](/docs/reference/engine/classes/Light#Brightness)  property sets the light's brightness with maximum effect at the center of the light. Note that [Brightness](/docs/reference/engine/classes/Light#Brightness)  is still limited to the light's defined range, so a higher [Brightness](/docs/reference/engine/classes/Light#Brightness)  value doesn't light up a larger region around the light.

2 10 50

![A torch that emits low light.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Light-Brightness-2.jpg)

### [Shadows](#shadows)[](#shadows)

The [Shadows](/docs/reference/engine/classes/Light#Shadows)  property projects shadows where light is blocked by an obstacle.

Enabled Disabled

![A corner view of the diner with shadows enabled.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Light-Shadows-True.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
