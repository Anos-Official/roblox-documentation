<!-- Source: https://create.roblox.com/docs/en-us/studio/plugins -->

Studio plugins | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/plugins.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Studio plugins

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/plugins.md)

A plugin  is an extension that adds additional features or functionality to Studio. You can [install](/docs/en-us/production/creator-store#find-assets)  community-made plugins from the Creator Store, or you can [create](#create-new-plugins)  and [publish](#upload-plugins)  your own to the [Toolbox](/docs/en-us/projects/assets/toolbox)  to use across your games.

If you choose to also distribute your plugins to the Creator Store, you can either offer them for free or sell them for United States Dollars . Roblox offers a market-leading revenue share for these sales, as only taxes and payment processing fees are deducted. For more information on selling plugins, see [Creator Store - Distribute and sell assets](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

## [Create new plugins](#create-new-plugins)[](#create-new-plugins)

You can create your own plugins to improve your workflow in Studio. The following code sample is a plugin called AddEmptyScript  that inserts an empty [Script](/docs/en-us/reference/engine/classes/Script)  as the child of an [Instance](/docs/en-us/reference/engine/classes/Instance)  or in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) . The following sections explain the major parts to creating this plugin.

To begin, you should enable Plugin Debugging Enabled  in the Studio  section of Studio's settings. This will expose the [PluginDebugService](/docs/en-us/reference/engine/classes/PluginDebugService)  in Studio which provides real-time debugging for your plugin's code and makes it easier to reload and save your plugin.

AddEmptyScript Plugin

```

local ServerScriptService = game:GetService("ServerScriptService")

local Selection = game:GetService("Selection")

-- Create a new toolbar section and Plugins menu folder titled "Custom"

local toolbar = plugin:CreateToolbar("Custom")

-- Add a toolbar button labeled "Empty Script"

local newScriptButton = toolbar:CreateButton("Empty Script", "Create an empty script", "rbxassetid://14978048121")

-- Make button clickable even if 3D viewport is hidden

newScriptButton.ClickableWhenViewportHidden = true

local function onPluginButtonClicked()

	local selectedObjects = Selection:Get()

	local parent = selectedObjects[1] or ServerScriptService

	local newScript = Instance.new("Script")

	newScript.Source = ""

	newScript.Parent = parent

end

newScriptButton.Click:Connect(onPluginButtonClicked)

```

### [Save plugin script](#save-plugin-script)[](#save-plugin-script)

To create a plugin, first create a [Script](/docs/en-us/reference/engine/classes/Script)  and save it locally.

1.

Insert a new [Script](/docs/en-us/reference/engine/classes/Script)  inside [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage)  and rename it to AddEmptyScript .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Plugin-Empty-Script-Adder.png)

2.

Copy and paste the AddEmptyScript Plugin  code above into the new script.

3.

With the new script selected in the Explorer  window, select Save as Local Plugin  from Studio's Plugins  menu.

4.

In the popup window, click Save  to insert the plugin script into your local Plugins  folder of the Studio installation.

5.

The plugin should appear in [PluginDebugService](/docs/en-us/reference/engine/classes/PluginDebugService)  and start running.

6.

IMPORTANT

 Delete the original script in [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage)  and work from the AddEmptyScript  plugin inside [PluginDebugService](/docs/en-us/reference/engine/classes/PluginDebugService) , otherwise you may end up applying changes to the wrong script.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Plugin-Created.png)

To update a specific plugin within [PluginDebugService](/docs/en-us/reference/engine/classes/PluginDebugService) , right‑click it and select Save and Reload Plugin  from the context menu. If you simply want to reload the plugin, for example to step through a section of code using a breakpoint without saving the plugin, right‑click it and select Reload Plugin .

At the broadest level, you can also update all  plugins by right-clicking [PluginDebugService](/docs/en-us/reference/engine/classes/PluginDebugService)  and selecting Save and Reload All Plugins in Debugger  (shortcut Ctrl Shift L  or ⌘ Shift L ).

### [Add toolbar button](#add-toolbar-button)[](#add-toolbar-button)

To add a button for your plugin to the Plugins  tab of the Studio toolbar, use the [Plugin:CreateToolbar()](/docs/en-us/reference/engine/classes/Plugin#CreateToolbar)  and [PluginToolbar:CreateButton()](/docs/en-us/reference/engine/classes/PluginToolbar#CreateButton)  methods. In the code for AddEmptyScript , line 5 creates a new section in the toolbar and Plugins  menu folder titled Custom , while line 8 creates a button labeled Empty Script .

 ![New plugin button added to toolbar in Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Custom-Plugin-Button.png)

### [Execute code on click](#execute-code-on-click)[](#execute-code-on-click)

To make the plugin execute code when a user clicks the toolbar button, connect a function to the button's [PluginToolbarButton.Click](/docs/en-us/reference/engine/classes/PluginToolbarButton#Click)  event. In the code for AddEmptyScript , the connecting function is onPluginButtonClicked() .

### [Check user selection](#check-user-selection)[](#check-user-selection)

To modify a plugin's behavior based on what the user has selected, use the [Selection](/docs/en-us/reference/engine/classes/Selection)  service. The onPluginButtonClicked()  function checks if the user has anything selected and creates the new script as its child instead of inside [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) . If the user doesn't have anything selected, it creates the new script in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Plugin-Inserted-Script.png)

### [Support undo and redo](#support-undo-and-redo)[](#support-undo-and-redo)

Use [ChangeHistoryService](/docs/en-us/reference/engine/classes/ChangeHistoryService)  to allow users to undo and redo changes made by a plugin within a game. In your script, set the plugin to call [TryBeginRecording()](/docs/en-us/reference/engine/classes/ChangeHistoryService#TryBeginRecording)  and store the identifier assigned to the API call before making changes. Then set the plugin to call [FinishRecording()](/docs/en-us/reference/engine/classes/ChangeHistoryService#FinishRecording)  after making changes, so it captures any changes made during the recording session for undo and redo.

The following code sample creates an example plugin that can apply the neon material to selected parts. It uses [ChangeHistoryService](/docs/en-us/reference/engine/classes/ChangeHistoryService)  to record and manage the changes made by the plugin:

Example Material Plugin with Recordings for Undo and Redo

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

-- Create an example plugin

local toolbar = plugin:CreateToolbar("Example Plugin")

local button = toolbar:CreateButton("Neon it up", "", "")

-- Connect a function to the click event

button.Click:Connect(function()

	-- Try to begin a recording with a specific identifier

	local recording = ChangeHistoryService:TryBeginRecording("Set selection to neon")

	-- Check if recording was successfully initiated

	if not recording then

		-- This indicates that your plugin began a previous recording and never completed it

		-- You may only have one recording per plugin active at a time

		return

	end

	-- Iterate through the selected instances

	for _, instance in Selection:Get() do

		-- Check if the instance is a BasePart

		if instance:IsA("BasePart") then

			instance.Material = Enum.Material.Neon -- Set the material of the part to Neon

		end

	end

	-- Finish the recording, committing the changes to the history

	ChangeHistoryService:FinishRecording(recording, Enum.FinishRecordingOperation.Commit)

end)

```

Note the following caveats with [ChangeHistoryService](/docs/en-us/reference/engine/classes/ChangeHistoryService)  recordings:

-

If you're using the [Multi-line Command Bar](/docs/en-us/studio/overview#command-bar) , don't run any code in the command bar that will always be running while you have a place open, since the command bar uses [ChangeHistoryService](/docs/en-us/reference/engine/classes/ChangeHistoryService)  recordings to allow for undo/redo with commands that make changes to the [DataModel](/docs/en-us/reference/engine/classes/DataModel) .

-

Reloading a plugin won't cancel its ongoing [ChangeHistoryService](/docs/en-us/reference/engine/classes/ChangeHistoryService)  recordings, so make use of [attributes](/docs/en-us/scripting/attributes#create-attributes)  to store the last recording identifier so it can be canceled by the plugin when it reloads.

## [Upload plugins](#upload-plugins)[](#upload-plugins)

After you finish creating a plugin, you can upload it to your inventory so that it is accessible across all of your projects.

To upload a plugin:

1.

In the Explorer  window, select a plugin script.

2.

Navigate to Studio's Plugins  menu, then select Publish as Plugin .

3.

OPTIONAL

 In the upper-left corner of the asset configuration window, click the default puzzle piece image to upload a 512×512 image thumbnail for your plugin.

4.

Fill in the following fields:

-

Name  — A title for your plugin.

-

Description  — A description that describes what a potential user can expect the plugin to do.

-

Creator  — The creator or group that you want to attribute as the creator of the plugin.

5.

Click the Submit  button. Your plugin is now available to you in the [Toolbox](/docs/en-us/projects/assets/toolbox)  under the Inventory  and Creations  tabs.

## [Distribute and sell plugins](#distribute-and-sell-plugins)[](#distribute-and-sell-plugins)

You can publicly distribute and sell your own plugins on the Creator Store for others to use within their own game development. This monetization method lets you earn 100% of net proceeds on transactions, bypassing platform fees and DevEx rates. For more information on this process, including how to set up a seller account to set prices and receive payouts, see [Creator Store - Distribute and sell assets](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
