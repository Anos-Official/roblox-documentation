<!-- Source: https://create.roblox.com/docs/en-us/effects -->

Effects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/effects.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Effects](/docs/en-us/effects)

# Effects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/effects/index.md)

You can create special effects by parenting special effect objects to other objects or attachments.

## [Light sources](#light-sources)[](#light-sources)

Light sources let you attach lighting effects to objects or attachments. There are three types of light sources:

-

A [PointLight](/docs/en-us/reference/engine/classes/PointLight)  emits light spherically from a single point. This object is ideal for non-directional lights like bulbs, torches, and fireballs.

-

A [SpotLight](/docs/en-us/reference/engine/classes/SpotLight)  emits light in the shape of a cone with a spherical base. This object is ideal for directional lights like street lamps, flashlights, and headlights.

-

A [SurfaceLight](/docs/en-us/reference/engine/classes/SurfaceLight)  emits light from the face of a BasePart. This object is ideal for lighting from TV or computer screens, billboards, and fluorescent panels.

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/PointLight-Range-8.jpg) Point lights

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SpotLight-Face-Bottom.jpg) Spotlights

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SurfaceLight-Angle-0.jpg) Surface lights

## [Particle emitters](#particle-emitters)[](#particle-emitters)

A [particle emitter](/docs/en-us/effects/particle-emitters)  is an object that emits customizable 2D images (particles) into the world, useful for simulating special effects like fire, smoke, and sparks.

## [Beams](#beams)[](#beams)

A [beam](/docs/en-us/effects/beams)  is an object that renders a texture between two [Attachment](/docs/en-us/reference/engine/classes/Attachment)  objects [Beam.Attachment0](/docs/en-us/reference/engine/classes/Beam#Attachment0)  and [Beam.Attachment1](/docs/en-us/reference/engine/classes/Beam#Attachment1) . By setting beam properties, you can:

-

Add a [texture](/docs/en-us/effects/beams#texture)  and [color gradient](/docs/en-us/effects/beams#color)  to create interesting visuals like waterfalls and force fields.

-

Modify a beam's [transparency](/docs/en-us/effects/beams#transparency)  so that it fades over time.

-

Warp its shape by changing the [width](/docs/en-us/effects/beams#width)  or [curve](/docs/en-us/effects/beams#curve)  of each attachment point.

## [Trails](#trails)[](#trails)

A [trail](/docs/en-us/effects/trails)  is an object that creates a trail between and behind two [Attachment](/docs/en-us/reference/engine/classes/Attachment)  objects as they move through space. Trails can help players visualize movement, such as a sword slashing through the air, projectiles flying to their target, or footprints walking away.

By setting trail properties, you can:

-

Add a [texture](/docs/en-us/effects/trails#texture)  to create interesting visuals.

-

Set a constant or gradient [color](/docs/en-us/effects/trails#color) .

-

Modify a trail's [lifetime](/docs/en-us/effects/trails#lifetime) .

## [Highlighting](#highlighting)[](#highlighting)

[Highlight](/docs/en-us/reference/engine/classes/Highlight)  is a visual effect which you can use to call attention to a specific object within a game, such as to provide visual feedback that the object is important and/or interactable. See [Highlighting Objects](/docs/en-us/effects/highlighting)  for details.

![A tree mesh against a grey background.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-1.jpg) Base object

![The same tree mesh with a white outline and a red highlight interior.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Adding-Highlight.jpg) White outline, 50% red interior

![The same tree mesh with a yellow outline and a black highlight interior.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Overview-Yellow-Outline.jpg) Yellow outline, black interior

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
