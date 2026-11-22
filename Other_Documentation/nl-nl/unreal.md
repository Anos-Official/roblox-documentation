<!-- Source: https://create.roblox.com/docs/nl-nl/unreal -->

Roblox voor Unreal-ontwikkelaars | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. [Get started for experienced creators](/docs/nl-nl/onboarding)

# Roblox voor Unreal-ontwikkelaars

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze pagina bevat informatie om ervaren Unreal Engine-ontwikkelaars te helpen beginnen met Roblox, inclusief basisoriëntatie, een conceptuele vergelijking en belangrijke verschillen tussen de twee platforms.

## [Oriëntatie](#oriëntatie)[](#oriëntatie)

 ![De gebruikersinterface van de Unreal Editor met markeringen om de verschillende vensters en panelen te tonen.](https://prod.docsiteassets.roblox.com/assets/engine-comparisons/Unreal-Editor-Layout.png)  ![De gebruikersinterface van Roblox Studio met markeringen om de verschillende vensters en panelen te tonen.](https://prod.docsiteassets.roblox.com/assets/studio/general/Studio-Layout.png)

De Outliner  van Unreal en de [Explorer](/docs/nl-nl/studio/explorer)  van Roblox Studio zijn de primaire vensters voor het organiseren van elementen in 3D-ruimtes. Beide tonen een hiërarchie van objecten en mappen. De Outliner  heeft echter een plattere, minder gedefinieerde structuur en toont alleen Actors . Het Explorer -venster heeft een diep geneste, strikte structuur en toont alle objecten als onderdeel van de hiërarchie, zelfs objecten die als componenten in Unreal zouden worden beschouwd.

De [Asset Manager](/docs/nl-nl/projects/assets/manager)  van Roblox Studio en de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  overlappen met de Content Browser  van Unreal. De Asset Manager  stelt je in staat om alle assets binnen je game te beheren, terwijl de Toolbox  je toegang geeft tot alle assets die je hebt gepubliceerd. De Toolbox  stelt je ook in staat om de [Creator Store](/docs/nl-nl/production/creator-store)  te doorzoeken naar assets van Roblox of de community, vergelijkbaar met de Marketplace  van Unreal Engine, maar toegankelijk direct vanuit de gebruikersinterface van Studio.

## [Filosofische verschillen](#filosofische-verschillen)[](#filosofische-verschillen)

Roblox is een "simulatie-engine" in plaats van een traditionele game-engine. Unreal Actors  en Roblox [Parts](/docs/nl-nl/reference/engine/classes/Part)  dienen beide als fundamentele bouwstenen, maar in de praktijk zijn de twee behoorlijk verschillend:

-

Representatie : Actors  in Unreal zijn een hoger niveau concept voor elk object in een level, terwijl [Parts](/docs/nl-nl/reference/engine/classes/Part)  in Roblox zijn ontworpen om fysieke objecten zoals houten blokken en plastic bollen te vertegenwoordigen.

-

Fysica : Om fysicasimulaties in Unreal uit te voeren, schakel je fysica in binnen bepaalde componenten (zoals de StaticMeshComponent ) of door componenten aan Actors  toe te voegen, zoals fysica-beperkingen. In Roblox zijn fysica ingebouwd in het [Parts](/docs/nl-nl/reference/engine/classes/Part)  datatype; de engine beheert interacties automatisch.

Je kunt het verschil onmiddellijk zien als je een Actor  en een [Part](/docs/nl-nl/reference/engine/classes/Part)  maakt. De Actor  heeft weinig meer dan een locatie, rotatie en schaal. De [Part](/docs/nl-nl/reference/engine/classes/Part)  heeft diezelfde informatie, plus een materiaal en kleur, waarden voor reflectie en transparantie, massa en vorm, en nog veel meer. De twee beginnen pas vergelijkbare eigenschappen te delen wanneer je een StaticMeshActor  in Unreal vergelijkt met een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  in Roblox.

![Een voorbeeld van een Unreal actor in het Details-paneel.](https://prod.docsiteassets.roblox.com/assets/engine-comparisons/Unreal-Details-Panel.png) Details-paneel van de Unreal Editor

![Een voorbeeld van een Roblox part in het Properties-venster.](https://prod.docsiteassets.roblox.com/assets/engine-comparisons/Studio-Properties.png) Properties-venster van Roblox Studio

Een nuttige vergelijking is de Unreal Actor  met de Roblox [Model](/docs/nl-nl/reference/engine/classes/Model) . Modellen fungeren als een container voor een verzameling onderling verbonden delen op dezelfde manier als Actors  in Unreal containers zijn voor componenten. Je specificeert een van de delen van het model als zijn [primaire deel](/docs/nl-nl/parts/models#stel-een-primair-onderdeel-in)  om het draaipunt te definiëren. Modellen bevatten ook scripts, animaties, geluidseffecten, prompts, beperkingen, deeltjesemitteren en meer.

Bijvoorbeeld, een Unreal Actor  kan een NiagaraComponent  hebben die verschillende emitteren gebruikt om het gewenste visuele effect te bereiken, een mesh voor de vorm, een fysica-beperking om veerkracht toe te voegen, en een script voor spelersinteractiviteit. In de Outliner zie je een enkele Actor  genaamd SpringyFireball .

In Roblox kan een vergelijkbaar SpringyFireball -model in het Explorer -venster er ongeveer zo uitzien:

```

Model

|- ParticleEmitter

|- MeshPart

|- SpringConstraint

|- ClickDetector

|  |- Script

```

De filosofie van Roblox om fysica standaard in te schakelen, strekt zich uit tot het proces van het bouwen van 3D-modellen. In Roblox is het lassen van meerdere delen tot een [assemblage](/docs/nl-nl/physics/assemblies)  een uitstekende manier om snel dingen te bouwen, omdat Roblox de gelaste delen als één rigide lichaam beschouwt. Deze aanpak is niet praktisch in Unreal.

In plaats van standaard metrische eenheden voor lengte en massa te gebruiken, gebruikt Roblox hypothetische eenheden genaamd studs en Roblox Mass Units (RMU's). Voor benaderende metrische conversies en aanbevelingen rond gebruik, zie [Eenheden](/docs/nl-nl/physics/units) .

## [Locatie is belangrijk](#locatie-is-belangrijk)[](#locatie-is-belangrijk)

Roblox-games zijn standaard multiplayer, dus Roblox Studio bevat veel verschillende opslaglocaties met specifieke gedragingen. Voor meer informatie, zie [client-server runtime](/docs/nl-nl/projects/client-server)  en [objectorganisatie](/docs/nl-nl/projects/data-model#object-organization) .

| Location | | Description |
| --- | --- |
| [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) | | Vertegenwoordigt de 3D-wereld van het spel. Kan serverscripts uitvoeren die direct aan objecten zijn gekoppeld en hun gedrag controleren. |
| [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) | | Bevat objecten die als eerste naar de client worden gerepliceerd. Deze locatie is ideaal voor de absoluut minimale set objecten en clientscripts die nodig zijn om een laadscherm weer te geven. |
| [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) | | Bevat objecten die naar zowel de client als de server worden gerepliceerd. Deze locatie is ideaal voor [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  van [Client](/docs/nl-nl/reference/engine/enums/RunContext) , client [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) , en [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  die je op zowel de server als de client wilt gebruiken. [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  worden niet vanuit deze locatie uitgevoerd. |
| [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) | | Bevat serverscripts. Deze locatie is ideaal voor scripts die toegang nodig hebben tot server-side functionaliteit of objecten, zoals spel-logica en cloudopslag. |
| [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) | | Bevat server-side objecten. Deze locatie is ideaal voor grote objecten die niet onmiddellijk naar clients hoeven te worden gerepliceerd wanneer ze een spel joinen. Scripts worden niet vanuit deze locatie uitgevoerd, maar je kunt hier server-side [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  opslaan. |
| [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  ⟩ [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) | | Bevat [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  die worden uitgevoerd wanneer het personage spawnt. |
| [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  ⟩ [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) | | Bevat [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  die worden uitgevoerd wanneer de speler het spel joinet. |
| [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) | | Bevat GUI-elementen die de client weergeeft wanneer het spel wordt geladen. [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  kunnen vanuit deze locatie worden uitgevoerd. |
| [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack) | | Bevat over het algemeen alleen [Tools](/docs/nl-nl/reference/engine/classes/Tool) , maar kan ook [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  bevatten voor het instellen van spelersrugzakken. |

## [Scripting](#scripting)[](#scripting)

Roblox-games ondersteunen drie verschillende soorten Luau-scripts:

-

Client-scripts

Deze scripts worden op de client uitgevoerd, en de server heeft geen zicht op hun gedrag. Om legacy-redenen kunnen deze scripts de vorm aannemen van [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  of [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  waarde van [Client](/docs/nl-nl/reference/engine/enums/RunContext) . Client-scripts bevinden zich meestal in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  of [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) .

-

Server-scripts

Deze scripts worden op de server uitgevoerd, en de client heeft geen zicht op hun gedrag. Server-scripts hebben een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  waarde van [Server](/docs/nl-nl/reference/engine/enums/RunContext)  en bevinden zich meestal in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) , waarvan de inhoud niet naar de client wordt gerepliceerd.

-

Module-scripts

Deze scripts zijn herbruikbare stukjes code die precies één waarde retourneren, meestal een functie of tabel (of een tabel van functies). In plaats van code te dupliceren in client- en server-scripts, gebruik module-scripts om code en gegevens tussen de twee te delen. Module-scripts bevinden zich vaak in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , maar kunnen ook elders worden geplaatst als je code wilt delen tussen scripts aan dezelfde kant van de client-servergrens.

Unreal heeft niet het concept van verschillende scripttypes. Als je ervoor kiest om een multiplayer-game te maken, schrijf je extra code om de game-status tussen de server en de clients te synchroniseren.

In Unreal is veel van de functionaliteit van de engine beschikbaar door ingebouwde klassen zoals UObject , ACharacters , ULevel  en UWorld  in C++ of Blueprint uit te breiden. Unreal ondersteunt aangepaste evenementen, maar veel klassen bevatten evenementen die de engine automatisch oproept als onderdeel van de natuurlijke levenscyclus van het level.

In vergelijking met het "ticking"-systeem van Unreal zijn Roblox-scripts veel meer gebeurtenisgestuurd. Je krijgt toegang tot vergelijkbare enginefunctionaliteit door je in te schrijven voor services en te luisteren naar updates.

### [C++ en Luau](#c-en-luau)[](#c-en-luau)

Voor scripting gebruikt Unreal C++. Roblox gebruikt [Luau](/docs/nl-nl/luau) , een scripttaal afgeleid van [Lua 5.1](https://www.lua.org/manual/5.1/) .

In vergelijking met Luau heeft C++ een algemeen prestatievoordeel, wat relevant kan zijn of niet voor de soorten games die je wilt bouwen. Luau is geleidelijk getypeerd en heeft een minder uitgebreide syntaxis. In grotere projecten kan geleidelijk typen echter categorieën van bugs introduceren die sterk getypeerde talen zoals C++ vermijden, dus overweeg om [strikte typecontrole](/docs/nl-nl/luau/type-checking#inferentiemodi)  in Roblox-scripts in te schakelen.

Unreal bevat ook een visueel scripttingssysteem genaamd Blueprints . Roblox heeft derde-partij plugins die vergelijkbare functionaliteit bieden, maar geen vergelijkbaar systeem ingebouwd.

### [Luau codevoorbeeld](#luau-codevoorbeeld)[](#luau-codevoorbeeld)

De volgende Luau-codevoorbeeld demonstreert hoe je, nadat een speler een hengel heeft uitgerust, kunt luisteren naar gebruikersinvoer (in dit geval de E -toets) en aanvullende functies kunt aanroepen:

```

local ContextActionService = game:GetService("ContextActionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Verkrijg een module-script uit ReplicatedStorage dat een enkele functie retourneert

local performSomeAction = require(ReplicatedStorage.performSomeAction)

-- Gaat ervan uit dat dit script een kind is van de hengel

local fishingPole = script.Parent

local ACTION_CAST = "Cast"

-- Controleer of de toets ingedrukt is, en roep dan een andere functie aan

local function castLine(_actionName, inputState, _inputObject)

	if inputState == Enum.UserInputState.Begin then

		performSomeAction()

	end

end

-- Schakel de actie alleen in wanneer de speler de hengel uitrust

fishingPole.Equipped:Connect(function()

	ContextActionService:BindAction(ACTION_CAST, castLine, true, Enum.KeyCode.E)

end)

-- Deactiveer de actie wanneer de speler de hengel uittrekt

fishingPole.Unequipped:Connect(function()

	ContextActionService:UnbindAction(ACTION_CAST)

end)

```

Het Roblox-script kan relatief beknopt zijn omdat Roblox veel ingebouwde aannames heeft: een [Player](/docs/nl-nl/reference/engine/classes/Player)  met een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -personage dat verbonden is met de server en [Tools](/docs/nl-nl/reference/engine/classes/Tool)  kan uitrusten. Deze aannames bestaan niet in Unreal, dus de implementatie zou heel anders zijn.

## [Assets](#assets)[](#assets)

Zowel Unreal als Roblox ondersteunen het importeren van aangepaste meshes en modellen in .fbx -formaat. Bepaalde soorten assets kunnen specifieke configuraties en exportinstellingen van je derde-partij modelleringsoftware vereisen. Voor meer informatie, zie de volgende pagina's:

-

[Importer](/docs/nl-nl/studio/importer)

-

[3D-modelleringsspecificaties](/docs/nl-nl/art/modeling/specifications)

-

[Blender en Maya exportvereisten](/docs/nl-nl/art/modeling/export-requirements)

In Unreal worden assets geïmporteerd in je Content -directory, zichtbaar in de Content Browser . In Roblox worden assets geïmporteerd in je Workspace en in de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of [Asset Manager](/docs/nl-nl/projects/assets/manager) .

Roblox biedt ook een open-source [Blender-plugin](/docs/nl-nl/art/modeling/roblox-blender-plugin)  om het importproces te stroomlijnen, vergelijkbaar met de Send to Unreal -functie van Blender Tools.

## [Transforms](#transforms)[](#transforms)

Unreal Engine 's transformaties en Roblox's [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame)  dienen vergelijkbare doelen bij het weergeven van 3D-transformaties van objecten:

-

Zowel transformaties als [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame)  vertegenwoordigen de positie en rotatie van een object in 3D-ruimte. Transformaties omvatten schaal, terwijl Roblox een [BasePart.Size](/docs/nl-nl/reference/engine/classes/BasePart#Size) -eigenschap gebruikt die geen deel uitmaakt van de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) .

-

Beide ondersteunen vermenigvuldiging voor complexe transformaties en hebben ingebouwde methoden voor andere manipulaties.

## [Samenwerking](#samenwerking)[](#samenwerking)

In Unreal werk je samen met versiebeheersystemen zoals Perforce of SVN, meestal via de ingebouwde gebruikersinterface van Unreal. Deze versiebeheersystemen gebruiken het gecentraliseerde "checkout"-model dat bestanden vergrendelt terwijl één persoon eraan werkt.

Roblox-bestanden leven in de cloud (hoewel je kopieën kunt exporteren), dus Roblox Studio biedt ingebouwde samenwerkingsworkflows voor gelijktijdige bewerking, groepsbeheer, machtigingen, scriptontwerp en meer. Zie [Samenwerking](/docs/nl-nl/projects/collaboration) .

Cloud-synchronisatie biedt verdere voordelen met [pakketten](/docs/nl-nl/projects/assets/packages) , de Roblox-equivalent van Unreal Blueprint-klassen. Het converteren van een asset of asset-hiërarchie naar een pakket helpt met lokale herbruikbaarheid, maar ook met samenwerking. Wanneer jij of je samenwerkers een nieuwe versie van een pakket publiceren, kun je bestaande instanties van dat pakket binnen een game snel bijwerken of ze automatisch laten bijwerken.

## [Plugins](#plugins)[](#plugins)

Vergelijkbaar met Unreal ondersteunt Roblox Studio [plugins](/docs/nl-nl/studio/plugins) , die verschillende aspecten van het ontwikkelingsproces kunnen vereenvoudigen of je extra controle kunnen geven. Plugins zijn beschikbaar in de [Creator Store](/docs/nl-nl/production/creator-store) , net als assets, veel gratis.

## [Woordenlijst](#woordenlijst)[](#woordenlijst)

| Unreal | | Roblox | | Opmerkingen |
| Level | | [Plaats](/docs/nl-nl/projects#plaatsen) | |  |
| Actor | | [Part](/docs/nl-nl/reference/engine/classes/Part)  of [Model](/docs/nl-nl/reference/engine/classes/Model) | | Zie [Filosofische verschillen](#filosofische-verschillen) . |
| Blueprint Class | | [Pakket](/docs/nl-nl/projects/assets/packages) | |  |
| Transform | | [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) | | [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  bevat geen schaalinformatie. Zie [Transforms](#transforms) . |
| Outliner | | [Explorer](/docs/nl-nl/studio/explorer) | |  |
| Details paneel | | [Properties](/docs/nl-nl/studio/properties) | |  |
| Level Viewport | | [3D viewport](/docs/nl-nl/studio/overview#3d-viewport) | |  |
| Content Browser | | [Asset Manager](/docs/nl-nl/projects/assets/manager)  of [Toolbox](/docs/nl-nl/projects/assets/toolbox) | |  |
| Landscape Mode | | [Terrain Editor](/docs/nl-nl/studio/terrain-editor) | |  |
| PlayerStart | | [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation) | |  |
| Output Log | | [Output](/docs/nl-nl/studio/output) | |  |
| Marketplace | | [Creator Store](/docs/nl-nl/production/creator-store) | |  |
| Menu bar | | [Toolbar](/docs/nl-nl/studio/overview#werkbalk-en-mezzanine) | |  |
| Plugin | | [Plugin](/docs/nl-nl/studio/plugins) | |  |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
