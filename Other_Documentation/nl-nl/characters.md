<!-- Source: https://create.roblox.com/docs/nl-nl/characters -->

Personages | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Personages

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Personages  zijn de figuren die spelers besturen of mee interageren, en ze helpen het spel vooruit te drijven, bieden uitdagingen en maken de wereld levendig. Op Roblox is een personage elk [Model](/docs/nl-nl/reference/engine/classes/Model) , humanoïde of anderszins, dat beweegt, communiceert en interactie heeft met de omgeving. Ze kunnen zo eenvoudig zijn als een gloeiende orb die belangrijke informatie voor een quest biedt, of zo rijk als een volledig gerigged draak met gezichtsanimaties die rigide en gelaagde accessoires kan dragen.

Het platform ondersteunt een spectrum van type personages die je kunt bouwen voor de specifieke ontwerpeisen van je game, zoals lichte niet-speler personages voor omgevingsleven, gestandaardiseerde avatar-personages met ingebouwde functionaliteit om cosmetica te dragen en animaties af te spelen, of aangepaste rigs die toegang hebben tot universele animatiebibliotheken. Laten we je opties verkennen.

## [Typen](#typen)[](#typen)

In grote lijnen zijn er twee hoofdtypen personages: speler personages  en niet-speler personages . Hoewel beide typen personages er visueel hetzelfde uit kunnen zien, kunnen hun interne configuraties aanzienlijk variëren afhankelijk van wat elk personage moet doen in jouw game.

### [Speler personages](#speler-personages)[](#speler-personages)

Speler personages zijn personages die de speler bestuurt om een spel te spelen. Terwijl sommige game-ontwikkelaars aangepaste speler personages vanaf nul creëren die passen bij hun game-ontwerp esthetiek, kiezen velen ervoor om spelers hun [platform avatar](/docs/nl-nl/avatar)  als hun speler personage te laten behouden.

![](https://prod.docsiteassets.roblox.com/assets/characters/overview/bird-example.png) In [BIRD](https://www.roblox.com/games/3633505977/BIRD)  komen alle spelers het spel binnen als een aangepast vogelpersonage.

![](https://prod.docsiteassets.roblox.com/assets/avatar/AvatarSample.png) In [The Mystery of Duvall Drive](https://www.roblox.com/games/7902470429/The-Mystery-of-Duvall-Drive)  komen alle spelers het spel binnen als hun avatar.

Voor spelers zijn avatars diep persoonlijk omdat ze iemands digitale identiteit symboliseren, uniek gecreëerd door individuele aankopen op de [Marketplace](https://www.roblox.com/catalog)  en in games, of van weggeefacties. Voor game-ontwikkelaars bieden avatars een gestandaardiseerd, volledig uitgerust personage dat platformcompatibiliteit ontgrendelt voor:

-

Lichaams- en gezichtsanimaties

-

Rigide accessoires, gelaagde accessoires, klassieke kleding en make-up assets

-

Kernpersonagegedrag en eigenschappen, zoals een weergavenaam, gezondheidsbalk en basisbewegingsstaten

Avatars kunnen deze functionaliteit bieden omdat ze het volgende systeem van componenten moeten bevatten om door makers naar de Marketplace te worden geüpload:

| ** Component** | | ** Functionaliteit** |
| --- | --- |
| 15 [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  lichaamsdelen met gestandaardiseerde naamgevingsconventies | | Consistente hoeveelheid ledematen voor elk personage met een uniforme indeling voor accessoires, cosmetica en animaties. |
| Rigging armatuur met gestandaardiseerde naamgevingsconventies en een gewricht hiërarchie | | Consistente hoeveelheid poseerbare gewrichten voor animatieondersteuning. Er zijn 15 vereiste poseerbare gewrichten voor [standaard R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs) , maar je kunt tot 37 extra gewrichten toevoegen voor [geavanceerde R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs) . |
| [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object | | Consistent personagegedrag en eigenschappen, zoals:
-

Het weergeven van de naam en gezondheid van het personage boven hun Head  lichaamsdeel.

-

Items uitrusten in de 3D-ruimte.

-

Toegang tot bewegingsstaten zoals lopen, springen en zwemmen.

 |
| [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  object met ten minste 17 gestandaardiseerde gezichtsbasishoudingen | | Consistente gezichtsuitdrukkingen. |
| 15 [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  objecten | | Consistente vervormingsdoelen voor gelaagde accessoires die zich uitstrekken, passen en op het lichaam van het personage lagen. |
| 19 [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  punten | | Consistente doelen voor rigide accessoires en in-game uitrustbare objecten om aan het lichaam van het personage te bevestigen. |

Wat zijn geavanceerde R15 rigs?

Standaard avatar rigs vereisen 15 poseerbare gewrichten om de 15 lichaamsdelen van het personage te articuleren. Als je echter hogere-fidelity personages wilt creëren met een groter niveau van realisme, zijn er tot 37 extra optionele gewrichten voor geavanceerde R15 rigs  die je kunt maken voor gearticuleerde handen, schouders en wervelkolombewegingen.

Deze optionele gewrichten omvatten:

-

Wervelkolom : Spine  en Chest  subonderdelen

-

Sleutelbeenderen : LeftClavicle  en RightClavicle  voor schouderarticulatie

-

Hoofd : HeadBase  geparent onder het Head  lichaamsdeel voor nek- en gezichtsarticulatie

-

Vingers : Tot 15 gewrichten per hand (3 phalangen × 5 vingers)

-

Tenen : LeftToeBase  en RightToeBase  voor voetarticulatie

Voor meer informatie, zie [Lichaam specificaties - Geavanceerde R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs) .

Wat is AvatarJointUpgrade ?

Wanneer je [StarterPlayer.AvatarJointUpgrade](/docs/nl-nl/reference/engine/classes/StarterPlayer#AvatarJointUpgrade)  inschakelt, introduceert de upgrade automatisch kracht- en koppelbeperkte [AnimationConstraint](/docs/nl-nl/reference/engine/classes/AnimationConstraint)  objecten naar de gewrichten van elk personage, ter vervanging van [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  objecten. Dit stelt je in staat om realistische, fysica-gedreven bewegingen en interacties te creëren, zoals volledig gesimuleerde ledematen en aangedreven ragdolls.

### [Niet-speler personages](#niet-speler-personages)[](#niet-speler-personages)

Niet-speler personages (NPC's) zijn personages die door systemen binnen het spel worden bestuurd om de speler te ondersteunen of uit te dagen, zoals bondgenoten of vijanden, of anderszins de omgeving in te vullen om het meeslepend te maken. In tegenstelling tot speler personages die een breed scala aan attributen en functionaliteit vereisen om speldoelen te voltooien, hoeven niet-speler personages vaak slechts één of twee eenvoudige taken uit te voeren, zoals een pad lopen, schade oplopen of reageren op de acties van de speler.

![](https://prod.docsiteassets.roblox.com/assets/characters/overview/npc-example.png) In [Mansion of Wonder](https://www.roblox.com/games/6901029464/Mansion-of-Wonder)  kunnen spelers interageren met een vos NPC om prijzen te verwerven en met een rotswezen om naar het hoofdgamegebied te teleporteren.

Omdat ze niet dezelfde componentenset, rigging armatuur of functie-diepte van speler personages vereisen, hoeven de meest basale niet-speler personages alleen een [Model](/docs/nl-nl/reference/engine/classes/Model)  te hebben met geometrie en enkele scripts om hun doel voor jouw game-ontwerpvereisten te vervullen. In feite kiezen veel game-ontwikkelaars ervoor om hun NPC's te creëren als een [Model](/docs/nl-nl/reference/engine/classes/Model)  met slechts een kind mesh of twee en een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object om basis personagegedrag en eigenschappen te implementeren en te benaderen.

## [Creatietools](#creatietools)[](#creatietools)

De tools en het proces die je gebruikt om je personages te creëren kunnen er anders uitzien, afhankelijk van het type en de complexiteit van elk personage dat je creëert, maar over het algemeen beginnen veel game-ontwikkelaars met het maken van ten minste een ruwe mesh in een derde-partij modelleertool voor het lichaam van het personage. De volgende zijn voorbeelden van populaire derde-partij software die makers vaak gebruiken om aangepaste personage lichamen, evenals texturen, rigging armaturen, accessoires en animaties te creëren.

| ![](https://prod.docsiteassets.roblox.com/assets/landing/blender-logo.png) | | ![](https://prod.docsiteassets.roblox.com/assets/landing/maya-logo.png) | | ![](https://prod.docsiteassets.roblox.com/assets/landing/gimp-logo.png) |
| [Blender](https://www.blender.org/)  is een gratis, open-source 3D creatiesuite met een breed scala aan modellering, sculpting, texturering, rigging en animatietools. | | [Autodesk Maya](https://www.autodesk.com/products/maya/overview)  is een op abonnement gebaseerde industriestandaard professionele toolset die de volledige 3D productie pipeline dekt. | | [GNU Image Manipulation Program](https://www.gimp.org/)  (GIMP) is een gratis, open-source afbeeldingseditor die 2D asset creatie ondersteunt. |

Zodra je de basis van je personage hebt, kun je je creaties [importeren](/docs/nl-nl/studio/importer)  in Studio en toegang krijgen tot alle first-party tooling die Roblox te bieden heeft, inclusief een volledige pipeline om een ruwe mesh om te zetten naar een personage dat ook voldoet aan platformbeleid en technische normen om klaar te zijn voor de Marketplace. De volgende details alle belangrijke tools die je kunt gebruiken om personage-assets te creëren, configureren en testen voor game-ontwikkelaars van alle vaardigheidsniveaus.

Ondersteunende functies

De volgende functies bieden ondersteuning voor verschillende fasen van het personage creatieproces:

| ** Tool** | | ** Beschrijving** |
| [Avatar Instellingen](/docs/nl-nl/studio/avatar-settings) | | Schakel wereldwijde game-niveau avatar gedrag, botsing, animatiepakketten en Character Controller Library schakelaars in. |
| [Importer](/docs/nl-nl/studio/importer) | | Importeer je aangepaste meshes met PBR texturen, rigging, skinning en animatiegegevens voor je personages. |
| [Animatie Editor](/docs/nl-nl/animation/editor) | | Importeer, ontwerp en publiceer animaties voor je personages, zoals gebaren en reacties. |
| [Accessoire Pasvorm Tool](/docs/nl-nl/avatar/accessory-fitting-tool) | | Test je aangepaste modellen op meerdere combinaties van personage lichamen, animaties en accessoires. |
| [Automatische Skinning Overdracht](/docs/nl-nl/avatar/automatic-skinning-transfer) | | Verplaats of genereer skinning gegevens naar je gelaagde en gezichtsaccessoires zodat ze vervormen langs het lichaam van het personage waaraan ze zijn bevestigd. |

### [Avatar Setup](#avatar-setup)[](#avatar-setup)

[Avatar Setup](/docs/nl-nl/avatar-setup)  is het snelste pad van een ruwe mesh naar een speler personage, omdat het automatisch aangepaste modellen verwerkt in avatar personage assets. Als je personages niet alle componenten hebben die ze nodig hebben om te bewegen, animeren en accessoires te dragen, kan Avatar Setup alle ontbrekende componenten genereren, zoals:

-

Indelingen  - Scheidt het lichaam van het personage in de standaard 15 lichaamsdelen.

-

Rigging gegevens  - Voegt een [R15 rigging armatuur](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  toe aan het lichaam van je personage om beweging en animatie mogelijk te maken.

-

Skinning gegevens  - Voegt gewichten en invloeden toe aan verschillende oppervlakken van het lichaam van je personage, waardoor een organische en natuurlijke flexibiliteit tijdens beweging wordt gegarandeerd.

-

Gezichtsanimaties  - Genereert de FACS houdingen, gezichtsrigging, skinning en animatiegegevens die nodig zijn voor gezichtsanimaties.

-

Cages  - Voegt de vereiste binnen- en buitenkaders toe aan de lichaamsdelen van je personage zodat het gelaagde accessoires kan dragen.

-

Bevestigingspunten  - Voegt de juiste bevestigingspunten toe aan het lichaam van je personage zodat het rigide accessoires kan dragen.

Voor game-ontwikkelaars die hun personages naar de Marketplace willen uploaden, vereenvoudigt Avatar Setup wat vroeger een multi-tool, multi-iteratie workflow was tot een enkele doorgang:

 ![](https://prod.docsiteassets.roblox.com/assets/characters/overview/avatar-setup-workflow.png)  ![](https://prod.docsiteassets.roblox.com/assets/characters/overview/Avatar-Setup-Example.png)

Voor informatie over configuratiestandaarden om ervoor te zorgen dat alle Avatar Setup functies werken zoals verwacht, zie [Avatar Setup specificaties](/docs/nl-nl/avatar-setup/auto-setup-requirements) .

### [Adaptieve Animatie](#adaptieve-animatie)[](#adaptieve-animatie)

[Adaptieve Animatie](/docs/nl-nl/characters/adaptive-animation)  lost een moeilijk probleem op: hoe één animatiebibliotheek te laten werken over aanzienlijk verschillende lichaamstypes. Met behulp van [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten, laat Adaptieve Animatie je de gewrichten van je personage toewijzen aan Roblox's [gestandaardiseerde rigging armatuur specificaties](/docs/nl-nl/avatar/character-bodies/specifications#rigging) . Dit werkt bidirectioneel:

-

Avatar vereisten > Aangepaste rig  - Je aangepaste rigs kunnen onmiddellijk de volledige animatiebibliotheek van emotes en bewegingsstaten gebruiken.

-

Aangepaste rig > Avatar vereisten  - De animaties die je maakt op je aangepaste rigs kunnen onmiddellijk opnieuw gericht worden naar avatars met standaard rigging armaturen.

Dit geldt ook voor handen en vingers in [geavanceerde R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs) ; wanneer je de handgewrichten van je personage toewijst met behulp van het Adaptieve Animatie systeem, passen vingeranimaties voor de proporties van één hand zich onmiddellijk aan verschillende handgeometrieën aan.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Assign-Joints-A.png)

### [Animatie Grafiek Editor](#animatie-grafiek-editor)[](#animatie-grafiek-editor)

[Animatie Grafiek Editor](/docs/nl-nl/animation/graph-editor)  is een visuele, node-gebaseerde tool die individuele animatieclips samenstelt in runtime-logica zonder dat je animatiecontroller scripts met de hand hoeft te schrijven. Je kunt blend trees, state machines en geparametriseerd animatiegedrag voor je personages bouwen terwijl je nog steeds toegang hebt tot animatie grafiek knooppunten programmatisch voor directe controle.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Connect-To-Add.png)

## [Personage optimalisatie](#personage-optimalisatie)[](#personage-optimalisatie)

Naarmate je games groeien met meer spelers, uitgestrekte omgevingen en rijke animaties, vereisen je personagesystemen architectuur om optimalisatie te ondersteunen. Er zijn twee systemen die dit direct aanpakken: de Character Controller Library voor personagebeweging en gedrag, en SLIM voor renderprestaties.

### [Character Controller Library](#character-controller-library)[](#character-controller-library)

Het standaard [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object binnen speler personages biedt een toestandsmachine die functioneert, maar het is rigide. Het bevat hard-coded toestanden die je slechts één tegelijk kunt activeren met vaste overgangslogica, het is moeilijk te componeren, en het is moeilijk te configureren op schaal.

Om deze uitdagingen aan te pakken, biedt de [Character Controller Library](/docs/nl-nl/characters/character-controller-library)  (CCL) een vervanging met een op vaardigheden gebaseerde architectuur:

-

Vaardigheden  bepalen dynamisch wat een personage kan doen, zoals rennen, springen, klimmen en zwemmen.

-

Controllers  behandelen dynamisch hoe de beweging van dat personage wordt gesimuleerd, zoals grondwrijving, versnellingcurves en realistische behoud van lineaire en hoeksnelheid wanneer personages springen.

Wanneer je je aanmeldt voor CCL in [Avatar Instellingen](/docs/nl-nl/studio/avatar-settings) , kun je experimenteren met vaardigheidsconfiguraties terwijl je game draait en specifieke controllers aanpassen om de fysieke simulatie van het personage en de interactie met de omgeving aan te passen, zoals de basisbeweging snelheid van het personage.

 ![Character Controller Library schakelaar in het Avatar Instellingen venster](https://prod.docsiteassets.roblox.com/assets/studio/general/Avatar-Settings-CCL.png)

### [SLIM voor rendering](#slim-voor-rendering)[](#slim-voor-rendering)

Personages kunnen duur zijn om te renderen, vooral voor hoge-resolutie personages met gelaagde accessoires en fysiek gebaseerde rendering (PBR) texturen. Voor games die veel modellen en personages bevatten, zoals een levendige stad vol NPC's, gebouwen, props en voertuigen, kunnen spelers lage framerates en slechte prestaties ervaren.

Om deze uitdagingen voor renderprestaties aan te pakken, biedt [Scalable Lightweight Interactive Models](/docs/nl-nl/workspace/streaming/slim)  (SLIM) een automatisch optimalisatiesysteem om lichte, geoptimaliseerde representaties van avatar personages en modellen te genereren met behulp van cloud-gebaseerde transcoding. Tijdens runtime selecteert de engine de beste representatie op basis van afstand, apparaatscapaciteit en streamingstatus.

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Disabled.jpg) Zonder SLIM — gestreamde modellen zijn onzichtbaar

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Enabled.jpg) Met SLIM — geoptimaliseerde stand-ins blijven zichtbaar

SLIM biedt drie belangrijke voordelen:

-

Visuele kwaliteit  - Distant modellen verschijnen gedetailleerder dan het legacy model niveau-van-detail systeem, met een nauwere trouw aan het origineel.

-

Consistente overgangen  - Alle delen binnen een model schakelen gelijktijdig detailniveaus, waardoor schokkende per-deel overgangen worden geëlimineerd.

-

Prestaties  - Composite meshes verminderen dramatisch het aantal draw calls, driehoekenaantallen en geheugengebruik, waardoor rijkere scènes mogelijk zijn op alle apparaatsniveaus.

Bovendien, wanneer je SLIM configureert voor avatar personages, render de engine:

-

Een SLIM-versie wanneer een daadwerkelijk avatar model wordt gestreamd.

-

Wisselt tussen SLIM en full-resolutie representaties op basis van beschikbare middelen, zelfs binnen de streamingradius.

-

Beperkt SLIM-animaties op basis van scènebelang en beschikbare bandbreedte.

Publiek op Grote Afstand Publiek in Dichte Nabijheid

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Avatars-Enabled-Far.jpg)

SLIM Ingeschakeld

~170,000 driehoeken

~4,000 client instanties

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Avatars-Disabled-Far.jpg)

SLIM Uitgeschakeld

~2,600,000 driehoeken

~60,000 client instanties

SLIM vereist dat je [instance streaming](/docs/nl-nl/workspace/streaming)  inschakelt, wat de Roblox-engine in staat stelt om 3D-inhoud en gerelateerde instanties in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  dynamisch te laden en te ontladen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
