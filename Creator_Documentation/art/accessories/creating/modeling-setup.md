<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/creating/modeling-setup -->

Modeling setup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/accessories/creating/modeling-setup.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Modeling setup

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/accessories/creating/modeling-setup.md)

Modeling, sometimes known as sculpting , is the process of creating and shaping the 3D geometry of an object. In this tutorial, you will use one of Roblox's template files to create the initial shape of a t-shirt, then add unique and clothing-specific modifications to its geometry for your own design. You can further apply the techniques and processes in this tutorial to create any other type of clothing, such as pants, skirts, and shoes.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Mannequin-Start.png) Base Mannequin using Roblox provided cage meshes

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Complete-2.png) Sculpted clothing mesh for a long sleeve shirt

The next four modeling sections cover the following processes:

1.

Setting up your project and creating your base mesh.

2.

Clearing the duplicated mesh of extra attributes.

3.

Trimming the shape to match the desired clothing type.

4.

Adding and smoothing the vertices of your clothing shape.

5.

Scaling and positioning the clothes onto the mannequin.

6.

Sculpting fabric and other details onto the mesh object.

7.

Closing the holes in your mesh, making it watertight.

## [Set up mesh](#set-up-mesh)[](#set-up-mesh)

To get your project started, download and open Roblox's Clothing_Cage.blend  project and begin setting up your basic project objects.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Cages-Selected.png) 3D viewport - duplicated cage mesh object

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Cage-Copied.png) Outliner - duplicated object named "LongSleeve"

To set up your project and your initial mesh object:

1.

Download and open the [Clothing_Cage.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip)  project that includes the inner and outer cage mesh that you will use as temporary mannequins.

2.

Navigate to File  > Save As , then save the project with a new name. This will be your main Blender project for your layered accessory.

3.

In the Outliner, copy and paste InnerCage  object to duplicate it.

4.

With the duplicated object active, right-click in the viewport, then select Parent  > Clear and Keep Transformation  from the contextual menu.

5.

Back in the Outliner,

1.

Right-click and delete the extra Clothing Cages.001  object.

2.

Rename the duplicated object as LongSleeve .

3.

Rename the original cages as LongSleeve_OuterCage  and LongSleeve_InnerCage , respectively, then hide them for now.

## [Clear extra attributes](#clear-extra-attributes)[](#clear-extra-attributes)

The cage mesh objects in the template include some helper vertex color properties that need to be removed from your clothing mesh. If left in, the vertex colors may clash with the texture of the object after importing in Studio.

To remove extra attribute data:

1.

With LongSleeve  active, navigate to the Properties Editor > Object Data Properties  tab > Color Attributes .

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Clear-Vertex-Colors.png)

2.

With colorSet1  selected, remove it by pressing the –  button.

[Next](/docs/en-us/art/accessories/creating/trimming)[Previous](/docs/en-us/art/accessories/creating)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
