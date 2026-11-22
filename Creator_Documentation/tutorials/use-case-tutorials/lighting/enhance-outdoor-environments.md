<!-- Source: https://create.roblox.com/docs/en-us/tutorials/use-case-tutorials/lighting/enhance-outdoor-environments -->

Enhance outdoor environments with realistic lighting | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/lighting/enhance-outdoor-environments.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Lighting

# Enhance outdoor environments with realistic lighting

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/lighting/enhance-outdoor-environments.md)

[Realistic](/docs/en-us/reference/engine/enums/LightingStyle)  lighting is the most advanced and powerful [LightingStyle](/docs/en-us/reference/engine/classes/Lighting#LightingStyle)  you can use for rendering the 3D environment within your games. It offers pixel perfect light emission, detailed shadows, and specular highlights that mimic real-world lighting for both indoor and outdoor spaces.

Using the [Lighting Outdoors - Start](https://www.roblox.com/games/17835285085/Lighting-Outdoors-Start)  .rbxl  file as a starting place and [Lighting Outdoors - Complete](https://www.roblox.com/games/17835194683/Lighting-Outdoors-Complete)  as a reference, this tutorial shows you how to utilize realistic lighting with strategic global and local light source configurations to produce realistic, immersive outdoor lighting behavior for an evening campfire scene, including guidance on:

-

Ensuring metallic surfaces produce accurate reflections as light sources continuously shift in the environment, such as dynamic movement from the roaring campfire.

-

Moving the sun to a new position that's realistic for the real world's time of day.

-

Customizing the atmosphere's layered hues, density, and haze.

-

Configuring point source local lighting to impact how it interacts with the overall environment.

If at any point you become stuck in the process, you can use Lighting Outdoors - Complete  as a reference to compare your progress.

![The starting outdoor environment you can use to complete this tutorial.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Intro-Before.png) Lighting Outdoors - Start

![The complete outdoor environment with global and local lighting you will create by the end of this tutorial.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Intro-After.png) Lighting Outdoors - Complete

## [Configure global lighting](#configure-global-lighting)[](#configure-global-lighting)

Global lighting is the luminescence from either the sun or moon in a game. By adjusting a couple of key default properties in the [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service, you can dramatically change how that light appears to players, as well as how it interacts with any other object you place in the game.

### [Enable realistic lighting](#enable-realistic-lighting)[](#enable-realistic-lighting)

The [LightingStyle](/docs/en-us/reference/engine/classes/Lighting#LightingStyle)  property determines the behavior of both global and local lighting in your game. Studio begins every game with [Soft](/docs/en-us/reference/engine/enums/LightingStyle)  lighting which renders a flatter look with softer lights and shadows. However, to enhance the environment and equip your local light sources to also produce precise shadows and illumination, such as the light from the campfire, you must enable [Realistic](/docs/en-us/reference/engine/enums/LightingStyle)  lighting.

To demonstrate this concept, see the following two images of the same campfire with different lighting styles. The local lighting from the campfire with [Soft](/docs/en-us/reference/engine/enums/LightingStyle)  lighting doesn't produce shadows in the same way that the global lighting from the sun does, making this area of the environment unevenly lit with unrealistic shadows. By contrast, the local lighting from the campfire with [Realistic](/docs/en-us/reference/engine/enums/LightingStyle)  lighting interacts with the kindling, rocks, and brush around the environment, producing crisp and realistic shadows for evening time.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/LightingStyle-Soft.jpg)[Soft](/docs/en-us/reference/engine/enums/LightingStyle)  lighting style

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/LightingStyle-Realistic.jpg)[Realistic](/docs/en-us/reference/engine/enums/LightingStyle)  lighting style

To enable realistic lighting:

1.

In the Explorer  window, select Lighting .

2.

In the Properties  window, click the LightingStyle  dropdown, then select Realistic .

### [Elevate metal reflections](#elevate-metal-reflections)[](#elevate-metal-reflections)

By default, all materials use physically-based rendering (PBR) textures that allow you to display realistic surfaces in various lighting scenarios by using multiple image files on a single object. This means that when you use Studio's built-in materials, the metalness and roughness of a particular surface is already defined for you, and the objects with those materials naturally react more accurately to the lighting in your environment with realistic reflections. You can enhance this effect by setting the [Lighting.EnvironmentDiffuseScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  and [Lighting.EnvironmentSpecularScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentSpecularScale)  properties to 1  to truly take advantage of metal reflections from [Enum.LightingStyle.Realistic](/docs/en-us/reference/engine/enums/LightingStyle#Realistic)  lighting.

This step is important because it ensures that any PBR textures in your game, including those from [MaterialVariants](/docs/en-us/reference/engine/classes/MaterialVariant)  or [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  objects, look their best and reflect their surroundings better. For example, examine the following two images of the same pan and utensils near the campfire with different [Lighting.EnvironmentDiffuseScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  and [Lighting.EnvironmentSpecularScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentSpecularScale)  property values. When you adjust these values, the metal becomes more apparent and reflects the lighting from both the global and local light sources significantly more than before.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/EnvironmentScale-0.jpg)[Lighting.EnvironmentDiffuseScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  and [Lighting.EnvironmentSpecularScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentSpecularScale)  = 0

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/EnvironmentScale-1.jpg)[Lighting.EnvironmentDiffuseScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  and [Lighting.EnvironmentSpecularScale](/docs/en-us/reference/engine/classes/Lighting#EnvironmentSpecularScale)  = 1

To elevate metal reflections:

1.

In the Explorer  window, select Lighting .

2.

In the Properties  window, set EnvironmentalDiffuseScale  and EnvironmentSpecularScale  to 1 . The metal in the game becomes more reflective.

### [Change the time of day](#change-the-time-of-day)[](#change-the-time-of-day)

Now that your game is using the [Enum.LightingStyle.Realistic](/docs/en-us/reference/engine/enums/LightingStyle#Realistic)  lighting style and materials are reacting realistically to the light sources in your game, it's time to move the sun to a different position according to where it would be in the real world for the time of day. The sun's default position is high in the sky, emulating around midday in the real world, so it's best to move it nearer to the skyline, right above the mountains. This step also allows the light to move down the path onto the campfire and achieve a nice golden sun.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Default-Sun-Position.png) The default sun is high in the sky. While this placement is great if the campfire was happening around noon, it's not realistic for the evening.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/New-Sun-Position.png) The new sun position is much more appropriate for the time of day right before sunset.

To change the time of day:

1.

In the Explorer  window, select Lighting .

2.

In the Properties  window, set ClockTime  to 17 . The sun moves to the approximate position it would be in at 5pm.

### [Adjust the color of ambient light](#adjust-the-color-of-ambient-light)[](#adjust-the-color-of-ambient-light)

There are two [Lighting](/docs/en-us/reference/engine/classes/Lighting)  properties that control the color of ambient lighting:

-

[Lighting.OutdoorAmbient](/docs/en-us/reference/engine/classes/Lighting#OutdoorAmbient)  controls ambient lighting where the sky is visible.

-

[Lighting.Ambient](/docs/en-us/reference/engine/classes/Lighting#Ambient)  controls ambient lighting within spaces where anything blocks the sky, such as indoor spaces or under tree cover.

By default, these properties are set to produce gray ambient lighting, but to compliment the evening sky, you must adjust these values to add a realistic hue and brightness in darker spaces of the game for evening time. For example, an evening sky has a lot more purple than gray, so picking a purple hue for ambient lighting creates a realistic environment.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Ambient-Default.png)[Lighting.OutdoorAmbient](/docs/en-us/reference/engine/classes/Lighting#OutdoorAmbient)  and [Lighting.Ambient](/docs/en-us/reference/engine/classes/Lighting#Ambient)  = 70, 70, 70

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Ambient-New.png)[Lighting.OutdoorAmbient](/docs/en-us/reference/engine/classes/Lighting#OutdoorAmbient)  and [Lighting.Ambient](/docs/en-us/reference/engine/classes/Lighting#Ambient)  = 156, 136, 176

To adjust the color of ambient lighting:

1.

In the Explorer  window, select Lighting .

2.

In the Properties  window, set Outdoor Ambient  and Ambient  to 156, 136, 176 . The ambient lighting changes to a light purple hue.

### [Choose a skybox](#choose-a-skybox)[](#choose-a-skybox)

A skybox is a cube made up of six individual images that create a game's sky, including what's above and below the horizon. Skyboxes can have a major impact on the look and feel of what's in your environment, so it's important to carefully consider how you can choose a skybox that enhances your game's visual quality. For example:

-

A skybox's lower hemisphere should be similar to the color of your general terrain. This ensures the lower hemisphere closely relates to the ground surface, and that the colors that reflect off of objects will roughly match the skybox.

-

A skybox's lower hemisphere should be darker than the upper hemisphere because a darker lower hemisphere replicates the natural occlusion of light from below the ground, making your lighting more immersive.

-

A skybox doesn't require clouds, because you can easily add in [dynamic clouds](/docs/en-us/environment/clouds)  to achieve the same effect and supplement your skybox.

To illustrate these concepts, examine the following two images to see how the same chrome sphere reflects two different skyboxes. The first skybox has the same level of brightness for both the upper and lower hemispheres, so it doesn't seem like the sphere is reflecting the world around it well. By contrast, the second skybox has a darker lower hemisphere from its upper hemisphere, achieving a more natural look. For information on how to create and customize skyboxes, see [Skyboxes](/docs/en-us/environment/skybox) .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Bad-Skybox.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Good-Skybox.png)

### [Atmospheric effects](#atmospheric-effects)[](#atmospheric-effects)

The [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service has a child [Atmosphere](/docs/en-us/reference/engine/classes/Atmosphere)  object with properties that allow you to simulate realistic environments by scattering sunlight in unique ways. These properties can be very useful in creating a thickness in the game's air, giving the environment a tangible sense of depth. The [Atmosphere](/docs/en-us/reference/engine/classes/Atmosphere)  object pulls most of its colors from the skybox directly, which is why the previous decisions about your skybox were so important.

#### [Increase air particle density](#increase-air-particle-density)[](#increase-air-particle-density)

The [Atmosphere.Density](/docs/en-us/reference/engine/classes/Atmosphere#Density)  property controls how many particles exist in the air of your game. When you increase this property, the additional amount of particles obstruct the player's view of objects in the background. For example, when [Atmosphere.Density](/docs/en-us/reference/engine/classes/Atmosphere#Density)  is 0 , the background trees, sun, and skybox are clearly visible, but when you increase this property to 0.391 , the particles start to scatter the light and conceal the trees.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Density-0.jpg)[Atmosphere.Density](/docs/en-us/reference/engine/classes/Atmosphere#Density)  = 0

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Density-0.3.jpg)[Atmosphere.Density](/docs/en-us/reference/engine/classes/Atmosphere#Density)  = 0.391

To increase density of the air particles in the atmosphere:

1.

In the Explorer  window, select Atmosphere .

2.

In the Properties  window, set Density  to 0.272 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Density-0.272.png)

#### [Add a haze](#add-a-haze)[](#add-a-haze)

The [Atmosphere.Haze](/docs/en-us/reference/engine/classes/Atmosphere#Haze)  property controls the overall haziness of the atmosphere to create a visible effect both above the horizon and far into the distance from the camera. When you increase this property, it not only affects the overall environment, but it also affects objects that have a particularly powerful fresnel effect, such as metal objects that reflect the environment around them.

To add haze to the atmosphere:

1.

In the Explorer  window, select Atmosphere .

2.

In the Properties  window, set Haze  to 1 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Haze-1.png)

#### [Adjust the color of the atmosphere](#adjust-the-color-of-the-atmosphere)[](#adjust-the-color-of-the-atmosphere)

The [Atmosphere.Color](/docs/en-us/reference/engine/classes/Atmosphere#Color)  property sets the hue of the atmosphere for subtle environmental moods and themes, and it can really enhance the haze within your game. You can set this to any color you want to suit your game, but it's recommended to set it to a color value that is close to the average of the objects in the environment.

To adjust the color of the atmosphere:

1.

In the Explorer  window, select Atmosphere .

2.

In the Properties  window, set Color  to 85, 78, 54 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Color-85-78-54.png)

## [Configure local lighting](#configure-local-lighting)[](#configure-local-lighting)

Local lighting is the luminescence from local [light sources](/docs/en-us/effects/light-sources)  in your game, such as [SpotLight](/docs/en-us/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/en-us/reference/engine/classes/SurfaceLight) , and [PointLight](/docs/en-us/reference/engine/classes/PointLight)  objects. The key local light source you can create for this game is the campfire's glow, and by adjusting a couple of its default properties, you can significantly alter how this local lighting interacts with the overall environment and complement your global lighting configuration.

### [Add a PointLight](#add-a-pointlight)[](#add-a-pointlight)

Unlike [SpotLight](/docs/en-us/reference/engine/classes/SpotLight)  or [SurfaceLight](/docs/en-us/reference/engine/classes/SurfaceLight)  objects that only project light from one direction, [PointLight](/docs/en-us/reference/engine/classes/PointLight)  objects allow you to project omnidirectional lighting. This means that when you add a [PointLight](/docs/en-us/reference/engine/classes/PointLight)  to your campfire mesh, it projects in all directions outward from its source, similar to a real-life campfire, and it illuminates all surrounding objects in shadows and allows players to see the roughness of their surfaces much clearer.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/No-PointLight.png) The scene without a local light source

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Yes-PointLight.jpg) The same scene with a local light source

To add a [PointLight](/docs/en-us/reference/engine/classes/PointLight)  to the campfire:

1.

In the Explorer  window, hover over FireLight  and click the ⊕  button. A contextual menu displays.

2.

From the menu, select PointLight . The [PointLight](/docs/en-us/reference/engine/classes/PointLight)  object displays as a child of the campfire mesh.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/New-PointLight-Values.png)

### [Increase the range of the PointLight](#increase-the-range-of-the-pointlight)[](#increase-the-range-of-the-pointlight)

The default properties of the [PointLight](/docs/en-us/reference/engine/classes/PointLight)  aren't enough to fully brighten the objects surrounding the campfire, so you need to increase the range that the light can reach. Because the fire is large and bright, the light needs to cast far enough to illuminate the nearby trees, rocks, and brush. This also helps to make the space feel warm and cozy, as though the heat of the fire is naturally expanding outward.

To increase the range of the [PointLight](/docs/en-us/reference/engine/classes/PointLight) :

1.

In the Explorer  window, select the campfire's PointLight .

2.

In the Properties  window, set Range  to 48 . The light's maximum lighting range expands.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Increasing-Range.png)

### [Enable shadows](#enable-shadows)[](#enable-shadows)

While the lighting's range is realistic to its size, it's unrealistic that the surrounding trees and rocks don't cast shadows from the campfire's light. Sometimes this is useful if you need to add in a couple of point lights to brighten dark spaces within your game, but when you're aiming to emulate the real world, you can enable local lighting's ability to cast shadows. It's important to note that additional shadows can impact your game's performance on low-end devices, so only enable shadows when they significantly add to the scene.

To enable shadows from the campfire's local lighting:

1.

In the Explorer  window, select the campfire's PointLight .

2.

In the Properties  window, enable Shadows .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Enabling-Shadows.png)

### [Adjust the lighting's brightness and color](#adjust-the-lightings-brightness-and-color)[](#adjust-the-lightings-brightness-and-color)

While the local lighting is already looking and feeling closer to realistic behavior, it's still weak in strength and too white for a warm glow. When you increase the campfire's brightness and add a warmer hue, it really brings life to the fire and adds to the coziness of the scene.

To enable shadows from the campfire's local lighting:

1.

In the Explorer  window, select the campfire's PointLight .

2.

In the Properties  window,

1.

Set Brightness  to 2 .

2.

Set Color  to 255, 179, 73 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Adjusting-Brightness-Color.png)

You now have a campfire scene that is complete and welcoming for players to relax. Using the skills in this tutorial, you can combine the realistic lighting style with the PBR materials available to create rich and immersive games. It only takes setting up the correct properties and making decisions about these features that suit your environment.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
