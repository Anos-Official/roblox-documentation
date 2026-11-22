<!-- Source: https://create.roblox.com/docs/effects/highlighting -->

Highlighting objects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/effects/highlighting.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Effects](/docs/effects)

# Highlighting objects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/effects/highlighting.md)

The [Highlight](/docs/reference/engine/classes/Highlight)  instance is a visual effect which you can use to call attention to a specific object within a game. Every highlight effect has a silhouette outline  that surrounds the object and a solid overlay interior  that displays over the object. You can customize both of these components independently to modify the highlight's visual appearance.

![A tree mesh against a grey background.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-1.jpg) Base object

![The same tree mesh with a yellow outline and a black highlight interior.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Overview-Yellow-Outline.jpg) Yellow outline and black interior

![The same tree mesh with a black outline and a yellow highlight interior.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Overview-Yellow-Interior.jpg) Black outline and yellow interior

Useful applications of the highlight effect include:

-

Providing visual feedback that an object is important and/or interactable.

-

Making distant objects visible through objects that are closer to the user.

-

Indicating the current position and status of other characters.

## [Add highlights](#add-highlights)[](#add-highlights)

As a performance limit, Studio only displays 255 simultaneous [Highlight](/docs/reference/engine/classes/Highlight)  instances on the client-side at a time. If you add more than this limit, the additional [Highlight](/docs/reference/engine/classes/Highlight)  instances are silently ignored.

Note also that highlights on low-end devices may be more pixelated but will otherwise look the same as on other devices with any combination of settings.

### [Parent to objects](#parent-to-objects)[](#parent-to-objects)

To add a highlight effect to an object, you can parent a new [Highlight](/docs/reference/engine/classes/Highlight)  directly to the object.

1.

In the Explorer  window, hover over either a [Model](/docs/reference/engine/classes/Model)  or a [BasePart](/docs/reference/engine/classes/BasePart) , then click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a Highlight . The highlight displays on the object with its default property values that create a white outline and a red tint overlay.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Adding-Highlight.jpg)

### [Set the adornee](#set-the-adornee)[](#set-the-adornee)

Alternatively, you can place the [Highlight](/docs/reference/engine/classes/Highlight)  instance outside of a child/parent relationship either within the workspace, [StarterPlayer](/docs/reference/engine/classes/StarterPlayer) , [StarterGui](/docs/reference/engine/classes/StarterGui) , [StarterPack](/docs/reference/engine/classes/StarterPack) , or [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , then set its [Adornee](/docs/reference/engine/classes/Highlight#Adornee)  property to the [Model](/docs/reference/engine/classes/Model)  or [BasePart](/docs/reference/engine/classes/BasePart)  that you want to highlight.

## [Customize highlights](#customize-highlights)[](#customize-highlights)

You can change the properties of a [Highlight](/docs/reference/engine/classes/Highlight)  instance to create interesting visual effects that properly highlight objects in theme with your game.

### [OutlineColor](#outlinecolor)[](#outlinecolor)

The [OutlineColor](/docs/reference/engine/classes/Highlight#OutlineColor)  property sets the [Color3](/docs/reference/engine/datatypes/Color3)  value of the highlight's outline.

![A tree mesh with red outline.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineColor-Red.jpg) OutlineColor = [255, 100, 50]

![A tree mesh with green outline.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineColor-Green.jpg) OutlineColor = [0, 255, 125]

![A tree mesh with blue outline.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineColor-Blue.jpg) OutlineColor = [75, 150, 255]

### [OutlineTransparency](#outlinetransparency)[](#outlinetransparency)

The [OutlineTransparency](/docs/reference/engine/classes/Highlight#OutlineTransparency)  property sets the visibility of the highlight's outline to any value between the default value of 0  (opaque) and 1  (invisible).

![A tree mesh with black opaque outline.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-0.jpg) OutlineTransparency = 0

![A tree mesh with transparent outline.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-1.jpg) OutlineTransparency = 1

### [FillColor](#fillcolor)[](#fillcolor)

The [FillColor](/docs/reference/engine/classes/Highlight#FillColor)  property sets the [Color3](/docs/reference/engine/datatypes/Color3)  value of the highlight's interior.

![A tree mesh with a red fill.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillColor-Red.jpg) FillColor = [255, 100, 50]

![A tree mesh with a red fill.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillColor-Green.jpg) FillColor = [0, 255, 125]

![A tree mesh with a blue fill.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillColor-Blue.jpg) FillColor = [75, 150, 255]

### [FillTransparency](#filltransparency)[](#filltransparency)

The [FillTransparency](/docs/reference/engine/classes/Highlight#FillTransparency)  property sets the visibility of the highlight's interior to any value between the default value of 0  (opaque) and 1  (invisible). You can use this property to determine how much of the object's existing color you want viewers to see.

![A tree mesh with an opaque black fill.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillTransparency-0.jpg) FillTransparency = 0

![A tree mesh with a semi-transparent black fill.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillTransparency-Half.jpg) FillTransparency = 0.5

![A tree mesh with a transparent black fill.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillTransparency-1.jpg) FillTransparency = 1

### [DepthMode](#depthmode)[](#depthmode)

The [DepthMode](/docs/reference/engine/classes/Highlight#DepthMode)  property controls how the effect displays with respect to other objects in the world.

-

[AlwaysOnTop](/docs/reference/engine/enums/HighlightDepthMode#AlwaysOnTop)  — Allows the highlight to display regardless if there are objects between the camera and the highlighted object. This means the viewer is always able to see the highlight regardless of what is between the highlighted object and the camera.

-

[Occluded](/docs/reference/engine/enums/HighlightDepthMode#Occluded)  — Hides the highlight if there are objects between the camera and the highlighted object. This means the viewer is only able to see the object if there are no obstructing objects between the highlighted object and the camera's view.

AlwaysOnTop Occluded

![Two objects are behind pillars, but because their AlwayOnTop property is set to true, you can still see the objects and their highlight.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/DepthMode-AlwaysOnTop.jpg)

### [Enabled](#enabled)[](#enabled)

The [Enabled](/docs/reference/engine/classes/Highlight#Enabled)  property allows you to quickly enable or disable the highlight without any impact on performance .

While a disabled [Highlight](/docs/reference/engine/classes/Highlight)  doesn't display, it still takes one of the 255 available [Highlight](/docs/reference/engine/classes/Highlight)  slots. If you plan to permanently disable a [Highlight](/docs/reference/engine/classes/Highlight)  instance, it's best to delete the highlight rather than disable it.

## [Performance tips](#performance-tips)[](#performance-tips)

While you have a lot of options to customize [Highlight](/docs/reference/engine/classes/Highlight)  instances, the following tips are recommended to increase your game's performance on all devices:

-

Adding or removing a [Highlight](/docs/reference/engine/classes/Highlight)  can cause a geometry rebuilding step that might lead to performance spikes and extra draw calls. If you want to change a [Highlight](/docs/reference/engine/classes/Highlight)  instance's appearance or temporarily hide/display it on an object, it's best to customize the properties of the [Highlight](/docs/reference/engine/classes/Highlight)  instance directly, as changing any property of the [Highlight](/docs/reference/engine/classes/Highlight)  instance is lightweight and doesn't impact performance.

-

Roblox draws objects in a back to front order, which can cause problems if you embed objects with a child [Highlight](/docs/reference/engine/classes/Highlight)  inside other objects that also have children [Highlight](/docs/reference/engine/classes/Highlight)  instances. For this reason, it's best to keep objects with [Highlight](/docs/reference/engine/classes/Highlight)  instances outside of a parent/child relationship with other objects with [Highlight](/docs/reference/engine/classes/Highlight)  instances.

-

The first [Highlight](/docs/reference/engine/classes/Highlight)  rendered on the screen incurs most of the performance cost (up to 1 millisecond of GPU time on mobile devices). For additional highlights beyond the first, you should not see a significant performance impact on any platform.

-

On mobile devices, highlights are more costly on performance when they cover more of the screen. On other platforms, highlights have the same performance cost regardless of their screen coverage.

-

On all platforms, highlights that are not visible on the screen (whether disabled or fully transparent) incur no performance cost.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
