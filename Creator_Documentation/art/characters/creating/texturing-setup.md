<!-- Source: https://create.roblox.com/docs/en-us/art/characters/creating/texturing-setup -->

Texturing setup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/creating/texturing-setup.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Texturing setup

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/creating/texturing-setup.md)

Texturing  is the process of customizing the color, tone, and shading of your model's surface. Custom meshes and models use a 2D image, known as a texture map, to project various surface appearance elements onto your 3D object.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Pre-Texturing.png)  Model after custom sculpting

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Texturing.png) Model after texturing

Each template comes with a color texture map, which you can alter and modify using Blender's texture editing tools. Since most Roblox avatars can take advantage of custom skin tones, it's important to understand how to [preview custom skin tones](/docs/en-us/art/characters/creating/blender-configurations#preview-skin-tones)  in Blender to verify how your final asset will look in a Roblox game.

For the purpose of demonstrating the basic texturing process, this tutorial goes over basic texture painting setup, applies a completely opaque texture over parts of the character eyes, and partially opaque details over the face. You can apply these same techniques to other parts of your character geometry.

When texturing parts of your character model's body, ensure that your character model includes a modesty layer over sensitive regions. For more information, see [Marketplace policy - Modesty layers](/docs/en-us/marketplace/marketplace-policy#modesty-layers) .

## [Texture settings](#texture-settings)[](#texture-settings)

If you're using a Blender downloadable template, it's important to keep in mind that Blender requires you to manually  save your textures in the Texture Paint tab's 2D view window. If you just save your .blend  project file, your textures do * not*  save with it. This can cause you to lose hours of work if you don't periodically save your progress as you go.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Blender-Save-Image.png)

Blender 5.2 and later versions offer a texture setting to override this behavior:

1.

In the topbar, navigate to Edit  > Preferences . The Preferences  window displays.

2.

In the vertical navigation, select the Save & Load  tab.

3.

In the Blend Files  section, set Save Modified Images  to Always Save .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Blender-Always-Save-Setting.png)

## [Set texture resolution](#set-texture-resolution)[](#set-texture-resolution)

Roblox Studio supports a texture resolution of 1024 x 1024  for albedo texture maps. When using applications like Blender or Maya to texture paint directly on a model, extremely fine details may not paint as expected due to the resolution and level of detail of the painting.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Texture-Resolution-A.png)  Texture painting at 1024 x 1024 resolution

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Texture-Resolution-B.png) Texture painting at 2048 x 2048 resolution

When adding fine details to your texture, increase the image resolution of your texture map temporarily to 2048 x 2048  or 4096 x 4096 . After completing your texturing, change the image resolution back to 1024 x 1024  to bake in the changes.

To change your texture image resolution:

1.

In the Layout  tab, select the Head_Geo .

2.

Switch to the Texture Paint  tab, then in the 2D view window, select Image  > Resize .

3.

Set the texture size:

-

Use 2048  or 4096  for a higher resolution when creating detailed texture work.

-

Use 1024  for the default Roblox-supported resolution.

[Next](/docs/en-us/art/characters/creating/texturing-eyes)[Previous](/docs/en-us/art/characters/creating/sculpting)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
