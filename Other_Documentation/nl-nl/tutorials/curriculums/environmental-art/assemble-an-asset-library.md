<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library -->

Stel een assetbibliotheek samen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Stel een assetbibliotheek samen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het samenstellen van een assetbibliotheek  is het proces van het importeren en configureren van een verzameling assets op een centrale locatie binnen je game voor gemakkelijke toegang en hergebruik. Dit proces kan je aanzienlijke tijd besparen terwijl je je voorbereidt om je omgeving te construeren, vooral als je de waarden van elke asset configureert om de prestaties te verbeteren en het geheugengebruik op mid- tot low-end apparaten te optimaliseren.

Met behulp van het [Environment Art - Assembling](https://www.roblox.com/games/14447787049/Environment-Art-Assembling)  .rbxl  bestand als referentie, laat deze sectie van het curriculum voor milieukunst je zien hoe je een assetbibliotheek samenstelt van je gepolijste assets, inclusief stapsgewijze instructies over:

-

Het maken van aangepaste materialen voor je terrein van je tegelbare texturen.

-

Het maken van SurfaceAppearance-objecten voor je trim sheet en deze toepassen op ongewikkelde meshes in je assetbibliotheek.

-

Het instellen van renderparameters voor je assets om optimale prestaties op alle apparaten te waarborgen.

-

Het omzetten van je assets in pakketten zodat je ze kunt bijwerken en hergebruiken in al je projecten.

Nadat je deze sectie hebt voltooid, leer je hoe je je assetbibliotheek op creatieve manieren kunt gebruiken om de greybox-omgeving te vervangen of om te zetten, en om de laatste hand te leggen aan de algehele 3D-ruimte.

 ![De modulaire en prop kit van het voorbeeld laser tag spel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/Overview.png)

Voordat je begint met het samenstellen van je assetbibliotheek door je tegelbare texturen, trim sheets, modulaire assets en props in Studio te importeren, is het een best practice om al je inhoud te ordenen en te organiseren in een mappenstructuur op basis van hun datatype, zoals trim sheets, decals, modulaire assets en props. Dit kan je een gemakkelijke referentie bieden terwijl je aangepaste materialen en visuele behandelingen maakt.

## [Maak aangepaste materialen](#maak-aangepaste-materialen)[](#maak-aangepaste-materialen)

Studio vertegenwoordigt aangepaste materialen als [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  objecten binnen de [MaterialService](/docs/nl-nl/reference/engine/classes/MaterialService) . Deze [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  objecten hebben vier eigenschappen die de vier tegelbare [textuurkaarten](/docs/nl-nl/art/modeling/surface-appearance#textuurkaarten)  combineren om een hoogwaardig aangepast materiaal met fysieke eigenschappen te creëren:

-

[MaterialVariant.ColorMap](/docs/nl-nl/reference/engine/classes/MaterialVariant#ColorMap)  – Vertegenwoordigt de albedo textuurkaart.

-

[MaterialVariant.MetalnessMap](/docs/nl-nl/reference/engine/classes/MaterialVariant#MetalnessMap)  – Vertegenwoordigt de metalness textuurkaart.

-

[MaterialVariant.NormalMap](/docs/nl-nl/reference/engine/classes/MaterialVariant#NormalMap)  – Vertegenwoordigt de normale textuurkaart.

-

[MaterialVariant.RoughnessMap](/docs/nl-nl/reference/engine/classes/MaterialVariant#RoughnessMap)  – Vertegenwoordigt de ruwheid textuurkaart.

Nadat je de textuurkaarten aan deze eigenschappen hebt geleverd, kun je je nieuwe aangepaste materiaal toepassen op zowel onderdelen, meshes als terrein. Je kunt de voorbeeld textuurkaart .png  bestanden gebruiken of aanpassen om de Lumpy Moss, Flowering Lumpy Moss, Lumpy Moss met stenen en Stones aangepaste materialen binnen de uiteindelijke voorbeeld laser tag omgeving te creëren, of je kunt je eigen ontwerpen gebruiken die je in de vorige sectie van de tutorial hebt gemaakt.

Om [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  objecten voor je tegelbare texturen te maken:

1.

Selecteer in het Venster  ⟩ 3D  menu Materiaal  om de Materiaalbeheerder  te openen.

2.

Selecteer in de Materialen  lijst het basismateriaal dat het meest overeenkomt met je tegelbare textuur. Als je bijvoorbeeld een [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  object voor de Lumpy Moss tegelbare textuur aan het maken bent, kies dan het standaard grondmateriaal zodat het materiaal zijn fysieke eigenschappen erft.

3.

Klik in de bovenste werkbalk op het ⊕  pictogram. Een nieuw [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  wordt weergegeven in het palet met een pictogram in de rechterbenedenhoek dat aangeeft dat het een aangepast materiaal is.

 ![Nieuw MaterialVariant tegel in Materiaalbeheerder met pictogram om een aangepast materiaal aan te geven](https://prod.docsiteassets.roblox.com/assets/studio/material-manager/Custom-Material-Icon.png)

4.

Navigeer in de Inspector  naar de Algemeen  sectie, en hernoem het materiaal zodat het overeenkomt met de naam van je tegelbare textuur.

 ![De Inspector-weergave met de naam van het materiaal gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CustomMaterials-4.jpg)

5.

Klik in de Textuurkaarten  sectie, aan de rechterkant van Kleur , op de Importeren  knop. Een bestandsbrowser wordt weergegeven.

 ![De Textuurkaarten sectie van de Inspector-weergave met de Importeren knop gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CustomMaterials-5.jpg)

6.

Selecteer in de bestandsbrowser het Albedo  textuurkaart .png  bestand voor de overeenkomstige tegelbare textuur, en klik vervolgens op de Openen  knop. De bestandsbrowser sluit, en de nieuwe kleurkaart wordt weergegeven met zijn asset-ID.

7.

Herhaal dit proces voor de Metalness , Normal , en Roughness  textuurkaarten. Het aangepaste materiaal wordt bijgewerkt om de textuurkaarten weer te geven.

![Alle textuurkaarten voor het materiaal Moss_Lumpy_A.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CustomMaterials-7a.jpg)

![Sferisch onderdeel met het materiaal Moss_Lumpy_A toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CustomMaterials-7b.jpg)

8.

Schakel in de Overrides  sectie de Instellen als Override  schakelaar in om ervoor te zorgen dat wanneer je grond op je terrein toepast, Studio dit aangepaste materiaal gebruikt.

 ![De Instellen als Override schakelaar ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CustomMaterials-8.jpg)

9.

OPTIONEEL

 Als je een aangepast materiaal maakt dat een organisch materiaal vertegenwoordigt,

1.

Klik in de Tiling  sectie op de Patroon  dropdown.

2.

Selecteer Organisch  om de uitvoer te randomiseren en zichtbare tegelvorming te verminderen.

 ![De Tiling sectie van de Inspector-weergave met zijn instellingen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CustomMaterials-9.jpg)

10.

Herhaal dit proces voor elke tegelbare textuur die je in je game wilt opnemen.

## [Maak SurfaceAppearance-pakketten](#maak-surfaceappearance-pakketten)[](#maak-surfaceappearance-pakketten)

Studio maakt gebruik van trim sheets binnen [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten die je kunt koppelen aan [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  die UV-gegevens bevatten. Net als bij aangepaste materialen hebben [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten vier eigenschappen die de vier trim sheet textuurkaarten combineren om een hoogwaardige 3D visuele oppervlaktebehandeling te creëren:

[SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  – Vertegenwoordigt de albedo textuurkaart.
 [SurfaceAppearance.MetalnessMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#MetalnessMap)  – Vertegenwoordigt de metalness textuurkaart.
 [SurfaceAppearance.NormalMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#NormalMap)  – Vertegenwoordigt de normale textuurkaart.
 [SurfaceAppearance.RoughnessMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#RoughnessMap)  – Vertegenwoordigt de ruwheid textuurkaart.

Nadat je de textuurkaarten aan deze eigenschappen hebt geleverd, kun je het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object een kind maken van een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met UV-gegevens die naar je trim sheet zijn gemapt, en de UV-gegevens worden automatisch toegepast op de bovenliggende mesh. Om deze reden is het nuttig om het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object een [pakket](/docs/nl-nl/projects/assets/packages)  te maken, zodat je hetzelfde [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object kunt hergebruiken in al je modulaire assets en props. Bijvoorbeeld, de volgende meshes hebben allemaal UV-gegevens die naar dezelfde trim sheet lay-out zijn gemapt die binnen een enkel [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objectpakket wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SAPackages-Intro.jpg)

Je kunt de voorbeeld textuurkaart .png  bestanden gebruiken of aanpassen om een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object te creëren dat de UV-gegevens respecteert voor de voorbeeld modulaire assets en props binnen de uiteindelijke voorbeeld laser tag omgeving, of je kunt je eigen ontwerpen gebruiken die je in de vorige sectie van de tutorial hebt gemaakt die van toepassing zijn op je eigen modulaire assets en props.

Om [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  pakketten te maken die je kunt koppelen aan je modulaire kit en props:

1.

Voeg een SurfaceAppearance  object toe aan [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) .

2.

Selecteer het SurfaceAppearance  object, en selecteer vervolgens in het Eigenschappen  venster de ColorMap  eigenschap. Een pop-up wordt weergegeven.

3.

Klik op de Afbeelding toevoegen...  knop. Een bestandsbrowser wordt weergegeven.

 ![De ColorMap pop-up met de Afbeelding toevoegen knop gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SAPackages-3.jpg)

4.

Selecteer de Albedo  textuurkaart voor de overeenkomstige tegelbare textuur, en klik vervolgens op de Openen  knop. De bestandsbrowser sluit, en de ColorMap  eigenschap wordt bijgewerkt met een nieuwe asset-ID.

5.

Herhaal dit proces voor de MetalnessMap , NormalMap , en RoughnessMap  eigenschappen, waarbij je hun respectieve textuurkaarten uit de bestandsbrowser selecteert.

6.

Klik met de rechtermuisknop op het SurfaceAppearance  object in het Explorer  venster, en selecteer vervolgens Converteren naar Pakket  uit het contextmenu. De Converteren naar Pakket  dialoog wordt weergegeven.

7.

Vul de velden Titel  en Beschrijving  in, stel het eigendom in op jezelf of een groep, en klik vervolgens op de Indienen  knop. Zodra dit is voltooid, verschijnt er een kettingsymbool boven het pictogram van het SurfaceAppearance-object om het als een pakket te identificeren.

 ![Het Surface Appearance pictogram met een kettingsymbool.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SAPackages-7.jpg)

8.

OPTIONEEL

 Selecteer het kind PackageLink  object van het SurfaceAppearance  object, en schakel in het Eigenschappen  venster AutoUpdate  in om het pakket automatisch bij te werken als je wijzigingen aanbrengt in het SurfaceAppearance  object.

## [Importeer modulaire assets en props](#importeer-modulaire-assets-en-props)[](#importeer-modulaire-assets-en-props)

Studio vertegenwoordigt de modulaire assets en props die je importeert als [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten met kind [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  voor elk onderdeel van de asset. Als je bijvoorbeeld een wandsectie met een bovenste trim, onderste trim en wandcomponent importeert, vertegenwoordigt Studio het .fbx  of .obj  bestand als een Wall_Section  [Model](/docs/nl-nl/reference/engine/classes/Model)  met aparte kind Top_Trim , Bottom_Trim , en Wall  [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/Importing-Intro.png)

Met de Importer kun je de voorbeeld modulaire kit en props in Studio importeren voor gebruik in je assetbibliotheek, of je kunt elke asset importeren die je in de vorige sectie van de tutorial hebt ontworpen. Voor meer informatie over de functionaliteit van deze tool, zie [Importer](/docs/nl-nl/studio/importer) .

Om je modulaire assets en props in de game te importeren:

1.

Selecteer in het Bestand  menu Importeren . Een bestandsbrowser wordt weergegeven.

2.

Selecteer een .fbx  bestand voor een modulaire asset of prop.

3.

Controleer de objectpreview en controleer of de importinstellingen correct zijn voor je object.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/Importing-3.jpg)

4.

Controleer eventuele [waarschuwing- of foutmeldingen](/docs/nl-nl/studio/importer#waarschuwingen-en-fouten) .

5.

Klik op Importeren . De asset wordt weergegeven in het Explorer  venster en in de viewport.

6.

Herhaal dit proces voor elke modulaire asset en prop.

7.

Verplaats al je assets naar één gebied van je game nabij je greybox-geometrie. Deze zone is je assetbibliotheek.

## [Pas SurfaceAppearance-gegevens toe](#pas-surfaceappearance-gegevens-toe)[](#pas-surfaceappearance-gegevens-toe)

Wanneer je het proces doorloopt van het onwikkelen van de UV's van een mesh in software voor derden, slaat de software de UV-gegevens op binnen het .fbx  of .obj  bestand van de mesh. Wanneer je die mesh in Studio importeert, behoudt het resulterende [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object die gegevens, maar je moet nog steeds een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object toepassen met textuurkaart eigenschappen van je trim sheet om je trim texturen op de asset weer te geven.

Om [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  textuurkaartgegevens toe te passen op ongewikkelde meshes in je assetbibliotheek:

1.

Klik in het Explorer  venster op je SurfaceAppearance  pakket, en druk op Ctrl D  (⌘ D ) om het te dupliceren.

2.

Maak het duplicaat SurfaceAppearance  pakket een kind van een modulaire asset of een prop. De asset past zijn UV-gegevens toe op de textuurkaarten en toont zijn visuele behandeling.

3.

Herhaal dit proces voor elke modulaire asset en prop.

## [Stel fysica- en renderparameters in](#stel-fysica--en-renderparameters-in)[](#stel-fysica--en-renderparameters-in)

Nu je je assets binnen Studio hebt, is het belangrijk om fysica- en renderparameters in te stellen die ervoor zorgen dat de assets de hoogst mogelijke visuele kwaliteit behouden op apparaten met geheugen- en GPU-beperkingen. Over het algemeen, hoe dichter je je houdt aan de richtlijnen in deze sectie, hoe beter de prestaties van je game. Het is echter belangrijk om zorgvuldig na te denken over de context waarin je van plan bent elke asset binnen de algehele omgeving te plaatsen om ervoor te zorgen dat je je esthetische doelen en gameplayvereisten behoudt.

### [Geankerd](#geankerd)[](#geankerd)

De [BasePart.Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  eigenschap bepaalt of het fysicasysteem van de Roblox Engine de positie van het object beïnvloedt. Wanneer je deze eigenschap inschakelt voor een [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , verwijdert het object uit de fysieke berekeningen van de dynamische simulatie die altijd in de game draait, wat betekent dat het object nooit van positie verandert door de zwaartekracht of botsingen met andere objecten.

Objecten die geen fysica-respons simuleren zijn goedkoper om te renderen omdat ze geen GPU vereisen die nodig is voor die fysica-berekeningen. Wanneer je GPU vrijmaakt, verbeter je de prestaties van je game, vooral op low-end apparaten die GPU moeten besparen voor snelle gameplay. Om deze reden zijn alle  assets, behalve deuren in de uiteindelijke voorbeeld laser tag omgeving, geankerd.

### [KanBotsen](#kanbotsen)[](#kanbotsen)

De [BasePart.CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap bepaalt of het object fysiek kan interageren met andere objecten. Wanneer je deze eigenschap inschakelt voor een [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , is het object ondoordringbaar, en de Roblox Engine houdt er rekening mee in fysica-berekeningen. Deze berekeningen kunnen de prestaties van je game beïnvloeden wanneer er veel objecten zijn die de engine in zijn fysica-berekeningen moet overwegen.

Om een deel van deze impact op de prestaties te verlichten, schakel je deze eigenschap uit voor objecten waarmee de gebruiker nooit zal interageren. Bijvoorbeeld, de uiteindelijke voorbeeld laser tag omgeving schakelt deze eigenschap uit voor alle loof.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SettingParameters-CanCollide.png)

### [KanAanraken](#kanaanraken)[](#kanaanraken)

De [BasePart.CanTouch](/docs/nl-nl/reference/engine/classes/BasePart#CanTouch)  eigenschap bepaalt of [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  en [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  evenementen op het object worden geactiveerd. Wanneer je deze eigenschap inschakelt voor een [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , controleert de Roblox Engine de aanraakstatus van het object om te zien of het een evenement moet activeren of stoppen.

Dit proces gebeurt voor elk enkel frame, wat een aanzienlijke hoeveelheid geheugen kan verbruiken als de engine de aanraakstatus voor veel objecten tegelijk moet controleren. Om een deel van deze impact op het geheugen te verlichten, schakel je deze eigenschap alleen in voor objecten die een evenement moeten activeren.

### [KanQuery](#kanquery)[](#kanquery)

De [BasePart.CanQuery](/docs/nl-nl/reference/engine/classes/BasePart#CanQuery)  eigenschap bepaalt of de Roblox Engine het object in over ruimtelijke query-operaties, zoals raycasting, overweegt. Studio schakelt deze eigenschap standaard in voor elke [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , wat betekent dat de engine controleert of elk object een ruimtelijke query-operatie moet aanroepen. Dit proces vindt plaats voor elk enkel frame, wat een aanzienlijke hoeveelheid geheugen kan verbruiken wanneer de engine deze controles voor veel objecten tegelijk moet uitvoeren.

Om deze reden is het aan te raden om deze eigenschap uit te schakelen voor objecten die de Roblox Engine niet hoeft te overwegen voor ruimtelijke query-operaties. Wanneer je beslissingen neemt over waar je deze eigenschap moet uitschakelen, overweeg dan hoe elke asset de gameplay beïnvloedt. Bijvoorbeeld, de uiteindelijke voorbeeld laser tag omgeving houdt deze eigenschap ingeschakeld voor elke muur in het gebouw omdat de engine rekening moet houden met deze oppervlakken terwijl gebruikers lasers afvuren vanuit hun laser tag wapen. Als de engine deze assets niet in overweging neemt, zou de laser recht door het gebouw schieten alsof het er helemaal niet was.

### [SchaduwWerpen](#schaduwwerpen)[](#schaduwwerpen)

De [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  eigenschap bepaalt of het object een schaduw werpt. Wanneer je deze eigenschap inschakelt voor een [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , berekent de Roblox Engine elke vertexlocatie van het object tijdens runtime, en tekent vervolgens een raycast van de zon naar een van zijn naburige objecten totdat het met een ander object botst om de schaduw te creëren.

Deze berekeningen kunnen een prestatiekost met zich meebrengen, vooral wanneer je veel objecten met geometrische complexiteit hebt. Dit komt omdat objecten met geometrische complexiteit meer polygonen hebben dan objecten die geometrisch eenvoudig zijn, wat betekent dat ze meer vertices hebben die de engine moet berekenen voor de schaduw van het object. Hoe minder polygonen in een object, hoe sneller de operatie en goedkoper de schaduw.

 ![Een wandsectie met weinig polygonen, en een plant met veel polygonen die schaduwen werpt op een witte muur.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SettingParameters-CastShadow1.png)

Schaduwen kunnen een groot gevoel van realisme geven aan objecten met 3D geometrische diepte, dus wanneer je beslist waar je deze eigenschap moet uitschakelen, overweeg dan waar objecten een significante visuele verbetering aan de omgeving bieden, en waar gebruikers het ontbreken van schaduwen zullen opmerken. Bijvoorbeeld, de complexe schaduwen van loof kunnen een groot gevoel van onderdompeling bieden in de buitenruimte waar gebruikers ze waarschijnlijk zullen zien, maar diezelfde onderdompeling is niet nodig voor het loof dat door het plafond piekt waar gebruikers nooit mee zullen interageren.

![Loof dat schaduwen werpt.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CastShadow-Enabled.jpg)[BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  = Ingeschakeld

![Loof dat geen schaduwen werpt.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CastShadow-Disabled.jpg)[BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  = Uitgeschakeld

### [Dubbelzijdig](#dubbelzijdig)[](#dubbelzijdig)

De [MeshPart.DoubleSided](/docs/nl-nl/reference/engine/classes/MeshPart#DoubleSided)  eigenschap bepaalt of beide gezichten of polygonen in de mesh worden gerenderd. Wanneer je deze eigenschap inschakelt voor een vlakke [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , zoals bladeren, haar of stofkaarten, rendert de Roblox Engine beide gezichten of polygonen in de mesh zodat gebruikers de volheid van het object kunnen zien, ongeacht de hoek van waaruit ze naar het object kijken. Bijvoorbeeld, de volgende boombladeren zijn enkelzijdige vlakke meshes, en wanneer je deze eigenschap inschakelt, worden alle bladeren die van de camera afkijken zichtbaar voor de gebruiker.

![Een boom met alle vlakke meshes die naar de camera wijzen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/DoubleSided-Enabled.png)[MeshPart.DoubleSided](/docs/nl-nl/reference/engine/classes/MeshPart#DoubleSided)  = Ingeschakeld

![Een boom met minder bladeren omdat alle vlakke meshes die van de camera afkijken zijn uitgeschakeld.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/DoubleSided-Disabled.png)[MeshPart.DoubleSided](/docs/nl-nl/reference/engine/classes/MeshPart#DoubleSided)  = Uitgeschakeld

Deze eigenschap is nuttig voor het toevoegen van realisme aan je omgeving, maar het komt met een prestatiekost omdat de engine de polygonen van het object twee keer moet renderen: eenmaal voor de richting die naar de camera van de gebruiker kijkt, en opnieuw voor alle meshes die van de camera van de gebruiker afkijken. Om een deel van deze impact op de prestaties te verlichten, schakelt de uiteindelijke voorbeeld laser tag omgeving deze eigenschap alleen in voor loof omdat het een sterke visuele impact heeft voor realisme in de 3D ruimte.

### [Botsingsnauwkeurigheid](#botsingsnauwkeurigheid)[](#botsingsnauwkeurigheid)

De [MeshPart.CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity)  eigenschap bepaalt hoe nauwkeurig de fysieke hitbox van een mesh of unie overeenkomt met de visuele weergave ervan. Standaard rendert deze instelling een hitbox die ruwweg dezelfde is als de polygonale vorm van de mesh, wat betekent dat waar gebruikers met het object botsen vergelijkbaar is met de werkelijke geometrie van de mesh. Bijvoorbeeld, de kasteelmesh in de volgende afbeeldingen heeft een standaard hitbox die bijna overeenkomt met de vorm van zijn geometrie.

![Een grijze kasteelmesh.](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-MeshPart.jpg) Originele Mesh

![Dezelfde kasteelmesh met een kleurrijke hitbox die laat zien waar gebruikers met het kasteel kunnen botsen.](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-Default.jpg) Standaard

Je kunt deze eigenschap op een andere waarde instellen om de precisie van de hitbox van een mesh te verminderen. Bijvoorbeeld, wanneer je deze eigenschap instelt op Hull , vermindert de Roblox Engine aanzienlijk het aantal vertices van de hitbox van de mesh, en wanneer je deze eigenschap instelt op Box , vermindert de engine de hitbox van de mesh tot een kubus die de mesh omringt. Bovendien, als je de precisie van de hitbox van een mesh wilt verhogen, kun je deze eigenschap instellen op PreciseConvexDecomposition  om het aantal vertices in de hitbox te verhogen.

![Dezelfde kasteelmesh met een kubus hitbox die laat zien waar gebruikers met het kasteel kunnen botsen.](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-Box.jpg) Box

![Dezelfde kasteelmesh met een cilindrische hitbox die laat zien waar gebruikers met het kasteel kunnen botsen.](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-Hull.jpg) Hull

![Dezelfde kasteelmesh met een kleurrijke hitbox die laat zien waar gebruikers met het kasteel kunnen botsen. Deze versie toont meer kleurrijke vlakken dan de standaard hitbox.](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-Precise.jpg) PreciseConvexDecomposition

Net als bij [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow) , hoe meer vertices de Roblox Engine moet renderen, hoe hoger de prestatiekost. Om deze reden is het belangrijk om te overwegen hoe je wilt dat gebruikers met elke mesh interageren om te zien of je het aantal vertices dat de engine moet renderen voor de hitbox van de mesh kunt verminderen. In gevallen waar het niet nodig is dat een hitbox nauwkeurig is, stel je deze eigenschap in op Box  of Hull .

Om dit concept te demonstreren, verwijs naar de volgende afbeeldingen die de hitbox van elke mesh van het wandmodel tonen dat een verhoging in hoogte biedt tussen de eerste en tweede verdieping van de uiteindelijke voorbeeld laser tag omgeving. De standaard hitbox voor de hoofdwand heeft veel onnodige geometrie wanneer het alleen een oppervlak hoeft te bieden om te voorkomen dat de gebruiker in die richting beweegt. Als je de eigenschap instelt op Box  voor deze mesh, kun je deze overbodige geometrie verwijderen terwijl je het doel van de hitbox intact houdt.

![Een wandmodel dat een verhoging in hoogte biedt.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CollisionFidelity-WallMesh.jpg) Originele Mesh

![Hetzelfde wandmodel met een kleurrijke hitbox die laat zien waar gebruikers met de wand kunnen botsen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CollisionFidelity-Default.jpg) Standaard

![Hetzelfde wandmodel met een kleurrijke hitbox voor de trim, maar alleen een box hitbox voor de wandmesh.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CollisionFidelity-Box.jpg) Box

Terwijl je deze beslissingen neemt, is het belangrijk om te overwegen hoe het wijzigen van de standaardwaarde gebruikers negatief kan beïnvloeden terwijl ze door je omgeving navigeren. Bijvoorbeeld, als je de eigenschap instelt op Box  voor de trim meshes van het wandmodel, zouden gebruikers met de hitbox botsen als ze proberen te springen in de buurt van de wand. In plaats daarvan stel je deze meshes in op Hull  zodat je het aantal vertices vermindert terwijl je de hitbox dichter bij de vorm van de geometrie van de mesh houdt.

![Een wandmodel met een box hitbox voor de bovenste trim. Omdat de box uitsteekt, kunnen gebruikers onbedoeld met de bovenste trim botsen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CollisionFidelity-BoxTop.jpg) Box

![Hetzelfde wandmodel met een hull hitbox voor de bovenste trim. Omdat de hull hitbox veel dichter bij de bovenkant van het model past, kunnen gebruikers botsingen met de trim vermijden.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CollisionFidelity-Hull.jpg) Hull

Merk op dat het belangrijk kan zijn om een hitbox te hebben die precies overeenkomt met de vorm van je mesh, vooral wanneer je precies wilt controleren hoe gebruikers met de vorm botsen. Bijvoorbeeld, in de uiteindelijke voorbeeld laser tag omgeving is het belangrijk dat gebruikers alleen met de randen van de deurpost botsen en niet met de deurpost zelf, anders zouden ze nooit in of uit een gevechtszone kunnen komen.

 ![Een deurmodel met geoptimaliseerde hitbox meshes.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/CollisionFidelity-Doorway.png)

Om de botsingsnauwkeurigheid in Studio te bekijken, schakel je Botsingsnauwkeurigheid  in vanuit de [Visualisatie-opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van de 3D viewport.

### [RenderNauwkeurigheid](#rendernauwkeurigheid)[](#rendernauwkeurigheid)

De [MeshPart.RenderFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#RenderFidelity)  eigenschap bepaalt het detailniveau van de mesh dat aan de gebruiker wordt weergegeven. Wanneer je deze eigenschap instelt op [Enum.RenderFidelity.Automatic](/docs/nl-nl/reference/engine/enums/RenderFidelity#Automatic) , vermindert de Roblox Engine de nauwkeurigheid van de mesh naarmate de gebruiker verder van de mesh verwijderd is, en wanneer je deze eigenschap instelt op [Enum.RenderFidelity.Precise](/docs/nl-nl/reference/engine/enums/RenderFidelity#Precise) , wordt elke vertex van je mesh precies weergegeven zoals je bedoelt, ongeacht de afstand tussen hen.

Hoe meer objecten de engine precies aan de gebruiker moet renderen vanaf elke afstand, vooral als ze een hoog aantal vertices hebben, hoe hoger de prestatiekost. Om een deel van deze impact op de prestaties te verlichten, stel je deze eigenschap in op [Enum.RenderFidelity.Performance](/docs/nl-nl/reference/engine/enums/RenderFidelity#Performance)  voor objecten met geometrische complexiteit, zoals loof in de voorbeeld assetbibliotheek, omdat ze niet in hun geheel vanaf een afstand hoeven te worden weergegeven voor enige gameplayvereiste. Dit vermindert het aantal polygonen in je game zonder de algehele visuele kwaliteit op te offeren.

## [Zet assets om in pakketten](#zet-assets-om-in-pakketten)[](#zet-assets-om-in-pakketten)

Nu al je modulaire assets in Studio zijn met renderparameters die zijn ingesteld om hun hoge visuele kwaliteit voor alle gebruikers te behouden, is het tijd om ze om te zetten in pakketten. Het is belangrijk om je assets in pakketten om te zetten omdat het je in staat stelt om ze herhaaldelijk te hergebruiken in je huidige game en andere projecten. Bovendien kun je eenvoudig wijzigingen aanbrengen in een pakket die onmiddellijk worden doorgevoerd naar al zijn instanties, wat je veel tijd bespaart in het iteratieproces.

Omdat je [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten al pakketten zijn, worden je [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten genestelde pakketten wanneer je ze in pakketten omzet. Genestelde pakketten stellen je in staat om complexe hiërarchieën van kindobjecten te behouden die je onafhankelijk van het [Model](/docs/nl-nl/reference/engine/classes/Model)  objectpakket kunt wijzigen. Dit geeft je meer controle over de individuele componenten van je assets.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/ConvertingAssets-Intro.png)

Om je modulaire assets en props in pakketten om te zetten:

1.

Klik met de rechtermuisknop op een modulaire asset of een prop in het Explorer  venster, en selecteer Converteren naar Pakket  uit het contextmenu. De Converteren naar Pakket  dialoog wordt weergegeven.

2.

Vul de velden Titel  en Beschrijving  in, stel het eigendom in op jezelf of een groep, en klik vervolgens op de Indienen  knop. Zodra dit is voltooid, verschijnt er een kettingsymbool boven het pictogram van het model om het als een pakket te identificeren.

 ![Het Model pictogram met een kettingsymbool.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/ConvertingAssets-2.png)

3.

Herhaal dit proces voor elke modulaire asset en prop.

Zodra je tevreden bent met de algehele indeling van je assetbibliotheek, kun je verder gaan met het decoreren van de omgeving met je nieuw gepolijste assets, en het configureren van aanvullende elementen van de 3D ruimte om je wereld tot leven te brengen.

[Volgende](/docs/nl-nl/tutorials/curriculums/environmental-art/construct-your-world)[Vorige](/docs/nl-nl/tutorials/curriculums/environmental-art/develop-polished-assets)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
