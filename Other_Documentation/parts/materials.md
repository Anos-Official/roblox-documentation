<!-- Source: https://create.roblox.com/docs/parts/materials -->

Materials | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts/materials.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)

# Materials

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/materials.md)

Roblox's materials are unlike materials on other platforms, in that their visual appearance and  their [physical properties](#physical-properties)  reflect those of materials in the real world. For example, concrete is heavier than plastic and sinks faster in water. When you set the material of a part or terrain, Roblox simulates its physical material properties to make this behavior just work.

The Roblox Engine offers a range of [base materials](#base-materials)  suitable to build many games, including various categories of metal, rock, and organic materials.

You can also create your own [custom materials](#custom-materials)  and apply them to parts or [terrain](/docs/parts/terrain) . Custom materials have an additional [adaptive materials](#adaptive-materials)  behavior that lets you adapt any model to use your art style and custom materials, even if someone else created the model.

## [Apply materials](#apply-materials)[](#apply-materials)

You can quickly apply materials to [parts](/docs/parts)  through the [Material](#material-widget)  widget. The [Material Manager](#material-manager)  offers the same functionality and an additional "paint tool" application mode.

### [Material widget](#material-widget)[](#material-widget)

The Material  widget is accessible from the Home  or Model  tab toolbars. Click‑holding over the small corner arrow on the button reveals a material picker. See [Parts](/docs/parts#material)  for more information.

 ![Material widget's picker highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Material-Picker.png)

### [Material Manager](#material-manager)[](#material-manager)

The Material Manager  is accessible through Window  ⟩ 3D  ⟩ Material  or from the Material  widget's picker popup. From the manager window, you can apply materials to [parts](/docs/parts)  through the following workflows.

Apply to Selected Paint Tool

The default [Enum.Material](/docs/reference/engine/enums/Material)  property for new [Part](/docs/reference/engine/classes/Part)  instances is Plastic . To apply a different material to parts:

1.

In the 3D viewport or [Explorer](/docs/studio/explorer) , select one or more parts.

2.

In the Material Manager  palette, hover your mouse over the desired material (you don't need to select it) and click the Apply to Selected Parts  button.

 ![Apply to Selected Parts button indicated in Material Manager](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Apply-To-Selected-Parts.png)

## [Custom materials](#custom-materials)[](#custom-materials)

The [Material Manager](#material-manager)  provides a user interface to interact with various aspects of [MaterialService](/docs/reference/engine/classes/MaterialService) , including creating new custom materials and applying them to parts and [terrain](/docs/parts/terrain) . Custom materials are represented by [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instances within [MaterialService](/docs/reference/engine/classes/MaterialService) .

 ![Explorer window showing two MaterialVariant instances within MaterialService](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Explorer-MaterialVariant-Instances.png)

You can apply custom materials per-part or globally to both parts and terrain, and you can fine-tune how custom materials apply to faces of terrain with [TerrainDetail](/docs/reference/engine/classes/TerrainDetail)  instances. To paint many distinct materials onto terrain in one place, including multiple color variations, see [Custom terrain materials](/docs/parts/custom-terrain-materials) .

[MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  and [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  instances both use [PBR](/docs/art/modeling/surface-appearance)  textures to customize the appearance of objects. The difference is that [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  is for customizing the appearance of reusable tileable material, whereas [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  is for customizing the visual appearance of a specific mesh with UV mapping. [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instances also have [physical properties](#physical-properties)  that [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  instances don't.

### [Create custom materials](#create-custom-materials)[](#create-custom-materials)

You can edit all properties of a custom material in the [Material Manager](#material-manager)  or through the properties of a [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instance. You can also generate custom materials through the prompt‑based [Material Generator](/docs/studio/material-generator) .

To create a custom material in the [Material Manager](#material-manager) :

1.

Click the base material  from which your custom material will inherit [physical properties](#physical-properties) . If you skip this step, the base material will be Plastic , but you can change it later.

 ![A Base material of Asphalt that's selected in the Material Manager.](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Base-Material-Selected.png)

2.

In the top-left corner, click Create Material Variant .

 ![Create Material Variant button indicated in Material Manager.](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Create-Material-Variant.png)

A new variant appears in the palette with an icon in the bottom-right corner, indicating it's a custom material.

 ![New MaterialVariant tile in Material Manager with icon to indicate a custom material.](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Custom-Material-Icon.png)

3.

In the inspector, rename your custom material to describe its purpose. You can change the name later, but if you do so after  applying the material to parts, you'll need to re-apply it to those parts.

4.

For each texture map  option such as Color  or Normal , paste an asset ID or import a new texture from your computer. Square textures work best. If you don't specify an asset for a texture map, that texture remains blank.

5.

If desired, adjust the Studs Per Tile  and Pattern  values to change how the material looks.

If necessary, you can delete a custom material from the [Material Manager](#material-manager)  by selecting it and clicking the Delete  button below its preview globe. Alternatively, you can delete its associated [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instance within MaterialService  of the [Explorer](/docs/studio/explorer) .

### [Apply custom materials](#apply-custom-materials)[](#apply-custom-materials)

For [parts](/docs/parts) , you can use a custom material just like any other material, applying it to selected parts through the [Material](#apply-materials)  widget or the [Material Manager](#material-manager) .¹

You can also apply the new material to a part by setting its MaterialVariant  property in the [Properties](/docs/studio/properties)  window. In this case, Studio automatically sets its Material  property to the base material you chose when creating the material.

 ![Material and MaterialVariant properties set in the Properties window.](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Properties-Material-And-MaterialVariant.png)

Note that if you rename a custom material after  applying it to parts, those parts will not automatically use the custom material with the new name. This behavior allows for [Adaptive Materials](#adaptive-materials) . If you want parts to continue using a custom material after you rename it, you'll need to re-apply the custom material.

 ¹ On terrain, you can set a custom material as a [material override](#material-overrides)  for an existing base material, or paint many distinct materials with [custom terrain materials](/docs/parts/custom-terrain-materials)  after you enable Expanded Terrain .

### [Material overrides](#material-overrides)[](#material-overrides)

You can set a custom material as a material override  to make its base material serve as a reference to the custom material. When you do so, Studio will use the custom material for both the textures and [physical properties](#physical-properties)  of any part or [terrain](/docs/parts/terrain)  that uses the custom material.

Material overrides apply one custom material to every instance of a base material in a place, including terrain that uses that base material. To paint multiple variants or colors of the same base material onto terrain in one place, use [custom terrain materials](/docs/parts/custom-terrain-materials) .

#### [Set overrides](#set-overrides)[](#set-overrides)

To set a custom material as a material override in the [Material Manager](#material-manager) :

1.

Click the custom material that you want to set as an override.

2.

In the inspector, scroll down to Overrides  and enable Set as Override .

 ![.](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Set-Override-Enabled.png)

The new override appears as a property of MaterialService  in the [Properties](/docs/studio/properties)  window.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Properties-View-Override.png)

#### [Terrain details](#terrain-details)[](#terrain-details)

By default, applying a custom material to parts or as an override applies that custom material as tiles across each face. For terrain, you can optionally configure [TerrainDetail](/docs/reference/engine/classes/TerrainDetail)  instances to customize the top , side , and bottom  of terrain voxels using that custom material.

To customize the faces of terrain using a custom material:

1.

In the palette of the [Material Manager](#material-manager) , click the custom material.

2.

In the inspector, confirm that its Set as Override  toggle is enabled.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Set-Override-Enabled.png)

3.

In the Terrain Details  section, click Create  for each face you want to customize.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Terrain-Details-Create-Buttons.png)

4.

For each face you enable, expand the arrow to access and edit details such as its name, texture maps, studs per tile, and pattern.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Terrain-Details-Edit.png)

#### [Disable overrides](#disable-overrides)[](#disable-overrides)

You can disable an entire material override and all base materials that it's currently overriding, or you can disable the override for a specific base material.

Disable Entire Override Disable Override for Specific Material

1.

In the palette of the [Material Manager](#material-manager) , click a custom material  that's being used as an override.

2.

In the inspector, scroll down to Overrides  and disable Set as Override .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Set-Override-Disabled.png)

## [Physical properties](#physical-properties)[](#physical-properties)

All materials have built-in physical properties  such as density, elasticity, and friction. Through the application of [custom materials](#custom-materials)  with unique physical properties, you can affect global material behavior for all parts and [terrain](/docs/parts/terrain)  which use the custom material, such as creating an extremely slippery variant of the Ice  material.

When factoring physical properties, the engine prioritizes more granular per-part settings over material behaviors to determine the effective physical properties of a surface:

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Highest.png)

Custom physical properties of the specific part.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Higher.png)

Custom physical properties of the part's custom material.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-High.png)

Custom physical properties of the [material override](#set-overrides)  of the part's material.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Neutral.png)

The [default physical properties](#default-physical-properties)  of the part's material.

Applying to Custom Materials Per-Part Overrides

To set unique physical properties for any [custom material](#custom-materials)  and automatically apply them to all parts and [terrain](/docs/parts/terrain)  which use the material:

1.

In the palette of the [Material Manager](#material-manager) , click the custom material.

2.

In the inspector, scroll down to the Physics  section and set custom physical properties as detailed in the [PhysicalProperties](/docs/reference/engine/datatypes/PhysicalProperties)  reference.

 ![Custom physical properties in Material Manager inspector pane](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Physical-Properties.png)

For any part that uses the custom material and does not  have [part-specific](#physical-properties)  overrides, the CurrentPhysicalProperties  branch in the [Properties](/docs/studio/properties)  window reveals that its default physical properties are overridden by the custom material's properties.

 ![Properties window showing physical properties overridden by those of custom material](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Properties-Physical-Overridden.png)

## [Adaptive materials](#adaptive-materials)[](#adaptive-materials)

When you apply a custom material to a part, the part's [Part.MaterialVariant](/docs/reference/engine/classes/Part#MaterialVariant)  property becomes the name of its [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  rather than its specific instance. This means that when you reuse the part in the same or a different place, as in a model or package, it's easier for you to adapt different custom materials to adjust the part's look. The adaptive behavior of custom materials has the following effects:

-

If you create collections of custom materials with the same name but different textures, then you can quickly change the style of a place by changing which collection is a child of [MaterialService](/docs/reference/engine/classes/MaterialService) .

-

If you insert a model with parts that use a custom material, then you can modify its look by creating an instance of [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  in [MaterialService](/docs/reference/engine/classes/MaterialService)  and renaming it to the same name as the previous custom material, rather than applying the new material to the parts in the model.

When you reuse custom materials in models and packages, each MaterialVariant  instance must be in [MaterialService](/docs/reference/engine/classes/MaterialService)  for it to work.

-

If you distribute a model to the Creator Store with a custom material, include the [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instance in the model. For more information about distributing models to the Creator Store, see [Distributing Assets](/docs/production/creator-store) .

-

If you insert a model from the Creator Store, look for any [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instances and copy them to [MaterialService](/docs/reference/engine/classes/MaterialService) . For more information about importing models from the Creator Store, see [Creator Store](/docs/production/creator-store) .

-

If you want to use custom materials with packages, put the package in [MaterialService](/docs/reference/engine/classes/MaterialService) . For more information on packages, see [Packages](/docs/projects/assets/packages) .

The [Creator Store](/docs/production/creator-store)  has a category called Materials for "material packs", models that contain only [MaterialVariant](/docs/reference/engine/classes/MaterialVariant) , [TerrainDetail](/docs/reference/engine/classes/TerrainDetail) , [Folder](/docs/reference/engine/classes/Folder) , and [Model](/docs/reference/engine/classes/Model)  instances. The Materials category is a way to promote and discover custom materials by other creators.

To make the most of adaptive materials, use a consistent naming convention for your [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instances. For example, you can use PascalCase  with the base material of the custom material as the first word, as in GrassWet , GrassDry , and GrassBurned .

## [Asset and property reference](#asset-and-property-reference)[](#asset-and-property-reference)

### [Base materials](#base-materials)[](#base-materials)

Shaders generate the look and feel of materials. The base material shaders work differently than the shader which [MaterialVariant](/docs/reference/engine/classes/MaterialVariant)  instances use, so you can't create custom materials that look exactly like base materials, but you can still create custom materials that use their textures. The following tables list the asset IDs for material details such as [ColorMap](/docs/reference/engine/classes/SurfaceAppearance#ColorMap)  and [RoughnessMap](/docs/reference/engine/classes/SurfaceAppearance#RoughnessMap) .

Current Base Pre-2022 Base Current Terrain Pre-2022 Terrain

| Material | | ColorMap | | Normal | | Metalness | | Roughness |
| --- | --- |
| [Asphalt](/docs/reference/engine/enums/Material#Asphalt) | | 9930003046 | | 9429449876 | |  | | 9429450346 |
| [Basalt](/docs/reference/engine/enums/Material#Basalt) | | 9920482056 | | 9438412214 | |  | | 9438412457 |
| [Brick](/docs/reference/engine/enums/Material#Brick) | | 9920482813 | | 9438453152 | |  | | 9438453413 |
| [Cardboard](/docs/reference/engine/enums/Material#Cardboard) | | 14108651729 | | 14108654002 | |  | | 14108654299 |
| [Carpet](/docs/reference/engine/enums/Material#Carpet) | | 14108662587 | | 14108663154 | |  | | 14108663726 |
| [CeramicTiles](/docs/reference/engine/enums/Material#CeramicTiles) | | 17429425079 | | 17429425915 | | 17429426100 | | 17429426861 |
| [ClayRoofTiles](/docs/reference/engine/enums/Material#ClayRoofTiles) | | 18147681935 | | 18147683410 | |  | | 18147684855 |
| [Cobblestone](/docs/reference/engine/enums/Material#Cobblestone) | | 9919718991 | | 9438457162 | |  | | 9438457470 |
| [Concrete](/docs/reference/engine/enums/Material#Concrete) | | 9920484153 | | 9466554006 | |  | | 9466554186 |
| [CorrodedMetal](/docs/reference/engine/enums/Material#CorrodedMetal) | | 9920589327 | | 9439548484 | | 9439548749 | | 9439556441 |
| [CrackedLava](/docs/reference/engine/enums/Material#CrackedLava) | | 9920484943 | | 9438508790 | |  | | 9438509046 |
| [DiamondPlate](/docs/reference/engine/enums/Material#DiamondPlate) | | 10237720195 | | 9438583222 | | 9438583347 | | 9438583558 |
| [Fabric](/docs/reference/engine/enums/Material#Fabric) | | 9920517696 | | 9873280412 | |  | | 9873282563 |
| [Foil](/docs/reference/engine/enums/Material#Foil) | | 9466552117 | | 9424786192 | | 9424786272 | | 9424786620 |
| [ForceField](/docs/reference/engine/enums/Material#ForceField) ² | |  | |  | |  | |  |
| [Glacier](/docs/reference/engine/enums/Material#Glacier) | | 9920518732 | | 9438812958 | |  | | 9438851286 |
| [Glass](/docs/reference/engine/enums/Material#Glass) ³ | | 9438868521 | | 7547304785 | |  | | 7547304892 |
| [Granite](/docs/reference/engine/enums/Material#Granite) | | 9920550238 | | 9438882935 | |  | | 9438883109 |
| [Grass](/docs/reference/engine/enums/Material#Grass) | | 9920551868 | | 9438955773 | |  | | 9438955997 |
| [Ground](/docs/reference/engine/enums/Material#Ground) | | 9920554482 | | 9439043558 | |  | | 9439043765 |
| [Ice](/docs/reference/engine/enums/Material#Ice) | | 9920555943 | | 9467301039 | |  | | 9467301203 |
| [LeafyGrass](/docs/reference/engine/enums/Material#LeafyGrass) | | 9920557906 | | 9439080781 | |  | | 9439080950 |
| [Leather](/docs/reference/engine/enums/Material#Leather) | | 14108670073 | | 14108670486 | |  | | 14108670748 |
| [Limestone](/docs/reference/engine/enums/Material#Limestone) | | 9920561437 | | 9439415191 | |  | | 9439415495 |
| [Marble](/docs/reference/engine/enums/Material#Marble) | | 9439430596 | | 9439431240 | |  | | 9439431383 |
| [Metal](/docs/reference/engine/enums/Material#Metal) | | 9920574687 | | 9873295432 | | 9873318201 | | 9873318890 |
| [Mud](/docs/reference/engine/enums/Material#Mud) | | 9920578473 | | 9439509827 | |  | | 9439510012 |
| [Neon](/docs/reference/engine/enums/Material#Neon) ² | |  | |  | |  | |  |
| [Pavement](/docs/reference/engine/enums/Material#Pavement) | | 9920579943 | | 9439519281 | |  | | 9439519532 |
| [Pebble](/docs/reference/engine/enums/Material#Pebble) | | 9920581082 | | 9439528644 | |  | | 9439537267 |
| [Plaster](/docs/reference/engine/enums/Material#Plaster) | | 14108671255 | | 14108671870 | |  | | 14108672378 |
| [Plastic](/docs/reference/engine/enums/Material#Plastic) ² | |  | |  | |  | |  |
| [Rock](/docs/reference/engine/enums/Material#Rock) | | 9920587470 | | 9439538417 | |  | | 9439545859 |
| [RoofShingles](/docs/reference/engine/enums/Material#RoofShingles) | | 119722544879522 | | 77534750680073 | |  | | 129397260312247 |
| [Rubber](/docs/reference/engine/enums/Material#Rubber) | | 14108673018 | | 14108674698 | | 14108674894 | | 14108675142 |
| [Salt](/docs/reference/engine/enums/Material#Salt) | | 9920590225 | | 9439565809 | |  | | 9439566688 |
| [Sand](/docs/reference/engine/enums/Material#Sand) | | 9920591683 | | 9439577084 | |  | | 9439577327 |
| [Sandstone](/docs/reference/engine/enums/Material#Sandstone) | | 9920596120 | | 9439596530 | |  | | 9439596711 |
| [Slate](/docs/reference/engine/enums/Material#Slate) | | 9920599782 | | 9439612514 | |  | | 9439612733 |
| [SmoothPlastic](/docs/reference/engine/enums/Material#SmoothPlastic) ² | |  | |  | |  | |  |
| [Snow](/docs/reference/engine/enums/Material#Snow) | | 9920620284 | | 9439632006 | |  | | 9439632145 |
| [Wood](/docs/reference/engine/enums/Material#Wood) | | 9920625290 | | 9439641376 | |  | | 9439648605 |
| [WoodPlanks](/docs/reference/engine/enums/Material#WoodPlanks) | | 9920626778 | | 9439650689 | |  | | 9439658127 |

² Material is unique and/or its texture assets are bundled with Studio instead of being accessible as a typical asset ID.
³ Refraction of light through the glass material is not supported on mobile devices due to computational limitations.

### [Default colors](#default-colors)[](#default-colors)

The following table lists the default RGB values for each base material. For information on how to color parts and terrain, see [Parts](/docs/parts#color)  and [Environmental Terrain](/docs/parts/terrain#custom-terrain-colors) .

| Material | | RGB Value | | Color |
| [Asphalt](/docs/reference/engine/enums/Material#Asphalt) | | [80, 84, 84] | |  |
| [Basalt](/docs/reference/engine/enums/Material#Basalt) | | [75, 74, 74] | |  |
| [Brick](/docs/reference/engine/enums/Material#Brick) | | [138, 97, 73] | |  |
| [Cardboard](/docs/reference/engine/enums/Material#Cardboard) | | [255, 206, 152] | |  |
| [Carpet](/docs/reference/engine/enums/Material#Carpet) | | [163, 162, 165] | |  |
| [CeramicTiles](/docs/reference/engine/enums/Material#CeramicTiles) | | [181, 173, 156] | |  |
| [ClayRoofTiles](/docs/reference/engine/enums/Material#ClayRoofTiles) | | [255, 142, 87] | |  |
| [Cobblestone](/docs/reference/engine/enums/Material#Cobblestone) | | [134, 134, 118] | |  |
| [Concrete](/docs/reference/engine/enums/Material#Concrete) | | [152, 152, 152] | |  |
| [CorrodedMetal](/docs/reference/engine/enums/Material#CorrodedMetal) | | [104, 140, 173] | |  |
| [CrackedLava](/docs/reference/engine/enums/Material#CrackedLava) | | [255, 24, 67] | |  |
| [DiamondPlate](/docs/reference/engine/enums/Material#DiamondPlate) | | [168, 175, 176] | |  |
| [Fabric](/docs/reference/engine/enums/Material#Fabric) | | [194, 193, 168] | |  |
| [Foil](/docs/reference/engine/enums/Material#Foil) | | [168, 175, 176] | |  |
| [ForceField](/docs/reference/engine/enums/Material#ForceField) | | [163, 162, 165] | |  |
| [Glacier](/docs/reference/engine/enums/Material#Glacier) | | [221, 228, 229] | |  |
| [Glass](/docs/reference/engine/enums/Material#Glass) | | [138, 167, 168] | |  |
| [Granite](/docs/reference/engine/enums/Material#Granite) | | [149, 146, 139] | |  |
| [Grass](/docs/reference/engine/enums/Material#Grass) | | [111, 126, 62] | |  |
| [Ground](/docs/reference/engine/enums/Material#Ground) | | [140, 130, 104] | |  |
| [Ice](/docs/reference/engine/enums/Material#Ice) | | [204, 210, 223] | |  |
| [LeafyGrass](/docs/reference/engine/enums/Material#LeafyGrass) | | [106, 134, 64] | |  |
| [Leather](/docs/reference/engine/enums/Material#Leather) | | [110, 73, 53] | |  |
| [Limestone](/docs/reference/engine/enums/Material#Limestone) | | [255, 243, 192] | |  |
| [Marble](/docs/reference/engine/enums/Material#Marble) | | [122, 122, 122] | |  |
| [Metal](/docs/reference/engine/enums/Material#Metal) | | [168, 175, 176] | |  |
| [Mud](/docs/reference/engine/enums/Material#Mud) | | [121, 112, 98] | |  |
| [Neon](/docs/reference/engine/enums/Material#Neon) | | [163, 162, 165] | |  |
| [Pavement](/docs/reference/engine/enums/Material#Pavement) | | [143, 144, 135] | |  |
| [Pebble](/docs/reference/engine/enums/Material#Pebble) | | [122, 122, 118] | |  |
| [Plaster](/docs/reference/engine/enums/Material#Plaster) | | [204, 142, 105] | |  |
| [Plastic](/docs/reference/engine/enums/Material#Plastic) | | [163, 162, 165] | |  |
| [Rock](/docs/reference/engine/enums/Material#Rock) | | [99, 100, 102] | |  |
| [RoofShingles](/docs/reference/engine/enums/Material#RoofShingles) | | [66, 66, 66] | |  |
| [Rubber](/docs/reference/engine/enums/Material#Rubber) | | [32, 32, 32] | |  |
| [Salt](/docs/reference/engine/enums/Material#Salt) | | [255, 255, 254] | |  |
| [Sand](/docs/reference/engine/enums/Material#Sand) | | [207, 203, 167] | |  |
| [Sandstone](/docs/reference/engine/enums/Material#Sandstone) | | [148, 124, 95] | |  |
| [Slate](/docs/reference/engine/enums/Material#Slate) | | [88, 89, 86] | |  |
| [SmoothPlastic](/docs/reference/engine/enums/Material#SmoothPlastic) | | [163, 162, 165] | |  |
| [Snow](/docs/reference/engine/enums/Material#Snow) | | [235, 253, 255] | |  |
| [Wood](/docs/reference/engine/enums/Material#Wood) | | [172, 148, 108] | |  |
| [WoodPlanks](/docs/reference/engine/enums/Material#WoodPlanks) | | [172, 148, 108] | |  |

### [Default physical properties](#default-physical-properties)[](#default-physical-properties)

The following table lists each material's default physical properties as detailed in the [PhysicalProperties](/docs/reference/engine/datatypes/PhysicalProperties)  reference. For information on customizing physical properties, see [physical properties](#physical-properties) .

| Material | | Density | | Elasticity | | ElasticityWeight | | Friction | | FrictionWeight |
| [Asphalt](/docs/reference/engine/enums/Material#Asphalt) | | 2.36 | | 0.2 | | 1 | | 0.8 | | 0.3 |
| [Basalt](/docs/reference/engine/enums/Material#Basalt) | | 2.691 | | 0.15 | | 1 | | 0.7 | | 0.3 |
| [Brick](/docs/reference/engine/enums/Material#Brick) | | 1.922 | | 0.15 | | 1 | | 0.8 | | 0.3 |
| [Cardboard](/docs/reference/engine/enums/Material#Cardboard) | | 0.7 | | 0.05 | | 2 | | 0.5 | | 1 |
| [Carpet](/docs/reference/engine/enums/Material#Carpet) | | 1.1 | | 0.25 | | 2 | | 0.4 | | 1 |
| [CeramicTiles](/docs/reference/engine/enums/Material#CeramicTiles) | | 2.4 | | 0.2 | | 1 | | 0.51 | | 1 |
| [ClayRoofTiles](/docs/reference/engine/enums/Material#ClayRoofTiles) | | 2 | | 0.2 | | 1 | | 0.51 | | 1 |
| [Cobblestone](/docs/reference/engine/enums/Material#Cobblestone) | | 2.691 | | 0.17 | | 1 | | 0.5 | | 1 |
| [Concrete](/docs/reference/engine/enums/Material#Concrete) | | 2.403 | | 0.2 | | 1 | | 0.7 | | 0.3 |
| [CorrodedMetal](/docs/reference/engine/enums/Material#CorrodedMetal) | | 7.85 | | 0.2 | | 1 | | 0.7 | | 1 |
| [CrackedLava](/docs/reference/engine/enums/Material#CrackedLava) | | 2.691 | | 0.15 | | 1 | | 0.65 | | 1 |
| [DiamondPlate](/docs/reference/engine/enums/Material#DiamondPlate) | | 7.85 | | 0.25 | | 1 | | 0.35 | | 1 |
| [Fabric](/docs/reference/engine/enums/Material#Fabric) | | 0.7 | | 0.05 | | 1 | | 0.35 | | 1 |
| [Foil](/docs/reference/engine/enums/Material#Foil) | | 2.7 | | 0.25 | | 1 | | 0.4 | | 1 |
| [ForceField](/docs/reference/engine/enums/Material#ForceField) | | 2.403 | | 0.2 | | 1 | | 0.25 | | 1 |
| [Glacier](/docs/reference/engine/enums/Material#Glacier) | | 0.919 | | 0.15 | | 1 | | 0.05 | | 2 |
| [Glass](/docs/reference/engine/enums/Material#Glass) | | 2.403 | | 0.2 | | 1 | | 0.25 | | 1 |
| [Granite](/docs/reference/engine/enums/Material#Granite) | | 2.691 | | 0.2 | | 1 | | 0.4 | | 1 |
| [Grass](/docs/reference/engine/enums/Material#Grass) | | 0.9 | | 0.1 | | 1.5 | | 0.4 | | 1 |
| [Ground](/docs/reference/engine/enums/Material#Ground) | | 0.9 | | 0.1 | | 1 | | 0.45 | | 1 |
| [Ice](/docs/reference/engine/enums/Material#Ice) | | 0.919 | | 0.15 | | 1 | | 0.02 | | 3 |
| [LeafyGrass](/docs/reference/engine/enums/Material#LeafyGrass) | | 0.9 | | 0.1 | | 2 | | 0.4 | | 2 |
| [Leather](/docs/reference/engine/enums/Material#Leather) | | 0.86 | | 0.25 | | 1 | | 0.35 | | 1 |
| [Limestone](/docs/reference/engine/enums/Material#Limestone) | | 2.691 | | 0.15 | | 1 | | 0.5 | | 1 |
| [Marble](/docs/reference/engine/enums/Material#Marble) | | 2.563 | | 0.17 | | 1 | | 0.2 | | 1 |
| [Metal](/docs/reference/engine/enums/Material#Metal) | | 7.85 | | 0.25 | | 1 | | 0.4 | | 1 |
| [Mud](/docs/reference/engine/enums/Material#Mud) | | 0.9 | | 0.07 | | 4 | | 0.3 | | 3 |
| [Neon](/docs/reference/engine/enums/Material#Neon) | | 0.7 | | 0.2 | | 1 | | 0.3 | | 1 |
| [Pavement](/docs/reference/engine/enums/Material#Pavement) | | 2.691 | | 0.17 | | 1 | | 0.5 | | 0.3 |
| [Pebble](/docs/reference/engine/enums/Material#Pebble) | | 2.403 | | 0.17 | | 1.5 | | 0.4 | | 1 |
| [Plaster](/docs/reference/engine/enums/Material#Plaster) | | 0.75 | | 0.2 | | 1 | | 0.6 | | 0.3 |
| [Plastic](/docs/reference/engine/enums/Material#Plastic) | | 0.7 | | 0.5 | | 1 | | 0.3 | | 1 |
| [Rock](/docs/reference/engine/enums/Material#Rock) | | 2.691 | | 0.17 | | 1 | | 0.5 | | 1 |
| [RoofShingles](/docs/reference/engine/enums/Material#RoofShingles) | | 2.36 | | 0.2 | | 1 | | 0.8 | | 0.3 |
| [Rubber](/docs/reference/engine/enums/Material#Rubber) | | 1.3 | | 0.95 | | 2 | | 1.5 | | 3 |
| [Salt](/docs/reference/engine/enums/Material#Salt) | | 2.165 | | 0.05 | | 1 | | 0.5 | | 1 |
| [Sand](/docs/reference/engine/enums/Material#Sand) | | 1.602 | | 0.05 | | 2.5 | | 0.5 | | 5 |
| [Sandstone](/docs/reference/engine/enums/Material#Sandstone) | | 2.691 | | 0.15 | | 1 | | 0.5 | | 5 |
| [SmoothPlastic](/docs/reference/engine/enums/Material#SmoothPlastic) | | 0.7 | | 0.5 | | 1 | | 0.2 | | 1 |
| [Slate](/docs/reference/engine/enums/Material#Slate) | | 2.691 | | 0.2 | | 1 | | 0.4 | | 1 |
| [Snow](/docs/reference/engine/enums/Material#Snow) | | 0.9 | | 0.03 | | 4 | | 0.3 | | 3 |
| [Wood](/docs/reference/engine/enums/Material#Wood) | | 0.35 | | 0.2 | | 1 | | 0.48 | | 1 |
| [WoodPlanks](/docs/reference/engine/enums/Material#WoodPlanks) | | 0.35 | | 0.2 | | 1 | | 0.48 | | 1 |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
