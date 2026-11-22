<!-- Source: https://create.roblox.com/docs/studio/texture-generator -->

Texture Generator | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/texture-generator.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Studio](/docs/en-us/studio)

# Texture Generator

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/texture-generator.md)

The Texture Generator  tool is designed to quickly create custom textures for your meshes through text or image prompts. You can select a mesh or [Model](/docs/reference/engine/classes/Model)  made up of several meshes¹, describe the look you want, preview results within a few seconds, then generate a full texture.

Two generation modes are available depending on your needs:

-

Fast  mode produces a quick 1K diffuse texture, ideal for rapid iteration.

-

Quality  mode generates a 4K physically based rendering (PBR) texture when you want higher fidelity and can wait a bit longer.

![Side-by-side Fast and Quality floral guitar textures](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_flower_guitar.jpg) Floral texture — Fast  (left) vs Quality  (right)

![Side-by-side Fast and Quality wood-grain guitar textures](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_wooden_guitar.jpg) Wood grain — Fast  (left) vs Quality  (right)

![Side-by-side Fast and Quality rusted guitar textures](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_rusted_guitar.jpg) Rusted metal — Fast  (left) vs Quality  (right)

![Side-by-side Fast and Quality tiger-stripe guitar textures](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_tiger_guitar.jpg) Tiger stripe — Fast  (left) vs Quality  (right)

Texture Generator  is best suited for custom 3D assets where the desired texture is contextual to the asset itself. To generate repeating or tiled images for texturing surfaces like a wood floor or cobblestone pathway, [Material Generator](/docs/studio/material-generator)  might produce better results.

 1  When generating a texture for a [Model](/docs/reference/engine/classes/Model)  group of [MeshParts](/docs/reference/engine/classes/MeshPart) , the meshes should be arranged in a sensible way such that a unified body is formed. Avoid generating a texture for an arbitrary group of meshes scattered about the model's bounds, or for more than one identical mesh in the same operation.

## [Generate textures](#generate-textures)[](#generate-textures)

You can generate textures through the Studio tool, through Assistant with the [/generate_texture  command](/docs/assistant/guide) , or through [Roblox Studio MCP](/docs/studio/mcp) .

To use the Studio tool:

1.

In Studio, select a mesh in your scene. The Texture Generator is only available when a mesh is selected.

2.

Go to the Model  tab and select Texture . The tool opens in a pop-up window beside the selected mesh.

 ![Texture generation tool open beside an untextured guitar mesh](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/untextured_guitar_texture_tool_open.jpg)

3.

In the tool pop-up window, choose one of two ways to describe the texture you want:

-

Text prompt : Enter a text description in the text box.

-

Image prompt : Click the +  button to upload a reference image.

 ![Texture generation prompting window with a text box, plus button, and Preview button](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_tool_initial_window.jpg)

4.

OPTIONAL

 Before clicking Preview , open the ⋯  menu and select View , then choose how the tool sets the preview orientation:

 ![View selection menu with Automatic and Manual options](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texturing_tool_view_selection_mode.jpg)

-

Manual : The viewing angle in the Studio viewport defines the mesh orientation for the preview images. Orbit around the mesh to choose your preferred view before clicking Preview .

-

Automatic : The tool uses a smart algorithm to choose a preview orientation without user input. This algorithm finds a view that exposes the most relevant parts of the mesh, although it can fail.

5.

Click Preview  to create texture previews. The tool returns three preview images in about 10 seconds.

 ![Three texture previews, with the hovered preview enlarged](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texturing_tool_preview_selection.jpg)

Generating previews again with the same prompt can produce slightly different results. Refining the prompt is usually the easiest way to get a meaningfully different set of images.

6.

From the dropdown in the preview window, choose a generation mode:

-

Fast  mode generates a 1K diffuse texture in under 30 seconds. Use Fast  for rapid prototyping, background assets, and simple assets that don't need sharp details.

-

Quality  mode generates a 4K PBR texture with sharper details. Generation can take a couple of minutes, and because the texture is sharper, small generation artifacts can also be easier to see.

7.

When you're satisfied with the preview, click Generate  to create the full texture for your mesh. You can keep working on other parts of your experience while generation runs, including texturing other assets at the same time.

Don't modify the asset in place while texture generation is running. Editing it before generation completes can cause the process to fail.

When generation finishes:

-

Fast  mode applies the texture directly to the [MeshPart](/docs/reference/engine/classes/MeshPart)  by attaching a new texture ID.

-

Quality  mode applies the PBR texture through a [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  parented to the [MeshPart](/docs/reference/engine/classes/MeshPart) .

If the asset contains multiple separate [MeshPart](/docs/reference/engine/classes/MeshPart)  objects, each one gets its own texture. In Quality  mode, each [MeshPart](/docs/reference/engine/classes/MeshPart)  also gets its own [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance) .

If you're unsatisfied with the final textured result, press Ctrl / Cmd  + Z  to undo. This can get more complicated if you're also working on other parts of your scene while texturing is in progress, so consider backing up your assets before using this tool.

### [Compare generation modes](#compare-generation-modes)[](#compare-generation-modes)

From far away, Fast  and Quality  results can look similar. Up close, though, Quality  mode's 4K PBR textures show sharper material detail, clearer patterns, and more surface variation than Fast  mode's 1K diffuse textures.

Floral pattern close-up:

![Close-up of a Fast mode floral guitar texture](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_flower_fast.jpg) Fast

![Close-up of a Quality mode floral guitar texture](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_flower_quality.jpg) Quality

Rusty pattern close-up:

![Close-up of a Fast mode rusty guitar texture](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_rusted_fast.jpg) Fast

![Close-up of a Quality mode rusty guitar texture](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_rusted_quality.jpg) Quality

## [Prompting tips](#prompting-tips)[](#prompting-tips)

The following tips help the tool provide better and more consistent results.

### [Text prompts](#text-prompts)[](#text-prompts)

Provide as much detail as possible in your prompt. Short, vague prompts can lead to inconsistent or unexpected results. Include texture attributes like material types, colors, patterns, and other distinctive features.

The more constraints you give the tool, the better it can generate what you have in mind.

Examples of simple and detailed prompts:

-

Simple prompt:  make it out of wood

-

Detailed prompt:  Acoustic guitar made from deep reddish-brown cherry wood with realistic wood grain, a deep blue fretboard, golden tuning pegs, and a leopard print pickguard.

![Side-by-side results from a simple wood prompt and a highly detailed guitar prompt](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_2_simple_v_detailed_prompt.jpg) Simple prompt  vs Detailed prompt

The system automatically enhances simple prompts with additional details of its own choosing, so you can spend more or less time writing your prompts. You can also start with a simple prompt, evaluate the preview images, and then refine the prompt until you achieve a result you like.

Avoid the following when writing a prompt:

-

Changing the mesh geometry

-

Referencing the current texture on the mesh

-

Referencing objects or terrain in other parts of the scene

-

Referencing previously generated textures

-

Describing the reflectivity or transparency properties of the texture

### [Image prompts](#image-prompts)[](#image-prompts)

When you provide an image prompt, the texture generation tool treats it as a style guide rather than an exact template. The generated texture draws inspiration from the reference image, but might not preserve every detail.

![Image prompt: a guitar painted with a dragon, a samurai, and red maple leaves](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/style_guidance_japanese_guitar.jpg) Image prompt

![Guitar mesh with a generated texture of dragons, samurai, and red maple leaves](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_2_japanese_guitar.jpg) Generated texture

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
