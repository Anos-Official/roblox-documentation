<!-- Source: https://create.roblox.com/docs/nl-nl/avatar-setup -->

Avatar Setup | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Avatar instellen

# Avatar Setup

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Avatar Setup  helpt het proces van het maken van het avatarpersonage, starre accessoires en gelaagde accessoires te versnellen door aangepaste modellen automatisch om te zetten in avatar-assets. Als je personages en starre/gelaagde accessoires niet alle essentiële componenten hebben voor publicatie op de [Marketplace](https://www.roblox.com/catalog) , kan Avatar Setup het volgende doen voor je 3D-modellen:

-

Rigging  — Voegt een [R15 rigging armature](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  toe aan je lichaamsmodel om beweging en animatie mogelijk te maken.

-

Skinning  — Voegt gewichten en invloeden toe aan verschillende oppervlakken van je mesh, waardoor een organische en natuurlijke flexibiliteit tijdens beweging wordt gegarandeerd.

-

Gezichtsanimatie  — Genereert de FACS-poses, gezichtsrigging, skinning en animatiedata die nodig zijn voor gezichtsanimatie en avatarchat.

-

Caging  — Voegt de vereiste cages toe aan je asset, zodat deze gelaagde accessoires kan ondersteunen.

-

Partitionering  — Scheidt de lichaamsmesh in de juiste 15 lichaamsdelen die nodig zijn voor een avatarpersonage.

-

Creëren van bijlagen  — Voegt de juiste bevestigingspunten toe zodat het personage starre accessoires kan dragen.

 ![Avatar Preview-knop aangegeven in het Avatar-tabblad](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Avatar-Setup.png)

## [Importeer een 3D-asset](#importeer-een-3d-asset)[](#importeer-een-3d-asset)

De [Importer](/docs/nl-nl/studio/importer)  tool stelt je in staat om aangepaste 3D-assets die je hebt gemaakt in externe modelleringstools zoals Blender of Maya rechtstreeks in Studio te importeren. Als je aangepaste 3D-assets niet alle essentiële avatarcomponenten voor de Marketplace bevatten, zal Avatar Setup de ontbrekende componenten toevoegen terwijl het de assets verwerkt.

Om een aangepaste 3D-asset te importeren met de Importer-tool:

1.

Navigeer naar het Home -tabblad en selecteer vervolgens Importeren . Een bestandsbrowser wordt weergegeven.

2.

Selecteer het .fbx , .obj  of .gltf  model dat je wilt importeren. Na een paar momenten opent het Import Preview -venster met een voorbeeld van je asset.

3.

In de sectie Bestand Algemeen , schakel de optie Uploaden naar Roblox  uit. Deze instelling voorkomt dat de asset onmiddellijk wordt opgeslagen in je Toolbox, waardoor ongewenste kopieën van soortgelijke assets worden voorkomen.

4.

OPTIONEEL

 Om een importpreset voor deze workflow te maken,

1.

Klik in de rechterbovenhoek van het Import Preview -venster op de ⋯ dropdown.

2.

Klik in het contextmenu op Opslaan als Nieuw .

5.

Controleer de preview en eventuele [waarschuwingen of fouten](/docs/nl-nl/studio/importer#waarschuwingen-en-fouten)  in je model. Bepaalde waarschuwingen en fouten kunnen vereisen dat je het model opnieuw aanpast in de externe software die je hebt gebruikt om de asset te maken.

6.

Klik op de Importeren -knop om het model aan je werkruimte toe te voegen. Na een moment wordt het weergegeven als een [Model](/docs/nl-nl/reference/engine/classes/Model)  object in het Explorer -venster.

Wanneer je een nieuw model in Studio importeert, voegt het systeem het model toe aan de moderatiewachtrij. Als je model wordt gemodereerd, ontvang je een moderatie-e-mail met een link om in beroep te gaan. Dit beroep kan tot 10 minuten duren om op te lossen.

## [Voer Avatar Setup uit](#voer-avatar-setup-uit)[](#voer-avatar-setup-uit)

Wanneer je project het juiste [Model](/docs/nl-nl/reference/engine/classes/Model)  object in je werkruimte heeft, kun je Avatar Setup uitvoeren om te zien of je 3D-asset aanvullende avatarcomponenten nodig heeft voordat je het kunt publiceren op de Marketplace als een karakterlichaam, starre accessoire of gelaagde accessoire. Avatar Setup ondersteunt de conversie van de volgende 3D-assettypes vanuit een basis [Model](/docs/nl-nl/reference/engine/classes/Model) :

| Assettype | | Invoervoorwerp | | Uitvoervoorwerp |
| --- | --- |
| Avatar karakterlichaam | | [Model](/docs/nl-nl/reference/engine/classes/Model)  met een of meer [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten die voldoen aan de ondersteunde [lichaamsinvoeren](/docs/nl-nl/avatar-setup/auto-setup-requirements#karakterlichamen)  van Avatar Setup. | | [Model](/docs/nl-nl/reference/engine/classes/Model)  die de bijbehorende 15 [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten en andere verwachte [avatarcomponenten](/docs/nl-nl/avatar/character-bodies#componenten-van-het-lichaamsmodel)  bevat. |
| Starre accessoire | | [Model](/docs/nl-nl/reference/engine/classes/Model)  met een of meer [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten die voldoen aan de ondersteunde [starre accessoire-invoeren](/docs/nl-nl/avatar-setup/auto-setup-requirements#starre-accessoires) .

Moet [bundelen](/docs/nl-nl/avatar-setup/auto-setup-requirements#meerdere-assets-bundelen)  met een avatarlichaam [Model](/docs/nl-nl/reference/engine/classes/Model)  voor Avatar Setup. | | [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  die alle verwachte [starre accessoirecomponenten](/docs/nl-nl/avatar/rigid-accessories#componenten-van-stijve-accessoires)  bevat. |
| Gelaagde accessoire | | [Model](/docs/nl-nl/reference/engine/classes/Model)  met een of meer [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten die voldoen aan de ondersteunde [accessoire-invoeren](/docs/nl-nl/avatar-setup/auto-setup-requirements#accessories-and-clothing)  van Avatar Setup.

Kan optioneel [bundelen](/docs/nl-nl/avatar-setup/auto-setup-requirements#meerdere-assets-bundelen)  met een avatarlichaam [Model](/docs/nl-nl/reference/engine/classes/Model)  voor Avatar Setup. | | [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  die alle verwachte [gelaagde accessoirecomponenten](/docs/nl-nl/avatar/layered-accessories#componenten-van-gelaagde-accessoires)  bevat. |
| Meerdere accessoires met één lichaam | | Folder  [bundel](/docs/nl-nl/avatar-setup/auto-setup-requirements#meerdere-assets-bundelen)  met een of meer [Model](/docs/nl-nl/reference/engine/classes/Model)  die voldoen aan de ondersteunde invoeren voor starre accessoires, gelaagde accessoires of avatarlichamen.

Moet [bundelen](/docs/nl-nl/avatar-setup/auto-setup-requirements#meerdere-assets-bundelen)  met een avatar karakterlichaam [Model](/docs/nl-nl/reference/engine/classes/Model)  voor Avatar Setup. | | [Model](/docs/nl-nl/reference/engine/classes/Model)  karakterlichaam en eventuele [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  draagbare items.

Alle gegenereerde assets bevatten verwachte avataritemcomponenten. |

Voor meer gedetailleerde informatie over ondersteunde invoerconfiguraties, zie de individuele assetspecificaties op de [Avatar Setup-vereisten](/docs/nl-nl/avatar-setup/auto-setup-requirements) .

Om Avatar Setup uit te voeren:

1.

Selecteer in het Explorer -venster het model of specifieke meshes van het model. Als je meerdere meshes tegelijk wilt selecteren, breid dan het [Model](/docs/nl-nl/reference/engine/classes/Model)  object uit en houd vervolgens shift ingedrukt terwijl je op de individuele meshobjecten klikt die je wilt verwerken als avatar-assets.

Referentiemodellen

Voor een asset die aan al deze modelvereisten voldoet, download een van de volgende Avatar Setup-sjablonen voor je eigen referentie en testen:

Natuurmeisje

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Archer-Girl-Preview.png)

Een uitgebreide .zip  map van een Avatar Setup-klaar karaktermodel, inclusief starre en gelaagde accessoire-assets en PBR-texturen.

Deze sjabloon is niet compatibel met de traditionele avatarcreatieworkflow.

[Downloaden](https://prod.docsiteassets.roblox.com/assets/art/reference-files/NatureArcherGirl-AutoSetup.zip)

Stijlvolle Man

![](https://prod.docsiteassets.roblox.com/assets/art/resources/StylizedMale-Preview.png)

Een uitgebreide .zip  map van een Avatar Setup-klaar karaktermodel, inclusief het basislichaam en bijbehorende PBR-texturen.

Deze sjabloon is niet compatibel met de traditionele avatarcreatieworkflow.

[Downloaden](https://prod.docsiteassets.roblox.com/assets/art/reference-files/StylizedMale-AutoSetup.zip)

2.

Met het model of de meshes geselecteerd, navigeer naar het Avatar -tabblad en selecteer vervolgens Avatar Setup .

3.

In de sectie Configureer Modellen ,

1.

Stel Preset  in op de juiste categorie.

1.

Als je je assets wilt publiceren op de Marketplace zodat gebruikers ze kunnen kopen en gebruiken in Roblox, selecteer dan Platform Avatar . Deze optie genereert een meer restrictieve setup die nodig is om validatie en moderatie te doorstaan.

2.

Als je je assets wilt uploaden naar je inventaris voor niet-spelerpersonages (NPC's) of startspelerpersonages voor je games, selecteer dan Development Avatar . Deze optie genereert een minder restrictieve setup.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Configure-Models.png)

2.

Stel Type  voor elk asset in op het juiste assettype, zodat het correct beweegt en animeert in de 3D-ruimte.

1.

Voor karakterlichaamgeometrie, selecteer Body .

2.

Voor gelaagde accessoire-assets, selecteer Layered .

3.

Voor starre accessoire-assets, selecteer Rigid .

4.

Voor wenkbrauw- en wimper-assets, selecteer Eye Layered .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Set-Type.png)

4.

OPTIONEEL

 Klik rechtsonder in de hoek op het tandwielpictogram om speciale instellingen voor je karaktermodel te configureren.

1.

Als je karakter een decal voor zijn gezicht heeft en je wilt de conversie van de textuur naar een [dynamisch hoofd](/docs/nl-nl/avatar/dynamic-heads)  inschakelen, schakel dan Behandel gezicht als 2D-decal  in. Dit proces stelt je in staat om je creatieve intentie te behouden terwijl je voldoet aan het Marketplace-beleid dat vereist dat alle avatars dynamische hoofden hebben.

Een decal omzetten in een dynamisch hoofd?

Het proces van het omzetten van een decal in een dynamisch hoofd inferreert oog- en mondgebieden van je bestaande textuur, genereert cages en FACS-gegevens, en map het resultaat op een dynamisch hoofdtemplate. Voor de beste resultaten, bekijk de volgende richtlijnen:

Voer Avatar Setup uit met het lichaam en hoofd van het personage

-

Als je Avatar Setup alleen met het hoofd van het personage uitvoert, zal deze speciale instelling falen.

Controleer of het avatar gezicht naar voren gericht is

-

Voordat je Avatar Setup uitvoert, controleer of het gezicht van je karakter naar voren gericht is en zichtbaar is in de preview. Wanneer je handmatig het gezicht van je karakter positioneert, zorg ervoor dat je Handmatig vooraan uitlijnen  inschakelt in de speciale instellingen van het Avatar Setup-venster.

Verwijder het [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  object

-

Avatar Setup behoudt je huidige gezichtsinstelling telkens wanneer het een [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  object onder het [Head](/docs/nl-nl/reference/engine/enums/BodyPart)  model van je karakter detecteert. Als er een bestaat in je karakter, verwijder het dan voordat je Avatar Setup uitvoert.

Gebruik [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  in plaats van [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureId)

-

Wanneer je alleen [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureId)  of zowel [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureId)  als [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten gedefinieerd hebt voor je avatar, verwijder of vervang de [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureId)  objecten door [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten voor aanzienlijke verbeteringen in textuurkwaliteit bij het renderen.

2.

Als je karakter een [geavanceerde R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  met extra gewrichten bevat, schakel dan Maak R15 met optionele gewrichten  in.

3.

Als je de voorwaartse richting van je karakter handmatig wilt uitlijnen met de negatieve Z-as in de wereldruimte, schakel dan Handmatig Vooruit Uitlijnen  in. Terwijl auto-setup dit automatisch voor je doet, kan het soms falen om de voorkant van je karakter correct te bepalen.

4.

Als je een post-processing stap wilt toevoegen om de uitlijning van de cage van het hoofd van je karakter met het hoofdmodel en zijn gelaatskenmerken aanzienlijk te verbeteren, schakel dan Verbeter gezichts-caging  in. Dit is vooral belangrijk als je van plan bent om [make-up](/docs/nl-nl/avatar/makeup)  met je karakter te gebruiken.

5.

Als je een ontwikkelingsavatar importeert en je wilt de auto-decimatie van invoer-meshes met een resolutie boven de driehoekbudgetten die vereist zijn voor de Marketplace overslaan, schakel dan Verminder het aantal driehoeken  uit.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Gear-Icon.png)

5.

Klik rechtsonder in de hoek op de Instellen -knop.

1.

Als je model auto-setup vereist voor ontbrekende avatarcomponenten, begint de tool met het verwerken van je model. Dit kan enkele minuten duren. Zodra de auto-setup is voltooid, vult de tool je avatarasset in het Avatar Setup-venster in.

2.

Als je model geen auto-setup vereist, vult de tool je avatarasset in het Avatar Setup-venster in.

## [Testtools](#testtools)[](#testtools)

Nadat je je karakter succesvol in het Avatar Setup-venster hebt geladen, kun je verschillende testtools in de zijnavigation van het venster gebruiken om ervoor te zorgen dat je karakter correct beweegt, animeert en starre en gelaagde accessoires draagt.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Testing-Interface.png)

In elk van deze interfaces kun je zien welke items momenteel aan je karakter zijn bevestigd aan de rechterkant van het Avatar Setup-venster. Van hieruit kun je:

-

Items uittrekken  door met de rechtermuisknop op een uitgerust item te klikken en vervolgens Item Uittrekken  te selecteren in het contextmenu.

-

De draagvolgorde instellen  door de verschillende uitgeruste accessoires te slepen en te ordenen.

Als je problemen ontdekt die niet kunnen worden opgelost met de testtools van Avatar Setup, moet je mogelijk je karaktermodel bijwerken met de externe modelleringsoftware die je hebt gebruikt om de asset te maken, en vervolgens het auto-setup proces opnieuw proberen.

### [Controleer Lichaam](#controleer-lichaam)[](#controleer-lichaam)

De Controleer Lichaam  interface bevat verschillende tabbladen om te controleren hoe je karaktermodel animeert, emoteert, starre en gelaagde accessoires draagt, en de huidskleur verandert. Om meer te leren over wat je met deze interface kunt doen, klik door de volgende tabbladen.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Skin-Tone-Selector.png)

Animaties Kleding Accessoires Lichaam

Het Animaties  tabblad laat je testen hoe je karakter animeert en emoteert met behulp van elke [standaardanimatie](/docs/nl-nl/animation/using#standaard-personage-animaties)  die Roblox biedt voor elke avatar, zoals de loop-, sprong- en zwemanimatie.

Als je problemen opmerkt met het lichaam van je karakter terwijl het animeert, kun je ofwel de bewerkingstools van Avatar Setup gebruiken of je favoriete externe 3D-modelleringsapplicatie gebruiken om het rig van je karakter aan te passen totdat de animaties correct worden afgespeeld.

### [Controleer Gezicht](#controleer-gezicht)[](#controleer-gezicht)

De Controleer Gezicht  interface zoomt dichterbij het gezicht van het karakter en stelt je in staat om verschillende gezichtsposes en cosmetica te testen. Om meer te leren over wat je met deze interface kunt doen, klik door de volgende tabbladen.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Test-Face-1.png) Controleer het bereik van gezichtsposes met meerdere gezichtsanimatietests.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Test-Face-2.png) Onverwacht gezichtsanimatiegedrag, zoals vastlopen of artefacten, kan kleine aanpassingen aan de basismesh vereisen en het auto-setup proces opnieuw uitvoeren.

Animaties Lichaam Make-up Accessoires

Het Animaties  tabblad laat je de gezichtsanimaties van je karakter en het bewegingsbereik voor verschillende delen van het gezicht testen, zoals de ogen, wenkbrauwen en mond van het karakter.

Als je problemen opmerkt met de gezichtsuitdrukkingen van je karakter, kun je ofwel de bewerkingstools van Avatar Setup gebruiken of je favoriete externe 3D-modelleringsapplicatie gebruiken om je karakter aan te passen totdat de animaties correct worden afgespeeld.

### [Test in Ervaring](#test-in-ervaring)[](#test-in-ervaring)

Het Test in Ervaring  tabblad start het playtesten van de game met je karaktermodel. Deze knop verwijst naar je actieve [playtestmodus](/docs/nl-nl/studio/testing-modes)  en behoudt de wijzigingen die je aanbrengt in het Avatar Setup-venster.

### [Voeg testitems toe](#voeg-testitems-toe)[](#voeg-testitems-toe)

Naast de testtools in de zijnavigation kun je aangepaste assets aan de testpalette van Avatar Setup toevoegen die actief zijn in je huidige project of via assetID. Voor meer informatie over beide methoden, bekijk de onderstaande tabbladen.

Van Project Via AssetID

Om een aangepast item dat actief is in je huidige project aan de testpalette van Avatar Setup toe te voegen:

1.

Selecteer in het Explorer -venster of de viewport een geldig accessoire of lichaamsdeelasset.

2.

Navigeer in het Avatar Setup -venster naar de Controleer Lichaam  of Controleer Gezicht  interface en klik vervolgens op de plusknop onderaan de selectiekolom aan de linkerkant van het venster. Het item verschijnt in de juiste sectie en subsectie van de interface, zoals Accessoires → Haar.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Add-Object.png)

## [Bewerktools](#bewerktools)[](#bewerktools)

Naast het Avatar Setup-venster kun je de Attachment Tool en Cage Brush van Avatar Setup in de viewport gebruiken om kleine tot gematigde aanpassingen aan de bevestigingspunten en cage van het karakter aan te brengen.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Editing-Tools.png)

### [Attachment Tool](#attachment-tool)[](#attachment-tool)

De Attachment Tool  toont alle bevestigingspunten op het lichaam van het karakter. Wanneer je een bevestigingspunt selecteert, wordt de Verplaats-tool weergegeven, waarmee je de positie van het bevestigingspunt binnen het lichaam van het karakter kunt aanpassen.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Active-Attachment.png)

### [Cage Brush](#cage-brush)[](#cage-brush)

De Cage Brush stelt je in staat om de cage-mesh van het lichaam van je karakter te wijzigen en aanpassingen te maken aan hoe gelaagde accessoires op je karakter passen. De volgende bedieningselementen bieden fijne controle over je cage-bewerkingen:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Cage-Edit-Panel.png)

-

Symmetrische en spiegelbewerkingen langs de X-as.

-

Borstel met radius- en vervalbediening.

-

Visualisatie van borstelverval over de vertices.

-

Mogelijkheid om uitgeruste gelaagde accessoires te verbergen of weer te geven. Gelaagde accessoires worden in realtime bijgewerkt in het voorbeeldvenster van de Avatar Setup  tool.

Grote cage-bewerkingen kunnen vereisen dat je terugkeert naar je externe modelleringstool, je cage-aanpassingen aanbrengt en vervolgens de asset opnieuw exporteert.

## [Publiceer naar de Marketplace](#publiceer-naar-de-marketplace)[](#publiceer-naar-de-marketplace)

De Opslaan -knop opent de Asset Configuratie dialoog, waarmee je de avatar en eventuele accessoire-items naar je inventaris kunt uploaden of alles dat is geconfigureerd als platformavatar-assets naar de Marketplace kunt publiceren.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Save.png)

Bij het publiceren van je assets naar de Marketplace moet je een [uploadvergoeding](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum)  betalen en de moderatie doorstaan om je assets aan de catalogus toe te voegen. Voor aanvullende bronnen over het publicatieproces en de Marketplace, zie het volgende:

-

[Publiceer naar de Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace)

-

[Marketplace vergoedingen en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions)

-

[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
