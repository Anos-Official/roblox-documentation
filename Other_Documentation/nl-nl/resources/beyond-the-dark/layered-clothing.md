<!-- Source: https://create.roblox.com/docs/nl-nl/resources/beyond-the-dark/layered-clothing -->

Voorbeeld van gelaagde kleding | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Beyond The Dark](/docs/nl-nl/resources/beyond-the-dark)

# Voorbeeld van gelaagde kleding

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gelaagde kleding stelt je in staat om 3D-kleding en accessoires te creëren die bijna elke avatar kan dragen met elke combinatie van andere gelaagde kleding. Gelaagde kleding rekt zich natuurlijk over het lichaam van een avatar en andere gelaagde kledingstukken zonder te knippen of te breken.

We raden aan om een basislichaamskarakter te bouwen waarop je de gelaagde kleding kunt passen die je aan het maken bent. We zullen bespreken hoe je dit kunt doen in een externe DCC-toepassing en alles in Studio kunt combineren om het uiteindelijke karakter vanuit het ruimtestation te creëren.

Voor aanvullende bronnen over gelaagde kleding, zoals handleidingen, voorbeeldprojecten en referentiemodellen, zie [Gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories) .

## [Bouw het aangepaste karakter](#bouw-het-aangepaste-karakter)[](#bouw-het-aangepaste-karakter)

We wilden dat de gebruikers in ons spel iemand belichamen die naar het station was gestuurd om enkele verontrustende gebeurtenissen te onderzoeken. We wisten in het begin niet precies wat ons daadwerkelijke karakter zou zijn of er meerdere soorten karakters zouden zijn, maar we wilden dat ze ruimtepakken droegen. Daarom besloten we om de kleding een afzonderlijk onderdeel te maken, wat flexibiliteit in ons ontwerp zou bieden.

Uiteindelijk hebben we ons neergelegd bij een enkel karakterontwerp dat we "De Bezoeker" noemden, maar gelaagde kleding stelde ons in staat om een hoofdkarakter te creëren terwijl we ook de kleding als een modulair onderdeel op de Marketplace konden uitbrengen. Als maker kun je binnenkort hetzelfde doen, dus volg mee om te zien hoe we dit hebben gedaan.

 ![Voorbeeld van Aangepast Karakter](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Custom-Character-Example.png)

### [Maak het basislichaam](#maak-het-basislichaam)[](#maak-het-basislichaam)

Het basislichaam is in wezen de laagste laag van het gelaagde kleding systeem. Dit kan alles zijn, van het lichaam van onze karakter in ondergoed, tot een visman of zelfs een blokachtige avatar.

Checklist voor gelaagde accessoires:

-

De lichaamsgeo, cage-onderdelen en skelet moeten voldoen aan het [standaard R15-schema](/docs/nl-nl/avatar/character-bodies/specifications) .

-

De lichaamskooi moet de kooi gebruiken die door Roblox is geleverd.

-

De kooi moet hetzelfde aantal onderdelen hebben als de lichaamsgeo, met de suffix _OuterCage.

-

LeftUpperArm_Geo (mesh)

-

LeftUpperArm_OuterCage (cage)

-

Het poly-budget voor elk onderdeel mag niet meer dan 10.000 driehoeken bedragen.

-

De grootte van het karakter mag niet meer dan 2000×2000×2000 eenheden bedragen.

### [Maak het model](#maak-het-model)[](#maak-het-model)

Gelaagde kleding laat kleding passen op bijna elk soort lichaam, of het nu een visman, een rotsgolem of een menselijke ruimteverkenner is. De enige vereisten zijn dat ze bipedale humanoïden zijn.

Je moet het karakter in een neutrale en natuurlijke houding modelleren. Dit zorgt voor een breder bewegingsbereik bij het animeren en geeft je ook een impliciete richting aan beweging. Impliciete richting betekent dat wanneer je het skelet van je karakter bouwt, de gewrichten een kleine buiging hebben om te weten welke kant ze natuurlijk moeten buigen. De volgende voorbeelden tonen een zeer kleine buiging in de armen en benen om dit mogelijk te maken. We hebben ook de handen in een natuurlijke houding geposeerd die nog steeds iets kan vasthouden als we items of uitrusting in ons spel willen.

 ![Unieke Karakter Voorbeelden](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Unique-Characters.png)

De silhouet, of de vorm van je karakter, moet ook onderscheidend en herkenbaar zijn voor een andere speler op afstand, wat belangrijk is voor multiplayer games. Dit vermindert verwarring en helpt gebruikers te weten wat veilig of gevaarlijk is wanneer er veel dingen aan de hand zijn.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Silhouette-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Silhouette-2.png)

Een belangrijke opmerking over het basis karakter: aangezien dit een spelersavatar is, en we uiteindelijk het lichaam en de kleding op de Marketplace wilden uitbrengen, moet het nog steeds voldoen aan het [standaard R15-schema](/docs/nl-nl/avatar/character-bodies/specifications) . Dit omvat dat het lichaam is verdeeld in 15 onderdelen.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Character-Model.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Character-Model-Exploded.png)

Om ervoor te zorgen dat de onderdelen aaneengeschakeld blijven, is het aan te raden om je mesh-componenten af te sluiten en vervolgens je toepassing te gebruiken om de vertex-normals tussen de "naden" van de lichaamsdelen te "gemiddeld". Dit zal de twee vertices aan weerszijden van het lichaamsdeel als één beschouwen, wat betreft de oppervlakte-normals.

 ![Invloeden Tussen Naden Voorbeeld 1](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Seams-Example-1.png)  ![Invloeden Tussen Naden Voorbeeld 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Seams-Example-2.png)

### [Textuur](#textuur)[](#textuur)

Het textureren van je karakters laat je ze tot leven brengen op basis van hoe je wilt dat ze eruitzien. Voor het ruimtestation wilden we een karakter dat een vergelijkbaar niveau van realisme had als zijn omgeving en kwamen we uit op het volgende karakter:

 ![Texturering Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Texturing-Showcase.png)

Nu zullen we bespreken hoe we texturen in Studio kunnen krijgen en ervoor kunnen zorgen dat het karakter er geweldig uitziet en in het spel past.

1.

Voor het textureren hebben we een reeks bewegingsproeven gedaan door de gewrichten van het karakter te bewegen en het te poseren om ervoor te zorgen dat het model goed vervormt. Het is niet altijd nodig om bewegingsproeven te doen voordat je gaat textureren, maar het helpt je om verrassingen in je model op te vangen voordat je uren in de texturen steekt. Daarna hebben we het rig van de mesh gescheiden (ongebonden) om ons te concentreren op het textureren. Het is niet aan te raden om textuurwerk of iets anders dan animeren te doen zodra een karakter aan zijn rig is gebonden.

 ![Bewegingsproef Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Motion-Test.png)

2.

Om huidtintcontroles voor de Marketplace mogelijk te maken, hebben we gebieden zoals het shirt, de shorts, de handschoenen en de laarzen volledig ondoorzichtig gemaakt. Voor de gebieden met blootgestelde huid hebben we echter gedeeltelijke transparantie gebruikt om details aan de huidtint toe te voegen, maar niet volledig te overschrijven. Dit stelde ons in staat om anatomische kenmerken te verbeteren, verder dan wat de huidige verlichting van Studio kan doen.

 ![Texturering en UV-diagram](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/UV-Diagram.png)

De volgende afbeeldingen tonen kleur (albedo), metalness, roughness en normal maps.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/UV-Maps-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/UV-Maps-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/UV-Maps-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/UV-Maps-4.png)

En de volgende afbeeldingen tonen huidtinttransparantie in actie in Studio, en tonen dezelfde kleurkaart met transparantie en een huidtintkleur toegepast.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skin-Tone-Maps-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skin-Tone-Maps-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skin-Tone-Maps-3.png)

 ![Verschillende Textuurvergelijkingen](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Texture-Comparisons.png)

### [Kooi](#kooi)[](#kooi)

Zodra we het basislichaam hadden vastgesteld, moesten we het kooi maken zodat gelaagde kleding erop kon passen. Cages zijn de manier waarop de kleding en het lichaam met elkaar interageren. Zowel het lichaam als de kleding hebben dezelfde kooi, vervormd door de gebruiker om de pasvorm van de kleding te definiëren. De lichaamskooi vertelt de kleding de vorm van het karakter zonder al de fijne details van de mesh zelf. De binnenkooi van de kleding definieert hoe strak de pasvorm van de kleding is.

De eerste pas van het passen van de kooi moet voorlopig binnen een externe DCC-toepassing worden gedaan. Je kunt de kooi gebruiken die door Roblox is geleverd om te beginnen.

De kooi voor het lichaam is grotendeels hetzelfde als die van de kleding, behalve dat het eindresultaat een kooi is die 15 onderdelen heeft (elk overeenkomend met een mesh van een lichaamsdeel). Hieronder is de "bewerkbare" kooi die een enkele mesh is, de kooi-onderdelen die worden vervormd door de "bewerkbare" kooi te bewerken, en de mesh zelf.

 ![Individuele Lichaamsdeel Cages](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Body-Cage-Example-1.png)

Wanneer je voor het eerst met de kooi begint, is het zeer waarschijnlijk dat deze niet overeenkomt met je karakter, dus je moet de "bewerkbare" kooi of de onderdelen direct aanpassen om aan te passen aan de buitenste grenzen van de lichaamsmesh. Net als bij kleding moet de buitenste kooi altijd buiten de lichaamsmesh passen, zodat de kleding de vorm van het lichaam zelf kent. Het gebruikt een "tweeling" kooi in de kleding om de kleding in wezen aan deze buitenste kooi te bevestigen (hierover zullen we hieronder meer in detail ingaan).

 ![Kooi Aanpassings Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Body-Cage-Example-2.png)

We besloten dat we de buitenste kooi de huid wilden laten bedekken, maar niet de handschoenen en laarzen. Behalve die gebieden zie je dat de kooi zo goed mogelijk buiten het lichaam past, inclusief de gezichtskooien die overeenkomen met de afstand en vorm van de gelaatskenmerken.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Body-Cage-Example-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Body-Cage-Example-4.png)

 ![Buitenste Kooi Voorbeeld 3](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Body-Cage-Example-5.png)  ![Buitenste Kooi Voorbeeld 4](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Body-Cage-Example-6.png)

### [Huid](#huid)[](#huid)

Het skinnen van het karakter, vergelijkbaar met Aangepaste Karakters, is wat de organische buiging en draaiing van je karakter geeft wanneer deze door de omgeving beweegt. We vonden de volgende richtlijnen nuttig, zodat de karaktermesh correct in Studio wordt geïmporteerd:

-

Individuele gewrichten en botten moeten unieke namen hebben.

-

Meshes mogen geen transformaties hebben vóór het skinnen/binden; met andere woorden, transformaties moeten 0 zijn en schalen moeten 1 zijn.

-

Mesh-normals moeten naar buiten wijzen (het model mag niet binnenstebuiten lijken).

-

Skeletten mogen geen schaalfactor hebben; alle gewrichten moeten [1, 1, 1] zijn.

-

Het skinnen van dit karakter was iets moeilijker gezien de beperkingen van het aantal gewrichten, maar hier zijn enkele aantekeningen van het werk dat we hebben gedaan:

-

Bij het skinnen van een mens met duidelijke anatomie is het het beste om je gewichten te schilderen zodat de buiging er natuurlijk uitziet, bijvoorbeeld de schouderspier die uitrekt of samenperst wanneer je de arm omhoog en omlaag beweegt.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skinning-Influence-Example-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skinning-Influence-Example-2.png)

-

Een ander veelvoorkomend probleem bij het skinnen van mensen is dat de standaard skinning vaak "te soepel" is, wat betekent dat gebieden zoals de ellebogen en knieën te veel invloed hebben. Het is het beste om ze strakker te schilderen, zodat je benen/armen niet samenpersen wanneer ze buigen.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skinning-Influence-Example-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skinning-Influence-Example-4.png)

-

Ten slotte, omdat je model is verdeeld in 15 onderdelen, moet je ervoor zorgen dat de naden tussen de onderdelen 1:1 zijn qua gewicht. De meeste toepassingen stellen je in staat om invloeden van de ene vertex naar de andere te kopiëren, zodat ze exact hetzelfde gewicht hebben.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Shoulder-Seams-Example-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Shoulder-Seams-Example-2.png)

### [Handschoenen en laarzen](#handschoenen-en-laarzen)[](#handschoenen-en-laarzen)

Zoals je kunt zien aan het basislichaam, hebben we besloten om handschoenen en laarzen op te nemen. Je wilt dit misschien tijdelijk ook doen, om de volgende redenen:

1.

We wilden dat handschoenen deel uitmaakten van het gelaagde kledingpak, maar handschoenen worden momenteel niet ondersteund in de gelaagde kledingfunctie, dus we vervingen de handen van ons initiële model door een model met handschoenen.

2.

We wilden dat de metalen ring van de schoen stijf was en niet vervormde om zich aan de voet en het been aan te passen, dus we vervingen de voeten van ons initiële model door een model met laarzen.

 ![Vergelijking Na Vervangen van Voeten en Handen](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Replacing-Hands-And-Feet.png)

3.

Om ervoor te zorgen dat gelaagde kleding niet probeerde zich aan te passen aan de laarzen of handschoenen, hebben we de kooien binnenin ze opzettelijk behouden. Dit stelt de boven- en onderkant van het ruimtepak in staat om zich aan de handen en voeten aan te passen.

 ![Kooi met Handschoenen](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Caging-With-Gloves.png)

## [Bouw het pak](#bouw-het-pak)[](#bouw-het-pak)

Vroeg in het proces besloten we dat het pak op meerdere karakters moest passen, en dat we de activa op de Marketplace wilden uitbrengen, zodat anderen van de kleding konden genieten. Naast gelaagde kleding had ons karakter "hardpoint"-items zoals een helm en rugzak als finishing touch nodig. De volgende afbeelding toont hoe het ruimtepak eruitziet op verschillende karakters.

 ![Vergelijking van Gelaagd Kleding Pak](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Layerable-Suit-Comparison.png)

We vonden de volgende richtlijnen nuttig bij het bouwen van gelaagde kleding:

-

Het geëxporteerde .fbx -bestand van je DCC-toepassing moet de kledingmesh , binnenkooi , buitenkooi  en skelet  bevatten.

-

De manier waarop je je kleding benoemt is willekeurig, maar beide kooien moeten dit naamgevingsformaat hebben:

-

[kleding naam] _InnerCage

-

[kleding naam] _OuterCage

-

Je moet kleding skinnen aan het [standaard R15](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  skelet met een maximum van 4  invloeden.

-

Je standaard R15-skelet moet dit naamgevingsschema volgen.

Met deze richtlijnen in gedachten, zijn hier de stappen die we hebben gevolgd om het ruimtepak te bouwen:

1.

Gebruik de Roblox gelaagde kledingkooi-sjabloon, een basisframe dat je kunt gebruiken om kleding op te passen. Afhankelijk van de afstand van de kleding tot het frame, kun je kleding hebben die strak of los zit.

2.

Modelleer de kleding op het frame en beeld een hoger-poly model uit in een externe DCC-toepassing.

3.

Bouw de lagere-poly, game-klaar versie van het hogere-poly model opnieuw. Als je meer informatie over dit proces wilt, zijn er veel tutorials online voor high-poly naar game-klaar modellen. Merk op dat kleding niet in onderdelen hoeft te worden verdeeld die overeenkomen met de lichaamsdelen die ze bedekken; het kan een enkele mesh zijn.

 ![Voorbeeld van Kledingontwerp 1](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Clothing-Design-Example-1.png)  ![Voorbeeld van Kledingontwerp 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Clothing-Design-Example-2.png)

4.

Test de beweging en pasvorm op andere karakters voordat je enige texturen finaliseert.

5.

Definieer de "buitenste kooi" of de buitenste grenzen van het kledingstuk. Dit vertelt eventuele extra lagen hoe strak ze moeten passen op de bovenkant van het astronautenpak.

Het is erg belangrijk dat de buitenste kooien van de kleding dicht bij de kledingmesh volgen, maar altijd buiten de kleding zijn. Dit stelt Studio ook in staat om een andere krachtige functie te gebruiken, Hidden Surface Removal. Deze functie verwijdert geometrie van een laag kleding of zelfs het lichaam, als het bedekt is door een andere laag. Dit is immens nuttig, omdat je je geen zorgen hoeft te maken over het binnendringen van meshes wanneer het karakter rondloopt.

 ![Voorbeeld van Gelaagde Kleding Buitenste Kooi](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Clothing-Outer-Cage.png)

6.

Na het kooiën kan het helpen om de kleding tijdelijk aan het skelet in het sjabloonbestand te binden, alleen om een bewegingsproef te doen. Door het rig in verschillende posities te poseren, kun je bevestigen dat het goed vervormt voordat je de texturering finaliseert. Als je dit doet, zorg er dan voor dat je ongebonden voordat je naar texturering gaat!

 ![Gelaagde Kleding Rig Binding](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Clothing-Posing.png)

### [Textuur](#textuur-1)[](#textuur-1)

Nadat we de kleding hadden geskin, en het bewoog zoals we bedoelden, gingen we verder met textureren.

1.

Omdat we realisme wilden nastreven, gebruikten we oppervlakteverschijning voor de prachtige PBR-materialen. We brachten dit in een textureringsapplicatie om de albedo-, metalness-, roughness- en normal maps te maken. Dit stelde het outfit in staat om delen te hebben die er metallic uitzagen en andere die meer op ruwe canvas leken.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Suit-Texturing-Example-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Suit-Texturing-Example-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Suit-Texturing-Example-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Suit-Texturing-Example-4.png)

 ![Oppervlakteverschijning Verlichtingstest 1](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Suit-Lighting-Test.gif)

2.

Voordat we veel verder gingen, brachten we het model en de texturen in Studio om de materialen met de juiste verlichting in het ruimtestation te testen. Dit leidde tot enkele aanpassingen aan de metalness van de arm- en torso-banden.

 ![Oppervlakteverschijning Verlichtingstest 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Suit-Lighting-Test-2.png)

Houd bij het textureren van je kleding de volgende punten in gedachten:

-

Voor oppervlakteverschijning, zorg ervoor dat je kleur (albedo), metalness, roughness en normal maps opneemt.

-

Zonder metalness, valt de oppervlakteverschijning terug op 0 metalness, of een plastic oppervlak.

-

Zonder roughness, valt de oppervlakteverschijning terug op 0 roughness, of een glad oppervlak.

### [Huid](#huid-1)[](#huid-1)

Het skinnen van kleding is vereist om ervoor te zorgen dat het goed buigt met het basislichaam. Door het te skinnen, vertel je ook de animaties hoe de kleding moet buigen, inclusief welke delen stijf zijn of met het karakter meebewegen.

 ![Geskinnd Model Animatie](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Skinning-Movement.gif)

Gelukkig, in tegenstelling tot het basislichaam, hoef je je kleding niet op te splitsen, zodat de bovenkant van het pak een enkele mesh kan zijn en als zodanig geskinnd kan worden. Om tijd te besparen, zullen de meeste toepassingen je alleen toestaan om je mesh aan bepaalde gewrichten te skinnen. De gewrichten die we wilden dat de bovenkant van het pak beïnvloedden, waren alleen boven-/onderlichaam, boven-/onderarmen en het hoofd. Niet binden aan het hele lichaam bespaarde tijd bij het verwijderen van onnodige gewichten.

 ![Maya Karakter Vertex Invloeden Voorbeeld 1](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Vertex-Influence-Example-1.png)

Net als bij het lichaam, wil je dit zo skinnen dat het natuurlijk buigt gezien het materiaal. Dit betekende dat voor het middelste plastic gedeelte, we een solide gewicht hadden aan het bovenlichaam.

Aangezien de handschoenen stijf zouden zijn, en de bovenkant van het pak goed boven de pols stopte, vonden we het niet nodig dat het met de handen meeboog.

 ![Maya Karakter Vertex Invloeden Voorbeeld 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Vertex-Influence-Example-2.png)

Zodra het skinnen van de bovenkant van het pak was voltooid, herhaalden we eenvoudig dezelfde procedure op de broek om ze klaar te maken voor Studio en om in de engine te brengen!

### [Importeren in Studio](#importeren-in-studio)[](#importeren-in-studio)

Wanneer de kleding er goed uitzag in onze DCC-toepassing en in Studio, waren we klaar om het in Studio te importeren en de Accessory Tool te gebruiken, een aanstaande release die je zal helpen de kooien van de kleding te verfijnen voor de best mogelijke pasvorm. De tool kan ook kleding exporteren als een accessoire, waarmee je je kleding aan een karakter kunt toevoegen.

In Studio noemden we onze gelaagde kledingitems met een LC_ prefix, zodat we ze konden onderscheiden van legacy-stijl accessoires (de helm en rugzak onderdelen van het pak).

 ![Accessoires in de Studio Explorer](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Accessories-In-Explorer.png)

## [Bouw de helm](#bouw-de-helm)[](#bouw-de-helm)

De helm is een belangrijk element van het pak. We wilden dat gebruikers het gezicht van het karakter konden zien en ook de glans van het glazen oppervlak van de helm konden vastleggen.

 ![Helm Glazen Oppervlak Render](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Glass-Surface-Example.png)

Accessoires waarbij we geen vervorming willen om aan het hoofd te passen, zoals deze helm, worden het beste gebouwd als "hardpoint" accessoires, wat de soorten accessoires zijn die je momenteel in de Marketplace vindt. Het belangrijkste verschil met de helm en wat je in de Marketplace vindt, is dat het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  gebruikt, wat overtuigende plastic- en metalen looks creëert en de helmvizier enige transparantie geeft.

### [Maak het model](#maak-het-model-1)[](#maak-het-model-1)

Om een helmmodel te bouwen:

1.

We hebben een goede silhouet vastgesteld toen we de helm op het hoofd van het karakter plaatsten.

 ![Helm Silhouet](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Helmet-Silhouette.png)

2.

We hergebruikten de trim-maps van het ruimtestation om de hoeveelheid texturen tot een minimum te beperken. We modelleerden de helm met voldoende aparte secties zodat we de UV's konden plaatsen om de textuurkaarten optimaal te benutten.

 ![Helm Textuurkaarten](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Helmet-Texture-Map.png)

3.

We gebruikten vervolgens dezelfde trim-maps die we in veel gebieden van het station gebruikten.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Trim-Map-Texture-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Trim-Map-Texture-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Trim-Map-Texture-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Trim-Map-Texture-4.png)

### [Importeren in Studio](#importeren-in-studio-1)[](#importeren-in-studio-1)

Wanneer we de helm ruw passend en geplaatst hadden in onze DCC-toepassing, konden we deze in Studio importeren met alle effecten die we wilden.

1.

We importeerden de helm aanvankelijk met de Asset Manager , maar omdat het een enkele mesh is, kun je ook een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  in je plaats plaatsen en de MeshId specificeren met het Properties -venster.

 ![Helm Mesh Importeren](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Importing-Helmet-Mesh.jpeg)

2.

We voegden vervolgens de textuurkaarten toe via een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object op het mesh-onderdeel. Dit proces vereiste enige afstemming om de ideale alpha op de kleur (albedo) kaart te krijgen, zodat je door de helm kon kijken zonder dat deze volledig transparant was.

 ![Textureren Helm Mesh](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Adding-Surface-Appearance.jpeg)

3.

Omdat we wilden dat sommige pakken schoon waren en andere vuil zonder meerdere texturen te hoeven gebruiken, voegden we decals toe aan hetzelfde object om dit effect te creëren. Decals werken door vlak te projecteren op elk oppervlak.

 ![Toevoegen van Extra Texturen aan Helm Mesh](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Adding-Surface-Appearance-2.jpeg)

4.

We wilden een lichtstraal en licht om aan te geven welke kant de gebruiker op keek in donkere kamers en om de gebieden te verlichten waar ze doorheen liepen. Om dit te doen, gebruikten we attachments, omdat je er een willekeurig aantal kunt toevoegen, en omdat ze geen onderdelen zijn, zijn ze geldig in accessoires. Je kunt attachments gebruiken voor deeltjes effecten, stralen of lichten zoals in het volgende voorbeeld.

 ![Toevoegen van Verlichting aan Helm Mesh](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Helmet-Attachments.jpeg)

### [Introduceer de accessoire-tool](#introduceer-de-accessoire-tool)[](#introduceer-de-accessoire-tool)

 Zie [Accessoire Pasvorm Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  voor meer informatie over het converteren van een mesh of model naar een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) .

Met zoveel componenten die parallel worden gebouwd, kan het een beetje moeilijk zijn om te weten of je activa precies passen en eruitzien zoals je wilt. Echter, met de aanstaande Accessory Tool is het passen en verfijnen van kleding veel gemakkelijker. We gebruikten deze tool om de boven- en onderkant van het karakter in te stellen, evenals de hardpoint helm en rugzakaccessoires.

 ![Overzicht van Karakter en Pak](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Character-And-Suit-Overview.png)

Hier is een samenvatting van het gebruik van de Accessory Tool voor gelaagde kleding:

1.

We pasten eerst de bovenkant van het pak aan het karakter aan. Gelukkig was de pasvorm geweldig en paste onze binnenkooi goed bij het lichaam. We testten ook de buitenkooi met andere kledingstukken. Toen we tevreden waren met de pasvorm, gebruikten we de tool om het juiste accessoire voor de Marketplace te genereren.

 ![Gebruik van Accessoire Pasvorm Tool Mannequin](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Accessory-Tool-Mannequin.png)

2.

Met de onderkant van het pak wilden we de pasvorm binnen Studio aanpassen omdat ze aanvankelijk te bulky waren. Met de punteditor duwden we dingen om ze in positie te krijgen. Net als de bovenkant van het pak maakten we het tot een accessoire.

 ![Aanpassen van Gelaagde Kleding met Accessoire Pasvorm Tool](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Accessory-Fitting-Tool-Adjustments.png)

3.

Voor de helm en rugzak pasten we deze gewoon aan door ze te schalen, roteren en verplaatsen waar we ze wilden, omdat ze geen kooien hebben.

 ![Aanpassen van Gelaagde Kleding Helm met Accessoire Pasvorm Tool](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Accessory-Fitting-Tool-Adjustments-2.png)

4.

Het is lastig om te zien hoe de helm past zonder de rest van het pak, dus gebruikten we de Accessory Tool om de boven- en onderkant van het pak te visualiseren. Dit stelde ons in staat om ervoor te zorgen dat de pasvorm zou overeenkomen met de bovenkant van het pak.

 ![Aanpassen van Gelaagde Kleding Helm met Accessoire Pasvorm Tool](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Accessory-Fitting-Tool-Adjustments-3.png)

5.

Met de helm, rugzak, boven- en onderkant compleet, waren we klaar om te zien hoe dit karakter eruitzag in ons ruimtestation. We kopieerden en plakten de accessoires op het karakter en konden zien hoe ze pasten. We plaatsten het karakter vervolgens in ons plaatsbestand en bevestigden dat alle materialen, verlichting en andere effecten precies waren zoals we wilden.

 ![Eindrender van Gelaagde Kleding Accessoires](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/layered-clothing/Helmet-Equipped-Final.png)

[Volgende](/docs/nl-nl/resources/beyond-the-dark/sound-design)[Vorige](/docs/nl-nl/resources/beyond-the-dark/custom-characters)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
