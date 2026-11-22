<!-- Source: https://create.roblox.com/docs/nl-nl/unity -->

Roblox voor Unity-ontwikkelaars | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. [Get started for experienced creators](/docs/nl-nl/onboarding)

# Roblox voor Unity-ontwikkelaars

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze pagina bevat informatie om ervaren Unity-ontwikkelaars te helpen beginnen met Roblox, inclusief basisoriëntatie, een conceptuele vergelijking en belangrijke verschillen tussen de twee platforms.

## [Oriëntatie](#oriëntatie)[](#oriëntatie)

 ![De gebruikersinterface van Unity met markeringen om de verschillende vensters en panelen te tonen.](https://prod.docsiteassets.roblox.com/assets/engine-comparisons/Unity-Editor-Layout.png)  ![De gebruikersinterface van Roblox Studio met markeringen om de verschillende vensters en panelen te tonen.](https://prod.docsiteassets.roblox.com/assets/studio/general/Studio-Layout.png)

Het Hiërarchie  venster van Unity en de [Explorer](/docs/nl-nl/studio/explorer)  van Roblox Studio zijn de primaire vensters voor het organiseren van elementen in 3D-scènes:

-

Beide stellen je in staat om objecten te beheren en te organiseren (bijvoorbeeld, personages en omgevingsassets).

-

Beide gebruiken een boomstructuur voor de ouder-kindrelaties tussen objecten.

Echter, het Hiërarchie  venster heeft geen vooraf gedefinieerde structuur, terwijl het Explorer  venster een strikte structuur heeft. Het kan helpen om het Explorer  venster te beschouwen als een combinatie van Unity's Hiërarchie  en Project  vensters, met de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  map als het meest herkenbare element.

Evenzo overlappen de [Asset Manager](/docs/nl-nl/projects/assets/manager)  en [Toolbox](/docs/nl-nl/projects/assets/toolbox)  van Roblox Studio met het Unity Project  venster. De Asset Manager  stelt je in staat om alle assets binnen je game te beheren, terwijl de Toolbox  je toegang geeft tot alle assets die je hebt gepubliceerd. De Toolbox  stelt je ook in staat om de [Creator Store](/docs/nl-nl/production/creator-store)  te doorzoeken naar assets van Roblox of de community, vergelijkbaar met de Unity Asset Store .

## [Filosofische verschillen](#filosofische-verschillen)[](#filosofische-verschillen)

Roblox is een "simulatie-engine" in plaats van een traditionele game-engine. Unity GameObjects  en Roblox [Parts](/docs/nl-nl/reference/engine/classes/Part)  dienen beide als de fundamentele bouwstenen voor het creëren van objecten in een 3D-omgeving, maar in de praktijk zijn de twee behoorlijk verschillend:

-

Representatie : GameObjects  in Unity zijn een hoger niveau concept voor elk object in een scène, terwijl Parts  in Roblox zijn ontworpen om fysieke objecten zoals houten blokken en plastic bollen te vertegenwoordigen, in plaats van abstracte geometrie zoals primitieve objecten in Unity.

-

Fysica : Om fysicasimulaties in Unity uit te voeren, koppel je componenten zoals Rigidbody  en Collider  aan een GameObject . In Roblox zijn fysica ingebouwd in het Parts  datatype; de engine beheert interacties automatisch.

Je kunt het verschil onmiddellijk zien als je een GameObject  en een Part  maakt. Het GameObject  heeft niets meer dan een positie, rotatie en schaal. De Part  heeft diezelfde informatie—plus een materiaal en kleur, waarden voor reflectie en transparantie, massa en vorm, en nog veel meer. Een Part  omzetten in iets dat meer lijkt op een leeg GameObject  betekent het verwijderen  van veel ingebouwde eigenschappen. Omgekeerd kun je een GameObject  maken dat veel lijkt op een Part  door MeshFilter , MeshRenderer , Collider  en Rigidbody  componenten eraan toe te voegen.

Vanuit een script perspectief is GameObject  het meest vergelijkbaar met de Roblox [Instance](/docs/nl-nl/reference/engine/classes/Instance) , de basis klasse voor alle andere Roblox klassen, maar omdat je geen objecten van het type Instance  kunt (en kunt) maken, is de vergelijking niet bijzonder praktisch.

Een andere vergelijking is de Unity GameObject  met de Roblox [Model](/docs/nl-nl/reference/engine/classes/Model) . Modellen fungeren als een container voor een verzameling onderling verbonden delen op dezelfde manier als je een ouder-kindrelatie zou kunnen vaststellen tussen veel GameObjects  in Unity. Je specificeert een van de delen van het model als zijn [primaire deel](/docs/nl-nl/parts/models#stel-een-primair-onderdeel-in)  om het draaipunt te definiëren. Modellen bevatten ook scripts, animaties, geluidseffecten, prompts, beperkingen, deeltjesemitteren, en meer.

Bijvoorbeeld, een Unity GameObject  kan componenten hebben voor ParticleSystem , Physics3D , SpringConstraint , en een script. In het Hiërarchie venster zie je een enkel GameObject  genaamd SpringyFireball . Het Inspector venster toont de verzameling componenten en eigenschappen.

In Roblox kan een vergelijkbaar SpringyFireball  model in het Explorer  venster er ongeveer zo uitzien:

```

Model

|- ParticleEmitter

|- MeshPart

|- SpringConstraint

|- ClickDetector

|  |- Script

```

Roblox's fysica-standaard filosofie strekt zich uit tot het proces van het bouwen van 3D-modellen. In Roblox is het samenvoegen van meerdere delen tot een [assemblage](/docs/nl-nl/physics/assemblies)  een uitstekende manier om snel dingen te bouwen, omdat Roblox de gelaste delen beschouwt als één rigide lichaam. Deze aanpak is niet beschikbaar in Unity.

In plaats van standaard metrische eenheden voor lengte en massa, gebruikt Roblox hypothetische eenheden genaamd studs en Roblox Mass Units (RMU's). Voor benaderende metrische conversies en aanbevelingen rond gebruik, zie [Eenheden](/docs/nl-nl/physics/units) .

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

Unity heeft niet het concept van verschillende script types. Als je ervoor kiest om een multiplayer game te maken, gebruikt Unity zijn netwerklibraries om aan te geven wanneer een GameObject  (en zijn scripts) exclusief voor de server moet zijn.

In Unity is veel van de functionaliteit van de engine beschikbaar via de methoden van MonoBehaviour . Bijvoorbeeld, om code uit te voeren vóór de renderloop, voeg je code toe aan de Update()  methode. Om fysica botsingsevents te verwerken, voeg je code toe aan de OnCollideEnter()  methode.

Roblox-scripts zijn meer gebeurtenisgestuurd. Je krijgt toegang tot vergelijkbare functionaliteit door je in te schrijven voor services en te luisteren naar updates.

### [C# en Luau](#c-en-luau)[](#c-en-luau)

Voor scripting gebruikt Unity C#. Roblox gebruikt [Luau](/docs/nl-nl/luau) , een scripttaal afgeleid van [Lua 5.1](https://www.lua.org/manual/5.1/) .

In vergelijking met C# is Luau geleidelijk getypeerd en heeft het over het algemeen een minder uitgebreide syntaxis. In grotere projecten kan geleidelijk typen echter categorieën van bugs introduceren die sterk getypeerde talen zoals C# vermijden, dus overweeg om [strikte typecontrole](/docs/nl-nl/luau/type-checking#inferentiemodi)  in Roblox-scripts in te schakelen.

Voor basis syntaxisverschillen tussen de scripttalen, zie [Luau en C# vergelijking](/docs/nl-nl/luau/luau-csharp-comparison) .

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

Het Roblox-script kan relatief beknopt zijn omdat Roblox veel ingebouwde aannames heeft: een [Player](/docs/nl-nl/reference/engine/classes/Player)  met een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  karakter verbonden met de server en kan [Tools](/docs/nl-nl/reference/engine/classes/Tool)  uitrusten. Deze aannames bestaan niet in Unity, dus de implementatie zou heel anders zijn.

## [Assets](#assets)[](#assets)

Unity en Roblox ondersteunen beide het importeren van aangepaste meshes en modellen in .fbx  formaat. Bepaalde soorten assets kunnen specifieke configuraties en exportinstellingen van je derde partij modellering software vereisen. Voor meer informatie, zie de volgende pagina's:

-

[Importer](/docs/nl-nl/studio/importer)

-

[Algemene specificaties](/docs/nl-nl/art/modeling/specifications)

-

[Blender en Maya exportvereisten](/docs/nl-nl/art/modeling/export-requirements)

In Unity importeren objecten in je Assets  directory, zichtbaar in het Project  venster. In Roblox importeren assets in je [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  en in de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of [Asset Manager](/docs/nl-nl/projects/assets/manager) .

Roblox biedt ook een open-source [Blender-plugin](/docs/nl-nl/art/modeling/roblox-blender-plugin)  om het importproces te stroomlijnen.

## [Transforms](#transforms)[](#transforms)

Unity 's transformaties en Roblox's [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame)  dienen vergelijkbare doelen bij het weergeven van 3D-transformaties van objecten:

-

Zowel transformaties als [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame)  vertegenwoordigen de positie en rotatie van een object in 3D-ruimte. Transformaties omvatten schaal, terwijl Roblox een [BasePart.Size](/docs/nl-nl/reference/engine/classes/BasePart#Size) -eigenschap gebruikt die geen deel uitmaakt van de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) .

-

Beide ondersteunen vermenigvuldiging voor complexe transformaties en hebben ingebouwde methoden voor andere manipulaties.

## [Samenwerking](#samenwerking)[](#samenwerking)

In Unity werk je samen met standaard versiebeheersystemen of betaalde diensten zoals Unity Version Control.

Roblox-bestanden leven in de cloud (hoewel je kopieën kunt exporteren), dus Roblox Studio biedt ingebouwde samenwerkingsworkflows voor gelijktijdige bewerking, groepsbeheer, machtigingen, scriptontwerp en meer. Zie [Samenwerking](/docs/nl-nl/projects/collaboration) .

Cloud-synchronisatie biedt verdere voordelen met [pakketten](/docs/nl-nl/projects/assets/packages) , de Roblox-equivalent van Unity prefabs. Het omzetten van een asset of assethiërarchie naar een pakket helpt met lokale herbruikbaarheid, maar ook met samenwerking. Wanneer jij of je samenwerkers een nieuwe versie van een pakket publiceren, kun je bestaande instanties van dat pakket binnen een game snel bijwerken of ze instellen om automatisch bij te werken.

## [Plugins](#plugins)[](#plugins)

Vergelijkbaar met Unity-tools ondersteunt Roblox Studio [plugins](/docs/nl-nl/studio/plugins) , die verschillende aspecten van het ontwikkelingsproces kunnen vereenvoudigen of je extra controle kunnen geven. Plugins zijn beschikbaar in de [Creator Store](/docs/nl-nl/production/creator-store) , net als assets, veel gratis.

## [Woordenlijst](#woordenlijst)[](#woordenlijst)

| Unity | | Roblox | | Opmerkingen |
| Scene | | [Plaats](/docs/nl-nl/projects#plaatsen) | |  |
| GameObject | | [Part](/docs/nl-nl/reference/engine/classes/Part)  of [Model](/docs/nl-nl/reference/engine/classes/Model) | | Zie [Filosofische verschillen](#filosofische-verschillen) . |
| Prefab | | [Pakket](/docs/nl-nl/projects/assets/packages) | |  |
| Transform | | [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) | | [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  bevat geen schaalinformatie. Zie [Transforms](#transforms) . |
| Hiërarchie | | [Explorer](/docs/nl-nl/studio/explorer) | |  |
| Inspector | | [Eigenschappen](/docs/nl-nl/studio/properties) | |  |
| Scene view | | [3D viewport](/docs/nl-nl/studio/overview#3d-viewport) | |  |
| Game view | | [3D viewport](/docs/nl-nl/studio/overview#3d-viewport) | | Het viewport verandert in een gameplay-weergave wanneer je je game test. |
| Project window | | [Asset Manager](/docs/nl-nl/projects/assets/manager)  of [Toolbox](/docs/nl-nl/projects/assets/toolbox) | |  |
| Terrain Inspector | | [Terrain Editor](/docs/nl-nl/studio/terrain-editor) | |  |
| Spawn point | | [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation) | |  |
| Console | | [Output](/docs/nl-nl/studio/output) | |  |
| Asset Store | | [Creator Store](/docs/nl-nl/production/creator-store) | |  |
| Overlays | | [Toolbar](/docs/nl-nl/studio/overview#werkbalk-en-mezzanine) | |  |
| Tool | | [Plugin](/docs/nl-nl/studio/plugins) | |  |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
