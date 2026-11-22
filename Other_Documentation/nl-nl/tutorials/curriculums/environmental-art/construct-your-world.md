<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/environmental-art/construct-your-world -->

Bouw je wereld | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Bouw je wereld

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het bouwen van je wereld , ook wel wereldopbouw genoemd, is het proces van het decoreren van de omgeving met gepolijste assets uit je assetbibliotheek, en vervolgens het toevoegen en configureren van aanvullende elementen van de 3D-ruimte om je wereld tot leven te brengen. Deze spannende stap in de workflow is waar je al je visie en harde werk samen ziet komen in een samenhangende omgeving die compleet is en klaar voor publicatie.

Met behulp van het [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  .rbxl -bestand als referentie, laat deze sectie van het curriculum voor milieukunst je zien hoe je je hoogwaardige assets en aangepaste materialen kunt gebruiken en toepassen op je greybox-geometrie op een manier die elk afzonderlijk gebied van het teamgebaseerde first-person laser tag shooter spel onderscheidt, inclusief stapsgewijze instructies over:

-

Het toepassen van je assetbibliotheek op de architectuur van het gebouw en de buitenruimte om gebruikers informatie te geven over de algehele wereld.

-

Het sculpturen van terrein met je aangepaste tegelbare texturen om het algehele eiland te creëren waarop het gebouw zich bevindt.

-

Het afbakenen van de speelbare gebieden om ervoor te zorgen dat gebruikers in gevecht blijven zonder van het eiland te vallen.

-

Het configureren van speciale effecten en lichtbronnen om de 3D-ruimte te verrijken met beweging, warmte en realisme.

Nadat je deze sectie hebt voltooid, leer je hoe je je inhoud kunt beoordelen en configureren om ervoor te zorgen dat je spel optimale prestaties levert op verschillende apparaten.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Overview.png)

De instructies in deze sectie van de tutorial laten je zien hoe je de voorbeeld eindomgeving exact  kunt recreëren met behulp van de [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library) , wat ongeveer 90 minuten of minder duurt van begin tot eind. Als je de meegeleverde coördinaten niet wilt gebruiken, kun je de geometrie aanpassen zoals je nodig hebt om aan de specificaties van je eigen spel te voldoen, of de sample zelf gebruiken voor de rest van de tutorial.

## [Pas je assetbibliotheek toe](#pas-je-assetbibliotheek-toe)[](#pas-je-assetbibliotheek-toe)

De eerste stap in het bouwen van je omgeving is het toepassen van je assetbibliotheek op de 3D-ruimte, en dit proces valt vaak in een van de volgende werkcategorieën:

-

Het direct toepassen van je assetbibliotheek op de greybox-geometrie om exact overeen te komen met het oorspronkelijke ontwerp.

-

Het omzetten van de greybox-geometrie in iets heel anders dat nog steeds de bedoeling van het oorspronkelijke ontwerp respecteert.

-

Het omzetten van de greybox-geometrie in iets anders terwijl je ook je assetbibliotheek toepast op het nieuwe object om samenhang in de omgeving te behouden.

Het proces tussen greyboxing en het bouwen van je omgeving met je assetbibliotheek lijkt zelden op een rechte lijn van je oorspronkelijke ontwerp naar de uiteindelijke kunst. Iteratie tussen elke stap en over stappen heen is normaal en bijna altijd noodzakelijk in het ontwikkelingsproces terwijl je nieuwe manieren vindt om de gebruikerservaring in je wereld te verbeteren. Bijvoorbeeld, de richtlijnen in de sectie Vloeren  zetten de oorspronkelijke vloer greybox-geometrie om in nieuwe verdelingen om gebruikers beter te oriënteren op waar ze zich in het gebouw bevinden.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ApplyingLibraryDiagram.png)

Terwijl je deze instructies volgt die de eindomgeving binnen het voorbeeld [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  .rbxl -bestand exact recreëren, let op hoe elke stap samenwerkt om karakter aan de omgeving toe te voegen en gebruikers informatie te geven over de algehele wereld. Je kunt elk deel van het proces aanpassen om aan de specificaties van je eigen spel te voldoen , aangezien je omgeving mogelijk andere behoeften heeft afhankelijk van de wereld die je aan het creëren bent.

### [Vloeren](#vloeren)[](#vloeren)

Het oorspronkelijke greybox-ontwerp voor vloeren was om het gebouw in twee helften te verdelen, één voor elk team. Dit was nuttig om elke helft als zijn eigen ruimte voor het respectieve team te visualiseren en om het midden van de kaart af te bakenen. Echter, terwijl je begint met het bouwen van je omgeving, kun je ontdekken dat muren dit doel effectiever kunnen vervullen, en dat vloeren nuttiger zijn om gebruikers te helpen zich te oriënteren op waar ze zich bevinden ten opzichte van de buitenkant van het gebouw.

Bijvoorbeeld, de uiteindelijke voorbeeld laser tag omgeving gebruikt nieuwe vloerstukken met unieke materialen om gebruikers te informeren of ze zich ergens binnen het gebouw bevinden, of de buitenruimte naderen. Wanneer een gebruiker zich binnen het gebouw bevindt, loopt hij op oppervlakken met de GlossyTiles  [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant) , en wanneer ze in de middelste binnenplaats of onder de overhangstukken lopen die je later in deze tutorial zult maken, lopen ze op oppervlakken met de Concrete_Tiles_A  [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant) . Je kunt beide materialen vinden in de voorbeeld [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Floors-Intro.jpg)

Hoewel deze techniek de oorspronkelijke greybox-geometrie vervangt en omzet, respecteert het nog steeds de bedoeling van het oorspronkelijke ontwerp om pieken en dalen te creëren die zichtlijnen en betrokkenheidsafstanden door het spel heen controleren buiten de horizontale beweging. Dit betekent dat gebruikers alle fysieke en emotionele zintuigen van stijging en daling behouden, terwijl ze ook het voordeel hebben te weten waar ze zich bevinden in de 3D-ruimte.

Maak je eigen Recreëer de sample

Om je eigen assetbibliotheek op de vloeren toe te passen:

1.

Gebruik blok  onderdelen om symmetrische oppervlakken voor je binnenvloeren te creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-1.jpg)

2.

Gebruik wig  onderdelen om een stijging in hoogte  te creëren tussen de hoofd- en mezzaninevloeren aan de binnenkant van je gebouw.

3.

Selecteer deze binnenonderdelen, en stel in het Eigenschappen  venster Kleur , Materiaal , en/of MateriaalVariant  in op waarden die een onderscheidende visuele behandeling toepassen ten opzichte van andere oppervlakken in je omgeving. Dit stelt spelers in staat om altijd te weten dat ze zich binnen het gebouw bevinden.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-2.jpg)

4.

Gebruik blok  onderdelen om symmetrische oppervlakken voor je buitenvloeren  te creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-3.jpg)

5.

Gebruik wig  onderdelen om een stijging in hoogte  te creëren tussen de hoofd- en mezzaninevloeren aan de buitenkant van je gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-4.jpg)

6.

Gebruik blok  of wig  onderdelen om een daling in hoogte te creëren tussen de hoofd- en buitenvloeren aan de buitenkant van je gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-5.jpg)

7.

Selecteer deze buitenonderdelen, en stel in het Eigenschappen  venster Kleur , Materiaal , en/of MateriaalVariant  in op waarden die een onderscheidende visuele behandeling toepassen ten opzichte van andere oppervlakken in je omgeving. Dit stelt spelers in staat om altijd te weten dat ze zich buiten het gebouw bevinden.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralFloors-6.jpg)

8.

Veranker al deze vloeronderdelen.

### [Spawnzones](#spawnzones)[](#spawnzones)

Het oorspronkelijke greybox-ontwerp voor spawnzones was om een gebied aan de tegenovergestelde uiteinden van hun kaart te creëren voor gebruikers om zich bij hun respectieve team aan te sluiten wanneer de wedstrijd begint. De plaatsing van deze spawnzones stelt gebruikers in staat om een veilige locatie te hebben aan het begin van de wedstrijd die ver weg is van vijandelijk vuur.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/ThreeLaneLayout-SpawnZones.jpg)

De uiteindelijke voorbeeld laser tag omgeving behoudt de bedoeling van dit ontwerp terwijl het ook een kleurthema toevoegt: mint  voor het team dat zich aan de linkerkant van de kaart verzamelt, en carnation pink  voor het team dat zich aan de rechterkant van de kaart verzamelt. Je zult ditzelfde kleurenschema blijven gebruiken in deze sectie van de tutorial om gebieden van de kaart nabij de respectieve spawnzone van elk team te onderscheiden.

Maak je eigen Recreëer de sample

Om je eigen assetbibliotheek op de spawnzones toe te passen:

1.

Voeg en configureer alle toepasselijke muur , hoek , en deurframe  modulaire assets aan de binnenkant van je linker spawnzone .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/SpawnZones-1.jpg)

2.

Selecteer je muurcomponenten, en stel in het Eigenschappen  venster Kleur  in op een unieke  tint. Je zult deze kleur blijven gebruiken in de rest van de kaart om spelers te oriënteren op hun locatie ten opzichte van het kleurthema van dit team.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/SpawnZones-2.jpg)

3.

Herhaal dit proces voor je rechter spawnzone .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/SpawnZones-4.jpg)

4.

Veranker al deze spawnzone-assets.

### [Gevechtspockets](#gevechtspockets)[](#gevechtspockets)

Het oorspronkelijke greybox-ontwerp voor de gevechtspockets was om opzettelijke ruimtes voor gevechten te creëren waar de primaire lanes van de kaart kruisen met de kruis lanes. Bovendien vereiste het oorspronkelijke greybox-ontwerp dat elke gevechtspocket maximaal drie in- of uitgangspunten moest bevatten om te voorkomen dat gebruikers overweldigd werden door keuzes terwijl ze de ruimte navigeren.

De uiteindelijke voorbeeld laser tag omgeving past de voorbeeld [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  direct toe op de greybox-geometrie om exact overeen te komen met het oorspronkelijke ontwerp, terwijl het ook het kleurthema gebruikt dat in de vorige sectie is geïntroduceerd om gebieden van de kaart nabij de respectieve spawnzone van elk team te onderscheiden. Met behulp van deze kleuren en het vloermateriaal kunnen gebruikers zich snel oriënteren op waar ze zich bevinden, ongeacht waar ze zich rond het gebouw bevinden, en respecteren ze de oorspronkelijke bedoeling achter het greybox-ontwerp voor de vloeren van het gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-Intro1.jpg)

Bovendien past de techniek in deze sectie ook props uit de voorbeeld assetbibliotheek toe op de linker en rechter gevechtspockets om karakter aan de omgeving toe te voegen en geloofwaardigheid te bieden dat het een leven op zich heeft, zelfs als gebruikers niet aanwezig zijn. Dit proces, ook wel set dressing  genoemd, biedt gebruikers zowel directe als indirecte informatie over de wereld die ze bezoeken. Bijvoorbeeld, de bewegwijzering en het groen in deze sectie versterken de voorbeeld kunststijl van [Ontwikkel Gepolijste Assets](/docs/nl-nl/tutorials/curriculums/environmental-art/develop-polished-assets) , en informeren gebruikers dat ze zich in een high-tech omgeving bevinden die nog steeds prioriteit geeft aan organisch leven.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-Intro2.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-Intro3.jpg)

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek toe te passen op de gevechtzakken:

1.

Voeg alle toepasselijke props of muur , hoek , deurframe  en deur  modulaire assets toe en configureer deze aan de binnen- en buitenkant van je linker gevechtzak .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralCombatPockets-1.jpg)

2.

Selecteer je muurelementen aan de buitenkant van je linker gevechtzak, en stel in het Eigenschappen  venster de Kleur  in op dezelfde tint als het kleurthema van de linker spawnzone. Dit stelt spelers in staat om zich te oriënteren ten opzichte van het kleurthema van dit team terwijl ze de primaire en kruisbanen navigeren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralCombatPockets-2.jpg)

3.

Selecteer je muurelementen aan de binnenkant van je linker gevechtzak, en stel in het Eigenschappen  venster de Kleur  in op een unieke  tint. Dit stelt spelers in staat om zich te oriënteren wanneer ze zich binnen de gevechtzak bevinden en door de uitgangspunten kijken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-6.jpg)

4.

Herhaal dit proces voor je middelste gevechtzak  en rechte gevechtzak .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/CombatPockets-16.jpg)

5.

Veranker al deze gevechtzak assets.

### [Perimeter gangen](#perimeter-gangen)[](#perimeter-gangen)

Door je assetbibliotheek toe te passen op de buitenkant van de gevechtzakken in de vorige sectie, bevatten de meeste kruisbanen nu gepolijste assets, afgezien van de gangen die de perimeter van het gebouw vormen. Naast het gebruik van hetzelfde kleurenschema uit eerdere secties, gebruikt de uiteindelijke voorbeeld laser tag omgeving ook muurasets met hun standaard oranje kleur om gebruikers te informeren waar ze zich bevinden ten opzichte van de achterkant van het gebouw.

Bijvoorbeeld, met het perspectief in de volgende afbeelding, hebben gebruikers onmiddellijk de volgende informatie om zich te oriënteren waar ze zich binnen het gebouw bevinden:

-

De geprofileerde beton  informeert gebruikers dat als ze naar links bewegen, ze de middelste gevechtzak zullen betreden.

-

De gele muur  informeert gebruikers dat als ze vooruit bewegen, ze de achterkant van het gebouw en de binnenste primaire baan zullen bereiken.

-

De roze muur  informeert gebruikers dat als ze naar rechts bewegen, ze de rechter gevechtzak zullen betreden, en dat ze het dichtst bij de rechterkant van de kaart zijn.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-Intro1.jpg)

Afgezien van deze techniek die de voorbeeld [Omgevingskunst Assetbibliotheek](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  direct toepast op de grijsbox geometrie voor de muren om exact overeen te komen met het oorspronkelijke ontwerp, voegt het ook geometrie toe in de vorm van crate prop assets om gebruikers dekking te bieden tegen vijandelijk vuur terwijl ze de binnenste primaire baan navigeren. Deze ontwerpiteratie respecteert nog steeds de bedoeling om zichtlijnen en engagementafstanden te onderbreken met uitstekende gangruimtes en hoogteverschillen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-Intro2.jpg)

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek toe te passen op de perimetergangen:

1.

Voeg alle toepasselijke prop- of muur , hoek  en deurframe  modulaire assets toe en configureer deze voor de perimetergangen aan de linkerkant  van het gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-1.jpg)

2.

Selecteer je muurelementen, en stel in het Eigenschappen  venster de Kleur  in op dezelfde tint als het kleurthema van de linker spawnzone.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-2.jpg)

3.

Voeg alle toepasselijke prop- of muur , hoek  en deurframe  modulaire assets toe en configureer deze voor de perimetergangen aan de achterkant  van het gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-4.jpg)

4.

Selecteer je muurelementen, en stel in het Eigenschappen  venster de Kleur  in op een unieke  tint. Dit stelt spelers in staat om zich te oriënteren ten opzichte van waar ze zich bevinden in relatie tot de primaire binnenbaan. De voorbeeldgame houdt deze assets in hun standaardkleur.

5.

Voeg alle toepasselijke prop- of muur , hoek  en deurframe  modulaire assets toe en configureer deze voor de perimetergangen aan de rechterkant van het gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-5.jpg)

6.

Selecteer je muurelementen, en stel in het Eigenschappen  venster de Kleur  in op dezelfde tint als het kleurthema van de rechter spawnzone.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Perimeter-6.jpg)

7.

Veranker al deze perimetergang-assets.

### [Deuren](#deuren)[](#deuren)

De uiteindelijke voorbeeld laser tag omgeving past deuren direct toe op de greybox geometrie om exact overeen te komen met het oorspronkelijke ontwerp, echter, niet alle in- of uitgangspunten hebben deurassets. Je kunt ontdekken dat de vereisten van je eigen game meer of minder deuren vereisen, afhankelijk van hoe je de strijd binnen je gevechtszones wilt beheersen. Meer deuren leiden vaak tot langere wachttijden voordat gebruikers een gevechtszone binnenkomen of verlaten, maar minder deuren kunnen ongewenste zichtlijnen openen.

Om deze reden wordt aanbevolen om met meerdere variaties te playtesten om verschillende speelstijlen te experimenteren. In feite kun je experimenteren met het plaatsen van deurassets in je gevechtszones die alleen voor gebruikers van één kant van de deur openen, of helemaal niet.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek toe te passen op de deuren:

1.

Voeg alle deur  modulaire assets toe en configureer deze voor de deuropeningen van je gevechtszones.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Doors-2.jpg)

2.

OPTIONEEL

 Veranker al deze deurassets.

### [Externe assets](#externe-assets)[](#externe-assets)

Het oorspronkelijke greybox ontwerp voor externe assets was om tijdelijke posities in te stellen voor objecten die dekking bieden tegen vijandelijk vuur terwijl gebruikers de externe primaire baan navigeren. Dit was nuttig om te helpen visualiseren wat gebruikers zou helpen terwijl ze trappen op- of afgaan, de middelste gevechtszone oversteken, of anderszins in de buitenruimte bestaan, maar terwijl je je omgeving construeert, kun je dit ontwerp verbeteren door verschillende toepassingen voor deze dekkingsobjecten te bieden.

De volgende secties bieden richtlijnen over hoe je deze initiële tijdelijke assets kunt omzetten in esthetisch aantrekkelijke objecten die de kunststijl van je game volgen, en de intentie achter het oorspronkelijke ontwerp behouden.

#### [Torens](#torens)[](#torens)

De eerste externe assets die je kunt omzetten voor de buitenruimte zijn de twee torens direct buiten de middelste gevechtszone die de externe primaire baan kruisen. De techniek in deze sectie creëert niet alleen objecten die esthetisch aantrekkelijk zijn voor het oog, maar het creëert ook objecten die gebruikers een gevoel van schaal in hun omgeving bieden. Elk ander object tot nu toe is ongeveer de grootte van het karakter van de gebruiker behalve  voor deze torens, wat kan leiden tot intrige in het verhaal achter de architectuur of het algehele eiland waarop het gebouw zich bevindt.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek toe te passen op de torens:

1.

Gebruik blok  onderdelen om een toren te creëren die veel groter is dan de speler om een gevoel van schaal in de omgeving te bieden.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralTowers-1.jpg)

2.

Pas unieke kleuren en materialen toe op verschillende blokonderdelen volgens de kunststijl van je game.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Towers-1.jpg)

3.

Dupliceer deze toren, en positioneer deze op een symmetrische locatie op je kaart.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Towers-3.jpg)

4.

Veranker al deze onderdelen.

#### [Kolommen](#kolommen)[](#kolommen)

De tweede externe assets die je kunt omzetten voor de buitenruimte zijn de twee kolommen die de overhangstukken ondersteunen die je later in deze tutorial zult maken. Net als bij de torens, creëert de techniek in deze sectie niet alleen objecten die esthetisch aantrekkelijk zijn voor het oog, maar het biedt ook verdere visuele aanwijzingen aan gebruikers over waar ze zich bevinden in de algehele omgeving. Bijvoorbeeld, elke kolom heeft ofwel muntgroene of anjerroze details om gebruikers te informeren of ze het dichtst bij hun eigen of de spawnzone van hun vijand zijn.

Maak je eigen Recreëer het Voorbeeld

1.

Gebruik blok  en wig  onderdelen om een kolom te creëren die het dak van je gebouw zal ondersteunen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GeneralColumns-1.jpg)

2.

Pas unieke kleuren en materialen toe op verschillende onderdelen volgens de kunststijl van je game.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Columns-2.jpg)

3.

Dupliceer deze kolom, en positioneer deze op een symmetrische locatie op je kaart.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Columns-5.jpg)

4.

OPTIONEEL

 Verander de kleur van één onderdeel in elke kolom om overeen te komen met het respectieve kleurthema van elk team.

5.

Veranker al deze onderdelen.

#### [Plantenbakken](#plantenbakken)[](#plantenbakken)

De laatste externe assets die je kunt omzetten voor de buitenruimte zijn de acht plantenbakken die zich over de gehele lengte van de externe primaire baan uitstrekken. Met behulp van [solide modellering](/docs/nl-nl/parts/solid-modeling)  operaties, kun je onderdelen negateren en samenvoegen om de basis van elke plantenbak te vormen, en vervolgens je assetbibliotheek toepassen met verschillende materialen, loof, en/of trim assetconfiguraties zodat elke plantenbak uniek aanvoelt in de 3D ruimte.

Om je assetbibliotheek toe te passen op de meest linkse plantenbak:

1.

Voeg de volgende blok  onderdelen toe en configureer deze voor de meest linkse plantenbak:

| Onderdeel | | Grootte | | CFrame.Positie |
| --- | --- |
| Plantenbak buitenkant | | 20, 11, 5 | | -15, 4.5, 257.5 |
| Uitholling | | 18.5, 1, 4 | | -15, 9.75, 257.5 |

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-1.jpg)

2.

Selecteer het uithollingsonderdeel.

3.

Navigeer naar de Model  tabwerkbalk van Studio, en klik vervolgens op de Negate  knop. Het onderdeel wordt doorschijnend.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-3.jpg)

4.

Selecteer zowel het genegateerde onderdeel als het plantenbak buitenkant onderdeel.

5.

Klik in de Model  tabwerkbalk van Studio op de Union  knop. Het genegateerde onderdeel wordt uit het overlappende plantenbak buitenkant onderdeel gesneden.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-5.jpg)

6.

Selecteer de unie, en stel in het Eigenschappen  venster,

1.

Stel Kleur  in op 181, 173, 156 .

2.

Stel Materiaal  in op Concrete .

3.

Stel MateriaalVariant  in op Concrete_Board_Formed_A .

4.

Schakel UsePartColor  in.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-6.jpg)

7.

Voeg de volgende blok  onderdelen toe en configureer deze voor de aarde en rand van de plantenbak:

| Onderdeel | | Grootte | | CFrame.Positie | | CFrame.Orientatie | | Kleur | | Materiaal | | MateriaalVariant |
| Aarde | | 19, 0.5, 4 | | -15, 9.25, 257.5 | | 0, 0, 0 | | 248, 248, 248 | | LeafyGrass | | Moss_Lumpy_Stones_A |
| Bovenrand plantenbak | | 1.652, 1, 6.483 | | -24.838, 5.298, 257.741 | | 0, 0, 0 | | 181, 173, 156 | | Concrete | | Concrete_Tie_Holes_A |
| Onder rand plantenbak | | 6.483, 1.5, 19.652 | | -15.154, 1.479, 257.758 | | 0, 0, -21.62 | | 181, 173, 156 | | Concrete | | Concrete_Tie_Holes_A |

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-7.jpg)

8.

Voeg loofassets toe aan de bovenkant van de plantenbak om meer organisch leven aan de buitenruimte toe te voegen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-8.jpg)

9.

Veranker al deze onderdelen en loofassets.

Nu je weet hoe je de solide modelleringstools kunt gebruiken, kun je experimenteren met het creëren van soorten plantenbakken met verschillende exterieurs, materialen, plantvariëteiten en trimstukken. Bijvoorbeeld, de andere variaties van plantenbakken binnen de uiteindelijke voorbeeld laser tag omgeving maken ofwel een 'L'-vorm, of ze stapelen blok  onderdelen en witte trim samen om hogere dekking in het midden van de kaart te bieden.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-9.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-10.jpg)

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Planters-11.jpg)

### [Dak](#dak)[](#dak)

Het oorspronkelijke greybox ontwerp bevatte geen dak voor het gebouw omdat het je zou hebben verhinderd om je voortgang te zien terwijl je je driebaan kaartlay-out ontwierp en construeerde. Nu het interieur van het gebouw compleet is, buiten het configureren van de lichtbronnen, kun je je assetbibliotheek toepassen op nieuwe geometrie om het gebouw af te maken en gebruikers beschutting te bieden tegen de buitenruimte.

Het dak van het gebouw is een van de meest complexe assets in de uiteindelijke voorbeeld laser tag omgeving omdat het meerdere lagen bevat die met elkaar en met de interne geometrie moeten passen. De volgende instructies begeleiden je bij het construeren van elke laag, te beginnen met de bovenste geometrie tot de laatste laag trim die de omtrek van het dak omringt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Roof-Intro.jpg)

#### [Dakramen](#dakramen)[](#dakramen)

De eerste, bovenste laag van het dak is de dakraam geometrie. Het doel van deze laag is om buitenlicht in de interne gevechtsgebieden te bieden.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek toe te passen op de dakramen:

1.

Voeg alle dakraam  modulaire assets toe en configureer deze voor het plafond van je gebouw. Dit laat globale verlichting in gevechtsgebieden toe, en biedt een rijker gevoel van onderdompeling voor spelers.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Skylight-5.jpg)

2.

Gebruik blok  onderdelen om glas voor enkele van je dakramen te creëren.

1.

Voeg een blok  onderdeel toe en positioneer dit in een dakraam.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Skylight-6.jpg)

2.

Selecteer het onderdeel, en stel in het Eigenschappen  venster,

1.

Stel Kleur  in op 105, 162, 172 .

2.

Stel Materiaal  in op Neon .

3.

Stel Transparantie  in op 0.6 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Skylight-7.jpg)

3.

Veranker al deze dakraam-assets.

#### [Plafond](#plafond)[](#plafond)

De tweede laag van het dak is de plafondgeometrie die gebruikers zien aan de bovenkant van hun zicht terwijl ze het interieur van het gebouw navigeren. Het doel van deze laag is om de open gebieden tussen de bovenste trim van elk muuraset te vullen.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek op het plafond van het dak toe te passen:

1.

Gebruik blok  en wig  onderdelen om de open ruimte rond je lichtkoepels te vullen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Ceiling-3.jpg)

2.

Selecteer deze onderdelen, en stel in het Eigenschappen  venster Kleur , Materiaal , en/of MateriaalVariant  in op waarden die een onderscheidende visuele behandeling toepassen ten opzichte van andere oppervlakken in je omgeving. Dit helpt spelers zich te oriënteren wanneer ze hun camera snel bewegen.

3.

Veranker al deze plafondonderdelen.

#### [Bovenste dak](#bovenste-dak)[](#bovenste-dak)

De derde laag van het dak is de geometrie van het bovenste dak. Het doel van deze laag is om volume te geven aan het buitenste dakgebied dat gebruikers zien wanneer ze naar het gebouw kijken vanuit de buitenruimte. Het voegt ook een gevoel van diepte toe aan de lichtkoepels, waardoor het gebouw er van binnen en van buiten completer uitziet.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek op de bovenkant van het dak toe te passen:

1.

Gebruik blok  en wig  onderdelen om een dikke laag toe te voegen die het plafond bedekt zonder je lichtkoepels te verbergen. Dit oppervlak is wat spelers kunnen zien wanneer ze naar het gebouw kijken vanuit de buitenruimte.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/TopRoof-3.jpg)

2.

Selecteer deze onderdelen, en stel in het Eigenschappen  venster Kleur , Materiaal , en/of MateriaalVariant  in op waarden die een visuele behandeling toepassen volgens de kunststijl van je spel.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/TopRoof-4.jpg)

3.

Veranker al deze bovenste dakonderdelen.

#### [Overstek](#overstek)[](#overstek)

De vierde laag van het dak is de geometrie van de overstek die de kolomonderdelen ondersteunt om het gebouw structureel gezond te houden. Het doel van deze laag is om een esthetisch aangename luifelruimte te bieden voor gebruikers die de primaire buitenroute navigeren.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek op de overstek van het dak toe te passen:

1.

Gebruik blok  en wig  onderdelen om een dikke overstek toe te voegen die je kolommen ondersteunen. Dit oppervlak biedt spelers gedeeltelijke beschutting tegen de zon terwijl ze de primaire buitenroute navigeren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Overhang-4.jpg)

2.

Selecteer deze onderdelen, en stel in het Eigenschappen  venster Kleur , Materiaal , en/of MateriaalVariant  in op waarden die een visuele behandeling toepassen volgens de kunststijl van je spel.

3.

Veranker al deze overstekonderdelen.

#### [Trim](#trim)[](#trim)

De laatste laag van het dak is de trimgeometrie die de omtrek van het dak omringt. Het doel van deze laag is om visuele samenhang te bieden tussen elke vorige laag voor gebruikers die de kamer vanuit de buitenruimte bekijken.

Maak je eigen Recreëer het voorbeeld

Om je eigen assetbibliotheek op de trim van het dak toe te passen:

1.

Voeg trim  modulaire assets toe langs de overstek van je dak.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Trim-5.jpg)

2.

Selecteer deze onderdelen, en stel in het Eigenschappen  venster Kleur , Materiaal , en/of MateriaalVariant  in op waarden die een visuele behandeling toepassen volgens de kunststijl van je spel.

3.

Veranker al deze overstekonderdelen.

## [Verwijder overtollige geometrie](#verwijder-overtollige-geometrie)[](#verwijder-overtollige-geometrie)

Nu je gebouw compleet is, is het tijd om de onderliggende greybox-geometrie en de basisplaat te verwijderen. Dit proces verwijdert overtollige polygonen die gebruikers nooit zullen zien of mee zullen interageren, wat de geheugen- en prestatieverbetering voor apparaten met geheugen- en grafische verwerkingsunit (GPU) beperkingen snel verbetert. Bovendien zorgt het verwijderen van de basisplaat ervoor dat het gebouw in de lucht kan zweven, wat een goede voorbereiding is om terrein voor de buitenruimte te sculpten in de volgende sectie.

Om overtollige geometrie te verwijderen:

1.

Verwijder in het Explorer  venster alle greybox-geometrie uit de eerste sectie van deze tutorial.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DeletingGeo-1.png)

2.

Verwijder het basisplaatobject.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DeletingGeo-2.png)

## [Sculpt terrein](#sculpt-terrein)[](#sculpt-terrein)

Op dit moment is je omgeving voornamelijk architectonisch, afgezien van het loof in je plantenbakken. Echter, volgens de voorbeeldkunststijl van [Ontwikkel Gepolijste Assets](/docs/nl-nl/tutorials/curriculums/environmental-art/develop-polished-assets) , zou de 3D-ruimte een gezonde mix van futuristische technologie en weelderig groen moeten bevatten om gebruikers te informeren dat de wereld technologische vooruitgang waardeert, maar niet ten koste van de aarde.

Met de [Terrein Editor](/docs/nl-nl/parts/terrain)  kun je snel gedetailleerd en realistisch terrein genereren en sculpten om organisch leven aan de buitenruimte toe te voegen. Omdat je materiaaloverrides hebt ingesteld terwijl je je aangepaste materialen in [Stel een Assetbibliotheek samen](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library)  hebt gemaakt, kun je ook je tegelbare texturen gebruiken via Terrein Editor  penselen om mos, bloemen en stenen paden toe te voegen die samenhangend zijn met de rest van je omgeving.

Het sculpten van terrein is een kunstvorm, en het is moeilijk om penseelstreken en subtiele materiaalanpassingen exact te recreëren. Zolang je terrein voldoet aan de behoeften van je eigen spel, is het normaal en te verwachten dat je omgeving er anders uitziet en aanvoelt dan de voorbeeld laser tag omgeving.

Maak je eigen Recreëer het voorbeeld

Om je eigen terrein aan de buitenruimte toe te passen:

1.

Klik op Terrein  in het Home  tabblad van de werkbalk. Het [Terrein Editor](/docs/nl-nl/studio/terrain-editor)  venster opent.

2.

Navigeer naar het Bewerken  tabblad, en klik op de Teken  knop.

3.

In de sectie Borstelinstellingen , pas je borstel aan volgens het materiaal dat je aan je kaart wilt toevoegen. Bijvoorbeeld, het voorbeeld begint dit proces met de instellingen in de volgende afbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Terrain-3.jpg)

4.

In de sectie Materiaalinstellingen , selecteer een materiaal voor het onbespeelbare gebied , zoals water of gebroken lava, en teken vervolgens in de viewport waar je wilt dat je speelbare gebied eindigt. Dit materiaal communiceert waar de kaart eindigt voor de buitenruimte.

5.

Navigeer terug naar de sectie Materiaalinstellingen , selecteer een materiaal voor het speelbare gebied , zoals gras, asfalt of houten planken, en teken vervolgens in de viewport waar je wilt dat je speelbare gebied begint. Dit materiaal communiceert waar de kaart begint voor de buitenruimte.

6.

Navigeer terug naar de Terrein Editor , en selecteer de Verf  tool.

7.

In de sectie Borstelinstellingen , pas je borstel aan volgens het materiaal dat je aan je kaart wilt toevoegen, en selecteer een nieuw materiaal.

8.

Teken in de viewport langs de buitenste route. Dit materiaal communiceert het primaire pad dat spelers kunnen nemen terwijl ze de buitenruimte navigeren.

9.

(Optioneel)  Voeg en configureer eventuele toepasselijke props toe aan de buitenruimte voor visuele variatie.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/Terrain-10.jpg)

## [Beperk het speelbare gebied](#beperk-het-speelbare-gebied)[](#beperk-het-speelbare-gebied)

Als je je spel test en van het eiland navigeert, zal je personage vallen totdat ze de [Workspace.FallenPartsDestroyHeight](/docs/nl-nl/reference/engine/classes/Workspace#FallenPartsDestroyHeight)  van het project bereiken en weer in de spawnzone van je team verschijnen. Om ervoor te zorgen dat gebruikers niet van het eiland kunnen vallen, of te vroeg bij de wedstrijd kunnen komen vanuit de zwevende spawnzone voordat ze in teams scheiden, moet je het speelbare gebied omringen met een onzichtbare barrière.

De waarden in deze sectie zijn sterk afhankelijk van het terrein binnen de uiteindelijke voorbeeld laser tag omgeving. Het wordt aanbevolen om te playtesten en te verifiëren dat er geen gaten in de barrière zijn volgens het aangepaste terrein binnen je eigen spel.

Maak je eigen Recreëer het voorbeeld

Om het speelbare gebied in je spel te beperken:

1.

Gebruik blok  onderdelen om het speelbare gebied in je buitenruimte te omringen. Het is belangrijk om ervoor te zorgen dat deze onderdelen hoog genoeg zijn om spelers te blokkeren zodat ze niet over je barrière kunnen springen, en dat er geen kieren zijn waar ze doorheen kunnen glippen en van de rand van je kaart kunnen vallen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ContainingPlayableArea-1.jpg)

2.

Selecteer deze onderdelen, en stel in het Eigenschappen  venster,

1.

Stel Transparantie  in op 1 .

2.

Schakel Kan Botsen  uit.

3.

Schakel Verankerd  in.

## [Configureer speciale effecten](#configureer-speciale-effecten)[](#configureer-speciale-effecten)

De architectuur van je gebouw en de buitenruimte zijn bijna compleet met assets uit je assetbibliotheek, maar je hebt misschien opgemerkt dat de algehele omgeving statisch aanvoelt, of dat nu bewust of onbewust is. Dit komt omdat realistische omgevingen beweging van veel verschillende bronnen bevatten, of dat nu van wolken is die door de lucht kruipen, wind die door het groen waait, of levensvormen die de ruimte navigeren.

Je kunt realistische omgevingen nabootsen door speciale effecten te configureren die dynamische beweging aan je omgeving toevoegen en emotie bij gebruikers oproepen. Dit proces zorgt er vaak voor dat werelden levendiger aanvoelen, wat een diep gevoel van onderdompeling ondersteunt terwijl mensen toegang hebben tot je spel.

### [Achtergrondwolken](#achtergrondwolken)[](#achtergrondwolken)

Het eerste type speciale effect dat de uiteindelijke voorbeeld laser tag omgeving gebruikt om beweging aan de 3D-ruimte toe te voegen, is een effect dat dynamische wolken wordt genoemd. [Dynamische wolken](/docs/nl-nl/environment/clouds)  zijn realistische wolken die langzaam door de lucht drijven, en ze zijn nuttig voor het creëren van beweging die ver weg van de gebruiker voelt, maar nog steeds aanwezig is in de omgeving. Je kunt hun uiterlijk aanpassen via het [Clouds](/docs/nl-nl/reference/engine/classes/Clouds)  object om unieke sferen te creëren, en hun richting en snelheid aanpassen via globale wind.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-Intro1.jpg) Zonder dynamische wolken

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-Intro2.jpg) Met standaard dynamische wolken

Maak je eigen Recreëer het voorbeeld

Om je eigen dynamische wolken op de achtergrond toe te voegen en te configureren:

1.

In het Explorer  venster, voeg een Clouds  object toe aan het Terrain  object.

1.

Beweeg de muis boven het Terrain  object en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu een Clouds  object.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-1.jpg)

2.

Selecteer het Clouds  object, en in het Properties  venster,

1.

Stel Cover  in op een waarde tussen 0  (geen wolken) en 1  (volledige bewolking).

2.

Stel Density  in op een waarde tussen 0  (lichte, doorschijnende wolken) en 1  (zware, donkere wolken).

3.

Stel Color  in op een materiaal kleur van wolken deeltjes volgens de kunststijl van je spel.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/BackgroundClouds-2.jpg)

### [Voorkeurswolken](#voorkeurswolken)[](#voorkeurswolken)

Het tweede type speciale effect dat de uiteindelijke voorbeeld laser tag omgeving gebruikt om beweging aan de 3D ruimte toe te voegen, is een effect dat deeltjesemitteren wordt genoemd. [Deeltjesemitteren](/docs/nl-nl/effects/particle-emitters)  stoten 2D afbeeldingen, of deeltjes, uit die eruit zien en zich gedragen volgens de ingestelde eigenschappen van de deeltjesemitter gedurende hun levensduur, en ze zijn nuttig voor het creëren van beweging die aanvoelt en vaak dicht bij de gebruiker is.

Deeltjesemitteren hebben veel eigenschappen die je kunt aanpassen om zowel subtiele als gedurfde effecten te bereiken. De volgende instructies laten je zien hoe je de voorkeurswolken precies kunt recreëren binnen het voorbeeld [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  plaatsbestand, maar je kunt elke eigenschap aanpassen aan de behoeften van je eigen spel. Het wordt aanbevolen om deze wolken groot te houden en met een zachte beweging tussen de gameplay ruimte en de statische achtergrond.

Om voorkeurswolken toe te voegen en te configureren:

1.

Voeg een block  onderdeel toe op een positie waar je wilt dat gebruikers een zwevende wolk zien.

2.

Selecteer dit block  onderdeel, en in het Properties  venster,

1.

Stel Transparency  in op 1 .

2.

Schakel CanCollide  uit.

3.

Schakel Anchored  in.

3.

Maak een deeltjesemitter binnen dit onderdeel.

1.

In het Explorer  venster, beweeg de muis boven het block  onderdeel en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu een ParticleEmitter . De deeltjesemitter stoot onmiddellijk deeltjes uit binnen het gebied van het onderdeel.

4.

Selecteer deze deeltjesemitter, en in het Properties  venster,

1.

Stel Color  in op een kleursequentie die eruit ziet als de volgende afbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ForegroundClouds-4a.png)

2.

Stel LightEmission  in op 0.3  om de kleuren van de textuur en zijn omgeving te mengen.

3.

Stel LightInfluence  in op 0.2  om omgevingslicht een subtiele invloed op de kleur van de deeltjes te laten hebben.

4.

Stel Orientation  in op FacingCameraWorldUp  zodat de deeltjes altijd omhoog naar de lucht worden uitgestoten.

5.

Stel Size  in op 100  om grote wolken te creëren.

6.

Stel Squash  in op -0.25  om de deeltjes horizontaal te verkleinen.

7.

Stel Texture  in op een afbeelding van een wolk. Het voorbeeld gebruikt rbxassetid://10714362544 .

8.

Stel Transparency  in op een nummersequentie die eruit ziet als de volgende afbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ForegroundClouds-4b.png)

9.

Stel Lifetime  in op 30  om de deeltjes na 30 seconden te laten vervagen.

10.

Stel Rate  in op 0.25  om de deeltjes langzaam uit te stoten.

11.

Stel Acceleration  in op 0, -0.8, 0  om de snelheid van de deeltjes gedurende hun levensduur te beïnvloeden.

12.

Stel Drag  in op 0.1  om de deeltjes hun snelheid in de loop van de tijd te laten zien.

13.

Schakel LockedToPart  in om de deeltjes dicht bij de deeltjesemitter te houden.

5.

Herhaal dit proces door de deeltjesemitter voor wolken door de omgeving te verplaatsen.

Daarnaast kun je meerdere deeltjesemitteren samenvoegen om de wolken meer diepte te geven. Bijvoorbeeld, in de uiteindelijke voorbeeld laser tag omgeving, lagen de voorkeurswolken een extra deeltjesemitter met een Color  eigenschap van 248, 248, 248 , Texture  eigenschap van rbxassetid://10714433747 , en een Rate  eigenschap van 0.1 . Je kunt beide deeltjesemitteren vinden in de voorbeeld [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library) .

  ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/ForegroundClouds-5.jpg)

### [Stofdeeltjes](#stofdeeltjes)[](#stofdeeltjes)

Deeltjesemitteren zijn een veelzijdig type speciaal effect omdat ze zoveel eigenschappen bieden die je kunt aanpassen om interessante visuele effecten te creëren, zoals gloeiende poorten, groene rook of levendige explosies. De uiteindelijke voorbeeld laser tag omgeving gebruikt opnieuw deeltjesemitteren in deze sectie om zwevende stofdeeltjes te creëren die de gebruiker omringen terwijl ze de buitenruimte navigeren.

Vergelijkbaar met de stappen voor de voorkeurswolken, laten de volgende instructies je zien hoe je de stofdeeltjes precies kunt recreëren binnen het voorbeeld [Environment Art - Constructing](https://www.roblox.com/games/14447826396/Environment-Art-Constructing)  plaatsbestand, maar je kunt elke eigenschap aanpassen aan de behoeften van je eigen spel. Het wordt aanbevolen om de snelheid van de deeltjes laag te houden om alleen microbeweging binnen de omgeving te bieden.

Om stofdeeltjes voor de buitenruimte toe te voegen en te configureren:

1.

Voeg een block  onderdeel toe aan de omgeving dat het hele eiland bedekt.

2.

Selecteer dit block  onderdeel, en in het Properties  venster,

1.

Stel Transparency  in op 1 .

2.

Schakel CanCollide  uit.

3.

Schakel Anchored  in.

3.

Maak een deeltjesemitter binnen dit onderdeel.

1.

In het Explorer  venster, beweeg de muis boven het block  onderdeel en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu een ParticleEmitter . De deeltjesemitter stoot onmiddellijk deeltjes uit binnen het gebied van het onderdeel.

4.

Selecteer deze deeltjesemitter, en in het Properties  venster,

1.

Stel Color  in op 192, 241, 255  om de deeltjes een lichtblauwe tint te geven.

2.

Stel Size  in op een nummersequentie die eruit ziet als de volgende afbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DustParticles-4b.png)

3.

Stel Texture  in op een afbeelding van een stofdeeltje. Het voorbeeld gebruikt rbxassetid://14302399641 .

4.

Stel Transparency  in op een nummersequentie die eruit ziet als de volgende afbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/DustParticles-4d.png)

5.

Stel ZOffset  in op -5  om de deeltjes van de camera weg te bewegen.

6.

Stel Lifetime  in op 1, 10  om de minimum en maximum leeftijd van een deeltje op respectievelijk 1 en 10 seconden in te stellen.

7.

Stel Rate  in op 50000  om veel deeltjes voor je omgeving te creëren.

8.

Stel RotSpeed  in op -60  om een bereik van snelheden voor nieuw uitgezonden deeltjes te creëren.

9.

Stel Speed  in op 1, 5  om de minimum en maximum snelheid van een deeltje op respectievelijk 1 en 5 studs per seconde in te stellen.

10.

Stel Acceleration  in op 1, -1, 1  om de snelheid van de deeltjes gedurende hun levensduur te beïnvloeden.

11.

Schakel LockedToPart  in om de deeltjes dicht bij de deeltjesemitter te houden.

## [Configureer lichtbronnen](#configureer-lichtbronnen)[](#configureer-lichtbronnen)

Nu je omgeving beweging heeft, is de laatste stap in het construeren van je omgeving het configureren van lichtbronnen. Studio biedt twee hoofdcategorieën van lichtbronnen:

-

Globale verlichting  - Produceert verlichting voor de hele buitenomgeving.

-

Lokale verlichting  - Produceert verlichting rond waar je ze plaatst binnen je spel.

Beide lichtbronnen zijn belangrijk om te overwegen omdat je spel zowel een binnen- als buitenomgeving heeft die de mogelijkheid van de gebruiker beïnvloeden om te zien wat er om hen heen gebeurt terwijl ze in gevecht zijn.

### [Globale verlichting](#globale-verlichting)[](#globale-verlichting)

Globale verlichting is de luminescentie van de zon of de maan in een spel. Door een paar belangrijke standaard eigenschappen in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service aan te passen, kun je dramatisch veranderen hoe dat licht aan gebruikers verschijnt, evenals hoe het interactie heeft met elk ander object dat je in het spel plaatst.

Studio begint elk spel met [Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting die een plattere uitstraling met zachtere lichten en schaduwen geeft. Om de omgeving te verbeteren en je lokale lichtbronnen in staat te stellen om precieze schaduwen en verlichting te produceren, zoals de verlichting in de gangen en boven de borden, moet je [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting inschakelen. Dit stelt zowel je globale als lokale verlichting in staat om samen te werken en meer realistische en meeslepende visuals te bieden.

Bijvoorbeeld, de [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingsstijl detecteert automatisch wanneer een gebruiker zich in een binnen- of buitenruimte bevindt, en reageert door het juiste verlichtingsmodel in te schakelen. Dit betekent dat reflecties kunnen weerkaatsen van de vloer en het plafond binnen het gebouw, wat een rijkere visuele ervaring biedt terwijl gebruikers door gevechtspockets navigeren.

Maak je eigen Recreëer het voorbeeld

Om je eigen globale verlichting te configureren:

1.

In het Explorer  venster, selecteer de Lighting  service, en in het Properties  venster, stel de eigenschappen in op waarden die de kunststijl van je spel weerspiegelen. Voor meer informatie over deze eigenschappen, zie [Globale verlichting](/docs/nl-nl/environment/lighting) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GlobalLighting-1.jpg)

2.

In het Explorer  venster, selecteer het kind Atmosphere  object van de Lighting  service, en in het Properties  venster, stel de eigenschappen in op waarden die de kunststijl van je spel weerspiegelen. Voor meer informatie over deze eigenschappen, zie [Atmosferische effecten](/docs/nl-nl/environment/atmosphere) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GlobalLighting-2.jpg)

3.

OPTIONEEL

 Pas een of meer aanpasbare filters toe, zoals bloom, scherptediepte of zonnestralen. Voor meer informatie over deze eigenschappen, zie [Post-processing effecten](/docs/nl-nl/environment/post-processing-effects) .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/GlobalLighting-4.jpg)

### [Lokale verlichting](#lokale-verlichting)[](#lokale-verlichting)

Lokale verlichting is de luminescentie van lokale [lichtbronnen](/docs/nl-nl/effects/light-sources)  in je spel, zoals [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight) , en [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  objecten. Het is belangrijk om de behoeften van je spel te analyseren om te weten welke type lokale lichtbron je moet gebruiken. Bijvoorbeeld, de uiteindelijke voorbeeld laser tag omgeving heeft verlichting nodig om gebruikers te helpen de verschillende gebieden binnen het gebouw te zien terwijl ze in gevecht zijn, evenals verlichting om de verschillende spawnzonegebieden te onderscheiden.

Lokale lichtbronnen creëren referentiepunten en richting voor gebruikers. Bijvoorbeeld, het voorbeeld gebruikt oppervlakte lichten om gebruikers te informeren of ze de omtrek navigeren of dicht bij de blauw-groene of roze spawnzone zijn, en schijnwerpers om deuropeningen te benadrukken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-Intro.jpg)

Het toepassen van lichtbronnen is een kunstvorm, en het kost tijd om uit te vinden welke verlichtingsconfiguraties werken om aan de behoeften van je spel te voldoen. Het is normaal en te verwachten dat je verlichting er anders uitziet en aanvoelt dan de uiteindelijke voorbeeld laser tag omgeving.

Maak je eigen Recreëer het voorbeeld

Om je eigen lokale verlichting te configureren:

1.

Voeg gloeiende lichten toe en configureer ze rond de omtrekgangen die oriëntatie aanwijzingen bieden aan gebruikers die zich door het gebouw navigeren.

1.

Voeg een block  onderdeel toe en positioneer het nabij de bovenkant van een van je omtrekgangen, en in het Properties  venster,

1.

Stel Color  in op een heldere kleur.

2.

Stel Material  in op Neon .

3.

Schakel Anchored  in.

2.

In het Explorer  venster, voeg een SurfaceLight  object toe aan het onderdeel.

1.

Beweeg de muis boven het onderdeel en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu een SurfaceLight  object.

3.

Selecteer het SurfaceLight  object, en in het Properties  venster,

1.

Stel Color  in op een heldere kleur.

2.

Stel Face  in op de richting waarin je wilt dat het licht schijnt.

3.

Stel Range  in op een waarde die weerspiegelt hoe ver je wilt dat je licht reikt.

4.

Herhaal dit proces, positioneer en oriënteer onderdelen om de gloeiende omtreklampen te voltooien.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-1.jpg)

2.

Voeg en configureer kleine binnenverlichting in de gangen die de kruislijnen verlichten.

1.

Voeg een block  onderdeel toe en positioneer het nabij de bovenkant van een van je kruislijn gangen, en in het Properties  venster,

1.

Stel Color  in op een heldere kleur.

2.

Stel Material  in op Neon .

3.

Schakel Anchored  in.

2.

In het Explorer  venster, voeg een SpotLight  object toe aan het onderdeel.

1.

Beweeg de muis boven het onderdeel en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu een SpotLight  object.

3.

Selecteer het SpotLight  object, en in het Properties  venster,

1.

Stel Angle  in op een waarde die weerspiegelt de hoek waarin je wilt dat je licht schijnt.

2.

Stel Face  in op de richting waarin je wilt dat het licht schijnt.

3.

Stel Range  in op een waarde die weerspiegelt hoe ver je wilt dat je licht reikt.

4.

Herhaal dit proces, positioneer en oriënteer onderdelen boven deuren en gangen totdat je tevreden bent met de binnenverlichting.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-2.jpg)

3.

Voeg en configureer de spawnzone lichten.

1.

Voeg een block  onderdeel toe dat de grootte van je linker spawnzone heeft, en positioneer het boven het plafond van de spawnzone.

2.

In het Properties  venster,

1.

Stel Color  in op het kleurthema van het team aan de linkerkant van de kaart.

2.

Stel Material  in op Neon .

3.

Schakel Anchored  in.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-3a.jpg)

1.

Herhaal dit proces voor de rechter spawnzone.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-3B.jpg)

1.

OPTIONEEL

 Voeg en veranker lichtarmaturen rond de binnen- en buitenkant van het gebouw vanuit je eigen assetbibliotheek.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section4/LocalLighting-4.jpg)

Zodra je tevreden bent met het uiterlijk en gevoel van je omgeving, kun je verder gaan met het configureren van je assets en Studio-instellingen om je framerate en prestatie niveaus hoog te houden voor low-end apparaten. Dit proces zorgt ervoor dat bijna elke gebruiker dezelfde gameplay en visuele ervaring heeft terwijl ze je omgeving bekijken.

[Volgende](/docs/nl-nl/tutorials/curriculums/environmental-art/optimize-your-experience)[Vorige](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
