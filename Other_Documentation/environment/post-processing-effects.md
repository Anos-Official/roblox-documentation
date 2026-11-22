<!-- Source: https://create.roblox.com/docs/environment/post-processing-effects -->

Post-processing effects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment/post-processing-effects.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/environment)

# Post-processing effects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/post-processing-effects.md)

Post-processing effects  are customizable filters that allow you to quickly enrich the visuals of your game. Using the post-processing effect objects in the [Lighting](/docs/reference/engine/classes/Lighting)  service or [Camera](/docs/reference/engine/classes/Camera) , you can:

-

Simulate a camera viewing a bright light and exaggerate its glow ([bloom](#bloom) ).

-

Apply a Gaussian [blur](#blur)  to the entirety of your game, or add a blur to parts of your game that aren't in focus ([depth‑of‑field](#depth-of-field) ).

-

Enhance an environment's appearance to create a specific mood through hue ([color correction](#color-correction) ).

-

Render a halo of light that moves with the sun ([sun rays](#sun-rays) ).

![Landscape with depth-of-field effect applied, simulating distance blur](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/DepthOfFieldEffect-With.jpg) Landscape with depth-of-field effect applied, simulating distance blur

## [Add post-processing effects](#add-post-processing-effects)[](#add-post-processing-effects)

When you add post-processing effects to the [Lighting](/docs/reference/engine/classes/Lighting)  service, they display to all players  who enter the game. This is useful for effects that affect the global environment, such as [sun rays](#sun-rays) .

When you add post-processing effects to the [Camera](/docs/reference/engine/classes/Camera)  object, they only display to a specific player . This is useful for effects that should only pertain to that player based on their actions, such as blurring the 3D world view when they have a UI menu open.

To add post-processing effects to either the [Lighting](/docs/reference/engine/classes/Lighting)  service or [Camera](/docs/reference/engine/classes/Camera) :

1.

In the Explorer  window, hover over the [Lighting](/docs/reference/engine/classes/Lighting)  service or [Camera](/docs/reference/engine/classes/Camera) , then click the ⊕ button. A contextual menu displays.

2.

From the menu, insert one or more of the following post-processing effects:

-

BloomEffect

-

BlurEffect

-

ColorCorrectionEffect

-

DepthOfFieldEffect

-

SunRaysEffect

-

ColorGradingEffect

3.

Depending on your Studio settings, some effects may not appear. To increase your rendering quality level:

1.

Open [Studio Settings](/docs/studio/setup#customization) .

2.

In the left-side navigation, select Rendering , then the Editor Quality Level  dropdown menu.

3.

Set it to the highest level.

## [Bloom](#bloom)[](#bloom)

The [BloomEffect](/docs/reference/engine/classes/BloomEffect)  effect exaggerates lights within your game by simulating a camera viewing a bright light. When this effect has a high value, parts with light colors glow.

Default Bloom Effect

![Game without any effects applied](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/BloomEffect-Without.jpg)

## [Blur](#blur)[](#blur)

The [BlurEffect](/docs/reference/engine/classes/BlurEffect)  effect applies a Gaussian blur to the entirety of the 3D world view. You can use this effect to blur the background when a player has a menu open, allowing them to focus on the most important details.

Default Blur Effect

![Game without any effects applied](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/BlurEffect-Without.jpg)

## [Color correction](#color-correction)[](#color-correction)

The [ColorCorrectionEffect](/docs/reference/engine/classes/ColorCorrectionEffect)  effect adjusts color properties to enhance an environment's appearance. You can also use this effect to provide player feedback, such as tinting the screen red when their character's health is low.

The following list describes the primary [ColorCorrectionEffect](/docs/reference/engine/classes/ColorCorrectionEffect)  properties:

-

[Brightness](/docs/reference/engine/classes/ColorCorrectionEffect#Brightness)  — Sets the brightness of pixels.

-

[Contrast](/docs/reference/engine/classes/ColorCorrectionEffect#Contrast)  — Sets the change in separation between dark and light colors.

-

[Saturation](/docs/reference/engine/classes/ColorCorrectionEffect#Saturation)  — Sets the intensity of colors.

-

[TintColor](/docs/reference/engine/classes/ColorCorrectionEffect#TintColor)  — Determines how much the RGB channels of pixels scale.

Default Color Correction Effect

![Game without any effects applied](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/ColorCorrectionEffect-Without.jpg)

## [Depth-of-field](#depth-of-field)[](#depth-of-field)

The [DepthOfFieldEffect](/docs/reference/engine/classes/DepthOfFieldEffect)  effect blurs parts of your game that aren't in focus. You can use this effect to blur distant objects or to focus a player on specific parts of your game, such as an item in a shop.

Default Depth-of-Field Effect

![Game without any effects applied](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/DepthOfFieldEffect-Without.jpg)  ![](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/DepthOfFieldEffect/Depth-Of-Field-Diagram.svg)

## [Sun rays](#sun-rays)[](#sun-rays)

The [SunRaysEffect](/docs/reference/engine/classes/SunRaysEffect)  effect creates a halo of light with rays around the sun that move based on the [ClockTime](/docs/reference/engine/classes/Lighting#ClockTime)  or [TimeOfDay](/docs/reference/engine/classes/Lighting#TimeOfDay)  property. Objects between the player's camera and the sun shape this effect, allowing for realistic visuals of light and shadow.

## [Color grading](#color-grading)[](#color-grading)

The [ColorGradingEffect](/docs/reference/engine/classes/ColorGradingEffect)  effect modifies how color values calculated by the renderer should be converted to the screen's color range, impacting the mood and appearance of your place.

This effect's primary property is [TonemapperPreset](/docs/reference/engine/classes/ColorGradingEffect#TonemapperPreset) . The following values are available:

-

[Enum.TonemapperPreset.Default](/docs/reference/engine/enums/TonemapperPreset#Default)  — Sets the tone mapper to use the post‑2019 Roblox appearance which provides vivid colors and high contrasts.

-

[Enum.TonemapperPreset.Retro](/docs/reference/engine/enums/TonemapperPreset#Retro)  — Sets the tone mapper to imitate the pre‑2019 Roblox appearance. Colors look less saturated and there's less contrast between them.

If you wish to recreate a full pre‑2019 Roblox look for your game, experiment with [Enum.TonemapperPreset.Retro](/docs/reference/engine/enums/TonemapperPreset#Retro)  and set the brightness of all lights to a maximum of 1.0 .

Default Retro

![Game without any effects applied](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/ColorGrading-Default.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
