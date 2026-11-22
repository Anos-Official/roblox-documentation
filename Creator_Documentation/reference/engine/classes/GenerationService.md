<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/GenerationService -->

GenerationService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/GenerationService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GenerationService](/docs/en-us/reference/engine/classes/GenerationService)

English

Feedback

Engine Class

GenerationService

Not Creatable

Service

---

## Summary

Methods

|

[GenerateMeshAsync](#GenerateMeshAsync) (inputs :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , player :  [Player](/docs/en-us/reference/engine/classes/Player) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , intermediateResultCallback :  [function](/docs/en-us/luau/functions) ? ) :[Tuple](/docs/en-us/luau/tuples)

Deprecated

 |
| --- | --- |
|

[GenerateModelAsync](#GenerateModelAsync) (inputs :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , schema :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ? ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[LoadGeneratedMeshAsync](#LoadGeneratedMeshAsync) (generationId :  [string](/docs/en-us/luau/strings) ) :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

 |
|

[SegmentMeshAsync](#SegmentMeshAsync) (meshPart :  [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) , schema :  [Dictionary](/docs/en-us/luau/tables#dictionaries) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ? ) :[Tuple](/docs/en-us/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

GenerateMeshAsync

Deprecated

Show details

---

GenerateModelAsync

Yields

Capabilities: DynamicGeneration

GenerationService:GenerateModelAsync (

inputs :[Dictionary](/docs/en-us/luau/tables#dictionaries) , schema :[Dictionary](/docs/en-us/luau/tables#dictionaries) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

inputs :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

schema :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

Generation of Basic Car Chassis

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Set up inputs for the generated geometry

local inputs = {

	TextPrompt = "a green dragon car with 4 wheels"

}

-- Set schema to the predefined five-model car chassis

local schema = {

	PredefinedSchema = "Car5"

}

-- Make the call to generate the model

local success, model, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Scale model to target size and position near world center

	local targetSize = 16

	local modelSize = model:GetExtentsSize()

	local scaleFactor = targetSize / math.max(modelSize.X, modelSize.Y, modelSize.Z)

	model:ScaleTo(scaleFactor)

	model:PivotTo(CFrame.new(15, model:GetExtentsSize().Y / 2, 0))

	-- Anchor all parts so that the meshes don't fall apart

	for _, descendant in model:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Name the model and parent it to workspace

	model.Name = "BasicDragonCarGeneration"

	model.Parent = Workspace

end

```

Generation With a Custom Schema

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Describe the object to generate

local inputs = {

	TextPrompt = "a wooden cart with four wheels",

}

-- Define a custom multi-part structure instead of using a predefined schema.

-- Each entry in `Groups` names a part the generation should produce.

local schema = {

	SchemaDefinition = {

		Groups = { "body", "wheel_fl", "wheel_fr", "wheel_rl", "wheel_rr" },

	},

}

-- Make the call to generate the model

local success, model, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Anchor all parts so that the meshes don't fall apart

	for _, descendant in model:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Name the model and parent it to workspace

	model.Name = "CustomSchemaGeneration"

	model.Parent = Workspace

end

```

Generation Conditioned on an Image

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Reference image used to condition the generation. Replace `0` with the asset

-- ID of your own uploaded image.

local imageAssetId = 0

local inputs = {

	Image = Content.fromAssetId(imageAssetId),

	TextPrompt = "a low-poly treasure chest",

}

-- Produce a single-mesh output

local schema = {

	PredefinedSchema = "Body1",

}

-- Make the call to generate the model

local success, model, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Anchor all parts so that the meshes don't fall apart

	for _, descendant in model:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Name the model and parent it to workspace

	model.Name = "ImageConditionedGeneration"

	model.Parent = Workspace

end

```

Provide feedback

---

LoadGeneratedMeshAsync

Yields

Capabilities: DynamicGeneration

GenerationService:LoadGeneratedMeshAsync (generationId :[string](/docs/en-us/luau/strings) ) :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

Parameters

|

generationId :[string](/docs/en-us/luau/strings)

 |

Returns

[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

Provide feedback

---

SegmentMeshAsync

Yields

Capabilities: DynamicGeneration

GenerationService:SegmentMeshAsync (

meshPart :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart) , schema :[Dictionary](/docs/en-us/luau/tables#dictionaries) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

meshPart :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

 |
|

schema :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

Jump to

▼

GenerationService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GenerateMeshAsync()](#GenerateMeshAsync)

[GenerateModelAsync()](#GenerateModelAsync)

[LoadGeneratedMeshAsync()](#LoadGeneratedMeshAsync)

[SegmentMeshAsync()](#SegmentMeshAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
