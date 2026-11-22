<!-- Source: https://create.roblox.com/docs/en-us/projects/assets/in-experience-asset-creation -->

In-game asset creation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/assets/in-experience-asset-creation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Assets](/docs/en-us/assets)

# In-game asset creation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/assets/in-experience-asset-creation.md)

With the in-game asset creation feature, you can allow your users to save creations they made in your game to their inventories. Your users can use these in-game creations just like any other asset. Additionally, these creations attribute to your game when displayed on the Roblox platform, so any user can use the attribution link to come to your game and create their own.

For example, you can enable users to create custom creatures as pets in your game, and allow them to save their favorite pets to their inventories. You have full control to specify which objects users can modify and save from your game. Users in turn can display their creations on their profiles with attribution to your game, boosting visibility of your game.

## [Supported asset types and limits](#supported-asset-types-and-limits)[](#supported-asset-types-and-limits)

Just like all assets on the platform, in-game creations are subject to [asset moderation](/docs/en-us/projects/assets#asset-moderation) . Currently, you can allow users to create the following type of in-game content:

-

Images  ([Enum.AssetType.Image](/docs/en-us/reference/engine/enums/AssetType#Image) ) from a [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  that your game generates or edits at runtime.

Creating packages ([Enum.AssetType.Model](/docs/en-us/reference/engine/enums/AssetType#Model) ) from an [Instance](/docs/en-us/reference/engine/classes/Instance)  is not currently supported.

When you are running or testing your game and the save action fails, Studio prompts error messages to the [Output window](/docs/en-us/studio/output)  or the [Developer Console](/docs/en-us/studio/developer-console) .

## [Enable in-game platform content creation](#enable-in-game-platform-content-creation)[](#enable-in-game-platform-content-creation)

To enable in-game creation for your users, use the [AssetService:PromptCreatePlatformContentAsync()](/docs/en-us/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  API method in a server-side script, along with other creation logic. Specify which objects in your game you want to enable this functionality for, set a custom trigger (such as a UI icon) for invoking the method, and listen for client remote events for saving assets.

[AssetService:PromptCreatePlatformContentAsync()](/docs/en-us/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  takes the following parameters:

-

A [Player](/docs/en-us/reference/engine/classes/Player)  object representing the user who submits a creation.

-

An Object , such as a [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) , representing the content for creation.

-

The [Enum.AssetType](/docs/en-us/reference/engine/enums/AssetType) , currently only [Enum.AssetType.Image](/docs/en-us/reference/engine/enums/AssetType#Image)  for an image.

When the server invokes [AssetService:PromptCreatePlatformContentAsync()](/docs/en-us/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync) , it prompts a Submit  dialog on the client, so the user who triggers the save action can enter a name and description for the asset. Roblox provides the dialog UI out of the box, as the save workflow is a platform-level functionality.

Before you use this method, make sure that:

-

The script calling [AssetService:PromptCreatePlatformContentAsync()](/docs/en-us/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  runs on the server.

-

Your place is published. Testing the prompt in Studio on an unpublished place fails.

-

Allow Mesh/Image APIs  is turned on for your experience.

[AssetService:PromptCreatePlatformContentAsync()](/docs/en-us/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  replaces the older [AssetService:PromptCreateAssetAsync()](/docs/en-us/reference/engine/classes/AssetService#PromptCreateAssetAsync) , which only supports creating packages from an [Instance](/docs/en-us/reference/engine/classes/Instance) . Package creation is not currently supported through the new method.

### [Create an image from an EditableImage](#create-an-image-from-an-editableimage)[](#create-an-image-from-an-editableimage)

You can also let users publish images that your game generates at runtime using [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) . The following example server-side script procedurally draws a simple logo into an [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  and prompts each player to publish it as an image asset when they join the game:

Example Script for Creating an Image

```

local AssetService = game:GetService("AssetService")

local Players = game:GetService("Players")

local BLUE = Color3.fromRGB(49, 86, 255)

local WHITE = Color3.new(1, 1, 1)

local SIZE = 400

local OUTER_SIZE = 200

local INNER_SIZE = 56

local ANGLE = 15 -- degrees, clockwise

local function generateLogo()

	-- Unrotated logo: white square with a blue square in the center.

	local logo = AssetService:CreateEditableImage({

		Size = Vector2.new(OUTER_SIZE, OUTER_SIZE),

	})

	-- Final canvas: solid blue.

	local canvas = AssetService:CreateEditableImage({

		Size = Vector2.new(SIZE, SIZE),

	})

	if not logo or not canvas then

		warn("Could not create EditableImage. Make sure access to the Editable Mesh / Image apis is enabled.")

		return nil

	end

	logo:DrawRectangle(

		Vector2.zero,

		Vector2.new(OUTER_SIZE, OUTER_SIZE),

		WHITE, 0, Enum.ImageCombineType.Overwrite

	)

	logo:DrawRectangle(

		Vector2.new((OUTER_SIZE - INNER_SIZE) / 2, (OUTER_SIZE - INNER_SIZE) / 2),

		Vector2.new(INNER_SIZE, INNER_SIZE),

		BLUE, 0, Enum.ImageCombineType.Overwrite

	)

	canvas:DrawRectangle(

		Vector2.zero,

		Vector2.new(SIZE, SIZE),

		BLUE, 0, Enum.ImageCombineType.Overwrite

	)

	-- Project the logo onto the canvas, rotated about its center.

	canvas:DrawImageTransformed(

		Vector2.new(SIZE / 2, SIZE / 2),

		Vector2.one,

		ANGLE,

		logo,

		{

			CombineType = Enum.ImageCombineType.BlendSourceOver,

			ResamplerMode = Enum.ResamplerMode.Default, -- smooth edges

		}

	)

	logo:Destroy()

	return canvas

end

Players.PlayerAdded:Connect(function(player)

	-- CoreGui needs to be loaded for the Prompt method to work.

	player.CharacterAdded:Wait()

	local logo = generateLogo()

	if not logo then

		return

	end

	local complete, result, assetId = pcall(function()

		return AssetService:PromptCreatePlatformContentAsync(player, logo, Enum.AssetType.Image)

	end)

	if complete then

		if result == Enum.PromptCreateAssetResult.Success then

			print("successfully uploaded, AssetId:", assetId)

		else

			print("Received result", result)

		end

	else

		print("error")

		print(result)

	end

end)

```

[In-Experience Creation Demo Arena](https://www.roblox.com/games/12992503026/In-Experience-Creation-Demo-Arena)  showcases an example on how you can use this feature. You can join the demo to walk through the in-game creation workflow as a user, or edit the place in Studio to reference the design.

## [Post-creation and attribution](#post-creation-and-attribution)[](#post-creation-and-attribution)

After users create and save an asset from your game, they can find it in the following places:

-

Their [My Inventory](https://en.help.roblox.com/hc/en-us/articles/360000463726-How-to-View-or-Hide-Your-Inventory-in-a-Browser)  page.

-

The Creations  tab of their [Profile](https://en.help.roblox.com/hc/en-us/articles/203313660-All-About-Profiles-Blurbs-and-Profile-Customization)  page.

-

The Development Items  tab under their Creator Dashboard [Creations](https://create.roblox.com/dashboard/creations?activeTab=Model)  page.

-

The Inventory  tab of their [Toolbox](/docs/en-us/projects/assets/toolbox)  in Studio.

When users see in-game creations on their friends' profiles or inventories, they see attribution to the original game in which the asset was created. Users can click on the attribution link to redirect to the game page, so they can join the game and create their own.

Attribution is currently tied to a specific version of the created asset. If a user saves a package from a game and further edits in Studio to create a new version, attribution no longer displays for the new version.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
