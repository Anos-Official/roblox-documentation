<!-- Source: https://create.roblox.com/docs/environment/lighting -->

Global lighting | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment/lighting.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/environment)

# Global lighting

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/lighting.md)

The [Lighting](/docs/reference/engine/classes/Lighting)  service contains properties that you can adjust to update and customize the global lighting in a game. There are five categories of lighting properties:

-

[Color](#color)  — Configures hue within the game.

-

[Intensity](#intensity)  — Configures the intensity or amount of light hitting the camera.

-

[Shadows](#shadows)  — Configures how a user experiences shadows within the game.

-

[Appearance](#appearance)  — Properties that determine the lighting style and lighting/shading quality or view distance prioritization.

-

[Environment](#environment)  — Configures the conditions of the game's world, such as the time of day and geographic latitude.

## [Color](#color)[](#color)

### [Ambient](#ambient)[](#ambient)

The [Ambient](/docs/reference/engine/classes/Lighting#Ambient)  property sets a hue for the entirety  of a game. This property affects the lighting for both outdoor and indoor environments.

[0, 0, 0] [160, 80, 0] [25, 0, 125]

![Lighting.Ambient property of [0, 0, 0]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/Ambient-0-0-0.jpg)

### [OutdoorAmbient](#outdoorambient)[](#outdoorambient)

The [OutdoorAmbient](/docs/reference/engine/classes/Lighting#OutdoorAmbient)  property sets a hue for outdoor areas  of a game. This can help simulate how the ambient color of real-life lighting changes throughout the day. For example, sunlight in the early morning or late afternoon is usually warmer and more pink and orange in tone, while late evening is usually cooler and more blue and purple in tone.

In the following images, note that the lighting inside the garage and cafe doesn't change like it would if you were changing the [Ambient](#ambient)  property.

[255, 150, 50] [200, 150, 240] [0, 175, 255]

![Lighting.OutdoorAmbient property of [255, 150, 50]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/OutdoorAmbient-255-150-50.jpg)

### [ColorShift_Top](#colorshift_top)[](#colorshift_top)

The [ColorShift_Top](/docs/reference/engine/classes/Lighting#ColorShift_Top)  property sets a hue that reflects from surfaces facing the sun or moon.

[0, 100, 255] [255, 60, 0]

![Lighting.ColorShift_Top property of [0, 100, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ColorShift-Top-0-100-255.jpg)

### [ColorShift_Bottom](#colorshift_bottom)[](#colorshift_bottom)

The [ColorShift_Bottom](/docs/reference/engine/classes/Lighting#ColorShift_Bottom)  property sets a hue that reflects from surfaces that are facing away from the sun or moon.

In the following images, note the hue change on the sandstone wall facing away from the sun.

[255, 0, 220] [0, 255, 190]

![Lighting.ColorShift_Bottom property of [255, 0, 220]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ColorShift-Bottom-255-0-220.jpg)

## [Intensity](#intensity)[](#intensity)

### [Brightness](#brightness)[](#brightness)

The [Brightness](/docs/reference/engine/classes/Lighting#Brightness)  property sets the intensity of illumination. This can help increase the contrast between brightly illuminated areas and shadows, simulating bright sunshine and warmer weather.

0.5 1.5 3.75

![Lighting.Brightness property of 0.5](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/Brightness-0.5.jpg)

### [ExposureCompensation](#exposurecompensation)[](#exposurecompensation)

The [ExposureCompensation](/docs/reference/engine/classes/Lighting#ExposureCompensation)  property applies exposure to a game. Exposure is the amount of light that reaches the camera.

A lower value is similar to under-exposure in photography, while a higher value is similar to over-exposure.

0 -1 1.25

![Lighting.ExposureCompensation property of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ExposureCompensation-0.jpg)

## [Shadows](#shadows)[](#shadows)

### [GlobalShadows](#globalshadows)[](#globalshadows)

When enabled, the [GlobalShadows](/docs/reference/engine/classes/Lighting#GlobalShadows)  property renders shadows.

Enabled Disabled

![Lighting.GlobalShadows property enabled](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/GlobalShadows-True.jpg)

### [ShadowSoftness](#shadowsoftness)[](#shadowsoftness)

The [ShadowSoftness](/docs/reference/engine/classes/Lighting#ShadowSoftness)  property adjusts how blurry shadows are from a value of 0  (hard edges) to 1  (soft edges). This property is only valid when [LightingStyle](/docs/reference/engine/classes/Lighting#LightingStyle)  is set to [Realistic](/docs/reference/engine/enums/LightingStyle) .

0 1

![Lighting.ShadowSoftness property of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ShadowSoftness-0.jpg)

## [Appearance](#appearance)[](#appearance)

### [LightingStyle](#lightingstyle)[](#lightingstyle)

[LightingStyle](/docs/reference/engine/classes/Lighting#LightingStyle)  indicates the artistic intent behind lighting in the game, as an [Enum.LightingStyle](/docs/reference/engine/enums/LightingStyle)  option. [Realistic](/docs/reference/engine/enums/LightingStyle)  provides the most advanced and realistic lighting and shadows Roblox can deliver, while [Soft](/docs/reference/engine/enums/LightingStyle)  produces a flat, retro‑Roblox look with softer lights and shadows.

Realistic Soft

![Lighting.LightingStyle setting of Realistic](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/LightingStyle-Realistic.jpg)

### [PrioritizeLightingQuality](#prioritizelightingquality)[](#prioritizelightingquality)

The [PrioritizeLightingQuality](/docs/reference/engine/classes/Lighting#PrioritizeLightingQuality)  property indicates whether you prefer lighting/shading quality or view distance to scale down first. As the rendering quality level reduces, a setting of true  prioritizes features such as advanced shadows and high‑quality shaders at closer distances, while a setting of false  prioritizes view distance. If lighting and shadows are very important to the artistic feel of your game, set this to true .

## [Environment](#environment)[](#environment)

### [ClockTime and TimeOfDay](#clocktime-and-timeofday)[](#clocktime-and-timeofday)

The [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime)  and [TimeOfDay](/docs/reference/engine/classes/Lighting#TimeOfDay)  property both represent the current time of day in hours, and they are directly related; if you change one property, the other also changes.

The only difference between these properties is their numeric value; [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime)  represents time from hour 0  through 24  while [TimeOfDay](/docs/reference/engine/classes/Lighting#TimeOfDay)  represents time through a 24 hour string.

0 = 00:00:00 6.3 = 06:18:00 17 = 17:00:00

![Lighting.ClockTime of 0 (TimeOfDay of 00:00:00)](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/TimeOfDay-0.jpg)

Note that each property doesn't follow the actual time of day, and they will not change during a game unless changed through a script.

### [GeographicLatitude](#geographiclatitude)[](#geographiclatitude)

The [GeographicLatitude](/docs/reference/engine/classes/Lighting#GeographicLatitude)  property represents the geographic latitude in degrees. Note that while this property changes the position of the sun and moon, it does not change the [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime)  and [TimeOfDay](/docs/reference/engine/classes/Lighting#TimeOfDay)  properties.

### [EnvironmentDiffuseScale](#environmentdiffusescale)[](#environmentdiffusescale)

The [EnvironmentDiffuseScale](/docs/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  property determines how much ambient light is derived from the environment.

In the following images, note how the ambient light changes, particularly inside the kitchen of the ramen shop.

0 1

![Lighting.EnvironmentDiffuseScale property of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/EnvironmentDiffuseScale-0.jpg)

### [EnvironmentSpecularScale](#environmentspecularscale)[](#environmentspecularscale)

The [EnvironmentSpecularScale](/docs/reference/engine/classes/Lighting#EnvironmentSpecularScale)  property determines how much specular light is derived from the environment. When set near a value of 1, smooth objects better reflect the environment and metal appears more realistic.

0 1

![Lighting.EnvironmentSpecularScale property of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/EnvironmentSpecularScale-0.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
