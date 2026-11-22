<!-- Source: https://create.roblox.com/docs/avatar/character-bodies/caging-best-practices -->

Character body caging best practices | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/character-bodies/caging-best-practices.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Bodies

# Character body caging best practices

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/character-bodies/caging-best-practices.md)

Caging defines the outer surface of a character body that layered accessories stretch and fit over. A character body only needs an outer cage, which consists of 15 cage meshes, one for each body part. A precise outer cage lets layered accessories fit any body shape and layer naturally with each other. An imprecise cage causes clipping, stretching, and visual artifacts that players notice right away.

![A character body render mesh without a cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Body-Render-Mesh.jpg) A character body render mesh.

![The same character body with its outer cage displayed over the render mesh.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Body-Outer-Cage.jpg) The same character body with its outer cage.

A high-quality outer cage matters because it affects:

-

Fit and layering  - The cage defines how layered accessories wrap over the body and over each other. Poor cages cause clipping, unnatural stretching, or accessories that don't stack correctly.

-

Body shape compatibility  - Characters come in many shapes and sizes. A precise cage helps layered accessories fit as well as possible on every body, not just one.

-

Inflation control  - The outer cage of the body and the inner cage of a layered accessory define the space that the accessory occupies. Imprecise cages cause unnatural puffing or clipping.

-

Hidden surface removal  - Hidden surface removal (HSR) hides the parts of the body underneath a layered accessory. HSR depends on cage parts that line up with the body parts of the render mesh.

-

Animation  - The cage drives how layered accessories move with the skeleton. Sloppy cages create visual artifacts during any animation other than idle.

The following best practices and examples apply to caging character bodies. For head-specific guidance, see [Dynamic head caging best practices](/docs/avatar/dynamic-heads/caging-best-practices) . For caging layered accessories, see [Layered accessory caging best practices](/docs/avatar/layered-accessories/caging-best-practices) .

## [Best practices](#best-practices)[](#best-practices)

Always start with one of Roblox's body cage templates from the [reference files](/docs/avatar/character-bodies/project-files) , or use [Avatar Setup](/docs/avatar-setup) . These templates include all 15 outer cage meshes with the correct naming and UVs.

### [Keep the vertex count and UVs the same](#keep-the-vertex-count-and-uvs-the-same)[](#keep-the-vertex-count-and-uvs-the-same)

Don't change the vertex count or UVs of the 15 outer cage meshes. The outer cage is a deformer that relies on matching vertex counts and UVs to deform layered accessories correctly. If either changes, layered accessories distort or fail to deform.

 ![A body cage in a modeling application next to its unchanged UV layout.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Vertex-Count-UVs.jpg)

### [Keep the middle axis at the origin](#keep-the-middle-axis-at-the-origin)[](#keep-the-middle-axis-at-the-origin)

Keep the middle axis of the cage at the origin when possible. This keeps the middle of the cage consistent.

 ![A front view of a body cage with its middle axis at the origin.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Middle-Axis.jpg)

### [Keep geometry equidistant](#keep-geometry-equidistant)[](#keep-geometry-equidistant)

Keep the geometry of the cage evenly spaced whenever possible. This reduces texture distortion and fit distortion in layered accessories. Keep in mind that this isn't always possible.

 ![A torso cage with evenly spaced edges.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Equidistant-Geometry.jpg)

### [Line up vertex-colored areas](#line-up-vertex-colored-areas)[](#line-up-vertex-colored-areas)

Line up the vertex-colored areas of each cage part with the matching areas of the body. This helps layered accessories line up correctly with those areas.

![The vertex-colored areas of a torso cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Vertex-Colored-Areas-A.jpg)

![The torso cage lined up with the torso of the render mesh.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Vertex-Colored-Areas-B.jpg)

### [Line up cage parts with body parts](#line-up-cage-parts-with-body-parts)[](#line-up-cage-parts-with-body-parts)

Line up each cage part with the matching body part of the render mesh. The alignment doesn't have to be exact, but it should be close. This lets HSR accurately hide the body underneath layered accessories. It helps to segment your character body so its parts line up with the cage parts.

![The upper and lower arm cage parts.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Line-Up-Cage-Parts-A.jpg)

![The arm cage parts lined up with the arm of the render mesh.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Line-Up-Cage-Parts-B.jpg)

### [Keep hand landmarks consistent](#keep-hand-landmarks-consistent)[](#keep-hand-landmarks-consistent)

Keep the landmarks of the hand cage consistent with the template. This helps accessories around the hands, such as gloves, line up with the hand as closely as possible.

![The back of a hand cage with landmarks marked.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Hand-Landmarks-A.jpg)

![The palm of a hand cage with landmarks marked.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Hand-Landmarks-B.jpg)

![The thumb side of a hand cage with landmarks marked.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Hand-Landmarks-C.jpg)

![The pinky side of a hand cage with landmarks marked.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Hand-Landmarks-D.jpg)

### [Keep foot landmarks consistent](#keep-foot-landmarks-consistent)[](#keep-foot-landmarks-consistent)

Keep the landmarks of the foot cage consistent with the template. This helps shoes line up with the foot as closely as possible.

 ![A foot cage with landmarks marked.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Foot-Landmarks.png)

### [Flatten the bottom of the foot cage](#flatten-the-bottom-of-the-foot-cage)[](#flatten-the-bottom-of-the-foot-cage)

Flatten the bottom of the foot cage. A flat base keeps shoes consistent and helps them keep their structure.

![A foot cage with a flat bottom.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Flat-Foot-Bottom-A.jpg)

![The flat foot cage over the foot of the render mesh.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Flat-Foot-Bottom-B.jpg)

### [Cover the render mesh closely](#cover-the-render-mesh-closely)[](#cover-the-render-mesh-closely)

Keep the cage close to the render mesh without intersecting it. Because the cage has a different topology and a lower resolution than the render mesh, this can be difficult. A close cage lets layered accessories fit closely without intersecting the body, and keeps them from looking puffy or floating away from the body.

![A front view of a body cage that closely covers the render mesh.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Close-Cage-A.jpg)

![A side view of a body cage that closely covers the render mesh.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Close-Cage-B.jpg)

### [Decide which areas to leave uncaged](#decide-which-areas-to-leave-uncaged)[](#decide-which-areas-to-leave-uncaged)

Decide which parts of the render mesh to leave outside the cage, basing the decision on how you want layered accessories to fit the body. For example, leaving the ears outside the cage helps hair and hats keep their original shape.

 ![A character head with its ears left outside the cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Uncaged-Ears.jpg)

### [Cage missing or different body parts](#cage-missing-or-different-body-parts)[](#cage-missing-or-different-body-parts)

Decide how to cage body parts that are missing or that differ from a standard humanoid, basing the decision on how you want layered accessories to fit the body. For example, keeping the overall shape of the foot cage helps shoes keep their shape, even on feet that aren't human.

 ![Cages that keep a standard foot shape over non-human legs and feet.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Different-Body-Parts.jpg)

## [Caging examples](#caging-examples)[](#caging-examples)

The following examples show how to cage character bodies that differ from a standard humanoid.

### [Classic body](#classic-body)[](#classic-body)

![A classic blocky character body.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Classic-Body-A.jpg)

![The classic character body with its outer cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Classic-Body-B.jpg)

### [Robot body](#robot-body)[](#robot-body)

![A robot character body.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Robot-Body-A.jpg)

![The robot character body with its outer cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Robot-Body-B.jpg)

### [Baked-in clothing](#baked-in-clothing)[](#baked-in-clothing)

![A character body with clothing modeled into the body.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Baked-In-Clothing-A.jpg)

![The character body with baked-in clothing and its outer cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Baked-In-Clothing-B.jpg)

### [Asymmetry and missing areas](#asymmetry-and-missing-areas)[](#asymmetry-and-missing-areas)

![An asymmetrical rock character body with gaps between its parts.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Asymmetry-Missing-Areas-A.jpg)

![The rock character body with its outer cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Asymmetry-Missing-Areas-B.jpg)

### [Anthropomorphized animals](#anthropomorphized-animals)[](#anthropomorphized-animals)

![An anthropomorphized red panda character body.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Anthropomorphized-Animal-A.jpg)

![The red panda character body with its outer cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Anthropomorphized-Animal-B.jpg)

### [Missing or different body parts](#missing-or-different-body-parts)[](#missing-or-different-body-parts)

![An alien character body with non-human features.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Missing-Different-Parts-A.jpg)

![The alien character body with its outer cage.](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/caging-best-practices/Missing-Different-Parts-B.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
