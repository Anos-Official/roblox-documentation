<!-- Source: https://create.roblox.com/docs/environment -->

Lighting and effects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/environment)

# Lighting and effects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/index.md)

The [Lighting](/docs/reference/engine/classes/Lighting)  container services let you control and customize a game's environment such as [lighting](#global-lighting) , [atmosphere](#atmospheric-effects) , and [clouds](#clouds-and-skies) . You can also apply [post-processing effects](#post-processing-effects)  to adjust how the game appears on the screen.

## [Global lighting](#global-lighting)[](#global-lighting)

The [Lighting](/docs/reference/engine/classes/Lighting)  service contains properties that you can adjust to update the global lighting in a game, such as the [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime)  and [Brightness](/docs/reference/engine/classes/Lighting#Brightness) .

ClockTime = 0 ClockTime = 6.3 Brightness = 0.5 Brightness = 3.75

![Lighting with ClockTime of 0 (TimeOfDay of 00:00:00)](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/TimeOfDay-0.jpg)

In addition to global lighting, you can create and attach [light sources](/docs/effects/light-sources)  to parts or attachments to simulate objects like lamps, torches, spotlights, or TV screens.

## [Atmospheric effects](#atmospheric-effects)[](#atmospheric-effects)

[Atmospheric effects](/docs/environment/atmosphere)  simulate realistic environments by scattering sunlight in unique ways. Using the [Atmosphere](/docs/reference/engine/classes/Atmosphere)  object in the [Lighting](/docs/reference/engine/classes/Lighting)  service, you can control air particle [density](/docs/environment/atmosphere#density) , simulate [haze](/docs/environment/atmosphere#haze)  or [glare](/docs/environment/atmosphere#glare) , set an atmosphere's [color](/docs/environment/atmosphere#color) , and more.

![Atmospheric effects used to render a brilliant sunset scene](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Showcase.jpg) Atmospheric effects used to render a brilliant sunset scene

## [Clouds and skies](#clouds-and-skies)[](#clouds-and-skies)

By default, the [Sky](/docs/reference/engine/classes/Sky)  object forms a [skybox](/docs/environment/skybox)  with celestial bodies such as a sun, moon, and stars. In addition, you can adjust the cloud cover, density, and color properties of the [Clouds](/docs/reference/engine/classes/Clouds)  object to render realistic, [dynamic clouds](/docs/environment/clouds)  that drift slowly across the sky through [global wind](/docs/environment/global-wind) .

Wind blowing dynamic clouds across the sky

## [Post-processing effects](#post-processing-effects)[](#post-processing-effects)

Post-processing effects  are customizable filters that allow you to quickly enrich the visuals of your game. Using the post-processing effect objects in the [Lighting](/docs/reference/engine/classes/Lighting)  service or [Camera](/docs/reference/engine/classes/Camera) , you can:

-

Simulate a camera viewing a bright light and exaggerate its glow.

-

Apply a Gaussian blur to the entirety of your game or add a blur to parts of your game that aren't in focus.

-

Enhance an environment's appearance to create a specific mood through hue.

-

Render a halo of light that moves with the sun.

![Landscape with depth-of-field effect applied, simulating distance blur](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/DepthOfFieldEffect-With.jpg) Landscape with depth-of-field effect applied, simulating distance blur

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
