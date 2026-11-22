<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ProceduralModel -->

ProceduralModel | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ProceduralModel.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/en-us/reference/engine/classes/PVInstance)
8. /
9. [Model](/docs/en-us/reference/engine/classes/Model)
10. /
11. [ProceduralModel](/docs/en-us/reference/engine/classes/ProceduralModel)

English

Feedback

Engine Class

ProceduralModel

---

## Summary

Properties

|

[GenerationError](#GenerationError) :[string](/docs/en-us/luau/strings)

 |
| --- | --- |
|

[Generator](#Generator) :[ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript)

 |
|

[Size](#Size) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Methods

|

[ForceGeneration](#ForceGeneration) () :[boolean](/docs/en-us/luau/booleans)

 |
|

[WaitForGenerationAsync](#WaitForGenerationAsync) () :[boolean](/docs/en-us/luau/booleans)

 |

Inherited Members

26  inherited from [Model](/docs/en-us/reference/engine/classes/Model)

4  inherited from [PVInstance](/docs/en-us/reference/engine/classes/PVInstance)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

GenerationError

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

ProceduralModel.GenerationError :[string](/docs/en-us/luau/strings)

Provide feedback

---

Generator

Read Parallel

Capabilities: Basic

ProceduralModel.Generator :[ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript)

Code Samples

Default Generator Module

```

-- A generator module is a ModuleScript that defines how a ProceduralModel builds its contents.

-- See https://create.roblox.com/docs/reference/engine/classes/ProceduralModel for details.

--

-- To be used as a generator, the ModuleScript must return a table with two fields:

--   * `Attributes`  - a table of default values. Each key becomes an attribute on every

--                     ProceduralModel that uses this generator. Users can then tweak these

--                     attributes in the Properties panel to re-run generation with new inputs.

--   * `OnGenerate`  - a function the engine calls to (re)build the model's contents.

--

-- Nothing about this script or its placement is special. It can live anywhere in the DataModel

-- and the `Generator` property on a ProceduralModel can be reassigned to point at it.

-- The type annotations below are optional but documented here so the required shape is explicit.

-- `GenerationFunctionParams` is passed to `OnGenerate` every time generation runs. It exposes:

--   * `Attributes` - the current attribute values on the ProceduralModel.

--   * `Size`       - the bounding volume to generate within (from `ProceduralModel.Size`).

--   * `Pause`      - a cooperative yield. Call `parameters:Pause()` inside long loops so large

--                    generations don't stall the calling thread; the engine may resume you later.

type GenerationFunctionParams<Attributes> = {

	Attributes: Attributes,

	Size: Vector3,

	Pause: (self: GenerationFunctionParams<Attributes>) -> (),

}

-- `GeneratorModuleDefinition` is the table the ModuleScript must return.

-- `OnGenerate` must not return a value; parent generated instances into `targetContainer` instead.

-- Anything parented to `targetContainer` (or its descendants) becomes the output of generation.

type GeneratorModuleDefinition<Attributes> = {

	Attributes: Attributes,

	OnGenerate: (

		parameters: GenerationFunctionParams<Attributes>,

		targetContainer: GeneratedFolder

	) -> (),

}

-- Default attributes. Each entry here shows up as an editable attribute on the ProceduralModel.

-- A fixed `RandomSeed` keeps generation deterministic: the same inputs always produce the same

-- output, which is important because generation may run many times as the user edits properties.

local defaultAttributes = {

	BorderThickness = 1,

	RandomSeed = 142376088,

}

local Generator: GeneratorModuleDefinition<typeof(defaultAttributes)> = {

	Attributes = defaultAttributes,

	OnGenerate = function(parameters, targetContainer)

		-- Inputs. `parameters.Attributes` reflects whatever the user has set on the

		-- ProceduralModel; `parameters.Size` is the bounding box to build into.

		local borderThickness = parameters.Attributes.BorderThickness

		local random = Random.new(parameters.Attributes.RandomSeed)

		local size = parameters.Size

		-- Derived values. Seeded `random` above makes these reproducible per RandomSeed.

		local minSize = math.min(size.X, size.Y, size.Z)

		local baseColor = Color3.fromHSV(random:NextNumber(0.5, 0.8), 0.7, 0.8)

		local outlineColor = Color3.fromHSV(random:NextNumber(), 0.4, 0.25)

		-- Small helpers to make the construction below read top-to-bottom. You don't need

		-- helpers like these to write a generator; they just cut down on repetition.

		local function assignProperties(instance: Instance, properties: { [string]: unknown })

			-- Set Parent last so other properties are in place before the instance enters

			-- the DataModel and fires Changed events.

			for name, value in properties do

				if name ~= "Parent" then

					(instance :: any)[name] = value

				end

			end

			if properties.Parent ~= nil then

				instance.Parent = properties.Parent :: Instance

			end

			return instance

		end

		local function createInstance(className: string, properties: { [string]: unknown })

			return assignProperties(Instance.new(className), properties)

		end

		local function createPartWithDefaults(properties: { [string]: unknown })

			-- Generated parts are typically anchored and non-colliding; override per-part as needed.

			local part = createInstance("Part", {

				Anchored = true,

				CanCollide = false,

				Color = baseColor,

				Material = Enum.Material.SmoothPlastic,

				BottomSurface = Enum.SurfaceType.Smooth,

				TopSurface = Enum.SurfaceType.Smooth,

			})

			return assignProperties(part, properties)

		end

		-- Everything below parents into `targetContainer`, which is how instances become

		-- part of the generated output. Instances not parented here are discarded.

		-- Invisible bounding part used as the billboard adornee.

		local bounds = createPartWithDefaults({

			Name = "Bounds",

			Parent = targetContainer,

			Transparency = 1,

			Size = size,

		})

		-- A recessed platform with a border outline underneath it.

		local base = createPartWithDefaults({

			Name = "PlatformBase",

			Parent = targetContainer,

			Color = baseColor,

			CFrame = CFrame.new(0, (-size.Y + 1) / 2, 0),

			Size = Vector3.new(

				size.X - 2 * borderThickness,

				1.01,

				size.Z - 2 * borderThickness

			),

		})

		local outline = createPartWithDefaults({

			Name = "PlatformOutline",

			Parent = targetContainer,

			Color = outlineColor,

			Position = Vector3.yAxis * (-size.Y + 1) / 2,

			Size = Vector3.new(size.X, 1, size.Z),

		})

		-- "Hello World!" billboard. Generators can create any instance type, not just parts.

		local billboard = createInstance("BillboardGui", {

			Name = "Text",

			Parent = targetContainer,

			Adornee = bounds,

			LightInfluence = 0,

			Size = UDim2.fromScale(minSize, minSize),

		})

		local textLabel = createInstance("TextLabel", {

			Name = "HelloWorld",

			Parent = billboard,

			AnchorPoint = Vector2.new(0.5, 0.5),

			BackgroundTransparency = 1,

			Position = UDim2.fromScale(0.5, 0.5),

			Size = UDim2.fromScale(1, 1),

			Text = "Hello World!",

			TextColor3 = baseColor,

			TextScaled = true,

			TextStrokeTransparency = 0,

		})

		local textStroke = createInstance("UIStroke", {

			Parent = textLabel,

			Color = outlineColor,

			Thickness = borderThickness * 3,

		})

	end,

}

-- Returning the module definition is what makes this ModuleScript usable as a `Generator`.

return Generator

```

Classic Ladder Generator Module

```

-- A generator module is a ModuleScript that returns a table with `Attributes` and `OnGenerate`.

-- Assigning this ModuleScript to a ProceduralModel's `Generator` property runs `OnGenerate`

-- whenever the model's Size, attributes, or the module source changes.

-- See https://create.roblox.com/docs/reference/engine/classes/ProceduralModel.

local ClassicRobloxLadderGenerator = {}

-- Default attribute values. Each key becomes an editable attribute on any ProceduralModel that

-- uses this generator, and shows up in the Studio Properties panel under Attributes. Editing any

-- of them re-runs `OnGenerate` with the new values.

ClassicRobloxLadderGenerator.Attributes = {

	RungSpacing = 2,

	RungThickness = 1,

	PostSize = 1,

	Color = Color3.new(0.5, 0.3, 0),

}

-- `OnGenerate` is called by the engine to build the model's contents.

-- Contract:

--   * `parameters.Size`       - the bounding box (from `ProceduralModel.Size`) to build within.

--   * `parameters.Attributes` - current attribute values on the ProceduralModel.

--   * `parameters:Pause()`    - cooperative yield; call inside long loops so large generations

--                               don't stall the thread.

--   * `targetContainer`       - anything parented here (or to its descendants) becomes the output.

--   * Do not return a value from `OnGenerate`; outputs are communicated via `targetContainer`.

ClassicRobloxLadderGenerator.OnGenerate = function(parameters, targetContainer)

	local size = parameters.Size

	local rungThickness = parameters.Attributes.RungThickness

	local postSize = parameters.Attributes.PostSize

	local count = (size.Y - rungThickness) // parameters.Attributes.RungSpacing + 1

	local function createPart(position, size)

		local part = Instance.new("Part")

		part.Size = size

		part.Position = position

		part.Anchored = true

		part.Color = parameters.Attributes.Color

		part.TopSurface = Enum.SurfaceType.Smooth

		part.BottomSurface = Enum.SurfaceType.Smooth

		-- Parenting into `targetContainer` is what adds the part to the generated output.

		part.Parent = targetContainer

	end

	-- Rungs, stacked from the bottom of the bounding box upward.

	local position = Vector3.new(0, -size.Y / 2 + rungThickness / 2, 0)

	for i = 1, count do

		-- Yield between rungs so a ladder with many rungs doesn't block the thread.

		parameters:Pause()

		createPart(position, Vector3.new(size.X - 2 * postSize, rungThickness, size.Z))

		position += Vector3.new(0, parameters.Attributes.RungSpacing, 0)

	end

	-- Left and right side posts spanning the full height.

	createPart(Vector3.new(-0.5 * size.X + postSize / 2, 0, 0), Vector3.new(postSize, size.Y, size.Z))

	createPart(Vector3.new(0.5 * size.X - postSize / 2, 0, 0), Vector3.new(postSize, size.Y, size.Z))

end

-- Returning the module definition is what makes this ModuleScript usable as a `Generator`.

return ClassicRobloxLadderGenerator

```

Provide feedback

---

Size

Read Parallel

Capabilities: Basic

ProceduralModel.Size :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Methods

ForceGeneration

Capabilities: Basic

ProceduralModel:ForceGeneration () :[boolean](/docs/en-us/luau/booleans)

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

WaitForGenerationAsync

Yields

Capabilities: Basic

ProceduralModel:WaitForGenerationAsync () :[boolean](/docs/en-us/luau/booleans)

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

Failed generation

```

local proceduralModel = ...

proceduralModel:SetAttribute("ThrowAnError", true) --> Deliberately fail

print(proceduralModel:WaitForGenerationAsync()) --> false

```

Provide feedback

---

Jump to

▼

ProceduralModel

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[GenerationError](#GenerationError)

[Generator](#Generator)

[Size](#Size)

[Methods](#methods)

[ForceGeneration()](#ForceGeneration)

[WaitForGenerationAsync()](#WaitForGenerationAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
