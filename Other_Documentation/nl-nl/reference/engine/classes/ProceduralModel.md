<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ProceduralModel -->

ProceduralModel | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)
8. /
9. [Model](/docs/nl-nl/reference/engine/classes/Model)
10. /
11. [ProceduralModel](/docs/nl-nl/reference/engine/classes/ProceduralModel)

Nederlands

Feedback

Engine-klasse

ProceduralModel

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ProceduralModel)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[GenerationError](#GenerationError) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[Generator](#Generator) :[ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)

 |
|

[Size](#Size) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Methoden

|

[ForceGeneration](#ForceGeneration) () :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[WaitForGenerationAsync](#WaitForGenerationAsync) () :[boolean](/docs/nl-nl/luau/booleans)

 |

Overgenomen leden

26  overgenomen van [Model](/docs/nl-nl/reference/engine/classes/Model)

4  overgenomen van [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

GenerationError

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

ProceduralModel.GenerationError :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Generator

Parallel lezen

Mogelijkheden: Basic

ProceduralModel.Generator :[ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)

Codevoorbeelden

Standaard Generator Module

```

-- Een generator module is een ModuleScript dat definieert hoe een ProceduralModel zijn inhoud bouwt.

-- Zie https://create.roblox.com/docs/reference/engine/classes/ProceduralModel voor details.

--

-- Om als generator te worden gebruikt, moet het ModuleScript een tabel retourneren met twee velden:

--   * `Attributes`  - een tabel van standaardwaarden. Elke sleutel wordt een attribuut op elke

--                     ProceduralModel die deze generator gebruikt. Gebruikers kunnen deze

--                     attributen vervolgens aanpassen in het Eigenschappen-paneel om de generatie

--                     opnieuw uit te voeren met nieuwe invoer.

--   * `OnGenerate`  - een functie die de engine aanroept om de inhoud van het model te (her)bouwen.

--

-- Niets aan dit script of de plaatsing ervan is speciaal. Het kan overal in het DataModel

-- leven en de `Generator` eigenschap op een ProceduralModel kan opnieuw worden toegewezen om naar

-- het te wijzen.

-- De type annotaties hieronder zijn optioneel maar hier gedocumenteerd zodat de vereiste structuur expliciet is.

-- `GenerationFunctionParams` wordt doorgegeven aan `OnGenerate` elke keer dat de generatie draait. Het exposeert:

--   * `Attributes` - de huidige attribuutwaarden op de ProceduralModel.

--   * `Size`       - de begrenzende volume om binnen te genereren (van `ProceduralModel.Size`).

--   * `Pause`      - een coöperatieve yield. Roep `parameters:Pause()` aan binnen lange lussen zodat grote

--                    generaties de aanroepende thread niet blokkeren; de engine kan je later hervatten.

type GenerationFunctionParams<Attributes> = {

	Attributes: Attributes,

	Size: Vector3,

	Pause: (self: GenerationFunctionParams<Attributes>) -> (),

}

-- `GeneratorModuleDefinition` is de tabel die het ModuleScript moet retourneren.

-- `OnGenerate` mag geen waarde retourneren; parent gegenereerde instanties in `targetContainer` in plaats daarvan.

-- Alles wat aan `targetContainer` (of zijn afstammelingen) is geparent, wordt de output van de generatie.

type GeneratorModuleDefinition<Attributes> = {

	Attributes: Attributes,

	OnGenerate: (

		parameters: GenerationFunctionParams<Attributes>,

		targetContainer: GeneratedFolder

	) -> (),

}

-- Standaard attributen. Elke invoer hier verschijnt als een bewerkbaar attribuut op de ProceduralModel.

-- Een vaste `RandomSeed` houdt de generatie deterministisch: dezelfde invoer produceert altijd dezelfde

-- output, wat belangrijk is omdat de generatie mogelijk meerdere keren wordt uitgevoerd terwijl de gebruiker eigenschappen bewerkt.

local defaultAttributes = {

	BorderThickness = 1,

	RandomSeed = 142376088,

}

local Generator: GeneratorModuleDefinition<typeof(defaultAttributes)> = {

	Attributes = defaultAttributes,

	OnGenerate = function(parameters, targetContainer)

		-- Invoeren. `parameters.Attributes` weerspiegelt wat de gebruiker heeft ingesteld op de

		-- ProceduralModel; `parameters.Size` is de begrenzende doos om in te bouwen.

		local borderThickness = parameters.Attributes.BorderThickness

		local random = Random.new(parameters.Attributes.RandomSeed)

		local size = parameters.Size

		-- Afgeleide waarden. Gezaaid `random` hierboven maakt deze reproduceerbaar per RandomSeed.

		local minSize = math.min(size.X, size.Y, size.Z)

		local baseColor = Color3.fromHSV(random:NextNumber(0.5, 0.8), 0.7, 0.8)

		local outlineColor = Color3.fromHSV(random:NextNumber(), 0.4, 0.25)

		-- Kleine helpers om de constructie hieronder van boven naar beneden te laten lezen. Je hebt geen

		-- helpers zoals deze nodig om een generator te schrijven; ze verminderen gewoon de herhaling.

		local function assignProperties(instance: Instance, properties: { [string]: unknown })

			-- Stel Parent als laatste in zodat andere eigenschappen op hun plaats zijn voordat de instantie binnenkomt

			-- in het DataModel en Changed-evenementen worden geactiveerd.

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

			-- Gegenereerde delen zijn doorgaans verankerd en niet-colliderend; overschrijf per deel indien nodig.

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

		-- Alles hieronder wordt geparent in `targetContainer`, wat is hoe instanties deel worden van

		-- de gegenereerde output. Instanties die hier niet aan zijn geparent, worden weggegooid.

		-- Onzichtbaar begrenzend deel dat wordt gebruikt als de billboard adornee.

		local bounds = createPartWithDefaults({

			Name = "Bounds",

			Parent = targetContainer,

			Transparency = 1,

			Size = size,

		})

		-- Een verzonken platform met een randomtrek eronder.

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

		-- "Hallo Wereld!" billboard. Generators kunnen elk type instantie creëren, niet alleen delen.

		local billboard = createInstance("BillboardGui", {

			Name = "Text",

			Parent = targetContainer,

			Adornee = bounds,

			LightInfluence = 0,

			Size = UDim2.fromScale(minSize, minSize),

		})

		local textLabel = createInstance("TextLabel", {

			Name = "HalloWereld",

			Parent = billboard,

			AnchorPoint = Vector2.new(0.5, 0.5),

			BackgroundTransparency = 1,

			Position = UDim2.fromScale(0.5, 0.5),

			Size = UDim2.fromScale(1, 1),

			Text = "Hallo Wereld!",

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

-- Het retourneren van de module definitie maakt dit ModuleScript bruikbaar als een `Generator`.

return Generator

```

Classic Ladder Generator Module

```

-- Een generator module is een ModuleScript dat een tabel retourneert met `Attributes` en `OnGenerate`.

-- Het toewijzen van dit ModuleScript aan de `Generator` eigenschap van een ProceduralModel voert `OnGenerate`

-- uit telkens wanneer de grootte, attributen of de modulebron van het model verandert.

-- Zie https://create.roblox.com/docs/reference/engine/classes/ProceduralModel.

local ClassicRobloxLadderGenerator = {}

-- Standaard attribuutwaarden. Elke sleutel wordt een bewerkbaar attribuut op elk ProceduralModel dat

-- deze generator gebruikt, en verschijnt in het Studio Eigenschappenpaneel onder Attributen. Het bewerken van elk

-- van hen voert `OnGenerate` opnieuw uit met de nieuwe waarden.

ClassicRobloxLadderGenerator.Attributes = {

	RungSpacing = 2,

	RungThickness = 1,

	PostSize = 1,

	Color = Color3.new(0.5, 0.3, 0),

}

-- `OnGenerate` wordt door de engine aangeroepen om de inhoud van het model te bouwen.

-- Contract:

--   * `parameters.Size`       - de begrenzende doos (van `ProceduralModel.Size`) om binnen te bouwen.

--   * `parameters.Attributes` - huidige attribuutwaarden op het ProceduralModel.

--   * `parameters:Pause()`    - coöperatieve yield; aanroepen binnen lange lussen zodat grote generaties

--                               de thread niet blokkeren.

--   * `targetContainer`       - alles wat hier (of aan zijn afstammelingen) is gekoppeld, wordt de output.

--   * Geef geen waarde terug van `OnGenerate`; outputs worden gecommuniceerd via `targetContainer`.

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

		-- Het koppelen aan `targetContainer` is wat het onderdeel toevoegt aan de gegenereerde output.

		part.Parent = targetContainer

	end

	-- Treden, gestapeld van de onderkant van de begrenzende doos omhoog.

	local position = Vector3.new(0, -size.Y / 2 + rungThickness / 2, 0)

	for i = 1, count do

		-- Yield tussen treden zodat een ladder met veel treden de thread niet blokkeert.

		parameters:Pause()

		createPart(position, Vector3.new(size.X - 2 * postSize, rungThickness, size.Z))

		position += Vector3.new(0, parameters.Attributes.RungSpacing, 0)

	end

	-- Linker en rechter zijpalen die de volledige hoogte overspannen.

	createPart(Vector3.new(-0.5 * size.X + postSize / 2, 0, 0), Vector3.new(postSize, size.Y, size.Z))

	createPart(Vector3.new(0.5 * size.X - postSize / 2, 0, 0), Vector3.new(postSize, size.Y, size.Z))

end

-- Het retourneren van de module-definitie is wat deze ModuleScript bruikbaar maakt als een `Generator`.

return ClassicRobloxLadderGenerator

```

Feedback geven

---

Size

Parallel lezen

Mogelijkheden: Basic

ProceduralModel.Size :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Methoden

ForceGeneration

Mogelijkheden: Basic

ProceduralModel:ForceGeneration () :[boolean](/docs/nl-nl/luau/booleans)

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

WaitForGenerationAsync

Opbrengst

Mogelijkheden: Basic

ProceduralModel:WaitForGenerationAsync () :[boolean](/docs/nl-nl/luau/booleans)

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Mislukte generatie

```

local proceduralModel = ...

proceduralModel:SetAttribute("ThrowAnError", true) --> Opzettelijk laten falen

print(proceduralModel:WaitForGenerationAsync()) --> false

```

Feedback geven

---

Ga naar

▼

ProceduralModel

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[GenerationError](#GenerationError)

[Generator](#Generator)

[Size](#Size)

[Methoden](#methods)

[ForceGeneration()](#ForceGeneration)

[WaitForGenerationAsync()](#WaitForGenerationAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
