<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/dynamic-heads/caging-best-practices -->

Beste praktijken voor dynamische hoofdkooi | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Beste praktijken voor dynamische hoofdkooi

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende informatie is van toepassing op karaktercreators die hun karakter hoofdkooien willen verbeteren of fouten willen oplossen. Dit verbetert de compatibiliteit met Marketplace-items, zoals accessoires en make-up.

De dynamische hoofdkooi van een karakter helpt de oppervlakte van het 3D-model te definiëren. De kooi speelt ook een belangrijke rol in de Marketplace [hoofdvalidatie](/docs/nl-nl/avatar/dynamic-heads/validate) , dus het is belangrijk om kooien goed te construeren om een nauwkeurige pasvorm met hoofdaccessoires en animaties te garanderen.

De volgende informatie en voorbeelden zijn beste praktijken die van toepassing zijn op gezichtkooien en andere kooiprocessen. Voor aanvullende beste praktijken voor kooien, zie [Beste praktijken voor gelaagde accessoirekooien](/docs/nl-nl/avatar/layered-accessories/caging-best-practices) .

## [Algemeen](#algemeen)[](#algemeen)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Primary-A.png) Referentie voor realistisch gezichtmodel

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Primary-B.png) Referentie voor realistische gezichtmodelkooi

### [Gelijkmatige geometrie](#gelijkmatige-geometrie)[](#gelijkmatige-geometrie)

Probeer de geometrie zoveel mogelijk gelijkmatig te houden. Dit helpt om vervorming van texturen en gelaagde accessoires te verminderen. Houd er rekening mee dat dit niet altijd mogelijk is.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Equidistant-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Equidistant-B.png)

### [Vertex gekleurde gebieden](#vertex-gekleurde-gebieden)[](#vertex-gekleurde-gebieden)

Het sjabloonbestand bevat vertexkleuren in de kooien op belangrijke gebieden. Het uitlijnen van vertex gekleurde gebieden met de lippen, wenkbrauwen en haarlijn helpt om een goede overdracht van make-up te garanderen en daarnaast voor haar, gezichtshaar, wenkbrauwen of wimpers accessoires.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Vertex-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Vertex-B.png)

### [Belangrijke niet-vertex gekleurde gebieden](#belangrijke-niet-vertex-gekleurde-gebieden)[](#belangrijke-niet-vertex-gekleurde-gebieden)

Lijn gebieden die niet zo duidelijk gedefinieerd zijn uit met de neus, ogen en oren om een goede overdracht van make-up en de pasvorm van haar, gezichtshaar, wenkbrauwen en wimperaccessoires te garanderen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Non-Vertex-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Non-Vertex-B.png)

### [Middenas op oorsprong](#middenas-op-oorsprong)[](#middenas-op-oorsprong)

Probeer het indien mogelijk op de oorsprong te houden. Dit zorgt voor enige consistentie in het midden.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Middle-axis.png)

### [Lijn de nekkooi uit](#lijn-de-nekkooi-uit)[](#lijn-de-nekkooi-uit)

Kooi-onderdelen moeten uitgelijnd zijn met de render mesh-objecten. Dit hoeft niet exact te zijn, maar moet wel dicht in de buurt komen. Dit zorgt ervoor dat HSR (Hidden Surface Removal) de onderliggende oppervlakte nauwkeurig kan verbergen wanneer gelaagde accessoires bovenop worden gedragen.

Dit is niet iets waar je je zorgen over hoeft te maken als je auto-setup gebruikt, maar het kan helpen bij het oplossen van problemen rond de nek. Houd er rekening mee dat HSR is uitgeschakeld op het hoofd, maar niet op het lichaam waar de nek aanhecht.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Neck-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Neck-B.png)

### [Kooi moet de render mesh nauwelijks bedekken](#kooi-moet-de-render-mesh-nauwelijks-bedekken)[](#kooi-moet-de-render-mesh-nauwelijks-bedekken)

De kooi moet dicht bij de render mesh zijn zonder deze daadwerkelijk te snijden. Omdat de kooi een andere topologie en lagere resolutie heeft dan je render mesh, kan dit moeilijk zijn. Dit helpt met de pasvorm van gelaagde accessoires en met de nauwkeurigheid van de make-upoverdracht.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Tight-Cage-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Tight-Cage-B.png)

## [Ogen](#ogen)[](#ogen)

### [Bepaal het binnenste en buitenste oog](#bepaal-het-binnenste-en-buitenste-oog)[](#bepaal-het-binnenste-en-buitenste-oog)

Je zou drie vertices voor het bovenste ooglid en drie vertices voor het onderste ooglid moeten hebben, en ze moeten gelijkmatig van elkaar verwijderd zijn.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eye-Inner.png)

### [Sluit de kooi af](#sluit-de-kooi-af)[](#sluit-de-kooi-af)

Sluit indien van toepassing de open rand van het ooggedeelte helemaal tot aan de oogmesh.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eye-Enclosed.png)

## [Wenkbrauwen](#wenkbrauwen)[](#wenkbrauwen)

Het is iets gemakkelijker om de vorm van de wenkbrauw te visualiseren met de vertexkleur die in het sjabloon is gegeven. Zodra je het hoofd en de staart van de wenkbrauw hebt vastgesteld, moet je de drie bovenste en onderste vertices gelijkmatig van elkaar plaatsen.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Primary-B.png)

### [Bepaal de hoofd en staart](#bepaal-de-hoofd-en-staart)[](#bepaal-de-hoofd-en-staart)

Het is iets gemakkelijker om de vorm van de wenkbrauw te visualiseren vanwege de vertexkleur. Zodra je het hoofd en de staart van de wenkbrauw hebt vastgesteld, moet je de drie bovenste en onderste vertices gelijkmatig van elkaar plaatsen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eyebrows-head-tail.png)

### [Ontbrekende wenkbrauwen](#ontbrekende-wenkbrauwen)[](#ontbrekende-wenkbrauwen)

Voor ontbrekende wenkbrauwen is het belangrijk om te vertrouwen op basisregels van gezichtsproporties om de plaatsing te bepalen. Houd rekening met stylisatie en gezichtsvorm om te bepalen hoe je ze moet vormen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-Eyebrows.png)

### [Gelaagde kleding wenkbrauwen](#gelaagde-kleding-wenkbrauwen)[](#gelaagde-kleding-wenkbrauwen)

Probeer voor gelaagde wenkbrauwen het vertexgekleurde gebied zo goed mogelijk af te stemmen op de vorm van de wenkbrauw.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eyebrows-Layered-Clothing.png)

### [Gekleurde wenkbrauwen](#gekleurde-wenkbrauwen)[](#gekleurde-wenkbrauwen)

Vergelijkbare regel als voor gelaagde wenkbrauwen, probeer het vertexgekleurde gebied zo goed mogelijk af te stemmen op de vorm van de wenkbrauw. Draagbare wenkbrauwen moeten precies bovenop passen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eyebrows-Textured.png)

## [Mond](#mond)[](#mond)

Omrand de buitenkant en binnenkant van de lippen. Groene vertexkleur moet op de bovenlip staan, en paars op de onderlip met een gelijkmatige afstand.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Mouth.png)

## [Neus](#neus)[](#neus)

De brug van de neus begint bij het binnenste deel van de ogen en eindigt twee vlakken boven de lippen. Probeer dit over het algemeen in het gebied te houden waar de neus zou moeten zijn.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Nose.png)

## [Oren](#oren)[](#oren)

Bepaal de bovenkant van het oor met het driehoekige gedeelte van het oor, de onderkant met de vierkant. Houd de vorm van de haarlijn rond het oor.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Ears-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Ears-B.png)

## [Haarlijn](#haarlijn)[](#haarlijn)

Bepaal vanaf de wenkbrauwen de vorm van het voorhoofd en de haarlijn.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Hairline-A.png)

Als je met bakkebaarden werkt, definieer dan de vorm van de bakkebaarden aan de voorkant en rond de oren en overweeg waar de haarlijn aan de basis van de nek moet eindigen. Dit helpt bepalen hoe gelaagde haaraccessoires op het hoofd passen.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Hairline-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Hairline-B.png)

## [Kooien voorbeelden van andere gezichtstypes](#kooien-voorbeelden-van-andere-gezichtstypes)[](#kooien-voorbeelden-van-andere-gezichtstypes)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Paint-on-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Paint-on-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Creatures-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Creatures-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Inorganic-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Inorganic-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Anthro-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Anthro-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-C.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-D.png)

## [Ontbrekende kenmerken](#ontbrekende-kenmerken)[](#ontbrekende-kenmerken)

Voor gezichten die belangrijke gezichtskenmerken missen, gebruik de volgende richtlijnen. Deze tips zijn mogelijk niet altijd van toepassing, maar ze bieden een goed kader om te begrijpen hoe je gezichten met ontbrekende kenmerken kunt kooien.

-

Het gezicht is horizontaal verdeeld in drie gelijke delen

-

Haarlijn tot wenkbrauwen

-

Wenkbrauwen tot de onderkant van de neus

-

Onderkant van de neus tot de onderkant van de kin.

-

Ogen zijn halverwege het hoofd

-

Ruimte tussen de ogen is ongeveer de breedte van een oog

-

Het hoofd is ongeveer vijf ogen breed

-

Tranen van de ogen lijnen uit met de randen van de neusgaten

-

De hoeken van de mond en de pupillen van de ogen zijn uitgelijnd

-

De onderkant van de oren lijn uit met de onderkant van de neus

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-Regions.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
