<!-- Source: https://create.roblox.com/docs/ui/ui-drag-detectors -->

UI drag detectors | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/ui-drag-detectors.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)
6. /
7. UI objects

# UI drag detectors

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/ui-drag-detectors.md)

The [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  instance facilitates and encourages interaction with 2D user interface elements in a game, such as sliders, spinners, and more. Key features include:

-

Place a [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  under any [GuiObject](/docs/reference/engine/classes/GuiObject)  instance to make it draggable via all user inputs without a single line of code.

-

Choose from several [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  options, define how the object responds to motion via [ResponseStyle](/docs/reference/engine/classes/UIDragDetector#ResponseStyle) , and optionally apply axis, movement limits, or drag boundaries.

-

Scripts can respond to manipulation of dragged objects to drive logic responses, such as adjusting settings.

-

[UIDragDetectors](/docs/reference/engine/classes/UIDragDetector)  work in Studio's edit and play mode as long as you're not  using the Select , Move , Scale , or Rotate  tools, nor certain plugins or Studio's UI  editor tools.

For drag detectors that manipulate 3D objects in a game, such as opening doors and drawers or sliding a part around, see [3D Drag Detectors](/docs/ui/3D-drag-detectors) .

## [Make UI elements draggable](#make-ui-elements-draggable)[](#make-ui-elements-draggable)

To make any [GuiObject](/docs/reference/engine/classes/GuiObject)  instances draggable, simply add a [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  as a direct descendant.

1.

In the [Explorer](/docs/studio/explorer)  window, hover over the [GuiObject](/docs/reference/engine/classes/GuiObject)  instance and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a UIDragDetector .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-UIDragDetector.png)

3.

By default, the object will now be draggable in the [LayerCollector](/docs/reference/engine/classes/LayerCollector)  interface.

Remember that [UIDragDetectors](/docs/reference/engine/classes/UIDragDetector)  only work in Studio if you're not  using the Select , Move , Scale , or Rotate  tools, nor certain plugins or Studio's UI  editor tools.

## [Customize UI drag detectors](#customize-ui-drag-detectors)[](#customize-ui-drag-detectors)

### [Drag style](#drag-style)[](#drag-style)

[UIDragDetectors](/docs/reference/engine/classes/UIDragDetector)  map cursor motion to calculate proposed 2D motion and/or rotation. Through the [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  property, you can choose from different mappings to suit your needs. For example, [Enum.UIDragDetectorDragStyle.TranslatePlane](/docs/reference/engine/enums/UIDragDetectorDragStyle#TranslatePlane)  produces translation in the 2D plane of the [LayerCollector](/docs/reference/engine/classes/LayerCollector) , while [Enum.UIDragDetectorDragStyle.Rotate](/docs/reference/engine/enums/UIDragDetectorDragStyle#Rotate)  normally produces a rotation instead of translation.

| Setting | | Description |
| --- | --- |
| [TranslateLine](/docs/reference/engine/enums/UIDragDetectorDragStyle#TranslateLine) | | 1D motion along the detector's [DragAxis](/docs/reference/engine/classes/UIDragDetector#DragAxis) . |
| [TranslatePlane](/docs/reference/engine/enums/UIDragDetectorDragStyle#TranslatePlane) | | 2D motion in the plane of the [LayerCollector](/docs/reference/engine/classes/LayerCollector) . |
| [Rotate](/docs/reference/engine/enums/UIDragDetectorDragStyle#Rotate) | | By default, rotation about the absolute center position of the detector's parent [GuiObject](/docs/reference/engine/classes/GuiObject) . If [ReferenceUIInstance](/docs/reference/engine/classes/UIDragDetector#ReferenceUIInstance)  is set, rotation happens about that instance's absolute center position. |
| [Scriptable](/docs/reference/engine/enums/UIDragDetectorDragStyle#Scriptable) | | Calculates desired motion via a custom function provided through [SetDragStyleFunction()](/docs/reference/engine/classes/UIDragDetector#SetDragStyleFunction) . |

### [Drag direction](#drag-direction)[](#drag-direction)

By default, 2D motion and the associated [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  map to the space of the ancestor [LayerCollector](/docs/reference/engine/classes/LayerCollector) . However, you may want to change the [ReferenceUIInstance](/docs/reference/engine/classes/UIDragDetector#ReferenceUIInstance)  or the [DragAxis](/docs/reference/engine/classes/UIDragDetector#DragAxis)  when building different UI components.

| Setting | | Description | | Default |
| [ReferenceUIInstance](/docs/reference/engine/classes/UIDragDetector#ReferenceUIInstance) | | A [GuiObject](/docs/reference/engine/classes/GuiObject)  instance whose local space and absolute center position is the reference space and origin for the detector. Setting this reference affects properties such as [DragUDim2](/docs/reference/engine/classes/UIDragDetector#DragUDim2) , [DragRotation](/docs/reference/engine/classes/UIDragDetector#DragRotation) , and the behavior of [DragAxis](/docs/reference/engine/classes/UIDragDetector#DragAxis) . | | nil |
| [DragAxis](/docs/reference/engine/classes/UIDragDetector#DragAxis) | | [Vector2](/docs/reference/engine/datatypes/Vector2)  value that defines the axis of movement for the dragged object when [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  is set to [Enum.UIDragDetectorDragStyle.TranslateLine](/docs/reference/engine/enums/UIDragDetectorDragStyle#TranslateLine) . The axis is defined in the local space of the [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  unless [ReferenceUIInstance](/docs/reference/engine/classes/UIDragDetector#ReferenceUIInstance)  is defined, in which case the axis is defined in that instance's local space. | | (1, 0) |

### [Response to motion](#response-to-motion)[](#response-to-motion)

The [UIDragDetector.ResponseStyle](/docs/reference/engine/classes/UIDragDetector#ResponseStyle)  property specifies how an object's position value is changed by the proposed motion. The custom response styles let you use the resulting [UIDragDetector.DragUDim2](/docs/reference/engine/classes/UIDragDetector#DragUDim2)  and [UIDragDetector.DragRotation](/docs/reference/engine/classes/UIDragDetector#DragRotation)  values as desired, without having the detector's parent execute the proposed motion.

| Setting | | Description |
| [Offset](/docs/reference/engine/enums/UIDragDetectorResponseStyle#Offset) | | Move by the [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values of the detector's parent's [GuiObject.Position](/docs/reference/engine/classes/GuiObject#Position)  value. This is the setting by default. |
| [Scale](/docs/reference/engine/enums/UIDragDetectorResponseStyle#Scale) | | Move by the [Scale](/docs/reference/engine/datatypes/UDim#Scale)  values of the detector's parent's [GuiObject.Position](/docs/reference/engine/classes/GuiObject#Position)  value. |
| [CustomOffset](/docs/reference/engine/enums/UIDragDetectorResponseStyle#CustomOffset) | | The UI element will not move at all, but the [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values of the detector's [DragUDim2](/docs/reference/engine/classes/UIDragDetector#DragUDim2)  will still be updated and the detector's events will still fire, allowing you to respond to drag manipulation however you'd like. |
| [CustomScale](/docs/reference/engine/enums/UIDragDetectorResponseStyle#CustomScale) | | The UI element will not move at all, but the [Scale](/docs/reference/engine/datatypes/UDim#Scale)  values of the detector's [DragUDim2](/docs/reference/engine/classes/UIDragDetector#DragUDim2)  will still be updated and the detector's events will still fire, allowing you to respond to drag manipulation however you'd like. |

### [Translation & rotation limits](#translation--rotation-limits)[](#translation--rotation-limits)

By default, there are no limits to 2D motion behind the inherent restrictions of the [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle) . Limits for both minimum and maximum translations and rotations can be declared with the following properties if desired. Additionally, you can define how the dragged object is constrained within the bounds of a specified [GuiObject](/docs/reference/engine/classes/GuiObject)  such as a [Frame](/docs/reference/engine/classes/Frame) .

| Properties | | Description | | Default |
| [MinDragTranslation](/docs/reference/engine/classes/UIDragDetector#MinDragTranslation)
 [MaxDragTranslation](/docs/reference/engine/classes/UIDragDetector#MaxDragTranslation) | | Limits to drag translation in each dimension, defined by a [UDim2](/docs/reference/engine/datatypes/UDim2)  value. If [MaxDragTranslation](/docs/reference/engine/classes/UIDragDetector#MaxDragTranslation)  is greater than [MinDragTranslation](/docs/reference/engine/classes/UIDragDetector#MinDragTranslation) , translation will be clamped within that range. | | {0, 0}, {0, 0} |
| [MinDragAngle](/docs/reference/engine/classes/UIDragDetector#MinDragAngle)
 [MaxDragAngle](/docs/reference/engine/classes/UIDragDetector#MaxDragAngle) | | Only relevant if [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  is set to [Enum.UIDragDetectorDragStyle.Rotate](/docs/reference/engine/enums/UIDragDetectorDragStyle#Rotate) , or if the functions set through [SetDragStyleFunction()](/docs/reference/engine/classes/UIDragDetector#SetDragStyleFunction)  or [AddConstraintFunction()](/docs/reference/engine/classes/UIDragDetector#AddConstraintFunction)  defines a rotation value. If [MaxDragAngle](/docs/reference/engine/classes/UIDragDetector#MaxDragAngle)  is greater than [MinDragAngle](/docs/reference/engine/classes/UIDragDetector#MinDragAngle) , rotation will be clamped within that range. | | 0 |
| [BoundingBehavior](/docs/reference/engine/classes/UIDragDetector#BoundingBehavior) | | Determines the [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  instance's bounding behavior when its [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI)  is set. Setting this to [EntireObject](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior#EntireObject)  bounds the entire dragged UI within the [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI) , while setting it to [HitPoint](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior#HitPoint)  bounds the dragged UI only by the exact hit/grab point and its respective position after translation/rotation. As a convenience, the default of [Automatic](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior#Automatic)  mimics the [EntireObject](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior#EntireObject)  behavior for a UI object that's entirely contained by the [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI) , or else [HitPoint](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior#HitPoint)  for a UI object that's partially outside the [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI) . | | [Automatic](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior#Automatic) |

### [Speed adjustments](#speed-adjustments)[](#speed-adjustments)

Through [SelectionModeDragSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed)  and [SelectionModeRotateSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeRotateSpeed) , you can fine‑tune the maximum drag/rotate speeds for a detector. Furthermore, through [UIDragSpeedAxisMapping](/docs/reference/engine/classes/UIDragDetector#UIDragSpeedAxisMapping) , you can fine‑tune the X / Y  dimension dragging speeds, based on the detector's [SelectionModeDragSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed) .

| Property | | Description |
| [SelectionModeDragSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed) | | Defines the maximum drag speed for translation as a combination of [Scale](/docs/reference/engine/datatypes/UDim#Scale)  and [Offset](/docs/reference/engine/datatypes/UDim#Offset)  of the first ancestor [ScreenGui](/docs/reference/engine/classes/ScreenGui)  or [SurfaceGui](/docs/reference/engine/classes/SurfaceGui)  the [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  belongs to. |
| [SelectionModeRotateSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeRotateSpeed) | | Defines the maximum angle per second at which the [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)  can rotate. |
| [UIDragSpeedAxisMapping](/docs/reference/engine/classes/UIDragDetector#UIDragSpeedAxisMapping) | | Determines the X / Y  dimension dragging speeds, based on the detector's [SelectionModeDragSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed) . The default is [XY](/docs/reference/engine/enums/UIDragSpeedAxisMapping#XY) , meaning the X  and Y  axis speeds are based off the X  and Y  [Scale](/docs/reference/engine/datatypes/UDim#Scale) /[Offset](/docs/reference/engine/datatypes/UDim#Offset)  values respectively.
Alternatives are [XX](/docs/reference/engine/enums/UIDragSpeedAxisMapping)  and [YY](/docs/reference/engine/enums/UIDragSpeedAxisMapping) , meaning both the X  and Y  axis speeds are based off the X  ([XX](/docs/reference/engine/enums/UIDragSpeedAxisMapping) ) or Y  ([YY](/docs/reference/engine/enums/UIDragSpeedAxisMapping) ) axis for [Scale](/docs/reference/engine/datatypes/UDim#Scale) , while the [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values still apply to their respective axis. For example, if the first ancestor [ScreenGui](/docs/reference/engine/classes/ScreenGui)  is sized 800×600 and [SelectionModeDragSpeed](/docs/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed)  is {0.1, 10}, {0.1, 20} , a setting of [XX](/docs/reference/engine/enums/UIDragSpeedAxisMapping)  results in an X / Y  drag speed of 80+10 / 80+20 , while [YY](/docs/reference/engine/enums/UIDragSpeedAxisMapping)  results in 60+10 / 60+20  (note the [Offset](/docs/reference/engine/datatypes/UDim#Offset)  values remain the same in both cases). |

## [Script responses to clicking and dragging](#script-responses-to-clicking-and-dragging)[](#script-responses-to-clicking-and-dragging)

Through [event signals](#event-signals) , property changes, [Scriptable](/docs/reference/engine/enums/UIDragDetectorDragStyle#Scriptable)  drag style, and custom functions, scripts can respond to the manipulation of dragged UI elements to drive various settings or make logical decisions, such as sliders that adjust music and sound effect volume separately.

For user-initiated script responses like [Event Signals](#event-signals)  and [Scripted Drag Style](#scripted-drag-style) , you'll most commonly need to put your script code inside a [LocalScript](/docs/reference/engine/classes/LocalScript) , or a [Script](/docs/reference/engine/classes/Script)  with [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  set to [Client](/docs/reference/engine/enums/RunContext#Client) .

### [Event signals](#event-signals)[](#event-signals)

Through the following event signals, you can detect when a user starts, continues, and ends dragging an object.

| Event | | Description |
| [DragStart](/docs/reference/engine/classes/UIDragDetector#DragStart) | | Fires when a user starts dragging the object. |
| [DragContinue](/docs/reference/engine/classes/UIDragDetector#DragContinue) | | Fires when a user continues dragging the object after [DragStart](/docs/reference/engine/classes/UIDragDetector#DragStart)  has been initiated. |
| [DragEnd](/docs/reference/engine/classes/UIDragDetector#DragEnd) | | Fires when a user stops dragging the object. |

The following slider designates its container as the [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI)  to limit its movement within the container area, allowing the scale‑based [TranslateLine](/docs/reference/engine/enums/UIDragDetectorDragStyle)  drag to be limited to the full width of the container without extra scripting.

To test this example, download the [TransparencySlider.rbxm](https://prod.docsiteassets.roblox.com/assets/ui/ui-drag-detectors/TransparencySlider.rbxm)  file, right‑click [StarterGui](/docs/reference/engine/classes/StarterGui)  in the [Explorer](/docs/studio/explorer)  window, select Insert  ⟩ Import Roblox Model , and choose the downloaded file.

UIDragDetector - Event Signal Transparency Change

```

-- Hierarchy is SliderContainer ⟩ Handle ⟩ UIDragDetector ⟩ (this script)

local sliderContainer = script.Parent.Parent.Parent

local handle = sliderContainer:FindFirstChild("Handle")

local uiDragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.ResponseStyle = Enum.UIDragDetectorResponseStyle.Scale  -- Set dragging by scale

uiDragDetector.DragStyle = Enum.UIDragDetectorDragStyle.TranslateLine  -- Restricts dragging to line

uiDragDetector.BoundingUI = sliderContainer

-- Initially set container transparency to X scale value of handle

sliderContainer.BackgroundTransparency = 1 - handle.Position.X.Scale

-- Expand handle border to indicate grab start

uiDragDetector.DragStart:Connect(function(inputPosition)

	handle:FindFirstChildWhichIsA("UIStroke").Thickness = 6

end)

-- Change transparency by how much it dragged in scale

uiDragDetector.DragContinue:Connect(function(inputPosition)

	sliderContainer.BackgroundTransparency = 1 - handle.Position.X.Scale

end)

-- Revert handle border to indicate grab end

uiDragDetector.DragEnd:Connect(function(inputPosition)

	handle:FindFirstChildWhichIsA("UIStroke").Thickness = 4

end)

```

### [Position & rotation changes](#position--rotation-changes)[](#position--rotation-changes)

In addition to [event signals](#event-signals) , you can monitor changes to the detector's [DragUDim2](/docs/reference/engine/classes/UIDragDetector#DragUDim2)  and/or [DragRotation](/docs/reference/engine/classes/UIDragDetector#DragRotation)  properties directly.

The following detector has its [DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  set to [Rotate](/docs/reference/engine/enums/UIDragDetectorDragStyle) , allowing users to drag the handle around the hue rotator ring, all while detecting changes to drag rotation through [Instance:GetPropertyChangedSignal()](/docs/reference/engine/classes/Instance#GetPropertyChangedSignal) .

To test this example, download the [HueRotator.rbxm](https://prod.docsiteassets.roblox.com/assets/ui/ui-drag-detectors/HueRotator.rbxm)  file, right‑click [StarterGui](/docs/reference/engine/classes/StarterGui)  in the [Explorer](/docs/studio/explorer)  window, select Insert  ⟩ Import Roblox Model , and choose the downloaded file.

UIDragDetector - DragRotation Change

```

local handle = script.Parent.Parent  -- UI element to drag

local uiDragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.DragStyle = Enum.UIDragDetectorDragStyle.Rotate  -- Set drag style to rotate

local function changeHue()

	local currAngle = (math.fmod(handle.Rotation, 360)) / 360

	if currAngle < 0 then

		currAngle += 1

	end

	handle.BackgroundColor3 = Color3.fromHSV(currAngle, 1, 1)

end

-- Initially set hue to handle rotation

changeHue()

-- Connect function to GetPropertyChangedSignal() of the detector's drag rotation

uiDragDetector:GetPropertyChangedSignal("DragRotation"):Connect(changeHue)

```

### [Scripted drag style](#scripted-drag-style)[](#scripted-drag-style)

If you set a detector's [UIDragDetector.DragStyle](/docs/reference/engine/classes/UIDragDetector#DragStyle)  to [Enum.UIDragDetectorDragStyle.Scriptable](/docs/reference/engine/enums/UIDragDetectorDragStyle#Scriptable) , you can provide your own function that takes in a [Vector2](/docs/reference/engine/datatypes/Vector2)  of the input position and returns a [UDim2](/docs/reference/engine/datatypes/UDim2)  (position) and a float (rotation). The detector will update the object to the computed position/rotation based off of the returns, the [DragSpace](/docs/reference/engine/classes/UIDragDetector#DragSpace)  property, and the [DragRelativity](/docs/reference/engine/classes/UIDragDetector#DragRelativity)  property.

By default, the returned [UDim2](/docs/reference/engine/datatypes/UDim2)  and float will be the final  desired position/rotation in the local space of the detector's parent. Existing translation/rotation limits will still apply, as will boundary limits imposed by a specified [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI)  instance.

The following example drags a UI element following a sine wave computed by the change in X  coordinate input. Note that the detector's [DragRelativity](/docs/reference/engine/classes/UIDragDetector#DragRelativity)  is set to [Enum.UIDragDetectorDragRelativity.Relative](/docs/reference/engine/enums/UIDragDetectorDragRelativity#Relative) .

UIDragDetector - Drag Following Sine Wave

```

local frame = script.Parent  -- UI element to drag

local uiDragDetector = frame:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.DragStyle = Enum.UIDragDetectorDragStyle.Scriptable

uiDragDetector.DragRelativity = Enum.UIDragDetectorDragRelativity.Relative

local initialXValue = 0

local maxHeightChange = 200

local pixelsPerRadian = 75  -- Lower this value to increase frequency

uiDragDetector.DragStart:Connect(function(inputPosition)

	initialXValue = inputPosition.X

end)

local function computeSinWaveCoordinate(inputPosition)

	local deltaX = inputPosition.X - initialXValue

	-- Negative Y delta so that it goes "up" on the screen with positive Y change

	local deltaY = -math.sin(deltaX / pixelsPerRadian) * maxHeightChange

	return UDim2.fromOffset(deltaX, deltaY)

end

uiDragDetector:SetDragStyleFunction(computeSinWaveCoordinate)

```

### [Custom constraint function](#custom-constraint-function)[](#custom-constraint-function)

[UIDragDetectors](/docs/reference/engine/classes/UIDragDetector)  do not have built-in motion rules about grids and snapping, but you can register custom constraint functions to edit the detector's [UIDragDetector.DragUDim2](/docs/reference/engine/classes/UIDragDetector#DragUDim2)  and [UIDragDetector.DragRotation](/docs/reference/engine/classes/UIDragDetector#DragRotation)  before they are applied. For example, you can keep motion on a grid by rounding positions to specific increments, or define allowed areas of motion. Note that this is applied before  any existing translation/rotation limits.

Multiple constraint functions can be registered and they will be called in the order of their priority value passed in upon registration, from least to greatest.

The following example utilizes a constraint function that clamps the planar drag into an X / Y  grid based on the number of rows and columns. Note that the detector's [ResponseStyle](/docs/reference/engine/classes/UIDragDetector#ResponseStyle)  is set to [Enum.UIDragDetectorResponseStyle.Scale](/docs/reference/engine/enums/UIDragDetectorResponseStyle#Scale)  and its [BoundingUI](/docs/reference/engine/classes/UIDragDetector#BoundingUI)  is set to the grid container.

To test this example, download the [GridDrag.rbxm](https://prod.docsiteassets.roblox.com/assets/ui/ui-drag-detectors/GridDrag.rbxm)  file, right‑click [StarterGui](/docs/reference/engine/classes/StarterGui)  in the [Explorer](/docs/studio/explorer)  window, select Insert  ⟩ Import Roblox Model , and choose the downloaded file.

UIDragDetector - Drag in Grid, Snapping to Tiles

```

-- Hierarchy is GridContainer ⟩ Handle ⟩ UIDragDetector ⟩ (this script)

local gridContainer = script.Parent.Parent.Parent

local handle = gridContainer:FindFirstChild("Handle")  -- UI element to drag

local uiDragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.ResponseStyle = Enum.UIDragDetectorResponseStyle.Scale  -- Set dragging by scale

uiDragDetector.DragRelativity = Enum.UIDragDetectorDragRelativity.Relative

uiDragDetector.BoundingUI = gridContainer

local NUM_COLUMNS = 10

local NUM_ROWS = 5

local xScaleIncrement = 1 / NUM_COLUMNS

local yScaleIncrement = 1 / NUM_ROWS

local initialParentPosition = uiDragDetector.Parent.Position

uiDragDetector.DragStart:Connect(function()

	initialParentPosition = uiDragDetector.Parent.Position

end)

local function dragToGridOnly(proposedPosition, proposedRotation)

	local griddedXScale = math.round(proposedPosition.X.Scale / xScaleIncrement) * xScaleIncrement

	local griddedYScale = math.round(proposedPosition.Y.Scale / yScaleIncrement) * yScaleIncrement

	return UDim2.fromScale(griddedXScale, griddedYScale), proposedRotation

end

uiDragDetector:AddConstraintFunction(1, dragToGridOnly)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
