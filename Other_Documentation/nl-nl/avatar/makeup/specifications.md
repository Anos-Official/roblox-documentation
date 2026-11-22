<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/makeup/specifications -->

Make-up specificaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Make-up

# Make-up specificaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Make-up vereist een specifieke set componenten en configuratiestandaarden om ervoor te zorgen dat het correct wordt weergegeven op avatar gezichten van alle vormen en maten. Voordat je begint met het exportproces, controleer of je make-up voldoet aan de volgende specificaties en richtlijnen voor een goede Studio-compatibiliteit.

Wanneer je klaar bent om je make-up te exporteren, raadpleeg dan alle [exportinstellingseisen](/docs/nl-nl/avatar/makeup/reassign-textures)  voor Blender en Maya.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/specifications)  specificaties.

-

[Stijve accessoire](/docs/nl-nl/avatar/rigid-accessories/specifications)  specificaties.

-

[Gelaagde accessoire](/docs/nl-nl/avatar/layered-accessories/specifications)  specificaties.

## [Algemeen](#algemeen)[](#algemeen)

Als je de beste praktijk [creatieproces](/docs/nl-nl/avatar/makeup#creatieproces)  volgt, zorg er dan voor dat je sjabloonbestand indiening de volgende objecten bevat die correct zijn geconfigureerd en benoemd in hun respectieve derde-partij modellering software:

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Blender-Datamodel.png)

-

Een hoofd mesh-object  en bijbehorend cage mesh-object .

-

Deze twee objecten moeten het voorvoegsel "TransferTarget_" in hun naam bevatten.

-

TransferTexture mesh-objecten  voor elke regio: Ogen , Gezicht , Lippen .

-

Deze drie objecten moeten de volgende naamgevingsconventies volgen.

-

TransferTexture_Ogen_01

-

TransferTexture_Lippen_01

-

TransferTexture_Gezicht_01

-

Voor meerdere regio's, verhoog het achtervoegsel nummer: TransferTexture_Gezicht_02

-

Optionele [wenkbrauwen en wimpers](#wenkbrauwen-en-wimpers) .

De [geleverde Roblox make-up sjabloon hoofd](https://github.com/Roblox/avatar/tree/main/Makeup)  zou al correct geconfigureerd moeten zijn met de juiste objecten en naamgevingsconventies. Om problemen met import te voorkomen, vermijd het hernoemen of verwijderen van het datamodel van het sjabloon hoofd bij het maken van je eigen make-up.

## [Decals en texturen](#decals-en-texturen)[](#decals-en-texturen)

Alle accessoire texturen moeten voldoen aan Roblox's [textuur specificaties](/docs/nl-nl/art/modeling/texture-specifications) , maar make-up texturen bevatten twee extra overwegingen:

-

Er is een limiet van 4K textuur voor [in-game](/docs/nl-nl/avatar/in-experience-creation)  make-up creatie.

-

Er is een limiet van 1K textuur voor make-up die je uploadt naar de [Marketplace](https://www.roblox.com/catalog) .

Voor aanvullende informatie over PBR-texturen, zie [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) .

## [Wenkbrauwen en wimpers](#wenkbrauwen-en-wimpers)[](#wenkbrauwen-en-wimpers)

Wenkbrauwen en wimpers zijn optionele gelaagde accessoires voor make-up looks. Als je ervoor kiest om ze in je creaties op te nemen, moeten ze voldoen aan alle [gelaagde accessoire vereisten](/docs/nl-nl/avatar/layered-accessories/specifications) , met name:

-

Cage-gegevens  - Wenkbrauwen en wimpers hebben elk hun eigen binnen- en buiten-cage nodig.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eye-Accessory-Datamodel.png)

-

Wenkbrauwen en wimpers kunnen ook profiteren van automatische skinning, specifiek met [speciale skinning gewrichten](/docs/nl-nl/avatar/automatic-skinning-transfer#speciale-skinning-overdracht-gewrichten) .

-

Geometriegrootte  - Oogaccessoires mogen de [maximale afmetingen](/docs/nl-nl/avatar/layered-accessories/specifications)  voor hun type activa niet overschrijden.

-

Budgets  - Oogaccessoires mogen niet meer dan 4k driehoeken elk hebben.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
