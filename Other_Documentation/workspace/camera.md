<!-- Source: https://create.roblox.com/docs/workspace/camera -->

Customize the camera | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/camera.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Camera](/docs/workspace/camera)

# Customize the camera

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/camera/index.md)

Roblox's built-in camera powers a default third person  mode and an optional first person  mode, so you don't need to build your own following camera. For more customized scenarios, you can adjust the default properties in [Camera](/docs/reference/engine/classes/Camera)  or replace it entirely like for over-the-shoulder, isometric, and weapon scoping views.

## [Basic settings](#basic-settings)[](#basic-settings)

You can configure common camera settings directly within Studio's [StarterPlayer](/docs/reference/engine/classes/StarterPlayer)  object. These settings include [zoom distance](#zoom-distance)  and various [camera](#camera-mode) , [occlusion](#occlusion-mode) , and [movement](#movement-mode)  modes.

1.

In the Explorer  window, select the StarterPlayer  object.

 ![StarterPlayer in Explorer](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterPlayer.png)

2.

In the Properties  window, scroll down to locate the Camera  section. You can configure the following properties directly or through a script.

 ![Camera properties on StarterPlayer in Properties Window](https://prod.docsiteassets.roblox.com/assets/studio/properties/StarterPlayer-Camera-Group.png)

### [Zoom distance](#zoom-distance)[](#zoom-distance)

Together, [CameraMaxZoomDistance](/docs/reference/engine/classes/StarterPlayer#CameraMaxZoomDistance)  and [CameraMinZoomDistance](/docs/reference/engine/classes/StarterPlayer#CameraMinZoomDistance)  set the range in which players can zoom the camera in respect to their player character. Setting a very high maximum such as 500 allows players to zoom the camera far out in space. If you want to lock the camera to a specific distance away from the character and prevent zooming, set both of these properties to the same value.

LocalScript - Camera Zoom Range

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMaxZoomDistance = 25

player.CameraMinZoomDistance = 50

```

### [Camera mode](#camera-mode)[](#camera-mode)

The [CameraMode](/docs/reference/engine/classes/StarterPlayer#CameraMode)  property sets the overall behavior of the camera between two options:

| Setting | | Description |
| --- | --- |
| Classic | | The classic Roblox third-person camera which can be zoomed into first-person. Allows players to zoom in and out (unless zoom is locked) and rotate the camera around their character. |
| LockFirstPerson | | Locks the camera to first-person mode. When in this mode, all parts/elements of the player's character are invisible to them, except for equipped [Tools](/docs/reference/engine/classes/Tool) . |

### [Occlusion mode](#occlusion-mode)[](#occlusion-mode)

The [DevCameraOcclusionMode](/docs/reference/engine/classes/StarterPlayer#DevCameraOcclusionMode)  property controls camera behavior when the player cannot see their character, such as when it's obscured by a [BasePart](/docs/reference/engine/classes/BasePart) .

| Setting | | Description |
| Zoom | | If the player's character moves behind an object with [Transparency](/docs/reference/engine/classes/BasePart#Transparency)  lower than 0.25, the camera zooms in very close to the character so that it can be seen. Once the character moves back into a viewable position, the camera zooms back out. |
| Invisicam | | If the player's character moves behind an object with [Transparency](/docs/reference/engine/classes/BasePart#Transparency)  lower than 0.75, the camera remains unmoved but the object becomes semi-transparent so that the character can be seen. Once the character moves back into a viewable position, the object returns to its normal opacity. |

Zoom  and Invisicam  occlusion modes

### [Movement mode](#movement-mode)[](#movement-mode)

The [DevComputerCameraMovementMode](/docs/reference/engine/classes/StarterPlayer#DevComputerCameraMovementMode)  (computer) and [DevTouchCameraMovementMode](/docs/reference/engine/classes/StarterPlayer#DevTouchCameraMovementMode)  (phone/tablet) determine how the player can move the camera around.

| Setting | | Description |
| UserChoice | | The camera will move based on the player's in-game camera settings. |
| Classic | | The camera remains at its [zoom distance](#zoom-distance) , tracking the player's character as it moves around the world. Players can also pitch the camera view up/down and orbit it around their character. |
| Follow | | Similar to Classic  but the camera may rotate slightly to face the player's character if they're moving in any direction that isn't parallel to the camera's facing direction. |
| Orbital | | The camera remains at a fixed zoom distance and tracks the player's character as it moves around the world. Players can orbit the camera around their character but can't pitch the view up or down. |
| CameraToggle | | Only functional on computers (not phones/tablets) through [DevComputerCameraMovementMode](/docs/reference/engine/classes/StarterPlayer#DevComputerCameraMovementMode) . When the player clicks the right mouse button, the camera toggles between Classic  mode and a "free look" mode where moving the mouse looks around the world. |

## [Script the camera](#script-the-camera)[](#script-the-camera)

Each player [client](/docs/projects/client-server)  has its own [Camera](/docs/reference/engine/classes/Camera)  object residing in the local [Workspace](/docs/reference/engine/classes/Workspace) , accessible through the [Workspace.CurrentCamera](/docs/reference/engine/classes/Workspace#CurrentCamera)  property. You can override Roblox's default camera scripts by setting its [CameraType](/docs/reference/engine/classes/Camera#CameraType)  to [Scriptable](/docs/reference/engine/enums/CameraType)  and then, most commonly, control the camera through the following properties.

| Property | | Description |
| [Camera.CFrame](/docs/reference/engine/classes/Camera#CFrame) | | The [CFrame](/docs/reference/engine/datatypes/CFrame)  of the camera. This is the most frequently used property for positioning and orienting a [Scriptable](/docs/reference/engine/enums/CameraType)  camera in a game. |
| [Camera.FieldOfView](/docs/reference/engine/classes/Camera#FieldOfView) | | The extent of the observable 3D space that can be seen on screen, measured between 1–120 degrees in the direction defined by [Camera.FieldOfViewMode](/docs/reference/engine/classes/Camera#FieldOfViewMode) . Default is 70. |
| [Camera.CameraType](/docs/reference/engine/classes/Camera#CameraType) | | Toggles between the various camera behaviors outlined in [Enum.CameraType](/docs/reference/engine/enums/CameraType) , some of which mimic the selectable [movement modes](#movement-mode) . Setting this to [Scriptable](/docs/reference/engine/enums/CameraType)  gives you full control of the camera. |
| [Camera.Focus](/docs/reference/engine/classes/Camera#Focus) | | The point in 3D space where the camera is looking. If you've set [Camera.CameraType](/docs/reference/engine/classes/Camera#CameraType)  to [Scriptable](/docs/reference/engine/enums/CameraType) , you should update this property every frame because certain visuals are more detailed depending on how close they are to the focus point. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
