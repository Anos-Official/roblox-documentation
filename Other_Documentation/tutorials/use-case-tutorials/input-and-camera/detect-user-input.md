<!-- Source: https://create.roblox.com/docs/tutorials/use-case-tutorials/input-and-camera/detect-user-input -->

Detect user input | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/input-and-camera/detect-user-input.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Input and camera

# Detect user input

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/input-and-camera/detect-user-input.md)

Connecting user input to actions gives users much better and more intuitive control over your game's features. In this tutorial, you will bind a reloading action to a specific key.

## [Get started](#get-started)[](#get-started)

This tutorial uses the Blaster  tool created in [Create Player Tools](/docs/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-player-tools) . You can follow those instructions to create the tool or you can download the [Blaster](https://www.roblox.com/library/6571559694/Blaster)  model and insert it into StarterPack .

Models can be added into your Inventory to be used between any game. To add a model to your game:

1.

In a browser, open the [model](https://www.roblox.com/library/6571559694/Blaster)  page, click the Get  button. This adds the model into your inventory.

2.

From Studio's Window  menu or Home  tab toolbar, open the [Toolbox](/docs/projects/assets/toolbox)  and select the Inventory  tab.

3.

Make sure the dropdown is on My Models .

4.

Select the Blaster  model to add it into the game.

## [Create an action handler](#create-an-action-handler)[](#create-an-action-handler)

First, you'll need a function to handle when user input is detected.

1.

Open the ToolController  [LocalScript](/docs/reference/engine/classes/LocalScript)  inside of the Blaster.

![View of the Explorer where the ToolController script inside of the Blaster tool is selected](https://prod.docsiteassets.roblox.com/assets/tutorials/detecting-user-input/ToolControllerExplorer.png)

2.

Make a variable to store a name for the action.

```

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

local function toolEquipped()

	tool.Handle.Equip:Play()

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Activated:Connect(toolActivated)

```

3.

Create a function named onAction that receives three arguments: actionName , inputState , and inputObject . This will be the function that runs when user input is detected.

```

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

local function onAction(actionName, inputState, inputObject)

end

local function toolEquipped()

	tool.Handle.Equip:Play()

end

```

4.

Inside the function, check that the given actionName  matches the reload action name and make sure inputState  is [UserInputState.Begin](/docs/reference/engine/enums/UserInputState)  (the beginning state). This is important because the function will run every time the inputState  changes, but the reload only needs to happen once.

```

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

	end

end

```

5.

To make it obvious when the user reloads, change the [TextureId](/docs/reference/engine/classes/BackpackItem#TextureId)  of the tool to "rbxassetid://6593020923"  for a moment, and then change it back to its original value of "rbxassetid://92628145" .

```

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

		tool.TextureId = "rbxassetid://6593020923"

		task.wait(2)

		tool.TextureId = "rbxassetid://92628145"

	end

end

```

## [Bind the action](#bind-the-action)[](#bind-the-action)

[ContextActionService](/docs/reference/engine/classes/ContextActionService)  can be used to bind  a function to a specific input by using the [BindAction](/docs/reference/engine/classes/ContextActionService#BindAction)  function, which accepts several arguments:

-

The name of the action.

-

The function to handle the action (also called a "callback").

-

Whether or not a touchscreen button should be displayed.

-

Any amount of Enum.KeyCodes  to detect and associate with the action.

KeyCodes are values that represent different input buttons, such as keyboard keys or controller buttons. A full list of codes is available [here](/docs/reference/engine/enums/KeyCode) .

1.

Get [ContextActionService](/docs/reference/engine/classes/ContextActionService)  at the top of the script.

```

local ContextActionService = game:GetService("ContextActionService")

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

```

2.

Inside of the toolEquipped  function, call BindAction  and pass through the following arguments:

-

The name of the action (RELOAD_ACTION )

-

The action handler (onAction )

-

A value to create a touch button (true )

-

A key press to detect ([Enum.KeyCode.R](/docs/reference/engine/enums/KeyCode#R) )

```

local RELOAD_ACTION = "reloadWeapon"

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

		tool.TextureId = "rbxassetid://6593020923"

		task.wait(2)

		tool.TextureId = "rbxassetid://92628145"

	end

end

local function toolEquipped()

	ContextActionService:BindAction(RELOAD_ACTION, onAction, true, Enum.KeyCode.R)

	tool.Handle.Equip:Play()

end

```

3.

Playtest by equipping the tool and pressing the R  key on your keyboard. The backpack icon should momentarily change to a waiting symbol to signal that the weapon is reloading:

## [Unbind the action](#unbind-the-action)[](#unbind-the-action)

When the user unequips the tool, the action needs to be unbound  so they can't reload without the tool being equipped.

1.

Create a new function called toolUnequipped  and call [UnbindAction](/docs/reference/engine/classes/ContextActionService#UnbindAction) , passing through the action name.

```

local function toolEquipped()

	ContextActionService:BindAction(RELOAD_ACTION, onAction, true, Enum.KeyCode.R)

	tool.Handle.Equip:Play()

end

local function toolUnequipped()

	ContextActionService:UnbindAction(RELOAD_ACTION)

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Activated:Connect(toolActivated)

```

2.

Connect the toolUnequipped  function to the [Unequipped](/docs/reference/engine/classes/Tool#Unequipped)  event so the function will run when the event fires.

```

local ContextActionService = game:GetService("ContextActionService")

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

		tool.TextureId = "rbxassetid://6593020923"

		task.wait(2)

		tool.TextureId = "rbxassetid://92628145"

	end

end

local function toolEquipped()

	ContextActionService:BindAction(RELOAD_ACTION, onAction, true, Enum.KeyCode.R)

	tool.Handle.Equip:Play()

end

local function toolUnequipped()

	ContextActionService:UnbindAction(RELOAD_ACTION)

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Unequipped:Connect(toolUnequipped)

tool.Activated:Connect(toolActivated)

```

3.

Playtest to confirm that everything works correctly. You should be able to reload when the tool is equipped, but not when it is unequipped.

Your reloading animation is now complete - for an extra challenge, try counting down an ammo counter each time the blaster is fired. You can then deactivate the toolActivated  function when the gun has no ammo, then reactivate it once the reload animation is finished.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
