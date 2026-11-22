<!-- Source: https://create.roblox.com/docs/en-us/art/characters/creating/export-character -->

Export character model | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/creating/export-character.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Export character model

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/creating/export-character.md)

It's important to test your assets multiple times at every point of the asset creation process, whether it is within Blender or after importing into Studio. See [Test characters](/docs/en-us/avatar/character-bodies/test)  for more information.

Whether you are exporting your character for testing, or are performing a final export out of Blender, you must apply the appropriate export settings to ensure that Blender exports the proper character data.

To export your character:

1.

In the topbar, navigate to File  > Export  > FBX (.fbx) . The Blender file browser window displays.

2.

Set Path Mode  to Copy  and enable the Embed Textures  icon.

3.

In the Include  section, enable Custom Properties .

4.

Expand the Armature  section and disable Add Leaf Bones .

5.

Enable Bake Animation , expand the section, then:

1.

Disable NLA Strips , All Actions , and Force Start/End Keyframes .

2.

Set Simplify  to 0.0 .

6.

Click the Export FBX  button and save the .fbx  to the directory of your choice.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Export-Settings.png)

After exporting your .fbx file, see [Test character bodies](/docs/en-us/avatar/character-bodies/test)  for steps on importing your character model into a test place and verifying your avatar and related components.

After importing the [Model](/docs/en-us/reference/engine/classes/Model)  character to Studio, you can now perform the following with this asset:

-

[Upload the character](/docs/en-us/marketplace/publish-to-marketplace)  to the Marketplace.

-

Use the humanoid character on an existing game by applying a [HumanoidDescription](/docs/en-us/characters/appearance#manually-modify-appearance) to the [Model](/docs/en-us/reference/engine/classes/Model)  object.

-

Save the asset to your [Toolbox](/docs/en-us/projects/assets/toolbox)  to share or use within any of your games.

[Previous](/docs/en-us/art/characters/creating/export-textures)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
