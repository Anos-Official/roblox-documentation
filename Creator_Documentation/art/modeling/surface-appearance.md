<!-- Source: https://create.roblox.com/docs/en-us/art/modeling/surface-appearance -->

PBR textures | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/surface-appearance.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Texturing

# PBR textures

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/surface-appearance.md)

Physically-Based Rendering  (PBR) textures allow you to represent realistic shading and lighting by using multiple types of texture images, or maps , on a single object. Combining multiple texture maps can more accurately simulate color, roughness, and reflectivity in any lighting environment and can enhance the visual elements of your assets and environment.

Clothing Environment

![A humanoid avatar with dreadlocks, a glossy jacket, jeans with decals, and boots.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png)

![A humanoid avatar with a short haircut, leather jacket, capri pants, and orange shoes.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example-2.jpg)

Various applications and workflows are available for creating PBR textures. You can use these during the modeling and texturing phases of custom 3D object creation, provided that Roblox Studio [supports](/docs/en-us/avatar/character-bodies/specifications#textures)  the specific texture maps you're using.

For information on how to properly connect PBR textures to your model in Blender and Maya for import into Studio, see [Blender / Maya texture settings](/docs/en-us/art/modeling/assign-textures) .

This guide provides instructions on [setting up](#enable-surface-appearance)  your mesh objects to use PBR texture maps, and describes common use-cases and best practices for Roblox's supported PBR [texture maps](#texture-maps) . When creating your own surfaces, see [material references](/docs/en-us/art/modeling/material-reference)  for common material values, image comparisons and clothing examples.

## [Enable surface appearance](#enable-surface-appearance)[](#enable-surface-appearance)

You can add PBR textures to any [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  by adding a [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  object which overwrites the original assigned texture. In general, you can't modify [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  properties by scripts during a game because the engine requires some pre-processing to display these graphics. Similar to adding a basic texture, each texture image map must point to the appropriate uploaded image asset ID.

To enable surface appearance for a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) :

1.

In the Explorer  window, hover over the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  and click the ⊕ button.

2.

Insert a [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  from the contextual menu.

 ![A SurfaceAppearance object parented within a MeshPart in Studio's Explorer window.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/MeshPart-SurfaceAppearance.png)

When you're ready to add texture maps to the [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  object, you can click each map property in the Properties  window and enter an asset ID.

## [Texture maps](#texture-maps)[](#texture-maps)

Studio currently supports 5 types of PBR texture maps: [color](#color-albedo) , [normal](#normal) , [roughness](#roughness) , [metalness](#metalness) , and [emissive](#emissive-mask) . Each of these maps corresponds to an important aspect of the object's surface appearance. Texture maps only change visual appearance and don't affect the geometry of the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  object.

Avoid adjusting material values to look better in one specific lighting situation. You should base your material values on the physical characteristics and test and iterate to achieve a result that remains visually accurate in various lighting environments.

See the following examples for an overview of Roblox's supported texture maps and additional resources:

Color Normal Roughness Metalness Emissive Mask

The [ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  property sets the color data of the surface, including any transparency present in the map. See [color (albedo)](#color-albedo)  for additional information.

![A completely filled image, mostly red with various black splotches and white scratches.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap.jpg) Example map

![A blank white sphere with a dark background.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap-Before.jpg) Example mesh

![A red sphere with black splotches and white scratches with a dark background.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap-After.jpg) Mesh and texture

For technical details on texture file requirements, see [texture requirements](/docs/en-us/art/modeling/texture-specifications) .

### [Color (albedo)](#color-albedo)[](#color-albedo)

The color , or albedo , map determines the color of your texture and consists of mostly color information with little to no lighting or textural information. For additional customization, you can also add [transparency](#alpha-modes)  in your albedo texture by adding opacity to your image map.

While albedo maps and generic [non-PBR texture maps](/docs/en-us/parts/textures-decals) , commonly known as diffuse maps , contain very similar base color data for a surface, diffuse maps often include shading and lighting values to imitate a specific visual element that are more effectively handled by PBR's [normal](#normal) , [roughness](#roughness) , and [metalness](#metalness)  maps. Using a typical diffuse map instead of an albedo map may often look incorrect when the lighting doesn't match with these added baked-in texture elements.

#### [Alpha modes](#alpha-modes)[](#alpha-modes)

For objects that require partial or complete sections of transparency, such as grass, leaves, lace, or decals like dirt or grunge, you can use various alpha modes  to apply transparency to your color map. If your color map image format supports alpha channels, you can apply a grayscale alpha map where 0.0  is transparent and 1.0  is opaque. Similarly, when using an image format such as a .png , any opacity on the color map applies as transparency on the asset.

You can apply transparency in two different behaviors by setting the following [AlphaMode](/docs/en-us/reference/engine/classes/SurfaceAppearance#AlphaMode)  values:

-

[Opaque](#opaque)  — Ignores the alpha channel of the [ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  and uses the color value directly from the color map.

-

[Overlay](#overlay)  — Overlays the [ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  over the underlying mesh's [MeshPart.Color](/docs/en-us/reference/engine/classes/MeshPart#Color) . Color maps using overlay mode reveal the base color of the mesh anywhere transparency is present. This is the default setting.

-

[Transparency](#alpha-modes)  — Removes the visible mesh based on transparency in the ColorMap . This renders the mesh see-through and does not reveal the original mesh color whenever transparency is present.

-

[Tint mask](#tint-mask)  — Blends the tinted [ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  over the un-tinted [ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap) .

##### [Opaque](#opaque)[](#opaque)

This mode is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ MaterialVariant Alpha Mode .

You can use [Enum.AlphaMode.Opaque](/docs/en-us/reference/engine/enums/AlphaMode#Opaque)  mode to ignore the alpha channel of the [ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  altogether. In this case the alpha value is assumed to be 1 (fully opaque).

The following example demonstrates how the [Opaque](/docs/en-us/reference/engine/enums/AlphaMode#Opaque)  mode works using a blue object as reference:

![A polkadot texture with transparency. The background is completely transparent.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Opaque-ColorMap.png) Color/albedo map with transparency

![A blue sphere on a plane.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Opaque-Before.jpg) Example mesh object

![The sphere has the polkadot patterns scattered over its surface. Transparency value is ignored.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Opaque-After.jpg)[AlphaMode](/docs/en-us/reference/engine/classes/SurfaceAppearance#AlphaMode)  set to [Opaque](/docs/en-us/reference/engine/enums/AlphaMode#Opaque)

##### [Overlay](#overlay)[](#overlay)

You can use [Enum.AlphaMode.Overlay](/docs/en-us/reference/engine/enums/AlphaMode#Overlay)  to reveal sections of the mesh's original color. Since the transparent areas of the color map expose the underlying color, you can design a unique texture map that partially or fully reveals the mesh's [Color](/docs/en-us/reference/engine/classes/MeshPart#Color)  property for custom skin tones or other situations with unique colors.

The following example demonstrates how the [Overlay](/docs/en-us/reference/engine/enums/AlphaMode#Overlay)  mode works using a light blue sphere reference:

![A completely filled image of a semi-repeating pattern with small light blue squares. The background is checkered to indicate transparency.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-ColorMap.png) Color/albedo map with transparency

![A blank cyan sphere over a dark background.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap-Before.jpg) Example mesh object

![A white sphere with small blue squares scattered over the surface.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-Overlay.jpg)[AlphaMode](/docs/en-us/reference/engine/classes/SurfaceAppearance#AlphaMode)  set to [Overlay](/docs/en-us/reference/engine/enums/AlphaMode#Overlay)

The following example uses the [Overlay](/docs/en-us/reference/engine/enums/AlphaMode#Overlay)  mode for custom characters, revealing the character's original skin-tone:

![A completely filled image of a texture map for a 3D humanoid model. Various parts of the image is checkered or partially checkered to indicate varying levels of transparency.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Custom-Skin-Tone-Map.png) Color map containing transparency in sections to expose the original mesh color

![Four of the same humanoid models with different skin tones: light brown, black, white, dark green.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Custom-Skin-Tone-Example.png) Several variations of characters with a single color map using [Overlay](/docs/en-us/reference/engine/enums/AlphaMode#Overlay)  mode

See [custom skin tone](/docs/en-us/avatar/character-bodies/specifications#custom-skin-tone)  for additional details on optimizing an overlay for skin and similar applications.

##### [Transparency](#transparency)[](#transparency)

You can use the [Enum.AlphaMode.Transparency](/docs/en-us/reference/engine/enums/AlphaMode#Transparency)  mode to create complex or extremely fine objects, such as lace or netting, by removing visible parts of the mesh as an alternative to sculpting the mesh geometry. Since this does not affect the geometry of the mesh object, this can allow you to create detailed objects without the performance impact of an intricate mesh model.

The following example demonstrates how a partial and full transparency in this mode visually removes sections of the mesh:

Sample Meshes Image Maps

![A sphere with a basket-like surface.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Opacity-0.png) No transparency

![A sphere with regular triangular patterns on its surface partially invisible.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Opacity-Half.png) Half transparency in sections

![A sphere with regular triangular patterns on its surface completely invisible.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Opacity-1.png) Full transparency in sections

There are two outcomes of [Transparency](/docs/en-us/reference/engine/enums/AlphaMode#Transparency)  mode, depending on whether the [MeshPart.Transparency](/docs/en-us/reference/engine/classes/MeshPart#Transparency)  is set to 0  or at least  0.02 , although numerical precision may result in small values such as 0.01  triggering the opaque transparency.

-

When alpha is used to cut out the shape of mostly opaque objects with hard edges such as foliage, lace fabric, and netting, set the [MeshPart.Transparency](/docs/en-us/reference/engine/classes/MeshPart#Transparency)  to 0 . When parts of the surface are fully opaque, the Roblox engine can render them with proper depth‑based occlusion. Opaque surfaces also generally work better with depth‑based effects like [DepthOfFieldEffect](/docs/en-us/reference/engine/classes/DepthOfFieldEffect) , glass and water refraction, and water reflection.

-

When alpha is used to add detail to semi‑transparent objects or objects with smooth gradients of transparency, set the [MeshPart.Transparency](/docs/en-us/reference/engine/classes/MeshPart#Transparency)  to at least  0.02 . This improves the quality of blending for objects such as dirty windows and soft‑edged feathers, but it will not work with all effects.

##### [Tint mask](#tint-mask)[](#tint-mask)

You can use the [Enum.AlphaMode.TintMask](/docs/en-us/reference/engine/enums/AlphaMode#TintMask)  mode to apply [SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  tinting to selective areas of a surface. The tinting is strongest where the alpha channel is fully visible and not applied where the alpha channel is transparent.

ColorMap RGB ColorMap Alpha Example Results

![A warm, light colored brick texture with darker grey textured grout between the bricks.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-TintMask-Bricks-Albedo.jpg)

Example brick texture, showing the color detail on brick faces as well as in the grout between the bricks.

When creating [SurfaceAppearance.ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  textures for use with a tint mask, preserve color in the transparent regions and turn off options such as pre-multiplied alpha that darken the color in transparent areas. The alpha values can also be semi-transparent to apply a partial tint to areas of the texture.

#### [Color tinting](#color-tinting)[](#color-tinting)

You can apply a tint to your color map by modifying the [SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  property. Tinting does not affect performance and you can save on memory by reusing a single color map with different tints. Use color tinting to create additional low-cost variation between your [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  PBR textures or to programmatically modify your PBR surface colors in real-time.

![A statue with a default yellow tint and reflective jade-like properties.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Tinting-None.png) Statue mesh from [The Mystery of Duvall Drive](/docs/en-us/resources/the-mystery-of-duvall-drive)  with no tinting.

![A statue with a red tint and continues to have a shiny reflective properties from its other texture maps.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Tinting-Red.png) Statue mesh with [Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  set to red.

![A statue with a green tint and continues to have a shiny reflective properties from its other texture maps.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Tinting-Green.png) Statue mesh with [Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  set to green.

[SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  tinting applies as a multiplier, so the final appearance is a function of [Color3](/docs/en-us/reference/engine/datatypes/Color3)  (texel color) times [SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color) . This means that authoring your original [SurfaceAppearance.ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  in near-white grayscale colors creates the strongest tinting effect when this property is applied.

Tinting only applies to the [SurfaceAppearance.ColorMap](/docs/en-us/reference/engine/classes/SurfaceAppearance#ColorMap)  and not the [MeshPart.Color](/docs/en-us/reference/engine/classes/MeshPart#Color) . You can continue to use alpha channels when applying [transparency](#transparency) .

When [SurfaceAppearance.AlphaMode](/docs/en-us/reference/engine/classes/SurfaceAppearance#AlphaMode)  is set to [Overlay](/docs/en-us/reference/engine/enums/AlphaMode)  and an alpha channel is present, the underlying [MeshPart.Color](/docs/en-us/reference/engine/classes/MeshPart#Color)  is revealed and [SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  tinting only applies to the visible [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  color map.

When [SurfaceAppearance.AlphaMode](/docs/en-us/reference/engine/classes/SurfaceAppearance#AlphaMode)  is set to [TintMask](/docs/en-us/reference/engine/enums/AlphaMode)  and an alpha channel is present, the alpha channel controls the amount of [SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  tinting. The tinting is strongest where the alpha channel is fully visible and not applied where the alpha channel is transparent.

Transparency AlphaMode Overlay AlphaMode TintMask AlphaMode

![A floating square plane with a cyan slate texture, that gradually changes from fully transparent on the left to fully opaque on the right. A thin horizontal bar below the floating plane has a gradient with black on the left and white on the right.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-Gradient-Transparency.jpg)

[AlphaMode](/docs/en-us/reference/engine/classes/SurfaceAppearance#AlphaMode)  set to [Transparency](/docs/en-us/reference/engine/enums/AlphaMode) . The greyscale gradient bar at the bottom indicates the alpha value. [MeshPart.Color](/docs/en-us/reference/engine/classes/MeshPart#Color)  is set to red and [SurfaceAppearance.Color](/docs/en-us/reference/engine/classes/SurfaceAppearance#Color)  is set to cyan.

### [Normal](#normal)[](#normal)

The normal , or surface , map adds texture depth to your surface and behaves similarly to a [height map](/docs/en-us/parts/terrain#heightmaps) . As a result, the effect may fade or intensify depending on the viewing angle and lighting environment.

In the following figure, you can switch between the mesh reference and the map reference for comparisons of normal map values:

Sample Meshes Image Maps

![A clay colored smooth sphere.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Normal-0.png)

![A clay colored sphere with a moderately rocky surface.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Normal-Half.png)

![A clay colored sphere with an extremely rocky surface](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Normal-1.png)

The R , G , and B  channels of the image correspond respectively to the X , Y , and Z  components of the local surface vector. A uniform image of color [127, 127, 255]  translates to a completely flat normal map. Roblox only supports OpenGL format - Tangent Space  normal maps.

Normal maps prominently affect the visual surface of a mesh and can accentuate awkward seams in your texture. Whenever possible, keep your texture seams hidden to avoid visual issues with your mesh.

### [Roughness](#roughness)[](#roughness)

Roughness , or microsurface , maps determine how light is spread across your model's surface. When roughness is at 0%, the surface doesn't scatter light at all, resulting in a much sharper and brighter reflection and glossiness on your material. At 100%, light and reflections evenly scatter over the model resulting in a less reflective matte-like surface.

The following figure shows comparisons of various roughness map values:

![A blue glossy sphere.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-0.png) 0%

![A blue semi-glossy sphere.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-Half.png) 50%

![A blue matte sphere.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-1.png) 100%

Roughness may impact how reflective an object is at different angles, referred to as the Fresnel  effect. Studio's fresnel processing aims for physical real-world accuracy, although you may get unexpected specular contribution at certain angles even with rough surfaces. In some cases, you can compensate by increasing your roughness map value by around 0.1  more rough to achieve a consistent lighting response with your materials.

Even though Roblox renders this lighting effect accurately, the brightness and reflectivity of a surface may not respond consistently between your texture content creating software, such as Substance Painter, and Studio. See [clothing examples](/docs/en-us/art/modeling/material-reference#clothing-examples)  for differences in rendering between applications.

Various combinations of the roughness and metalness can represent almost every possible real-world material surface. See [material references](/docs/en-us/art/modeling/material-reference)  for examples and references of how combinations of material values can create various surface appearances.

### [Metalness](#metalness)[](#metalness)

Metalness  determines the reflectivity of a surface. In most cases, you should set this value to either 0% (non-metal) or 100% (metal), although you can use partial metalness values when creating surfaces with moderate reflective properties like satin or silk. This practice can subtly fake the reflections in the material to highlight the color from the [color/albedo map](#color-albedo)  over colors reflected in the environment.

See the following figure for comparisons of various metalness map values:

![A brown sphere with light splotches.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Metalness-0.png) 0%

![A brown sphere with light splotches and some reflectiveness.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Metalness-Half.png) 50%

![A brown sphere with moderate splotches and lots of reflectiveness.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Metalness-1.png) 100%

Different PBR renderers use various workflows for processing reflectiveness. Studio only uses the metalness workflow  which determines whether a material is a nonmetal  or a metal , sometimes referred to as an insulator  or conductor .

Various combinations of the roughness and metalness can represent almost every possible real-world material surface. See [material references](/docs/en-us/art/modeling/material-reference)  for examples and references of how combinations of material values can create various surface appearances.

### [Emissive mask](#emissive-mask)[](#emissive-mask)

A grayscale [EmissiveMaskContent](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveMaskContent)  content texture applies an emissive mask  across the surface. This lets you use a texture to control emissiveness for more artistic control than the all‑or‑nothing [Neon](/docs/en-us/reference/engine/enums/Material#Neon)  material and allows you to create detailed glowing effects like illuminated text, futuristic armor, or bioluminescent creatures.

The associated [EmissiveTint](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveTint)  property determines the tinting color for emissive contribution, and [EmissiveStrength](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  determines the strength of emissive contribution.

You can use emissive masks on avatar items published to the Marketplace, not just objects inside experiences. This applies to 3D accessories and layered clothing, and to avatar bodies, where any single emissive body part classifies the whole body as an emissive item. 2D clothing doesn't support emissive qualities. Emissive support doesn't yet extend to makeup, though Face Makeup, Lip Makeup, and Eye Makeup will gain support for emissive qualities in a future update. Creating emissive items through In-Experience Creation (IEC) also isn't supported at launch and is planned as a follow-up release. Items published to the Marketplace must keep [EmissiveStrength](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  between 0 and 40 to pass validation.

![An orange sphere with a jack-o-lantern emissive mask at 50% strength.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/EmissiveStrength-Half.png)[EmissiveStrength](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  at 50%

![An orange sphere with a jack-o-lantern emissive mask at 100% strength.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/EmissiveStrength-Full.png)[EmissiveStrength](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  at 100%

![An orange sphere with a jack-o-lantern emissive mask tinted to magenta.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/EmissiveTint-Magenta.png)[EmissiveTint](/docs/en-us/reference/engine/classes/SurfaceAppearance#EmissiveTint)  = [255, 0, 255]

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
