<!-- Source: https://create.roblox.com/docs/environment/skybox -->

Skyboxes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment/skybox.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/environment)

# Skyboxes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/skybox.md)

A skybox  is a cube made up of six individual images that create an immersive sky background in a game. When the images are designed to be perfectly aligned with each other, the skybox appears to be panoramic without the impression of being inside a cube. This makes games feel larger than they really are, and it adds depth to your atmosphere, such as simulating deep space or underwater environments.

Additionally, the [Sky](/docs/reference/engine/classes/Sky)  object includes celestial bodies such as a sun, moon, and stars which dynamically appear, rise, and set based on the [TimeOfDay](/docs/reference/engine/classes/Lighting#TimeOfDay)  or [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime) .

Finally, the [Sky](/docs/reference/engine/classes/Sky)  object can be used as a cubemap for reflections in [ViewportFrames](/docs/reference/engine/classes/ViewportFrame) . For details, see [viewport frames](/docs/ui/viewport-frames) .

## [Skybox construction](#skybox-construction)[](#skybox-construction)

If you've created your own skybox images, you must first [import](/docs/projects/assets/manager#asset-import)  them to Roblox before you can use them in a skybox. Each image must be seamless along all edges  of neighboring images when "folded" into a cube.

Image Faces Skybox "Folded"

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/skybox/Skybox-Unfolded.png)

To create a skybox:

1.

In the Explorer  window, insert a [Sky](/docs/reference/engine/classes/Sky)  object into the [Lighting](/docs/reference/engine/classes/Lighting)  service.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Lighting-Sky.png)

2.

Select the new [Sky](/docs/reference/engine/classes/Sky)  object, then in the Properties  window, assign a texture to each of the following sky properties:

-

SkyboxBk  — The back  square of the skybox.

-

SkyboxDn  — The down  square of the skybox.

-

SkyboxFt  — The front  square of the skybox.

-

SkyboxLf  — The left  square of the skybox.

-

SkyboxRt  — The right  square of the skybox.

-

SkyboxUp  — The up  square of the skybox.

 ![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/skybox/Skybox-Property-Faces.png)

## [Celestial bodies](#celestial-bodies)[](#celestial-bodies)

By default, the [Sky](/docs/reference/engine/classes/Sky)  object includes celestial bodies such as a sun, moon, and stars. These bodies dynamically appear, rise, and set based on the [TimeOfDay](/docs/reference/engine/classes/Lighting#TimeOfDay)  or [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime)  property values.

You can customize celestial bodies through the following properties:

-

[SunTextureId](/docs/reference/engine/classes/Sky#SunTextureId)  — Sets the texture of the sun.

-

[SunAngularSize](/docs/reference/engine/classes/Sky#SunAngularSize)  — Sets the relative size of the sun in degrees.

-

[MoonTextureId](/docs/reference/engine/classes/Sky#MoonTextureId)  — Sets the texture of the moon.

-

[MoonAngularSize](/docs/reference/engine/classes/Sky#MoonAngularSize)  — Sets the relative size of the moon in degrees.

-

[StarCount](/docs/reference/engine/classes/Sky#StarCount)  — Sets the amount of stars in the skybox.

To disable all celestial bodies, you can toggle off the [CelestialBodiesShown](/docs/reference/engine/classes/Sky#CelestialBodiesShown)  property. Alternatively, you can disable only the sun and/or moon (while keeping the stars) by setting [SunAngularSize](/docs/reference/engine/classes/Sky#SunAngularSize)  or [MoonAngularSize](/docs/reference/engine/classes/Sky#MoonAngularSize)  to 0 .

## [Orientation](#orientation)[](#orientation)

The [SkyboxOrientation](/docs/reference/engine/classes/Sky#SkyboxOrientation)  property changes the orientation of the skybox surfaces. The property takes a [Vector3](/docs/reference/engine/datatypes/Vector3)  of degree values in the typical XYZ  order, but rotation is applied  first around the Y  axis, then X , and then Z  to allow for predictable control over complex movements.

An easy way to script an orientation animation is to spin around the Y  axis (keeping the horizon level), then tilt this axis by setting X  and Z  to a fixed value. The following script, for example, animates the Y  axis for spinning while keeping a consistent 30° tilt on the X  axis.

```

local Lighting = game:GetService("Lighting")

local RunService = game:GetService("RunService")

local sky = Lighting:FindFirstChild("Sky")

local ROTATION_SPEED = 5  -- In degrees per second

RunService.Heartbeat:Connect(function(deltaTime)

	sky.SkyboxOrientation = Vector3.new(

		30,

		(sky.SkyboxOrientation.Y + ROTATION_SPEED * deltaTime) % 360,

		0

	)

end)

```

The modulo operation %  is optional but recommended. You can use values above 360  or below 0 , but using smaller numbers avoids issues when the animation runs for a very long time (due to limited precision).

Note that skybox orientation is a low-cost feature which works seamlessly across all platforms and visual quality levels. As a result, some intentional exceptions include:

-

If the sky is visible in indoor reflections such as a mirror surface through an open window, that specific reflected view will not be rotated. Achieving this would require expensive re‑rendering and convolving of cubemaps which would significantly impact performance and broad availability.

-

Only the skybox surfaces rotate; [celestial bodies](#celestial-bodies)  are not affected by this property.

-

If you utilize a [Sky](/docs/reference/engine/classes/Sky)  within a [ViewportFrame](/docs/reference/engine/classes/ViewportFrame) , it will reflect the global [SkyboxOrientation](/docs/reference/engine/classes/Sky#SkyboxOrientation)  values. You cannot adjust the angle per [ViewportFrame](/docs/reference/engine/classes/ViewportFrame) .

-

The [dynamic clouds](/docs/environment/clouds)  feature under [Terrain](/docs/reference/engine/classes/Terrain)  is not impacted.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
