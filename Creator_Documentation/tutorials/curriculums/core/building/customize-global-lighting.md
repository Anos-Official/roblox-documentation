<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/core/building/customize-global-lighting -->

Customize global lighting | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/core/building/customize-global-lighting.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Customize global lighting

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/core/building/customize-global-lighting.md)

Global lighting  controls the overall look and atmosphere of your game. By adjusting a few properties on the [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service, you can change the color, shadows, time of day, and atmospheric effects of a scene.

In this section, you'll update the lighting to match the [Island Jump - Final](https://www.roblox.com/games/14238807008/Island-Jump-Completed-Sample)  sample.

Lighting is mostly configured through property values, making it a great fit for Assistant. After applying the prompt, spend some time in the viewport adjusting Ambient , ClockTime , and Density  until the scene looks the way you want. For an overview of every lighting object Studio offers, see [Lighting and effects](/docs/en-us/environment) .

## [Set lighting properties](#set-lighting-properties)[](#set-lighting-properties)

The [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service controls how light behaves in your game. The sample game adjusts properties such as ambient color, lighting technology, shadow settings, and sun position to create a cooler ocean palette, sharper shadows, and stronger directional lighting.

Build with Assistant Build it Yourself

Customize global lighting

```

On the Lighting service, set the following properties:

- Ambient: Color3.fromRGB(16, 16, 16)

- ColorShift_Top: Color3.fromRGB(196, 222, 255)

- OutdoorAmbient: Color3.fromRGB(134, 158, 190)

- ShadowSoftness: 0

- LightingStyle: Realistic

- ClockTime: 9

- GeographicLatitude: 78

```

After it runs, the world picks up a cooler blue-grey tone, shadows get hard edges, and the sun shifts to mid-morning over to the right of your sea stacks.

For an overview of the rest of the [Lighting](/docs/en-us/reference/engine/classes/Lighting)  properties, see [Global lighting](/docs/en-us/environment/lighting) .

## [Atmosphere properties](#atmosphere-properties)[](#atmosphere-properties)

The [Atmosphere](/docs/en-us/reference/engine/classes/Atmosphere)  object is a child of the [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service. It adds depth by simulating particles in the air and blending distant scenery into the sky. The two most important properties are Density , which controls the thickness of the atmosphere, and Offset , which controls where that blending begins.

Build with Assistant Build it Yourself

Thicken the atmosphere

```

On the Atmosphere object inside the Lighting service, set:

- Density: 0.375

- Offset: 0.17

```

For more information about Atmosphere, see [Atmospheric Effects](/docs/en-us/environment/atmosphere) .

Now that you've configured the game's lighting, the next section shows you how to replace the greybox layout with polished assets.

Pre-Customization Customized Visual Effects

![The sample Island Jump game's lighting visuals before the customization from this page.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Lighting-Pre-Customization.jpg)

[Next](/docs/en-us/tutorials/curriculums/core/building/apply-polished-assets)[Previous](/docs/en-us/tutorials/curriculums/core/building/create-basic-visual-effects)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
