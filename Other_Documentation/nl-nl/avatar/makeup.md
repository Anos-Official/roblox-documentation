<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/makeup -->

Make-up | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Make-up

# Make-up

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Make-up  is een cosmetisch item dat je kunt aanbrengen op het gezicht van een avatar of niet-speelbaar personage voor extra creatieve expressie, zoals traditionele make-upkunst (bijv. oogschaduw, lippenstift en blush), gezichtsschildering, strijdmarkeringen en camouflage.

Make-up bestaat uit meerdere gespecialiseerde textuurlagen die zijn gebakken in een [Decal](/docs/nl-nl/reference/engine/classes/Decal)  object, en elke textuurlaag bevat een unieke make-upcomponent zoals de lippen of het ooggebied. Spelers kunnen make-up als een set kopen op de [Marketplace](https://www.roblox.com/catalog)  en het aanbrengen als een complete samenhangende look, of individuele make-upcomponenten verwisselen voor andere die passen bij de stijl van hun eigen avatar.

Deze gids behandelt het maken van make-upassets in Studio. Om spelers in staat te stellen make-up direct binnen jouw ervaring te creëren en aan te schaffen tijdens runtime, zie [In-experience creatie voor make-up](/docs/nl-nl/avatar/in-experience-creation-makeup) .

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-FullFace.png) Complete look

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-Eyes.png) Ogen textuurlaag

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-Lips.png) Lippen textuurlaag

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-Face.png) Gezicht textuurlaag

Deze gids biedt verschillende [make-up sjablonen](#bronnen)  die je kunt gebruiken binnen jouw creatieproces, zoals:

-

Sjabloontexturen die je kunt gebruiken in 2D-bewerkingssoftware om make-up te maken.

-

Sjabloonhoofden die je kunt gebruiken om je make-up te bekijken en te testen voordat je exporteert.

-

Referentiespel dat je kunt gebruiken om je make-upassets te importeren en te testen op personages met verschillende huidtinten en lichaamstypes.

Je kunt deze sjablonen gebruiken als een puur referentie om te zien hoe alles werkt, of je kunt ze allemaal gebruiken bij elke stap van het voorgestelde creatieproces.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Full-Render.png) Referentiesjabloon render

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Blender-Datamodel.png) Referentiesjabloon datamodel

## [Make-upcomponenten](#make-upcomponenten)[](#make-upcomponenten)

Je kunt texturen aanbrengen op drie primaire gebieden van het gezicht: het ooggebied, het lipgebied en het gezichtgebied. Elk gebied heeft overlappende oppervlakken met andere gebieden om naadloze, continue looks tussen make-upcomponenten mogelijk te maken.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eyes-Region.png) Ogen gebied

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Lips-Region.png) Lippen gebied

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Face-Region.png) Gezicht gebied

Daarnaast kun je wenkbrauwen en wimpers opnemen in je make-upcreaties. Wenkbrauwen en wimpers zijn [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten die [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten bevatten met skinning- en caging-gegevens. Dit stelt ze in staat om correct te animeren terwijl de gezichtsuitdrukkingen van het personage veranderen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eye-Acc.png) Wenkbrauw- en wimpermeshobjecten

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eye-Accessory-Datamodel.png) Wenkbrauw- en wimperdatamodel

Wanneer je je make-upcreatie importeert vanuit je favoriete derde-partij modellering software in het [referentiespel](#referentiespel) , detecteert Studio automatisch de mesh-namen en genereert vervolgens de benodigde [Decal](/docs/nl-nl/reference/engine/classes/Decal)  objecten onder het geïmporteerde model. Je kunt dan snel je make-up [Decal](/docs/nl-nl/reference/engine/classes/Decal)  objecten en accessoires toepassen door ze van het geïmporteerde referentiehoofd naar de Make-up  of Accessoires  map van een personage te slepen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Imported-DataModel.png) Het geïmporteerde model bevat je make-up decals en gezichtaccessoires

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Character-Folders.png) Je make-up wordt tijdens runtime weergegeven wanneer je je make-upassets in de juiste mappen sleept

Make-upassets die je maakt voor de [Marketplace](https://www.roblox.com/catalog)  kunnen tot 6 totale [Decal](/docs/nl-nl/reference/engine/classes/Decal)  objecten bevatten, bestaande uit elke combinatie van gebieden.

## [Bronnen](#bronnen)[](#bronnen)

De volgende zijn downloadbare bronnen die je kunt gebruiken binnen het creatieproces:

-

Zie [Sjabloontexturen](#sjabloontexturen)  voor afbeeldings- en projectbestanden die je kunt gebruiken in 2D-bewerkingssoftware zoals GIMP of Photoshop.

-

Zie [Sjabloonhoofden](#sjabloonhoofden)  voor vereiste 3D-modellen die je kunt gebruiken om je make-upassets te bekijken en te testen.

-

Zie [Referentiespel](#referentiespel)  om je make-upassets in Studio te importeren en te testen.

Voor bronnen die twee sjablonen bevatten, is het in bijna alle gevallen aanbevolen om de mesh-sjabloon  te gebruiken om make-up te maken omdat:

-

Het is gemakkelijker en intuïtiever te gebruiken omdat het het aanbrengen van make-up in de echte wereld nabootst.

-

Het bevat een mesh van hogere kwaliteit en UV's met minimale vervorming.

Sommige makers geven de voorkeur aan het gebruik van de cage-sjabloon omdat er slechts één overdracht is bij het projecteren van de textuur, terwijl er twee overdrachten zijn voordat de textuur voor de mesh-sjabloon wordt geprojecteerd. Dit kan resulteren in een nauwkeuriger overdragen van make-up met minder artefacten.

Zorg ervoor dat je je opties voordat  je begint met het maken van make-up bekijkt, omdat je niet met het ene sjabloon kunt beginnen en vervolgens je make-up naar het andere kunt overdragen.

### [Sjabloontexturen](#sjabloontexturen)[](#sjabloontexturen)

Wanneer je klaar bent met het aanbrengen van wijzigingen aan een van de volgende sjabloontextuurafbeeldingen:

1.

Exporteer je nieuwe texturen.

Exporteren vanuit Photoshop

De video-presentator gebruikt Bestand  > Exporteren  > Lagen naar Bestanden  om elke laag als zijn eigen .png  bestand te exporteren.

Exporteren vanuit Substance Painter

Exporteren vanuit Procreate

Om texturen vanuit Procreate te exporteren:

1.

Navigeer naar het Lagen  paneel, verberg dan alles behalve je eerste make-upcomponentlaag, zoals je ogen-, lippen- of gezichtlaag.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-ActiveLayer.jpg)

2.

Met je make-upcomponentlaag actief, navigeer naar het Acties  menu > Delen  tab > Deel Texturen - PNG  om alle texturen van je make-upcomponent op te slaan op een locatie op je apparaat.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-ShareTextures.jpg)  ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-AllTextures.jpg)

3.

Verwijder alle hoofd-, wenkbrauw- en wimpertexturen.

1.

Open de locatie waar je alle texturen van je make-upcomponent hebt opgeslagen.

2.

Verwijder alles behalve de volgende PBR-texturen:

-

TransferTarget_FullHead_Mat-Color

-

TransferTarget_FullHead_Mat-Metallic

-

TransferTarget_FullHead_Mat-Roughness

4.

Vervang de TransferTarget_FullHead_Mat-Color  laag van je make-upcomponent door een versie die transparantie in de uitvoertextuur zal exporteren.

1.

Kopieer je actieve make-upcomponentlaag.

2.

Navigeer naar de Galerij  > Plus  icoon > Klembord . Een nieuw Procreate-bestand wordt weergegeven met je make-upcomponentlaag.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-Clipboard.png)

3.

In het Lagen  paneel, schakel de Achtergrondkleur  laag uit. Je make-upcomponent wordt zonder achtergrond weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-HideBackground.png)

4.

Met je make-upcomponentlaag actief, navigeer naar het Acties  menu > Delen  tab > Deel Afbeelding - PNG .

5.

In de bestandsbrowser, navigeer naar de locatie op je apparaat met alle texturen van je make-upcomponent, en sla de TransferTarget_FullHead_Mat-Color  textuur op/overschrijf deze.

5.

Hernoem de PBR-texturen van je make-upcomponent op de juiste manier zodat je gemakkelijk naar de PBR-gegevens van elke make-upcomponent kunt verwijzen wanneer je je texturen opnieuw toewijst in Blender of Maya. Bijvoorbeeld, als je textuurkaarten voor lippen exporteert:

-

Lips-Color

-

Lips-Metallic

-

Lips-Roughness

6.

Herhaal dit proces voor elke make-upcomponent die je wilt importeren voor je make-uplook.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-Final.png)

2.

[Herschrijf de vooraf ingestelde texturen](/docs/nl-nl/avatar/makeup/reassign-textures)  in een [sjabloonhoofd](#sjabloonhoofden)  met je nieuwe texturen.

3.

[Importeer het referentiehoofd](/docs/nl-nl/avatar/makeup/import)  met je nieuwe texturen in Studio.

Photoshop / GIMP textuurafbeeldingen

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Realistic-Cage-Thumbnail.png)

Een uitgebreide .zip  map met realistische textuurafbeeldingen voor gebruik in Photoshop of je favoriete afbeeldingseditor.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Gimp-Realistic-Mesh.zip)

[Cage-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Gimp-Realistic-Cage.zip)

Substance Painter-bestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Substance-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Substance-Realistic-Cage-Thumbnail.png)

Een uitgebreide .zip  map met realistische textuurbestanden voor gebruik in Substance Painter, een industriestandaard PBR-autoriseringssoftware.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/SubstancePainter-Realistic-Mesh.zip)

[Cage-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/SubstancePainter-Realistic-Cage.zip)

Procreate textuurafbeeldingen

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Cage-Thumbnail.png)

Een uitgebreide .zip  map met realistische textuurafbeeldingen voor gebruik in Procreate.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Mesh.zip)

[Cage-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Cage.zip)

Photoshop / GIMP textuurafbeeldingen

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Blocky-Mesh-Thumbnail.png)

Een uitgebreide .zip  map met blokkerige textuurafbeeldingen voor gebruik in Photoshop of je favoriete afbeeldingseditor.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Gimp-Blocky-Mesh.zip)

Substance Painter-bestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Substance-Blocky-Mesh-Thumbnail.png)

Een uitgebreide .zip  map met blokkerige textuurbestanden voor gebruik in Substance Painter, een industriestandaard PBR-autoriseringssoftware.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/SubstancePainter-Blocky-Mesh.zip)

Procreate textuurafbeeldingen

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Blocky-Mesh-Thumbnail.png)

Een uitgebreide .zip  map met blokkerige textuurafbeeldingen voor gebruik in Procreate.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Blocky-Mesh.zip)

### [Sjabloonhoofden](#sjabloonhoofden)[](#sjabloonhoofden)

Elk sjabloonhoofd bevat:

-

Doel hoofdmeshobject of hoofd cage meshobject

-

Oog-, lip- en meerdere gezichtgebied meshobjecten, volledig gekoppeld aan referentie PBR-texturen

-

Wenkbrauw- en wimpermeshobjecten

De Blender- en Maya-sjablonen bevatten ook een referentie .png  bestand van het gezichtgebied dat je kunt gebruiken om te refereren hoe je make-upassets passen in de ogen, lippen en gezicht/wangen gebieden.

Blender sjabloon referentiebestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Cage-Thumbnail.png)

Een uitgebreide .zip  map met Blender-assets, inclusief meerdere realistische referentiehoofden die zijn geconfigureerd voor testen in de Make-up testplaats of voor het maken van je eigen make-up.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Mesh.zip)

[Cage-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Cage.zip)

Maya sjabloon referentiebestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Cage-Thumbnail.png)

Een uitgebreide .zip  map met Maya-assets, inclusief meerdere realistische referentiehoofden die zijn geconfigureerd voor testen in de Make-up testplaats of voor het maken van je eigen make-up.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Mesh.zip)

[Cage-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Cage.zip)

FBX / GLTF sjabloon referentiebestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Fbx-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Fbx-Realistic-Cage-Thumbnail.png)

Een uitgebreide .zip  map van .fbx  en .gltf  assets, inclusief realistische hoofden met verschillende voorbeeld make-uplooks die klaar zijn om in Studio te worden geïmplementeerd voor testdoeleinden.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/FBX-GLTF-Realistic-Mesh.zip)

[Cage-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/FBX-GLTF-Realistic-Cage.zip)

Blender sjabloon referentiebestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Blocky-Mesh-Thumbnail.png)

Een uitgebreide .zip  map met Blender-assets, inclusief meerdere blokkerige referentiehoofden die zijn geconfigureerd voor testen in de Make-up testplaats of voor het maken van je eigen make-up.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Blocky-Mesh.zip)

Maya sjabloon referentiebestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Blocky-Mesh-Thumbnail.png)

Een uitgebreide .zip  map met Maya-assets, inclusief meerdere blokkerige referentiehoofden die zijn geconfigureerd voor testen in de Make-up testplaats of voor het maken van je eigen make-up.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Blocky-Mesh.zip)

FBX / GLTF sjabloon referentiebestanden

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Fbx-Blocky-Mesh-Thumbnail.png)

Een uitgebreide .zip  map van .fbx  en .gltf  assets, inclusief blokkerige hoofden met verschillende voorbeeld make-uplooks die klaar zijn om in Studio te worden geïmplementeerd voor testdoeleinden.

[Mesh-sjabloon](https://prod.docsiteassets.roblox.com/assets/makeup/resources/FBX-GLTF-Blocky-Mesh.zip)

### [Referentiespel](#referentiespel)[](#referentiespel)

Referentieplaatsbestand (download)

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Experience-Thumbnail.png)

Op dit moment kun je alleen make-up testen op het downloadbare plaatsbestand.

In Github, selecteer het downloadpictogram aan de rechterkant om het MakeupBeta.zip  bestand te downloaden.

[Github-link](https://github.com/Roblox/avatar/blob/main/Makeup/MakeupBeta.zip)

## [Creatieproces](#creatieproces)[](#creatieproces)

Dit proces gaat ervan uit dat je bedreven bent in 3D-modelleringssoftware, zoals Blender of Maya, en dat je begrijpt hoe je materialen binnen je modelleringstool en eventuele aanvullende textureringssoftware of plugins kunt bijwerken, vervangen, exporteren, opslaan en wijzigen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Creation-Steps-1.png) Download het 3D referentiesjabloon hoofd en textuursjablonen die van toepassing zijn op jouw workflow.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Creation-Steps-2.png) Wijzig de textuurafbeeldingen in de tools van jouw keuze.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Creation-Steps-3.png) In Blender of Maya, vervang de texturen in het sjabloon door je nieuwe texturen en exporteer.

Hoewel je gemakkelijk [Decal](/docs/nl-nl/reference/engine/classes/Decal)  objecten in Studio kunt verwisselen om een snelle wijziging aan te brengen in de make-up van een personage, is de volgende instructie de beste praktijk voor het implementeren van PBR-gebaseerde texturen in Roblox make-up op grote schaal. Dit proces vereist:

-

De [Make-up testplaats en sjabloonbestanden](#bronnen)

-

Een 3D-modelleringshulpmiddel zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview)

-

Elke PBR textureringssoftware, zoals [Substance Painter](https://www.adobe.com/products/substance3d/apps/painter.html) , [Materialize](http://boundingboxsoftware.com/materialize/index.php) , of plugins zoals [Ucupaint](https://extensions.blender.org/add-ons/ucupaint/)  (Blender).

Zoals altijd met 3D-kunst en creatieworkflows, zijn er veel manieren om een specifiek doel te bereiken, en de make-up en PBR publicatieflow is daarop geen uitzondering. Het wordt aanbevolen om eerst de workflow in deze gids te proberen, en deze vervolgens aan te passen aan jouw eigen creatievereisten:

1.

Download een [referentiesjabloon hoofd](#bronnen)  en open het in de algemene modelleringsoftware van jouw keuze.

2.

Gebruik je textureringshulpmiddelen of afbeeldingsbewerkingssoftware om de textuurafbeeldingen die zijn geassocieerd met de verschillende gebieden te wijzigen: TransferTexture_Eyes , TransferTexture_Face , of TransferTexture_Lips .

3.

Wanneer je je nieuwe textuurafbeeldingen hebt gemaakt, gebruik je Blender of Maya om de bestaande bestandstexturen in het sjabloon opnieuw toe te wijzen. Voor meer informatie, zie [Herschrijf texturen](/docs/nl-nl/avatar/makeup/reassign-textures) .

4.

Bekijk [Beste praktijken voor gezichtscaging](/docs/nl-nl/avatar/dynamic-heads/caging-best-practices)  voor richtlijnen over hoe je gezichtscages kunt aanpassen zodat je make-up correct wordt weergegeven voor jouw gebruiksdoel.

5.

Exporteer het hele sjabloonbestand als een .fbx  of .gltf . Alle 3D-modellerings [exportvereisten](/docs/nl-nl/art/modeling/export-requirements)  zijn van toepassing, maar er zijn een paar make-up specifieke instellingen die je moet configureren:

-

Als je Blender gebruikt,

1.

In het exportbestandbrowservenster, navigeer naar de Inbegrepen  sectie, en schakel de Aangepaste Eigenschappen  schakelaar in voor make-up UV-gegevensoverdracht.

2.

In de Armature  sectie, schakel Alleen Deformeren Botten  in om ervoor te zorgen dat je exportbestand skinninggegevens voor wenkbrauwen en wimpers bevat.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Blender-MakeupExport.png) Alle noodzakelijke Blender exportinstellingen voor make-up

-

Als je Maya gebruikt, navigeer in het exportbestandbrowservenster naar de Gedeformeerde Modellen  sectie, en schakel de Skin  schakelaar in om ervoor te zorgen dat je exportbestand skinninggegevens voor wenkbrauwen en wimpers bevat.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Maya-MakeupExport.png)

6.

[Importeer](/docs/nl-nl/avatar/makeup/import)  het sjabloonbestand in Studio. Studio detecteert automatisch je meshobjectnamen en bijbehorende texturen, en genereert Decal  objecten.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Imported-DataModel.png)

7.

Pas eventuele make-up decals of wenkbrauw- en wimperaccessoires toe op personages in de testplaats door make-upassets in de juiste Make-up  of Accessoires  map van het personage te slepen.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Character-Folders.png)

8.

Klik op de Speel  knop, navigeer vervolgens naar het personage met nieuwe make-upassets om een preview te bekijken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
