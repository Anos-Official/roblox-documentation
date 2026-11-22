<!-- Source: https://create.roblox.com/docs/en-us/characters/appearance -->

Character appearance | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/characters/appearance.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Characters](/docs/en-us/characters)

# Character appearance

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/characters/appearance.md)

Most games let players use their own Roblox avatar, although some implement an in-game customization system like the [UGC Homestore](/docs/en-us/resources/templates#ugc-homestore)  template. Other games make limited [modifications](/docs/en-us/characters/appearance)  to player avatars such as helmets, wings, or accessories that match the genre.

To create a unique game that alters the appearance of your users, you can customize the default character properties through [avatar settings](#global-avatar-settings)  or a [manually modify appearance](#manually-modify-appearance) .

## [Global avatar settings](#global-avatar-settings)[](#global-avatar-settings)

Studio's File  ⟩ Avatar Settings  allows you to quickly set several global player character properties in your game. These settings apply globally to all player character models joining your game. To modify specific characters, such as non-player character models, see [manually modify appearance](#manually-modify-appearance) .

In this window, you can set various presets for clothing, accessories, body parts, collision behavior, animations and more. When editing these settings, a preview of the applied settings displays in the workspace.

For more information, see [Avatar Settings](/docs/en-us/studio/avatar-settings) .

## [Manually modify appearance](#manually-modify-appearance)[](#manually-modify-appearance)

Character models contain a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  object that gives the model special characteristics, such as walking, jumping, equipping items, and interacting with the environment.

You can programmatically modify a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  by updating [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) . This includes player character models or non-player character models in your game.

You can adjust the following character properties in your game using [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) :

| Character property | | Description |
| --- | --- |
| Scale | | Number values for physical traits [height](/docs/en-us/reference/engine/classes/HumanoidDescription#HeightScale) , [width](/docs/en-us/reference/engine/classes/HumanoidDescription#WidthScale) , [head](/docs/en-us/reference/engine/classes/HumanoidDescription#HeadScale) , [body type](/docs/en-us/reference/engine/classes/HumanoidDescription#BodyTypeScale)  and [proportion](/docs/en-us/reference/engine/classes/HumanoidDescription#ProportionScale) . This doesn't affect R6 body types. |
| Accessories  | | The asset IDs of [accessories](/docs/en-us/reference/engine/classes/Accessory)  equipped by a character.  |
| Classic Clothing | | The asset IDs of the [Shirt](/docs/en-us/reference/engine/classes/Shirt) , [Pants](/docs/en-us/reference/engine/classes/Pants) , and [ShirtGraphic](/docs/en-us/reference/engine/classes/ShirtGraphic)  image textures that you can apply to the character. |
| Body Part | | The asset IDs of the [Face](/docs/en-us/reference/engine/classes/HumanoidDescription#Face) , [Head](/docs/en-us/reference/engine/classes/HumanoidDescription#Head) , [Torso](/docs/en-us/reference/engine/classes/HumanoidDescription#Torso) , [RightArm](/docs/en-us/reference/engine/classes/HumanoidDescription#RightArm) , [LeftArm](/docs/en-us/reference/engine/classes/HumanoidDescription#LeftArm) , [RightLeg](/docs/en-us/reference/engine/classes/HumanoidDescription#RightLeg)  and [LeftLeg](/docs/en-us/reference/engine/classes/HumanoidDescription#LeftLeg)  parts of a character. |
| Body Colors | | The [BodyColors](/docs/en-us/reference/engine/classes/BodyColors)  of the character's individual parts. |
| Animations | | The asset IDs of [Animations](/docs/en-us/reference/engine/classes/Animation)  you can use on a character. |

Customize a character with [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  using the following steps:

1.

[Create a description](#create-humanoiddescription)  from the user's character, a specific Outfit ID, or from a specific User ID.

2.

[Modify the description](#modify-humanoiddescription)  to customize the properties that you want to apply to the [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  character.

3.

[Apply the description](#apply-humanoiddescription)  on either a single character, all player characters, or even on all spawning characters.

When updating a character's properties through [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) , it is important to use an up-to-date [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  of that specific [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  with [Humanoid:GetAppliedDescription()](/docs/en-us/reference/engine/classes/Humanoid#GetAppliedDescription) .

### [Create HumanoidDescription](#create-humanoiddescription)[](#create-humanoiddescription)

You can create a new [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  instance directly within the Explorer  hierarchy or within a [Script](/docs/en-us/reference/engine/classes/Script)  with the following code:

Create new HumanoidDescription instance

```

local humanoidDescription = Instance.new("HumanoidDescription")

```

In most cases, you should use an existing [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  instead of a default new [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  by referencing an existing player character, avatar outfit, or user ID.

####  From the player character

Use the following code sample to create a new [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  based on the player character's current properties:

Generate a HumanoidDescription from a player character

```

local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

local humanoidDescription = Instance.new("HumanoidDescription")

if humanoid then

	humanoidDescription = humanoid:GetAppliedDescription()

end

```

####  From an existing outfit

Use the following sample code to create a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  from an outfit ID using [Players.GetHumanoidDescriptionFromOutfitID](/docs/en-us/reference/engine/classes/Players#GetHumanoidDescriptionFromOutfitId) :

Generate a HumanoidDescription from an Outfit ID

```

local Players = game:GetService("Players")

local outfitId = 480059254

local humanoidDescriptionFromOutfit = Players:GetHumanoidDescriptionFromOutfitId(outfitId)

```

####  From a specific user

Use the following sample code to create a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  from a user ID using [Players:GetHumanoidDescriptionFromUserId()](/docs/en-us/reference/engine/classes/Players#GetHumanoidDescriptionFromUserId) :

Generate a HumanoidDescription from a user ID

```

local Players = game:GetService("Players")

local userId = 491243243

local humanoidDescriptionFromUser = Players:GetHumanoidDescriptionFromUserId(userId)

```

### [Modify HumanoidDescription](#modify-humanoiddescription)[](#modify-humanoiddescription)

To customize [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  properties, set them directly on the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  or use a specified method before applying the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  to a character.

The following code sample provides examples of setting the different types of [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  properties:

Update various HumanoidDescription properties

```

local humanoidDescription = Instance.new("HumanoidDescription")

humanoidDescription.HatAccessory = "2551510151,2535600138"

humanoidDescription.BodyTypeScale = 0.1

humanoidDescription.ClimbAnimation = 619521311

humanoidDescription.Face = 86487700

humanoidDescription.GraphicTShirt = 1711661

humanoidDescription.HeadColor = Color3.new(0, 1, 0)

```

####  Set multiple accessories

For layered or bulk accessory changes, you can use [HumanoidDescription:SetAccessories()](/docs/en-us/reference/engine/classes/HumanoidDescription#SetAccessories)  to make accessory related updates. The following code sample adds a layered sweater and jacket in that order to a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) :

Change multiple accessories at once

```

local humanoidDescription = Instance.new("HumanoidDescription")

local accessoryTable = {

	{

		Order = 1,

		AssetId = 6984769289,

		AccessoryType = Enum.AccessoryType.Sweater

	},

	{

		Order = 2,

		AssetId = 6984767443,

		AccessoryType = Enum.AccessoryType.Jacket

	}

}

humanoidDescription:SetAccessories(accessoryTable, false)

```

### [Apply HumanoidDescription](#apply-humanoiddescription)[](#apply-humanoiddescription)

Apply [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  to specific [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  characters in your game with [Humanoid:ApplyDescription()](/docs/en-us/reference/engine/classes/Humanoid#ApplyDescription)  or [Humanoid.LoadCharacterWithHumanoidDescription](/docs/en-us/reference/engine/classes/Player#LoadCharacterWithHumanoidDescription) .

Changing the assets on a character while also changing [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  might lead to undefined behavior.

####  On a single character

[ApplyDescription()](/docs/en-us/reference/engine/classes/Humanoid#ApplyDescription)  can target any [Humanoid](/docs/en-us/reference/engine/classes/Humanoid) . Use the following code to add a new pair of sunglasses and a new torso to the player character:

Update HumanoidDescription for a specific player character

```

local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

if humanoid then

	local descriptionClone = humanoid:GetAppliedDescription()

	descriptionClone.Torso = 86500008

	-- Multiple face accessory assets are allowed in a comma-separated string

	descriptionClone.FaceAccessory = descriptionClone.FaceAccessory .. ",2535420239"

	-- Apply modified "descriptionClone" to humanoid

	humanoid:ApplyDescription(descriptionClone)

end

```

####  On all player characters

Use the following sample code to apply a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  to all current players in the game:

Update HumanoidDescription for all current player characters

```

local Players = game:GetService("Players")

for _, player in Players:GetPlayers() do

	local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		-- Create a HumanoidDescription

		local humanoidDescription = Instance.new("HumanoidDescription")

		humanoidDescription.HatAccessory = "2551510151,2535600138"

		humanoidDescription.BodyTypeScale = 0.1

		humanoidDescription.ClimbAnimation = 619521311

		humanoidDescription.Face = 86487700

		humanoidDescription.GraphicTShirt = 1711661

		humanoidDescription.HeadColor = Color3.new(0, 1, 0)

		humanoid:ApplyDescription(humanoidDescription)

	end

end

```

####  On all spawning characters

Use the following sample code to set a specific [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  for all spawning player characters:

Update HumanoidDescription for all spawning characters

```

local Players = game:GetService("Players")

-- Stop automatic spawning so it can be done in the "PlayerAdded" callback

Players.CharacterAutoLoads = false

local function onPlayerAdded(player)

	-- Create a HumanoidDescription

	local humanoidDescription = Instance.new("HumanoidDescription")

	humanoidDescription.HatAccessory = "2551510151,2535600138"

	humanoidDescription.BodyTypeScale = 0.1

	humanoidDescription.ClimbAnimation = 619521311

	humanoidDescription.Face = 86487700

	humanoidDescription.GraphicTShirt = 1711661

	humanoidDescription.HeadColor = Color3.new(0, 1, 0)

	-- Spawn character with the HumanoidDescription

	player:LoadCharacterWithHumanoidDescription(humanoidDescription)

end

-- Connect "PlayerAdded" event to "onPlayerAdded()" function

Players.PlayerAdded:Connect(onPlayerAdded)

```

If the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  instance was created in the Explorer  and parented to the workspace, use the following sample code in a [Script](/docs/en-us/reference/engine/classes/Script)  to access the workspace instance:

```

local Players = game:GetService("Players")

-- Stop automatic spawning so it can be done in the "PlayerAdded" callback

Players.CharacterAutoLoads = false

local function onPlayerAdded(player)

	-- Spawn character with "workspace.StudioHumanoidDescription"

	player:LoadCharacterWithHumanoidDescription(workspace.StudioHumanoidDescription)

end

-- Connect "PlayerAdded" event to "onPlayerAdded()" function

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Layered accessories on non-R15](#layered-accessories-on-non-r15)[](#layered-accessories-on-non-r15)

Caged accessories, like layered accessories, use [WrapTarget](/docs/en-us/reference/engine/classes/WrapTarget)  and [WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer)  to stretch and wrap over a target [Model](/docs/en-us/reference/engine/classes/Model) . Layered accessories can work with both standard [player characters](/docs/en-us/characters#player-characters)  and non-R15 models.

Custom implementation of layered accessories, such as a model using a unique cage UV map, cannot be uploaded and published to the Marketplace. However, you can [create custom cage meshes](/docs/en-us/art/modeling/cage-meshes)  for in-game assets like buildings, game-specific clothing, and props.

Whether you are implementing layered accessories on an [R15 rigging armature](/docs/en-us/avatar/character-bodies/specifications#rigging) , or using a custom rig, ensure that your accessories and bodies include the following:

-

The target model, typically the body, has a [WrapTarget](/docs/en-us/reference/engine/classes/WrapTarget)  component on the meshes that additional models are intended to wrap around.

-

The layering model, typically the clothing or accessory, has a [WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer)  component on the meshes meant to wrap the target model.

-

The outer cage of the target model , and the inner and outer cage of the layering model  have matching UV maps.

-

The corresponding vertices on the target cage should have the same UVs as those vertices on the layer cage.

-

If your target model is not R15, or doesn't include a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid) , you must add a [Weld](/docs/en-us/reference/engine/classes/Weld)  object to the layering [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

-

The [Weld](/docs/en-us/reference/engine/classes/Weld)  must have Part0  and Part1  set to link the layering MeshPart to the Part hierarchy of the Model. For example, Part0  refers to the accessory and Part1  refers to the parent Part.

-

If your target model is both R15 and includes a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid) , this weld is created automatically.

See the following resources for additional information on layered accessories and caging:

-

[Layered accessories caging overview](/docs/en-us/avatar/layered-accessories#cage-meshes)

-

[Layered accessories caging best practices](/docs/en-us/avatar/layered-accessories/caging-best-practices)

-

[Layered accessories cage mesh specifications](/docs/en-us/avatar/layered-accessories/specifications#cage-meshes)

-

[Avatar body cage specifications](/docs/en-us/avatar/character-bodies/specifications#outer-cages)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
