<!-- Source: https://create.roblox.com/docs/nl-nl/resources/beyond-the-dark/building-architecture -->

Bouwarchitectuur | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Beyond The Dark](/docs/nl-nl/resources/beyond-the-dark)

# Bouwarchitectuur

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het bouwen van het station op een modulaire manier stelde ons in staat om inhoudsupdates soepel bij te werken en te verspreiden, en het was essentieel om ervoor te zorgen dat we geen uren besteedden aan het bijwerken van individuele meshes, texturen, onderdelen en meer.

Roblox-pakketten stelden ons in staat om dit modulaire ontwerp te bereiken door ons in staat te stellen een palet van [Meshparts](/docs/nl-nl/reference/engine/classes/MeshPart)  samen te voegen dat gemakkelijk in elkaar klikte, trim sheet sets en [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -knopen die de [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  konden delen. Dit stelde ons in staat om ons aan te passen aan veranderingen in indeling en grootte tijdens vroege playtests en maakte het proces van het invullen van het station veel sneller.

 ![Architectuur Overzicht](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture-Overview.jpeg)

## [Flexibele ontwerpen naar eindkunst](#flexibele-ontwerpen-naar-eindkunst)[](#flexibele-ontwerpen-naar-eindkunst)

Toen we voor het eerst begonnen, hadden we geen volledig begrip van wat we in het station wilden hebben, of hoe groot het moest zijn voor 50 spelers.

Om dat uit te zoeken, begonnen we eerst met het bouwen van de omgeving met [Parts](/docs/nl-nl/reference/engine/classes/Part)  en brachten we enkele meshes in, zoals de rotunda-vorm uit onze externe DCC-toepassing, zoals Maya of Blender. Met deze eenvoudige vormen pasten we de schaal van de kaart, de indeling van de kamers en de paden aan om de meest leuke indelingen te vinden. Of het nu voor een spel of een sociale ervaring is, deze vroege fase is meestal de meest dynamische.

Bij het bouwen van de indeling van het station was het belangrijkste om de verkenning te stimuleren door de gebruiker een doel te geven. In dit geval is het meest voor de hand liggende doel om een beter kijkje te nemen bij het zwarte gat. Vervolgens wisten we dat het geven van een rechte weg naar het zwarte gat saai zou zijn, omdat een speler gewoon van de spawn naar het einde van de kaart kan lopen. We hebben het pad onderbroken zodat de speler niet bij het zwarte gat kon komen zonder eerst om te gaan en andere dingen te zien die hen ook zouden kunnen aantrekken.

Het modulaire ontwerp stelde ons in staat om dergelijke wijzigingen in de omgeving aan te brengen zonder catastrofale herontwerpen van het algehele ontwerp. We konden hele secties van het station verplaatsen om met verschillende gameplay-ideeën te spelen. Uiteindelijk konden dezezelfde modulaire stukken vervolgens worden bijgewerkt met behulp van pakketten, zodat we niet meerdere versies van hetzelfde asset hoefden te reconstrueren.

 ![Architectuur Voorbeeld 1](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_1.jpeg)  ![Architectuur Voorbeeld 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_2.jpeg)  ![Architectuur Voorbeeld 3](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_3.jpeg)  ![Architectuur Voorbeeld 4](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_4.jpeg)

## [Modulaire ontwerp van Kerr-Newman DSR-14](#modulaire-ontwerp-van-kerr-newman-dsr-14)[](#modulaire-ontwerp-van-kerr-newman-dsr-14)

Het ruimtestation gebruikt slechts een handvol modulaire paletstukken. Modulaire paletstukken zijn herbruikbare assets, wat betekent dat we niet elke muur uniek hoeven te maken, maar in plaats daarvan verschillende kleinere muren kunnen samenvoegen. Dit biedt flexibiliteit in de indeling terwijl we bouwen.

Hier zijn enkele tips die ons hielpen bij het creëren van ons modulaire ontwerp:

-

Kies een uniforme rastergrootte  — Voor het station hebben we gekozen voor een rastergrootte van 16 studs om de meeste modulaire set te creëren. De rastergrootte die je gebruikt is willekeurig, maar moet consistent zijn in het hele project en bij alle artiesten die aan dat project werken. Het kiezen van een rastergrootte aan het begin van je project zorgt ervoor dat elk stuk mooi past bij het stuk ernaast. Het stelt je ook in staat om stukken gemakkelijk te verwisselen, bijvoorbeeld het verwisselen van een muurgedeelte voor een deursectie.

-

Alle eenheden worden geïmporteerd als studs  — Bij het maken van meshes in andere DCC-toepassingen, zoals Maya of Blender, converteert Studio geen meters, centimeters, voeten of inches — het vervangt eenvoudig de binnenkomende eenheden door dezelfde eenheden in studs. Als je bijvoorbeeld je eenheden op meters instelt, converteert Studio 2 meter naar 2 studs. Het is het beste om je eenheidsschalen in je applicatie naar keuze te behandelen als studschalen in Roblox. De dichtstbijzijnde schaal in de echte wereld voor een enkele stud in Roblox is 28 centimeter.

-

Houd stukken eenvoudig  — Probeer niet elk stuk te bouwen dat je denkt ooit nodig te hebben. Het idee is om een paar zeer veelzijdige stukken te hebben en niet veel unieke stukken. Hoe meer stukken je hebt, hoe meer tijd het kost om elk stuk te maken, en hoe meer het je algehele geheugen- en prestatiebudget beïnvloedt. Je kunt altijd een ander stuk aan je kit toevoegen als het absoluut nodig is.

-

Gebruik pakketten  — Zet elk modulaire stuk om in een pakket en zet ook materialen in pakketten voordat je ze in je spel begint te populeren. Dit stelt je in staat om gemakkelijk updates naar alle instanties te pushen. We zullen later dieper ingaan op pakketten.

De volgende screenshots tonen verschillende manieren waarop we modulaire ontwerpen hebben gebruikt om delen van het station te construeren.

 ![Architectuur Voorbeeld 5](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_5.png)  ![Architectuur Voorbeeld 6](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_6.png)  ![Architectuur Voorbeeld 7](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_7.png)  ![Architectuur Voorbeeld 8](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Architecture_Example_8.png)

## [Maak trim sheets](#maak-trim-sheets)[](#maak-trim-sheets)

1:1 texturen zijn de toekomst, maar ze worden kostbaar wat betreft geheugenbudgetten en tijd om te creëren. Voor het ruimtestation gebruikte 90% van de architectonische elementen een handvol verwisselbare trim sheet sets, wat een set van textuurkaarten is die in een verticale of horizontale opstelling zijn gerangschikt. Elke rij of kolom van de sheet heeft een unieke uitstraling, waardoor je een aantal verschillende oppervlaktebehandelingen kunt kiezen bij het unwrappen van een model, terwijl je slechts één afbeeldingsblad gebruikt.

Hier zijn enkele tips voor het maken van trim sheets:

-

Begin met een inventaris van de soorten objecten en materialen die je nodig hebt  — Trim sheets kunnen een grote variatie in materiaaltypes bevatten, zoals hout, metaal, rubber en meer. Voordat je begint met het modelleren van je eerste object, maak je een trim sheet-sjabloon. Dit is het startpunt voor al je andere trim sheet sets en het geeft je een snel startpunt voor het unwrappen van je modellen. Deze trim sheets bevinden zich binnen de [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -knop, die we later zullen behandelen.

-

Inclusief een verscheidenheid aan oppervlaktebehandelingen in één sheet  — Dit stelt je in staat om meer van de mesh samen te houden, zodat je nieuwe behandelingen kunt toepassen zonder je meshes in meerdere meshes te hoeven splitsen. Dit verbetert de runtime-prestaties door het aantal object- en materiaal-tekenopdrachten te verminderen.

-

Maak een trim sheet-sjabloon  — Een sjabloon zorgt ervoor dat je elke kaartset voor een andere kunt verwisselen. Je kunt bijvoorbeeld een schone metalen set verwisselen met een verroeste metalen set.

Hier is hoe we trim sheets voor het station hebben gemaakt:

We maakten een ruwe schets van hoe de sheet eruit zou moeten zien:

 ![Trim Sheet Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Trim_Sheet_Example.png)

In Photoshop maakten we een mockup om een snel idee te krijgen van hoe elk trimgedeelte van de sheet eruit zou zien.

 ![Trim Sectie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Trim_Sheet_Example_2.png)

We gebruikten Substance, maar je kunt elke applicatie gebruiken die je helpt om de uiteindelijke kaarten te maken. Dit is de uiteindelijke set van trim sheet-kaarten die in Substance zijn gegenereerd. Alle vier de kaarten werken samen binnen een SurfaceAppearance-knoop om een Physically Based Rendered (PBR) materiaal te produceren.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/PBR_Example_1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/PBR_Example_2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/PBR_Example_3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/PBR_Example_4.png)

Hier zijn enkele laatste renders van de trim sheet binnen Substance Designer:

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Trim_Sheet_Final_1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Trim_Sheet_Final_2.png)

En hier zijn voorbeelden van dezelfde trim sheets die op een groot aantal objecten worden gebruikt:

 ![Modulaire Trim Sheets](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Modular_Trim_Sheet.png)

Als je meer wilt leren over Trim Sheet UV Mapping, zoek dan gewoon het onderwerp op het web; er zijn veel geweldige tutorials beschikbaar.

## [Pas oppervlakteverschijningen toe](#pas-oppervlakteverschijningen-toe)[](#pas-oppervlakteverschijningen-toe)

[SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  stelt je in staat om nieuwe textuurinvoeren op ons Physically Based Rendering-systeem voor [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  op te geven en stelt je in staat om het uiterlijk van een mesh te overschrijven met geavanceerde grafische opties, waaronder ColorMap, MetalnessMap, RoughnessMap en NormalMap. Het maakt ook gebruik van het nieuwe dynamische cubemap-systeem dat Roblox gebruikt voor reflecties in materialen, zoals chroom. Bijvoorbeeld, hier is een zij-aan-zij afbeelding van een mesh met SurfaceAppearance toegepast naast een mesh zonder het:

 ![Oppervlakte Verschijning Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Surface_Appearance_Example_1.png)

Bij het gebruik van oppervlakteverschijning, houd de volgende tips in gedachten:

-

Als je trimkaarten alfa-informatie voor transparantie bevatten, wijzig dan de AlphaMode van Overlay naar Transparency.

-

Oppervlakteverschijning werkt niet met Parts omdat ze de UV-informatie missen die nodig is om de kaarten toe te passen. Parts gebruiken wereldgeoriënteerde projecties in plaats van UV-informatie. MeshParts worden normaal gesproken in een andere app zoals Maya, 3ds Max of Blender gemaakt en bevatten UV-unwrap-informatie.

Om [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  toe te passen:

1.

Klik op het einde van een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  of mapnaam in de Explorer  en zoek naar [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) . Het toevoegen van een zal elke BrickColor, Color, Material en TextureID die je mogelijk al hebt toegepast, overschrijven.

2.

Hernoem de [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -knop naar iets unieks en voeg een postfix van _SA  toe om ze gemakkelijk te doorzoeken. In dit voorbeeld gebruikten we Metal_Trim_A_SA .

3.

Importeer de trim sheet-kaarten, kopieer de ID's uit het Asset Manager -venster en plak ze in de juiste vakken in het Properties -venster. Hier is hoe de Metal_Trim_A_SA -knop eruit ziet met alle kaart-ID's ingevoerd en toegepast op de deur.

 ![Oppervlakte Verschijning Voorbeeld 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Surface_Appearance_Example_2.png)

Voor meer informatie over Physically Based Rendering (PBR), zie de documentatie van Adobe's Substance Designer [Deel 1](https://substance3d.adobe.com/tutorials/courses/the-pbr-guide-part-1)  en [Deel 2](https://substance3d.adobe.com/tutorials/courses/the-pbr-guide-part-2) .

## [Verhoog de efficiëntie met pakketten](#verhoog-de-efficiëntie-met-pakketten)[](#verhoog-de-efficiëntie-met-pakketten)

Pakketten stellen je in staat om objectinstanties door je Roblox-spellen te creëren, zodat updates die je aan het pakket aanbrengt, worden gepubliceerd naar alle instanties van dat pakket. We gebruikten pakketten voor bijna elk object dat we in het station plaatsten, zodat we niet elke plaatsing hoefden te zoeken als we aanpassingen moesten maken. We gebruikten bijvoorbeeld meer dan 1.000 wandpaneelinstanties van een pakket en konden updates onmiddellijk publiceren door het pakket te wijzigen.

Volg deze tips bij het gebruik van pakketten:

Zet de auto-updatefunctie aan in [PackageLink](/docs/nl-nl/reference/engine/classes/PackageLink) . Alle wijzigingen worden toegepast op alle gebruiksinstances van het pakket wanneer dit is ingeschakeld, waardoor je de stap bespaart om de "alle bijwerken" functie te gebruiken.

 ![Pakketten Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Packages_Example_1.png)

Je kunt pakketten gebruiken voor [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -objecten om een "materiaalbibliotheek" te creëren. Dit stelt je in staat om bitmapafbeeldingen in een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -object te wijzigen en deze naar elk object dat het gebruikt te publiceren. De volgende screenshot toont mastermaterialen die door de demo heen zijn gebruikt. Als we de kaarten moesten wijzigen, hoefden we alleen maar het mastermateriaal bij te werken en het pakket opnieuw te publiceren.

 ![Pakketten Voorbeeld 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/building-architecture/Packages_Example_2.png)

[Volgende](/docs/nl-nl/resources/beyond-the-dark/custom-characters)[Vorige](/docs/nl-nl/resources/beyond-the-dark)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
