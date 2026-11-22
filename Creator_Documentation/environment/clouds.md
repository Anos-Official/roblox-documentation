<!-- Source: https://create.roblox.com/docs/en-us/environment/clouds -->

Dynamic clouds | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment/clouds.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/en-us/environment)

# Dynamic clouds

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/clouds.md)

Roblox's dynamic clouds  are realistic clouds that drift slowly across the sky. You can adjust their appearance through the [Clouds](/docs/en-us/reference/engine/classes/Clouds)  object to create unique atmospheres such as stormy skies, stunning sunsets, and alien worlds. You can also customize their direction and speed through [global wind](/docs/en-us/environment/global-wind) .

## [Enable clouds](#enable-clouds)[](#enable-clouds)

You can manage dynamic clouds in a game through the [Clouds](/docs/en-us/reference/engine/classes/Clouds)  object. While you can place this object anywhere for organization or replication purposes, clouds only render if you parent the object under the [Terrain](/docs/en-us/reference/engine/classes/Terrain)  class.

To enable dynamic clouds:

1.

In the Explorer  window, hover over Terrain  and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert Clouds .

 ![Clouds object shown in Explorer window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Terrain-Clouds.png)

3.

Adjust the appearance of clouds through the new object's properties.

4.

Set the clouds in motion through [global wind](/docs/en-us/environment/global-wind) .

## [Cloud properties](#cloud-properties)[](#cloud-properties)

From the [Clouds](/docs/en-us/reference/engine/classes/Clouds)  object under [Terrain](/docs/en-us/reference/engine/classes/Terrain) , you can adjust the appearance of clouds through the Properties  window.

### [Cover](#cover)[](#cover)

The [Cover](/docs/en-us/reference/engine/classes/Clouds#Cover)  property controls how much the clouds span across the overall skyscape layer from a value of 0 (sparse cloud cover) to 1 (full cloud cover).

0.65 0.8

![Clouds with Cover value of 0.65](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/clouds/Cover-A.jpg)

### [Density](#density)[](#density)

The [Density](/docs/en-us/reference/engine/classes/Clouds#Density)  property controls the intensity of the particles that make up each cloud, mainly affecting their transparency. For example, lower values produce light, semi-translucent clouds, and higher values produce heavy, dark clouds with a stormy appearance.

0.1 0.3

![Clouds with Density value of 0.05](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/clouds/Density-A.jpg)

### [Color](#color)[](#color)

The [Color](/docs/en-us/reference/engine/classes/Clouds#Color)  property controls the material color of cloud particles. It's important to note that several [Lighting](/docs/en-us/reference/engine/classes/Lighting)  and [Atmosphere](/docs/en-us/reference/engine/classes/Atmosphere)  properties also influence cloud color, so if you want to simulate specific atmospheres, experiment with multiple properties until you have the effect you want.

[255, 255, 255] [75, 50, 255]

![Clouds with Color value of [255, 255, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/clouds/Color-A.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
