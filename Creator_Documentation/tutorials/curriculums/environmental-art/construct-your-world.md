<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/environmental-art/construct-your-world -->

Construct your world | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/environmental-art/construct-your-world.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Construct your world

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/environmental-art/construct-your-world.md)

Constructing your world , also known as worldbuilding, is the process of decorating the environment with polished assets from your asset library, then adding and configuring additional elements of the 3D space to bring your world to life. This exciting step of the workflow is where you get to see all of your vision and hard work come together into a cohesive environment that is complete and ready for publication.

Using the [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  .rbxl  file as a reference, this section of the environmental art curriculum shows you how to use and apply your high quality assets and custom materials to your greybox geometry in a way that differentiates each distinct area of the team-based first-person laser tag shooter game, including step-by-step instructions on:

-

Applying your asset library to the building's architecture and outdoor space to provide users information about the overall world.

-

Sculpting terrain with your custom tileable textures to create the overall island that the building rests on.

-

Containing the playable areas to ensure users remain in combat without falling off the island.

-

Configuring special effects and lighting sources to enrich the 3D space with movement, warmth, and realism.

After you complete this section, you will learn how to review and configure your content to ensure your game has optimal performance across devices.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Overview.png)

The instructions in this section of the tutorial show you how to exactly  recreate the sample final environment using the [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library) , which takes about 90 minutes or less from start to finish. If you don't want to use the provided coordinates, you can adjust the geometry however you need to meet the specifications of your own game, or use the sample itself for the rest of the tutorial.

## [Apply your asset library](#apply-your-asset-library)[](#apply-your-asset-library)

The first step in constructing your environment is to apply your asset library to the 3D space, and this process often falls into one of the following categories of work:

-

Applying your asset library directly onto the greybox geometry to exactly match the original design.

-

Converting the greybox geometry into something else entirely that still respects the intention behind the original design.

-

Converting the greybox geometry into something else while also applying your asset library to the new object to maintain cohesion throughout the environment.

The process between greyboxing and constructing your environment with your asset library hardly ever looks like a straight line from your original design to the final art. Iteration between each step and across steps is normal and almost always necessary in the development process as you find new ways to improve the user's experience in your world. For example, the guidance in the Floors  section converts the original floor greybox geometry into new divisions in order to better orient users to where they are in the building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ApplyingLibraryDiagram.png)

As you follow these instructions that exactly recreate the final environment within the sample [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  .rbxl  file, observe how each step works together to add character to the environment, and provide users information about the overall world. You can adjust any part of the process to meet the specifications of your own game , as your environment may have different needs according to the world that you're creating.

### [Floors](#floors)[](#floors)

The original greybox design for floors was to divide the building into two halves, one for each team. This was useful to help visualize each half as its own space for its respective team, and to delineate the center of the map. However, as you begin to construct your environment, you may find that walls can fulfill this purpose more effectively, and that floors are more useful to help orient users to where they are in relation to the exterior of the building.

For example, the final sample laser tag environment uses new floor pieces with unique materials to inform users whether they're navigating somewhere inside the building, or approaching its outdoor space. When a user is inside of the building, they walk on surfaces with the GlossyTiles  [MaterialVariant](/docs/en-us/reference/engine/classes/MaterialVariant) , and when they're walking in the middle courtyard or under the overhang pieces you will make later in this tutorial, they walk on surfaces with the Concrete_Tiles_A  [MaterialVariant](/docs/en-us/reference/engine/classes/MaterialVariant) . You can find both of these materials in the sample [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Floors-Intro.jpg)

While this technique replaces and converts the original greybox geometry, it still respects the intention behind the original design to create peaks and valleys that control sight lines and engagement distances throughout the game outside of horizontal movement. This means that users retain all physical and emotional senses of ascension and descension while also having the benefit of knowing where they are in the 3D space.

Create your own Recreate the sample

To apply your own asset library to the floors:

1.

Using block  parts, create symmetrical surfaces for your indoor floors.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-1.jpg)

2.

Using wedge  parts, create a rise in elevation  between the main and mezzanine floors on the inside of your building.

3.

Select these indoor parts, then in the Properties  window, set Color , Material , and/or MaterialVariant  to values that apply a distinct visual treatment from other surfaces in your environment. This allows players to always know they are within the building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-2.jpg)

4.

Using block  parts, create symmetrical surfaces for your outdoor floors .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-3.jpg)

5.

Using wedge  parts, create a rise in elevation  between the main and mezzanine floors on the outside of your building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-4.jpg)

6.

Using block  or wedge  parts, create a drop in elevation between the main and outdoor floors on the outside of your building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-5.jpg)

7.

Select these outdoor parts, then in the Properties  window, set Color , Material , and/or MaterialVariant  to values that apply a distinct visual treatment from other surfaces in your environment. This allows players to always know they are outside of the building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-6.jpg)

8.

Anchor all of these floor parts.

### [Spawn zones](#spawn-zones)[](#spawn-zones)

The original greybox design for spawn zones was to create an area at opposite ends of their map for users to join their respective team when the match starts. The placement of these spawn zones allows users to have a safe location at the start of the match that's far away from enemy fire.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/ThreeLaneLayout-SpawnZones.jpg)

The final sample laser tag environment keeps the intent of this design while also adding a color theme: mint  for the team that assembles on the left side of the map, and carnation pink  for the team that assembles on the right side of the map. You will continue to use this same color scheme throughout this section of the tutorial to differentiate areas of the map near each team's respective spawn zone.

Create your own Recreate the sample

To apply your own asset library to the spawn zones:

1.

Add and configure any applicable wall , corner , and door frame  modular assets to the inside of your left spawn zone .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/SpawnZones-1.jpg)

2.

Select your wall components, then in the Properties  window, set Color  to a unique  hue. You will continue to use this color throughout the rest of the map to orient players to their location relative to this team's color theme.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/SpawnZones-2.jpg)

3.

Repeat this process for your right spawn zone .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/SpawnZones-4.jpg)

4.

Anchor all of these spawn zone assets.

### [Combat pockets](#combat-pockets)[](#combat-pockets)

The original greybox design for the combat pockets was to create intentional spaces for combat where the map's primary lanes intersect with the cross lanes. In addition, the original greybox design required that each combat pocket needed to only include three entrance or exit points at most to refrain from giving users choice overload as they're navigating the space.

The final sample laser tag environment applies the sample [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  directly onto the greybox geometry to exactly match the original design while also using the color theme introduced in the previous section to differentiate areas of the map near each team's respective spawn zone. Using these colors and the floor material, users can quickly orient themselves to where they are no matter where they are around the building, respecting the original intention behind the greybox design for the building's floors.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-Intro1.jpg)

In addition, the technique in this section also applies props from the sample asset library to left and right combat pockets in order to add character to the environment and provide believability that it has life on its own even if users weren't present. This process, also called set dressing , provides users both direct and indirect information about the world they're visiting. For example, the signage and foliage props in this section reinforce the sample art style from [Develop Polishing Assets](/docs/en-us/tutorials/curriculums/environmental-art/develop-polished-assets) , and inform users that they're in a high-tech environment that still prioritizes organic life.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-Intro2.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-Intro3.jpg)

Create your own Recreate the sample

To apply your own asset library to the combat pockets:

1.

Add and configure any applicable props or wall , corner , door frame , and door  modular assets to the inside and outside of your left combat pocket .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralCombatPockets-1.jpg)

2.

Select your wall components on the outside of your left combat pocket, then in the Properties  window, set Color  to the same  hue as the left spawn zone's color theme. This allows players to orient themselves relative to this team's color theme as they are navigating primary and cross lanes.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralCombatPockets-2.jpg)

3.

Select your wall components on the inside of your left combat pocket, then in the Properties  window, set Color  to a unique  hue. This allows players to orient themselves when they are within the combat pocket and looking through exit points.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-6.jpg)

4.

Repeat this process for your middle combat pocket  and right combat pocket .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-16.jpg)

5.

Anchor all of these combat pocket assets.

### [Perimeter hallways](#perimeter-hallways)[](#perimeter-hallways)

By applying your asset library to the exterior of the combat pockets in the previous section, most cross lanes now include polished assets aside from the hallways that make up the perimeter of the building. In addition to using the same color scheme from previous sections, the final sample laser tag environment also uses wall assets with their default orange color to inform users where they are in relation to the back of the building.

For example, using the point-of-view in the following image, users immediately have the following information to orient themselves to where they are within the building:

-

The ribbed concrete  informs users that if they move left, then they will enter the middle combat pocket.

-

The yellow wall  informs users that if they move forward, then they will reach the back of the building and the interior primary lane.

-

The pink wall  informs users that if they move right, then they will enter the right combat pocket, and that they are nearest the right side of the map.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-Intro1.jpg)

Aside from this technique that applies the sample [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  directly onto the greybox geometry for the walls to exactly match the original design, it also adds geometry in the form of crate prop assets in order to provide users cover from enemy fire as they navigate the interior primary lane. This design iteration still respects the intention to break up sight lights and engagement distances with protruding hallway spaces and elevation changes.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-Intro2.jpg)

Create your own Recreate the sample

To apply your own asset library to the perimeter hallways:

1.

Add and configure any applicable prop or wall , corner , and door frame  modular assets to the perimeter hallways on the left-side  of the building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-1.jpg)

2.

Select your wall components, then in the Properties  window, set Color  to the same  hue as the left spawn zone's color theme.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-2.jpg)

3.

Add and configure any applicable prop or wall , corner , and door frame  modular assets to the perimeter hallways at the back  of the building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-4.jpg)

4.

Select your wall components, then in the Properties  window, set Color  to a unique  hue. This allows players to orient themselves relative to where they are in relation to the interior primary lane. The sample game keeps these assets their default color.

5.

Add and configure any applicable prop or wall , corner , and door frame  modular assets to the perimeter hallways on the right-side of the building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-5.jpg)

6.

Select your wall components, then in the Properties  window, set Color  to the same hue as the right spawn zone's color theme.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-6.jpg)

7.

Anchor all of these perimeter hallway assets.

### [Doors](#doors)[](#doors)

The final sample laser tag environment applies doors directly onto the greybox geometry to exactly match the original design, however, not all entrance or exit points have door assets. You may find that the requirements of your own game require more or less doors, depending on how you want to control combat within your combat pockets. More doors often leads to longer wait times before users enter or exit a combat pocket, but less doors may open up unwanted lines of sight.

For this reason, it's recommended to playtest with multiple variations to experiment different play styles. In fact, you may experiment with placing door assets into your combat pockets that only open to users from one side of the door, or not at all.

Create your own Recreate the sample

To apply your own asset library to the doors:

1.

Add and configure any door  modular assets to the doorways of your combat pockets.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Doors-2.jpg)

2.

OPTIONAL

 Anchor all of these door assets.

### [Exterior assets](#exterior-assets)[](#exterior-assets)

The original greybox design for exterior assets was to set placeholder positions for objects that provide cover from enemy fire while users navigate the exterior primary lane. This was useful to help visualize what would help users as they ascend or descend stairs, cross the middle combat pocket, or otherwise exist in the outdoor space, but as you construct your environment, you can improve this design by providing different uses for these cover objects.

The following sections provide guidance on how to convert these initial placeholder assets into aesthetically pleasing objects that follow your game's art style, and keep the intent behind the original design.

#### [Towers](#towers)[](#towers)

The first exterior assets you can convert for the outdoor space are the two towers right outside of the middle combat pocket that intersect with the exterior primary lane. The technique in this section not only creates objects that are aesthetically pleasing to the eye, but it also creates objects that provide users a sense of scale in their environment. Every other object so far is about the size of the user's character except  for these towers, which can lead to intrigue in the story behind the architecture or overall island that the building rests on.

Create your own Recreate the sample

To apply your own asset library to the towers:

1.

Using block  parts, create a tower that is much larger than the player to provide a sense of scale in the environment.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralTowers-1.jpg)

2.

Apply unique colors and materials to different block parts according to the art style of your game.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Towers-1.jpg)

3.

Duplicate this tower, then position it to a symmetrical location on your map.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Towers-3.jpg)

4.

Anchor all of these parts.

#### [Columns](#columns)[](#columns)

The second exterior assets you can convert for the outdoor space are the two columns that hold up the overhang pieces you will make later in this tutorial. Similar to the towers, the technique in this section not only creates objects that are aesthetically pleasing to the eye, but it also provides further visual cues to users about where they are in the overall environment. For example, each column has either mint or carnation pink detailing to inform users if they are closest to either their own or their enemy's spawn zone.

Create your own Recreate the Sample

1.

Using block  and wedge  parts, create a column that will hold the roof of your building.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralColumns-1.jpg)

2.

Apply unique colors and materials to different parts according to the art style of your game.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Columns-2.jpg)

3.

Duplicate this column, then position it to a symmetrical location on your map.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Columns-5.jpg)

4.

OPTIONAL

 Change the color of one part in each column to match each team's respective color theme.

5.

Anchor all of these parts.

#### [Planters](#planters)[](#planters)

The final exterior assets you can convert for the outdoor space are the eight planters that extend along the entirety of the exterior primary lane. Using [solid modeling](/docs/en-us/parts/solid-modeling)  operations, you can negate and join parts together to form the base of each planter, then apply your asset library using different materials, foliage, and/or trim asset configurations so that each one feels unique in the 3D space.

To apply your asset library to the left-most planter:

1.

Add and configure the following block  parts for the left-most planter:

| Part | | Size | | CFrame.Position |
| --- | --- |
| Planter exterior | | 20, 11, 5 | | -15, 4.5, 257.5 |
| Divot | | 18.5, 1, 4 | | -15, 9.75, 257.5 |

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-1.jpg)

2.

Select the divot part.

3.

Navigate to Studio's Model  tab toolbar, then click the Negate  button. The part turns translucent.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-3.jpg)

4.

Select both the negated part and the planter exterior part.

5.

In Studio's Model  tab toolbar, click the Union  button. The negated part is cut out from the overlapping planter exterior part.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-5.jpg)

6.

Select the union, then in the Properties  window,

1.

Set Color  to 181, 173, 156 .

2.

Set Material  to Concrete .

3.

Set MaterialVariant  to Concrete_Board_Formed_A .

4.

Enable UsePartColor .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-6.jpg)

7.

Add and configure the following block  parts for the dirt and edging of the planter:

| Part | | Size | | CFrame.Position | | CFrame.Orientation | | Color | | Material | | MaterialVariant |
| Dirt | | 19, 0.5, 4 | | -15, 9.25, 257.5 | | 0, 0, 0 | | 248, 248, 248 | | LeafyGrass | | Moss_Lumpy_Stones_A |
| Top planter edging | | 1.652, 1, 6.483 | | -24.838, 5.298, 257.741 | | 0, 0, 0 | | 181, 173, 156 | | Concrete | | Concrete_Tie_Holes_A |
| Bottom planter edging | | 6.483, 1.5, 19.652 | | -15.154, 1.479, 257.758 | | 0, 0, -21.62 | | 181, 173, 156 | | Concrete | | Concrete_Tie_Holes_A |

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-7.jpg)

8.

Add foliage assets to the top of the planter to the top of the planter to add more organic life to the outdoor space.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-8.jpg)

9.

Anchor all of these parts and foliage assets.

Now that you know how to use the solid modeling tools, you can experiment in creating types of planters with different exteriors, materials, plant variety, and trim pieces. For example, the other variations of planters within the final sample laser tag environment either make an 'L' shape, or they layer block  parts and white trim together to provide higher cover in the middle of the map.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-9.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-10.jpg)

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-11.jpg)

### [Roof](#roof)[](#roof)

The original greybox design didn't include a roof to the building because it would have prevented you from seeing your progress as you designed and constructed your three lane map layout. However, now that the interior of the building is complete outside of configuring its light sources, you can apply your asset library to new geometry to finish the building and provide users shelter from the outdoor space.

The roof of the building is one of the most complex assets in the final sample laser tag environment because it includes multiple layers that must fit together with each other and with the interior geometry. The following instructions walk you through how to construct each layer, starting with the top-most geometry to the final layer of trim that surrounds the perimeter of the roof.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Roof-Intro.jpg)

#### [Skylights](#skylights)[](#skylights)

The first, top-most layer of the roof is the skylight geometry. The purpose of this layer is to provide outdoor light into interior combat areas.

Create your own Recreate the sample

To apply your own asset library to the skylights:

1.

Add and configure any skylight  modular assets to the ceiling of your building. This allows global lighting into combat areas, and provides a richer sense of immersion for players.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Skylight-5.jpg)

2.

Using block  parts, create glass for some of your skylights.

1.

Add and position a block  part into a skylight.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Skylight-6.jpg)

2.

Select the part, then in the Properties  window,

1.

Set Color  to 105, 162, 172 .

2.

Set Material  to Neon .

3.

Set Transparency  to 0.6 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Skylight-7.jpg)

3.

Anchor all of these skylight assets.

#### [Ceiling](#ceiling)[](#ceiling)

The second layer of the roof is the ceiling geometry that users see at the top of their view as they navigate the interior of the building. The purpose of this layer is to fill the open areas between the top trim of each wall asset.

Create your own Recreate the sample

To apply your own asset library to the ceiling of the roof:

1.

Using block  and wedge  parts, fill in the open space around your skylights.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Ceiling-3.jpg)

2.

Select these parts, then in the Properties  window, set Color , Material , and/or MaterialVariant  to values that apply a distinct visual treatment from other surfaces in your environment. This helps players orient themselves when they are moving their camera quickly.

3.

Anchor all of these ceiling assets.

#### [Top roof](#top-roof)[](#top-roof)

The third layer of the roof is the top roof geometry. The purpose of this layer is to provide bulk to the outermost roof area that users see as they look at the building from the outdoor space. It also adds a sense of depth to the skylights, making the building look more complete from the inside and out.

Create your own Recreate the sample

To apply your own asset library to the top of the roof:

1.

Using block  and wedge  parts, add in a thick layer to cover the ceiling without hiding your skylights. This surface is what players can see when they are looking at the building from the outdoor space.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/TopRoof-3.jpg)

2.

Select these parts, then in the Properties  window, set Color , Material , and/or MaterialVariant  to values that apply a visual treatment according to the art style of your game.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/TopRoof-4.jpg)

3.

Anchor all of these top roof assets.

#### [Overhang](#overhang)[](#overhang)

The fourth layer of the roof is the overhang geometry that the column assets hold up in order for the building to be structurally sound. The purpose of this layer is to provide an aesthetically pleasing awning space for users navigating the exterior primary lane.

Create your own Recreate the sample

To apply your own asset library to the overhang of the roof:

1.

Using block  and wedge  parts, add in a thick overhang for your columns to hold up. This surface provides players partial cover from the sun while they are navigating the exterior primary lane.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Overhang-4.jpg)

2.

Select these parts, then in the Properties  window, set Color , Material , and/or MaterialVariant  to values that apply a visual treatment according to the art style of your game.

3.

Anchor all of these overhang parts.

#### [Trim](#trim)[](#trim)

The final layer of the roof is the trim geometry that surrounds the perimeter of the roof. The purpose of this layer is to provide visual cohesion between each previous layer from users looking at the room from the outdoor space.

Create your own Recreate the sample

To apply your own asset library to the trim of the roof:

1.

Add and configure trim  modular assets along the overhang of your roof.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Trim-5.jpg)

2.

Select these parts, then in the Properties  window, set Color , Material , and/or MaterialVariant  to values that apply a visual treatment according to the art style of your game.

3.

Anchor all of these overhang parts.

## [Delete excess geometry](#delete-excess-geometry)[](#delete-excess-geometry)

Now that your building is complete, it's time to delete the underlying greybox geometry and the baseplate. This process removes excess polygons that users will never see nor interact with, which quickly improves memory and performance for devices with memory and graphics processing unit (GPU) limitations. In addition, removing the baseplate also allows the building to float in the sky, which is good preparation for you to sculpt terrain for the outdoor space in the next section.

To delete excess geometry:

1.

In the Explorer  window, delete all greybox geometry from the first section of this tutorial.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DeletingGeo-1.png)

2.

Delete the baseplate object.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DeletingGeo-2.png)

## [Sculpt terrain](#sculpt-terrain)[](#sculpt-terrain)

Right now your environment is mostly architectural aside from foliage in your planters. However, following the sample art style from [Develop Polished Assets](/docs/en-us/tutorials/curriculums/environmental-art/develop-polished-assets) , the 3D space should contain a healthy mix of futuristic technology and lush greenery to inform users that the world values technological advances, but not at the expense of the earth.

Using the [Terrain Editor](/docs/en-us/parts/terrain) , you can quickly generate and sculpt detailed and realistic terrain to bring organic life to the outdoor space. Because you set material overrides as you created your custom materials in [Assemble an Asset Library](/docs/en-us/tutorials/curriculums/environmental-art/assemble-an-asset-library) , you can also utilize your tileable textures through Terrain Editor  brushes to add moss, flowers, and stone paths that are cohesive with the rest of your environment.

Sculpting terrain is an art form, and it's difficult to exactly recreate brush strokes and subtle material edits. As long as your terrain meets the needs of your own game, it's normal and expected for your environment to look and feel different from the sample laser tag environment.

Create your own Recreate the sample

To apply your own terrain to the outdoor area:

1.

From the toolbar's Home  tab, click Terrain . The [Terrain Editor](/docs/en-us/studio/terrain-editor)  window opens.

2.

Navigate to the Edit  tab, then click the Draw  button.

3.

In the Brush Settings  section, customize your brush according to the material you want to add to your map. For example, the sample starts this process with the settings in the following image.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Terrain-3.jpg)

4.

In the Materials Settings  section, select a material for the unplayable area , such as water or cracked lava, then in the viewport, draw where you want your playable area to end. This material communicates where the map ends for the outdoor space.

5.

Navigate back to the Materials Settings  section, select a material for the playable area , such as grass, pavement, or wood planks, then in the viewport, draw where you want your playable area to start. This material communicates where the map starts for the outdoor space

6.

Navigate back to the Terrain Editor , then select the Paint  tool.

7.

In the Brush Settings  section, customize your brush according to the material you want to add to your map, and select a new material.

8.

In the viewport, draw along the exterior lane. This material communicates the primary path players can take as they are navigating the outdoor space.

9.

(Optiona)  Add and configure any applicable props to the outdoor space for visual variation.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Terrain-10.jpg)

## [Contain the playable area](#contain-the-playable-area)[](#contain-the-playable-area)

If you playtest your game and navigate off the island, your character will fall until they reach the project's [Workspace.FallenPartsDestroyHeight](/docs/en-us/reference/engine/classes/Workspace#FallenPartsDestroyHeight)  and respawn back in your team's spawn zone. To ensure that users cannot fall off the island, or join the match too early from the floating area spawn zone before they separate into teams, you must contain the playable area with an invisible barrier.

The values in this section are highly dependent on the terrain within the final sample laser tag environment. It's recommended to playtest and verify that there are no gaps in the barrier according to the custom terrain within your own game.

Create your own Recreate the sample

To contain the playable area in your game:

1.

Using block  parts, surround the playable area in your outdoor area. It's important to ensure these parts are tall enough to block players from jumping over your barrier, and that there are no cracks they can slip through and fall off the edge of your map.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ContainingPlayableArea-1.jpg)

2.

Select these parts, then in the Properties  window,

1.

Set Transparency  to 1 .

2.

Disable CanCollide .

3.

Enable Anchored .

## [Configure special effects](#configure-special-effects)[](#configure-special-effects)

Your building's architecture and outdoor space are nearly complete with assets from your asset library, but you may have noticed either consciously or unconsciously that the overall environment feels static. This is because realistic environments include movement from many different sources, whether that's from clouds crawling through the sky, wind brushing through greenery, or life forms navigating the space.

You can mimic realistic environments by configuring special effects that add dynamic movement to your environment, and provoke emotion from users. This process often makes worlds feel more alive, supporting a deep sense of immersion while people access your game.

### [Background clouds](#background-clouds)[](#background-clouds)

The first type of special effect the final sample laser tag environment uses to add movement to the 3D space is an effect called dynamic clouds. [Dynamic clouds](/docs/en-us/environment/clouds)  are realistic clouds that drift slowly across the sky, and they are useful for creating movement that feels far away from the user while still present in the environment. You can adjust their appearance through the [Clouds](/docs/en-us/reference/engine/classes/Clouds)  object to create unique atmospheres, and customize their direction and speed through global wind.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-Intro1.jpg) Without dynamic clouds

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-Intro2.jpg) With default dynamic clouds

Create your own Recreate the sample

To add and configure your own dynamic clouds in the background:

1.

In the Explorer  window, add a Clouds  object to the Terrain  object.

1.

Hover over the Terrain  object and click the ⊕  button. A contextual menu displays.

2.

From the contextual menu, insert a Clouds  object.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-1.jpg)

2.

Select the Clouds  object, then in the Properties  window,

1.

Set Cover  to a value between 0  (no clouds) and 1  (full cloud cover).

2.

Set Density  to a value between 0  (light, translucent clouds) and 1  (heavy, dark clouds).

3.

Set Color  to a material color of cloud particles according to the art style of your game.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-2.jpg)

### [Foreground clouds](#foreground-clouds)[](#foreground-clouds)

The second type of special effect the final sample laser tag environment uses to add movement to the 3D space is an effect called particle emitters. [Particle emitters](/docs/en-us/effects/particle-emitters)  emit 2D images, or particles, that look and behave for the duration of their lifetime according to the particle emitter's set properties, and they are useful for creating movement that feels and often is close to the user.

Particle emitters have many properties you can adjust to achieve both subtle and bold effects. The following instructions show you how to exactly recreate the foreground clouds within the sample [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  place file, but you can modify any property for the needs of your own game. It's recommended to keep these clouds large and with a gentle motion between the gameplay space and the static background.

To add and configure foreground clouds:

1.

Add a block  part to a position where you want users to see a floating cloud.

2.

Select this block  part, then in the Properties  window,

1.

Set Transparency  to 1 .

2.

Disable CanCollide .

3.

Enable Anchored .

3.

Create a particle emitter within this part.

1.

In the Explorer  window, hover over the block  part and click the ⊕  button. A contextual menu displays.

2.

From the contextual menu, insert a ParticleEmitter . The particle emitter immediately emits particles within the part's area.

4.

Select this particle emitter, then in the Properties  window,

1.

Set Color  to a color sequence that looks like the following image.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ForegroundClouds-4a.png)

2.

Set LightEmission  to 0.3  to blend the colors of the texture and its environment.

3.

Set LightInfluence  to 0.2  to allow environment light to have a subtle effect on the color of particles.

4.

Set Orientation  to FacingCameraWorldUp  so particles always emit up toward the sky.

5.

Set Size  to 100  to create large clouds.

6.

Set Squash  to -0.25  to shrink particles horizontally.

7.

Set Texture  to an image of a cloud. The sample uses rbxassetid://10714362544 .

8.

Set Transparency  to a number sequence that looks like the following image.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ForegroundClouds-4b.png)

9.

Set Lifetime  to 30  to fade out particles at 30 seconds.

10.

Set Rate  to 0.25  to emit particles slowly.

11.

Set Acceleration  to 0, -0.8, 0  to impact particle speed over their lifetime.

12.

Set Drag  to 0.1  to make particles look their speed over time.

13.

Enable LockedToPart  to keep particles close to the particle emitter.

5.

Repeat this process, moving cloud particle emitters throughout the environment.

In addition, you can layer multiple particle emitters together to give clouds more depth. For example, in the final sample laser tag environment, foreground clouds layer an additional particle emitter with a Color  property of 248, 248, 248 , Texture  property of rbxassetid://10714433747 , and a Rate  property of 0.1 . You can find both of these particle emitters in the sample [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library) .

  ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ForegroundClouds-5.jpg)

### [Dust particles](#dust-particles)[](#dust-particles)

Particle emitters are such a versatile type of special effect because they offer so many properties you can customize to create interesting visual effects, such as glowing portals, green billowing smoke, or vibrant explosions. The final sample laser tag environment uses particle emitters again in this section to create floating dust particles that surround the user as they navigate the outdoor space.

Similar to the foreground clouds steps, the following instructions show you how to exactly recreate the dust particles within the sample [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  place file, but you can modify any property for the needs of your own game. It's recommended to keep particle speed slow to only provide micro motion within the environment.

To add and configure dust particles for the outdoor space:

1.

Add a block  part to the environment that covers the entire island.

2.

Select this block  part, then in the Properties  window,

1.

Set Transparency  to 1 .

2.

Disable CanCollide .

3.

Enable Anchored .

3.

Create a particle emitter within this part.

1.

In the Explorer  window, hover over the block  part and click the ⊕  button. A contextual menu displays.

2.

From the contextual menu, insert a ParticleEmitter . The particle emitter immediately emits particles within the part's area.

4.

Select this particle emitter, then in the Properties  window,

1.

Set Color  to 192, 241, 255  to give the particles a light blue hue.

2.

Set Size  to a number sequence that looks like the following image.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DustParticles-4b.png)

3.

Set Texture  to a dust mote image. The sample uses rbxassetid://14302399641 .

4.

Set Transparency  to a number sequence that looks like the following image.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DustParticles-4d.png)

5.

Set ZOffset  to -5  to move particles away from the camera.

6.

Set Lifetime  to 1, 10  to set the minimum and maximum age of a particle to 1 and 10 seconds, respectively.

7.

Set Rate  to 50000  to create many particles for your environment.

8.

Set RotSpeed  to -60  to create a range of speeds for newly emitted particles.

9.

Set Speed  to 1, 5  to set the minimum and maximum speed of a particle to 1 and 5 studs per second, respectively.

10.

Set Acceleration  to 1, -1, 1  to impact particle speed over its lifetime.

11.

Enable LockedToPart  to keep particles close to the particle emitter.

## [Configure lighting sources](#configure-lighting-sources)[](#configure-lighting-sources)

Now that your environment has movement, the final step in constructing your environment is to configure lighting sources. Studio offers two high-level types of lighting sources:

-

Global lighting  - Produces lighting for the entire outdoor environment.

-

Local lighting  - Produces lighting around where you place them within your game.

Both lighting sources are important to consider because your game has both an indoor and outdoor environment that impact the user's ability to see what is happening around them while they're in combat.

### [Global lighting](#global-lighting)[](#global-lighting)

Global lighting is the luminescence from either the sun or moon in a game. By adjusting a couple of key default properties in the [Lighting](/docs/en-us/reference/engine/classes/Lighting)  service, you can dramatically change how that light appears to users, as well as how it interacts with any other object you place in the game.

Studio begins every game with [Soft](/docs/en-us/reference/engine/enums/LightingStyle)  lighting which renders a flatter look with softer lights and shadows. However, to enhance the environment and equip your local light sources to produce precise shadows and illumination, such as the lighting in the hallways and above the signage, you must enable [Realistic](/docs/en-us/reference/engine/enums/LightingStyle)  lighting. This allows both your global and local lighting to work together and provide more realistic and immersive visuals.

For example, the [Realistic](/docs/en-us/reference/engine/enums/LightingStyle)  lighting style automatically detects when a user is either in an interior or exterior space, then it responds by enabling the appropriate lighting model. This means that reflections are able to reflect off the floor and ceiling within the building, providing a richer visual game as users navigate through combat pockets.

Create your own Recreate the sample

To configure your own global lighting:

1.

In the Explorer  window, select the Lighting  service, then in the Properties  window, set its properties to values that reflect the art style of your game. For more information on these properties, see [Global lighting](/docs/en-us/environment/lighting) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GlobalLighting-1.jpg)

2.

In the Explorer  window, select the Lighting  service's child Atmosphere  object, then in the Properties  window, set its properties to values that reflect the art style of your game. For more information on these properties, see [Atmospheric effects](/docs/en-us/environment/atmosphere) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GlobalLighting-2.jpg)

3.

OPTIONAL

 Apply one or more customizable filters, such as bloom, depth‑of‑field, or sun rays. For more information on these properties, see [Post-processing effects](/docs/en-us/environment/post-processing-effects) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GlobalLighting-4.jpg)

### [Local lighting](#local-lighting)[](#local-lighting)

Local lighting is the luminescence from local [light sources](/docs/en-us/effects/light-sources)  in your game, such as [SpotLight](/docs/en-us/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/en-us/reference/engine/classes/SurfaceLight) , and [PointLight](/docs/en-us/reference/engine/classes/PointLight)  objects. It's important to analyze the needs of your game to know which type of local light source to use. For example, the final sample laser tag environment needs lighting to help users see the different areas inside of the building while they're in combat, as well as lighting to differentiate the different spawn zone areas.

Local light sources create points of reference and directionality for users. For example, the sample uses surface lights to inform users if they are navigating the perimeter or are near the blue-green or pink spawn zone, and spotlights to highlight doorways.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-Intro.jpg)

Applying light sources is an art form, and it takes time to figure out what lighting configurations work to meet the needs of your game. It's normal and expected for your lighting to look and feel different from the final sample laser tag environment.

Create your own Recreate the sample

To configure your own local lighting:

1.

Add and configure glowing lights around the perimeter hallways that provide orientation cues to users navigating around the building.

1.

Add and position a block  part near the top of one of your perimeter hallways, then in the Properties  window,

1.

Set Color  to a bright color.

2.

Set Material  to Neon .

3.

Enable Anchored .

2.

In the Explorer  window, add a SurfaceLight  object to the part.

1.

Hover over the part and click the ⊕  button. A contextual menu displays.

2.

From the contextual menu, insert a SurfaceLight  object.

3.

Select the SurfaceLight  object, then in the Properties  window,

1.

Set Color  to a bright color.

2.

Set Face  to the direction you want the light to shine.

3.

Set Range  to a value that reflects how far you want your light to reach.

4.

Repeat this process, positioning and orienting parts to complete the glowing perimeter lights.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-1.jpg)

2.

Add and configure small hallway interior lights that illuminate cross lanes.

1.

Add and position a block  part near the top of one of your cross lane hallways, then in the Properties  window,

1.

Set Color  to a bright color.

2.

Set Material  to Neon .

3.

Enable Anchored .

2.

In the Explorer  window, add a SpotLight  object to the part.

1.

Hover over the part and click the ⊕  button. A contextual menu displays.

2.

From the contextual menu, insert a SpotLight  object.

3.

Select the SpotLight  object, then in the Properties  window,

1.

Set Angle  to a value that reflects the angle you want your light to shine.

2.

Set Face  to the direction you want the light to shine.

3.

Set Range  to a value that reflects how far you want your light to reach.

4.

Repeat this process, positioning and orienting parts above doors and hallways until you are happy with the interior lighting.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-2.jpg)

3.

Add and configure the spawn zone lights.

1.

Add a block  part that is the size of your left spawn zone, and position it above the spawn zone's ceiling.

2.

In the Properties  window,

1.

Set Color  to the color theme of the team on the left of the map.

2.

Set Material  to Neon .

3.

Enable Anchored .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-3a.jpg)

1.

Repeat this process for the right spawn zone.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-3B.jpg)

1.

OPTIONAL

 Add and anchor light fixtures around the interior and exterior of the building from your own asset library.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-4.jpg)

Once you are happy with the look and feel of your environment, you can move on to configure your assets and Studio settings to keep your frame rate and performance levels high for low-end devices. This process ensures that nearly every user has the same gameplay and visual experience while they're viewing your environment.

[Next](/docs/en-us/tutorials/curriculums/environmental-art/optimize-your-experience)[Previous](/docs/en-us/tutorials/curriculums/environmental-art/assemble-an-asset-library)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
