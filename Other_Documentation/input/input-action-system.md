<!-- Source: https://create.roblox.com/docs/input/input-action-system -->

Input Action System | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/input/input-action-system.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Input](/docs/input)

# Input Action System

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/input/input-action-system.md)

The cross-platform Input Action System  lets you connect [actions](#input-actions)  and arrange [bindings](#input-bindings)  across various hardware inputs at edit time. Combined with [contexts](#input-contexts) , you can easily configure and edit a modular input system that works on any device in any phase of play. Use cases include:

-

A first-person shooter system with actions dynamically swapping in and out depending on if the player is in battle mode or spectator mode.

-

A comprehensive driving system equipped with acceleration/deceleration, car boosters, and refuel stations.

-

Hotkeys for an abilities system in a fighting game to swap out moves seamlessly without players missing a punch.

## [Input contexts](#input-contexts)[](#input-contexts)

An [InputContext](/docs/reference/engine/classes/InputContext)  is a collection of actions which holds related [input actions](#input-actions) , for example PlayContext  for in‑game character controls and NavContext  for controls to navigate around UI menus. You can [enable/disable contexts](#context-changes)  (and their corresponding actions) through their [Enabled](/docs/reference/engine/classes/InputContext#Enabled)  property, such as to enable the NavContext  when an inventory menu is open and then change to the PlayContext  when the player closes the menu and returns to primary gameplay.

Even if a game may not use multiple input contexts initially, it's recommended to create a primary context at the top level of any input system, for example the PlayContext  instance for input that occurs during gameplay.

1.

RECOMMENDED

 Create a [Folder](/docs/reference/engine/classes/Folder)  named Inputs  inside [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  to hold various input contexts.

 ![New Folder inside ReplicatedStorage, renamed to Inputs](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Folder-Inputs.png)

2.

Insert a new [InputContext](/docs/reference/engine/classes/InputContext)  into the folder and rename it to PlayContext .

 ![New InputContext instance inside ReplicatedStorage, renamed to PlayContext](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext.png)

3.

OPTIONAL

 In the [Properties](/docs/studio/properties)  window, set [Priority](/docs/reference/engine/classes/InputContext#Priority)  to 2000  and enable [Sink](/docs/reference/engine/classes/InputContext#Sink) . A context with [Sink](/docs/reference/engine/classes/InputContext#Sink)  enabled consumes input events for its bound [KeyCodes](/docs/reference/engine/enums/KeyCode)  at its priority level, blocking those inputs from reaching lower-priority contexts. This is practical for use cases like an inventory screen that should suppress specific gameplay inputs while open. In this example, PlayContext  is given a high enough [Priority](/docs/reference/engine/classes/InputContext#Priority)  to sink its bound inputs before the default [PlayerScripts](/docs/reference/engine/classes/PlayerScripts)  contexts process them.

 ![InputContext with Priority set to 2000 and Sink enabled](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputContext-Priority-Sink.png)

## [Input actions](#input-actions)[](#input-actions)

An [InputAction](/docs/reference/engine/classes/InputAction)  defines a gameplay action mechanic such as "Jump," "Sprint," or "Shoot." These actions are then mapped to hardware inputs using [input bindings](#input-bindings) .

An [InputAction](/docs/reference/engine/classes/InputAction)  can be of several variations depending on its [Type](/docs/reference/engine/classes/InputAction#Type)  property ([Enum.InputActionType](/docs/reference/engine/enums/InputActionType) ). The default is [Bool](/docs/reference/engine/enums/InputActionType) , designed to receive true / false  values from press/release of inputs such as [ButtonA](/docs/reference/engine/enums/KeyCode#ButtonA) , [E](/docs/reference/engine/enums/KeyCode#E) , or [MouseLeftButton](/docs/reference/engine/enums/KeyCode#MouseLeftButton) .

[InputAction](/docs/reference/engine/classes/InputAction)  also exposes a read-only [PreferredBinding](/docs/reference/engine/classes/InputAction#PreferredBinding)  property that returns the child [InputBinding](/docs/reference/engine/classes/InputBinding)  best matching the player's current input device (keyboard/mouse, gamepad, or touch). It updates dynamically as the player's device configuration changes and is the basis for [displaying bindings](#displaying-bindings)  to players.

| Input Action Type | | Example Usage |
| --- | --- |
| [Bool](/docs/reference/engine/enums/InputActionType) | | Triggered actions such as jump, shoot, sprint, etc. with support for pressed/released thresholds on analog inputs. |
| [Direction1D](/docs/reference/engine/enums/InputActionType) | | Variable zero-to-full actions such as a car's accelerator pedal or a view scope's zoom level. |
| [Direction2D](/docs/reference/engine/enums/InputActionType) | | 2D directional movement such as camera rotation, or the standard Roblox character movement. |
| [Direction3D](/docs/reference/engine/enums/InputActionType) | | 3D directional movement like an airborne vehicle that can levitate up/down, accelerate/decelerate, and drift left/right. |
| [ViewportPosition](/docs/reference/engine/enums/InputActionType) | | 2D viewport coordinates like mouse input, such as for custom cursors or raycasting to select world objects. |

Character Sprint Camera Rotation

To test an [InputAction](/docs/reference/engine/classes/InputAction)  for simple character sprinting:

1.

RECOMMENDED

 Select the top-level [Workspace](/docs/reference/engine/classes/Workspace)  object in the [Explorer](/docs/studio/explorer)  and then, in the [Properties](/docs/studio/properties)  window, set the [PlayerScriptsUseInputActionSystem](/docs/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  property to [Enabled](/docs/reference/engine/enums/RolloutState) .

2.

Create a new [InputAction](/docs/reference/engine/classes/InputAction)  inside the PlayContext  context within [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) . Rename it to CharacterSprint  to indicate its dedicated action.

 ![New InputAction instance inside an InputContext, renamed to CharacterSprint](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction.png)

3.

In the [Properties](/docs/studio/properties)  window, notice that the action's [Type](/docs/reference/engine/classes/InputAction#Type)  is [Bool](/docs/reference/engine/enums/InputActionType)  (default). This is a logical type for simple character sprinting as a boolean true / false  action (character is either sprinting or not sprinting).

 ![Type property of an InputAction set to Bool](https://prod.docsiteassets.roblox.com/assets/studio/properties/SprintAction-Type-Bool.png)

## [Input bindings](#input-bindings)[](#input-bindings)

An [InputBinding](/docs/reference/engine/classes/InputBinding)  defines which hardware binding should trigger the parent [InputAction](/docs/reference/engine/classes/InputAction) , for example a key press, gamepad button, or tap on a touch‑enabled device. For [cross‑platform](/docs/projects/cross-platform)  compatibility, each [InputAction](/docs/reference/engine/classes/InputAction)  should have an [InputBinding](/docs/reference/engine/classes/InputBinding)  for gamepad , keyboard/mouse , and touch  as illustrated here.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-InputBinding-All.png)

Default Bindings

Roblox provides default input bindings for movement, camera control, and basic environment interaction — Roblox players are familiar with these controls, so you should only override them in specific cases. Also note that the reserved  inputs cannot be overridden and will always operate with their intended purpose.

Roblox Reserved Character Interface / Inventory Camera

| Action | | Mouse/Keyboard | | Gamepad | | Touch |
| Open Roblox menu | | Esc | | Start  button ([ButtonStart](/docs/reference/engine/enums/KeyCode) ) | | N/A |
| [Developer Console](/docs/studio/developer-console) | | F9 | | N/A | | N/A |
| Fullscreen mode (Windows)
Show desktop (Mac) | | F11 | | N/A | | N/A |
| Record video (Windows) | | F12 | | N/A | | N/A |
| Take screenshot | | PrintScreen | | N/A | | N/A |

The [Type](/docs/reference/engine/classes/InputAction#Type)  assigned to the parent [InputAction](/docs/reference/engine/classes/InputAction)  directly affects which general input types (key/button/tap, analog trigger, thumbstick, etc.) are valid for child [InputBinding](/docs/reference/engine/classes/InputBinding)  instances. In turn, values sent to the parent action's connected events depend on a binding's chosen input type. See [input events](#input-events)  for details on the correlation between action types, bindings, and return values.

Character Sprint Camera Rotation

To hook up bindings for simple character sprinting:

1.

Insert a new [InputBinding](/docs/reference/engine/classes/InputBinding)  into the CharacterSprint  action and rename it to KeyboardBinding . Then set the binding's [KeyCode](/docs/reference/engine/classes/InputBinding#KeyCode)  property to [LeftShift](/docs/reference/engine/enums/KeyCode#LeftShift) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-InputBinding-KeyboardBinding.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputBinding-KeyCode-LeftShift.png)

2.

Insert a second [InputBinding](/docs/reference/engine/classes/InputBinding)  into the CharacterSprint  action and rename it to GamepadBinding . Then set the binding's [KeyCode](/docs/reference/engine/classes/InputBinding#KeyCode)  property to [ButtonY](/docs/reference/engine/enums/KeyCode#ButtonY) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-InputBinding-GamepadBinding.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputBinding-KeyCode-ButtonY.png)

3.

Inside a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  container inside [StarterGui](/docs/reference/engine/classes/StarterGui) , create an [on-screen button](/docs/ui/buttons) , rename it to SprintButton , and [position/resize](/docs/ui/position-and-size)  it as desired.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-SprintButton.png)  ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/Sprint-Button.png)

4.

Insert a third [InputBinding](/docs/reference/engine/classes/InputBinding)  into the CharacterSprint  action and rename it to TouchBinding . Then, in the [Properties](/docs/studio/properties)  window, link the binding's [UIButton](/docs/reference/engine/classes/InputBinding#UIButton)  property to the SprintButton  button you created previously inside [StarterGui](/docs/reference/engine/classes/StarterGui) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-InputBinding-TouchBinding.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputBinding-UIButton-SprintButton.png)

## [Input events](#input-events)[](#input-events)

The [InputAction](/docs/reference/engine/classes/InputAction)  instance has three built-in events  to handle player input coming from [InputBindings](/docs/reference/engine/classes/InputBinding) .

-

[Pressed](/docs/reference/engine/classes/InputAction#Pressed)  — This event fires only when the input action's [Type](/docs/reference/engine/classes/InputAction#Type)  is set to [Bool](/docs/reference/engine/enums/InputActionType) , and only when the state transitions from false  to true .

-

[Released](/docs/reference/engine/classes/InputAction#Released)  — This event fires only when the input action's [Type](/docs/reference/engine/classes/InputAction#Type)  is set to [Bool](/docs/reference/engine/enums/InputActionType) , and only when the state transitions from true  to false .

-

[StateChanged](/docs/reference/engine/classes/InputAction#StateChanged)  — This event fires for all input action types whenever the state changes, except if the state attempts to transition to the same state.

Depending on the input action's [Type](/docs/reference/engine/classes/InputAction#Type)  ([Bool](/docs/reference/engine/enums/InputActionType) , [Direction1D](/docs/reference/engine/enums/InputActionType) , [Direction2D](/docs/reference/engine/enums/InputActionType) , [Direction3D](/docs/reference/engine/enums/InputActionType) , or [ViewportPosition](/docs/reference/engine/enums/InputActionType) ) and the general input type coming from a child [InputBinding](/docs/reference/engine/classes/InputBinding)  (key/button/tap, analog trigger, thumbstick, etc.), different values are returned to the [Pressed](/docs/reference/engine/classes/InputAction#Pressed) , [Released](/docs/reference/engine/classes/InputAction#Released) , and [StateChanged](/docs/reference/engine/classes/InputAction#StateChanged)  event handlers. Examine the following tables to better understand the correlation.

Bool Direction1D Direction2D Direction3D ViewportPosition

The [Bool](/docs/reference/engine/enums/InputActionType)  type is best for triggered actions such as jump, shoot, sprint, etc. with support for pressed/released thresholds on analog inputs.

| Valid Input Types on [InputBindings](/docs/reference/engine/classes/InputBinding) | | Returned to the [InputAction](/docs/reference/engine/classes/InputAction)  Event(s) |
| Boolean inputs from keyboard keys or basic mouse/gamepad buttons through the binding's [KeyCode](/docs/reference/engine/classes/InputBinding#KeyCode)  property, or a [GuiButton](/docs/reference/engine/classes/GuiButton)  press/release through the binding's [UIButton](/docs/reference/engine/classes/InputBinding#UIButton)  property. | |
-

[Pressed](/docs/reference/engine/classes/InputAction#Pressed)  event:
-

true  when pressed

-

[Released](/docs/reference/engine/classes/InputAction#Released)  event:
-

true  when released

-

[StateChanged](/docs/reference/engine/classes/InputAction#StateChanged)  event:
-

true  (pressed) or false  (released)

 |
| Variable input amounts from analog inputs like gamepad triggers ([ButtonL2](/docs/reference/engine/enums/KeyCode#ButtonL2) /[ButtonR2](/docs/reference/engine/enums/KeyCode#ButtonR2) ) through the binding's [KeyCode](/docs/reference/engine/classes/InputBinding#KeyCode)  property. | |
-

[Pressed](/docs/reference/engine/classes/InputAction#Pressed)  event:
-

true  when trigger press is >=  [PressedThreshold](/docs/reference/engine/classes/InputBinding#PressedThreshold)

-

[Released](/docs/reference/engine/classes/InputAction#Released)  event:
-

true  when trigger press is <=  [ReleasedThreshold](/docs/reference/engine/classes/InputBinding#ReleasedThreshold)

-

[StateChanged](/docs/reference/engine/classes/InputAction#StateChanged)  event:
-

true  when trigger press is >=  [PressedThreshold](/docs/reference/engine/classes/InputBinding#PressedThreshold)

-

false  when trigger press is <=  [ReleasedThreshold](/docs/reference/engine/classes/InputBinding#ReleasedThreshold)

 |

Character Sprint Camera Rotation

To connect events for simple character sprinting:

1.

Insert a new [Script](/docs/reference/engine/classes/Script)  into the CharacterSprint  tree, alongside the various input bindings. Then set its [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  to [Client](/docs/reference/engine/enums/RunContext#Client)  and rename it to OnActivate .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-Script.png)

2.

Paste the following code into the OnActivate  script. Note the [Pressed](/docs/reference/engine/classes/InputAction#Pressed)  event connection on lines 13 ‑ 15  which doubles the character's walk speed when a sprint input binding is pressed, and the corresponding [Released](/docs/reference/engine/classes/InputAction#Released)  event connection on lines 16 ‑ 18  which resets the walk speed to default when a sprint input binding is released.

OnActivate (Client Script)

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character

if not character or character.Parent == nil then

	character = player.CharacterAdded:Wait()

end

local humanoid = character:WaitForChild("Humanoid")

local defaultWalkSpeed = humanoid.WalkSpeed

local inputAction = script.Parent

inputAction.Pressed:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed * 2

end)

inputAction.Released:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed

end)

```

3.

Playtest your game and test the character sprint action with the [bindings](#input-bindings)  you chose previously: [LeftShift](/docs/reference/engine/enums/KeyCode#LeftShift)  for keyboard, [ButtonY](/docs/reference/engine/enums/KeyCode#ButtonY)  for gamepad, and the on‑screen SprintButton  for touch‑enabled devices. Remember that you can use the [Controller Emulator](/docs/studio/testing-modes#controller-emulation)  to test gamepad inputs directly in Roblox Studio.

## [Context changes](#context-changes)[](#context-changes)

Once you have an [input context](#input-contexts)  such as PlayContext , you can enable/disable it during gameplay through scripting, change its [Priority](/docs/reference/engine/classes/InputContext#Priority)  to determine which actions take precedence over others, and [Sink](/docs/reference/engine/classes/InputContext#Sink)  inputs from being processed within contexts of lower priority.

1.

To make it easier to switch contexts from other scripts, insert a new [BindableEvent](/docs/reference/engine/classes/BindableEvent)  into your inputs folder within [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  and rename it to ContextEvent .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-BindableEvent-ContextEvent.png)

2.

Create a new [Script](/docs/reference/engine/classes/Script)  at the same level, set its [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  to [Client](/docs/reference/engine/enums/RunContext#Client) , and rename it to UpdateContext .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Script-UpdateContext.png)

3.

Inside the UpdateContext  script, paste the following code:

UpdateContext (Client Script)

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local inputsFolder = ReplicatedStorage:WaitForChild("Inputs")

local contextEvent = inputsFolder:WaitForChild("ContextEvent")

-- Connect bindable event

contextEvent.Event:Connect(function(targetContext, enabled)

	local context = inputsFolder:FindFirstChild(targetContext)

	if context then

		context.Enabled = enabled

		print(context.Name .. ": " .. tostring(context.Enabled))

	else

		warn("InputContext not found!")

	end

end)

```

4.

With the UpdateContext  script in place, you can now update a named [InputContext](/docs/reference/engine/classes/InputContext)  by firing the bindable event, for example from a [LocalScript](/docs/reference/engine/classes/LocalScript)  that powers a [GuiButton](/docs/reference/engine/classes/GuiButton)  inside a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  container.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-TextButton.png)

Button Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local inputsFolder = ReplicatedStorage:WaitForChild("Inputs")

local contextEvent = inputsFolder:WaitForChild("ContextEvent")

local button = script.Parent

button.Activated:Connect(function()

	-- Fire bindable event with target input context and enabled state

	contextEvent:Fire("PlayContext", true)

end)

```

## [Displaying bindings](#displaying-bindings)[](#displaying-bindings)

Once you've set up [actions](#input-actions)  and [bindings](#input-bindings) , you'll typically need to show players, via on‑screen [assistive hints](/docs/projects/cross-platform#assistive-hints) , which key or button triggers each action:

Keyboard Input Gamepad Input

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Inventory-Selection-Keyboard.jpg)

The Input Action System provides two approaches:

-

RECOMMENDED

 [InputActionLabel](/docs/reference/engine/classes/InputActionLabel)  — A no-code, drag-and-drop [GuiObject](/docs/reference/engine/classes/GuiObject)  that automatically displays the correct input per platform.

-

INTERMEDIATE

 [PreferredBinding](/docs/reference/engine/classes/InputAction#PreferredBinding)  — A read-only [InputAction](/docs/reference/engine/classes/InputAction)  property for creators who want full control over how bindings are displayed in custom UI.

InputActionLabel PreferredBinding

This class/object is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ InputActionLabel .

[InputActionLabel](/docs/reference/engine/classes/InputActionLabel)  is a [GuiObject](/docs/reference/engine/classes/GuiObject)  that you can insert into any [ScreenGui](/docs/reference/engine/classes/ScreenGui)  or [SurfaceGui](/docs/reference/engine/classes/SurfaceGui) . Once its [InputAction](/docs/reference/engine/classes/InputActionLabel#InputAction)  property is set to reference an existing [InputAction](/docs/reference/engine/classes/InputAction)  instance, it automatically resolves and displays the correct keybinding for the player's current input device — no scripting required. When the player switches devices (for example, picking up a gamepad after using a keyboard) or rebinds a control, the label updates instantly.

To add an [InputActionLabel](/docs/reference/engine/classes/InputActionLabel) :

1.

Inside a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  container inside [StarterGui](/docs/reference/engine/classes/StarterGui) , insert an [InputActionLabel](/docs/reference/engine/classes/InputActionLabel)  just like any other [GuiObject](/docs/reference/engine/classes/GuiObject) .

2.

In the [Properties](/docs/studio/properties)  window, set its [InputAction](/docs/reference/engine/classes/InputActionLabel#InputAction)  property to the [InputAction](/docs/reference/engine/classes/InputAction)  instance you want to display (for example, your "Sprint" action under [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) ) and [position/resize](/docs/ui/position-and-size)  it as desired.

3.

When the label resolves what to show, it checks the following in order:

1.

Custom Images  — If child [InputBindings](/docs/reference/engine/classes/InputBinding)  have their [DisplayImage](/docs/reference/engine/classes/InputBinding#DisplayImage)  property set, the label renders those images directly.

2.

Platform Key Images  — Lacking custom images, the label renders platform-provided images for child [InputBindings](/docs/reference/engine/classes/InputBinding)  through [UserInputService:GetImageForKeyCode()](/docs/reference/engine/classes/UserInputService#GetImageForKeyCode) , if such images are available. Composite bindings with modifiers show multiple icons with +  separators.

3.

Custom Names  — Lacking available images, if child [InputBindings](/docs/reference/engine/classes/InputBinding)  have their [DisplayName](/docs/reference/engine/classes/InputBinding#DisplayName)  property set, the label renders that text using the label's style properties.

4.

Platform Key Strings  — Lacking all of the above, the label renders platform-provided strings through [UserInputService:GetStringForKeyCode()](/docs/reference/engine/classes/UserInputService#GetStringForKeyCode) .

5.

If no [InputAction](/docs/reference/engine/classes/InputAction)  is assigned or no child [InputBinding](/docs/reference/engine/classes/InputBinding)  exists, the label renders a placeholder icon.

## [Input Action Manager](#input-action-manager)[](#input-action-manager)

This tool is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ Input Action Manager .

The Input Action Manager  tool is a unified, matrix-style interface to design, audit, and scale your input architecture.

To access it, navigate to the Window  menu in Studio and select Input  ⟩ Input Action Manager . If your game already uses input [contexts](#input-contexts) , [actions](#input-actions) , or [bindings](#input-bindings) , the manager will automatically scan the [DataModel](/docs/reference/engine/classes/DataModel)  and extract those existing instances into the editor grid. Any new input‑related instances will automatically populate into an Inputs  folder within [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) .

 ![Folder inside ReplicatedStorage named Inputs](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Folder-Inputs.png)

To configure an input setup for character sprint  as outlined in the sections above:

1.

RECOMMENDED

 Select the top-level [Workspace](/docs/reference/engine/classes/Workspace)  object in the [Explorer](/docs/studio/explorer)  and then, in the [Properties](/docs/studio/properties)  window, set the [PlayerScriptsUseInputActionSystem](/docs/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  property to [Enabled](/docs/reference/engine/enums/RolloutState) .

2.

Inside a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  container inside [StarterGui](/docs/reference/engine/classes/StarterGui) , create an [on-screen button](/docs/ui/buttons) , rename it to SprintButton , and [position/resize](/docs/ui/position-and-size)  it as desired.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-SprintButton.png)

3.

In the Input Action Manager , hover over the Context  column header and click the ＋  button. Enter an appropriate name for the new context such as PlayContext  and press Enter . An [InputContext](/docs/reference/engine/classes/InputContext)  of the matching name appears in [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) .

![](https://prod.docsiteassets.roblox.com/assets/studio/input-action-manager/Add-Context.png)

![New InputContext instance inside ReplicatedStorage named PlayContext](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext.png)

4.

Hover over the new context and click the ＋  button. From the popup menu, select [Bool](/docs/reference/engine/enums/InputActionType) , enter CharacterSprint  for the action's name, and press Enter . An [InputAction](/docs/reference/engine/classes/InputAction)  of the matching name appears under the context.

![](https://prod.docsiteassets.roblox.com/assets/studio/input-action-manager/Add-Action.png)

![New InputAction instance inside an InputContext named CharacterSprint](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction.png)

5.

In the new CharacterSprint  row, assign bindings for each input type:

1.

Keyboard and Mouse  — Click the arrow button and select [LeftShift](/docs/reference/engine/enums/KeyCode)  from the picker menu.

2.

Touch  — Click the cell and then, in the [Explorer](/docs/studio/explorer)  hierarchy, click the SprintButton  object that you previously inserted into the [ScreenGui](/docs/reference/engine/classes/ScreenGui) .

3.

Gamepad  — Click the arrow button and select [ButtonY](/docs/reference/engine/enums/KeyCode)  from the picker menu.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/input-action-manager/Add-Bindings-Sprint.png)

As you assign bindings, watch for warning/error icons in the UI. Yellow warnings (** ⚠** ) indicate a missing  binding for [cross‑platform](/docs/projects/cross-platform)  compatibility, while red warnings (** ⚠** ) indicate a duplicate  binding for actions within the same context.

6.

Insert a new [Script](/docs/reference/engine/classes/Script)  into the CharacterSprint  tree, alongside the various input bindings. Then set its [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  to [Client](/docs/reference/engine/enums/RunContext#Client)  and rename it to OnActivate .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-Script-IAM.png)

7.

Paste the following code into the OnActivate  script. Note the [Pressed](/docs/reference/engine/classes/InputAction#Pressed)  event connection on lines 13 ‑ 15  which doubles the character's walk speed when a sprint input binding is pressed, and the corresponding [Released](/docs/reference/engine/classes/InputAction#Released)  event connection on lines 16 ‑ 18  which resets the walk speed to default when a sprint input binding is released.

OnActivate (Client Script)

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character

if not character or character.Parent == nil then

	character = player.CharacterAdded:Wait()

end

local humanoid = character:WaitForChild("Humanoid")

local defaultWalkSpeed = humanoid.WalkSpeed

local inputAction = script.Parent

inputAction.Pressed:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed * 2

end)

inputAction.Released:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed

end)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
