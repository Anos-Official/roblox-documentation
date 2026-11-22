<!-- Source: https://create.roblox.com/docs/tutorials/use-case-tutorials/ui/create-hud-meters -->

Create HUD meters | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/ui/create-hud-meters.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. User interfaces

# Create HUD meters

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/ui/create-hud-meters.md)

A HUD  or Heads-Up Display  is a set of UI elements that are always visible or accessible during gameplay, such as score displays, health meters, and menu buttons. Including a HUD is essential for most games because it displays information that helps players to be successful in their gameplay objectives.

A common HUD element is a health meter with an icon on the left which can be adapted into a timer bar, progress bar, or similar.

 ![In-game view showing custom health meter in upper-right region.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Intro.png)

Using [Hazardous Space Station](https://www.roblox.com/games/99416825187098/Hazardous-Space-Station)  as a starting place and [UI Fundamentals - HUD Meter](https://www.roblox.com/games/104506915856758/UI-Fundamentals-HUD-Meter)  as a finished reference place, this tutorial demonstrates:

-

Setup and use of the Device Emulator  to test your design on multiple emulated screens.

-

Usage of [StarterGui](/docs/reference/engine/classes/StarterGui)  as both a design and storage container.

-

How to position/size UI elements around built‑in Roblox controls and device notches/islands, such as the camera notch on modern phones.

-

How to replace the default Roblox health meter with your own meter and hook it up to the character's health level.

-

How to animate the center portion of the health meter and set its color between five color gradient keypoints (red, orange, yellow, lime, green).

## [Enable the Device Emulator](#enable-the-device-emulator)[](#enable-the-device-emulator)

Roblox is inherently [cross‑platform](/docs/projects/cross-platform) , as players can discover and join games on their phone or tablet, then later continue where they left off on their PC or console. Mobile devices (phones and tablets) have the least amount of screen space, so it's important that your UI elements fit on smaller screens and that they're clearly visible to players.

The best way to test UI designs across platforms is Studio's [Device Emulator](/docs/studio/testing-modes#device-emulation) . This tool provides a preset selection of devices and allows you to add your own custom presets.

1.

Open the [Hazardous Space Station](https://www.roblox.com/games/99416825187098/Hazardous-Space-Station)  template in Studio.

2.

From Studio's Test  menu, toggle on Device Emulator .

3.

From the bar directly above the main viewport, select a phone emulation such as iPhone X  or Samsung Galaxy A51 . Then, set the view size to Fit to Window  to utilize the maximum space in Studio.

 ![Device Emulator settings options indicated at top of viewport window.](https://prod.docsiteassets.roblox.com/assets/studio/general/Device-Emulator-Phone.png)

## [Create a screen container](#create-a-screen-container)[](#create-a-screen-container)

A [ScreenGui](/docs/reference/engine/classes/ScreenGui)  container holds UI objects ([GuiObjects](/docs/reference/engine/classes/GuiObject) ) to display on a player's screen (in this tutorial, the entirety of the health meter). To display a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  and its child objects to every player who joins the game, place it inside the [StarterGui](/docs/reference/engine/classes/StarterGui)  container. When a player joins and their character first spawns, the [ScreenGui](/docs/reference/engine/classes/ScreenGui)  and its contents clone into the [PlayerGui](/docs/reference/engine/classes/PlayerGui)  container for that player, located within the [Players](/docs/reference/engine/classes/Players)  container.

 ![Diagram of how a ScreenGui clones from StarterGui to a player's PlayerGui](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/StarterGui-To-PlayerGui.png)

To insert an empty [ScreenGui](/docs/reference/engine/classes/ScreenGui) :

1.

In the Explorer  window, locate the [StarterGui](/docs/reference/engine/classes/StarterGui)  container.

 ![Explorer window showing the StarterGui container.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui.png)

2.

Hover over the container, click the ⊕ button, and insert a [ScreenGui](/docs/reference/engine/classes/ScreenGui) .

 ![ScreenGui inserted into the StarterGui container.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui.png)

3.

Rename the new container HUDContainer  to reflect its purpose.

 ![ScreenGui renamed to HUDContainer.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer.png)

### [Utilize safe areas](#utilize-safe-areas)[](#utilize-safe-areas)

Modern phones take advantage of the entire screen but typically include notches, cutouts, and other elements that occupy screen space. Every Roblox game also includes the top bar controls  for quick access to the main menu, [chat](/docs/chat/in-experience-text-chat) , [leaderboard](/docs/players/leaderboards) , and more.

 ![Mobile device showing Roblox top bar buttons and device cutout.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/Top-Bar-Cutout.png)

To ensure players can see and access all UI without obstruction, Roblox provides the [ScreenInsets](/docs/reference/engine/classes/ScreenGui#ScreenInsets)  property which controls the safe area  insets for the contents of a [ScreenGui](/docs/reference/engine/classes/ScreenGui) . Every UI object that you position inside a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  is relative to the inset bounds.

 ![Mobile device showing the core UI safe area.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/CoreUISafeInsets.png)

While the default of [CoreUISafeInsets](/docs/reference/engine/enums/ScreenInsets)  ensures all UI objects remain clear of Roblox UI and device cutouts, [DeviceSafeInsets](/docs/reference/engine/enums/ScreenInsets)  can be a better option to utilize limited screen space, as illustrated below.

CoreUISafeInsets DeviceSafeInsets

[CoreUISafeInsets](/docs/reference/engine/enums/ScreenInsets)  keeps the meter clear of all obstructions, but it adds a large gap between the meter and the physical top edge of the screen.

![ScreenInsets set to CoreUISafeInsets.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-CoreUISafeInsets.png)

1.

In the Explorer  window, select HUDContainer .

 ![Explorer window showing the HUDContainer selected.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer.png)

2.

In the [Properties](/docs/studio/properties)  window, set the [ScreenInsets](/docs/reference/engine/classes/ScreenGui#ScreenInsets)  property to [DeviceSafeInsets](/docs/reference/engine/enums/ScreenInsets) .

 ![ScreenInsets set to DeviceSafeInsets in the Properties window.](https://prod.docsiteassets.roblox.com/assets/studio/properties/ScreenGui-ScreenInsets-DeviceSafeInsets.png)

### [Set edge padding](#set-edge-padding)[](#set-edge-padding)

With [ScreenInsets](/docs/reference/engine/classes/ScreenGui#ScreenInsets)  set to [DeviceSafeInsets](/docs/reference/engine/enums/ScreenInsets) , content can now extend directly up to the physical top edge of the screen. However, a small amount of padding  can help push the health meter (and other objects inside the container) slightly away from the screen edges for a cleaner appearance and to prevent them from being clipped.

 ![Screen container with padding around all edges.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/ScreenGui-With-Padding.png)

One way to apply padding to a UI container is through the insertion of a [UIPadding](/docs/reference/engine/classes/UIPadding)  modifier:

1.

Insert a [UIPadding](/docs/reference/engine/classes/UIPadding)  modifier into HUDContainer .

 ![HUDContainer with UIPadding modifier inserted.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-UIPadding.png)

2.

With the new [UIPadding](/docs/reference/engine/classes/UIPadding)  object selected, enter a value of 0, 16  for all edges of the container ([PaddingBottom](/docs/reference/engine/classes/UIPadding#PaddingBottom) , [PaddingLeft](/docs/reference/engine/classes/UIPadding#PaddingLeft) , [PaddingRight](/docs/reference/engine/classes/UIPadding#PaddingRight) , [PaddingTop](/docs/reference/engine/classes/UIPadding#PaddingTop) ). This applies padding of 16 pixels all around the container, regardless of the screen's resolution.

 ![Properties window showing the UIPadding modifier with 0, 16 set for all edges.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-UIPadding-Values.png)

## [Construct the health meter](#construct-the-health-meter)[](#construct-the-health-meter)

With the [screen container configured](#create-a-screen-container) , you can begin constructing the health meter using Roblox UI objects such as [frames](/docs/ui/frames)  and an [image label](/docs/ui/labels) .

 ![Basic components used for the health meter.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Components.png)

### [Create the parent frame](#create-the-parent-frame)[](#create-the-parent-frame)

Similar to design applications like Figma and Photoshop, a [Frame](/docs/reference/engine/classes/Frame)  in Roblox serves as a container for other UI objects. For this tutorial, the entire health meter will be contained in a single parent frame, making it simple to reposition across various HUD layouts.

1.

Insert a [Frame](/docs/reference/engine/classes/Frame)  into HUDContainer . The new frame appears in the upper-left corner as an empty white square.

 ![New frame in viewport.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame.png)

If the new frame doesn't appear in the viewport, make sure you've toggled on GUI overlay  from the [Visualization Options](/docs/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

2.

Rename the new frame instance to MeterBar .

 ![New frame inserted and renamed to MeterBar.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar.png)

### [Position the frame](#position-the-frame)[](#position-the-frame)

In Roblox, the position of a UI object is represented by a [UDim2](/docs/reference/engine/datatypes/UDim2)  coordinate set containing [Scale](/docs/reference/engine/datatypes/UDim#Scale)  and [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values for both the X  and Y  axes:

-

[Scale](/docs/reference/engine/datatypes/UDim#Scale)  values represent a percentage  of the container's size along the corresponding axis, additive of any [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values.

-

[Offset](/docs/reference/engine/datatypes/UDim#Offset)  values represent how many pixels  to shift the object on the corresponding axis, additive of any [Scale](/docs/reference/engine/datatypes/UDim#Scale)  values.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/UDim2-Components.png)

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Scale-Offset-Positioning.png)

To position a UI object in the upper-right corner of the screen container, [Scale](/docs/reference/engine/datatypes/UDim#Scale)  is the best approach because an X  value of 1  (100%) represents the right edge of the container, regardless of the screen's physical pixel size. Similarly, a Y  scale value of 0  (0%) represents the top edge of the container.

 ![Scale ranges for the X and Y axes of a container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/ScreenGui-Axis-Ranges.png)

Additionally, you'll need to set an upper-right [anchor point](/docs/ui/position-and-size#anchorpoint)  for the parent frame to define its origin point. Acceptable values are between 0  and 1 , relative to the size of the object, so an anchor value of 1, 0  puts the frame's anchor point in its upper‑right corner.

 ![Frame anchor point in its upper-right corner.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Anchor.png)

1.

In the Explorer  window, select the MeterBar  frame that you inserted previously.

 ![Explorer window showing the MeterBar frame selected.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar.png)

2.

In the Properties  window, enter 1, 0, 0, 0  for [Position](/docs/reference/engine/classes/Frame#Position)  and press Enter . Studio will automatically add the brackets to form the [UDim2](/docs/reference/engine/datatypes/UDim2)  of {1, 0},{0, 0} .

3.

Enter 1, 0  for the [AnchorPoint](/docs/reference/engine/classes/Frame#AnchorPoint)  property. The frame should now be positioned in the upper‑right corner of the [device safe area](#utilize-safe-areas) , slightly indented from the edge as a result of the [padding](#set-edge-padding) .

 ![Frame repositioned in upper-right corner of container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Repositioned.png)

### [Resize the frame](#resize-the-frame)[](#resize-the-frame)

Like position, the [Size](/docs/reference/engine/classes/Frame#Size)  of a UI object is represented by a [UDim2](/docs/reference/engine/datatypes/UDim2)  coordinate set containing [Scale](/docs/reference/engine/datatypes/UDim#Scale)  and [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values for both the X  and Y  axes.

By default, the new frame's size is {0, 100},{0, 100} , meaning 100 pixels  in both width (X ) and height (Y ). While a strict pixel value is useful in certain cases, many UI elements scale more responsively across multiple screens when set to a percentage  of the overall screen container size.

1.

With the MeterBar  frame selected, access the Properties  window and navigate to the [Size](/docs/reference/engine/classes/Frame#Size)  property.

2.

Enter a value of 0.35, 0, 0.05, 0  to set a percentage size of 35% wide and 5% tall with no added pixel offsets.

 ![Frame resized to 35% wide and 5% tall.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Resized.png)

### [Style the frame](#style-the-frame)[](#style-the-frame)

By default, [Frames](/docs/reference/engine/classes/Frame)  are filled in solid white. The final health meter should have a darker and slightly opaque fill, as well as a dark outline, so that it stands out better on both light and dark backgrounds.

 ![Frame styled with opacity, border, and rounded corners.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Preview.png)

1.

With the MeterBar  frame selected, enter 0  for the [BackgroundColor3](/docs/reference/engine/classes/Frame#BackgroundColor3)  property. Studio will automatically convert it to the RGB value of [0, 0, 0] .

2.

Enter 0.75  for the [BackgroundTransparency](/docs/reference/engine/classes/Frame#BackgroundTransparency)  property. In Roblox, transparency ranges from 0  for fully opaque to 1  for fully transparent, so 0.75  equals 25% opacity in other applications such as Figma or Photoshop.

 ![Frame restyled with dark background and 25% opacity.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Opaque.png)

3.

Insert a [UIStroke](/docs/reference/engine/classes/UIStroke)  object, a powerful UI modifier that adds a [customizable stroke](/docs/ui/appearance-modifiers#stroke)  to the frame.

 ![Explorer window showing the MeterBar frame with a child UIStroke modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UIStroke.png)

4.

With the new [UIStroke](/docs/reference/engine/classes/UIStroke)  selected, set the following properties:

-

[Thickness](/docs/reference/engine/classes/UIStroke#Thickness)  = 3

-

[Transparency](/docs/reference/engine/classes/UIStroke#Transparency)  = 0.25  (75% opaque)

 ![Frame restyled with a UIStroke modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Stroked.png)

To finalize the meter frame's styling, you can round the corners to form a "pill" shape instead of a sharp rectangle.

1.

Insert a [UICorner](/docs/reference/engine/classes/UICorner)  instance into the MeterBar  frame.

 ![Explorer window showing the MeterBar frame with a child UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UICorner.png)

2.

With the new [UICorner](/docs/reference/engine/classes/UICorner)  selected, set the [CornerRadius](/docs/reference/engine/classes/UICorner#CornerRadius)  to 0.5, 0 . Using a scale  value of 0.5  (50%) instead of a pixel value is especially convenient for the meter bar because it ensures a fully rounded curve no matter how tall or wide the container becomes.

 ![Frame corners rounded with a UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Rounded.png)

### [Create the inner fill](#create-the-inner-fill)[](#create-the-inner-fill)

Now that the health meter's containing frame is complete, you can add an inner fill  portion to represent the character's variable health. Since it only needs to be a solid‑filled region, a sub‑child [Frame](/docs/reference/engine/classes/Frame)  inside the parent frame is suitable.

 ![Inner fill frame added to parent frame to represent the character's variable health.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Preview.png)

1.

Insert a child [Frame](/docs/reference/engine/classes/Frame)  into the MeterBar  frame.

2.

Rename the new frame instance to InnerFill .

 ![Explorer window showing the parent MeterBar frame with a child frame named InnerFill.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-InnerFill.png)

3.

With InnerFill  selected, set the following properties:

-

[AnchorPoint](/docs/reference/engine/classes/Frame#AnchorPoint)  = 0, 0.5  (left edge and vertical center)

-

[Position](/docs/reference/engine/classes/Frame#Position)  = 0, 0, 0.5, 0

-

[Size](/docs/reference/engine/classes/Frame#Size)  = 1, 0, 1, 0

Since children of frames are positioned and sized relative to their parent, use of scale makes the inner frame fill the parent's full width and height, starting from the parent's left edge.

 ![Inner fill frame repositioned and resized to fill entire parent frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Resized.png)

4.

To match the "pill" shape of the parent frame, insert an additional [UICorner](/docs/reference/engine/classes/UICorner)  into InnerFill .

 ![Explorer window showing the InnerFill frame with a child UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-InnerFill-UICorner.png)

5.

With the new [UICorner](/docs/reference/engine/classes/UICorner)  modifier selected, set its [CornerRadius](/docs/reference/engine/classes/UICorner#CornerRadius)  property to 0.5, 0  to match the "pill" shape of the parent MeterBar  frame.

 ![Inner fill frame corners rounded with a UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Rounded.png)

6.

To better represent that a full meter indicates good health, select InnerFill  and set its [BackgroundColor3](/docs/reference/engine/classes/Frame#BackgroundColor3)  property to [0, 225, 50]  (in a later task, you'll [script](#listen-for-health-changes)  this color to change based on actual health).

 ![Inner fill frame recolored green to represent good health.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Colored.png)

### [Add the icon](#add-the-icon)[](#add-the-icon)

To more clearly indicate the purpose of the meter, you can add an [image label](/docs/ui/labels)  to the left side, in this case a red heart which commonly symbolizes health or life.

 ![Image label of heart added to more clearly indicate a health meter.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Icon-Preview.png)

1.

Insert an [ImageLabel](/docs/reference/engine/classes/ImageLabel)  into the MeterBar  frame. This object lets you apply a 2D image asset that has been uploaded as a decal to Roblox.

2.

Rename the new label instance to Icon .

 ![Explorer window showing the MeterBar frame with a child ImageLabel.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-Icon.png)

3.

With Icon  selected, set its [ZIndex](/docs/reference/engine/classes/ImageLabel#ZIndex)  property to 2 . While newly inserted UI objects always layer in front of objects inserted previously, this change ensures the icon always displays in front of the meter's frame elements.

 ![Properties window showing the ZIndex of the ImageLabel set to 2.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-Icon-Values.png)

4.

Locate the icon's [Image](/docs/reference/engine/classes/ImageLabel#Image)  property and enter rbxassetid://91715286435585 , the reference to a pre‑uploaded heart image (if desired, you can [import](/docs/projects/assets/manager#asset-import)  your own image and use its asset ID).

 ![Image label of heart added to MeterBar frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Icon-Large.png)

5.

To ensure the icon [ImageLabel](/docs/reference/engine/classes/ImageLabel)  always stays at a 1:1 aspect ratio, insert a [UIAspectRatioConstraint](/docs/reference/engine/classes/UIAspectRatioConstraint) . Although this [constraint](/docs/ui/size-modifiers#constraints)  has customizable properties to control the aspect ratio, you can leave its default values intact.

 ![Explorer window showing the ImageLabel with a child UIAspectRatioConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-Icon-UIAspectRatioConstraint.png)

6.

With Icon  selected, finalize the appearance and position by changing the following properties:

-

[AnchorPoint](/docs/reference/engine/classes/ImageLabel#AnchorPoint)  = 0.5, 0.5  (center anchor)

-

[BackgroundTransparency](/docs/reference/engine/classes/ImageLabel#BackgroundTransparency)  = 1  (100% transparent)

-

[Position](/docs/reference/engine/classes/ImageLabel#Position)  = 0, 0, 0.5, 0  (left side of meter and vertical center)

-

[Size](/docs/reference/engine/classes/ImageLabel#Size)  = 2, 0, 2, 0  (200% the overall size of the MeterBar  frame, constrained to 1:1 by the [UIAspectRatioConstraint](/docs/reference/engine/classes/UIAspectRatioConstraint) )

 ![Image label of heart repositioned and resized with background fill made transparent.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Icon-Finalized.png)

### [Constrain the size](#constrain-the-size)[](#constrain-the-size)

While a [scale height](#resize-the-frame)  of 0.05  (5%) looks good on modern phone screens and gaming monitors which are 16:9 aspect ratio or wider, the meter may look slightly too tall on tablet screens and older phones. You can check this by emulating a tablet like iPad 7th Generation  from the Device Emulator .

 ![Device Emulator set to emulate a tablet device.](https://prod.docsiteassets.roblox.com/assets/studio/general/Device-Emulator-Tablet.png)  ![Emulation on tablet device with meter bar taller than desired.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Emulation-Tablet-Unconstrained.png)

To keep the meter bar's height more consistent with wider screens, you can apply a [UISizeConstraint](/docs/reference/engine/classes/UISizeConstraint)  to limit the maximum pixel height.

1.

Insert a [UISizeConstraint](/docs/reference/engine/classes/UISizeConstraint)  into the MeterBar  frame.

 ![Explorer window showing the MeterBar frame with a child UISizeConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UISizeConstraint.png)

2.

With the new constraint selected, set its [MaxSize](/docs/reference/engine/classes/UISizeConstraint#MaxSize)  property to inf, 20  to restrict its height to 20 pixels while enforcing no width restriction.

 ![Properties window showing the MaxSize of the UISizeConstraint set to inf, 20.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UISizeConstraint-Values.png)

Now, the meter bar maintains a more consistent height between wider and taller screens.

Phone Tablet

![Emulation on phone.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Emulation-Phone-Constrained.png)

## [Replace the default health meter](#replace-the-default-health-meter)[](#replace-the-default-health-meter)

Roblox games include a default health meter which becomes visible when characters take damage. If you keep the default meter visible, it will duplicate and potentially overlap the custom meter.

 ![Default health meter overlapping and duplicating the custom health meter.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Default-Health-Meter.png)

### [Disable the default meter](#disable-the-default-meter)[](#disable-the-default-meter)

To disable the default health meter, you'll use a client script  ([LocalScript](/docs/reference/engine/classes/LocalScript) ) within [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts)  that calls [StarterGui:SetCoreGuiEnabled()](/docs/reference/engine/classes/StarterGui#SetCoreGuiEnabled) .

1.

In the Explorer  window, expand the [StarterPlayer](/docs/reference/engine/classes/StarterPlayer)  container and locate the [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts)  container within it.

 ![Explorer window showing the StarterPlayerScripts container inside the StarterPlayer container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterPlayerScripts.png)

2.

Insert a new [LocalScript](/docs/reference/engine/classes/LocalScript)  into the container and rename it to HideDefaultHealthMeter  to describe its purpose. Scripts within [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts)  automatically run when the local player joins a game, making it an ideal container to run a script that permanently hides the default meter.

 ![Explorer window showing the new HideDefaultHealthMeter client script inside the StarterPlayerScripts container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterPlayerScripts-HideDefaultHealthMeter.png)

3.

When you insert a new script, it automatically opens in a new script editor tab (if it doesn't, double‑click the script in the Explorer  window).

Paste the following code inside the HideDefaultHealthMeter  script:

HideDefaultHealthMeter

```

local StarterGui = game:GetService("StarterGui")

-- Hide default health meter

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

```

Code Explanation

| Line | | Purpose |
| --- | --- |
| 1 | | Gets a reference to a core [service](/docs/scripting/services) , [StarterGui](/docs/reference/engine/classes/StarterGui) , which represents the same container where you created the custom health meter and whose contents clone into the [PlayerGui](/docs/reference/engine/classes/PlayerGui)  container for each player that joins the game. |
| 4 | | Calls the service's [SetCoreGuiEnabled()](/docs/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  method and instructs the default health meter to be disabled (false ). |

If you playtest the game now and take damage, you'll notice that the default meter is disabled and hidden (you'll script the custom meter to [reflect health changes](#listen-for-health-changes)  in the next section).

 ![Default health meter disabled.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Default-Health-Meter-Disabled.png)

### [Listen for health changes](#listen-for-health-changes)[](#listen-for-health-changes)

All default Roblox character models contain a [Humanoid](/docs/reference/engine/classes/Humanoid)  class which provides special behaviors and functionality to the character, such as setting its walk/run speed and managing its health. [Health](/docs/reference/engine/classes/Humanoid#Health)  changes on the server [replicate](/docs/projects/client-server#replication)  to each player's client and you can detect these changes to update both the size and color of the custom health meter.

1.

In the Explorer  window, locate the [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts)  container within [StarterPlayer](/docs/reference/engine/classes/StarterPlayer) .

 ![Explorer window showing the StarterCharacterScripts container inside the StarterPlayer container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterCharacterScripts.png)

2.

Insert a new [LocalScript](/docs/reference/engine/classes/LocalScript)  into the container and rename it to UpdateCustomMeter  to describe its purpose. Scripts within [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts)  automatically run each time the player's character spawns, making it an ideal container to run a script that fully resets the health meter on each respawn.

 ![Explorer window showing the new UpdateCustomMeter client script inside the StarterCharacterScripts container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterCharacterScripts-UpdateCustomMeter.png)

3.

In the editor window for the UpdateCustomMeter  script, paste the following code:

UpdateCustomMeter

```

local Players = game:GetService("Players")

-- Reference to local player, character, and humanoid

local player = Players.LocalPlayer

local character = player.Character

local humanoid = character:WaitForChild("Humanoid")

-- Reference to meter bar inner frame

local playerGui = player:WaitForChild("PlayerGui")

local meterBarInner = playerGui.HUDContainer.MeterBar.InnerFill

-- Gradient sequence colors (red, orange, yellow, lime, green)

local gradient = {

	Color3.fromRGB(225, 50, 0),

	Color3.fromRGB(255, 100, 0),

	Color3.fromRGB(255, 200, 0),

	Color3.fromRGB(150, 225, 0),

	Color3.fromRGB(0, 225, 50)

}

-- Function to get color in gradient sequence from fractional point

local function getColorFromSequence(fraction: number): Color3

	-- Each color in gradient defines the beginning and/or end of a section

	local numSections = #gradient - 1

	-- Each section represents a portion of 1

	local sectionSize = 1 / numSections

	-- Determine which section the requested fraction falls into

	local sectionStartIndex = 1 + math.clamp(fraction, 0, 1) // sectionSize

	-- Get the colors at the start and end of the section

	local sectionColorStart = gradient[sectionStartIndex]

	local sectionColorEnd = gradient[sectionStartIndex + 1] or sectionColorStart

	-- Normalize fraction to be a number from 0 to 1 within the section

	local fractionOfSection = math.clamp(fraction, 0, 1) % sectionSize / sectionSize

	-- Lerp between beginning and end based on the normalized fraction

	return sectionColorStart:Lerp(sectionColorEnd, fractionOfSection)

end

local function onHealthChanged()

	-- Calculate new health as percentage of max

	local healthFraction = math.max(0, humanoid.Health / humanoid.MaxHealth)

	-- Set the bar to new size/color targets

	meterBarInner.Size = UDim2.new(healthFraction, 0, 1, 0)

	meterBarInner.BackgroundColor3 = getColorFromSequence(healthFraction)

end

-- Listen for changes to humanoid health

humanoid.HealthChanged:Connect(onHealthChanged)

-- Initially set (or reset) bar size/color to current health

onHealthChanged()

```

Code Explanation

| Lines | | Purpose |
| 4 ‑ 6 | | Gets references to the local [Player](/docs/reference/engine/classes/Player) , their [Character](/docs/reference/engine/classes/Player#Character)  model, and the [Humanoid](/docs/reference/engine/classes/Humanoid)  class within it. |
| 9 ‑ 10 | | Gets a reference to the meter's InnerFill  object which must be resized and recolored as the character's health changes. |
| 13 ‑ 19 | | Declares an array of five colors (red, orange, yellow, lime, green) to recolor the meter at various points; for example, green for 100% health, yellow for 50%, red for 0%, or a blend at any fraction between the keypoints. |
| 22 ‑ 41 | | Helper function which returns the color blend between any of the gradient color keypoints. |
| 43 ‑ 50 | | Function which handles any changes to health. Here, it calculates the new health as a percentage of the character's [MaxHealth](/docs/reference/engine/classes/Humanoid#MaxHealth) , resizes InnerFill  to that scale percentage, and recolors it to the color returned from the getColorFromSequence()  function. |
| 53 | | The main [event](/docs/scripting/events)  connection which detects [Health](/docs/reference/engine/classes/Humanoid#Health)  changes replicated from the server and calls the onHealthChanged()  function. |
| 56 | | Initially (upon character spawn or respawn) calls the onHealthChanged()  function to size and color InnerFill  to the correct percentage. Typically this will be the full width and green. |

If you playtest the game now, you'll notice that the custom meter correctly updates both size and color as the character takes damage:

By default, the Roblox health metering system includes a gradual healing effect which allows characters to slowly regenerate health. If you wish to disable this effect, insert an empty [Script](/docs/reference/engine/classes/Script)  named Health  into the [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts)  container. This will prevent the default internal script from loading for each player character, effectively removing the regeneration effect.

### [Animate the meter bar](#animate-the-meter-bar)[](#animate-the-meter-bar)

To add an extra level of polish to the custom meter, you can animate health changes through tweening , gradually changing the meter bar's size and color over ½ second.

1.

Access the script editor tab for the UpdateCustomMeter  script that you edited previously.

2.

Select all lines (Ctrl A  or ⌘ A ) and then paste over them (Ctrl V  or ⌘ V ) with the following code:

UpdateCustomMeter

```

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

-- Reference to local player, character, and humanoid

local player = Players.LocalPlayer

local character = player.Character

local humanoid = character:WaitForChild("Humanoid")

-- Tween properties

local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out)

-- Reference to meter bar inner frame

local playerGui = player:WaitForChild("PlayerGui")

local meterBarInner = playerGui.HUDContainer.MeterBar.InnerFill

-- Gradient sequence colors (red, orange, yellow, lime, green)

local gradient = {

	Color3.fromRGB(225, 50, 0),

	Color3.fromRGB(255, 100, 0),

	Color3.fromRGB(255, 200, 0),

	Color3.fromRGB(150, 225, 0),

	Color3.fromRGB(0, 225, 50)

}

-- Function to get color in gradient sequence from fractional point

local function getColorFromSequence(fraction: number): Color3

	-- Each color in gradient defines the beginning and/or end of a section

	local numSections = #gradient - 1

	-- Each section represents a portion of 1

	local sectionSize = 1 / numSections

	-- Determine which section the requested fraction falls into

	local sectionStartIndex = 1 + math.clamp(fraction, 0, 1) // sectionSize

	-- Get the colors at the start and end of the section

	local sectionColorStart = gradient[sectionStartIndex]

	local sectionColorEnd = gradient[sectionStartIndex + 1] or sectionColorStart

	-- Normalize fraction to be a number from 0 to 1 within the section

	local fractionOfSection = math.clamp(fraction, 0, 1) % sectionSize / sectionSize

	-- Lerp between beginning and end based on the normalized fraction

	return sectionColorStart:Lerp(sectionColorEnd, fractionOfSection)

end

local function onHealthChanged()

	-- Calculate new health as percentage of max

	local healthFraction = math.max(0, humanoid.Health / humanoid.MaxHealth)

	-- Tween the bar to new size/color targets

	local tweenGoal = {

		Size = UDim2.new(healthFraction, 0, 1, 0),

		BackgroundColor3 = getColorFromSequence(healthFraction)

	}

	local meterBarTween = TweenService:Create(meterBarInner, tweenInfo, tweenGoal)

	meterBarTween:Play()

end

-- Listen for changes to humanoid health

humanoid.HealthChanged:Connect(onHealthChanged)

-- Initially set (or reset) bar size/color to current health

onHealthChanged()

```

Key Additions/Changes

| Lines | | Purpose |
| 2 | | Gets a reference to [TweenService](/docs/reference/engine/classes/TweenService)  to implement tweening functionality within the script. |
| 10 | | Creates a [TweenInfo](/docs/reference/engine/datatypes/TweenInfo)  constructor which defines the intended tween's duration, [easing style](/docs/ui/animation#style) , and [easing direction](/docs/ui/animation#direction) . |
| 52 ‑ 57 | | Instead of simply setting the bar's size and color as in the [previous version](#listen-for-health-changes) , declares a tweenGoal  table with the target size/color, creates a new tween using the tweenInfo  and tweenGoal  parameters, and plays the new tween. |

If you playtest the game now, you'll notice that the custom meter tweens between each change in health:

### [Add a damage effect](#add-a-damage-effect)[](#add-a-damage-effect)

The default health meter system includes a brief, subtle red tint on the screen edges when the character is damaged. By [disabling the default meter](#disable-the-default-meter) , this effect is removed, but you can replace it with your own implementation.

1.

Access the script editor tab for the UpdateCustomMeter  script that you edited previously.

2.

Select all lines and paste over them with the following code:

UpdateCustomMeter

```

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

-- Reference to local player, character, and humanoid

local player = Players.LocalPlayer

local character = player.Character

local humanoid = character:WaitForChild("Humanoid")

-- Tween properties

local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out)

-- Variable to store/cache character health

local cachedHealth = humanoid.Health / humanoid.MaxHealth

-- Get (or create new) color correction effect inside player camera

local colorCorrection = Workspace.CurrentCamera:FindFirstChildWhichIsA("ColorCorrectionEffect") or Instance.new("ColorCorrectionEffect", Workspace.CurrentCamera)

colorCorrection.Name = "DamageColorEffect"

-- Reference to meter bar inner frame

local playerGui = player:WaitForChild("PlayerGui")

local meterBarInner = playerGui.HUDContainer.MeterBar.InnerFill

-- Gradient sequence colors (red, orange, yellow, lime, green)

local gradient = {

	Color3.fromRGB(225, 50, 0),

	Color3.fromRGB(255, 100, 0),

	Color3.fromRGB(255, 200, 0),

	Color3.fromRGB(150, 225, 0),

	Color3.fromRGB(0, 225, 50)

}

-- Function to get color in gradient sequence from fractional point

local function getColorFromSequence(fraction: number): Color3

	-- Each color in gradient defines the beginning and/or end of a section

	local numSections = #gradient - 1

	-- Each section represents a portion of 1

	local sectionSize = 1 / numSections

	-- Determine which section the requested fraction falls into

	local sectionStartIndex = 1 + math.clamp(fraction, 0, 1) // sectionSize

	-- Get the colors at the start and end of the section

	local sectionColorStart = gradient[sectionStartIndex]

	local sectionColorEnd = gradient[sectionStartIndex + 1] or sectionColorStart

	-- Normalize fraction to be a number from 0 to 1 within the section

	local fractionOfSection = math.clamp(fraction, 0, 1) % sectionSize / sectionSize

	-- Lerp between beginning and end based on the normalized fraction

	return sectionColorStart:Lerp(sectionColorEnd, fractionOfSection)

end

local function onHealthChanged()

	-- Calculate new health as percentage of max

	local healthFraction = math.max(0, humanoid.Health / humanoid.MaxHealth)

	-- Tween the bar to new size/color targets

	local tweenGoal = {

		Size = UDim2.new(healthFraction, 0, 1, 0),

		BackgroundColor3 = getColorFromSequence(healthFraction)

	}

	local meterBarTween = TweenService:Create(meterBarInner, tweenInfo, tweenGoal)

	meterBarTween:Play()

	-- Show damage effect if new health is lower than cached health

	if healthFraction < cachedHealth then

		-- Cache new health value

		cachedHealth = healthFraction

		-- Set color correction to red as the initial tint before tweening

		colorCorrection.TintColor = Color3.fromRGB(255, 25, 25)

		colorCorrection.Saturation = 2.5

		-- Tween the tint back to white (neutral and no tint change from normal)

		local colorCorrectionTweenGoal = {

			TintColor = Color3.fromRGB(255, 255, 255),

			Saturation = 0

		}

		local colorCorrectionTween = TweenService:Create(colorCorrection, tweenInfo, colorCorrectionTweenGoal)

		colorCorrectionTween:Play()

	end

end

-- Listen for changes to humanoid health

humanoid.HealthChanged:Connect(onHealthChanged)

-- Initially set (or reset) bar size/color to current health

onHealthChanged()

```

Key additions/changes

| Lines | | Purpose |
| 14 | | Sets a placeholder reference (cachedHealth ) to track the character's health amount between changes, so you can compare if a change is lower (damage). |
| 17 ‑ 18 | | On the initial character spawn, creates a new [ColorCorrectionEffect](/docs/reference/engine/classes/ColorCorrectionEffect)  inside the player's current [Camera](/docs/reference/engine/classes/Camera) , or gets a reference to the same instance on later respawns. By parenting this [post‑processing effect](/docs/environment/post-processing-effects)  to the player's camera, it only applies to their local screen, not to every player's screen on the server. |
| 68 ‑ 83 | | First performs a conditional check to confirm that the health change is lower than the cachedHealth  value, indicating damage; if so, it sets cachedHealth  to the new value. Next, it sets the [ColorCorrectionEffect](/docs/reference/engine/classes/ColorCorrectionEffect)  tint to [255, 25, 25]  (red) with higher saturation, then tweens the tint back to the default of neutral white ([255, 255, 255] ) with no saturation. |

If you playtest the game now, you'll notice that the screen briefly flashes red whenever the character takes damage:

If you decide to adapt the custom meter bar to another purpose, such as a mana meter or poison meter, you can change the [TintColor](/docs/reference/engine/classes/ColorCorrectionEffect#TintColor)  on line 73  to something more suitable to the event, such as light blue ([200, 225, 255] )  or toxic green ([0, 255, 75] ) .

If your health meter doesn't match the appearance or behavior displayed in this tutorial, remember that you can inspect [UI Fundamentals - HUD Meter](https://www.roblox.com/games/104506915856758/UI-Fundamentals-HUD-Meter)  as a completed reference template.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
