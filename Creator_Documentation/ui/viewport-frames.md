<!-- Source: https://create.roblox.com/docs/en-us/ui/viewport-frames -->

Viewport frames | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/viewport-frames.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI objects

# Viewport frames

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/viewport-frames.md)

A [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame)  uses a camera to render 3D objects into a 2D viewport. Ideal use cases include:

-

A minimap of your game directly in the corner of a user's screen.

-

3D models of items in an inventory menu.

-

Rotating objects that a character has equipped.

## [Viewport configurations](#viewport-configurations)[](#viewport-configurations)

3D objects that users view through a [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame)  can either move with their camera, remain static, or rotate within the [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame) . This object can also include a [Sky](/docs/en-us/reference/engine/classes/Sky)  child as a cubemap for reflections.

With Camera Static Rotation Skybox Reflections

If you want a 3D object to move with the camera:

1.

Position your camera view within the game so that the object you want to see within the frame is visible.

2.

Add a new [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame)  to the [screen](/docs/en-us/ui/on-screen-containers)  and then make sure it's selected in the Explorer .

3.

In the Properties  window, assign the [CurrentCamera](/docs/en-us/reference/engine/classes/ViewportFrame#CurrentCamera)  property to the camera:

1.

Select the [CurrentCamera](/docs/en-us/reference/engine/classes/ViewportFrame#CurrentCamera)  property. Your cursor changes.

2.

In the Explorer  window, click on the top-level [Camera](/docs/en-us/reference/engine/classes/Camera)  object.

4.

Parent the desired 3D object to the new [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame) . Note that if you still want to see the object within your game, you must duplicate it in the [Workspace](/docs/en-us/reference/engine/classes/Workspace)  and then parent the duplicate  object to the [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame) .

When you move your camera, the object will also move within the [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame) .

When you want to update the view of your [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame) , be sure to update the camera, not  the objects within the view.

## [Lighting and appearance](#lighting-and-appearance)[](#lighting-and-appearance)

Lighting within a [ViewportFrame](/docs/en-us/reference/engine/classes/ViewportFrame)  is controlled through three properties:

| Property | | Description |
| --- | --- |
| [Ambient](/docs/en-us/reference/engine/classes/ViewportFrame#Ambient) | | Determines the overall lighting hue applied to the area within the viewport frame. Defaults to [Color3.fromRGB(200, 200, 200)](/docs/en-us/reference/engine/datatypes/Color3#fromRGB)  (ghost grey). |
| [LightDirection](/docs/en-us/reference/engine/classes/ViewportFrame#LightDirection) | | A [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  representing the direction of the light source from position (0, 0, 0) . Defaults to (-1, -1, -1) . |
| [LightColor](/docs/en-us/reference/engine/classes/ViewportFrame#LightColor) | | Color of the directional light. Defaults to [Color3.fromRGB(140, 140, 140)](/docs/en-us/reference/engine/datatypes/Color3#fromRGB)  (silver). |

Additionally, you can adjust the overall rendered appearance of the viewport throuugh the following properties:

| Property | | Description |
| [ImageColor3](/docs/en-us/reference/engine/classes/ViewportFrame#ImageColor3) | | Changes the image color/tint without modification of the rendered object. The default colorization value is [Color3.new(1, 1, 1)](/docs/en-us/reference/engine/datatypes/Color3#new)  (white) at which no color modification occurs. |
| [ImageTransparency](/docs/en-us/reference/engine/classes/ViewportFrame#ImageTransparency) | | Changes the image transparency without modification of the rendered object. A value of 0  (default) is completely opaque and a value of 1  is completely transparent (invisible). |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
