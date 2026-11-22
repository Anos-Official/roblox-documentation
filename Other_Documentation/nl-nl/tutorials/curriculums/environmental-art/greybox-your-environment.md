<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/environmental-art/greybox-your-environment -->

Greybox je omgeving | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Greybox je omgeving

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Greyboxen van je omgeving , ook wel massing out of blocking van je omgeving genoemd, is het proces van het toevoegen van eenvoudige vormen aan de 3D-ruimte om te begrijpen hoe gebruikers de gameplay zullen ervaren voordat er tijd wordt geïnvesteerd in het verfijnen van activa. Dit proces is cruciaal voor het vinden van problemen in de indeling van speelbare gebieden, zoals moeilijk te traverseren regio's, oneerlijke voordelen vanuit bepaalde uitkijkpunten, of activa met een onevenredige schaal ten opzichte van het karakter van de gebruiker.

Met behulp van het [Environment Art - Greyboxing](https://www.roblox.com/games/14447721254/Environment-Art-Greyboxing)  .rbxl -bestand als referentie, laat deze sectie van het curriculum voor milieukunst zien hoe je een standaard drie-lanen kaartindeling voor een team-gebaseerd first-person laser tag shooter spel kunt greyboxen, inclusief stapsgewijze instructies over:

-

Het creëren van speelbare gebieden die strategische gevechten voor meerdere speelstijlen aanmoedigen.

-

Het toepassen van tijdelijke materialen die gebruikers helpen hun positie en oriëntatie te begrijpen.

-

Het testen van de indeling om ervoor te zorgen dat het leuk is en geen speelbaarheidproblemen bevat.

Nadat je deze sectie hebt voltooid, leer je hoe je hoogwaardige activa kunt ontwikkelen om de greybox-omgeving te vervangen of om te zetten, en om te voldoen aan de ontwerpeisen van je spel.

 ![Een schuine bovenaanzicht van de uiteindelijke greybox-omgeving met tijdelijke materialen om unieke secties van de kaart aan te geven.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/PlaceholderMaterials.jpg)

## [Drie-lanen kaartindeling](#drie-lanen-kaartindeling)[](#drie-lanen-kaartindeling)

De drie-lanen kaartindeling  is een first-person shooter kaartindeling die een spawnzone voor elk team aan tegenovergestelde zijden van de kaart omvat, drie primaire lanes die elk team kan gebruiken om naar een van de spawnzones te reizen, en kruislanen die gebruikers in staat stellen van de ene primaire lane naar de andere te reizen. Dit type kaartindeling is een veelvoorkomende indeling voor first-person shooter games omdat het gebruikers snel in gevechtszones plaatst zodra ze een wedstrijd joinen, en het biedt een verscheidenheid aan speelstijlen afhankelijk van welke primaire lane gebruikers kiezen te volgen.

De volgende secties leggen elk onderdeel van de drie-lanen kaartindeling uit, inclusief overwegingen over hoe elk onderdeel samenwerkt om opzettelijke gameplay-interacties binnen first-person shooter games te creëren.

### [Spawnzones](#spawnzones)[](#spawnzones)

Spawnzones  zijn gebieden van de kaart waar gebruikers zich ofwel bij hun team voegen aan het begin van een wedstrijd, of opnieuw deelnemen aan de gameplay nadat hun gezondheid nul bereikt. Minimaal moet elk team een centrale spawnzone hebben wanneer gebruikers zich voor het eerst bij het spel voegen. Veel ontwikkelaars plaatsen deze centrale spawnzones aan tegenovergestelde uiteinden van hun kaarten om gebruikers tijd te geven om het spel te navigeren aan het begin van de wedstrijd voordat ze het vijandige team zien.

 ![Een bovenaanzicht van de basisplaat met de spawnzone van elk team gemarkeerd aan tegenovergestelde zijden van de kaart.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/ThreeLaneLayout-SpawnZones.jpg)

Bovendien bevatten veel team-gebaseerde first-person shooter games ook spawnzones door de kaart heen waar gebruikers willekeurig kunnen respawnen zodra hun gezondheid nul bereikt. De plaatsing van deze gedecentraliseerde spawnzones kan de moeilijkheidsgraad van het spel aanzienlijk verhogen, vooral wanneer je spawnzones dicht bij gebieden met zware gevechten plaatst. Om de gameplay eenvoudig te houden, bevat de voorbeeld laser tag greybox-omgeving slechts één centrale spawnzone voor elk team.

### [Primaire lanes](#primaire-lanes)[](#primaire-lanes)

Primaire lanes  zijn paden die de lengte van de kaart van de ene spawnzone naar de andere uitstrekken. De drie-lanen kaartindeling omvat drie primaire lanes, en hoe ontwikkelaars ze conceptualiseren is vaak afhankelijk van de algehele context van de omgeving van het spel. Bijvoorbeeld, omdat de voorbeeld laser tag kaart zowel een binnen- als buitenomgeving heeft, zijn de namen van de primaire lanes als volgt:

-

Interieur  - De binnenste lane die het verst van de ingang van het gebouw ligt.

-

Midden  - De lane die tussen de binnen- en buitenste primaire lanes ligt.

-

Exterieur  - De lane die het dichtst bij de ingang van het gebouw ligt en gedeeltelijk binnen en buiten is.

Voor de meeste first-person shooter games die de drie-lanen kaartindeling gebruiken, kruist de middelste primaire lane gebieden van de kaart die de meeste gevechten bevatten omdat gebruikers die de middelste primaire lane volgen, vanuit zowel de binnen- als buitenste primaire lanes kunnen worden aangevallen, terwijl gebruikers die de binnen- of buitenste primaire lanes volgen, alleen vanuit de middelste primaire lane kunnen worden aangevallen.

 ![Een bovenaanzicht van de basisplaat met drie primaire lanes gemarkeerd tussen de spawnzone van elk team aan tegenovergestelde zijden van de kaart.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/ThreeLaneLayout-PrimaryLanes.jpg)

### [Kruislanen](#kruislanen)[](#kruislanen)

Kruislanen  zijn paden die alle primaire lanes kruisen, van de binnenste naar de buitenste primaire lane. Dit zijn de paden die gebruikers kunnen gebruiken om van de ene primaire lane naar de andere te reizen, en ze bevatten vaak minimale obstructies om gebruikers te helpen dekking te zoeken tegen vijandelijk vuur. Dit komt omdat zones zonder dekking transitorische ruimtes creëren die gebruikers aanmoedigen om niet te lang op één plek te blijven zonder dat het gevaarlijk is.

 ![Een bovenaanzicht van de basisplaat met drie primaire lanes tussen de spawnzone van elk team aan tegenovergestelde zijden van de kaart, evenals vijf kruislanen die met de primaire lanes kruisen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/ThreeLaneLayout-CrossLanes.jpg)

Net als de reden waarom de meeste gevechten zich rond de middelste primaire lane voordoen, bevatten gebieden waar kruislanen met de middelste primaire lane kruisen, of gevechtsholtes , de meeste gevechten omdat ze gebruikers die van de binnen- of buitenste lanes komen, in staat stellen toegang te krijgen tot en te schieten in de middelste lane, en gebruikers die de middelste lane volgen kunnen in de richting van zowel de binnen- als buitenste lane schieten.

 ![Een bovenaanzicht van de basisplaat met drie primaire lanes tussen de spawnzone van elk team aan tegenovergestelde zijden van de kaart, evenals vijf kruislanen die met de primaire lanes kruisen. De kruispunten tussen de primaire en kruislanen zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/ThreeLaneLayout-IntersectingPoints.jpg)

Het bouwen van een drie-lanen kaartindeling met deze gevechtsholtes in gedachten stelt je in staat om de afstand van spawnzones te segmenteren en opzettelijke ruimtes te creëren waar gebruikers met elkaar moeten interageren. Dit moedigt gebruikers aan om deel te nemen aan snelle gameplay en snel vertrouwd te raken met de kaart terwijl ze tussen primaire lanes springen met behulp van kruislanen.

## [Creëer speelbare gebieden](#creëer-speelbare-gebieden)[](#creëer-speelbare-gebieden)

Nu je bekend bent met drie-lanen kaartindelingen, is het tijd om te leren hoe je de speelbare gebieden voor de voorbeeld laser tag greybox-omgeving kunt creëren die een drie-lanen kaartindeling volgt. Terwijl je deze instructies volgt die de geometrie binnen het voorbeeld [Environment Art - Greyboxing](https://www.roblox.com/games/14447721254/Environment-Art-Greyboxing)  .rbxl -bestand exact recreëren, begin je te zien hoe alles samenwerkt om twee spawnzones, drie primaire lanes en vijf kruislanen te vormen die zich spiegelen over het midden van de kaart wanneer je er van bovenaf naar kijkt.

 ![Een bovenaanzicht van de uiteindelijke greybox-geometrie met drie primaire lanes tussen de spawnzone van elk team aan tegenovergestelde zijden van de kaart, evenals vijf kruislanen die met de primaire lanes kruisen. De kruispunten tussen de primaire en kruislanen zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/CreatingPlayableAreas-Intro1.jpg)

De volgende instructies bieden twee verschillende instructiepaden: je kunt ofwel onderdelen invoegen om je eigen unieke laser tag-omgeving weer te geven, of je kunt onderdelen invoegen op een manier die de greybox-omgeving binnen het voorbeeld [Environment Art - Greyboxing](https://www.roblox.com/games/14447721254/Environment-Art-Greyboxing)  plaatsbestand exact recreëert.

Als je de geometrie aanpast om aan de specificaties van je eigen spel te voldoen, houd er dan rekening mee dat het voorbeeldbestand elke deur en gang minimaal 10 studs breed houdt, en elke muur minimaal 10 studs hoog. Deze parameters zorgen ervoor dat twee gebruikers gelijktijdig door gangen en deuren kunnen passeren, niemand over muren kan springen met de standaard spronghoogte van Roblox van 5 studs, en dat de camera veilig de kaart kan manoeuvreren zonder in de geometrie te interfereren.

 ![In een deur, zijn twee hagedis-avatar's op elkaar gestapeld aan de linkerkant, en twee blokachtige avatar's zijn op elkaar gestapeld aan de rechterkant. Dit demonstreert dat slechts twee karakters elkaar in een deur kunnen passeren, en ze kunnen niet hoger springen dan de muren.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/CreatingPlayableAreas-Intro2.png)

### [Vloergeometrie](#vloergeometrie)[](#vloergeometrie)

De eerste stap in het creëren van de laser tag greybox-omgeving is het creëren van de geometrie voor elk van de volgende vloeren:

-

Hoofdvloer  – Strekt zich uit van de ene spawnzone naar de andere.

-

Mezzaninevloer  – Strekt zich uit over de helft van de middelste gevechtsholte en biedt een verhoging in hoogte.

-

Buitenvloer  – Strekt zich uit over de buitenruimte en biedt een daling in hoogte.

Om de geometrie van elke vloer die je voor het spel creëert te visualiseren, verwijs je naar de volgende afbeelding die de hoofdvloer in geel markeert, de mezzaninevloer in rood, en de buitenvloer in blauw.

 ![Een bovenaanzicht van de uiteindelijke greybox-omgeving met tijdelijke materialen om de hoofd-, mezzanine- en buitenvloeren aan te geven.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Floor-Intro.jpg)

Het is belangrijk om ruimtes in het spel te hebben met pieken en dalen omdat dit je in staat stelt om zichtlijnen en engagementafstanden gedurende het spel buiten de horizontale beweging te controleren. Bijvoorbeeld, als de hele speelbare ruimte een enkele vloer was zonder hoogteverschil, zou elke gebruiker met elkaar kunnen interageren zolang er geen muur in de weg stond, wat betekent dat er weinig mogelijkheid is voor de gebruiker om een strategie te ontwikkelen buiten het niet gezien worden door andere gebruikers. Echter, met pieken en dalen kun je beslissen waar gebruikers elkaar kunnen zien.

Bovendien creëert een verhoging in hoogte zowel een fysieke als emotionele sensatie van stijging, waardoor gebruikers met een hoge positie een vogelperspectief op het slagveld hebben om een beter gevoel te krijgen van waar ze als volgende naartoe moeten. Wanneer ze klaar zijn om verder te gaan, creëert de daling in hoogte zowel een fysieke als emotionele sensatie van daling, waardoor gebruikers worden aangemoedigd om snelle beslissingen te nemen om zich rond de zichtlijnen van vijanden te manoeuvreren en hun doelen te bereiken.

Creëer je eigen Recreëer het voorbeeld

Om je eigen vloergeometrie te creëren:

1.

Open Roblox Studio met een Basisplaat -template.

2.

Navigeer naar de Home  of Model  tabwerkbalk van Studio, stel vervolgens [transformeren van onderdelen](/docs/nl-nl/parts#onderdelen-transformeren)  in op 5 studs  en 90° . Dit stelt je in staat om alle greybox-geometrie gelijkmatig op of van elkaar te positioneren in stappen van 5 studs.

3.

Gebruik blok  onderdelen om symmetrische linker- en rechteroppervlakken voor de hoofdvloer  van je gebouw te creëren. Deze geometrie vertegenwoordigt de lengte van je speelbare interieur, en de symmetrie geeft het midden van de kaart aan.

 ![Een schuine bovenaanzicht van de greybox-geometrie van de hoofdvloer gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralFloor-1.jpg)

4.

Gebruik blok  onderdelen om symmetrische linker- en rechteroppervlakken voor de mezzaninevloer  van je gebouw te creëren. Deze geometrie vertegenwoordigt de hoogste grond op de kaart.

 ![Een schuine bovenaanzicht van zowel de hoofd- als mezzaninevloeren. De greybox-geometrie van de mezzaninevloer is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Floor-3.jpg)

5.

Gebruik wedge  onderdelen om een verhoging in hoogte  te creëren tussen de hoofd- en mezzaninevloeren. Deze geometrie doorbreekt de zichtlijnen voor spelers die de binnenste primaire lane volgen, of de kruis lane in het midden van de kaart.

 ![Een schuine bovenaanzicht van zowel de hoofd-, mezzaninevloer, en verhoging in hoogte onderdelen. De greybox-geometrie van de verhoging in hoogte is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Floor-4.jpg)

6.

Gebruik wedge  onderdelen om een daling in hoogte  te creëren tussen de hoofd- en buitenvloer. Deze geometrie is je buitenste primaire lane, en het daalt naar het laagste punt op de kaart.

 ![Een schuine bovenaanzicht van zowel de hoofd-, mezzaninevloer, en verhoging en daling in hoogte onderdelen. De greybox-geometrie van de daling in hoogte is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Floor-5.jpg)

7.

Veranker al je onderdelen.

### [Geometrie van de perimeterwand](#geometrie-van-de-perimeterwand)[](#geometrie-van-de-perimeterwand)

De tweede stap in het creëren van de laser tag greybox-omgeving is het creëren van de geometrie voor de perimeterwanden van het gebouw. Dit biedt grenzen voor de interne gameplay van het spel, evenals begeleiding voor gebruikers over waar ze naartoe kunnen gaan om met elkaar te interageren.

Om de geometrie van de perimeterwanden van het gebouw dat je voor het spel creëert te visualiseren, verwijs je naar de volgende afbeelding die ze in geel markeert.

 ![Een bovenaanzicht van de uiteindelijke greybox-omgeving met de geometrie van de perimeterwand gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Perimeter-Intro.jpg)

Creëer je eigen Recreëer het voorbeeld

Om je eigen geometrie van de perimeterwand te creëren:

1.

Gebruik blok  onderdelen om een perimetergrens  rond je hoofdvloer te creëren, behalve voor de rand die opent naar de buitenste primaire lane. Deze geometrie voorkomt dat spelers je speelbare gebied verlaten terwijl ze het gebouw kunnen binnenkomen en verlaten.

 ![Een schuine bovenaanzicht van de vloer en perimeterwanden. De geometrie van de perimeterwand is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralPerimeter-1.jpg)

2.

Veranker deze onderdelen.

### [Geometrie van de spawnzone](#geometrie-van-de-spawnzone)[](#geometrie-van-de-spawnzone)

De derde stap in het creëren van de laser tag greybox-omgeving is het creëren van de geometrie om elke spawnzone van elk team te bevatten. Voor spellen die alleen gecentraliseerde spawnzones bevatten, laat het opdelen in hun eigen kamers gebruikers acclimatiseren aan het spel wanneer ze zich voor het eerst bij de wedstrijd voegen, en biedt het hen dekking tegen vijandelijk vuur wanneer ze opnieuw deelnemen aan de wedstrijd nadat hun gezondheid nul bereikt.

Er zijn twee spawnzones in het [Environment Art - Greyboxing](https://www.roblox.com/games/14447721254/Environment-Art-Greyboxing)  .rbxl -bestand, één voor elk team dat een gebruiker kan joinen, en ze bevinden zich aan tegenovergestelde uiteinden van de kaart. Elke spawnzone heeft twee uitgangspunten waar gebruikers voor kunnen kiezen om het hoofdgameplaygebied binnen te gaan, wat snelle toegang tot twee primaire lanes mogelijk maakt, en biedt dekking tegen vijandelijk vuur van gebruikers binnen de kruis lane nabij de spawnzone. Het hebben van twee uitgangspunten is belangrijk omdat een enkel uitgangspunt zou resulteren in een bottleneck van gebruikers die proberen de spawnzone binnen of buiten te gaan, en drie spawnzones zouden niet genoeg dekking bieden tegen vijandelijk vuur na het begin van de wedstrijd.

 ![Een schuine bovenaanzicht van een spawnzone met pijlen die naar de twee uitgangspunten wijzen en alle paden die gebruikers kunnen nemen weg van de spawnzone.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/SpawnZone-ExitPoints.jpg)

Om de geometrie van de spawnzonegebieden die je voor het spel creëert te visualiseren, verwijs je naar de volgende afbeelding die ze in geel markeert.

 ![Een bovenaanzicht van de uiteindelijke greybox-omgeving met de geometrie van de spawnzonewanden gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/SpawnZone-Intro.jpg)

Creëer je eigen Recreëer het voorbeeld

Om je eigen geometrie van de spawnzone te creëren:

1.

Gebruik blok  onderdelen om symmetrische secties aan de uiterste linker- en rechterzijde van de kaart voor elke team spawnzone  te segmenteren met twee uitgangspunten.

 ![Een schuine bovenaanzicht van de vloer, perimeter, en spawnzonewanden. De geometrie van de spawnzonewand is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralSpawnZone-1.jpg)

2.

Veranker deze onderdelen.

### [Geometrie van de gevechtsholtes](#geometrie-van-de-gevechtsholtes)[](#geometrie-van-de-gevechtsholtes)

De vierde stap in het creëren van de laser tag greybox-omgeving is het creëren van de geometrie voor gevechtsholtes in het interieur van het gebouw. Deze geometrie vormt de meerderheid van de speelbare gebieden in het spel omdat gevechtsholtes ontstaan uit de kruispunten van primaire lanes en kruislanen, die zich over het hele gebouw uitstrekken.

De instructies in deze sectie verwijzen naar deze geometrie als drie afzonderlijke gevechtsholtes volgens hun locatie op een bovenaanzicht van de kaart: de linker gevechtsholte, de middelste gevechtsholte, en de rechter gevechtsholte. De meeste gevechtsholtes bevatten maximaal drie in- of uitgangspunten om te voorkomen dat gebruikers overweldigd worden door keuzes terwijl ze de ruimte navigeren.

 ![Een bovenaanzicht van de uiteindelijke greybox-omgeving met de linker, middelste, en rechter gevechtsholtes gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/CombatPockets-Intro1.jpg)

Om de geometrie van de gevechtsholtes die je voor het spel creëert te visualiseren, verwijs je naar de volgende afbeelding die ze in geel markeert.

 ![Een bovenaanzicht van de uiteindelijke greybox-omgeving met de geometrie van de gevechtsholtes gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/CombatPockets-Intro2.jpg)

Creëer je eigen Recreëer het voorbeeld

Om je eigen geometrie van gevechtsholtes te creëren:

1.

Gebruik blok  onderdelen om een linker gevechtsholte  te creëren met twee uitgangspunten die spelers in staat stellen de middelste lane te traverseren, en één uitgangspunt dat opent naar de binnenste primaire lane. Deze geometrie moet ruimte aan beide zijden van de gevechtsholte hebben om kruislanen toe te staan, en blokkeren de toegang van spelers vanuit de buitenste primaire lane.

 ![Een schuine bovenaanzicht van de vloer, perimeter, spawnzonewanden, en linker gevechtsholte. De geometrie van de linker gevechtsholte is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/CombatPockets-1.jpg)

2.

Gebruik blok  onderdelen om een symmetrische kopie van deze gevechtsholte nabij de spawnzone van het andere team te creëren. Deze geometrie vertegenwoordigt je rechter gevechtsholte .

 ![Een schuine bovenaanzicht van de vloer, perimeter, spawnzonewanden, linker gevechtsholte, en rechter gevechtsholte. De geometrie van de rechter gevechtsholte is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralCombatPockets-2.jpg)

3.

Gebruik blok  onderdelen om een middelste gevechtsholte  te creëren met twee uitgangspunten die spelers in staat stellen de middelste lane te traverseren, één uitgangspunt dat opent naar de binnenste primaire lane, en open ruimte langs de rand die doorvloeit naar de buitenste primaire lane.

 ![Een schuine bovenaanzicht van de vloer, perimeter, spawnzonewanden, linker gevechtsholte, middelste gevechtsholte, en rechter gevechtsholte. De geometrie van de middelste gevechtsholte is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralCombatPockets-3.jpg)

4.

OPTIONEEL

 Gebruik blok  onderdelen om gangtoevoegingen  aan de middelste gevechtsholte te creëren om zichtlijnen over de binnenste primaire lane te doorbreken.

 ![Een schuine bovenaanzicht van de vloer, perimeter, spawnzonewanden, linker gevechtsholte, middelste gevechtsholte, rechter gevechtsholte, en gangtoevoegingen. De geometrie van de gangtoevoegingen is gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralCombatPockets-4.jpg)

5.

Veranker deze onderdelen.

### [Exterieur geometrie](#exterieur-geometrie)[](#exterieur-geometrie)

De laatste stap in het creëren van de laser tag greybox-omgeving is het creëren van de tijdelijke externe activa die interessante compositie voor de buitenruimte creëren, evenals minimale dekking voor gebruikers die de buitenste primaire lane traverseren. Dit gebied van het spel is belangrijk omdat het, hoewel het risico met zich meebrengt door de minimale dekking tegen vijandelijk vuur, ook gebruikers een snelle route naar de spawnzone van het vijandige team biedt.

Om de geometrie van de externe activa die je voor het spel creëert te visualiseren, verwijs je naar de volgende afbeelding die ze in geel markeert.

 ![Een bovenaanzicht van de uiteindelijke greybox-omgeving met de externe geometrie gemarkeerd in geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Exterior-Intro.jpg)

Maak je eigen Recreëer het voorbeeld

Om je eigen externe geometrie te maken:

1.

Gebruik blok  onderdelen om symmetrische obstakels  langs de primaire buitenbaan te creëren. Bijvoorbeeld, de voorbeeld greybox omgeving voegt onderdelen toe om zichtlijnen te blokkeren die later torens, pilaren en plantenbakken zullen worden.

 ![Een schuine bovenaanzicht van de vloer, perimeter, muren van de spawnzone, gevechtspockets en externe geometrie. De externe geometrie is gemarkeerd in het geel.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/GeneralExterior-1.jpg)

2.

Veranker deze onderdelen.

## [Pas tijdelijke materialen toe](#pas-tijdelijke-materialen-toe)[](#pas-tijdelijke-materialen-toe)

Nu je je tijdelijke geometrie hebt geplaatst, is het tijd om tijdelijke materialen toe te passen op de kaart in belangrijke gebieden om gebruikers te helpen zich te oriënteren waar ze zich in het spel bevinden. Het voorbeeld [Environment Art - Greyboxing](https://www.roblox.com/games/14447721254/Environment-Art-Greyboxing)  .rbxl  bestand gebruikt de volgende kleurenkaart, maar je kunt elke kleur gebruiken om hetzelfde doel te bereiken:

-

Diep Oranje voor de bovenste perimeter muren  – Informeert gebruikers waar ze zich bevinden ten opzichte van de achterkant van het gebouw.

-

Persimmon voor alle vloeren aan de linkerkant  – Informeert gebruikers waar ze zich bevinden ten opzichte van de rechterkant van het gebouw.

-

Lapis voor alle vloeren aan de rechterkant  – Informeert gebruikers waar ze zich bevinden ten opzichte van de linkerkant van het gebouw.

-

Heldere Groen voor de externe verhoging  – Informeert gebruikers waar ze zich bevinden ten opzichte van buiten het gebouw.

Het toepassen van materialen op deze specifieke belangrijke gebieden is belangrijk omdat, ongeacht waar een gebruiker zich in het spel bevindt, zolang ze ten minste één van deze kleuren kunnen zien, ze snel hun geschatte locatie binnen de algehele kaart kunnen afleiden, evenals waar ze zich bevinden ten opzichte van een spawnzone.

Bijvoorbeeld, als de volgende gebruiker in het "rode" team is, wanneer ze op de rode vloer lopen met de gele muur aan hun rechterkant, weten ze dat ze zich in de interne primaire baan bevinden en naar hun spawnzone bewegen. Omgekeerd, als ze op de lapis vloer lopen met de gele muur aan hun linkerkant, weten ze dat ze zich in de interne baan bevinden en naar de spawnzone van het vijandige team bewegen.

![Een Rthro avatar die op een rode vloer staat met een gele muur aan hun rechterkant. Deze kleurconfiguratie informeert de gebruiker dat ze zich in de interne primaire baan bevinden en naar de rode spawnzone bewegen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Placeholder-Left.jpg)

![Een Rthro avatar die op een blauwe vloer staat met een gele muur aan hun linkerkant. Deze kleurconfiguratie informeert de gebruiker dat ze zich in de interne primaire baan bevinden en naar de blauwe spawnzone bewegen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/Placeholder-Right.jpg)

Om tijdelijke materialen toe te passen:

1.

Selecteer de bovenste perimeter muren en de bovenste ganguitbreidingen, en stel hun [Part.Color](/docs/nl-nl/reference/engine/classes/Part#Color)  in op 255, 176, 0 .

2.

Selecteer de vloerdelen aan de linkerkant, en stel hun [Part.Color](/docs/nl-nl/reference/engine/classes/Part#Color)  in op 255, 89, 89 .

3.

Selecteer de vloerdelen aan de rechterkant, en stel hun [Part.Color](/docs/nl-nl/reference/engine/classes/Part#Color)  in op 16, 42, 220 .

4.

Selecteer het onderdeel voor de verhoging tussen de grond en de eerste verdieping, en stel hun [Part.Color](/docs/nl-nl/reference/engine/classes/Part#Color)  in op 75, 151, 75 .

 ![Een schuine bovenaanzicht van de uiteindelijke greybox omgeving met tijdelijke materialen om unieke secties van de kaart te markeren.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section1/PlaceholderMaterials.jpg)

## [Test je lay-out](#test-je-lay-out)[](#test-je-lay-out)

Het is belangrijk om de lay-out van je omgeving bijna elke stap van het ontwikkelingsproces  continu te testen, zodat je kunt zorgen dat het spel zowel leuk als functioneel is, en je kleine problemen kunt opmerken voordat ze grotere problemen worden naarmate je verder in het proces komt. Terwijl je test, stel jezelf de volgende vragen:

-

Zijn er voordelen of nadelen voor een van de teams?

-

Kunnen gebruikers zich succesvol oriënteren en hun locatie op elk moment op de kaart begrijpen?

-

Zijn er gebieden op de kaart die gebruikers overweldigen met te veel keuzes?

-

Wat vind ik leuk of waar word ik gefrustreerd over de lay-out of gameplay?

-

Zal dit gebruikers het gevoel geven dat ik wil dat ze hebben wanneer ze zich in dit gebied bevinden?

-

Is er een deel van de kaart dat ik kan omzeilen en toch mijn doelen kan bereiken?

Om te testen, selecteer een van de volgende simulatiemodi uit het dropdownmenu van de mezzanine en klik op de Speel  knop om te beginnen.

 ![Testoptie in het dropdownmenu van testmodi van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

| Modus | | Sneltoets | | Beschrijving |
| --- | --- |
| Test | | F5 | | Begint met het simuleren van de game, waarbij je avatar wordt geplaatst bij een [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  of coördinaten rond (0, 100, 0) . |
| Test Hier | |  | | Begint met het simuleren van de game, waarbij je avatar voor de huidige positie van de camera wordt geplaatst. |
| Uitvoeren | | F8 | | Begint met het simuleren van de game, maar plaatst je avatar niet. De simulatie begint bij de huidige camerastand en je kunt navigeren met de Studio camera besturingselementen. |

Tijdens het testen kun je dezelfde bedieningselementen gebruiken als in een standaard Roblox-spel. Zodra je tevreden bent met de algehele lay-out van je spel, kun je verder gaan met het maken van polijstassets die de greybox geometrie zullen vervangen in overeenstemming met je kunststijl.

[Volgende](/docs/nl-nl/tutorials/curriculums/environmental-art/develop-polished-assets)[Vorige](/docs/nl-nl/tutorials/curriculums/environmental-art)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
