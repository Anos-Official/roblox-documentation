<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/GenerationService -->

GenerationService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GenerationService](/docs/nl-nl/reference/engine/classes/GenerationService)

Nederlands

Feedback

Engine-klasse

GenerationService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/GenerationService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GenerateMeshAsync](#GenerateMeshAsync) (inputs :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , player :  [Player](/docs/nl-nl/reference/engine/classes/Player) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , intermediateResultCallback :  [function](/docs/nl-nl/luau/functions) ? ) :[Tuple](/docs/nl-nl/luau/tuples)

Verouderd

 |
| --- | --- |
|

[GenerateModelAsync](#GenerateModelAsync) (inputs :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , schema :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ? ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[LoadGeneratedMeshAsync](#LoadGeneratedMeshAsync) (generationId :  [string](/docs/nl-nl/luau/strings) ) :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

 |
|

[SegmentMeshAsync](#SegmentMeshAsync) (meshPart :  [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , schema :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ? ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GenerateMeshAsync

Verouderd

Details weergeven

---

GenerateModelAsync

Opbrengst

Mogelijkheden: DynamicGeneration

GenerationService:GenerateModelAsync (

inputs :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) , schema :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

inputs :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

schema :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

Generatie van Basis Auto Chassis

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Stel invoer in voor de gegenereerde geometrie

local inputs = {

	TextPrompt = "een groene draak auto met 4 wielen"

}

-- Stel schema in op het vooraf gedefinieerde vijf-model auto chassis

local schema = {

	PredefinedSchema = "Car5"

}

-- Maak de aanroep om het model te genereren

local success, model, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Schaal model naar doelgrootte en positioneer nabij wereldcentrum

	local targetSize = 16

	local modelSize = model:GetExtentsSize()

	local scaleFactor = targetSize / math.max(modelSize.X, modelSize.Y, modelSize.Z)

	model:ScaleTo(scaleFactor)

	model:PivotTo(CFrame.new(15, model:GetExtentsSize().Y / 2, 0))

	-- Veranker alle onderdelen zodat de meshes niet uit elkaar vallen

	for _, descendant in model:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Geef het model een naam en maak het een kind van de workspace

	model.Name = "BasisDraakAutoGeneratie"

	model.Parent = Workspace

end

```

Generatie met een Aangepaste Schema

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Beschrijf het object dat gegenereerd moet worden

local inputs = {

	TextPrompt = "een houten wagen met vier wielen",

}

-- Definieer een aangepaste multi-part structuur in plaats van een vooraf gedefinieerd schema.

-- Elke invoer in `Groups` benoemt een onderdeel dat de generatie moet produceren.

local schema = {

	SchemaDefinition = {

		Groups = { "body", "wheel_fl", "wheel_fr", "wheel_rl", "wheel_rr" },

	},

}

-- Maak de aanroep om het model te genereren

local success, model, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Veranker alle onderdelen zodat de meshes niet uit elkaar vallen

	for _, descendant in model:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Geef het model een naam en voeg het toe aan de workspace

	model.Name = "CustomSchemaGeneration"

	model.Parent = Workspace

end

```

Generatie Voorwaarden op een Afbeelding

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Referentieafbeelding gebruikt om de generatie te conditioneren. Vervang `0` door de asset

-- ID van je eigen geüploade afbeelding.

local imageAssetId = 0

local inputs = {

	Image = Content.fromAssetId(imageAssetId),

	TextPrompt = "een low-poly schatkist",

}

-- Produceer een enkele-mesh output

local schema = {

	PredefinedSchema = "Body1",

}

-- Maak de aanroep om het model te genereren

local success, model, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Veranker alle onderdelen zodat de meshes niet uit elkaar vallen

	for _, descendant in model:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Geef het model een naam en voeg het toe aan de workspace

	model.Name = "AfbeeldingGeconditioneerdeGeneratie"

	model.Parent = Workspace

end

```

Feedback geven

---

LoadGeneratedMeshAsync

Opbrengst

Mogelijkheden: DynamicGeneration

GenerationService:LoadGeneratedMeshAsync (generationId :[string](/docs/nl-nl/luau/strings) ) :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

Parameters

|

generationId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

Feedback geven

---

SegmentMeshAsync

Opbrengst

Mogelijkheden: DynamicGeneration

GenerationService:SegmentMeshAsync (

meshPart :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , schema :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

meshPart :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

 |
|

schema :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

Ga naar

▼

GenerationService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GenerateMeshAsync()](#GenerateMeshAsync)

[GenerateModelAsync()](#GenerateModelAsync)

[LoadGeneratedMeshAsync()](#LoadGeneratedMeshAsync)

[SegmentMeshAsync()](#SegmentMeshAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
