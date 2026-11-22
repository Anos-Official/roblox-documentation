<!-- Source: https://create.roblox.com/docs/nl-nl/parts/model-generation -->

Modelgeneratie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# Modelgeneratie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Door middel van tekstprompts en vooraf ingestelde schema's kun jij (en spelers in het spel) zowel statische 3D-assets als volledig functionele  modellen genereren, zoals voertuigen die rijden, vliegtuigen die vliegen en wapens die schieten. Deze gids laat zien hoe je [GenerateModelAsync()](/docs/nl-nl/reference/engine/classes/GenerationService#GenerateModelAsync)  kunt gebruiken als onderdeel van een dynamische, door spelers aangedreven creatieve ervaring.

## [Overzicht](#overzicht)[](#overzicht)

[GenerateModelAsync()](/docs/nl-nl/reference/engine/classes/GenerationService#GenerateModelAsync)  maakt de generatie van multi-mesh geometrieën mogelijk met de volgende voordelen:

-

Het opgegeven [schema](#schema-gebaseerde-generatie)  definieert hoe de gegenereerde geometrie in delen zal worden opgesplitst.

-

Elk object dat in het spel wordt gegenereerd, zal worden gerepliceerd en zichtbaar zijn voor alle spelers, waardoor ze samen in real-time kunnen bouwen.

-

Gegenereerde meshes zijn van hogere kwaliteit met betere algehele vormen, silhouetten, meer detail en minder artefacten. Gegenereerde texturen zijn coherenter en gedetailleerder, met minder korreligheid en minder uitgesproken gebakken verlichting.

-

De generatie tijden hebben een lagere latentie, waardoor snellere en responsievere creatie in games mogelijk is.

-

Jij en zelfs spelers tijdens de speeltijd kunnen begrenzingsdozen specificeren om de grootte en verhoudingen van het gegenereerde model voor te stellen.

-

Een optionele maximale driehoekentelling houdt gegenereerde objecten performant voor jouw spel.

## [Schema-gebaseerde generatie](#schema-gebaseerde-generatie)[](#schema-gebaseerde-generatie)

Om gearticuleerde, functionele objecten te creëren, moet de gegenereerde geometrie worden gescheiden in meerdere [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) . Bijvoorbeeld, om een rijdbare auto te maken met wielen die draaien en sturen, zijn er minstens vijf [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  nodig: één voor de carrosserie van de auto en vier voor elk van de wielen van de auto. [GenerateModelAsync()](/docs/nl-nl/reference/engine/classes/GenerationService#GenerateModelAsync)  bereikt dit via een schema  dat de te genereren delen opsomt, zoals weergegeven in de volgende codefragment:

Script in ServerScriptService

```

local GenerationService = game:GetService("GenerationService")

local Workspace = game:GetService("Workspace")

-- Stel de invoer in voor de gegenereerde geometrie

local inputs = {

	TextPrompt = "groene drakenauto met 4 wielen"

}

-- Stel schema in op het vooraf gedefinieerde vijf-modellen auto chassis

local schema = {

	PredefinedSchema = "Car5"

}

-- Maak de aanroep om het model te genereren

local success, result, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Schaal model naar doelgrootte en positioneer het nabij het wereldcentrum

	local targetSize = 16

	local modelSize = result:GetExtentsSize()

	local scaleFactor = targetSize / math.max(modelSize.X, modelSize.Y, modelSize.Z)

	result:ScaleTo(scaleFactor)

	result:PivotTo(CFrame.new(0, result:GetExtentsSize().Y / 2, -40))

	-- Veranker alle delen zodat de meshes niet uit elkaar vallen

	for _, descendant in result:GetDescendants() do

		if descendant:IsA("BasePart") then

			descendant.Anchored = true

		end

	end

	-- Geef het model een naam en maak het een kind van de workspace

	result.Name = "BasicDragonCarGeneration"

	result.Parent = Workspace

else

	warn(result)

end

```

[GenerateModelAsync()](/docs/nl-nl/reference/engine/classes/GenerationService#GenerateModelAsync)  ondersteunt momenteel twee vaste schema's: Car5 , dat een auto met een carrosserie en vier wielen produceert, en Body1 , dat een enkel [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object oplevert.

De volgende afbeelding toont de verwachte output en de constructie zoals deze verschijnt in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie:

![](https://prod.docsiteassets.roblox.com/assets/modeling/model-generation/Green-Dragon-Car.jpg)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-Generation-Hierarchy.png)

## [Herbestembare scripts](#herbestembare-scripts)[](#herbestembare-scripts)

In Roblox omvatten gedragingen  doorgaans de scripts, bijlagen, [beperkingen](/docs/nl-nl/physics#beperkingen)  en andere instantie types die aan statische, getextureerde geometrieën zijn bevestigd om ze functioneel te maken. Aangezien [GenerateModelAsync()](/docs/nl-nl/reference/engine/classes/GenerationService#GenerateModelAsync)  een breed scala aan geometrieën on-the-fly genereert, moeten herbestembare scripts  worden bevestigd om gedragingen automatisch aan te passen aan de verwachte functionaliteit.

Bijvoorbeeld, beschouw een spel waarin spelers hun eigen rijdbare auto's kunnen maken. [GenerateModelAsync()](/docs/nl-nl/reference/engine/classes/GenerationService#GenerateModelAsync)  neemt de spelerprompt en genereert vijf verschillende meshes (carrosserie en vier wielen) via het Car5  [schema](#schema-gebaseerde-generatie) . Vervolgens past een vooraf ingesteld herbestembaar script het rijgedrag aan op de grootte en vorm van het model om ervoor te zorgen dat de auto rijdbaar is en de wielen realistisch draaien.

Om herbestembare scripts te testen:

1.

Download het [Behaviors.rbxm](https://prod.docsiteassets.roblox.com/assets/modeling/model-generation/Behaviors.rbxm)  bestand.

2.

Klik met de rechtermuisknop op [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie van Studio, selecteer Invoegen  ⟩ Importeer Roblox Model , en kies het gedownloade bestand. Het model wordt uitgepakt in verschillende mappen.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-Generation-Behaviors.png)

3.

Kopieer en plak een van de volgende codefragmenten in een server [Script](/docs/nl-nl/reference/engine/classes/Script)  binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) , afhankelijk van het type object dat je wilt genereren.

Auto Vliegtuig

Dit voorbeeld genereert een functionele auto met een rem, nitroboost, audio- en visuele effecten, en een snelheidsmeter op het scherm.

Script in ServerScriptService

```

local GenerationService = game:GetService("GenerationService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

-- Stel de invoer in voor de gegenereerde geometrie

local inputs = {

	TextPrompt = "groene drakenauto met 4 wielen"

}

-- Stel schema in op het vooraf gedefinieerde vijf-modellen auto chassis

local schema = {

	PredefinedSchema = "Car5"

}

-- Maak de aanroep om het model te genereren

local success, result, metadata = pcall(function()

	return GenerationService:GenerateModelAsync(inputs, schema)

end)

if success then

	-- Schaal model naar doelgrootte

	local targetSize = 16

	local modelSize = result:GetExtentsSize()

	local scaleFactor = targetSize / math.max(modelSize.X, modelSize.Y, modelSize.Z)

	result:ScaleTo(scaleFactor)

	-- Laad "makeFunctional" module voor "CarBehavior"

	local makeFunctional = require(ReplicatedStorage.Behaviors.CarBehavior.makeFunctional)

	-- Verwijs naar auto onderdelen via namen die gegarandeerd zijn door het "Car5" schema

	local body = result:FindFirstChild("body")

	local frontLeftWheel = result:FindFirstChild("front left wheel")

	local frontRightWheel = result:FindFirstChild("front right wheel")

	local rearLeftWheel = result:FindFirstChild("rear left wheel")

	local rearRightWheel = result:FindFirstChild("rear right wheel")

	-- Stel gedragsconfiguratieparameters in

	local config = {

		seatPosition = "inside",

		invisibleWhenSeated = false

	}

	-- Bevestig gedrag via het "makeFunctional" script

	local functionalModel = makeFunctional(result, frontLeftWheel, frontRightWheel, rearLeftWheel, rearRightWheel, body, config)

	-- Positioneer het model nabij het wereldcentrum

	functionalModel:PivotTo(CFrame.new(0, functionalModel:GetExtentsSize().Y / 2, -40))

	functionalModel.Name = "BasicDragonCarGeneration"

	functionalModel.Parent = Workspace

else

	warn(result)

end

```

Om andere gegenereerde modellen met herbestembare scripts in het Car5  schema te testen, wijzig de TextPrompt  stringwaarde op regel 7 en speel opnieuw. Ideeën zijn onder andere:

-

"gele sportauto met een spoiler"

-

"paarse vleermuisauto met 4 wielen"

-

"gigantische monstertruck met spikes op het dak"

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
