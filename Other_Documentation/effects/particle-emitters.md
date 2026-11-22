<!-- Source: https://create.roblox.com/docs/effects/particle-emitters -->

Particle emitters | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/effects/particle-emitters.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Effects](/docs/effects)

# Particle emitters

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/effects/particle-emitters.md)

[ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter)  is an object that emits customizable 2D images (particles) into the world, useful for simulating special effects like fire, smoke, and sparks.

You can parent a [ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter)  to an [Attachment](/docs/reference/engine/classes/Attachment)  or an object of the [BasePart](/docs/reference/engine/classes/BasePart)  class. When parented to a [BasePart](/docs/reference/engine/classes/BasePart) , particles spawn randomly within the part's bounding box or [shape](#shape) ; when parented to an [Attachment](/docs/reference/engine/classes/Attachment) , particles spawn from the attachment's position.

Additionally, the [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection)  property determines the face ([Enum.NormalId](/docs/reference/engine/enums/NormalId) ) of emission when the emitter is parented to a [BasePart](/docs/reference/engine/classes/BasePart) . When you change this property, you consequently change the particle emission direction as well.

When you rotate an emitter's parent [BasePart](/docs/reference/engine/classes/BasePart) , the orientation of its face also changes, altering the direction of particle emission. Alternatively, if you add an emitter to an [Attachment](/docs/reference/engine/classes/Attachment) , you can rotate the attachment itself instead of using [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection) .

## [Customize particles](#customize-particles)[](#customize-particles)

By experimenting with the following properties, you can customize a particle's visual appearance to make unique gameplay elements like bursting volcanos, magical dust, and dust motes.

The visual quality of your particles can change depending on the graphic settings on the player's device. To review your particles across quality levels, it's recommended to open [Studio Settings](/docs/studio/setup#customization) , search for Editor Quality Level , and set it to the both the lowest and highest level after you finish customizing your particles.

### [Texture](#texture)[](#texture)

The [Texture](/docs/reference/engine/classes/ParticleEmitter#Texture)  property renders the image that each particle displays. By default, particle emitters have particles with a white sparkle texture, but you can change it to any texture to achieve interesting effects.

Three similar particle emitters with different [Texture](/docs/reference/engine/classes/ParticleEmitter#Texture)  assets

If you're creating an image to use as a particle texture, it's best to use .png  format with a transparent background. If your texture is grayscale with no alpha channel, try setting the particle emitter's [LightEmission](/docs/reference/engine/classes/ParticleEmitter#LightEmission)  property to 1  to hide the darker regions.

For steps on how to import an image for use as a particle texture, see [here](/docs/projects/assets/manager#asset-import) .

### [Color](#color)[](#color)

The [Color](/docs/reference/engine/classes/ParticleEmitter#Color)  property tints each particle's texture to either a specific hue, or to a color gradient across its [lifetime](#lifetime) .

Scripting Studio

In a script, set a [ColorSequence](/docs/reference/engine/datatypes/ColorSequence)  for the emitter's [Color](/docs/reference/engine/classes/ParticleEmitter#Color)  property:

```

local emitter = Instance.new("ParticleEmitter")

-- Constant color

emitter.Color = ColorSequence.new(Color3.fromRGB(255, 0, 40))

-- Gradient sequence

emitter.Color = ColorSequence.new{

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),

	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 125, 0)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 200, 0))

}

```

### [Size](#size)[](#size)

The [Size](/docs/reference/engine/classes/ParticleEmitter#Size)  property sets the size of each particle to a consistent size, or to a numerical sequence across its [lifetime](#lifetime) .

Scripting Studio

In a script, set a [NumberSequence](/docs/reference/engine/datatypes/NumberSequence)  for the emitter's [Size](/docs/reference/engine/classes/ParticleEmitter#Size)  property:

```

local emitter = Instance.new("ParticleEmitter")

-- Constant size

emitter.Size = NumberSequence.new(3)

-- Numerical sequence

emitter.Size = NumberSequence.new{

	NumberSequenceKeypoint.new(0, 1),

	NumberSequenceKeypoint.new(0.2, 4),

	NumberSequenceKeypoint.new(1, 0)

}

```

Particle size can impact performance due to fill-rate. The more pixels particles occupy on a player's screen, the more costly it is on the GPU.

### [Transparency](#transparency)[](#transparency)

The [Transparency](/docs/reference/engine/classes/ParticleEmitter#Transparency)  property sets the opacity of each particle as a consistent value, or as an opacity sequence across its [lifetime](#lifetime) . Opacity can range from 0  (totally opaque) to 1  (fully clear). For details on how to set particles to either a specific opacity or to a number sequence, follow the process in customizing [Size](#size)  but use the emitter's [Transparency](/docs/reference/engine/classes/ParticleEmitter#Transparency)  property field instead.

The [Transparency](/docs/reference/engine/classes/ParticleEmitter#Transparency)  property is one of the most vital properties of a particle emitter. Fading particles near the start and/or end of their lifetime avoids a popping in/out effect and provides a more realistic effect.

Static transparency vs. fading in/out

### [Lifetime](#lifetime)[](#lifetime)

The [Lifetime](/docs/reference/engine/classes/ParticleEmitter#Lifetime)  property sets the lifetime of a particle in seconds. You can set this property either as a consistent value, or provide a [Min](/docs/reference/engine/datatypes/NumberRange#Min)  and [Max](/docs/reference/engine/datatypes/NumberRange#Max)  range from which a random lifetime will be chosen for each particle.

Particles have a maximum lifetime of 20 seconds. [Lifetime](/docs/reference/engine/classes/ParticleEmitter#Lifetime)  values higher than this will be internally capped at 20 .

### [Speed](#speed)[](#speed)

The [Speed](/docs/reference/engine/classes/ParticleEmitter#Speed)  property determines a random range of velocities (minimum to maximum) at which new particles will emit, measured in studs per second. Each particle's velocity is chosen upon emission and it applies in the [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection) . Negative values cause particles to travel in reverse.

Note that changing [Speed](/docs/reference/engine/classes/ParticleEmitter#Speed)  does not affect active particles and they retain whatever speed they already have. However, [Acceleration](/docs/reference/engine/classes/ParticleEmitter#Acceleration) , [Drag](/docs/reference/engine/classes/ParticleEmitter#Drag) , and [VelocityInheritance](/docs/reference/engine/classes/ParticleEmitter#VelocityInheritance)  can be used to affect the speed of active particles over their lifetime.

### [Rate](#rate)[](#rate)

The [Rate](/docs/reference/engine/classes/ParticleEmitter#Rate)  property sets the number of particles that emit per second. A single particle emitter can create up to 400 particles per second (100 per second on mobile). For best performance, keep the particle rate as low as possible and experiment with [size](#size)  and [other properties](#other-properties)  to achieve the desired visual effect.

Particle count can impact performance due to overdraw, especially when particles are overlapping. The more layers of transparent effects on screen, the more costly it is on the GPU.

### [Orientation](#orientation)[](#orientation)

The [Orientation](/docs/reference/engine/classes/ParticleEmitter#Orientation)  property determines which orientation mode to use for an emitter's particle geometry.

| Orientation | | Particle behavior |
| --- | --- |
| [FacingCamera](/docs/reference/engine/enums/ParticleOrientation) | | Standard camera-facing billboard quad; default behavior. |
| [FacingCameraWorldUp](/docs/reference/engine/enums/ParticleOrientation) | | Facing the camera, but rotating only on the vertical upward world Y  axis. |
| [VelocityParallel](/docs/reference/engine/enums/ParticleOrientation) | | Aligned parallel to their direction of movement. |
| [VelocityPerpendicular](/docs/reference/engine/enums/ParticleOrientation) | | Aligned perpendicular to their direction movement. |

Expected outcome of particle orientation

### [LightEmission](#lightemission)[](#lightemission)

The [LightEmission](/docs/reference/engine/classes/ParticleEmitter#LightEmission)  property determines the blending of particle [Texture](/docs/reference/engine/classes/ParticleEmitter#Texture)  colors with the colors behind them. A value of 0  uses normal blending mode while a value of 1  uses additive blending. Higher values can make particles glow even in environments with low lighting.

### [SpreadAngle](#spreadangle)[](#spreadangle)

The [SpreadAngle](/docs/reference/engine/classes/ParticleEmitter#SpreadAngle)  property has an X  and a Y  value which determine the range of angles from which a particle can emit. The range is calculated from both sides around the axes; for example, a value of (45, 0)  emits particles in a range of 0° to 45° away from the [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection)  across the X  axis.

### [WindAffectsDrag](#windaffectsdrag)[](#windaffectsdrag)

If you've enabled [global wind](/docs/environment/global-wind)  in a game, particles will follow the global wind vector as long as the emitter's [WindAffectsDrag](/docs/reference/engine/classes/ParticleEmitter#WindAffectsDrag)  property is enabled and its [Drag](/docs/reference/engine/classes/ParticleEmitter#Drag)  property is greater than 0 .

### [Shape](#shape)[](#shape)

The [Shape](/docs/reference/engine/classes/ParticleEmitter#Shape)  property sets the shape of the particle emitter to either a [Box](/docs/reference/engine/enums/ParticleEmitterShape) , [Sphere](/docs/reference/engine/enums/ParticleEmitterShape) , [Cylinder](/docs/reference/engine/enums/ParticleEmitterShape) , or [Disc](/docs/reference/engine/enums/ParticleEmitterShape) .

![Emitter of Box shape](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Box.jpg)[Box](/docs/reference/engine/enums/ParticleEmitterShape)

![Emitter of Sphere shape](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Sphere.jpg)[Sphere](/docs/reference/engine/enums/ParticleEmitterShape)

![Emitter of Cylinder shape](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Cylinder.jpg)[Cylinder](/docs/reference/engine/enums/ParticleEmitterShape)

![Emitter of Disc shape](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Disc.jpg)[Disc](/docs/reference/engine/enums/ParticleEmitterShape)

After you select a shape for your particle emitter, you can experiment with the [ShapeStyle](#shapestyle) , [ShapeInOut](#shapeinout) , and [ShapePartial](#shapepartial)  properties to further customize particle emission.

If you parent a particle emitter to an [Attachment](/docs/reference/engine/classes/Attachment) , the [Sphere](/docs/reference/engine/enums/ParticleEmitterShape)  and [Cylinder](/docs/reference/engine/enums/ParticleEmitterShape)  shapes will not display correctly. These shapes should only be used if the emitter is parented to a [BasePart](/docs/reference/engine/classes/BasePart) .

#### [ShapeStyle](#shapestyle)[](#shapestyle)

The [ShapeStyle](/docs/reference/engine/classes/ParticleEmitter#ShapeStyle)  property sets the emission type to either:

-

[Volume](/docs/reference/engine/enums/ParticleEmitterShapeStyle)  — Particles emit anywhere within the shape.

-

[Surface](/docs/reference/engine/enums/ParticleEmitterShapeStyle)  — Particles only emit from the outside of the shape.

![Emitter of Cylinder shape with Volume shape style](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-Volume.jpg)[Cylinder](/docs/reference/engine/enums/ParticleEmitterShape)  + [Volume](/docs/reference/engine/enums/ParticleEmitterShapeStyle)

![Emitter of Cylinder shape with Surface shape style](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-Surface.jpg)[Cylinder](/docs/reference/engine/enums/ParticleEmitterShape)  + [Surface](/docs/reference/engine/enums/ParticleEmitterShapeStyle)

#### [ShapeInOut](#shapeinout)[](#shapeinout)

The [ShapeInOut](/docs/reference/engine/classes/ParticleEmitter#ShapeInOut)  property sets the emission as follows:

-

[Inward](/docs/reference/engine/enums/ParticleEmitterShapeInOut)  — Particles emit toward the shape.

-

[Outward](/docs/reference/engine/enums/ParticleEmitterShapeInOut)  — Particles emit away from the shape.

-

[InAndOut](/docs/reference/engine/enums/ParticleEmitterShapeInOut)  — Particles randomly behave as both [Inward](/docs/reference/engine/enums/ParticleEmitterShapeInOut)  and [Outward](/docs/reference/engine/enums/ParticleEmitterShapeInOut) .

#### [ShapePartial](#shapepartial)[](#shapepartial)

The [ShapePartial](/docs/reference/engine/classes/ParticleEmitter#ShapePartial)  property is a factor you can use to further modify [Cylinder](/docs/reference/engine/enums/ParticleEmitterShape) , [Disc](/docs/reference/engine/enums/ParticleEmitterShape) , and [Sphere](/docs/reference/engine/enums/ParticleEmitterShape)  shapes.

Cylinder Disc Sphere

For cylinders, [ShapePartial](/docs/reference/engine/classes/ParticleEmitter#ShapePartial)  multiplies the radius of the cylinder on the side of its [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection) .

![Emitter of Cylinder shape with ShapePartial value of 0.5](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-ShapePartial-0.5.jpg)[ShapePartial](/docs/reference/engine/classes/ParticleEmitter#ShapePartial)  = 0.5

![Emitter of Cylinder shape with ShapePartial value of 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-ShapePartial-0.jpg)[ShapePartial](/docs/reference/engine/classes/ParticleEmitter#ShapePartial)  = 0

### [Squash](#squash)[](#squash)

The [Squash](/docs/reference/engine/classes/ParticleEmitter#Squash)  property allows for non-uniform scaling of particles, curve-controlled over their lifetime. Values greater than 0  cause particles to both shrink horizontally and grow vertically, while values less than 0  cause particles to both grow horizontally and shrink vertically. For details on how to set the squash amount to either a constant or to a [NumberSequence](/docs/reference/engine/datatypes/NumberSequence) , follow the process in customizing [Size](#size)  but use the emitter's [Squash](/docs/reference/engine/classes/ParticleEmitter#Squash)  property field instead.

Squash is especially useful for rain. Stretching a particle makes its texture much less recognizable, so even the default sparkle texture can pass as a falling raindrop. For details, see [simulate rain](#simulate-rain) .

### [Flipbooks](#flipbooks)[](#flipbooks)

Particle flipbook textures let you animate a particle's texture over its lifetime.

The flipbook texture can have a frame layout of 2×2, 4×4, 8×8, or custom. For example, the following 1024×1024 image has an 8×8 layout, so it's suitable for a 64‑frame animation.

 ![Sample texture for particle flipbooks](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/8x8-Explosion.png)

When you create a flipbook texture, include spacing between each of the particle frames. In some cases, mip filtering might require even more spacing. The previous image has transparent spacing around each frame for the flipbook texture.

Features with custom textures such as flipbooks cost memory to render. If you use many flipbooks with other features that use high memory, then clients automatically deactivate flipbooks when they are low on memory, which is likely for older mobile phones. To reduce the memory usage of flipbooks, use fewer unique animated particle effects or choose a texture of smaller resolution when possible. Reusing textures costs less memory than using unique textures.

Once you've specified a valid flipbook [texture](#texture)  for the emitter's [Texture](/docs/reference/engine/classes/ParticleEmitter#Texture)  property, the [FlipbookLayout](/docs/reference/engine/classes/ParticleEmitter#FlipbookLayout)  property determines the layout of the texture. It can be any value of the [Enum.ParticleFlipbookLayout](/docs/reference/engine/enums/ParticleFlipbookLayout)  enum:

-

[None](/docs/reference/engine/enums/ParticleFlipbookLayout)  — Disable flipbook features and use the texture as a single static texture over the particle's lifetime.

-

[Grid2x2](/docs/reference/engine/enums/ParticleFlipbookLayout)  — 2×2 frames for a 4-frame animation.

-

[Grid4x4](/docs/reference/engine/enums/ParticleFlipbookLayout)  — 4×4 frames for a 16-frame animation.

-

[Grid8x8](/docs/reference/engine/enums/ParticleFlipbookLayout)  — 8×8 frames for a 64-frame animation.

-

[Custom](/docs/reference/engine/enums/ParticleFlipbookLayout)  — A custom grid size defined by [FlipbookSizeX](/docs/reference/engine/classes/ParticleEmitter#FlipbookSizeX)  and [FlipbookSizeY](/docs/reference/engine/classes/ParticleEmitter#FlipbookSizeY) .

To further customize the flipbook behavior, you can adjust the following properties:

FlipbookFramerate FlipbookMode FlipbookStartRandom

The [FlipbookFramerate](/docs/reference/engine/classes/ParticleEmitter#FlipbookFramerate)  property determines how fast the flipbook texture animates in frames per second. Like [Lifetime](/docs/reference/engine/classes/ParticleEmitter#Lifetime) , you can set a minimum and maximum range to randomize the framerate of the flip book, with a maximum of 30 frames per second.

### [Other properties](#other-properties)[](#other-properties)

To further customize particles, consider the following emitter properties, and click through to the [ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter)  reference page for more details.

Appearance Emission Motion

The following appearance properties are in addition to [color](#color) , [light emission](#lightemission) , [orientation](#orientation) , [size](#size) , [texture](#texture) , [transparency](#transparency) , [squash](#squash) , and [flipbooks](#flipbooks) .

| Property | | Description |
| [LightInfluence](/docs/reference/engine/classes/ParticleEmitter#LightInfluence) | | Determines how much environmental light affects the color of individual particles. |
| [Brightness](/docs/reference/engine/classes/ParticleEmitter#Brightness) | | Scales the light emitted from the emitter when [LightInfluence](/docs/reference/engine/classes/ParticleEmitter#LightInfluence)  is 0 . |
| [ZOffset](/docs/reference/engine/classes/ParticleEmitter#ZOffset)   | | Determines the forward-backward render position of particles, in studs, without changing their size on the screen. This allows for multiple emitters to be layered, or to render particles in front of or behind the parent object. |

## [Simulate rain](#simulate-rain)[](#simulate-rain)

Simulating every raindrop isn't practical, but particle emitters can create a convincing illusion of rain in a 3D world:

1.

Insert a [Part](/docs/reference/engine/classes/Part)  above the area where you want rain to fall. Anchor it, set its [Transparency](/docs/reference/engine/classes/BasePart#Transparency)  to 1 , and disable [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide) .

2.

Insert a [ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter)  into the part and set its [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection)  to [Bottom](/docs/reference/engine/enums/NormalId#Bottom) . A single emitter can create a limited number of particles per second (see [Rate](#rate) ), so heavier rain or a larger area requires many parts with emitters arranged in a grid over the desired area.

3.

Set [Squash](/docs/reference/engine/classes/ParticleEmitter#Squash)  to a positive value, such as 3 , to stretch each particle into a streak. Higher values make particles thinner, so you might need to increase [size](#size)  as well.

If you set [Orientation](/docs/reference/engine/classes/ParticleEmitter#Orientation)  to [VelocityParallel](/docs/reference/engine/enums/ParticleOrientation#VelocityParallel)  so that streaks align with their direction of travel, use a negative [Squash](/docs/reference/engine/classes/ParticleEmitter#Squash)  value instead.

4.

Darken [Color](/docs/reference/engine/classes/ParticleEmitter#Color) , increase [LightInfluence](/docs/reference/engine/classes/ParticleEmitter#LightInfluence)  so that the rain reacts to the lighting around it, increase [Speed](/docs/reference/engine/classes/ParticleEmitter#Speed) , and decrease [Lifetime](/docs/reference/engine/classes/ParticleEmitter#Lifetime)  so that particles disappear near the ground.

5.

To angle the rain, set a small [Rotation](/docs/reference/engine/classes/ParticleEmitter#Rotation)  or enable [WindAffectsDrag](/docs/reference/engine/classes/ParticleEmitter#WindAffectsDrag)  so that particles follow [global wind](/docs/environment/global-wind) . [Drag](/docs/reference/engine/classes/ParticleEmitter#Drag)  slows the fall in addition to applying the wind, so you might need to increase the downward [Acceleration](/docs/reference/engine/classes/ParticleEmitter#Acceleration)  to keep the rain falling quickly.

To show rain landing, place transparent parts on the ground with emitters whose [EmissionDirection](/docs/reference/engine/classes/ParticleEmitter#EmissionDirection)  is [Top](/docs/reference/engine/enums/NormalId#Top) . Splash particles aren't stretched like falling rain, so they usually need a custom [texture](#texture)  and a [transparency](#transparency)  sequence that makes each splash appear to dissipate. Splashes only look right on surfaces where you've placed them carefully. If you can't place them by hand, low-lying mist is much more forgiving.

### [Manage particle limits](#manage-particle-limits)[](#manage-particle-limits)

Rain that covers a large area reaches particle limits quickly, and mobile devices have much lower limits than desktops. If particles flicker in the distance, reduce how many are on screen at once:

-

Place the emitter parts lower in the air and shorten [Lifetime](/docs/reference/engine/classes/ParticleEmitter#Lifetime)  to match.

-

Decrease [Rate](/docs/reference/engine/classes/ParticleEmitter#Rate)  to turn a downpour into a lighter shower.

-

Cover a smaller area with fewer emitter parts.

### [Rain examples](#rain-examples)[](#rain-examples)

-

For a hand-built example, see [The Mystery of Duvall Drive](/docs/resources/the-mystery-of-duvall-drive) . It uses emitters for [rain, mist, splashes, and water dripping from awnings](/docs/resources/the-mystery-of-duvall-drive/develop-a-moving-world#make-storm-debris) .

-

For a scripted example, see the [weather-island](https://github.com/Roblox/resources/tree/main/experiences/weather-island)  project. It schedules storms, transitions [clouds](/docs/environment/clouds)  and wind, spawns rain and mist emitters, and performs roof detection.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
