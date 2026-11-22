<!-- Source: https://create.roblox.com/docs/avatar/makeup/specifications -->

Makeup specifications | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/makeup/specifications.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Makeup

# Makeup specifications

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/makeup/specifications.md)

Makeup requires a specific set of components and configuration standards to ensure it displays properly on avatar faces of all shapes and sizes. Before you start the export process, verify that your makeup meets the following specifications and guidelines for proper Studio compatibility.

When you're ready to export your makeup, reference all [export setting requirements](/docs/avatar/makeup/reassign-textures)  for Blender and Maya.

For other types of 3D models:

-

[General mesh](/docs/art/modeling/specifications)  specifications.

-

[Rigid accessory](/docs/avatar/rigid-accessories/specifications)  specifications.

-

[Layered accessory](/docs/avatar/layered-accessories/specifications)  specifications.

## [General](#general)[](#general)

If you are following the best practice [creation process](/docs/avatar/makeup#creation-process) , ensure that your template file submission includes the following objects that are correctly configured and named in their respective third-party modeling software:

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Blender-Datamodel.png)

-

A head mesh object  and associated cage mesh object .

-

These two objects must include the prefix "TransferTarget_" in their name.

-

TransferTexture mesh objects  for each region: Eyes , Face , Lips .

-

These three objects must follow the following naming conventions.

-

TransferTexture_Eyes_01

-

TransferTexture_Lips_01

-

TransferTexture_Face_01

-

Any for multiple regions, increment the affix number: TransferTexture_Face_02

-

Optional [eyebrows and eyelashes](#eyebrows-and-eyelashes) .

The [provided Roblox makeup template head](https://github.com/Roblox/avatar/tree/main/Makeup)  should already be properly configured with the correct objects and naming conventions. To prevent issues with import, avoid renaming or deleting the data model of the template head when creating your own makeup.

## [Decals and textures](#decals-and-textures)[](#decals-and-textures)

All accessory textures must meet Roblox's [texture specifications](/docs/art/modeling/texture-specifications) , but makeup textures include two additional considerations:

-

There is a 4K texture limit for [in-game](/docs/avatar/in-experience-creation)  makeup creation.

-

There is a 1K texture limit for makeup that you upload to the [Marketplace](https://www.roblox.com/catalog) .

For additional information on PBR textures, see [PBR textures](/docs/art/modeling/surface-appearance) .

## [Eyebrows and eyelashes](#eyebrows-and-eyelashes)[](#eyebrows-and-eyelashes)

Eyebrows and eyelashes are optional layered accessories for makeup looks. If you choose to include them in your creations, they must meet all [layered accessory requirements](/docs/avatar/layered-accessories/specifications) , notably:

-

Cage data  - Eyebrows and eyelashes each require their own inner and outer cage.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eye-Accessory-Datamodel.png)

-

Eyebrows and eyelashes can also take advantage of automatic skinning, specifically with [special skinning joints](/docs/avatar/automatic-skinning-transfer#special-skinning-transfer-joints) .

-

Geometry size  - Eye accessories can't exceed the [maximum dimensions](/docs/avatar/layered-accessories/specifications)  for their asset type.

-

Budgets  - Eye accessories can't exceed 4k triangles each.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
