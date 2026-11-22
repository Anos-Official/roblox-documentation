<!-- Source: https://create.roblox.com/docs/nl-nl/art/blender -->

Blender | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Software van derden

# Blender

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Blender is een gratis, open-source 3D-creatiesuite met een breed scala aan modellering-, sculptuur-, textuur- en animatietools. Het draait op Linux-, macOS- en Windows-systemen, en deze cross-platform applicatie is een populaire keuze voor makers die avatars, accessoires en 3D-objecten voor Roblox-spellen willen maken.

Hoewel dit geenszins een uitputtende lijst is, biedt de volgende gids hoog-niveau informatie over essentiële Blender-tools en -functies voor 3D-creatie, evenals richtlijnen voor best practices voor het ontwerpen van 3D-kunst tussen Blender en Studio.

Om de nieuwste versie van Blender te downloaden, bezoek [Blender.org](https://www.blender.org/download/) .

## [Bestandsinstellingen](#bestandsinstellingen)[](#bestandsinstellingen)

Voordat je begint met het maken van 3D-kunst op Blender voor het Roblox-platform, is het belangrijk om zowel de Blender- als de Studio-instellingen te configureren, zodat je 3D-objecten dezelfde positie, oriëntatie en schaal behouden terwijl je ze tussen de twee applicaties verplaatst.

### [Configureer eenheden](#configureer-eenheden)[](#configureer-eenheden)

Standaard gebruiken Blender en Studio verschillende primaire eenheden om lengte te meten: Blender heeft standaard de metrische schaal, en Studio heeft standaard [studs](/docs/nl-nl/physics/units) . Om ervoor te zorgen dat je 3D-objecten dezelfde afmetingen behouden wanneer je ze in een van de applicaties verplaatst of schaalt, moet je de eenheden van Blender configureren zodat ze consistent zijn met studs.

Om de eenheden van Blender compatibel te maken met de studeenheden van Roblox:

1.

Navigeer naar de Eigenschappen-editor , selecteer vervolgens in de navigatie aan de linkerkant het tabblad Scene .

 ![Blender's Properties editor met het Scene-tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/scene-tab.jpg)

2.

Klik op het dropdownmenu Eenheden  om de container uit te vouwen, en:

1.

Stel Eenheidssysteem  in op Geen .

2.

Stel Rotatie  in op Graden .

### [Importinstellingen](#importinstellingen)[](#importinstellingen)

3D-software en applicaties gebruiken coördinatensystemen om de positie en oriëntatie van objecten in de 3D-ruimte weer te geven. Deze coördinatensystemen bestaan doorgaans uit drie assen:

-

Eén as vertegenwoordigt de horizontale positie (beweging naar links en rechts).

-

Eén as vertegenwoordigt de verticale positie (beweging omhoog en omlaag).

-

Eén as vertegenwoordigt de diepte (beweging naar voren en naar achteren).

Blender en Studio gebruiken verschillende  coördinatensystemen, specifiek voor de as die de "omhoog" richting vertegenwoordigt. Net als andere modelleringsoftware gebruikt Blender de Z -as omdat 3D-objecten omhoog uit het 2D-vlak bewegen om een 3D-object te worden; omgekeerd gebruikt Studio, net als andere engines, de Y -as omdat personages zich op het grondvlak bewegen en omhoog springen voor verticale beweging.

Dit verschil is belangrijk om in gedachten te houden wanneer je je 3D-kunst in Blender of Studio importeert, omdat je aanpassingen aan de importinstellingen moet maken om ervoor te zorgen dat je object de juiste oriëntatie behoudt in een van de applicaties.

![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/NavigationGizmo.jpg) Blender's Navigatie Gizmo

![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/ViewSelector.jpg) Studio's View Selector

#### [Studio naar Blender](#studio-naar-blender)[](#studio-naar-blender)

Om de importinstellingen van Blender voor 3D-objecten vanuit Studio in te stellen:

1.

Klik in de linkerbovenhoek op het hamburgermenu. Een pop-upmenu verschijnt.

2.

Navigeer naar Bestand  > Importeren  > Wavefront (.obj) , FBX (.fbx)  of glTF 2.0 (.glb/.gltf) . Het Blender Bestandsweergave  venster verschijnt.

3.

Selecteer een of meerdere .obj , .fbx  of .gltf -bestanden die je wilt importeren.

4.

Navigeer in het rechterpaneel naar de sectie Algemeen :

1.

Stel Schaal  in op 1  om dezelfde schaal uit Studio te behouden.

2.

Stel Voorwaartse As  in op Z  om dezelfde "voorwaartse" as als Studio te behouden.

3.

Stel Omhoog As  in op Y  om dezelfde "omhoog" as als Studio te behouden.

 ![Het Blender Bestandsweergave venster met de Algemeen sectie gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/BlenderFileView-Import.png)

5.

Klik rechtsonder op de knop Importeren .

#### [Blender naar Studio](#blender-naar-studio)[](#blender-naar-studio)

Om de importinstellingen van Studio voor 3D-objecten vanuit Blender in te stellen:

1.

Navigeer naar Bestand  > Importeren . Je lokale bestandsbrowser verschijnt.

2.

Selecteer en bevestig het .obj , .fbx  of .gltf -bestand(en) van het 3D-object dat je wilt importeren vanuit je lokale systeem. Het Importer's Import Preview  venster verschijnt.

3.

Navigeer in het rechterpaneel naar de sectie Bestand Algemeen , en:

1.

Schakel Alleen importeren als een model  in als je meerdere objecten hebt die je wilt groeperen in een [Model](/docs/nl-nl/reference/engine/classes/Model)  object.

2.

Schakel Uploaden naar Roblox  in als je een asset wilt maken met een asset-ID die je kunt verwijzen in verschillende projecten.

3.

Stel Maker  in op Ik  als jij de enige bent die toegang tot het object nodig heeft, of op de groep die het project bezit waaraan je werkt. Deze laatste instelling zorgt ervoor dat alle in aanmerking komende groepsleden toestemming hebben om het 3D-object binnen het project te gebruiken.

4.

Schakel Invoegen met behulp van Scene-positie  in zodat het object de positie behoudt die je in Blender hebt ingesteld.

 ![Het Import Preview venster met de Bestands Algemeen sectie gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Studio-Import.png)

4.

Navigeer naar de sectie Bestand Transformatie , en stel de volgende instellingen in zodat het object dezelfde oriëntatie uit Blender behoudt:

1.

Stel Wereld Voorwaarts  in op Voor  om dezelfde "voorwaartse" as als Blender te behouden.

2.

Stel Wereld Omhoog  in op Boven  om dezelfde "omhoog" as als Blender te behouden.

5.

Navigeer naar de sectie Bestand Geometrie , en stel Schaal Eenheid  in op Stud  om dezelfde schaal uit Blender te behouden.

6.

Klik onderaan het venster op de knop Importeren . Je 3D-object wordt geïmporteerd met dezelfde schaal en oriëntatie uit Blender.

### [Exportinstellingen](#exportinstellingen)[](#exportinstellingen)

Net als in de vorige sectie over bestandsinstellingen, is het belangrijk om de verschillende coördinatensystemen van Blender en Studio in overweging te nemen wanneer je klaar bent om je 3D-kunst vanuit Blender te exporteren. Door iets extra tijd te besteden aan het configureren van je exportinstellingen, kun je ervoor zorgen dat je 3D-objecten de juiste oriëntatie, schaal en positie behouden wanneer je ze in Studio importeert.

Avatar-items, of andere assets die gespecialiseerde componenten gebruiken, vereisen unieke exportinstellingen. Zie de volgende links voor aanvullende informatie:

-

Voor rigide accessoires, zie [accessoire specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)  en [accessoire exportinstellingen](/docs/nl-nl/avatar/rigid-accessories/export) .

-

Voor gelaagde accessoires, zie [gelaagde accessoire specificaties](/docs/nl-nl/avatar/layered-accessories)  en [gelaagde exportinstellingen](/docs/nl-nl/avatar/layered-accessories/export) .

-

Voor avatar-personages, zie [avatar specificaties](/docs/nl-nl/avatar/character-bodies/specifications)  en [avatar exportinstellingen](/docs/nl-nl/avatar/character-bodies/export) .

Om de Blender-instellingen voor het exporteren van 3D-objecten voor Studio in te stellen:

1.

Klik in de linkerbovenhoek op het hamburgermenu. Een pop-upmenu verschijnt.

2.

Navigeer naar Bestand  > Exporteren  > Wavefront (.obj) , FBX (.fbx)  of glTF 2.0 (.glb/.gltf) . Het Blender Bestandsweergave  venster verschijnt.

3.

Navigeer in het rechterpaneel naar de sectie Inbegrepen , en schakel Beperk tot Geselecteerde Objecten  in om alleen je geselecteerde objecten te exporteren.

 ![Het Blender Bestandsweergave venster met de Algemeen sectie gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/BlenderFileView-Export.png)

4.

In de sectie Transformatie

1.

Als je .fbx  exporteert, stel Toepassen Schaling  in op FBX Eenheidsschaal  zodat je object(en) dezelfde schaal in Studio behouden. Voor meer informatie over schaling, zie [Schaal aanpassen](#schaal-aanpassen-fbx) .

2.

Stel Voorwaarts  in op Z Voorwaarts  om dezelfde "voorwaartse" as als Blender te behouden.

3.

Stel Omhoog  in op Y Omhoog  om dezelfde "omhoog" as als Blender te behouden.

5.

Klik rechtsonder op de knop Exporteren . Je 3D-object is nu klaar om te [importeren in Studio](#blender-naar-studio) .

### [Schaal aanpassen (FBX)](#schaal-aanpassen-fbx)[](#schaal-aanpassen-fbx)

Het FBX (.fbx ) bestandsformaat wordt veel gebruikt in 3D-werkstromen vanwege de brede ondersteuning in modelleringstools en engines. Echter, wanneer je vanuit Blender exporteert met de standaard .fbx  instellingen, worden modellen vaak op een onverwacht grote schaal in Roblox Studio geïmporteerd.

Roblox Studio ondersteunt ook GLTF (.gltf ) formaten die deze extra schalingconfiguraties niet vereisen.

 ![Twee standaard Blender-kubussen geïmporteerd in Studio met verschillende schalen.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Blender-Scale-Examples.png)

Als je op .fbx  vertrouwt in je werkstroom, zijn de juiste exportinstellingen of projectinstellingen essentieel om ervoor te zorgen dat je modellen op de juiste grootte verschijnen en hun bedoelde verhoudingen behouden over platforms heen.

Er zijn veel manieren om je model te configureren zodat je .fbx  model zoals verwacht schaalt in Studio. Zie de volgende populaire instellingen om schaling te beheren:

| Blender-instelling | | UI | | Beschrijving |
| --- | --- |
| Stel tijdens export Transformatie  > Toepassen Schaling  in op FBX Eenheidsschaal . | | ![Twee standaard Blender-kubussen geïmporteerd in Studio met verschillende schalen.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-5.png) | | Modellen die met deze instelling zijn geëxporteerd, worden in Studio of terug in Blender op dezelfde schaal geïmporteerd.
Zorg ervoor dat alle andere schalingswaarden in project- of exportinstellingen zijn ingesteld op standaard (1.0 ).
 Dit is de aanbevolen manier om .fbx -bestanden op dezelfde schaal te exporteren. |
| Stel tijdens export Transformatie  > Schaal  in op .01 . | | ![Twee standaard Blender-kubussen geïmporteerd in Studio met verschillende schalen.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-2.png) | | Dit schaalt je export zodat het model op de verwachte schaal in Studio wordt geïmporteerd.
Als je van plan bent om dit model terug in Blender of een andere niet-Studio-tool te importeren, moet je mogelijk het model bij de import schalen, anders wordt het model onverwacht klein geïmporteerd. |
| In het Scene Properties  paneel, stel Eenheden  > Eenheidsschaal  in op .01 .  | | ![Twee standaard Blender-kubussen geïmporteerd in Studio met verschillende schalen.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Scene-Units-Settings.png) | | Dit schaalt je hele scène zodat het model op de verwachte schaal in Studio wordt geïmporteerd. Als je je scène-eenheden hebt aangepast, kun je modellen met standaardinstellingen naar Studio exporteren.
Werken aan modellen op .01  schaal kan onverwachte Blender-problemen veroorzaken, zoals camera-problemen, problemen met modifiers of andere complicaties.
Als je van plan bent om dit model terug in Blender te importeren, moet je mogelijk het model bij de import schalen, anders wordt het model onverwacht klein geïmporteerd. |

Opmerking over bestaande bronnen

 Veel referentiebestanden, demo-projecten en downloadbare assets kunnen oudere of inconsistente schaalinstellingen gebruiken. Evenzo kunnen tutorials en gidsen verschillende benaderingen aanbevelen voor het omgaan met schaal tussen Blender en Studio.
Test en valideer altijd externe bronnen om ervoor te zorgen dat ze correct werken met je huidige exportwerkstroom.

## [Basisprincipes](#basisprincipes)[](#basisprincipes)

Voordat je een kijkje neemt naar alle gebruikelijke modellering-, sculptuur- en textuurtools voor het maken van 3D-kunst voor Studio, laten we de fundamentele interface-elementen van Blender bekijken die belangrijk zijn voor het navigeren door de applicatie en het vinden van de juiste menu's en bedieningselementen voor jouw specifieke 3D-creatietaak.

### [Werkruimtes](#werkruimtes)[](#werkruimtes)

 ![Blender's UI met werkruimtes gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Workspaces.png)

Werkruimtes  zijn vooraf ingestelde vensterindelingen met gespecialiseerde UI-configuraties en tooling voor verschillende 3D-creatiewerkzaamheden zoals modellering, sculptuur of texturering. Je kunt deze werkruimteconfiguraties zoals ze zijn gebruiken, of je kunt ze aanpassen zodat ze voor jou werken terwijl je snel tussen verschillende taken wisselt.

Voor informatie over aanvullende werkruimtes, zie de officiële [Werkruimtes](https://docs.blender.org/manual/en/2.81/interface/window_system/workspaces.html)  documentatie van Blender.

Er zijn veel standaard werkruimtes, maar de volgende zijn de meest voorkomende voor het creëren van 3D-kunst voor het Roblox-platform.

Indeling Modellering Sculptuur UV-bewerking Textuurverf

![Blender's Topbar met de Indeling werkruimte gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Layout_Workspace.png)

De Indeling  werkruimte is de standaard werkruimte wanneer je een Blender-bestand laadt, en het biedt basisgereedschappen voor het bekijken en transformeren van je 3D-objecten, zoals de Verplaatsen-, Schalen- en Roteren-tools. De standaardindeling van deze werkruimte omvat de volgende UI voor gemakkelijke toegang terwijl je je 3D-kunst opzet:

-

[3D Viewport](https://docs.blender.org/manual/en/latest/editors/3dview/introduction.html)  - Toont de hele scène.

-

[Outliner](https://docs.blender.org/manual/en/latest/editors/outliner/introduction.html)  - Toont alle objecten in de scène, vergelijkbaar met Studio's Explorer  venster.

-

[Eigenschappen-editor](https://docs.blender.org/manual/en/latest/editors/properties_editor.html)  - Toont bewerkbare gegevens voor het actieve object, vergelijkbaar met Studio's Eigenschappen  venster.

-

[Tijdlijn-editor](https://docs.blender.org/manual/en/latest/editors/timeline.html)  - Toont alle animatiesleutels, vergelijkbaar met de tijdlijn van de Animatie-editor .

### [3D Viewport](#3d-viewport)[](#3d-viewport)

 ![Blender's UI met de 3D Viewport gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/3DViewport.png)

Vergelijkbaar met Studio's viewport, laat de 3D Viewport  je toe om je 3D-objecten te bekijken en ermee te interageren zoals ze bestaan in de 3D-ruimte. Je kunt door de scène navigeren, objecten met je muis transformeren en je wijzigingen in realtime zien terwijl je je 3D-kunst ontwerpt.

Voor meer informatie, zie de officiële [3D Viewport](https://docs.blender.org/manual/en/latest/editors/3dview/introduction.html)  documentatie van Blender.

### [Modus](#modus)[](#modus)

 ![Blender's UI met de Modus-selector gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Modes.png)

Modi  bieden extra gereedschappen voor het bewerken van 3D-objecten in de 3D Viewport. Wanneer je een nieuwe modus selecteert uit de Modus-selector:

-

De Header toont nieuwe menu-opties.

-

De Toolbar toont een nieuwe set gereedschappen.

-

Editors en hun knoppen en panelen worden op de juiste manier in- of uitgeschakeld.

Afhankelijk van welke modus actief is, kan je cursor veranderen in een borstel, zoals in verf- of sculptuurmodi, en de 3D Viewport kan veranderen hoe het objecten weergeeft voor die specifieke taak, zoals het verduisteren van een object zodat je je verfstreken gemakkelijker kunt zien. Terwijl je Blender leert, is het nuttig om te experimenteren met verschillende modi om te zien welke tools beschikbaar zijn voor jouw specifieke 3D-creatietaak.

Voor meer informatie over modi, zie de officiële [Object Modi](https://docs.blender.org/manual/en/latest/editors/3dview/modes.html)  documentatie van Blender.

Object Bewerken Sculpt Vertex Paint Weight Paint Textuurverf

![Blender's Modes-selector met het Object Mode menu-item gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Object-Mode.jpg)

Objectmodus  is de standaardmodus en biedt gereedschappen die beschikbaar zijn voor alle objecttypes, zoals het positioneren van vertices, randen en vlakken, het roteren en schalen van objecten, en het meten van afstanden en hoeken. Deze modus is nuttig voor hoog-niveau objecttransformaties.

### [Toolbar](#toolbar)[](#toolbar)

 ![Blender's UI met de Toolbar gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Toolbar.png)

De Toolbar  is een verticale menulijst met gereedschappen aan de linkerkant van de 3D Viewport. Elke keer dat je van modus wisselt, reageert de Toolbar door een nieuwe unieke set gereedschappen voor die specifieke modus weer te geven.

Voor meer informatie over de Toolbar, zie de officiële [Toolbar](https://docs.blender.org/manual/en/latest/editors/3dview/toolbar/index.html)  documentatie van Blender.

### [3D Cursor](#3d-cursor)[](#3d-cursor)

 ![Blender's UI met de 3D Cursor gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/3DCursor.png)

De 3D Cursor  is een verplaatsbaar referentiepunt in de 3D-ruimte dat zowel locatie- als rotatiegegevens heeft. Hoewel dit gereedschap veel verschillende toepassingen heeft, zijn de meest voorkomende het gebruik van zijn positie en oriëntatie om:

-

Nauwkeurige transformaties te creëren.

-

Nieuwe objecten in de scène te plaatsen.

-

Objecten of hun vertices naar nieuwe punten in de 3D-ruimte te verplaatsen.

-

Pivotpuntlocaties opnieuw te positioneren.

Voor meer informatie over de 3D Cursor, zie de officiële [3D Cursor](https://docs.blender.org/manual/en/latest/editors/3dview/3d_cursor.html)  documentatie van Blender.

## [Modelleringstools](#modelleringstools)[](#modelleringstools)

Nu je weet hoe je door de gebruikersinterface navigeert en tools kunt wijzigen op basis van jouw specifieke 3D-creatietaak, laten we een kijkje nemen naar de meest voorkomende modelleringstools die je in staat stellen de vorm van 3D-objecten te veranderen door ofwel de hele mesh of een van de drie basis elementen van meshes te beïnvloeden:

-

Vertex  - Een enkel punt op de mesh.

-

Edge  - Een lijn die twee vertices verbindt.

-

Face  - Een oppervlakte tussen drie of meer vertices.

Elke van de volgende secties beschrijft hoe je elke tool kunt gebruiken voor objecten en/of meshelementen, de sneltoetsen die je kunt gebruiken om de tool te activeren, en hun meest voorkomende gebruikstoepassingen voor het creëren van 3D-kunst voor het Roblox-platform.

![Een enkele actieve vertex op een kubusmesh.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Vertex.png) Vertex

![Een enkele actieve edge op een kubusmesh.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Edge.png) Edge

![Een enkele actieve face op een kubusmesh.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Face.png) Face

Voor meer informatie over een van deze meshelementen, zie de officiële [Meshstructuur](https://docs.blender.org/manual/en/latest/modeling/meshes/structure.html)  documentatie van Blender.

### [Grijpen](#grijpen)[](#grijpen)

De Grijp  tool laat je objecten, vertices, edges en faces verplaatsen in de 3D-ruimte, en het is een van de meest essentiële tools voor het positioneren van objecten of meshelementen in een scène. Veel Roblox-makers gebruiken deze tool voor bewerkingsdoeleinden, zoals het positioneren van vertices, edges en faces naar een specifieke studeenheid in de 3D-ruimte.

Om de Grijp-tool te gebruiken:

1.

In Object  of Bewerken  modus, selecteer een of meerdere objecten, vertices, edges of faces.

2.

Druk op G  om de tool te activeren.

3.

Beweeg de muis om je selectie opnieuw te positioneren. Voor verdere precisie:

-

Druk op X , Y  of Z  nadat je op G  hebt gedrukt om de beweging te beperken tot de X , Y  of Z  as, respectievelijk.

-

Druk twee keer op een as-toets om vertices of edges langs hun natuurlijke pad te schuiven.

-

Houd Shift  ingedrukt terwijl je je muis beweegt om de beweging te vertragen voor fijne aanpassingen.

4.

Klik met de linkermuisknop of druk op Enter  om de nieuwe positie te bevestigen.

Voor meer informatie over deze tool, zie de officiële [Verplaatsen](https://docs.blender.org/manual/en/latest/scene_layout/object/editing/transform/move.html)  documentatie van Blender.

### [Snappen](#snappen)[](#snappen)

De Snap  tool laat je objecten en meshelementen uitlijnen door ze aan andere objecten, meshelementen of het raster van de 3D-ruimte te koppelen. Veel Roblox-makers gebruiken deze tool om meerdere objecten nauwkeurig samen te positioneren in de scène, zodat ze kunnen evalueren hoe ze samenwerken in een omgeving, met name met betrekking tot positie, oriëntatie en schaal.

Om de Snap-tool te gebruiken:

1.

In Object  of Bewerken  modus, navigeer naar de header, klik vervolgens op de Snapping  knop. Een contextmenu verschijnt.

 ![Blender's header met de Snapping knop gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Snapping.png)

1.

In het contextmenu,

1.

Stel Snap Basis  in op een van de volgende:

-

Dichtstbijzijnde  - Snapt met behulp van de vertex die het dichtst bij het doel ligt.

-

Midden  - Snapt met behulp van het pivotpunt.

-

Mediaan  - Snapt met behulp van de mediaan van de selectie.

-

Actief  - In Objectmodus snapt deze instelling met behulp van de oorsprong van het actieve element; in Bewerkenmodus snapt deze instelling met behulp van het midden van het actieve element.

2.

Stel Snap Doel  in op een van de volgende:

-

Incrementeel  - Snapt naar rasterpunten vanaf de locatie van de selectie.

-

Raster  - Snapt naar het raster in de 3D-viewport.

-

Vertex  - Snapt naar de vertex die het dichtst bij de muiscursor ligt.

-

Edge  - Snapt naar de edge die het dichtst bij de muiscursor ligt.

-

Face  - Snapt naar de face die het dichtst bij de muiscursor ligt.

-

Volume  - Snapt de selectie naar een diepte die gecentreerd is binnen het object onder de cursor.

-

Edge Midden  - Snapt naar het middelpunt van de edge die het dichtst bij de muiscursor ligt.

-

Edge Perpendicular  - Snapt naar een specifiek punt op de edge zodat de lijn van de oorspronkelijke locatie van de selectie naar de nieuwe locatie loodrecht op die edge staat.

3.

Stel Beïnvloeden  in op een van de volgende:

-

Verplaatsen  - Snapt terwijl je de selectie verplaatst.

-

Roteren  - Snapt terwijl je de selectie roteert.

-

Schalen  - Snapt terwijl je de selectie schaalt.

2.

Druk op Shift Tab  om de tool te activeren.

3.

Voor verdere precisie, houd Shift  ingedrukt om de selectie in fijnere stappen te snappen.

4.

Verplaats, roteer of schaal een object of meshelement volgens je instellingen.

Voor meer informatie over deze tool, zie de officiële [Snappen](https://docs.blender.org/manual/en/latest/editors/3dview/controls/snapping.html)  documentatie van Blender.

### [Inset](#inset)[](#inset)

De Inset  tool laat je een inset maken met aanpasbare dikte en diepte vanuit een face of groep faces. Veel Roblox-makers gebruiken deze tool om uniforme fijne details in hun meshes te creëren terwijl ze een schone randflow voor hun topologie behouden.

Om de Inset-tool te gebruiken:

1.

In Bewerken  modus, selecteer een of meerdere faces.

2.

Druk op I  om de tool te activeren.

3.

Beweeg de muis om de grootte van je inset aan te passen. Voor verdere precisie:

-

Houd Ctrl  ingedrukt om de diepte van de inset aan te passen.

-

Houd Shift  ingedrukt terwijl je je muis beweegt om de beweging te vertragen voor fijne aanpassingen.

-

Druk opnieuw op I  om elke actieve face in te zetten.

4.

Klik met de linkermuisknop of druk op Enter  om je inset(s) te bevestigen.

Voor meer informatie over deze tool, zie de officiële [Inset Faces](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/face/inset_faces.html)  documentatie van Blender.

### [Extrude](#extrude)[](#extrude)

De Extrude  tool laat je nieuwe geometrie creëren door nieuwe faces, edges of vertices uit bestaande geometrie te trekken. Veel Roblox-makers gebruiken deze tool om diepte, volume en complexe vormen te creëren vanuit de primitieve meshes van Blender.

Om de Extrude-tool te gebruiken:

1.

In Bewerken  modus, selecteer een of meerdere vertices, edges of faces.

2.

Druk op E  om de tool te activeren.

3.

Beweeg de muis om de lengte van je extrusie aan te passen. Voor verdere precisie, druk op X , Y  of Z  nadat je op E  hebt gedrukt om de beweging te beperken tot de X , Y  of Z  as, respectievelijk.

4.

Klik met de linkermuisknop of druk op Enter  om je extrusie(s) te bevestigen.

Voor meer informatie over deze tool, zie de volgende officiële Blender documentatie:

-

[Extrude](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/mesh/extrude.html)

-

[Extrude Vertices](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/vertex/extrude_vertices.html)

-

[Extrude Edges](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/edge/extrude_edges.html)

-

[Extrude Faces](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/face/extrude_faces.html)

### [Subdivide](#subdivide)[](#subdivide)

De Subdivide  tool laat je edges of faces in kleinere delen snijden, een proces dat nieuwe vertices en resolutie aan je meshes toevoegt. Veel Roblox-makers gebruiken deze tool om gladde krommingen te creëren, fijne details aan oppervlakken toe te voegen en meshes voor te bereiden voordat ze extra modifiers toepassen.

Om de Subdivide-tool te gebruiken:

1.

In Bewerken  modus, selecteer een of meerdere edges of faces.

2.

Klik met de rechtermuisknop om een contextmenu voor je actieve edges of faces weer te geven, en selecteer vervolgens Subdivide  om de tool te activeren. Het Subdivide-paneel verschijnt.

3.

Stel Aantal Snedes  in op het aantal onderverdelingen dat je wilt voor je edges of faces.

 ![Het Subdivide-paneel met de instelling Aantal Snedes gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Subdivide-Panel.png)

4.

Klik met de linkermuisknop om je onderverdeling(en) te bevestigen.

Voor meer informatie over deze tool, zie de officiële [Subdivide](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/edge/subdivide.html)  documentatie van Blender.

### [Bridge Edge Loops](#bridge-edge-loops)[](#bridge-edge-loops)

De Bridge Edge Loops  tool laat je meerdere edge loops met faces verbinden. Veel makers gebruiken deze tool om gaten te vullen zonder handmatig nieuwe faces te creëren, complexe secties van hun meshes samen te voegen en een schone topologie te behouden voor soepele vervormingen.

Om de Bridge Edge Loops-tool te gebruiken:

1.

In Bewerken  modus, selecteer twee of meer edge loops die je wilt verbinden.

2.

Druk op Ctrl E / ⌘ E  om een contextmenu voor je actieve edge loops weer te geven, en selecteer vervolgens Bridge Edge Loops  om de tool te activeren. Het Bridge Edge Loops  paneel verschijnt.

3.

Stel Aantal Snedes  in op het aantal onderverdelingen dat je wilt voor je nieuwe brug.

4.

OPTIONAL

 Voor verdere precisie voor gebogen bruggen, verhoog Gladheid  om een meer afgeronde brug te creëren.

5.

Klik met de linkermuisknop om je brug te bevestigen.

Voor meer informatie over deze tool, zie de officiële [Bridge Edge Loops](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/edge/bridge_edge_loops.html)  documentatie van Blender.

### [Vul](#vul)[](#vul)

De Vul  tool laat je driehoekige faces creëren tussen actieve edges of vertices, zolang ze een of meer complete omtrekken vormen. Veel Roblox-makers gebruiken deze tool om gaten in hun meshes te sluiten zodat ze waterdicht zijn, of zonder blootgestelde gaten.

Om de Vul-tool te gebruiken:

1.

In Bewerken  modus, selecteer ten minste drie vertices of twee of meer edges die ten minste één complete omtrek vormen.

2.

Druk op Alt F / ⌥ F  om de tool te activeren.

3.

OPTIONAL

 In het Vul  paneel, schakel Schoonheid  in om de driehoeken mooi te rangschikken.

4.

Klik met de linkermuisknop om je nieuwe face te bevestigen.

Voor meer informatie over deze tool, zie de officiële [Vul](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/face/fill.html)  documentatie van Blender.

### [Nieuwe Faces van Edges](#nieuwe-faces-van-edges)[](#nieuwe-faces-van-edges)

De Nieuwe Faces van Edges  tool laat je ofwel een edge creëren als er slechts twee vertices actief zijn, anders creëert het een face tussen de actieve meshelementen. Veel Roblox-makers gebruiken deze tool om veel gaten tegelijk in hun meshes te sluiten zodat de meshes waterdicht zijn, of om geometrie tussen veel solitaire vertices te creëren.

Om de Nieuwe Faces van Edges-tool te gebruiken:

1.

In Bewerken  modus, selecteer ten minste drie vertices, of twee of meer edges die een of meer complete omtrekken vormen.

2.

Druk op F  om de tool te activeren.

3.

Klik met de linkermuisknop om je nieuwe face te bevestigen.

Voor meer informatie over deze tool, zie de officiële [Nieuwe Edge/Face van Vertices](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/vertex/make_face_edge.html)  documentatie van Blender.

### [Verdampen](#verdampen)[](#verdampen)

De Verdampen  tool laat je geometrie verwijderen zonder gaten in je meshes achter te laten. Veel Roblox-makers gebruiken deze tool om hun 3D-kunst te optimaliseren, geometrie samen te voegen of onnodige meshelementen te verwijderen terwijl ze de algehele structuur van de mesh behouden.

Om de Verdampen-tool te gebruiken:

1.

In Bewerken  modus, selecteer de vertices, edges of faces die je uit je mesh wilt verwijderen.

2.

Klik met de rechtermuisknop om een contextmenu voor je actieve meshelementen weer te geven, en selecteer vervolgens:

1.

Als je selectie uit vertices bestaat, selecteer Verdampen Vertices  om de actieve vertices te verwijderen en hun naburige edges samen te voegen.

2.

Als je selectie uit edges bestaat, selecteer Verdampen Edges  om de actieve edges te verwijderen en de omliggende faces samen te voegen om de omtrek van de edge te behouden.

3.

Als je selectie uit faces bestaat, selecteer Verdampen Faces  om de actieve face(s) te verwijderen en de opening indien nodig met een nieuwe face te vullen.

Voor meer informatie over deze tool, zie de officiële [Verwijderen & Verdampen](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/mesh/delete.html#dissolve)  documentatie van Blender.

### [Verwijderen](#verwijderen)[](#verwijderen)

De Verwijder  tool laat je geometrie volledig uit je meshes verwijderen, waardoor er één of meerdere gaten ontstaan waar geometrie is verwijderd. Veel Roblox-makers gebruiken deze tool in plaats van de Verdampen-tool wanneer ze hun meshes tijdens het iteratieproces willen herstructureren.

Om de Verwijder-tool te gebruiken:

1.

In Bewerken  modus, selecteer de vertices, edges of faces die je uit je mesh wilt verwijderen.

2.

Druk op X  om een contextmenu voor je selectie weer te geven.

3.

Kies een van de volgende menu-items:

1.

Selecteer Vertices  om alle actieve vertices te verwijderen, waardoor alle faces of edges die eraan verbonden zijn worden verwijderd.

2.

Selecteer Edges  om alle actieve edges te verwijderen, waardoor alle faces die de edge ermee delen worden verwijderd.

3.

Selecteer Faces  om alle actieve faces te verwijderen, waardoor alle edges die eraan verbonden zijn worden verwijderd.

4.

Selecteer Alleen Edges en Faces  om alleen de actieve edges en aangrenzende faces te verwijderen.

5.

Selecteer Alleen Faces  om alle actieve faces te verwijderen zonder ook actieve edges in de selectie te beïnvloeden.

Voor meer informatie over deze tool, zie de officiële [Verwijderen & Verdampen](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/mesh/delete.html#delete)  documentatie van Blender.

### [Mirror Modifier](#mirror-modifier)[](#mirror-modifier)

De Mirror modifier  laat je geometrie spiegelen over een of meerdere assen, zodat je symmetrische 3D-kunst met minimale inspanning kunt creëren. Veel Roblox-makers gebruiken deze tool tijdens het modelleren van avatars of architectonische objecten die perfect symmetrisch moeten zijn.

Om de Mirror modifier te gebruiken:

1.

In Object  modus, selecteer het object dat je wilt spiegelen.

2.

Navigeer naar de Eigenschappen-editor , selecteer vervolgens in de navigatie aan de linkerkant het tabblad Modifiers .

 ![Blender's Properties editor met het Modifiers-tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Modifiers-Tab.png)

3.

Klik op de knop Modifier Toevoegen , en voeg de Mirror  modifier toe.

4.

Stel As  in op X , Y  en/of Z  om langs een of meerdere assen te spiegelen.

5.

In Bewerken  modus, wijzig je object of een van zijn meshelementen om je aanpassingen langs een as of meerdere assen te zien spiegelen.

## [Textureringtools](#textureringtools)[](#textureringtools)

Nadat je je 3D-object hebt gemodelleerd, is het tijd om een textuur op je mesh toe te passen, zodat deze extra visuele kenmerken heeft, zoals kleur, diepte en ruwheid via een [textuurkaart](/docs/nl-nl/art/modeling/surface-appearance) . Dit zijn details die modellering alleen niet kan bieden, waardoor je object verandert van een blanco vorm naar iets dat er realistisch of gestileerd uitziet, afhankelijk van de kunstvereisten van je spel.

![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/NoTexture.png) Model zonder textuur

![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/WithTexture.png) Model met textuur

Elke van de volgende secties beschrijft hoe je elke tool kunt gebruiken voor ofwel UV-bewerking of vertexverfobjecten, de sneltoetsen die je kunt gebruiken om de tool te activeren, en hun meest voorkomende gebruikstoepassingen voor het textureren van 3D-kunst voor het Roblox-platform.

### [UV-bewerking](#uv-bewerking)[](#uv-bewerking)

UV-bewerking is het proces van het unwrappen van de faces van je 3D-object en het mappen ervan op een 2D-afbeeldingstextuur. Dit proces stelt je in staat om een enkele textuur te gebruiken om visuele kenmerken op meerdere objecten in Blender toe te passen, waardoor je een negatieve impact op het geheugen in Studio bespaart. Bijvoorbeeld, de volgende deurframe-, plafond- en kaartlezer-meshes in de [Laser Tag](/docs/nl-nl/resources/templates#laser-tag)  template gebruiken allemaal dezelfde UV-kaart om metalen versieringen toe te voegen.

![Een deur met trim sheet texturen toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Doorway.jpg)

![Een groep plafondtegels met trim sheet texturen toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Ceiling.jpg)

![Een futuristische kaartlezer met trim sheet texturen toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Reader.jpg)

De "UV" in UV-bewerking staat voor de assen op de 2D-afbeeldingskaart die je gebruikt tijdens het mappen:

-

U-as - De horizontale positie (beweging naar links en rechts).

-

V-as - De verticale positie (beweging omhoog en omlaag).

Omdat 3D-objecten de X-, Y- en Z-assen in de 3D-ruimte gebruiken, gebruiken 3D-creatieapplicaties doorgaans U en V om verwarring te voorkomen bij het verwijzen naar coördinaten in 2D-afbeeldingsruimte. Dat gezegd hebbende, gebruiken veel Blender UI-werkstromen nog steeds X en Y, dus het is nuttig om de equivalente as in 2D-ruimte te kennen.

Wanneer je een 3D-object unwrapt, worden alle actieve faces in de 2D-ruimte in de UV-editor afgevlakt om de UV-kaart  te vormen, en verschillende secties van het model splitsen in afzonderlijke groepen, vaak aangeduid als UV-eilanden . Bijvoorbeeld, als je een standaard Blender-kubus zou unwrappen, zou elke face zijn eigen UV-eiland in de UV-kaart worden.

![Een UV-kaart van een 3D-kubus.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/CubeMap.png) UV-kaart in de UV-editor

![De 3D-kubus die wordt unwrapt.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/UV-Cube.png) Kubus in de 3D Viewport

Elk punt, lijn en face in de UV-kaart komt overeen met een vertex, edge en face in de mesh. Dit betekent dat wanneer je UV-eilanden naar verschillende delen van de textuur verplaatst, hun overeenkomstige vertices, edges en faces worden bijgewerkt om het gebied van de textuur weer te geven dat ze nu overlappen.

Blender maakt vaak UV-eilanden langs naden , of verbonden edges, om vervorming te minimaliseren en het gemakkelijker te maken om je textuur toe te passen. Hoewel deze standaardconfiguratie van UV-eilanden een geweldige plek is om te beginnen, is het bijna altijd noodzakelijk om de positie, oriëntatie en schaal van elk eiland aan te passen om het gebied van de textuur te overlappen dat je wilt projecteren, of om je eigen naden te markeren om je te concentreren op het textureren van specifieke gebieden tegelijk.

Door de tijd te investeren om je UV-eilanden te unwrappen, te rangschikken en te mappen, kun je de kwaliteit van je textuur verbeteren en het rekken of vervormen van al je 3D-kunst verminderen. De volgende subsections benadrukken de meest voorkomende tools voor dit proces, specifiek met betrekking tot het unwrappen en mappen van je objecten.

Voor meer hoog-niveau informatie over dit proces, zie de officiële [UV-editor](https://docs.blender.org/manual/en/latest/editors/uv/introduction.html)  en [Aan de slag met UV's](https://docs.blender.org/manual/en/latest/modeling/meshes/uv/unwrapping/introduction.html#getting-started)  documentatie van Blender.

#### [Naad Markeren](#naad-markeren)[](#naad-markeren)

De Naad Markeren  tool laat je handmatig een UV-kaart van een 3D-object in kleinere, beheersbare secties opsplitsen. Hoewel deze stap in het unwrap-proces technisch optioneel is, vinden veel Roblox-makers het nuttig om zich te concentreren op verzamelingen van gerelateerde faces voor complexe objecten die veel gedetailleerd textuurwerk vereisen.

Bijvoorbeeld, het volgende klinknagelpistool vereist een metalen textuur voor de loop, en een leren textuur voor de grip. Om het gemakkelijker te maken om dit object te textureren, kun je de naden van de grip markeren, alleen de faces tussen die naden unwrappen, en deze vervolgens mappen naar een leren textuurafbeelding.

![Een UV-kaart van een grip op een klinknagelpistool.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/MS-UVMap-Gun.png) Grip UV-kaart in de UV-editor

![De gemarkeerde naden en ingesloten faces op het klinknagelpistool die worden unwrapt.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/MS-Seams-Gun.png) Gemarkeerde naden in de 3D Viewport

Om de Naad Markeren-tool te gebruiken:

1.

Open de UV-bewerking  werkruimte. De UV-editor wordt aan de linkerkant van het scherm weergegeven, en de 3D-viewport wordt aan de rechterkant van het scherm in Bewerken-modus weergegeven.

2.

Navigeer in de 3D Viewport  naar je 3D-object, selecteer vervolgens de edges waar je naden wilt creëren.

3.

Druk op Ctrl E / ⌘ E  om het Edge  contextmenu te openen.

4.

Selecteer Naad Markeren . De naad wordt rood en is klaar voor de Unwrap-tool.

Wanneer je klaar bent om je object te unwrappen, zal Blender de ingesloten faces van de naad als zijn eigen eiland unwrappen.

Voor meer informatie over deze tool, zie de officiële [Naden](https://docs.blender.org/manual/en/latest/modeling/meshes/uv/unwrapping/seams.html)  documentatie van Blender.

#### [Unwrap](#unwrap)[](#unwrap)

De Unwrap  tool laat je de UV-kaart van alle gemarkeerde naden of actieve faces van een 3D-object unwrappen en opschonen, zodat je een solide basis van UV-eilanden hebt om mee te werken. Dit kan snel UV-coördinaten van een complete chaos naar iets beheersbaars brengen.

Veel Roblox-makers gebruiken deze tool voor complexe vormen waarvoor ze volledige controle nodig hebben bij het toepassen van texturen, zoals personages, kleding en kromme objecten, omdat het snel werkt en rekken en vervorming vermijdt.

![Een chaotische met ongeorganiseerde eilanden.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/Before-Unwrap.png) Voor het gebruik van de Unwrap-tool

![Een schone UV-kaart met georganiseerde eilanden.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/After-Unwrap.png) Na het gebruik van de Unwrap-tool

Om de Unwrap-tool te gebruiken:

1.

Open de UV-bewerking  werkruimte. De UV-editor wordt aan de linkerkant van het scherm weergegeven, en de 3D-viewport wordt aan de rechterkant van het scherm in Bewerken-modus weergegeven.

2.

Navigeer in de 3D Viewport  naar je 3D-object, selecteer vervolgens ofwel de Naad Markeren  tool om naden te creëren, en/of selecteer de specifieke faces die je wilt textureren.

3.

Druk op U  om het UV-mapping  contextmenu te openen.

4.

Selecteer Unwrap . De UV-eilanden van je selectie worden netjes weergegeven in de UV-editor.

5.

In de UV-editor , verplaats, schaal of roteer UV-eilanden naar de juiste positie, oriëntatie en schaal op je textuur.

Voor meer informatie over deze tool, zie de officiële [UV Operators - Unwrap](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#Unwrap)  documentatie van Blender.

#### [Volg Actieve Vieren](#volg-actieve-vieren)[](#volg-actieve-vieren)

De Volg Actieve Vieren  tool laat je schone en georganiseerde UV-eilanden genereren volgens de UV-coördinaten van een eerder unwrapte actieve face. Dit is bijzonder nuttig voor rasterachtige topologie, zoals wanneer je muren, vloeren of mechanische onderdelen unwrapt met trim sheets.

Veel Roblox-makers gebruiken deze tool om een consistente textuur op gebogen 3D-objecten toe te passen, zoals trottoirs voor spellen of riemen voor accessoires.

Om de Volg Actieve Vieren-tool te gebruiken:

1.

Open de UV-bewerking  werkruimte. De UV-editor wordt aan de linkerkant van het scherm weergegeven, en de 3D-viewport wordt aan de rechterkant van het scherm in Bewerken-modus weergegeven.

2.

Navigeer in de 3D Viewport  naar je 3D-object, unwrap elke face die je wilt textureren met behulp van een actieve face.

3.

OPTIONAL

 Configureer je actieve face.

1.

In de UV-editor , selecteer de face die je als actieve face wilt hebben, druk vervolgens op Alt M / ⌥ M  om het Split  contextmenu te openen.

2.

Selecteer Selectie . De actieve face scheidt van het UV-eiland.

3.

Verplaats, schaal of roteer je actieve face naar de juiste positie, oriëntatie en schaal die je wilt dat andere faces in de UV-kaart volgen.

4.

In de UV-editor , selecteer alle faces die je wilt laten volgen door de actieve face. Zorg ervoor dat je je actieve face als laatste selecteert, zodat Blender weet dat het de lay-out ervan als gids moet gebruiken.

5.

Druk op U  om het Unwrap  contextmenu te openen, selecteer vervolgens Volg Actieve Vieren . Blender past de UV-coördinaten van je selectie aan om de vorm en oriëntatie van de actieve face te volgen.

Voor meer informatie over deze tool, zie de officiële [UV Operators - Volg Actieve Vieren](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#follow-active-quads)  documentatie van Blender.

#### [Projectie](#projectie)[](#projectie)

Projectietools zijn tools die het oppervlak van een 3D-object op het 2D-afbeeldingstextuurvlak projecteren. Elke projectietool controleert hoe de vorm van het object unwrapt en mapt naar de 2D-textuur:

-

Kubusprojectie  - Projecteert de faces van het object op alle zes zijden van een kubus; nuttig voor blokachtige vormen zoals kisten.

-

Sferische projectie  - Projecteert het oppervlak van het object op een bol; nuttig voor ronde vormen zoals ogen.

-

Cilinderprojectie  - Projecteert het object op een cilindrische vorm; nuttig voor buizen, leidingen en ledematen.

-

Projecteer vanuit Weergave  - Projecteert de geselecteerde faces van het object volgens de huidige camera- of viewporthoek; nuttig voor platte oppervlakken en decals.

-

Slimme UV-projectie  - Unwrapt automatisch het model en genereert eilanden volgens een bepaalde hoek tussen faces.

Het is nuttig om te overwegen hoe je projectietools kunt gebruiken om tijd te besparen in het textureringsproces, vooral voor eenvoudige objecten die repetitieve texturen vereisen. Veel Roblox-makers gebruiken deze tools strategisch om efficiënt UV-eilanden voor basis geometrische vormen te creëren zonder naden van edges te hoeven markeren.

![Een UV-kaart met behulp van Slimme UV-projectie.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/SmartUVProject.png) Een UV-kaart met behulp van Slimme UV-projectie.

![Een UV-kaart met behulp van Kubusprojectie.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/CubeProjection.png) Een UV-kaart met behulp van Kubusprojectie.

Om een projectietool te gebruiken:

1.

Open de UV-bewerking  werkruimte. De UV-editor wordt aan de linkerkant van het scherm weergegeven, en de 3D-viewport wordt aan de rechterkant van het scherm in Bewerken-modus weergegeven.

2.

Navigeer in de 3D Viewport  naar je 3D-object, selecteer vervolgens elke face.

3.

Druk op U  om het UV-mapping  contextmenu te openen, selecteer vervolgens een van de volgende opties:

-

Kubusprojectie

-

Sferische projectie

-

Cilinderprojectie

-

Projecteer vanuit Weergave

-

Slimme UV-projectie

Voor meer informatie, zie de volgende officiële Blender documentatie:

-

[Kubusprojectie](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#cube-projection)

-

[Sferische projectie](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#sphere-projection)

-

[Cilinderprojectie](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#cylinder-projection)

-

[Projecteer vanuit Weergave](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#project-from-view)

-

[Slimme UV-projectie](https://docs.blender.org/manual/en/latest/modeling/meshes/editing/uv.html#smart-uv-project)

### [Vertexverf](#vertexverf)[](#vertexverf)

Vertexverf is het proces van het opslaan van kleurinformatie direct op de vertices van je 3D-object in plaats van via traditionele texturen of materialen. In deze benadering houdt elke vertex kleurgegevens vast die Blender over de faces van een mesh interpoleert, waardoor ofwel soepele overgangen of solide kleurblokken ontstaan zonder de noodzaak voor UV-mapping of afbeeldings texturen.

Vertexverf is nuttig voor het toevoegen van kleurvariatie aan je assets op een lichte, efficiënte manier, vooral in gestileerde werkstromen of spellen waar prestaties een zorg zijn, omdat het het gebruik van textuurgeheugen en draw calls kan verminderen. Veel Roblox-makers gebruiken vertexverf in combinatie met de standaardmaterialen van Studio, [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  objecten, en [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten om visuele complexiteit te creëren op anders eenvoudige 3D-objecten.

![Een raketwerperobject in Blender zonder kleur.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/VP-NoColor.png) Object zonder kleur

![Een raketwerperobject in Blender met vertexverf op de handgreep.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/VP-WithColor.png) Object met vertexverf

![Een raketwerperobject in Studio met vertexverf en een SurfaceAppearance textuur](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/VP-WithTexture.png) Object met vertexverf en afbeeldings textuur

Om vertexverf te gebruiken:

1.

Voeg een kleurattribuut toe om kleurinformatie op te slaan in de vertices van je object.

1.

Selecteer in de 3D Viewport  je 3D-object.

2.

Navigeer naar de Eigenschappen-editor , selecteer vervolgens in de navigatie aan de linkerkant het Gegevens -tabblad.

 ![Blender's Properties editor with the Data tab highlighted.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Data-Tab.png)

3.

Klik op het dropdownmenu Kleurattributen  om de container uit te vouwen, klik vervolgens op de + -knop. Het contextmenu Kleurattribuut toevoegen  wordt weergegeven.

4.

Stel Domein  in op Vertex , Gegevenstype  op Kleur , en klik vervolgens op de Toevoegen -knop. Je object heeft nu een kleurattribuut.

2.

Configureer de 3D Viewport om je kleurattribuut weer te geven.

1.

Navigeer in de 3D Viewport  naar de opties voor Viewport Shading  in de rechterbovenhoek, en klik vervolgens op de knop voor de Solid -schaduwmodus.

 ![Blender's Viewport Shading options with the Solid shading mode highlighted.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/ViewportShading-Solid.png)

2.

Klik op de dropdownpijl van Viewport Shading , en stel in het contextmenu Kleur  in op Attribuut . De 3D Viewport wordt bijgewerkt om je kleurattribuut op je object weer te geven.

 ![Blender's Viewport Shading dropdown menu with the dropdown arrow and Color settings highlighted.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/blender/ColorAttribute.png)

3.

Selecteer een kleur voor je penseel.

1.

Navigeer in de Vertex Paint -modus naar de linkerbovenhoek en klik op de actieve kleurstaal. Een contextmenu wordt weergegeven.

2.

Selecteer je kleur op het kleurenwiel, of met een RGB-, HSV- of Hex-code.

 ![Blender's active swatch UI highlighted.](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/ActiveSwatch.png)

4.

Pas kleur toe op je object.

1.

Om kleur toe te passen op individuele vertices:

1.

Klik en sleep in de 3D Viewport  over de vertices van je object om je kleur met een vloeiende gradient toe te passen.

2.

Voor meer precisie, druk op [ of ]  om de penseelgrootte respectievelijk te vergroten of te verkleinen.

2.

Om je kleur te vullen,

1.

Selecteer in de Bewerk -modus de vertices of vlakken waarop je je kleur wilt toepassen.

2.

Druk in de Vertex Paint -modus op Ctrl X / ⌘ X . Je geselecteerde vertices of vlakken tonen de nieuwe kleur.

Voor meer informatie over dit proces, zie de officiële [Vertex Paint](https://docs.blender.org/manual/en/latest/sculpt_paint/vertex_paint/index.html)  documentatie van Blender.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
