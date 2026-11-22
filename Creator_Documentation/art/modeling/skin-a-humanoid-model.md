<!-- Source: https://create.roblox.com/docs/en-us/art/modeling/skin-a-humanoid-model -->

Skin a humanoid model | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/skin-a-humanoid-model.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Animation
6. /
7. In Blender

# Skin a humanoid model

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/skin-a-humanoid-model.md)

A humanoid skinned mesh is a character model that, when posed or animated, bends and stretches naturally at its joints. You can create a skinned mesh using a third party modeling tool such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) .

This is an advanced guide on skinning a humanoid model into an R15 model in Blender using the humanoid model completed in [Rig a humanoid model](/docs/en-us/art/modeling/rig-a-humanoid-model) . Before skinning a humanoid model, you should also familiarize yourself with the basic concepts in [Skin a simple mesh](/docs/en-us/art/modeling/skin-a-simple-mesh) .

To skin a humanoid model in Blender, you need to:

-

[Set up Blender](#set-up-blender)  with a rigged model to optimize the weight painting process with bone visualization settings and Auto Normalize.

-

[Weight paint](#weight-painting)  vertices of your mesh objects by balancing influence of your vertices between two or more bones of a humanoid rig architecture.

This guide uses the humanoid model rigged in [Rig a humanoid model](/docs/en-us/art/modeling/rig-a-humanoid-model)  and [Blender version 3.0](https://www.blender.org/download/releases/3-0/) . If you are using another version of Blender, there may be minor differences in UI and settings.

## [Set up Blender](#set-up-blender)[](#set-up-blender)

This guide uses the rigged model completed in [Rig a humanoid model](/docs/en-us/art/modeling/rig-a-humanoid-model) . You can also download the rigged model [Blender project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/lola-rigged-r15.blend)  to follow along with this guide.

To optimize the process of skinning a rigid character, first set up the following in your Blender project:

-

Open the Blender project and configure the [bone visualization](#bone-visualization)  settings.

-

Enable [Auto Normalize](#auto-normalize)  to help optimize the weight-painting process.

### [Bone visualization](#bone-visualization)[](#bone-visualization)

By default, Blender displays bone objects as octahedral shapes. This original shape is useful when positioning bones but can get in the way while weight painting. To help visualization during the weight painting process, change your bone visualization to sticks.

To update the visualization of your bones:

1.

In Object Mode, click the armature .

2.

In the Object Data Properties , change the Display As  value to Sticks .

### [Auto normalize](#auto-normalize)[](#auto-normalize)

The Auto Normalize setting forces the influence on your vertices to equal one. This makes weight painting multiple meshes and bones more efficient by ensuring that each vertex in your character is fully influenced by at least one bone. See Blender's documentation on the [Auto Normalize](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/tool_settings/options.html)  for more information.

Auto Normalize also prevents cases where a vertex is fully influenced by multiple bones and can prevent common weight painting mistakes.

Without Auto Normalize, it is not clear until testing that this fully influenced head is also influenced by another bone due to a painting mistake.

With Auto Normalize, painting influence to an incorrect bone removes the existing influence from the original bone. This makes mistakes easier to catch and resolve.

Studio doesn't support more than 4 bones to influence any single vertex. This may occur in complex rigs or inadvertently with Auto Normalize disabled.

To enable Auto Normalize:

1.

In Object Mode , select the armature .

2.

Hold Shift  and select any mesh object  on your model.

3.

At the top of the 3D viewport, click on the Mode dropdown and switch to Weight Paint  mode.

4.

On the right side of the viewport, expand the Tool  tab.

5.

Under Options , enable Auto Normalize .

## [Weight painting](#weight-painting)[](#weight-painting)

Weight painting applies specific weights, or influences, that bones will have over parts of a mesh using a painting workflow. There are also additional ways to apply influences through weight painting or other tools, some which are covered in [Skin a simple mesh](/docs/en-us/art/modeling/skin-a-simple-mesh) . See additional online resources such as Blender's [Character Rigging](https://www.youtube.com/watch?v=f2pTkW-1JkE)  and [Vertex Groups](https://www.youtube.com/watch?v=dKZrzG5r13g)  fundamental guides for more information on skinning and applying weights.

This guide will cover one process of weight painting the head and arm meshes of a humanoid model. These weight painting techniques can be used to weight paint the rest of the model.

Do not apply influences on the Root or HumanoidRootNode parent bones in a humanoid rig. Any added influences are dropped when importing into Studio.

### [Paint the head mesh](#paint-the-head-mesh)[](#paint-the-head-mesh)

The head mesh connects to the upper torso at the bottom vertices of the neck. To create a realistic bend in the model, the head mesh needs to share influence with the Head bone and the Upper Torso bone near the neckline.

To begin weight painting the Head mesh object:

1.

In Object Mode, click the armature  then hold Shift  and click the Head mesh object .

2.

In the Mode dropdown, switch to Weight Paint  mode.

3.

Hold Shift  and click the Upper Torso bone . The head should be completely blue as the Upper Torso doesn't yet influence any head vertices.

A common error is to apply weights with the incorrect bone selected. Make sure to Shift  select and un-select the correct bones when applying weights. The name of the bone currently being painted will populate in the Viewport.

4.

In the top right of the Viewport, open the Tool  menu and set the brush strength  to 1 .

5.

With the Upper Torso bone selected, paint  the Head of your model at the neckline. You can temporarily Hide  the Upper Torso mesh in the Outliner to have direct access to the bottom of the neck.

6.

At any point, check the applied influences by holding Shift  and deselecting the Upper Torso bone and selecting the Head bone. Press R  to rotate the Head bone with your mouse and test how the mesh object shares influences between the Head and Upper Torso bone.

7.

If additional painting is required, hold Shift  and select the bone you want to add or remove influence from, and use the Brush tool to apply.

The final result of weight painting the head of the model should balance the head mesh influences with the Head bone and the Upper Torso bone:

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/skinning-humanoid/head-example-headbone-selected.png) The Head bone fully influences the Head_Geo mesh from the neck up.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/skinning-humanoid/head-example-uppertorso-selected.png) The Upper Torso bone fully influences the Head_Geo mesh from the neck down.

### [Paint the arm meshes](#paint-the-arm-meshes)[](#paint-the-arm-meshes)

Similar to the process for balancing influences between the Head bone and Upper Torso bone, arms and legs require a similar weight painting process.

The right arm includes the Right Hand, Right Lower Arm, and Right Upper Arm, each with their corresponding bones. The following instructions provide guidance on painting influences to all of the arm mesh objects. You can then apply these techniques to the rest of the meshes in your model.

#### [Hand](#hand)[](#hand)

Starting with the Right Hand, you can balance the influences of the mesh between the Hand bone  and the Lower Arm bone  to create a natural bend at the wrist.

To weight paint influences to the right hand:

1.

From Object Mode, click the armature , hold Shift , and click the right hand  geometry.

2.

In the mode dropdown, switch to Weight Paint  mode. With the hand bone selected in this mode, you can press R  and test the current rotation of the hand mesh object.

3.

In the top right of the Viewport, open the Tool  menu and set the brush strength  to 1 .

4.

With the Lower Arm bone selected, paint  the hand of your model at the wrist. You can temporarily Hide  the Lower Arm mesh in the Outliner to get better access to the wrist.

5.

During and after weight painting the hand, press R  with the bone selected to test the rotation and flexibility.

You can add and skin additional bones, such as fingers, if you want additional controls to your skinned mesh.

Extra bone objects that are skinned to a mesh but do not share a Humanoid bone object name (such as LowerTorso, LeftFoot, Right UpperArm) are imported into Studio as a [Bone](/docs/en-us/reference/engine/classes/Bone)  with the same name it was assigned with in the 3D modeling software.

#### [Lower arm](#lower-arm)[](#lower-arm)

After the wrist of the right hand is weight painted, you can proceed to balance the influences of the Lower Arm mesh between the Lower Arm bone  and the Upper Arm bone  to create a natural bend at the elbow.

To weight paint influences to the lower arm:

1.

Switch back to Object Mode.

2.

Click the armature  and hold Shift  and click the right lower arm  geometry.

3.

In the mode dropdown, switch to Weight Paint  mode.

4.

Hold Shift  and deselect other bones besides the Lower Arm bone. You can test the current rotation of the highlighted Lower Arm bone by pressing R .

5.

Hold Shift  and select the Upper Arm bone.

6.

With the Upper Arm bone selected, paint  the lower arm of your model at the elbow. You can temporarily Hide  the Upper Arm mesh in the Outliner to get better access to the elbow.

7.

During and after weight painting the lower arm, press R  with the lower arm bone selected to test the rotation and flexibility.

#### [Upper arm](#upper-arm)[](#upper-arm)

After the elbow of the right lower arm is weight painted, you can proceed to balance the influences of the Upper Arm mesh between the Upper Arm bone  and the Upper Torso bone  to create a natural bend at the underarm.

To weight paint influences to the upper arm:

1.

Switch back to Object Mode.

2.

Click the armature  and hold Shift  and click the right upper arm  geometry.

3.

In the mode dropdown, switch to Weight Paint  mode.

4.

Hold Shift  and deselect other bones besides the Upper Arm bone. You can test the current rotation of the highlighted Upper Arm bone by pressing R .

5.

Press R  and drag your mouse to rotate the Upper Arm so that the arm is horizontal. This makes it easier to access the vertices of the underarm.

6.

Hold Shift  and select the Upper Torso bone.

7.

With the Upper Torso bone selected, paint  the upper arm of your model at the underarm. You can temporarily Hide  the Upper Torso mesh in the Outliner to get better access to the elbow.

8.

During and after weight painting the lower arm, press R  with the upper arm bone selected to test the rotation and flexibility.

#### [Shoulder](#shoulder)[](#shoulder)

After the underarm is weight painted, you can proceed to balance the influences of the Upper Torso mesh between the Upper Torso bone  and the Upper Arm bone  to create a natural bend at the shoulder when the arm is moved. Since this movement is subtle, you only need to apply a partial strength influence to these vertices.

To weight paint a partial strength influence to the upper torso:

1.

Switch back to Object Mode.

2.

Click the armature  and hold Shift  and click the upper torso  geometry.

3.

In the mode dropdown, switch to Weight Paint  mode.

4.

Hold Shift  and deselect other bones besides the Upper Arm bone. You can test the current rotation of the highlighted Upper Arm bone by pressing R .

5.

In the top right of the Viewport, open the Tool  menu and set the brush strength  to .25 . You may want to adjust this based on the results when testing.

6.

With the Upper Torso bone selected, paint  the upper torso of your model at the shoulder.

7.

During and after weight painting the lower arm, press R  with the upper arm bone selected to test the rotation and flexibility of your influences to the upper torso.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/skinning-humanoid/Candywrap-Example.png)

When rotating arms to their full range of motion, a candy-wrapping effect may occur between the shoulder and torso where the skinning loses volume and doesn't deform naturally. This effect may not be avoidable in many cases.

You can continue to weight paint the rest of the limbs of your model using these processes. When completed, you can [export](/docs/en-us/art/modeling/export-requirements)  your skinned model as a .fbx  using the Blender export settings for use in Studio. For reference, you can download a [Blender project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/lola-skinned-s15.blend)  with the model fully skinned.

Since this reference model doesn't yet have [inner and outer cage mesh data](/docs/en-us/avatar/character-bodies/specifications#inner-and-outer-cages) , this model can't equip layered accessories.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
