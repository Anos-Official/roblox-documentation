<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/facial-animation/create-face-accessories -->

Maak gezichtaccessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Avataritems

# Maak gezichtaccessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze tutorial behandelt geavanceerde onderwerpen.  Voordat je begint, moet je kennis hebben van modelleren, UV-mapping, rigging, animatie en hoe je een karakter in [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview)  instelt.

Gezichtaccessoires zijn een type [gelaagd accessoire](/docs/nl-nl/avatar/layered-accessories)  dat wordt uitgerust op [dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads) . Terwijl het hoofd animeert en emoties toont, rekken en vervormen gezichtaccessoires zoals wenkbrauwen, wimpers of brillen mee met de gelaatsuitdrukkingen van het karakter.

Je kunt een gezichtaccessoire-model maken in externe modelleringsoftware, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) . Bij het maken van een gezichtaccessoire moet je model voldoen aan de volgende vereisten:

-

Het accessoire-model moet voldoen aan de [modelleringseisen](#modelleringseisen)  van Studio.

-

Het model moet worden gekoppeld (Blender) of gebonden (Maya) aan een karakter met een [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerd](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15-rig.

-

Het model moet een binnen- en buitenkooi bevatten.

Om je te helpen aan deze vereisten te voldoen, behandelt deze tutorial de processen van het verbinden van accessoires aan de rigging-armatuur van een Cubie-karakterlichaam uit [Maak basis dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/create-basic-heads) , het toepassen van skinning-gegevens en het toevoegen van kooien aan het accessoire, evenals hoe je het accessoire kunt exporteren voor import in Studio.

Deze tutorial gebruikt [Blender versie 5.2](https://www.blender.org/download/releases/5-2/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Referentiebestanden](#referentiebestanden)[](#referentiebestanden)

De volgende referentiebestanden voor gezichtaccessoires bevatten alle controlepunten door deze tutorial:

Het referentie Cubie karaktermodel is alleen voor educatieve doeleinden. Het voldoet niet aan de technische avatar [lichaamspecificaties](/docs/nl-nl/avatar/character-bodies/specifications)  om klaar te zijn voor de Marketplace.

| Naam | | Beschrijving |
| --- | --- |
| [Cubie-Complete.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx) | | Het complete Cubie referentie karakter, van [Maak basis dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/create-basic-heads) . Dit bestand is klaar voor import in Studio. |
| [Cubie-Cage-Only.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Cubie-Cage-Only.fbx) | | Het volledige lichaam kooimesh van het Cubie referentie karakter. Dit omvat de binnen- en buitenkooi meshes. |
| [Cubie-Eyebrow-Geo.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/CubieEyebrow_Geo.fbx) | | Een zelfstandige wenkbrauwmodel, ontworpen voor het Cubie-model. |
| [Cubie-Eyebrow-Rigged-And-Caged.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Cubie-Eyebrow-Rigged-And-Caged.fbx) | | Het Cubie wenkbrauwmodel, correct gerigged en ingekooid volgens de instructies in deze tutorial. Dit bestand is klaar voor import in Studio. |
| [Cubie-Hawk-Hair.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/CubieHawkHair_Geo.fbx) | | Een haarmodel referentie, ontworpen voor het Cubie-model. |
| [Creating-Face-Accessories-Reference-Files.zip](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Creating-Face-Accessories-Reference-Files.zip) | | Een verzameling van alle verstrekte referentiebestanden. |

## [Modelleringseisen](#modelleringseisen)[](#modelleringseisen)

Deze tutorial gebruikt een eenvoudige wenkbrauwreferentie als demonstratie over hoe je een gezichtaccessoire kunt maken. Als je een ander gezichtaccessoire aan het riggen en inkooien bent, zorg er dan voor dat je accessoire-model voldoet aan de [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  van Roblox, inclusief de vereisten voor [gezichtaccessoires](/docs/nl-nl/avatar/layered-accessories/specifications#gezichtsaccessoires) .

Als je je eigen gezichtaccessoire-mesh maakt, overweeg dan de volgende richtlijnen:

-

Modelleer je gezichtaccessoire-mesh samen met je karakterlichaam model voor de beste resultaten en pasvorm.

-

Probeer, waar mogelijk, de randen van de geometrie van je gezichtaccessoire af te stemmen op de randen/vertices van de onderliggende hoofdtopologie. Dit verbetert de vervorming van het accessoire met het onderliggende hoofdmodel.

-

Sommige accessoires zoals wenkbrauwen kunnen de karaktermodelmesh extruderen of lichtjes overlappen om een bepaalde cosmetische uitstraling te bereiken.

-

Wanneer je werkt met een gezichtaccessoire met meerdere stukken, zoals wenkbrauwen of wimpers, combineer de meshes tot een enkele mesh zodra je klaar bent met modelleren en riggen.

-

Gezichtaccessoire-meshes hoeven geen _Geo  naamgevingsconventie te volgen.

## [Rig de wenkbrauwen](#rig-de-wenkbrauwen)[](#rig-de-wenkbrauwen)

Rigging  is het proces van het verbinden van een mesh met een interne rig, zodat de oppervlakken van de mesh kunnen draaien en bewegen terwijl de gewrichten draaien en bewegen. Je moet je gezichtaccessoire [riggen](/docs/nl-nl/art/modeling/rigging)  aan de botstructuur van een karakterlichaam, zodat het accessoire kan buigen en vervormen met de gelaatsuitdrukkingen van het karakter.

Na het riggen kun je je model skinnen in je modelleringstool, of je kunt skinning-gegevens van je karakter naar het gezichtaccessoire overdragen tijdens runtime met behulp van [Automatische skinningoverdracht](/docs/nl-nl/avatar/automatic-skinning-transfer) .

### [Projectopzet](#projectopzet)[](#projectopzet)

Deze tutorial gebruikt een eenvoudig wenkbrauwmodel en de complete versie van het dynamische hoofdmodel uit [Maak basis dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/create-basic-heads)  in een nieuw Blender-project.

Om je Blender-project op te zetten:

1.

Open een nieuw Algemeen  project in Blender.

2.

Selecteer de standaardvorm, camera en lichten, en druk op Delete .

3.

Importeer [Cubie-Complete](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx) .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Importing-Cubie.png)

4.

Om de werkruimte te vereenvoudigen, verwijder de binnen- en buitenkooi mesh-objecten. Je zult later in de tutorial een volledige lichaam kooi importeren.

5.

Importeer [CubieEyebrow_Geo](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/CubieEyebrow_Geo.fbx) . Indien nodig:

1.

Herpositioneer het accessoire-model op het gezicht.

2.

Verberg de armatuur tijdelijk om de modelplaatsing te verifiëren.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Importing-Eyebrows.png)

### [Koppel accessoire aan armatuur](#koppel-accessoire-aan-armatuur)[](#koppel-accessoire-aan-armatuur)

Nu je het accessoire in je scène hebt, is het tijd om het te verbinden met de rigging-armatuur van het karakter, zodat de gewrichten de wenkbrauwen op de juiste manier kunnen bewegen. Het is aan te raden om te koppelen met automatische gewichten, omdat dit automatisch invloeden op je model toepast, wat je tijd kan besparen tijdens het [skinnen](#skin-de-wenkbrauwen)  proces.

Om je accessoire aan de armatuur te koppelen:

1.

In Object  modus, houd Shift  ingedrukt en klik op CubieEyebrow .

2.

Terwijl je Shift  nog steeds ingedrukt houdt, klik op een van de karaktergewrichten.

3.

Klik met de rechtermuisknop in de viewport en selecteer Parent  > Armature Deform  > With Automatic Weights .

Je kunt koppelen met Lege Gewichten  om geen enkele skinning-invloed op je accessoire-mesh toe te passen, waardoor je meer handmatige controle over het skinningproces hebt. Voor meer informatie, zie de officiële [Automatische Gewichten](https://docs.blender.org/manual/en/latest/animation/armatures/skinning/parenting.html#with-automatic-weights)  documentatie van Blender.

## [Skin de wenkbrauwen](#skin-de-wenkbrauwen)[](#skin-de-wenkbrauwen)

Skinning  is het proces van het toewijzen van welke delen van het oppervlak van de mesh bewegen en draaien met specifieke gewrichten. In veel gevallen kun je het skinningproces voor je accessoire overslaan en in plaats daarvan het [Automatische Skinning Transfer](/docs/nl-nl/avatar/automatic-skinning-transfer)  proces van Studio gebruiken. Alternatief, als je handmatige controle wilt, kun je handmatige skinning toepassen in Blender met hetzelfde proces in [Maak basis dynamische hoofden - Skin gewrichten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#skin-gewrichten) .

Omdat de complete versie van het dynamische hoofdmodel een volledig gerigged en geposeerd hoofd bevat, kun je je accessoire testen op verschillende FACS-poses die zijn opgeslagen op de tijdlijn binnen Blender, en vervolgens je skinning-gegevens indien nodig aanpassen.

## [Voeg kooien toe](#voeg-kooien-toe)[](#voeg-kooien-toe)

Het inkoiingsproces voor gezichtaccessoires is vergelijkbaar met het inkoiingsproces voor gelaagde accessoires en deelt dezelfde modellering- en inkoiingseisen. Nadat je klaar bent met riggen, is het tijd om een volledige binnen- en buitenkooi naar je project te importeren, de kooien te hernoemen en vervolgens de vertices van de Buitenkooi uit te rekken om het accessoire-model met minimale ruimte te bedekken.

Om de wenkbrauwaccessoire in te kooien:

1.

Importeer [Cubie-Cage-Only](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Cubie-Cage-Only.fbx) . Dit omvat een enkele volledige binnen- en buitenkooi mesh voor het Cubie-model.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Importing-Cage.png)

2.

Hernoem de kooien zodat ze beginnen met CubieEyebrow  voor de _InnerCage  en _OuterCage  toevoeging.

3.

In Bewerken  modus, verleng de buitenkooi om over het accessoire te passen met minimale ruimte. Gebruik verschillende materiaal- en weergave-opties om de juiste vertices op de buitenkooi gemakkelijk te manipuleren.

Als je automatische skinningoverdracht gebruikt, kun je ervoor zorgen dat automatische skinningoverdracht alleen op specifieke delen van het accessoire wordt toegepast door onnodige secties van de kooi te verwijderen. Voor meer informatie, zie [Automatische Skinning Transfer - Wijzig karakterkooien](/docs/nl-nl/avatar/automatic-skinning-transfer#wijzig-karakterkooien) .

## [Exporteer je accessoire](#exporteer-je-accessoire)[](#exporteer-je-accessoire)

Exporteer je model wanneer je klaar bent om je accessoire-model in Studio te testen of wanneer je je voorbereidt op de definitieve export. Houd bij het exporteren van gezichtaccessoires rekening met de volgende richtlijnen:

-

Zorg ervoor dat het uiteindelijke accessoire-model voldoet aan de [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  van Roblox, inclusief correct benoemde mesh- en kooi-objecten.

-

Exporteer geen onnodige gegevens, zoals animatiegegevens, of licht- en camera-objecten.

-

Als je PBR-texturen exporteert, volg dan de [textuurspecificaties](/docs/nl-nl/avatar/layered-accessories/specifications#texturen)  van Roblox bij het exporteren van textuurafbeeldingen vanuit je textuursoftware.

Om je gezichtaccessoire te exporteren:

1.

Zorg ervoor dat alleen de accessoire mesh , armatuur object  en kooi meshes  worden geëxporteerd. Verwijder alle andere objecten in de werkruimte. Je kunt snel Geo  en Att  genaamde objecten in je werkruimte filteren om ze snel te verwijderen.

2.

Volg de [exportinstellingen voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/export#blender-exportinstellingen)  en sla het bestand op op je voorkeurslocatie. De uiteindelijke export van de wenkbrauw .fbx  is beschikbaar ter referentie.

## [Test in Studio](#test-in-studio)[](#test-in-studio)

Om je geëxporteerde model in Studio te gebruiken als een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) , gebruik de [Accessoire Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  om het accessoire-object te testen en te genereren. Op dit punt kun je het accessoire aan een humanoïde karakter uitrusten. Als je van plan bent om skinning-gegevens van je karakter naar het accessoire-model over te dragen tijdens runtime, schakel dan ook [automatische skinningoverdracht](/docs/nl-nl/avatar/automatic-skinning-transfer)  in voor je accessoire.

Als je de referenties volgt die in deze tutorial zijn gegeven, past alleen EnabledOverride  de skinningoverdracht in Studio toe, aangezien sommige skinning-gegevens tijdens het [koppelen](#koppel-accessoire-aan-armatuur)  proces op het model zijn toegepast.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
