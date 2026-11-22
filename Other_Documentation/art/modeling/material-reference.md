<!-- Source: https://create.roblox.com/docs/art/modeling/material-reference -->

Material references | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/material-reference.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Texturing

# Material references

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/material-reference.md)

When combining different combinations of metalness and roughness values with your PBR textures, Roblox can render virtually every type of surface with a high level of realism. The following includes various material values for common materials and [clothing examples](#clothing-examples)  that you can use when creating your own PBR surfaces.

The following figure illustrates the various base surface types you can achieve with various roughness and metallic values:

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-Metalness-Matrix.png)

## [Common materials](#common-materials)[](#common-materials)

You can use the following material reference values as a baseline for creating your own custom surfaces:

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/01_GlossyPlastic.png) Glossy Plastic
Roughness: 0.1
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/02_MattePlastic.png) Matte Plastic
Roughness: 0.4
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/03_Rubber.png) Rubber
Roughness: 0.5 - 0.6
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/04_Latex.png) Latex
Roughness: 0.0
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/05_GlossyWood.png) Glossy Wood
Roughness: 0.2 - 0.3
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/06_WornWood.png) Worn Wood
Roughness: 0.7 - 0.9
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/07_CottonCanvasDenim.png) Cotton, Canvas, Denim
Roughness: 0.8 - 0.9
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/08_PolyesterNylon.png) Polyester, Nylon
Roughness: 0.6 - 0.8
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/09_WoolLinen.png) Wool, Linen
Roughness: 0.9 - 0.96
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/010_SilkSatin.png) Silk, Satin
Roughness: 0.4 - 0.6
Metalness: 0.4 - 0.6

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/011_VelvetSuede.png) Velvet, Suede
Roughness: 0.6 - 0.8
Metalness: 0.4 - 0.6

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/012_GlossyLeather.png) Glossy Leather
Roughness: 0.2 - 0.4
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/013_WornLeather.png) Worn Leather
Roughness: 0.5 - 0.7
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/014_Fur.png) Fur
Roughness: 0.65 - 0.75
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/015_Scales.png) Scales
Roughness: 0.5 - 0.6
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/016_Bone.png) Bone
Roughness: 0.5
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/017_Skin.png) Skin
Roughness: 0.65
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/018_Wax.png) Wax
Roughness: 0.38
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/019_Marble.png) Marble
Roughness: 0.375
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/020_Jade.png) Jade
Roughness: 0.15
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/021_PaintedMetal.png) Painted Metal
Roughness: 0.3
Metalness: 0.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/022_PureMetals.png) Pure Metals (Gold, Silver, Bronze)
Roughness: 0.2 - 0.3
Metalness: 1.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/023_WornMetals.png) Worn Metals
Roughness: 0.2 - 0.4
Metalness: 1.0

![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/024_GlassMirror.png) Glass Mirror
Roughness: 0.0
Metalness: 0.1

## [Clothing examples](#clothing-examples)[](#clothing-examples)

Layered clothing can take advantage of PBR textures to achieve realistic and visually popping cosmetics for avatar characters. Use the following reference examples to compare how various material values are used to achieve a certain cosmetic effect and its comparable real-time rendering in Substance Painter and Roblox Studio:

| Substance Painter render | | Roblox Studio render | | Material values |
| --- | --- |
| ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Leather-Jacket-Sp.png) | | ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Leather-Jacket-St.png) | | Leather fabric:
 Roughness: 0.62
 Metalness: 0.0
 Brass zipper:
 Roughness: 0.25
 Metalness: 1.0
 |
| ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Gold-Puffy-Jacket-Sp.png) | | ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Gold-Puffy-Jacket-St.png) | | Metallic puffer fabric:
 Roughness: 0.62
 Metalness: 1.0
 Brass zipper and buttons:
 Roughness: 0.482
 Metalness: 1.0
 Fur hood:
 Roughness: 0.75
 Metalness: 0.0
 Cotton band:
 Roughness: 0.8
 Metalness: 0.0
 |
| ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Green-Jacket-Sp.png) | | ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Green-Jacket-St.png) | | Silk fabric:
 Roughness: 0.52
 Metalness: 0.3
 Steel zipper and buttons:
 Roughness: 0.25
 Metalness: 1.0
 Cotton band:
 Roughness: 0.9
 Metalness: 0.0
 |
| ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Denim-Jacket-Sp.png) | | ![](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Denim-Jacket-St.png) | | Denim fabric:
 Roughness: 0.9
 Metalness: 0.0
 Tarnished steel buttons:
 Roughness: 0.33
 Metalness: 1.0
 |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
