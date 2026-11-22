<!-- Source: https://create.roblox.com/docs/parts/model-generation -->

Model generation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts/model-generation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)

# Model generation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/model-generation.md)

Through text prompts and preset schemas, you (and players in-game) can generate both static 3D assets and fully functional  models such as vehicles that drive, planes that fly, and weapons that shoot. This guide demonstrates how to use [GenerateModelAsync()](/docs/reference/engine/classes/GenerationService#GenerateModelAsync)  as part of a dynamic, player‑driven creative experience.

## [Overview](#overview)[](#overview)

[GenerateModelAsync()](/docs/reference/engine/classes/GenerationService#GenerateModelAsync)  enables generation of multi‑mesh geometries with the following advantages:

-

The provided [schema](#schema-based-generation)  defines how the generated geometry will be broken into parts.

-

Any object generated in-game will be replicated and visible to all players, allowing them to build together in real‑time.

-

Generated meshes are higher fidelity with better overall forms, silhouettes, more detail, and fewer artifacts. Generated textures are more coherent and detailed, with less graininess and less pronounced baked‑in lighting.

-

Generation times have lower latency, enabling quicker and more responsive creation in games.

-

You and even players during gametime can specify bounding boxes to suggest size and proportions of the generated model.

-

An optional max triangle count keeps generated objects performant for your game.

## [Schema-based generation](#schema-based-generation)[](#schema-based-generation)

To create articulated, functional objects, the generated geometry must be separated into multiple [MeshParts](/docs/reference/engine/classes/MeshPart) . For example, to create a drivable car with wheels that spin and steer, at least five [MeshParts](/docs/reference/engine/classes/MeshPart)  are needed: one for the car body and four for each of the car's wheels. [GenerateModelAsync()](/docs/reference/engine/classes/GenerationService#GenerateModelAsync)  achieves this through a schema  that lists the parts to generate, as shown in the following code snippet:

Script in ServerScriptService

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Set up inputs for the generated geometry

local inputs = {

	TextPrompt = "green dragon car with 4 wheels"

}

-- Set schema to the predefined five-model car chassis

local schema = {

	PredefinedSchema = "Car5"

}

-- Make the call to generate the model

local success, result, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Scale model to target size and position near world center

	local targetSize = 16

	local modelSize = result:GetExtentsSize()

	local scaleFactor = targetSize / math.max(modelSize.X, modelSize.Y, modelSize.Z)

	result:ScaleTo(scaleFactor)

	result:PivotTo(CFrame.new(0, result:GetExtentsSize().Y / 2, -40))

	-- Anchor all parts so that the meshes don't fall apart

	for _, descendant in result:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Name the model and parent it to workspace

	result.Name = "BasicDragonCarGeneration"

	result.Parent = Workspace

else

	warn(result)

end

```

[GenerateModelAsync()](/docs/reference/engine/classes/GenerationService#GenerateModelAsync)  currently supports two fixed schemas: Car5  which produces a car with a body and four wheels, and Body1  which yields a single [MeshPart](/docs/reference/engine/classes/MeshPart)  object.

The following image shows the expected output and its construction as it appears in the [Explorer](/docs/studio/explorer)  hierarchy:

![](https://prod.docsiteassets.roblox.com/assets/modeling/model-generation/Green-Dragon-Car.jpg)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-Generation-Hierarchy.png)

## [Retargetable scripts](#retargetable-scripts)[](#retargetable-scripts)

In Roblox, behaviors  typically encompass the scripts, attachments, [constraints](/docs/physics#constraints) , and other instance types attached to static textured geometries to make them functional. Since [GenerateModelAsync()](/docs/reference/engine/classes/GenerationService#GenerateModelAsync)  generates a wide range of geometries on‑the‑fly, retargetable scripts  must be attached to automatically adapt behaviors to expected functionality.

For example, consider a game where players get to make their own drivable cars. [GenerateModelAsync()](/docs/reference/engine/classes/GenerationService#GenerateModelAsync)  takes the player prompt and generates five distinct meshes (body and four wheels) via the Car5  [schema](#schema-based-generation) . Then, a preset retargetable script adapts its driving behavior to the size and shape of the model to ensure the car is drivable and its wheels spin realistically.

To test retargetable scripts:

1.

Download the [Behaviors.rbxm](https://prod.docsiteassets.roblox.com/assets/modeling/model-generation/Behaviors.rbxm)  file.

2.

In Studio's [Explorer](/docs/studio/explorer)  hierarchy, right‑click [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , select Insert  ⟩ Import Roblox Model , and choose the downloaded file. The model unpacks into several folders.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-Generation-Behaviors.png)

3.

Copy and paste one of the following code snippets into a server [Script](/docs/reference/engine/classes/Script)  within [ServerScriptService](/docs/reference/engine/classes/ServerScriptService) , depending on the object type you'd like to generate.

Car Airplane

This example generates a functional car with a brake, nitro boost, audio and visual effects, and an on‑screen UI speedometer.

Script in ServerScriptService

```

local GenerationService = game:GetService("GenerationService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

-- Set up inputs for the generated geometry

local inputs = {

	TextPrompt = "green dragon car with 4 wheels"

}

-- Set schema to the predefined five-model car chassis

local schema = {

	PredefinedSchema = "Car5"

}

-- Make the call to generate the model

local success, result, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Scale model to target size

	local targetSize = 16

	local modelSize = result:GetExtentsSize()

	local scaleFactor = targetSize / math.max(modelSize.X, modelSize.Y, modelSize.Z)

	result:ScaleTo(scaleFactor)

	-- Load "makeFunctional" module for "CarBehavior"

	local makeFunctional = require(ReplicatedStorage.Behaviors.CarBehavior.makeFunctional)

	-- Reference car parts by names guaranteed through the "Car5" schema

	local body = result:FindFirstChild("body")

	local frontLeftWheel = result:FindFirstChild("front left wheel")

	local frontRightWheel = result:FindFirstChild("front right wheel")

	local rearLeftWheel = result:FindFirstChild("rear left wheel")

	local rearRightWheel = result:FindFirstChild("rear right wheel")

	-- Set behavioral configuration parameters

	local config = {

		seatPosition = "inside",

		invisibleWhenSeated = false

	}

	-- Attach behavior via the "makeFunctional" script

	local functionalModel = makeFunctional(result, frontLeftWheel, frontRightWheel, rearLeftWheel, rearRightWheel, body, config)

	-- Position the model near world center

	functionalModel:PivotTo(CFrame.new(0, functionalModel:GetExtentsSize().Y / 2, -40))

	functionalModel.Name = "BasicDragonCarGeneration"

	functionalModel.Parent = Workspace

else

	warn(result)

end

```

To test other generated models with retargetable scripts in the Car5  schema, change the TextPrompt  string value on line 7 and playtest again. Ideas include:

-

"yellow sports car with a spoiler"

-

"purple bat car with 4 wheels"

-

"giant monster truck with spiked roof"

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
