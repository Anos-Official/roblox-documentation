<!-- Source: https://create.roblox.com/docs/art/characters/creating/remove-extra-bones -->

Remove extra bones | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/creating/remove-extra-bones.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Remove extra bones

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/creating/remove-extra-bones.md)

The helper bones used to help place the head geometries also require removal to validate correctly. While these extra bones do not include any skinning data, do not delete any of the facial animation bones parented within DynamicHead, as these include important skinning data that drives facial animation.

Failure to [combine head geometry](/docs/art/characters/creating/combine-head-geometry)  and remove head bones will cause issues with validation, as the character will no longer adhere to the standard [geometry](/docs/avatar/character-bodies/specifications#body-parts)  and [joint hierarchy](/docs/avatar/character-bodies/specifications#rigging) .

Remove the additional head bones by selecting them and deleting them in edit mode:

1.

If required for your template, toggle visibility on your Armature  object. The bones display in the viewport.

2.

In the Outliner, expand the character's armature object and find the Joints  object that parents the bone structure of the character.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Select-Joint-Objects.png)

3.

Expand the Joints  object's hierarchy by holding Shift  and clicking the expansion dropdown.

4.

In the viewport, select any bone and switch to Edit  mode.

5.

Under the Head  joint, hold Shift  and select all the head child joints except DynamicHead .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Select-Bone-Objects.png)

6.

With the extra head bones selected, right-click in the viewport and select Delete Selected Bones  from the contextual menu.

[Next](/docs/art/characters/creating/verify-attachments)[Previous](/docs/art/characters/creating/combine-head-geometry)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
