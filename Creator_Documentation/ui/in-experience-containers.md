<!-- Source: https://create.roblox.com/docs/en-us/ui/in-experience-containers -->

In-game UI containers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/in-experience-containers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)

# In-game UI containers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/in-experience-containers.md)

In-game UI containers hold [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  that you want to display within your game's 3D world.

-

A [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  allows for the rendering of UI objects onto a part's surface in the 3D world while also allowing for basic user interaction to occur.

-

A [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  is a container for UI objects to appear in the 3D space but always face the camera.

## [Surface UI](#surface-ui)[](#surface-ui)

Similar to [Decals](/docs/en-us/reference/engine/classes/Decal)  and [Textures](/docs/en-us/reference/engine/classes/Texture) , UI objects such as [TextLabels](/docs/en-us/reference/engine/classes/TextLabel)  and [ImageLabels](/docs/en-us/reference/engine/classes/ImageLabel)  parented to a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  face the same direction as the surface they're on, editable through the [SurfaceGui.Face](/docs/en-us/reference/engine/classes/SurfaceGui#Face)  property.

 ![SurfaceGui on a 3D part in the place with an ImageLabel child to depict a screen console.](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/SurfaceGui-Diagram.jpg)

To apply a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  to an in-game [BasePart](/docs/en-us/reference/engine/classes/BasePart) , simply parent it to that part and set the [SurfaceGui.Face](/docs/en-us/reference/engine/classes/SurfaceGui#Face)  property. Child UI objects then appear on that face of the parent part.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-SurfaceGui-ImageLabel.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/SurfaceGui-Face-Top.png)

Alternatively, you can place the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  inside a container like [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  and then set its [Adornee](/docs/en-us/reference/engine/classes/SurfaceGui#Adornee)  property to any [BasePart](/docs/en-us/reference/engine/classes/BasePart) , as well as the target [Face](/docs/en-us/reference/engine/classes/SurfaceGui#Face) . Setting [Adornee](/docs/en-us/reference/engine/classes/SurfaceGui#Adornee)  overrides direct parent association, allowing for more flexibility in placement since it can be set from a script during runtime.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-SurfaceGui.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/SurfaceGui-Adornee-Face.png)

Interactive UI elements like [ImageButtons](/docs/en-us/reference/engine/classes/ImageButton)  and [TextButtons](/docs/en-us/reference/engine/classes/TextButton)  inside a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  will only receive user input if they are parented to the player's [PlayerGui](/docs/en-us/reference/engine/classes/PlayerGui) , typically via placing the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  inside [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  as noted above. Additionally, the part's [CanQuery](/docs/en-us/reference/engine/classes/BasePart#CanQuery)  property must be true  for the interactive UI element to receive input.

To assist in choosing the correct face for a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui) , right-click the target part and select Show Orientation Indicator . This displays a blue circle with an F  and a line attached to the object's [Front](/docs/en-us/reference/engine/enums/NormalId#Front)  face, and a green arrow that points in the direction of the object's [Top](/docs/en-us/reference/engine/enums/NormalId#Top)  face.

### [Size and position](#size-and-position)[](#size-and-position)

The "canvas" of a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  occupies the entire [Face](/docs/en-us/reference/engine/classes/SurfaceGui#Face)  of the parent or [Adornee](/docs/en-us/reference/engine/classes/SurfaceGui#Adornee)  part. As a best practice, it's recommended that you use scale  values for the [size](/docs/en-us/ui/position-and-size#size)  and [position](/docs/en-us/ui/position-and-size#position)  of child UI objects like [ImageLabels](/docs/en-us/reference/engine/classes/ImageLabel) . You can also apply a [UIAspectRatioConstraint](/docs/en-us/reference/engine/classes/UIAspectRatioConstraint)  to children of the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  to maintain their desired aspect ratio regardless of the face's size.

### [Occlusion mode](#occlusion-mode)[](#occlusion-mode)

The [AlwaysOnTop](/docs/en-us/reference/engine/classes/SurfaceGui#AlwaysOnTop)  property determines whether the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  will render over top of 3D content or be occluded by it. When set to false  (default), the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  renders like other 3D content and is occluded by other 3D objects. When set to true , it always renders over top of 3D content and it is not influenced by [brightness/light](#brightness-and-light-influence)  in the 3D environment.

### [Brightness and light influence](#brightness-and-light-influence)[](#brightness-and-light-influence)

[Brightness](/docs/en-us/reference/engine/classes/SurfaceGui#Brightness)  and [LightInfluence](/docs/en-us/reference/engine/classes/SurfaceGui#LightInfluence)  work in conjunction to determine how environmental light affects the UI content of the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui) .

[Brightness](/docs/en-us/reference/engine/classes/SurfaceGui#Brightness)  determines the factor by which emitted light is scaled in a range of 0  to 1000 , letting you match the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  to its environment. For instance, a video billboard can be brightened inside a dark room by increasing [Brightness](/docs/en-us/reference/engine/classes/SurfaceGui#Brightness)  to 10 .

[LightInfluence](/docs/en-us/reference/engine/classes/SurfaceGui#LightInfluence)  controls how much the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  is influenced by lighting in the place, in a range from 0  to 1 . Setting this to 1  means that surrounding lighting has complete control over the appearance, while setting it to 0  means that the lighting has no effect.

Brightness = 0 Brightness = 10

![](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/SurfaceGui-Brightness-0.jpg)

Note that [Brightness](/docs/en-us/reference/engine/classes/SurfaceGui#Brightness)  is inaccessible in Studio and has no effect when either [LightInfluence](/docs/en-us/reference/engine/classes/SurfaceGui#LightInfluence)  is 1  or [AlwaysOnTop](/docs/en-us/reference/engine/classes/SurfaceGui#AlwaysOnTop)  is true .

### [Distance visibility](#distance-visibility)[](#distance-visibility)

[MaxDistance](/docs/en-us/reference/engine/classes/SurfaceGui#MaxDistance)  controls how far from the camera the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  will be displayed before it stops rendering. A value of 0  means there is no limit and it will render infinitely far away. The default value of 1000  works fine for most cases.

For [SurfaceGuis](/docs/en-us/reference/engine/classes/SurfaceGui)  that appear outdoors, it's recommended that [MaxDistance](/docs/en-us/reference/engine/classes/SurfaceGui#MaxDistance)  is high enough to ensure that the container's UI is sufficiently small on the screen when it appears or disappears, minimizing the sudden pop‑in/out effect.

### [Display order](#display-order)[](#display-order)

If multiple [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  containers exist on the same face, you can layer them by Z‑index through their [ZOffset](/docs/en-us/reference/engine/classes/SurfaceGui#ZOffset)  property (changing this does not visually "lift" or "sink" the container from the surface).

## [Billboard UI](#billboard-ui)[](#billboard-ui)

The [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  container displays UI objects in the 3D space but, unlike [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui) , children of a [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  always face the camera. This container is useful for displaying front‑facing info above in-game objects such as health meters or names above player characters, markers to guide players to an object in the 3D world, and more.

 ![BillboardGui with a TextLabel describing the screen console it floats above.](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/BillboardGui-Diagram.jpg)

To link a [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  to an in-game [BasePart](/docs/en-us/reference/engine/classes/BasePart)  or [Attachment](/docs/en-us/reference/engine/classes/Attachment) , simply parent it to that part or attachment and, if desired, adjust its [size/position](#size-and-position-1) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-BillboardGui-ImageLabel.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-Attachment-BillboardGui-ImageLabel.png)

Alternatively, you can place the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  inside a container like [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  and then set its [Adornee](/docs/en-us/reference/engine/classes/BillboardGui#Adornee)  property to any [BasePart](/docs/en-us/reference/engine/classes/BasePart)  or [Attachment](/docs/en-us/reference/engine/classes/Attachment) . This method offers more flexibility in placement since [Adornee](/docs/en-us/reference/engine/classes/BillboardGui#Adornee)  can be set from a script during runtime, for example to place a [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  over the head of player characters during runtime.

Interactive UI elements like [ImageButtons](/docs/en-us/reference/engine/classes/ImageButton)  and [TextButtons](/docs/en-us/reference/engine/classes/TextButton)  inside a [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  will only receive user input if they are parented to the player's [PlayerGui](/docs/en-us/reference/engine/classes/PlayerGui) , typically via placing the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  inside [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  as noted above.

### [Size and position](#size-and-position-1)[](#size-and-position-1)

For billboard sizing, the [scale](/docs/en-us/ui/position-and-size#size)  components of the [Size](/docs/en-us/reference/engine/classes/BillboardGui#Size)  property set the billboard's stud size in 3D space. For example, a setting of {10, 0},{2, 0}  ([UDim2.fromScale(10, 2)](/docs/en-us/reference/engine/datatypes/UDim2#fromScale) )  forms a billboard with a 10:2 aspect ratio that scales larger or smaller depending on its distance from the camera.

For positioning, the [StudsOffset](/docs/en-us/reference/engine/classes/BillboardGui#StudsOffset)  property shifts the billboard canvas on the X  axis (left/right), Y  axis (up/down), and Z  axis (forward/back) relative to the camera.

When creating a size-scaled [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  that contains a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel) , it's useful to enable the label's [TextScaled](/docs/en-us/reference/engine/classes/TextLabel#TextScaled)  property so that its text scales along with the billboard canvas as the camera distance changes.

### [Occlusion mode](#occlusion-mode-1)[](#occlusion-mode-1)

The [AlwaysOnTop](/docs/en-us/reference/engine/classes/BillboardGui#AlwaysOnTop)  property determines whether the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  will render over top of 3D content or be occluded by it. When set to false  (default), the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  renders like other 3D content and is occluded by other 3D objects. When set to true , it always renders over top of 3D content and it is not influenced by [brightness/light](#brightness-and-light-influence-1)  in the 3D environment.

### [Brightness and light influence](#brightness-and-light-influence-1)[](#brightness-and-light-influence-1)

[Brightness](/docs/en-us/reference/engine/classes/BillboardGui#Brightness)  and [LightInfluence](/docs/en-us/reference/engine/classes/BillboardGui#LightInfluence)  work in conjunction to determine how environmental light affects the UI content of the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui) .

[Brightness](/docs/en-us/reference/engine/classes/BillboardGui#Brightness)  determines the factor by which emitted light is scaled in a range of 0  to 1000 , letting you match the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  to its environment. For instance, a video billboard can be brightened inside a dark room by increasing [Brightness](/docs/en-us/reference/engine/classes/BillboardGui#Brightness)  to 10 .

[LightInfluence](/docs/en-us/reference/engine/classes/BillboardGui#LightInfluence)  controls how much the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  is influenced by lighting in the place, in a range from 0  to 1 . Setting this to 1  means that surrounding lighting has complete control over the appearance, while setting it to 0  means that the lighting has no effect.

LightInfluence = 1 LightInfluence = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/in-experience/BillboardGui-LightInfluence-1.jpg)

Note that [Brightness](/docs/en-us/reference/engine/classes/BillboardGui#Brightness)  is inaccessible in Studio and has no effect when either [LightInfluence](/docs/en-us/reference/engine/classes/BillboardGui#LightInfluence)  is 1  or [AlwaysOnTop](/docs/en-us/reference/engine/classes/BillboardGui#AlwaysOnTop)  is true .

### [Distance visibility](#distance-visibility-1)[](#distance-visibility-1)

[MaxDistance](/docs/en-us/reference/engine/classes/BillboardGui#MaxDistance)  controls how far from the camera the [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  will be displayed before it stops rendering. A value of 0  or inf  (default) means there is no limit and it will render infinitely far away.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
