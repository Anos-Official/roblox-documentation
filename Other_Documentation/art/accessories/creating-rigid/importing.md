<!-- Source: https://create.roblox.com/docs/art/accessories/creating-rigid/importing -->

Use Studio's Importer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/accessories/creating-rigid/importing.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Use Studio's Importer

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/accessories/creating-rigid/importing.md)

Studio's Importer provides a quick and easy way to import third-party 3D .fbx  or .gltf  assets into your projects. The importer provides object previews and error-checking to ensure that your asset meets Studio's general 3D requirements.

To import your asset ([downloadable reference](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Chest-Texturing-Complete.fbx) ):

1.

In the Home  tab, click the Import  button to open the Importer. A file browser opens.

2.

Select your asset's .fbx  file. The Importer loads a preview of the rigid accessory.

3.

Select Import . The asset populates in your workspace as a [Model](/docs/reference/engine/classes/Model)  with the appropriate textures applied as a [MeshPart.TextureID](/docs/reference/engine/classes/MeshPart#TextureID) .

Textures didn't load correctly?

If your textures didn't load correctly, you can import them manually using the [Asset Manager](/docs/projects/assets/manager) :

1.

In the Asset Manager , click the Import  button. If you are unable to access the Asset Manager, save and publish your game first.

2.

Upload your image file.

3.

After moderation clears your image, select the [MeshPart](/docs/reference/engine/classes/MeshPart)  parented within your imported [Model](/docs/reference/engine/classes/Model) .

4.

In the TextureID  property, select the value field and add the asset ID of the texture image.

After successful import, your model object populates in your project as a [Model](/docs/reference/engine/classes/Model)  with the appropriate textures applied. See [Importer](/docs/studio/importer)  for additional information on import settings and troubleshooting.

[Next](/docs/art/accessories/creating-rigid/converting)[Previous](/docs/art/accessories/creating-rigid/exporting)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
