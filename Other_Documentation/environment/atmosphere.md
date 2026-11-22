<!-- Source: https://create.roblox.com/docs/environment/atmosphere -->

Atmospheric effects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment/atmosphere.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/environment)

# Atmospheric effects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/atmosphere.md)

Atmospheric effects  simulate realistic environments by scattering sunlight in unique ways based on properties that control air particles. Using the [Atmosphere](/docs/reference/engine/classes/Atmosphere)  object, you can:

-

Control particle density.

-

Create a silhouette or blend distant objects with an offset.

-

Simulate a haze or glare.

-

Set an atmosphere's color or decay.

 ![Atmospheric effects used to render a brilliant sunset scene](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Sahara-Sunset.jpg)

## [Atmosphere properties](#atmosphere-properties)[](#atmosphere-properties)

Every property of the [Atmosphere](/docs/reference/engine/classes/Atmosphere)  object inside the [Lighting](/docs/reference/engine/classes/Lighting)  service works together to support the overall vision, themes, and mood of your game.

 ![Atmosphere object shown in Explorer window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Lighting-Atmosphere.png)

### [Density](#density)[](#density)

The [Density](/docs/reference/engine/classes/Atmosphere#Density)  property controls how many particles exist in the air of your game; the higher the density, the more particles, which obstruct a player's view of objects and terrain.

0 0.35

![Atmosphere with Density value of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Density-A.jpg)

Density only directly  affects objects and terrain; however, since you view a [skybox](/docs/environment/skybox)  through those objects and terrain, the visibility of a skybox is also affected.

### [Offset](#offset)[](#offset)

The [Offset](/docs/reference/engine/classes/Atmosphere#Offset)  property controls how light transmits between the camera and the sky background. When you increase this value, it creates a horizon silhouette; when you decrease this value, it blends distant objects into the sky for a seemingly endless and seamless open world.

0 1

![Atmosphere with Offset value of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Offset-A.jpg)

Carefully balance the [Offset](/docs/reference/engine/classes/Atmosphere#Offset)  property with the [Density](/docs/reference/engine/classes/Atmosphere#Density)  property. A low offset value may cause the [skybox](/docs/environment/skybox)  to be seen through objects and terrain, and a high offset value may cause distant objects and terrain to have too much detail for your desired lighting effect.

### [Haze](#haze)[](#haze)

The [Haze](/docs/reference/engine/classes/Atmosphere#Haze)  property controls the haziness of the atmosphere to create a visible effect both above the horizon and far into the distance from the camera. To create environmental moods, like a smoky tint for a polluted alien planet or a foggy blue tint for a somber game, combine this property with the [Color](#color)  property.

1 2.8

![Atmosphere with Haze value of 1](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Haze-A.jpg)

### [Color](#color)[](#color)

The [Color](/docs/reference/engine/classes/Atmosphere#Color)  property sets the hue of the atmosphere for subtle environmental moods and themes. To expand this property's visible effect, combine it with a high [Haze](#haze)  property value.

[255, 255, 255] [255, 200, 255]

![Atmosphere with Color value of [255, 255, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Color-A.jpg)

### [Glare](#glare)[](#glare)

The [Glare](/docs/reference/engine/classes/Atmosphere#Glare)  property sets an atmospheric glare around the sun. A high value results in an increased effect of sunlight cast onto the sky and game. To see this property's visible effect, you must  combine a glare with a [Haze](#haze)  value higher than 0.

0 1

![Atmosphere with Glare value of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Glare-A.jpg)

### [Decay](#decay)[](#decay)

The [Decay](/docs/reference/engine/classes/Atmosphere#Decay)  property sets the hue of the atmosphere away from the sun, gradually falling off from [Color](#color)  toward this value. To see this property's visible effect, you must  combine a glare with [Haze](#haze)  and [Glare](#glare)  values higher than 0.

[255, 255, 255] [255, 90, 80]

![Atmosphere with Decay value of [255, 255, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Decay-A.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
