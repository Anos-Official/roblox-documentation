<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/layered-accessories/caging-best-practices -->

Beste praktijken voor het omheinen van gelaagde accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Beste praktijken voor het omheinen van gelaagde accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Omheinen is een complex proces dat nodig is om het binnenste en buitenste oppervlak van een gelaagd accessoire te definiëren. Correct omheinde assets stellen je gelaagde accessoires in staat om uit te rekken en in combinatie met elkaar te lagen. Onjuist geconfigureerde omheiningen kunnen leiden tot cosmetische problemen met het uiterlijk en gevoel van je gelaagde accessoire.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-D.png) Een correct geconfigureerde omheining omvat doorgaans een strakke laag van de binnenste omheining, kledingmesh en de buitenste omheining.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-B.png) Het t-shirt rekt en past natuurlijk over een basislichaam.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-C.png) Andere gelaagde accessoires, zoals een jas, moeten zich natuurlijk rekken en passen over een doellichaam en andere omheinde assets.

In extreme gevallen kunnen onjuiste omheiningen de gameplay of sociale elementen op Roblox verstoren. Als je asset onjuiste omheiningen bevat, kan Roblox je verhinderen deze naar de Marketplace te uploaden en kan het bestaande assets met onjuiste omheiningen uit de catalogus verwijderen.

Roblox handhaaft een striktere set validatieregels om de algehele kwaliteit van gelaagde accessoires in de Marketplace te verbeteren.

De volgende [beste praktijken](#beste-praktijken)  en [veelvoorkomende problemen](#veelvoorkomende-problemen)  zijn nuttig voor avatar asset makers van alle niveaus en kunnen de kwaliteit van je gelaagde accessoire creaties verhogen en tijd besparen bij het oplossen van problemen.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Begin altijd met het omheinen van een van Roblox's [geleverde omheining templates](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip) . Deze templates bevatten een binnenste omheining en buitenste omheining met correct ingestelde UV's.

Je moet de UV's van de omheining niet bewerken, omdat dit visuele artefacten zal introduceren.

Wanneer je je gelaagde accessoires omheint, gebruik dan deze belangrijke universele richtlijnen:

-

Elke kledingmesh die zich tussen de binnenste omheining en de buitenste omheining bevindt, zal worden vervormd door het laag systeem. Dit is de typische configuratie voor bijna alle gelaagde accessoire assets.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-D.png) De t-shirt mesh past snugly tussen de binnenste en buitenste omheining.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-B.png) Het correct geconfigureerde t-shirt rekt zich natuurlijk over een doellichaam.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-C.png) Andere gelaagde accessoire assets moeten zich rekken en natuurlijk passen over een doellichaam en alle uitrusting omheinde assets.

-

Je moet de [naamgevingsconventies](/docs/nl-nl/avatar/layered-accessories/specifications#cage-meshes)  voor de geometrie van het gelaagde accessoire en de omheining volgen.

-

Veel omheining problemen beginnen met een onjuiste configuratie van de buitenste omheining. Zie [werken met buitenste omheiningen](#werken-met-buitenste-omheiningen)  voor specifieke details.

-

Wijzig geen gebieden van je omheining die niet gerelateerd zijn aan het gelaagde accessoire dat je omheint. Bijvoorbeeld, wijzig de binnenste of buitenste omheiningen van de onderbenen niet wanneer je een t-shirt omheint.

-

Bekijk eventuele specifieke beste praktijken voor [vormpassende kleding](#omheinen-van-vormpassende-kleding) , [bulky kleding](#omheinen-van-bulky-kleding) , en [kleding met uitsteeksels](#omheinen-van-uitsteeksels) .

-

Als je problemen oplost, bekijk dan [veelvoorkomende problemen](#veelvoorkomende-problemen)  om te helpen bij het identificeren van problematische gelaagde accessoires of specifieke validatiefouten.

### [Werken met buitenste omheiningen](#werken-met-buitenste-omheiningen)[](#werken-met-buitenste-omheiningen)

Zolang de kledingmesh goed past over de binnenste omheining  en onder de buitenste omheining , kun je de buitenste omheining op verschillende manieren bewerken, afhankelijk van het uiteindelijke visuele effect dat je wilt bereiken.

Wanneer je met de buitenste omheining werkt, gebruik dan de volgende richtlijnen waar mogelijk:

-

Verplaats de vertices naar buiten in de richting van de normaal.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/8-Symmetry.png)

-

Houd de buitenste omheining zo dicht mogelijk bij de kledingmesh.

-

Werk zo symmetrisch mogelijk om tijd te besparen.

-

Wijzig de UV's op geen enkele manier.

-

Stapel je vertices niet.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/9-Stacking-Vertices.png) Twee vertices gestapeld direct boven elkaar. Dit zal visuele artefacten introduceren wanneer andere gelaagde accessoires bovenop worden gelegd.

-

Houd het aantal vertices, randen en vlakken precies hetzelfde als toen je begon.

-

Houd de randafstand van je omheining zo gelijkmatig mogelijk.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/10-Even-Spacing-A.png)

Buitenste omheining met gelijke afstand waar mogelijk op de vlakken.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/10-Even-Spacing-B.png)

Buitenste omheining met ongelijke afstand in het torso gebied. Ongelijke omheiningen kunnen visuele artefacten en ongelijke vervormingen creëren.

-

Houd de breeklijnen van je omheining tussen lichaamsdelen zo goed mogelijk uitgelijnd met de positie van de gewrichten. Probeer bijvoorbeeld de elleboog uit te lijnen met de positie van het LowerArm gewricht.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/11-Positioning-Along-Joints.png) Proportionele veranderingen kunnen helpen de kwaliteit van animatie en pose te verbeteren.

### [Omheinen van vormpassende kleding](#omheinen-van-vormpassende-kleding)[](#omheinen-van-vormpassende-kleding)

Vormpassende kleding, zoals t-shirts, yogabroeken, shorts, truien en slanke jassen, zijn het meest voorkomende type gelaagd accessoire.

In dit geval moet de buitenste omheining het gelaagde accessoire volledig omhullen met minimale openingen tussen de binnenste omheining, kledingmesh en buitenste omheining.

-

Verplaats de vertices van de buitenste omheining naar buiten om het gelaagde accessoire volledig te bedekken, terwijl je de silhouet van de kledingmesh zoveel mogelijk behoudt.

-

Verplaats geen vertices van de buitenste omheining die niet bijdragen aan het bedekken van het gelaagde accessoire. Verplaats bijvoorbeeld geen vertices van de buitenste omheining in de onderbenen wanneer het gelaagde accessoire een t-shirt is.

-

Het gehele gelaagde accessoire moet zich bevinden tussen de buitenste en binnenste omheiningen.

### [Omheinen van bulky kleding](#omheinen-van-bulky-kleding)[](#omheinen-van-bulky-kleding)

Bulky kleding, zoals puffy jassen, sweatpants en hoodies, vereisen extra verplaatsing van de vertices van de buitenste omheining om het bulky item te omhullen. De buitenste omheining moet nog steeds het externe oppervlak van een bulky item volledig omhullen.

-

Besteed speciale aandacht aan de richting waarin aangrenzende vertices van de buitenste omheining worden verplaatst.

-

Verplaats zoveel mogelijk in de richtingen van de vertexnormaal.

-

Verplaats vertices die dichtbij elkaar liggen meer of minder in dezelfde richtingen (gladde relatieve verplaatsingen).

-

Vermijd het verplaatsen van vertices die niet bedekt zijn door het gelaagde accessoire, zoals het verplaatsen van vertices in het armgebied als je broeken maakt.

### [Omheinen van uitsteeksels](#omheinen-van-uitsteeksels)[](#omheinen-van-uitsteeksels)

Sommige kledingstukken hebben assets die uitsteken of verder gaan dan de rest van de kleding. Voorbeelden zijn kleding met puffy capuchons, schoudervullingen en spikes.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/12-Protusions-A.png) Zoals alle gelaagde accessoires, moet kleding met uitsteeksels over binnenste omheiningen passen.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/12-Protusions-B.png)

De buitenste omheining onder de puffy capuchon instellen maakt de capuchon zichtbaar, zelfs wanneer andere gelaagde accessoires worden uitgerust.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/12-Protusions-C.png)

De buitenste omheining boven de puffy capuchon instellen zorgt ervoor dat extra gelaagde accessoires zich uitstrekken en de uitsteeksel bedekken, wat vaak ongewenst is.

Om ervoor te zorgen dat het uitgestoken gebied zichtbaar blijft, ongeacht het aantal lagen:

-

Laat het uitgestoken gebied buiten de buitenste omheining. Bewerk anders de buitenste omheining zodat deze onder de gebieden gaat die zichtbaar en ongevormd moeten blijven.

-

Vermijd het verplaatsen van vertices die niet bedekt zijn door het gelaagde accessoire.

## [Veelvoorkomende problemen](#veelvoorkomende-problemen)[](#veelvoorkomende-problemen)

Onjuiste omheining kan verschillende render- en vervormingsproblemen veroorzaken. De volgende veelvoorkomende voorbeelden kunnen helpen bij het diagnosticeren en oplossen van eventuele omheining problemen die je tegenkomt.

### [Ongelijke omheining](#ongelijke-omheining)[](#ongelijke-omheining)

Onverwachte vormen van de buitenste omheining veroorzaken problemen wanneer andere gelaagde accessoires worden uitgerust. Hoewel het gelaagde accessoire correct kan passen op een doellichaam, zullen eventuele extra lagen niet goed rekken en vervormen.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/1-Uneven-Cage-A.png) De buitenste omheining van het zwarte shirt is ingesteld met ongelijke vertices die een golvende omheining oppervlakte produceren.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/1-Uneven-Cage-B.png) Elke gelaagde accessoire die bovenop past, zal visuele artefacten hebben, zelfs als het gelaagde accessoire zelf er goed uitziet.

### [Identieke binnenste en buitenste omheining](#identieke-binnenste-en-buitenste-omheining)[](#identieke-binnenste-en-buitenste-omheining)

Als de binnenste omheining en de buitenste omheining exact hetzelfde zijn, kan het gelaagde accessoire systeem het accessoire niet goed bepalen en kan het niet vervormen of onverwacht vervormen.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/2-Inner-Outer-Identical-A.png) Een voorbeeld van identieke binnenste en buitenste omheiningen.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/2-Inner-Outer-Identical-B.png) Het t-shirt vervormt op een onverwachte manier en faalt om in zijn oorspronkelijke vorm of plaatsing te renderen.

### [Kleding binnen de binnenste omheining](#kleding-binnen-de-binnenste-omheining)[](#kleding-binnen-de-binnenste-omheining)

Elk deel van de kledingmesh dat zich binnen  de binnenste omheining  bevindt, zal visuele artefacten introduceren wanneer het gelaagde accessoire bovenop andere kleding wordt gelaagd. Je moet altijd deze configuratie vermijden.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/3-Clothing-Under-Inner-A.png) De kledingmesh snijdt door en is gepositioneerd binnen de binnenste omheining bij de schouders en buikgebieden.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/3-Clothing-Under-Inner-B.png) Wanneer uitgerust, past het t-shirt niet goed, waardoor de problematische gebieden in de schouders en buik zichtbaar worden.

### [Kleding gedeeltelijk buiten de buitenste omheining](#kleding-gedeeltelijk-buiten-de-buitenste-omheining)[](#kleding-gedeeltelijk-buiten-de-buitenste-omheining)

Elk deel van de kledingmesh dat zich buiten  de buitenste omheining  bevindt, zal niet worden vervormd door het gelaagde systeem. Deze configuratie kan soms opzettelijk zijn voor effect, zoals wanneer [gelaagde accessoires met uitsteeksels worden omheind](#omheinen-van-uitsteeksels) .

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/4-Outer-Not-Fully-Covering-A.png) De buitenste omheining van het t-shirt is gepositioneerd binnen de kledingmesh nabij de buik.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/4-Outer-Not-Fully-Covering-B.png) Wanneer uitgerust, passen gelaagde accessoires niet goed in de aangetaste gebieden.

### [Te grote buitenste omheining](#te-grote-buitenste-omheining)[](#te-grote-buitenste-omheining)

Zorg ervoor dat de opening tussen het gelaagde accessoire en de buitenste omheining niet te groot is. Dit kan ernstige vervormingsproblemen veroorzaken wanneer het wordt gecombineerd met andere gelaagde accessoires.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/6-Oversized-Cage.png)

### [Ingezakte omheining vertices](#ingezakte-omheining-vertices)[](#ingezakte-omheining-vertices)

Wanneer omheining vertices zijn samengevoegd tot één vertex of een klein gebied, zal elke extra laag die bovenop je gelaagde accessoire wordt geplaatst vreemde artefacten hebben nabij het ingezakte gebied.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/9-Stacking-Vertices.png) De meeste 3D-toepassingen kunnen aangeven of vertices direct overlappen

Deze configuratie zal worden afgewezen tijdens de validatie.

### [Omheiningen met ontbrekende ledematen](#omheiningen-met-ontbrekende-ledematen)[](#omheiningen-met-ontbrekende-ledematen)

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/13-Cage-Missing-Parts.png)

De omheining is bedoeld om de vorm van het sjabloonlichaam te volgen dat is gebruikt om je gelaagde accessoire te modelleren. Omheiningen zonder hoofden of ontbrekende ledematen zullen niet goed werken met het gelaagde accessoire systeem.

Deze configuratie zal worden afgewezen tijdens de validatie.

### [Buitenste omheining binnen de binnenste omheining](#buitenste-omheining-binnen-de-binnenste-omheining)[](#buitenste-omheining-binnen-de-binnenste-omheining)

Het instellen van de buitenste omheining binnen de binnenste omheining creëert een gelaagd accessoire dat niet goed kan lagen met andere assets.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/14-Outer-Inside-Inner.png)

Deze configuratie zal worden afgewezen tijdens de validatie.

### [Mesh buiten de buitenste omheining](#mesh-buiten-de-buitenste-omheining)[](#mesh-buiten-de-buitenste-omheining)

Gelaagde accessoires die buiten hun buitenste omheiningen zijn geplaatst, vervormen niet. Als het gelaagde accessoire volledig buiten is, zal het zich gedragen als een rigide accessoire.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/15-Orbitting-Accessory-B.png) Gelaagde accessoires buiten hun omheining meshes worden niet ondersteund.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/15-Orbitting-Accessory-A.png) Zelfs met een correcte hiërarchie, zullen gelaagde accessoires buiten de omheiningen niet vervormen.

Deze configuratie zal worden afgewezen tijdens de validatie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
