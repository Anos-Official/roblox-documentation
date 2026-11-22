<!-- Source: https://create.roblox.com/docs/en-us/avatar/in-experience-creation -->

Avatar in-experience creation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/in-experience-creation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. In-game creation

# Avatar in-experience creation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/in-experience-creation.md)

The following guide applies to creators who are familiar with scripting and Roblox Studio and intend to develop experiences that allow user-generated avatar items.

You can publish an experience that allows players to create, customize, and purchase avatar bodies in real time, in addition to [in-experience makeup creation](/docs/en-us/avatar/in-experience-creation-makeup) . When purchased, these custom items save directly to the player's Roblox inventory, allowing players to equip and wear them in other experiences.

Experience owners that implement in-experience avatar creation benefit from [Marketplace commissions](/docs/en-us/marketplace/marketplace-fees-and-commissions#commissions)  as the publisher  of the avatar item, while the player who creates it is the item's creator . If an asset created in-experience is inspected, the item provides a link to the original experience it was created.

You can test in-experience creation in Roblox's [Avatar Creator](https://www.roblox.com/games/124012682058672/Roblox-Avatar-Creator)  demo.

Avatar assets created in-experience are not listed on the Marketplace, and cannot be resold or traded.

## [How to implement in-experience creation](#how-to-implement-in-experience-creation)[](#how-to-implement-in-experience-creation)

Use the following instructions and code references to create your first in-experience avatar creation project. The following instructions uses a base body [Model](/docs/en-us/reference/engine/classes/Model)  that players can modify and customize before publishing.

Before getting started, familiarize yourself with the following:

-

Avatar models — The following implementation requires importing a base body that meets Roblox's 15 part specifications. This [Model](/docs/en-us/reference/engine/classes/Model)  serves as a base for additional user customization and modification.

-

The base body must meet Roblox's [Avatar body guidelines](/docs/en-us/marketplace/marketplace-policy#avatar-body-guidelines) , including the minimum number of FACS control for facial rigging.

-

[Avatar creation tokens](#generate-an-avatar-creation-token)  — Experiences implementing avatar creation require at least one creation token. These tokens require Robux to purchase and allow you to set prices and other sale settings for purchases made in-experience.

-

API classes

-

[AvatarCreationService](/docs/en-us/reference/engine/classes/AvatarCreationService)  — Handles avatar creation prompting and validation.

-

[EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  — Handles runtime creation and manipulation of textures.

-

[EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh)  — Handles runtime manipulation of mesh geometry.

-

[WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  — Handles runtime manipulation of invisible outer cage geometry that allow avatar characters to equip [3D clothing](/docs/en-us/avatar/layered-accessories) .

### [Import a base body](#import-a-base-body)[](#import-a-base-body)

The base body acts as the initial foundation which users can customize and edit. You can use your own [Model](/docs/en-us/reference/engine/classes/Model) , or import a custom asset with the [Importer](/docs/en-us/studio/importer)  and setup through [Avatar Setup](/docs/en-us/avatar-setup) .

Base bodies must adhere to Roblox's avatar specifications, and must include components such as the 15 [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  instances that make up 6 body parts: head, torso, left arm, left leg, right arm, and right leg, as well as other [avatar components](/docs/en-us/avatar/character-bodies#character-body-components) .

If you have a single-mesh body, you can try using the [Avatar Auto Setup](/docs/en-us/avatar-setup#avatar-auto-setup)  to automatically add all the necessary avatar components.

For references and samples of properly configured avatar bodies, see [Avatar references](/docs/en-us/avatar/resources#references) .

### [Implement editing APIs](#implement-editing-apis)[](#implement-editing-apis)

To develop a system where users can edit the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  instances on an avatar in your experience for creation, use [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  for texture editing, [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh)  for mesh editing, and [WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  for maintaining skinning and FACS data during mesh edits.

1.

After importing your base body, use the following script to set up your [EditableImages](/docs/en-us/reference/engine/classes/EditableImage) , [EditableMeshes](/docs/en-us/reference/engine/classes/EditableMesh) , and [WrapDeformers](/docs/en-us/reference/engine/classes/WrapDeformer) .

```

local AssetService = game:GetService("AssetService")

local function setupBodyPart(meshPart, wrapTarget)

	-- Create and attach a WrapDeformer to the MeshPart

	local wrapDeformer = Instance.new("WrapDeformer")

	wrapDeformer.Parent = meshPart

	-- Create an editable mesh for the wrap target's cage mesh

	local cageEditableMesh: EditableMesh =

		AssetService:CreateEditableMeshAsync(Content.fromUri(wrapTarget.CageMeshId), {

			FixedSize = true,

		})

	-- Assign the cage mesh to the WrapDeformer

	wrapDeformer:SetCageMeshContent(Content.fromObject(cageEditableMesh))

end

local function setupRigidMesh(meshPart)

	-- Create an editable mesh from the original MeshPart

	local editableMesh = AssetService:CreateEditableMeshAsync(Content.fromUri(meshPart.MeshId), {

		FixedSize = true,

	})

	-- Generate a new MeshPart from the editable mesh

	local newMeshPart = AssetService:CreateMeshPartAsync(Content.fromObject(editableMesh))

	-- Copy size, position, and texture from the original MeshPart

	newMeshPart.Size = meshPart.Size

	newMeshPart.CFrame = meshPart.CFrame

	newMeshPart.TextureContent = meshPart.TextureContent

	-- Apply the new MeshPart back to the original

	meshPart:ApplyMesh(newMeshPart)

end

local function setupMeshTexture(meshPart, textureIdToEditableImageMap)

	-- If EditableImage already exists for this TextureID, resuse it rather than making a new one

	if textureIdToEditableImageMap[meshPart.TextureID] then

		meshPart.TextureContent =

			Content.fromObject(textureIdToEditableImageMap[meshPart.TextureID])

		return

	end

	-- Create a new EditableImage and apply it as the texture content

	local editableImage = AssetService:CreateEditableImageAsync(Content.fromUri(meshPart.TextureID))

	textureIdToEditableImageMap[meshPart.TextureID] = editableImage

	meshPart.TextureContent = Content.fromObject(editableImage)

end

local function setupModel(model)

	-- Map for reusing EditableImage instances by texture ID

	local textureIdToEditableImageMap = {}

	for _, descendant in model:GetDescendants() do

		if not descendant:IsA("MeshPart") then

			continue

		end

		-- Configure MeshPart based on WrapTarget presence

		-- If WrapTarget is present, add a WrapDeformer child with an EditableMesh

		-- Otherwise, apply EditableMesh to the MeshPart directly

		local wrapTarget = descendant:FindFirstChildOfClass("WrapTarget")

		if wrapTarget then

			setupBodyPart(descendant, wrapTarget)

		else

			setupRigidMesh(descendant)

		end

		-- Configure the EditableImage for the MeshPart

		setupMeshTexture(descendant, textureIdToEditableImageMap)

	end

end

```

2.

Create [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  tools that allow players to recolor, draw, or add stickers to your base body. You can leverage APIs in like [DrawImage()](/docs/en-us/reference/engine/classes/EditableImage#DrawImage) , [DrawRectangle()](/docs/en-us/reference/engine/classes/EditableImage#DrawRectangle) , [WritePixelsBuffer()](/docs/en-us/reference/engine/classes/EditableImage#WritePixelsBuffer) .

-

For advanced transformations, [DrawImageTransformed()](/docs/en-us/reference/engine/classes/EditableImage#DrawImageTransformed)  allows you to specify position, rotation, and scale when drawing one EditableImage onto another. Similarly, [DrawImageProjected()](/docs/en-us/reference/engine/classes/EditableImage#DrawImageProjected)  works much like [DrawImage()](/docs/en-us/reference/engine/classes/EditableImage#DrawImage)  but projects the drawn image properly if the [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  instance is used with a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

```

local function recolorTexture(

	meshPart: MeshPart,

	color: Color3

)

	local bodyPartTexture = AssetService:CreateEditableImageAsync(meshPart.TextureID)

	meshPart.TextureContent = Content.fromObject(bodyPartTexture)

	bodyPartTexture:DrawRectangle(

		Vector2.new(0, 0),

		bodyPartTexture.Size,

		color,

		0,

		Enum.ImageCombineType.Overwrite

	)

end

local function applySticker(

	meshPart: MeshPart,

	textureCoordinate: Vector2,

	stickerId: TextureId

)

	local bodyPartTexture = AssetService:CreateEditableImageAsync(meshPart.TextureID)

	meshPart.TextureContent = Content.fromObject(bodyPartTexture)

	local stickerTexture = AssetService:CreateEditableImageAsync(stickerId)

	bodyPartTexture:DrawImage(textureCoordinate, stickerTexture, Enum.ImageCombineType.BlendSourceOver)

end

local function applyStickerProjected(

  meshPart: MeshPart,

  targetMesh: EditableMesh,

  stickerId: TextureId,

  raycastHitPos: Vector3

)

  local bodyPartTexture = AssetService:CreateEditableImageAsync(meshPart.TextureID)

  local relativePos = meshPart.CFrame:PointToWorldSpace(raycastHitPos)

  local direction = (workspace.CurrentCamera.CFrame.Position - relativePos).Unit

  local projectionParams: ProjectionParams = {

      Direction = meshPart.CFrame:VectorToObjectSpace(direction),

      Position = meshPart.CFrame:PointToObjectSpace(relativePos),

      Size = Vector3.new(1, 1, 1),

      Up = meshPart.CFrame:VectorToObjectSpace(Vector3.new(0, 1, 0)),

  }

  local stickerTexture = AssetService:CreateEditableImageAsync(stickerId)

  local localBrushConfig: BrushConfig = {

      Decal = stickerTexture,

      ColorBlendType = Enum.ImageCombineType.BlendSourceOver,

      AlphaBlendType = Enum.ImageAlphaType.Default,

      BlendIntensity = 1,

      FadeAngle = 90.0

  }

  bodyPartTexture:DrawImageProjected(targetMesh, projectionParams, localBrushConfig)

end

```

3.

Using [WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  and [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh) , create tools for editing mesh deformations on your body.

1.

[WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  handles the live deformations of the rendered [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  geometry while maintaining the underlying skinning and FACS data.

2.

[EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh)  allows you to modify the cage mesh that the [WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  responds to.

1.

Use [WrapDeformer:SetCageMeshContent()](/docs/en-us/reference/engine/classes/WrapDeformer#SetCageMeshContent)  to apply the [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh)  instance that represents the relevant cage mesh to the [WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer) .

2.

Use [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh) , such as [SetPosition()](/docs/en-us/reference/engine/classes/EditableMesh#SetPosition) , to deform vertices and edit the shape of the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

```

local function deformBodyPart(

	meshPart: MeshPart,

	controlPointCenter: Vector3,

	controlPointRadius: number,

	controlPointDeformation: Vector3

)

	local wrapTarget = meshPart:FindFirstChildWhichIsA("WrapTarget")

	local cageMeshId = wrapTarget.CageMeshId

	local wrapDeformer = Instance.new("WrapDeformer")

	wrapDeformer.Parent = meshPart

	local cageEditableMesh = AssetService:CreateEditableMeshAsync(cageMeshId)

	local verticesWithinSphere =

		cageEditableMesh:FindVerticesWithinSphere(controlPointCenter, controlPointRadius)

	for _, vertexId in verticesWithinSphere do

		local vertexPosition = cageEditableMesh:GetPosition(vertexId)

		cageEditableMesh:SetPosition(vertexId, vertexPosition + controlPointDeformation)

	end

	wrapDeformer:SetCageMeshContent(Content.fromObject(cageEditableMesh))

end

```

### [Create creation prompt](#create-creation-prompt)[](#create-creation-prompt)

After setting up your base body and editing APIs, create a prompt for users to create and purchase from the experience using [AvatarCreationService:PromptCreateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync) .

```

export type BodyPartInfo = {

	bodyPart: Enum.BodyPart,

	instance: Instance --Folder with Created MeshParts

}

export type BodyPartList = {BodyPartInfo}

local function publishAvatar(bodyPartInstances: BodyPartList, player: Player, tokenId: string)

	local humanoidDescription = Instance.new("HumanoidDescription")

	for _, bodyPartInfo in bodyPartInstances do

		local bodyPartDescription = Instance.new("BodyPartDescription")

		bodyPartDescription.Instance = bodyPartInfo.instance

		bodyPartDescription.BodyPart = bodyPartInfo.bodyPart

		bodyPartDescription.Parent = humanoidDescription

	end

	local success, result, bundleIdOrErrorMessage, outfitId = pcall(function()

		return AvatarCreationService:PromptCreateAvatarAsync(tokenId, player, humanoidDescription)

	end)

	if success then

		if result == Enum.PromptCreateAvatarResult.Success then

			print("Successfully uploaded with BundleId: ", bundleIdOrErrorMessage)

      print("Successfully uploaded with OutfitId: ", outfitId)

		else

			print("Unsuccessfully uploaded with error message:", bundleIdOrErrorMessage)

		end

	else

		print("Avatar creation unsuccessful")

	end

end

```

[AvatarCreationService:PromptCreateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  takes a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  parameter to represent the avatar intended for purchase or creation. For avatar creation, the character's [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  must include new assets to be created for each of the 6 body parts ([Head](/docs/en-us/reference/engine/enums/BodyPart#Head) , [Torso](/docs/en-us/reference/engine/enums/BodyPart#Torso) , [RightLeg](/docs/en-us/reference/engine/enums/BodyPart#RightLeg) , [LeftLeg](/docs/en-us/reference/engine/enums/BodyPart#LeftLeg) , [RightArm](/docs/en-us/reference/engine/enums/BodyPart#RightArm) , [LeftArm](/docs/en-us/reference/engine/enums/BodyPart#LeftArm) ). Optionally, it can also include a new [Hair](/docs/en-us/reference/engine/enums/AccessoryType#Hair)  accessory.

To support this, the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  should include 6 [BodyPartDescription](/docs/en-us/reference/engine/classes/BodyPartDescription)  children. Each [BodyPartDescription.Instance](/docs/en-us/reference/engine/classes/BodyPartDescription#Instance)  property references a [Folder](/docs/en-us/reference/engine/classes/Folder)  which includes all of the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  instances that make up the body part. For example, the LeftArm  folder contains LeftHand , LeftUpperArm , and LeftLowerArm  [MeshParts](/docs/en-us/reference/engine/classes/MeshPart) . The [BodyPartDescription.BodyPart](/docs/en-us/reference/engine/classes/BodyPartDescription#BodyPart)  property should also be set to the relevant [Enum.BodyPart](/docs/en-us/reference/engine/enums/BodyPart) .

Each of the 15 [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  body parts must include:

-

An [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) .

-

A [WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  with an [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh) .

The provided [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  should not include any pre-existing asset IDs to represent body parts or accessories on the intended creation. On the other hand, the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  may include the humanoid scales of [BodyTypeScale](/docs/en-us/reference/engine/classes/HumanoidDescription#BodyTypeScale) , [HeadScale](/docs/en-us/reference/engine/classes/HumanoidDescription#HeadScale) , [HeightScale](/docs/en-us/reference/engine/classes/HumanoidDescription#HeightScale) , [WidthScale](/docs/en-us/reference/engine/classes/HumanoidDescription#WidthScale) , and [ProportionScale](/docs/en-us/reference/engine/classes/HumanoidDescription#ProportionScale) . Be mindful of the scales that a base body is imported with so that they match the scales provided to the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec/Avatar-Creation-Format.png)

#### [Include accessories](#include-accessories)[](#include-accessories)

If including an accessory, such as hair, the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  should include a child [AccessoryDescription](/docs/en-us/reference/engine/classes/AccessoryDescription)  where:

-

The [AccessoryDescription.Instance](/docs/en-us/reference/engine/classes/AccessoryDescription#Instance)  property references the [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance.

-

The [AccessoryDescription.AccessoryType](/docs/en-us/reference/engine/classes/AccessoryDescription#AccessoryType)  property is set to the relevant [Enum.AccessoryType](/docs/en-us/reference/engine/enums/AccessoryType) .

-

In the case of including [Enum.AccessoryType.Hair](/docs/en-us/reference/engine/enums/AccessoryType#Hair)  in your creations, the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  should include an [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) . However, it should not include a [WrapDeformer](/docs/en-us/reference/engine/classes/WrapDeformer)  child but should include an [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh)  set on the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  directly.

### [Generate an avatar creation token](#generate-an-avatar-creation-token)[](#generate-an-avatar-creation-token)

[AvatarCreationService:PromptCreateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  takes an Avatar Creation Token ID  parameter. This token is the key for creations from your universe, and it is what you can use to set the price of avatar creation from your experience. For instructions and additional details on generating tokens, see [Avatar Creation Tokens](/docs/en-us/production/monetization/avatar-creation-token) .

After purchasing and generating your token, you can inspect the token in the Creator Hub to find the ID which you can then use for the [AvatarCreationService:PromptCreateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  API.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec/Avatar-Token-Id.png)

## [Respond to players joining by attribution](#respond-to-players-joining-by-attribution)[](#respond-to-players-joining-by-attribution)

Avatar bundles created in-experience include an attribution link to the original experience the avatar was created. If the avatar is inspected by another player, a prompt displays providing an option to visit the experience where the avatar was created.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec/Avatar-Creation-Attribution.png)

To handle players joining your experience using this attribution link, use [Player:GetJoinData()](/docs/en-us/reference/engine/classes/Player#GetJoinData)  and parse the returned table for GameJoinContext .

GameJoinContext  includes the following table values:

-

JoinSource  — [Enum.JoinSource](/docs/en-us/reference/engine/enums/JoinSource)

-

A [Player](/docs/en-us/reference/engine/classes/Player)  joining your experience from this attribution link will have [Enum.JoinSource.CreatedItemAttribution](/docs/en-us/reference/engine/enums/JoinSource#CreatedItemAttribution)  to indicate entry from a created item.

-

ItemType  — optional [Enum.AvatarItemType](/docs/en-us/reference/engine/enums/AvatarItemType)

-

AssetId  — optional string

-

OutfitId  — optional string

-

AssetType  — optional [Enum.AssetType](/docs/en-us/reference/engine/enums/AssetType)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
