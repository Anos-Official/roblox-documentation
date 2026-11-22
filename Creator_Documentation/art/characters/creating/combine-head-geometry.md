<!-- Source: https://create.roblox.com/docs/en-us/art/characters/creating/combine-head-geometry -->

Combine head geometry | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/creating/combine-head-geometry.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Combine head geometry

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/creating/combine-head-geometry.md)

Whenever you are ready to export your model, it's important to clean up your project to ensure that your model is ready to export. This includes the following tasks that ensure the customized template model and all of the avatar components can import into Studio successfully:

-

Combining extra head geometry

-

Removing extra head bones

-

Verifying attachment points

-

Final technical checks

Failure to combine head geometry and [remove head bones](/docs/en-us/art/characters/creating/remove-extra-bones)  will cause issues with validation, as the character will no longer adhere to the expected standard [geometry](/docs/en-us/avatar/character-bodies/specifications#body-parts)  and [joint hierarchy](/docs/en-us/avatar/character-bodies/specifications#rigging) .

## [Combine head geometry](#combine-head-geometry)[](#combine-head-geometry)

At this point, you should also combine the separate head and face objects within the single Head_Geo  object. Some templates don't include some face objects, like lashes. To combine the head and face meshes:

1.

In the Outliner, hold Ctrl / ⌘  and click the following objects, ending with the Head_Geo :

-

UpperTeeth_Geo

-

LowerTeeth_Geo

-

Tongue_Geo

-

RightLash_Geo

-

RightEye_Geo

-

LeftLash_Geo

-

LeftEye_Geo

-

Head_Geo

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Template-Face-Objects.png)

When selecting multiple head objects, make sure that the Head_Geo  is highlighted as yellow, indicating it as the main object that the others merge into. This correctly preserves the custom properties stored in the head mesh. You can achieve this by selecting the head last in the Outliner.

2.

While in Object  mode, right-click in the viewport and select Join  from the contextual menu. The objects combine as a single Head_Geo  object.

[Next](/docs/en-us/art/characters/creating/remove-extra-bones)[Previous](/docs/en-us/art/characters/creating/caging)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
