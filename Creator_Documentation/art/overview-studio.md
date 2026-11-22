<!-- Source: https://create.roblox.com/docs/en-us/art/overview-studio -->

3D art and Studio | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/overview-studio.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Assets](/docs/en-us/assets)

# 3D art and Studio

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/overview-studio.md)

[Roblox Studio](/docs/en-us/studio/setup)  includes free powerful 3D creation tools that enable you to effectively contribute to asset creation, world building, and more. Whether you are just getting started, or are looking for a refresher on Studio tools, this guide provides an overview on using Studio for 3D art creation.

Each of the following sections include a brief description as well as additional links for further learning:

-

[Basic layout of Studio's interface](#studio-interface)  — Familiarize yourself with the various panels and tools available in Studio to navigate effectively.

-

[How to use assets and packages](#assets-and-packages)  — Learn to import, edit, and share assets and packages to enhance your workflow and collaboration.

-

[3D modeling within Studio](#3d-modeling)  — Explore the fundamentals of creating and importing 3D models within Studio.

-

[Materials and textures](#materials-and-textures)  — Discover how Roblox uses materials and textures with your models to enhance the surface appearance of your objects.

-

[Environments](#environments)  — Craft immersive environments using terrain tools, lighting effects, and atmospheric elements.

## [Studio interface](#studio-interface)[](#studio-interface)

After [installing Studio](/docs/en-us/studio/setup) , familiarize yourself with Studio's many 3D art tools and interfaces. While you can customize Studio to show various layouts and tools, Studio opens with the most commonly used windows by default.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Studio-Layout.png)

-

[Viewport](/docs/en-us/studio/overview#3d-viewport)  — Represents the workspace of a place. The items here are rendered similarly to how a user may view the environment they were to play your game.

-

[Explorer](/docs/en-us/studio/explorer)  — Shows a hierarchical list of all objects and services in a place. This includes visible objects, like parts and lights, and non-rendered objects like scripts, sounds, and folders.

-

[Properties](/docs/en-us/studio/properties)  — Populates all the properties of a selected object such as size, position, material, and much more. Many properties can be set through this window, or programmatically through a script.

-

[Toolbox](/docs/en-us/projects/assets/toolbox)  — Contains a selection of [models](/docs/en-us/parts/models) , [images](/docs/en-us/parts/textures-decals) , [meshes](/docs/en-us/parts/meshes) , [audio](/docs/en-us/audio/assets) , [plugins](/docs/en-us/studio/plugins) , [videos](/docs/en-us/ui/video-frames) , and fonts made by Roblox or Roblox community members.

-

[Asset Manager](/docs/en-us/projects/assets/manager)  — Lets you manage [places](/docs/en-us/production/publishing/publish-games-and-places)  and bulk import assets into your game.

-

[Output](/docs/en-us/studio/output)  — Displays all error, warning, or manually returned messages from the Roblox engine. This window is useful for troubleshooting behavior in your game.

For more information on the Studio interface and individual tools, see the [Studio overview](/docs/en-us/studio) .

## [Assets and packages](#assets-and-packages)[](#assets-and-packages)

Before you begin creating, it's important to understand how Roblox handles assets  and packages , the most basic object or group of objects that you can save, use, and share.

-

[Assets](/docs/en-us/projects/assets)  are a cloud-based version of an object that you can access any time to use, share, and modify. You can make nearly any object into an asset, such as a prop, building, character, sound, image, script, and more.

-

[Packages](/docs/en-us/projects/assets/packages)  are the Roblox equivalent of Unity Prefabs  or Unreal Blueprints , or a group of assets bundled together to reuse in one or more games. Packages can update and propagate their changes to any of their copies across one or more games, letting you take advantage of powerful versioning and asset management controls. Roblox recommends that most developers work with packages whenever possible.

All assets and packages save to your account's [Toolbox](/docs/en-us/projects/assets/toolbox)  for you or any associated [groups](/docs/en-us/projects/groups)  to access. You can also manage your saved assets and packages in the Creations  section of your [Creator Dashboard](https://create.roblox.com/dashboard/creations?activeTab=Model) .

You can also upload your assets to share on the [Creator Store](#creator-store) , and sell certain avatar assets to Roblox's [Marketplace](#marketplace)  for users to purchase and equip.

### [Creator Store](#creator-store)[](#creator-store)

The [Creator Store](/docs/en-us/production/creator-store) , accessible through the [web](https://create.roblox.com/store/)  and directly inside Studio's [Toolbox](/docs/en-us/projects/assets/toolbox) , contains millions of assets by Roblox and the Roblox community for use in Studio and your games. Anyone can contribute their assets to the store, including models, images, meshes, audio, plugins, and more.

Roblox also provides [free high quality assets](https://create.roblox.com/store/models?creatorName=Roblox) , many of which are used in the following showcases:

#### [Mystery of Duvall Drive](https://www.roblox.com/games/7902470429/The-Mystery-of-Duvall-Drive)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/overview/overview.png) ⟩ [Behind-the-scenes](/docs/en-us/resources/the-mystery-of-duvall-drive) ⟩ [Official model packs](https://create.roblox.com/store/models?creatorName=Roblox&includeOnlyVerifiedCreators=true&keyword=duvall+drive&pageNumber=1&querySource=0)

#### [Beyond the Dark](https://www.roblox.com/games/7208091524/Beyond-the-Dark-Vistech-Showcase)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Creature_Banner.png) ⟩ [Behind-the-scenes](/docs/en-us/resources/beyond-the-dark) ⟩ [Official model packs](https://create.roblox.com/store/models?creatorName=Roblox&includeOnlyVerifiedCreators=true&keyword=beyond+the+dark&pageNumber=1&querySource=0)

#### [Realistic Forest Demo](https://www.roblox.com/games/5326950832/Roblox-Realistic-Forest-Demo)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Intro-After.png)

### [Marketplace](#marketplace)[](#marketplace)

The Marketplace  is where all Roblox users can purchase virtual cosmetics, such as accessories and clothing, and various character bodies that they can save to their Roblox account and set as their Roblox avatar character.

To sell assets on the Marketplace, your creation must follow specific avatar specifications and meet certain policies and guidelines. For more information, see [Avatar](/docs/en-us/avatar)  and [Marketplace](/docs/en-us/marketplace) .

## [3D modeling](#3d-modeling)[](#3d-modeling)

3D modeling is the process of creating three-dimensional digital representations of objects or environments. Roblox supports [basic 3D modeling](#basic-parts)  in Studio, using primitive parts and allowing you to combine, subtract, and intersect the basic parts into more complex models.

Roblox also supports [custom 3D models](#mesh-parts)  created from 3D modeling software such as Maya and Blender. This includes advanced support for custom models and meshes that include modern textures, animation, and avatar-related features.

![A single gray sphere part](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Basic sphere part

![A bright blue hollow bowl that was made with solid modeling operations.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Part-Example-CSG.jpg) Bowl created with solid modeling

![A high-quality treasure chest mesh with a texture.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Mesh-Example.jpg)[Mesh](#mesh-parts)  with texture

### [Basic parts](#basic-parts)[](#basic-parts)

Studio natively supports basic parts that allow you to quickly add simple geometry to your game. This is ideal for creating simple environments or even greyboxing or prototyping a more complex 3D space.

Basic parts include the following benefits:

-

You can quickly add and modify parts directly in Studio.

-

Parts are performant and work well with Roblox's native physics behavior.

-

You can quicly modify the surface appearance of parts using materials and textures.

-

In many cases, a mix of basic parts and advanced custom mesh and models can work together to quickly create an immersive and performant environment.

For more information on using basic parts, as well as solid modeling operations, see [Parts](/docs/en-us/parts) .

### [Mesh parts](#mesh-parts)[](#mesh-parts)

Meshes are collections of vertices, edges, and faces that make up a 3D object. Unlike parts, which you can directly create in Studio, you first create meshes in a third-party modeling application like Blender or Maya before importing the model file into Studio. After importing a mesh, Studio represents the mesh object as a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

![A Roblox avatar wearing a glossy puffy jacket and jeans](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png) Create custom accessories, clothing, and characters that anyone can wear and use.

![A floating alien creature in space, from the Beyond The Dark game](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Beyond-The-Dark-Example.png) Design a custom character unique to your game.

![A cluttered interior room with a candle in the forefront and spooky interior lighting from the Mystery of Duvall Drive game](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mystery-of-Duvall-Example.png) Use custom meshes and models to give your environments ambiance and depth.

For more information on creating custom meshes, see [Custom meshes](/docs/en-us/art/modeling) .

## [Materials and textures](#materials-and-textures)[](#materials-and-textures)

It's always important to consider the surface appearance of your objects, as this empowers you to create cohesive and engaging assets and environments. Studio includes many tools to manage the look and feel of your assets, primarily by customizing your objects with [materials](#materials)  and [textures](#textures) .

### [Materials](#materials)[](#materials)

Materials allow you to quickly set the visual and physical properties of objects. While Roblox provides dozens of preset materials that you can set your parts to, you can also use the [Material Generator](/docs/en-us/parts/materials#material-generator)  to create your own custom materials using a prompt.

![](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Material-Generator-Example-1A.jpg)

![](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Material-Generator-Example-1B.jpg)

![](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Material-Generator-Example-1C.jpg)

![](https://prod.docsiteassets.roblox.com/assets/modeling/materials/Material-Generator-Example-1D.jpg)

Materials generated by [Material Generator](/docs/en-us/parts/materials#material-generator)  using a natural language prompt

Materials also affect physical properties beyond appearance. See [Materials](/docs/en-us/parts/materials)  for more information.

### [Textures](#textures)[](#textures)

Textures are 2D images that you can apply to the surface of an object to change its appearance. Unlike materials, textures are purely visual and never affect the physical properties of the object. In general, you create texture images with third-party software and import them into Studio directly as image files, or baked-in with an imported custom 3D object. You can also use Studio's [Texture Generator](/docs/en-us/studio/texture-generator)  to create brand new textures for your mesh using a natural language prompt.

![](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Example.png) A mesh object sets the shape and geometry of the 3D object

![](https://prod.docsiteassets.roblox.com/assets/art/Basic-Texture-Example.png) A texture image map applies a surface appearance and color

![](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png) The mesh and texture combine to make a unique custom 3D object

Textures are different from user interface objects which can apply customizable text or an image to the [surface](/docs/en-us/ui/in-experience-containers)  of a part, like a billboard or computer screen.

There are two types of textures in Roblox, single image basic textures  and advanced PBR textures  that dynamically react to different lighting and environment scenarios. Whether creating assets directly for the [Creator Store](#creator-store)  or [Marketplace](#marketplace)  or designing content for a game, you should incorporate PBR textures whenever you need realistic and impressive surface textures.

Loading many unique PBR textures at once can affect performance in your game. When working with many similar meshes, you can save processing power and memory by using a single set of PBR textures and [modifying alpha channels in combination with your mesh object base colors](https://devforum.roblox.com/t/using-alpha-masks-in-color-maps-to-customizetint-base-colors) .

For additional tips on improving performance with your assets, see [Improve performance](/docs/en-us/performance-optimization/improve#rendering) .

![A humanoid avatar with dreadlocks, a glossy jacket, jeans with decals, and boots.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png) A character model wearing cosmetic assets with PBR textures.

![A realistic leafy bush](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg) An environmental prop with PBR textures.

For more information see [Textures and decals](/docs/en-us/parts/textures-decals)  and [PBR textures](/docs/en-us/art/modeling/surface-appearance) .

## [Environments](#environments)[](#environments)

Environments refer to the visual and spatial world within your game. Environments are a combination of elements, such as [terrain](#terrain) , [lighting](#lighting) , architecture, effects, and more. Roblox provides many tools and services to quickly create high definition environments to elevate your games.

### [Terrain](#terrain)[](#terrain)

Terrain  refers to the landscape or outdoor environment of a Roblox game. Features such as mountains, valleys, hills, bodies of water, and vegetation all make up terrain. To quickly generate terrain, Studio provides a [Terrain Editor](/docs/en-us/studio/terrain-editor)  that allows you to quickly create various types of environments, such as mountains, grass-colored hills, deserts and more.

While many games include interior spaces, such as a city building or spaceship, it's important to use terrain for outdoor environments whenever possible to ensure performance and expected lighting and environmental behavior.

For more information, see [Environmental terrain](/docs/en-us/parts/terrain) .

### [Lighting](#lighting)[](#lighting)

 ![A campfire in a glade with a setting sun in the background illuminating the campsite.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Intro-After.png)

Lighting  refers to the illumination and visual effect applied to the environment and objects in your game. It plays a crucial role in setting the mood, atmosphere, and general visual quality of your creations.

Lighting can be categorized into the following:

-

Global lighting  — Refers to the luminescence from either the sun or moon in an outdoor environment. You can set the properties of your global lighting by adjusting the [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service. For additional hands-on instructions on adjusting global lighting, see the [Customize global lighting](/docs/en-us/tutorials/curriculums/core/building/customize-global-lighting)  lesson of our Core Curriculum.

-

Local lighting  — Refers to light sources placed within your games, such as pointlights, spotlights, and surface lights. You can modify lighting scenarios based on different interior rooms or sections of your game by using one or more light sources.

For additional information on modifying your environment's lighting, see [Global lighting](/docs/en-us/environment/lighting) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
