<!-- Source: https://create.roblox.com/docs/nl-nl/parts/solid-modeling -->

Solide modellering | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Delen](/docs/nl-nl/parts)

# Solide modellering

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Solide modellering  is het proces van het samenvoegen van [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  op unieke manieren om complexere vormen te vormen. Dit omvat de booleaanse operaties [unite](#unite) , [snijden](#snijden)  en [aftrekken](#aftrekken)  die algemeen bekend staan als Constructive Solid Geometry (CSG). Je kunt solide modellering uitvoeren in Studio, [plugins](/docs/nl-nl/studio/plugins) , en [in‑game](#in-game-solide-modellering)  op zowel de server als de client.

Naast booleaanse CSG ondersteunt solide modellering ook meshes, zolang ze [waterdicht](#waterdichte-geometrie)  zijn, en operaties zoals sweep  en fragment  die jou en je spelers in staat stellen om geometrie te snijden, te knippen en te vergruizen voor unieke gameplay-interacties.

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/SweepPart-Crinkle.jpg)[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  gemaakt met [SweepPartAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SweepPartAsync)

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Bridge.jpg)[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  gebroken met [FragmentAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#FragmentAsync)

Het uitvoeren van CSG op meshes en het gebruik van de sweep- en fragmentoperaties is alleen beschikbaar door de bètakenmerk in te schakelen via Bestand  ⟩ Bèta-functies  ⟩ Solide Modellering Op Meshes .

## [Waterdichte geometrie](#waterdichte-geometrie)[](#waterdichte-geometrie)

Solide modellering operaties kunnen alleen werken met waterdichte  geometrie. In technische termen betekent een mesh die waterdicht is dat deze gesloten, manifold en niet-zelfsnijdend is. Deze termen hebben strikte definities, maar hier zijn enkele eenvoudige regels:

-

Elke vlak  moet een "binnenkant" en een "buitenrand" hebben. Deze worden bepaald door de windingvolgorde van het vlak, wat de volgorde van de drie hoekpunten is.

-

Elke rand  moet precies door twee driehoeken worden gedeeld. Dit betekent dat er geen gaten in de mesh kunnen zijn, omdat de randen rond de rand van een gat slechts één driehoek zouden hebben.

-

Vlakken mogen niet door andere vlakken heen gaan.

-

Aangrenzende driehoeken moeten het eens zijn over welke kant de "buitenrand" is.

-

Elke hoek  moet precies één fan van aangrenzende driehoeken hebben.

Elk van de volgende voorbeelden is niet-waterdicht  om de aangegeven reden:

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Not-Watertight-A.png)

Mesh is niet gesloten

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Not-Watertight-B.png)

Zelfsnijdend

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Not-Watertight-C.png)

Delen een rand

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Not-Watertight-D.png)

Delen een hoek

Herstellen van niet-waterdichte meshes

Het solide modellering systeem kan automatisch specifieke kleine problemen met een mesh herstellen, maar over het algemeen zullen API-aanroepen mislukken als de mesh niet waterdicht is. Er is geen one-size-fits-all manier om een bestaande niet-waterdichte mesh te herstellen, maar er zijn verschillende Blender-plugins die kunnen helpen, zoals [3D Print Toolbox](https://extensions.blender.org/add-ons/print3d-toolbox)  en [Mesh Repair Tools](https://extensions.blender.org/add-ons/mesh-repair-tools) . Als een andere optie heeft [Meshlab](https://www.meshlab.net)  ook zeer nuttige tools ingebouwd om te proberen de mesh manifold te maken, wat de belangrijkste vereiste is voor een mesh die waterdicht is.

Een manier om te zien dat een mesh extreem moeilijk waterdicht te maken is, is door deze in Studio vanuit alle hoeken te bekijken en vervolgens de [MeshPart.DoubleSided](/docs/nl-nl/reference/engine/classes/MeshPart#DoubleSided)  eigenschap van de mesh in te schakelen en uit te schakelen. Als je enig verschil kunt zien, dan is de mesh gewoon een schaal en zullen de hierboven genoemde tools niet werken omdat ze niet kunnen raden welke ruimte binnen versus buiten de mesh is. Als je echter alleen een dunne mesh wilt en het niet belangrijk is om de afmetingen van de mesh exact hetzelfde te houden, kun je de [Solidify modifier](https://docs.blender.org/manual/en/latest/modeling/modifiers/generate/solidify.html)  van Blender gebruiken om de schaal iets te verdikken tot een waterdichte mesh.

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/DoubleSided-Diff-1.png)[DoubleSided](/docs/nl-nl/reference/engine/classes/MeshPart#DoubleSided)  = false

![](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/DoubleSided-Diff-2.png)[DoubleSided](/docs/nl-nl/reference/engine/classes/MeshPart#DoubleSided)  = true

## [Solide modellering in Studio](#solide-modellering-in-studio)[](#solide-modellering-in-studio)

Je kunt drie basis booleaanse operaties uitvoeren met behulp van vier tools binnen de werkbalk van het Model  tabblad.

 ![Solide modellering tools gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Solid-Modeling.png)

| Tool | | Sneltoets | | Beschrijving |
| --- | --- |
| [Unite](#unite) | | Shift Ctrl G  (Windows)
Shift ⌘ G  (Mac) | | Voeg twee of meer onderdelen samen tot een enkele solide unie. |
| [Snijden](#snijden) | | Shift Ctrl I  (Windows)
Shift ⌘ I  (Mac) | | Snijd overlappende onderdelen in een enkele solide snede. |
| [Scheiden](#scheiden) | | Shift Ctrl U  (Windows)
Shift ⌘ U  (Mac) | | Scheid de unie of snede terug in zijn individuele onderdelen. |
| [Aftrekken](#aftrekken) | | Shift Ctrl N  (Windows)
Shift ⌘ N  (Mac) | | Aftrekken van onderdelen, nuttig voor het maken van gaten en indeukingen. |

### [Unite](#unite)[](#unite)

De Unite  tool voegt twee of meer onderdelen samen tot een enkele solide [UnionOperation](/docs/nl-nl/reference/engine/classes/UnionOperation) .

![Een blok en een cilinder.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Union-Before.png) Individuele onderdelen

![Een blok en een cilinder samengevoegd tot één object.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Union-After.png) Unie resultaat

Om onderdelen samen te voegen tot een unie:

1.

Selecteer alle onderdelen die je wilt samenvoegen.

2.

Klik op de Unite  knop. Alle onderdelen worden samengevoegd tot één solide [UnionOperation](/docs/nl-nl/reference/engine/classes/UnionOperation)  met de naam Unie .

### [Snijden](#snijden)[](#snijden)

De Snijden  tool snijdt overlappende onderdelen in een enkele solide [IntersectOperation](/docs/nl-nl/reference/engine/classes/IntersectOperation) .

![Een blok en een cilinder.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Intersect-Before.png) Individuele onderdelen

![Een blok en een cilinder samengevoegd tot één object.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Intersect-After.png) Snede resultaat

Om overlappende onderdelen samen te snijden:

1.

Selecteer alle onderdelen die je wilt snijden.

2.

Klik op de Snijden  knop. Alle onderdelen worden samengevoegd tot één solide [IntersectOperation](/docs/nl-nl/reference/engine/classes/IntersectOperation)  met de naam Snede .

### [Aftrekken](#aftrekken)[](#aftrekken)

De Aftrekken  tool trekt een onderdeel af zodat wanneer het [samengevoegd wordt met een ander onderdeel](#unite) , de vorm van het afgetrokken onderdeel afgetrokken  wordt van het andere onderdeel.

![Een blok en een cilinder.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Subtract-Before.png) Blok en afgetrokken cilinder

![Een blok en een cilinder samengevoegd tot één object.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Subtract-After.png) Aftrek resultaat

Om een onderdeel van andere overlappende onderdelen af te trekken:

1.

Selecteer het onderdeel dat je wilt aftrekken van andere onderdelen.

2.

Klik op Aftrekken . Het onderdeel wordt doorschijnend met een rode tint om zijn status aan te geven.

3.

Selecteer zowel het afgetrokken onderdeel als de onderdelen waarvan je het wilt aftrekken.

4.

Klik op Unite . Het afgetrokken onderdeel wordt uit de inbegrepen overlappende onderdelen gesneden.

### [Scheiden](#scheiden)[](#scheiden)

De Scheiden  tool scheidt een [UnionOperation](/docs/nl-nl/reference/engine/classes/UnionOperation)  terug in zijn individuele onderdelen, wat in wezen dient als een "ongedaan maken" tool voor unies en sneden.

Om een unie of snede terug te scheiden in individuele onderdelen:

1.

Selecteer de unie of snede.

2.

Klik op Scheiden . De onderdelen scheiden terug in hun oorspronkelijke vorm.

## [In-game solide modellering](#in-game-solide-modellering)[](#in-game-solide-modellering)

Je kunt ook solide modellering operaties uitvoeren terwijl een spel draait of vanuit een [plugin](/docs/nl-nl/studio/plugins)  via [GeometryService](/docs/nl-nl/reference/engine/classes/GeometryService)  methoden.

In-game solide modellering operaties zijn asynchroon, wat betekent dat ze de prestaties kunnen beïnvloeden. Voor de beste resultaten moet je geen grote reeks aanroepen zoals [UnionAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#UnionAsync)  snel achter elkaar uitvoeren.

### [Kernoperaties](#kernoperaties)[](#kernoperaties)

Net als de ingebouwde operationele tools van Studio, kun je [GeometryService](/docs/nl-nl/reference/engine/classes/GeometryService)  methoden gebruiken zoals [UnionAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#UnionAsync) , [IntersectAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#IntersectAsync) , en [SubtractAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SubtractAsync)  om basis booleaanse operaties uit te voeren. Bijvoorbeeld, het volgende script gebruikt [SubtractAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SubtractAsync)  om het volume van het ene onderdeel van het andere af te trekken.

Aftrekken van één onderdeel van een ander

```

local GeometryService = game:GetService("GeometryService")

local mainPart = Instance.new("Part")

local otherPart = Instance.new("Part")

otherPart.Position = Vector3.new(1, 0.5, 1)

local success, newParts = pcall(function()

	return GeometryService:SubtractAsync(mainPart, {otherPart})

end)

if success and newParts then

	for _, newPart in pairs(newParts) do

		newPart.Parent = workspace

	end

end

```

Om verder te demonstreren, het volgende codevoorbeeld combineert de geometrie van mainPart  en de onderdelen in de otherParts  array, en vernietigt vervolgens de oorspronkelijke onderdelen die betrokken zijn bij de operatie. Je kunt de aanroep naar [UnionAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#UnionAsync)  vervangen door [IntersectAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#IntersectAsync)  of [SubtractAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SubtractAsync)  om de andere booleaanse operaties uit te voeren.

Combineer geometrie van meerdere onderdelen

```

local GeometryService = game:GetService("GeometryService")

local mainPart = workspace.BlueBlock

local otherParts = { workspace.PurpleCylinder }

local options = {

	CollisionFidelity = Enum.CollisionFidelity.Default,

	RenderFidelity = Enum.RenderFidelity.Automatic,

	SplitApart = false

}

local success, newParts = pcall(function()

	return GeometryService:UnionAsync(mainPart, otherParts, options)

end)

if success and newParts then

	-- Loop door de resulterende onderdelen om te herpositioneren

	for _, newPart in pairs(newParts) do

		newPart.Parent = mainPart.Parent

		newPart.CFrame = mainPart.CFrame

		newPart.Anchored = mainPart.Anchored

	end

	-- Vernietig de oorspronkelijke onderdelen

	mainPart.Parent = nil

	mainPart:Destroy()

	for _, otherPart in pairs(otherParts) do

		otherPart.Parent = nil

		otherPart:Destroy()

	end

end

```

Hoewel er geen engine-niveau methode voor onderdeel aftrekken  is, kun je de rbxNegate  tag binnen een script of [plugin](/docs/nl-nl/studio/plugins)  toevoegen om een aftrekking uit te voeren die gelijk is aan de [Aftrekken](#aftrekken)  werkbalkknop van Studio.

Onderdeel Aftrekken via Script

```

local CollectionService = game:GetService("CollectionService")

CollectionService:AddTag(workspace.Part, "rbxNegate")

```

Migreren van BasePart CSG Functies

In vergelijking met [BasePart:UnionAsync()](/docs/nl-nl/reference/engine/classes/BasePart#UnionAsync) /[BasePart:IntersectAsync()](/docs/nl-nl/reference/engine/classes/BasePart#IntersectAsync) /[BasePart:SubtractAsync()](/docs/nl-nl/reference/engine/classes/BasePart#SubtractAsync)  verschillen de [GeometryService](/docs/nl-nl/reference/engine/classes/GeometryService)  methoden als volgt:

-

De output is een array van instanties in plaats van een enkele instantie.

-

De invoeronderdelen hoeven niet aan de scène te zijn gekoppeld, waardoor achtergrondoperaties mogelijk zijn.

-

Wanneer de SplitApart  optie is ingesteld op true  (standaard), wordt elk afzonderlijk lichaam in zijn eigen [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation) /[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  geretourneerd.

-

Alle geretourneerde onderdelen bevinden zich in de coördinatenruimte van het hoofdonderdeel, zodat hun [PVInstance.Origin](/docs/nl-nl/reference/engine/classes/PVInstance#Origin)  posities hetzelfde zijn als die van het hoofdonderdeel. Dit houdt de vertices van de mesh in dezelfde positie ten opzichte van het object als voor de operatie, maar het betekent ook dat de (0, 0, 0)  van een geretourneerd onderdeel niet noodzakelijkerwijs in het midden van zijn lichaam is.

### [Sweep onderdeel](#sweep-onderdeel)[](#sweep-onderdeel)

Deze workflow is alleen beschikbaar door de functie in te schakelen via Bestand  ⟩ Bèta-functies  ⟩ Solide Modellering Op Meshes .

De [SweepPartAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SweepPartAsync)  methode creëert een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  die de vorm heeft van het invoeronderdeel dat door een gegeven set van [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  posities wordt getrokken. Deze methode kan zeer nuttig zijn voor het uitvoeren van snijden en knippen interacties.

De invoer kan een [Part](/docs/nl-nl/reference/engine/classes/Part) , [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation) , of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  zijn. De vorm van het resultaat wordt gedefinieerd als de unie van de convexe omhulsels van elk aangrenzend paar van [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame) ; als er slechts één [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  wordt opgegeven, is het resultaat een convexe omhulsel van het invoeronderdeel.

Om te demonstreren hoe deze methode werkt, veegt het volgende codevoorbeeld een bal door een set van [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  posities om een spiraal te creëren:

Sweep Onderdeel Langs Spiraal

```

local GeometryService = game:GetService("GeometryService")

local inputPart = Instance.new("Part")

inputPart.Shape = Enum.PartType.Ball

local cframeList = {}

for i = 1, 50 do

	local rotation = CFrame.Angles(0, i * 0.5, 0)

	local position = Vector3.new(0, i * 0.1, -1)

	table.insert(cframeList, rotation * CFrame.new(position))

end

local success, sweptPart = pcall(function()

	return GeometryService:SweepPartAsync(inputPart, cframeList)

end)

if success and sweptPart then

	sweptPart.Parent = workspace

end

```

 ![Een spiraalvorm gecreëerd door een bol te vegen.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/SweepPart-Spring.jpg)

Snijden gameplay met sweep

![Een doorschijnende gebogen vorm afgetrokken van een blok.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/SweepPart-Slice.png)

Dit voorbeeld gebruikt [SweepPartAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SweepPartAsync)  om een gameplayfunctie voor het snijden van een zwaard of laserpistool te bereiken, waarbij de beweging van het zwaard is gebaseerd op de muispositie van de speler. De muisbeweging van de gebruiker wordt vastgelegd als een lijst van [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame) , [SweepPartAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#SweepPartAsync)  bouwt een snede mesh van deze gegevens, en vervolgens wordt de snede mesh afgetrokken van het onderdeel dat werd geraakt.

Om dit voorbeeld in Studio aan de praat te krijgen:

1.

Maak de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  om alle solide modellering operaties uit te voeren.

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local GeometryService = game:GetService("GeometryService")

local DrawCurveEvent = ReplicatedStorage:WaitForChild("DrawCurveEvent")

DrawCurveEvent.OnServerEvent:Connect(function(player, cframeList, hitInstance)

    local blade = Instance.new("Part")

    blade.Size = Vector3.new(0.2, 0.2, 15.0)

    local success, sweptPart = pcall(function()

 	   return GeometryService:SweepPartAsync(blade, cframeList)

    end)

    if success and sweptPart then

 	   -- Visualiseer de sweep

 	   sweptPart.Parent = workspace

 	   sweptPart.Transparency = 0.5

 	   sweptPart.Anchored = true

 	   sweptPart.CanQuery = false

 	   -- Trek de sweep af van de geraakt instantie

 	   local subtractSuccess, newParts = pcall(function()

 		   return GeometryService:SubtractAsync(hitInstance, {sweptPart})

 	   end)

 	   if subtractSuccess and newParts then

 		   for _, newPart in pairs(newParts) do

 			   newPart.Parent = hitInstance.Parent

 			   newPart.Anchored = true

 		   end

 		   hitInstance:Destroy()

 	   end

    end

end)

```

2.

Maak de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  om gebruikersinvoer te verwerken.

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local GeometryService = game:GetService("GeometryService")

local DrawCurveEvent = ReplicatedStorage:WaitForChild("DrawCurveEvent")

DrawCurveEvent.OnServerEvent:Connect(function(player, cframeList, hitInstance)

    local blade = Instance.new("Part")

    blade.Size = Vector3.new(0.2, 0.2, 15.0)

    local success, sweptPart = pcall(function()

 	   return GeometryService:SweepPartAsync(blade, cframeList)

    end)

    if success and sweptPart then

 	   -- Visualiseer de sweep

 	   sweptPart.Parent = workspace

 	   sweptPart.Transparency = 0.5

 	   sweptPart.Anchored = true

 	   sweptPart.CanQuery = false

 	   -- Trek de sweep af van de geraakt instantie

 	   local subtractSuccess, newParts = pcall(function()

 		  return GeometryService:SubtractAsync(hitInstance, {sweptPart})

 	   end)

 	   if subtractSuccess and newParts then

 		   for _, newPart in pairs(newParts) do

 			   newPart.Parent = hitInstance.Parent

 			   newPart.Anchored = true

 		   end

 		   hitInstance:Destroy()

 	   end

    end

end)

```

3.

Maak een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  genaamd DrawCurveEvent .

### [Fragment](#fragment)[](#fragment)

Deze workflow is alleen beschikbaar door de functie in te schakelen via Bestand  ⟩ Bèta-functies  ⟩ Solide Modellering Op Meshes .

De [FragmentAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#FragmentAsync)  en [GenerateFragmentSites()](/docs/nl-nl/reference/engine/classes/GeometryService#GenerateFragmentSites)  methoden laten je een onderdeel in stukken vergruizen met natuurlijk uitziende vormen. [FragmentAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#FragmentAsync)  gebruikt [voronoi](https://en.wikipedia.org/wiki/Voronoi_diagram)  decompositie om een enkel onderdeel in meerdere [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  instanties te verdelen volgens het patroon van punten dat wordt doorgegeven, terwijl [GenerateFragmentSites()](/docs/nl-nl/reference/engine/classes/GeometryService#GenerateFragmentSites)  een hulpfunctie is die punten genereert die bekend staan als voronoi-sites om door te geven aan [FragmentAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#FragmentAsync) .

Het volgende codevoorbeeld genereert voronoi-sites om een blokonderdeel te fragmenteren:

```

local GeometryService = game:GetService("GeometryService")

local inputPart = Instance.new("Part")

inputPart.Position = Vector3.new(0, 0.7, 20)

local sites = GeometryService:GenerateFragmentSites(inputPart)

local success, fragments = pcall(function()

	return GeometryService:FragmentAsync(inputPart, sites)

end)

if success and fragments then

  for _, item in fragments do

		local instance = item.Instance

		instance.Parent = workspace

	end

end

```

 ![Een blok in stukken vergruist.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Simple-Block.jpg)

Houd er rekening mee dat het aantal kleine stukken dat wordt gemaakt enorm kan zijn. Als je gebruikers de vrijheid geeft om objecten te fragmenteren, heb je een systeem nodig om de stukken op te ruimen, zoals het verwijderen ervan na een bepaalde tijd met behulp van de [Debris](/docs/nl-nl/reference/engine/classes/Debris)  service. Bovendien kun je je eigen lijsten van sites handmatig maken in plaats van [GenerateFragmentSites()](/docs/nl-nl/reference/engine/classes/GeometryService#GenerateFragmentSites)  te gebruiken, maar het kan 50+ regels Luau kosten om goed gedragende punten te genereren.

Gelokaliseerd fragment op een gegeven positie

![Een blok met de hoek in stukken vergruist.](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Localized.jpg)

Het volgende script vergruist een gebied van een onderdeel, gegeven door een positie en straal. De positie kan vaak komen van een fysieke botsing of een raycast van een speler.

Het eerste element van de site-array die [GenerateFragmentSites()](/docs/nl-nl/reference/engine/classes/GeometryService#GenerateFragmentSites)  genereert, zal een interne array zijn van alle sites die buiten de gevraagde straal  liggen. Als je iets specifieks wilt doen met het resterende 'niet-vergruizende gedeelte' van het onderdeel, kun je dat gedeelte vinden door fragments[i].Index == 1  te controleren tijdens het doorlopen van de resultaten van [FragmentAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#FragmentAsync) .

```

local GeometryService = game:GetService("GeometryService")

local function fragmentAtPosition(player, part, contactPoint, radius)

	local allSites = GeometryService:GenerateFragmentSites(part, {Origin = contactPoint, Radius = radius})

	local success, fragments = pcall(function()

		return GeometryService:FragmentAsync(part, allSites)

	end)

	if not success then

		warn("Mislukt om te vergruizen:"..tostring(fragments))

		return

	end

	local decals = {}

	for _,child in pairs(part:GetChildren()) do

		if child:IsA("Decal") or child:IsA("SurfaceAppearance") then

			table.insert(decals,child)

		end

	end

	for i = 1, #fragments do

		local fragment = fragments[i].Instance

		if fragment == nil then

			continue

		end

		for _,d in pairs(decals) do

			local d2 = d:Clone()

			d2.Parent = fragment

		end

		fragment.Anchored = false

		fragment.Parent = part.Parent

		fragment:SetNetworkOwner(player)

	end

	if #fragments ~= 0  then

		part:Destroy()

	end

	return fragments

end

```

Fragment binnen een gebied gedefinieerd door een ander onderdeel

Het volgende script breekt fragmenten van het eerste onderdeel binnen een vorm gedefinieerd door een tweede onderdeel als sjabloon. Alleen voronoi-sites binnen het tweede onderdeel zullen resulteren in afzonderlijke stukken. Alle andere sites zullen hun cellen combineren in één onderdeel.

![Sjabloon in de vorm van het Roblox Studio-logo](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Stencil-Before.jpg) Onderdeel (donkergrijs) en sjabloononderdeel

![Resultaten van een fragment in de vorm van een sjabloon](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Stencil-After.jpg) Fragment script resultaat

```

local GeometryService = game:GetService("GeometryService")

local function fragmentWithinStencil(player, part)

	local overlapParams = OverlapParams.new()

	overlapParams.FilterType = Enum.RaycastFilterType.Include

	overlapParams.FilterDescendantsInstances = {workspace.Stencil}

	overlapParams.RespectCanCollide = false

	local sensor = Instance.new("Part")

	sensor.Size = Vector3.new(0.01, 0.01, 0.01)

	local allSites = GeometryService:GenerateFragmentSites(part, {SiteSpacing = 0.9})

	local fragmentSites = {}

	local mainPartSites = {}

	for _, site in ipairs(allSites) do

		sensor.CFrame = CFrame.new(site)

		local partsFound = workspace:GetPartsInPart(sensor, overlapParams)

		if #partsFound > 0 then

			table.insert(fragmentSites, site)

		else

			table.insert(mainPartSites, site)

		end

	end

	local sortedSites = fragmentSites

	table.insert(sortedSites, mainPartSites)

	workspace.Stencil:Destroy()

	local success, fragments = pcall(function()

		return GeometryService:FragmentAsync(part, sortedSites, {SplitApart = false})

	end)

	if not success then

		warn("Mislukt om te vergruizen:"..tostring(fragments))

		return

	end

	local decals = {}

	for _,child in pairs(part:GetChildren()) do

		if child:IsA("Decal") or child:IsA("SurfaceAppearance") then

			table.insert(decals,child)

		end

	end

	for i = 1, #fragments do

		local fragment = fragments[i].Instance

		if fragment == nil then

			continue

		end

		for _,d in pairs(decals) do

			local d2 = d:Clone()

			d2.Parent = fragment

		end

		fragment.Anchored = false

		fragment.Parent = part.Parent

		fragment:SetNetworkOwner(player)

	end

	if #fragments ~= 0  then

		part:Destroy()

	end

	return fragments

end

```

Fragment meerdere onderdelen en verberg de oorspronkelijke onderdeelgrenzen

Het volgende script is een veel niche gebruiksgeval, maar het demonstreert de kracht van de indexgegevens die worden geretourneerd van [FragmentAsync()](/docs/nl-nl/reference/engine/classes/GeometryService#FragmentAsync) .

Bijvoorbeeld, veel plaatsen bevatten gebouwen die zijn gevormd uit meerdere niet-verenigde blokonderdelen. Als een granaat, kanonskogel of sledgehammer het zou beschadigen, zou je willen dat alle wandonderdelen vergruisd worden. Dit script vergruist alle nabijgelegen onderdelen, en verenigt vervolgens de fragmenten van verschillende onderdelen samen om de naden volledig te verbergen.

Dit omvat meerdere Async()  operaties, dus het is mogelijk niet geschikt voor gebruik in-game als een onmiddellijke reactie op gebruikersinvoer, zoals een sledgehammer-tool.

![Een rij blokken](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Multiple-Before.jpg) Een rij blokken

![Een rij blokken vergruisd](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/Fragment-Multiple-After.jpg) Elk stuk kan afkomstig zijn van meerdere invoeronderdelen

```

local GeometryService = game:GetService("GeometryService")

local function fragmentCrossPart(player, part, contactPoint, radius)

	local allSites = GeometryService:GenerateFragmentSites(part, {Origin = contactPoint, Radius = radius})

	local fragmentsSorted = {}

	for i = 1, #allSites do

		fragmentsSorted[i] = {}

	end

	local partsFound = workspace:GetPartBoundsInRadius(contactPoint, radius)

	for i, part in ipairs(partsFound) do

		local success, fragments = pcall(function()

			return GeometryService:FragmentAsync(part, allSites)

		end)

		if not success then

			warn("Mislukt om te vergruizen:"..tostring(fragments))

			return

		end

		for i = 1, #fragments do

			local fragment = fragments[i].Instance

			local siteIndex = fragments[i].Index

			if fragment == nil or siteIndex == nil then

				continue

			end

			table.insert(fragmentsSorted[siteIndex], fragment)

		end

	end

	for i = 1, #fragmentsSorted do

		local fragmentList = fragmentsSorted[i]

		if #fragmentList == 0 then

			continue

		end

		if #fragmentList == 1 then

			local fragment = fragmentList[1]

			fragment.Anchored = false

			fragment.Parent = part.Parent

			fragment:SetNetworkOwner(player)

			continue

		end

		if i == #allSites then

			for j = 1, #fragmentList do

				local fragment = fragmentList[j]

				fragment.Parent = part.Parent

				fragment.Anchored = true

			end

			continue

		end

		local mainPart = fragmentList[1]

		local otherParts = {}

		for j = 2, #fragmentList do

			table.insert(otherParts, fragmentList[j])

		end

		local success, results = pcall(function()

			return GeometryService:UnionAsync(mainPart, otherParts)

		end)

		if not success then

			warn("Mislukt om te verenigen:"..tostring(results))

			return

		end

		for j = 1, #results do

			results[j].Parent = part.Parent

			results[j].Anchored = false

			results[j]:SetNetworkOwner(player)

		end

	end

	for i, part in ipairs(partsFound) do

		part:Destroy()

	end

end

```

Aanpasbare Luau GenerateFragmentSites()

Het volgende script is een bijna identieke Luau vervanging voor [GenerateFragmentSites()](/docs/nl-nl/reference/engine/classes/GeometryService#GenerateFragmentSites) . Als je vergelijkbaar gedrag wilt als [GenerateFragmentSites()](/docs/nl-nl/reference/engine/classes/GeometryService#GenerateFragmentSites)  maar kleine wijzigingen wilt aanbrengen, kun je dit als uitgangspunt gebruiken.

Het gebruikt een jittered grid van punten en garandeert dat het vergruisde gebied goed gedrag vertoont, in tegenstelling tot volledig willekeurige punten.

```

local function generateFragmentSites(part: BasePart, siteSpacing: number?, origin: Vector3?, radius: number?): {Vector3}

	local RANDOMNESS_MULTIPLIER = 1.0 -- Gebruik dit om de hoeveelheid jitter aan te passen

	if (origin and not radius) or (radius and not origin) then

		warn("Ofwel moeten zowel oorsprong als straal worden opgegeven, of geen van beide.")

		return {}

	end

	local isLocalized = (radius ~= nil) -- isLocalized betekent niet het hele onderdeel vergruizen, alleen een sectie.

	local partCFrame = part.ExtentsCFrame

	local gridDimensions: Vector3

	local localGridCenter: Vector3

	local spacing

	if siteSpacing then

		spacing = siteSpacing

	elseif isLocalized then

		spacing = radius * 0.5

	else

		local partSize = part.Size

		local volume = partSize.X * partSize.Y * partSize.Z

		spacing = (volume / 5) ^ (1/3)

	end

	if isLocalized then

		local localOrigin = partCFrame:PointToObjectSpace(origin)

		local gridSize = math.ceil(radius * 2 / spacing) + 3

		gridDimensions = Vector3.new(gridSize, gridSize, gridSize)

		localGridCenter = localOrigin

	else

		local partSize: Vector3 = part.Size

		local xCount = math.ceil(partSize.X / spacing)

		local yCount = math.ceil(partSize.Y / spacing)

		local zCount = math.ceil(partSize.Z / spacing)

		gridDimensions = Vector3.new(xCount, yCount, zCount)

		localGridCenter = Vector3.zero

	end

	local totalGridSize = gridDimensions * spacing

	local halfCell = Vector3.new(spacing, spacing, spacing) * 0.5

	local localStartOffset = localGridCenter - (totalGridSize * 0.5) + halfCell

	local innerJitter = spacing * 0.5 * RANDOMNESS_MULTIPLIER

	local outerJitter = math.min(spacing * 0.5 * 0.866, innerJitter)

	local sitesFlatList = {}

	for x = 0, gridDimensions.X - 1 do

		for y = 0, gridDimensions.Y - 1 do

			for z = 0, gridDimensions.Z - 1 do

				local isOuterShell =

					x == 0 or x == gridDimensions.X - 1 or

					y == 0 or y == gridDimensions.Y - 1 or

					z == 0 or z == gridDimensions.Z - 1

				local jitterAmount = if (isOuterShell and isLocalized) then outerJitter else innerJitter

				local jitterOffset = Vector3.new(

					(math.random() - 0.5) * 2 * jitterAmount,

					(math.random() - 0.5) * 2 * jitterAmount,

					(math.random() - 0.5) * 2 * jitterAmount

				)

				local offsetInGrid = Vector3.new(x, y, z) * spacing

				table.insert(sitesFlatList, localStartOffset + offsetInGrid + jitterOffset)

			end

		end

	end

	local sitesListFinal = {}

	if isLocalized then

		local mainPartSites = {}

		for _, localSite in ipairs(sitesFlatList) do

			local worldSite = partCFrame * localSite

			local distance = (worldSite - origin).Magnitude

			if distance < radius then

				table.insert(sitesListFinal, worldSite)

			else

				table.insert(mainPartSites, worldSite)

			end

		end

		table.insert(sitesListFinal, 1, mainPartSites)

	else

		for _, localSite in ipairs(sitesFlatList) do

			local worldSite = partCFrame * localSite

			table.insert(sitesListFinal, worldSite)

		end

	end

	return sitesListFinal

end

```

### [Behoud van beperkingen](#behoud-van-beperkingen)[](#behoud-van-beperkingen)

Als een invoeronderdeel beperkingen of bijlagen heeft die je wilt behouden, kun je ze overdragen aan de resulterende onderdelen. Het kan vervelend zijn om uit te zoeken aan welk uitvoeronderdeel een beperking moet worden bevestigd, dus het wordt aanbevolen om [CalculateConstraintsToPreserve()](/docs/nl-nl/reference/engine/classes/GeometryService#CalculateConstraintsToPreserve)  te gebruiken om een tabel met aanbevelingen te genereren die je kunt doorlopen en toepassen.

Om te demonstreren, voert het volgende codevoorbeeld een aftrekoperatie uit, doorloopt het de resulterende onderdelen om ze opnieuw te koppelen en te herpositioneren, en berekent vervolgens een tabel van beperkingen en bijlagen om ofwel te behouden of te laten vallen voordat alle oorspronkelijke onderdelen worden vernietigd.

```

local GeometryService = game:GetService("GeometryService")

local mainPart = workspace.PurpleBlock

local otherParts = { workspace.BlueBlock }

local options = {

	CollisionFidelity = Enum.CollisionFidelity.Default,

	RenderFidelity = Enum.RenderFidelity.Automatic,

	SplitApart = true,

}

local constraintOptions = {

	tolerance = 0.1,

	weldConstraintPreserve = Enum.WeldConstraintPreserve.All,

	dropAttachmentsWithoutConstraints = false,

}

-- Voer aftrekoperatie uit in pcall() omdat het asynchroon is

local success, newParts = pcall(function()

	return GeometryService:SubtractAsync(mainPart, otherParts, options)

end)

if success and newParts then

	-- Loop door de resulterende onderdelen om te herpositioneren

	for _, newPart in pairs(newParts) do

		newPart.Parent = mainPart.Parent

		newPart.CFrame = mainPart.CFrame

		newPart.Anchored = mainPart.Anchored

	end

	-- Bereken beperkingen/bijlagen om ofwel te behouden of te laten vallen

	local recommendedTable = GeometryService:CalculateConstraintsToPreserve(mainPart, newParts, constraintOptions)

	-- Behoud beperkingen/bijlagen op basis van aanbevolen tabel

	for _, item in pairs(recommendedTable) do

		if item.Attachment then

			item.Attachment.Parent = item.AttachmentParent

			if item.Constraint then

				item.Constraint.Parent = item.ConstraintParent

			end

		elseif item.NoCollisionConstraint then

			local newNoCollision = Instance.new("NoCollisionConstraint")

			newNoCollision.Part0 = item.NoCollisionPart0

			newNoCollision.Part1 = item.NoCollisionPart1

			newNoCollision.Parent = item.NoCollisionParent

		elseif item.WeldConstraint then

			local newWeldConstraint = Instance.new("WeldConstraint")

			newWeldConstraint.Part0 = item.WeldConstraintPart0

			newWeldConstraint.Part1 = item.WeldConstraintPart1

			newWeldConstraint.Parent = item.WeldConstraintParent

		end

	end

	-- Vernietig oorspronkelijke onderdelen

	mainPart.Parent = nil

	mainPart:Destroy()

	for _, otherPart in pairs(otherParts) do

		otherPart.Parent = nil

		otherPart:Destroy()

	end

end

```

## [Resultaten van solide modellering](#resultaten-van-solide-modellering)[](#resultaten-van-solide-modellering)

### [Gedragsdetails](#gedragsdetails)[](#gedragsdetails)

In deze sectie verwijst de term "hoofdonderdeel" naar het eerste onderdeel dat je selecteert tijdens solide modellering in Studio, of het eerste argument tijdens solide modellering in-game.

-

De oorspronkelijke onderdelen blijven intact na een succesvolle operatie, en de geretourneerde onderdelen hebben geen vastgestelde [Parent](/docs/nl-nl/reference/engine/classes/Instance#Parent) . In de meeste gevallen is het aan te raden om het/ze geretourneerde onderdeel(en) aan dezelfde plaats als het hoofdonderdeel te koppelen, en vervolgens [Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  de oorspronkelijke onderdelen.

-

Als het hoofdonderdeel beweegt tijdens de berekening van de operatie, kun je de resulterende onderdelen instellen op de bijgewerkte [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  van het hoofdonderdeel, aangezien de geretourneerde onderdelen zich in dezelfde coördinatenruimte als het hoofdonderdeel bevinden.

-

Als een solide modellering operatie zou resulteren in onderdelen met meer dan 20.000 driehoeken, worden ze vereenvoudigd tot 20.000. Als dat niet kan worden gedaan, meestal in een geval met duizenden niet-overlappende componenten, resulteert de operatie in een fout.

-

Er zijn methoden om de mesh-gegevens van een instantie te vervangen, waardoor het gemakkelijker wordt om de geometrie van de operatie te gebruiken terwijl eigenschappen, attributen, tags en kinderen van het hoofdonderdeel behouden blijven, zoals [Attachments](/docs/nl-nl/reference/engine/classes/Attachment) , [Constraints](/docs/nl-nl/reference/engine/classes/Constraint) , [ParticleEmitters](/docs/nl-nl/reference/engine/classes/ParticleEmitter) , lichtobjecten en decals. Deze aanpak omzeilt ook de potentiële "flikkering" van het volledig vervangen van de oorspronkelijke [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  door een andere.

-

Als je deze methode gebruikt met een [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  als het hoofdonderdeel en geen van de andere onderdelen zijn [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) , kun je de geometrie van een andere [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  vervangen via [SubstituteGeometry()](/docs/nl-nl/reference/engine/classes/PartOperation#SubstituteGeometry) .

-

Als het hoofdonderdeel een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is, kun je [MeshPart:ApplyMesh()](/docs/nl-nl/reference/engine/classes/MeshPart#ApplyMesh)  gebruiken.

-

Het is mogelijk om deze methoden aan te roepen op de client, maar met enkele beperkingen. Ten eerste moet dit worden gedaan met objecten die gemaakt  zijn op de client. Ten tweede is er geen replicatie beschikbaar van client naar server.

-

De volgende eigenschappen van het hoofdonderdeel worden toegepast op de resulterende [PartOperations](/docs/nl-nl/reference/engine/classes/PartOperation)  of [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) :

-

Uiterlijk  — [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color) , [BasePart.Material](/docs/nl-nl/reference/engine/classes/BasePart#Material) , [BasePart.MaterialVariant](/docs/nl-nl/reference/engine/classes/BasePart#MaterialVariant) , [BasePart.Reflectance](/docs/nl-nl/reference/engine/classes/BasePart#Reflectance) , [BasePart.Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)

-

Botsing  — [BasePart.AudioCanCollide](/docs/nl-nl/reference/engine/classes/BasePart#AudioCanCollide) , [BasePart.CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)

-

Onderdeel  — [BasePart.Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored) , [BasePart.CurrentPhysicalProperties](/docs/nl-nl/reference/engine/classes/BasePart#CurrentPhysicalProperties) /[BasePart.CustomPhysicalProperties](/docs/nl-nl/reference/engine/classes/BasePart#CustomPhysicalProperties)

### [Kleuren en UV's](#kleuren-en-uvs)[](#kleuren-en-uvs)

De kleuren van het resulterende onderdeel/de onderdelen na solide modellering komen uit twee plaatsen: de vlak kleuren en de kleur van het onderdeel [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color) .

-

Als het resultaat een [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  is, heeft het de [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color)  van het eerste onderdeel dat je in Studio selecteert, maar Studio gebruikt standaard de vlak kleuren om elk vlak dezelfde kleur te houden als het voor de operatie was. Je kunt de [UsePartColor](/docs/nl-nl/reference/engine/classes/PartOperation#UsePartColor)  eigenschap in Studio inschakelen om dit gedrag te overschrijven en het hele resultaat een enkele kleur te maken.

-

Als het resultaat een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is, is zijn [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color)  wit, en de vlak kleuren zullen altijd zichtbaar zijn. Je kunt de tint van het resulterende onderdeel/de onderdelen aanpassen door hun [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color)  te wijzigen, maar het zal worden gemengd (vermenigvuldigd) met de vlak kleuren. Dit tint het resultaat in plaats van de vlak kleuren volledig te overschrijven. Als je volledige controle wilt over de kleur van de output, is het het beste om de invoer wit te maken.

UV's worden ook anders behandeld, afhankelijk van het type resultaat:

-

[PartOperations](/docs/nl-nl/reference/engine/classes/PartOperation)  hebben altijd boxmapped UV's, wat betekent dat elk vlak het materiaal/tekstuur/decal vanuit één richting (één van -x , +x , -y , +y , -z , +z ) erop toegepast krijgt. Dit kan texturen uitrekken.

-

[MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  zijn niet boxmapped. De UV's van de mesh van het hoofdonderdeel worden gebruikt. Aangezien Roblox momenteel geen multi-materiaal ondersteuning heeft, krijgen de UV's van vlakken die afkomstig zijn van de andere onderdelen UV's van (0, 0) . Voor de beste resultaten, zorg ervoor dat pixel (0, 0)  van je textuur een redelijke kleur heeft.

### [Gladde hoek](#gladde-hoek)[](#gladde-hoek)

De [SmoothingAngle](/docs/nl-nl/reference/engine/classes/PartOperation#SmoothingAngle)  eigenschap van een solide gemodelleerd onderdeel maakt de hoeken tussen aangrenzende oppervlakken van dezelfde kleur glad. Een hogere waarde zorgt voor een gladdere uitstraling, terwijl een lagere waarde zorgt voor een ruwere uitstraling met meer scherpe randen.

Hoewel een waarde tussen 30 en 70 graden meestal een goed resultaat oplevert, worden waarden tussen 90 en 180 niet aanbevolen, omdat ze een "schaduweffect" kunnen veroorzaken op unies en sneden met scherpe randen.

![Solide gemodelleerd onderdeel met SmoothingAngle van 0](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/SmoothingAngle-0.png)[SmoothingAngle](/docs/nl-nl/reference/engine/classes/PartOperation#SmoothingAngle)  = 0

![Solide gemodelleerd onderdeel met SmoothingAngle van 45](https://prod.docsiteassets.roblox.com/assets/modeling/solid-modeling/SmoothingAngle-45.png)[SmoothingAngle](/docs/nl-nl/reference/engine/classes/PartOperation#SmoothingAngle)  = 45

Je kunt alleen de [SmoothingAngle](/docs/nl-nl/reference/engine/classes/PartOperation#SmoothingAngle)  eigenschap van een solide gemodelleerd onderdeel in Studio aanpassen, en het is momenteel niet mogelijk om de gladde hoek van een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  aan te passen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
