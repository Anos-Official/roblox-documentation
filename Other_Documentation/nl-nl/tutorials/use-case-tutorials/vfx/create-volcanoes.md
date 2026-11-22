<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/vfx/create-volcanoes -->

Maak vulkaanuitbarstingen met VFX | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. VFX

# Maak vulkaanuitbarstingen met VFX

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een vulkaan  is een krater in de aardkorst die lava en rook uitspuwt als gevolg van interne druk van magma en opgeloste gassen. Spellen bevatten vaak vulkanen binnen uitdagende gameplay-gebieden, zoals locaties waar spelers de gevaar van lava en gesmolten gesteente moeten balanceren met de beloning van waardevolle hulpbronnen, baasgevechtsarena's of omgevingen die dynamisch veranderen naarmate de vulkaan cyclisch uitbarst.

Met het [Vulkaan Eiland - Start](https://create.roblox.com/dashboard/creations/experiences/5825677169/overview)  .rbxl  bestand als startpunt en [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  als referentie, laat deze tutorial zien hoe je de omgeving kunt transformeren in een vulkaanuitbarsting met aangepaste verlichting en VFX-objecten die het gedrag van echte fysieke verschijnselen vertegenwoordigen, inclusief richtlijnen over:

-

Het opdelen van referentiemateriaal in individuele componenten met verschillende visuele en gedragskenmerken.

-

Het configureren van oppervlaktegolven om heet vloeistof dat naar de oppervlakte stijgt en de oppervlakte van de caldera verstoort na te bootsen.

-

Het configureren van gloed om stukken gesmolten gesteente na te bootsen die snel afkoelen terwijl ze de atmosfeer in stijgen.

-

Het configureren van lava die spettert en stroomt vanuit de caldera om verschillende soorten lava-viscositeitstoestanden na te bootsen.

-

Het configureren van een rookpluim om harde onzuiverheden na te bootsen die de lucht in stijgen en de aandacht van spelers trekken.

Je kunt je eigen texturen maken in externe textuurcreatietools en meedoen met je eigen ontwerp. Voor informatie over het importeren van texturen voor gebruik in Studio, zie [Asset Manager](/docs/nl-nl/projects/assets/manager) .

![Het start vulkaan terrein dat je kunt gebruiken om deze tutorial te voltooien.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Volcano-Start.jpg) Vulkaan Eiland - Start

![De complete vulkaan met VFX-objecten die je aan het einde van deze tutorial zult creëren.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Volcano-Complete.jpg) Vulkaan Eiland - Compleet

## [Breek referentie af](#breek-referentie-af)[](#breek-referentie-af)

Om geloofwaardige vulkanen te creëren, is het belangrijk om echte vulkaanuitbarstingen te refereren in het ontwerpproces, omdat dit je in staat stelt om het onderwerp op te splitsen in individuele componenten met verschillende visuele en gedragskenmerken. Bijvoorbeeld, het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  spel verwijst naar de vulkaanuitbarsting in IJsland om alle textuur- en VFX-ontwerpbeslissingen met betrekking tot de caldera en het omliggende terrein te informeren.

 ![Een verre kijk op een IJslandse vulkaanuitbarsting.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Volcano-NoComponents.jpg)

Het is nuttig om een uitbarstende vulkaan op te splitsen in individuele componenten, zodat je kunt plannen hoe je verschillende VFX-objecten kunt gebruiken om hun tegenhangers in de echte wereld na te bootsen. Om dit te demonstreren, splitst deze tutorial de voorbeeldvulkaan op in vijf unieke componenten:

-

Oppervlaktegolven  – De kleine golven van lava op het oppervlak van de caldera.

-

Gloed  – De kleine, lichte stukken gesmolten gesteente die de lucht in stijgen vanuit de caldera.

-

Lava-spetters  – Het dunne gesmolten gesteente dat uit de caldera barst door interne druk binnen de vulkaan.

-

Lava-stroom  – Het viskeuze gesmolten gesteente dat wegvloeit van de caldera.

-

Rookpluim  – Het warme, golvende gas dat de lucht in stijgt vanuit de caldera.

![De vulkaanuitbarsting referentie met alle vijf componenten gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Volcano-Components.jpg)

![De voorbeeld vulkaanuitbarsting met dezelfde vijf componenten gemarkeerd om de referentie afbeelding met het eindresultaat te vergelijken.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Sample-Components.jpg)

De volgende secties bieden een diepgaande analyse van de verschillende ontwerpbeslissingen en technieken die je kunt gebruiken om elk van deze componenten opnieuw te creëren. Terwijl je deze beslissingen bekijkt en experimenteert met verschillende verlichting, [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter) , en [Beam](/docs/nl-nl/reference/engine/classes/Beam)  eigenschappen, leer je hoe je verlichting en VFX kunt gebruiken om te voldoen aan de unieke omgevingsvereisten voor je eigen spellen.

## [Configureer verlichting](#configureer-verlichting)[](#configureer-verlichting)

Om een omgevingselement een punt van interesse binnen je spel te maken, is het belangrijk om het contrast ten opzichte van de algehele omgeving te verhogen, zodat het opvalt als iets dat spelers moeten verkennen. Bijvoorbeeld, om spelers naar de caldera te trekken, kun je je lichtbronnen zo configureren dat de lava van de vulkaan lijkt te gloeien als de enige lichtbron binnen een anders donkere omgeving.

Studio biedt twee hoog-niveau soorten lichtbronnen die je voor deze techniek kunt gebruiken:

-

Globale verlichting  - Produceert verlichting voor de gehele buitenomgeving.

-

Lokale verlichting  - Produceert verlichting rondom waar je ze plaatst binnen je spel.

Deze sectie van de tutorial leert je hoe je beide soorten lichtbronnen kunt gebruiken om je vulkaanuitbarsting het meest significante punt van interesse binnen je scène te maken, evenals een dramatisch effect voor je omgevingsverhaal te creëren. Om dit te illustreren, bekijk hoe dezelfde eindvulkaan zonder aangepaste verlichting aanvoelt als een onopvallend gevaar in een anders vrolijke omgeving, terwijl de vulkaan met aangepaste verlichting aanvoelt als een gevaarlijke aanwezigheid in een donkere, melancholische omgeving.

![De complete versie van de voorbeeld vulkaanuitbarsting met standaard lichtbronnen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Default-Lighting.jpg) Met standaard lichtbronnen

![De complete versie van de voorbeeld vulkaanuitbarsting met aangepaste lichtbronnen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Custom-Lighting.jpg) Met aangepaste lichtbronnen

### [Lokale verlichting](#lokale-verlichting)[](#lokale-verlichting)

Lokale verlichting is de luminescentie van lokale [lichtbronnen](/docs/nl-nl/effects/light-sources)  in je spel, zoals [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight) , en [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  objecten. Lokale verlichting is belangrijk om aan je vulkaan toe te voegen, omdat terwijl je helderheid kunt toepassen op je [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  en [Beam](/docs/nl-nl/reference/engine/classes/Beam)  texturen, ze de kloof niet alleen met genoeg licht kunnen vullen om realistisch te simuleren hoe de caldera en zijn stromende lava de omgeving in de echte wereld zouden verlichten.

![De complete versie van de voorbeeld vulkaanuitbarsting zonder lokale verlichting.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Without-LocalLighting.jpg) Zonder lokale verlichting

![De complete versie van de voorbeeld vulkaanuitbarsting met lokale verlichting.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/With-LocalLighting.jpg) Met lokale verlichting

Het is nuttig om je lokale verlichting te configureren voordat je je globale verlichting configureert voor deze tutorial, omdat zonder de lokale lichtbronnen je de 3D-ruimte niet kunt zien om je VFX-objecten te configureren. Echter, gebruikelijke workflows vereisen dat je gelijktijdig op zowel lokale als globale verlichting iteraties uitvoert om de effecten van je wijzigingen op VFX-objecten te zien, dus het is belangrijk om flexibel te zijn voor de ontwerpeisen van je eigen spellen.

Om de lokale verlichting voor de vulkaan in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle lokale lichtbronobjecten te bevatten, en hernoem de map naar LokaleVerlichting .

2.

Voeg drie blok  onderdelen toe aan de LokaleVerlichting  map, en hernoem ze respectievelijk naar LichtCaldera , LichtMagma , en LichtAfvoer .

3.

Verplaats de onderdelen naar een positie waar ze de gehele vulkaan kunnen verlichten.

1.

Verplaats LichtCaldera  naar het midden van de ruimte tussen de caldera en de klif.

2.

Verplaats LichtMagma  naar het midden van de kloof tussen de caldera en de magma-afvoer.

3.

Verplaats LichtAfvoer  iets boven waar de afvoer in twee stromen splitst.

 ![Een vooraanzicht van de vulkaan met drie blokonderdelen gepositioneerd door de vallei van de vulkaan.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LL-3.jpg)

4.

Voeg een Pointlight  toe aan elk onderdeel.

 ![Een vooraanzicht van de vulkaan met drie blokonderdelen met visuele hulpmiddelen voor puntlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LL-4.jpg)

5.

Selecteer de PointLight  kind van LichtCaldera , en in het Properties  venster,

1.

Stel Brightness  in op 15  om de lichtbron veel helderder te maken.

2.

Stel Color  in op 255, 85, 0  om het licht een donkere oranje tint te geven.

3.

Stel Range  in op 60  om het gehele caldera gebied te verlichten.

 ![Een vooraanzicht van de vulkaan met drie blokonderdelen. Het blokonderdeel dichtst bij de caldera straalt oranje licht uit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LL-5.jpg)

6.

Selecteer de PointLight  kinderen van LichtMagma  en LichtAfvoer , en in het Properties  venster,

1.

Stel Brightness  in op 2  om de lichtbron iets helderder te maken.

2.

Stel Color  in op 255, 81, 0  om het licht een oranje tint te geven.

3.

Stel Range  in op 50  om de kloof en afvoergebieden te verlichten.

 ![Een vooraanzicht van de vulkaan met drie blokonderdelen die allemaal oranje licht uitstralen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LL-6.jpg)

7.

In het Explorer  venster, selecteer alle blokonderdelen in de LokaleVerlichting  map, en in het Properties  venster, stel Transparency  in op 1  om de blokken onzichtbaar te maken.

 ![Een vooraanzicht van de vulkaan die oranje verlichting heeft door de vallei van de vulkaan.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LL-7.jpg)

### [Globale verlichting](#globale-verlichting)[](#globale-verlichting)

Globale verlichting is de luminescentie van de zon of de maan in een spel. Door een paar belangrijke standaard eigenschappen in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service en zijn kind post-processing effecten objecten aan te passen, kun je dramatisch veranderen hoe het globale licht voor spelers verschijnt, evenals hoe het interactie heeft met elk ander object dat je in het spel plaatst, inclusief [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  en [Beam](/docs/nl-nl/reference/engine/classes/Beam)  texturen.

Bijvoorbeeld, om ervoor te zorgen dat de [Beam](/docs/nl-nl/reference/engine/classes/Beam)  texturen die later in de tutorial een stromende lava-effect produceren kunnen gloeien, moet je de [BloomEffect](/docs/nl-nl/reference/engine/classes/BloomEffect)  eigenschappen configureren om de verlichting te overdrijven zoals een camera die naar een fel licht kijkt. Evenzo, om realistischere kleuren 's nachts te simuleren, moet je ook de eigenschappen van het effect aanpassen om de algehele omgeving te desatureren.

![De complete versie van de voorbeeld vulkaanuitbarsting zonder bloom.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Without-Bloom.jpg) Zonder bloom

![De complete versie van de voorbeeld vulkaanuitbarsting met bloom.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/With-Bloom.jpg) Met bloom

Om de globale verlichting in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

In het Explorer  venster, selecteer de Lighting  service, en in het Properties  venster,

1.

Stel Ambient  in op 133, 152, 176  om een lichte grijze tint over de gehele buitenomgeving in te stellen.

2.

Stel Brightness  in op 2  om de globale lichtbron iets dimmer te maken.

3.

Stel ColorShift_Top  in op 207, 178, 72  om een gele tint aan het licht te geven dat weerkaatst van oppervlakken die naar de globale lichtbron zijn gericht.

4.

Stel LightingStyle  in op Realistic  om gebruik te maken van Roblox's meest geavanceerde verlichtingstechnologie.

5.

Stel ClockTime  in op 4.3  om de tijd van de dag in te stellen op ongeveer een kwart na 4 uur 's ochtends.

6.

Stel GeographicLatitude  in op 199  om de positie van de maan te wijzigen.

7.

Stel ExposureCompensation  in op -1  om de omgeving bloot te stellen aan de helft van de belichting van de maan.

 ![Een vooraanzicht van de vulkaan met verduisterde buitenverlichting.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/GL-1.jpg)

2.

In het Explorer  venster, selecteer Bloom  kind van de Lighting  service, en in het Properties  venster,

1.

Stel Intensity  in op 0.75  om alle kleuren binnen de omgeving iets te dimmen.

2.

Stel Size  in op 80  om een bredere bloom-effect te creëren.

3.

Stel Threshold  in op 0.85  om meer kleuren in de omgeving te laten gloeien.

 ![Een vooraanzicht van de vulkaan met verduisterde buitenverlichting en lokale verlichting die oranje gloeit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/GL-2.jpg)

3.

In het Explorer  venster, voeg een ColorCorrection  object toe aan de Lighting  service, en in het Properties  venster,

1.

Stel Brightness  in op 0.017  om de kleur van je pixels iets te verschuiven.

2.

Stel Contrast  in op 0.25  om een scherpere contrast tussen lichte en donkere kleuren in de omgeving te maken.

3.

Stel Saturation  in op -0.15  om kleuren in de omgeving te desatureren.

4.

Stel TintColor  in op 255, 214, 143  om pixels een lichte gele tint te geven.

 ![Een vooraanzicht van de vulkaan met pitch black buitenverlichting en lokale verlichting die oranje gloeit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/GL-3.jpg)

4.

OPTIONAL

 Bied indirect licht met wolken in de lucht.

1.

In het Explorer  venster, voeg een Clouds  object toe aan de Terrain  service.

2.

Selecteer het Clouds  object, en in het Properties  venster,

1.

Stel Cover  in op 1  om volledige wolkenbedekking aan de lucht te bieden.

2.

Stel Density  in op 0.08  om de wolkenbedekking minder dicht te maken.

3.

Stel Color  in op 136, 143, 152  om een lichte grijze tint aan de wolkenbedekking te geven.

 ![Een vooraanzicht van de vulkaan met pitch black buitenverlichting, grijze wolken, en lokale verlichting die oranje gloeit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/GL-4.jpg)

## [Configureer vulkaan](#configureer-vulkaan)[](#configureer-vulkaan)

Nu je lokale en globale verlichting configuratie compleet is, is het tijd om alle VFX-objecten met betrekking tot de daadwerkelijke vulkaan en het omliggende terrein te configureren. Terwijl je deze instructies volgt die exact de eindomgeving binnen het voorbeeld [Vulkaan Eiland](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  .rbxl  bestand opnieuw creëren, observeer hoe elke stap samenwerkt om karakter, beweging en verlichting aan de omgeving toe te voegen.

### [Oppervlaktegolven](#oppervlaktegolven)[](#oppervlaktegolven)

Oppervlaktegolven  zijn de kleine lavagolven die over het oppervlak van de caldera stromen als gevolg van interne magma en onder druk staande gassen die omhoog bewegen vanuit de aardkorst. Dit visuele fenomeen geeft het fysieke proces van convectie weer, of de beweging binnen een vloeistof wanneer heet vloeistof naar de oppervlakte stijgt, en het voegt realisme toe aan je scène.

Oppervlaktegolven bieden waardevolle inzichten voor spelers in de staat van de vulkaanuitbarsting. Bijvoorbeeld, als magma en gas met genoeg kracht omhoog bewegen om de staat van de lava bovenop de caldera te verstoren en deze te laten draaien, kunnen spelers afleiden dat de vulkaan actief uitbarst met kokend magma, dus ze moeten voorzichtig zijn rond dit gameplaygebied.

![Een bovenaanzicht van de caldera zonder oppervlaktegolven.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Without-SurfaceRipples.jpg) Zonder oppervlaktegolven

Met oppervlaktegolven

Om dit proces te demonstreren, gebruikt het voorbeeld een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  object net onder de basis van de caldera om platte, heldere deeltjes uit te stoten die langzaam uitbreiden en samentrekken op een donkere achtergrond. Dit stelt de deeltjes in staat om het gedrag van lava soepel en continu te emuleren op een manier die lijkt op de realistische manier waarop elementen in de natuur bewegen.

![De 2D textuur die oppervlaktegolven vertegenwoordigt die voortkomen uit draaiende lava.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Foam-Texture.png) Schuim Golven Textuur = rbxassetid://16811365086

Om de oppervlaktegolven bovenop de caldera in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle caldera-objecten te bevatten, en hernoem de map naar Caldera .

2.

Maak een achtergrond om een hoog contrast achtergrond voor de oppervlaktegolven te bieden.

1.

Voeg een blok  onderdeel toe aan de Caldera  map, en hernoem het naar Achtergrond .

2.

Positioneer en schaal Achtergrond  iets verder dan het volledige oppervlak van de caldera. Het onderdeel lijkt te gloeien vanwege de nabijheid tot de lokale lichtbron van de caldera.

 ![Een bovenaanzicht van de caldera met een gemarkeerd blokonderdeel dat geel gloeit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Ripples-2B.jpg)

3.

Selecteer Achtergrond , en in het Properties  venster,

1.

Stel Color  in op 0, 0, 0  om het blok zwart te maken.

2.

Stel Material  in op Foil  om textuur aan de achtergrond te geven.

 ![Een bovenaanzicht van de caldera met een blokonderdeel dat zwart is met enige ruwe textuur.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Ripples-2C.jpg)

4.

Maak het golfeffect.

1.

Dupliceer Achtergrond , hernoem het naar MagmaGolven , en schaal het iets naar beneden naar het oppervlak van de caldera.

2.

Selecteer MagmaGolven , en in het Properties  venster, stel Transparency  in op 1  om het blok onzichtbaar te maken.

3.

Voeg een ParticleEmitter  toe aan MagmaGolven , en hernoem de emitter naar Golven .

4.

Selecteer Golven , en in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16829556885  om deeltjes weer te geven die eruit zien als schuimgolven.

2.

Stel Orientation  in op VelocityPerpendicular  om deeltjes loodrecht op de richting van hun beweging uit te stoten.

3.

Stel Color  in op een kleursequentie waarin de deeltjes bruin zijn, helder rood worden, en dan kastanjebruin worden.

1.

Klik op de Color  eigenschap, en klik dan op de ⋯  knop. Een kleursequentie pop-up verschijnt.

 ![Een close-up van het Properties venster van Studio met de ellipsknop van de Color eigenschap gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1G1.png)

Elke driehoek op de onderste as van de kleursequentie is een keypoint  die de kleurwaarde van de eigenschap op dat punt van de levensduur van het deeltje bepaalt.

1.

Stel de volgende tijd- en waarde-eigenschappen in door de kleursequentie:

-

Time  = 0 , RGB Value  = 130, 53, 2

-

Time  = 0.5 , RGB Value  = 224, 37, 0

-

Time  = 1 , RGB Value  = 147, 5, 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Ripples-3DColor.jpg)

4.

Stel Size  in op een nummersequentie waarin de deeltjes in grootte toenemen naar het midden van hun levensduur voordat ze terugkeren naar hun oorspronkelijke grootte met een kleine variatie.

1.

Klik op de Size  eigenschap, en klik dan op de ⋯  knop. Een nummersequentie pop-up verschijnt. Standaard is de grafiek een rechte lijn en blijft de afbeelding dezelfde grootte van links naar rechts.

 ![Een close-up van de Size nummersequentie grafiek.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1H1.png)

Elke vierkant aan het begin en einde van de nummersequentie is een keypoint  die de groottewaarde van de eigenschap op dat punt van de textuur van links naar rechts bepaalt.

1.

Stel de volgende tijd- en waarde-eigenschappen in door de nummersequentie:

-

Time  = 0 , Value  = 4.81 , Envelope  = 0.438

-

Time  = 0.341 , Value  = 8.75 , Envelope  = 0.48

-

Time  = 0.497 , Value  = 9.38 , Envelope  = 0.5

-

Time  = 0.644 , Value  = 8.75 , Envelope  = 0.48

-

Time  = 1 , Value  = 4.81 , Envelope  = 0.438

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Ripples-3DSize.jpg)

5.

Stel Transparency  in op een nummersequentie waarin de deeltjes beginnen als transparant, meer ondoorzichtig worden naar het midden van hun levensduur, en dan weer transparant worden aan het einde van hun levensduur.

1.

Klik op de Transparency  eigenschap, en klik dan op de ⋯  knop.

2.

Stel de volgende tijd- en waarde-eigenschappen in door de nummersequentie:

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.3 , Value  = 0.387 , Envelope  = 0.0375

-

Time  = 0.5 , Value  = 0.269 , Envelope  = 0.0812

-

Time  = 0.7 , Value  = 0.381 , Envelope  = 0.05

-

Time  = 0 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Ripples-3DTransparency.jpg)

6.

Stel ZOffset  in op -2  om de textuur iets van de caldera af te plaatsen.

7.

Stel Lifetime  in op 5, 8  om de levensduur van elk deeltje willekeurig in te stellen tussen 5 en 8 seconden.

8.

Stel Rate  in op 12  om 12 deeltjes per seconde uit te stoten.

9.

Stel Rotation  in op -360, 360  om elk deeltje willekeurig in een cirkel te oriënteren.

10.

Stel Speed  in op 0.01  om elk deeltje een tiende van een stud per seconde uit te stoten.

11.

Stel LightEmission  in op 1  om de deeltjes aanzienlijk te verlichten.

12.

Stel LightInfluence  in op 0  om te voorkomen dat het omgevingslicht de kleur van de deeltjes beïnvloedt.

13.

Stel Brightness  in op 15  om het licht dat van de emitter wordt uitgezonden te schalen.

### [Gloed](#gloed)[](#gloed)

Gloed  zijn de kleine, lichte stukken gesmolten gesteente die uit de caldera barsten, snel warmte uitstralend terwijl ze de lucht in stijgen. Net als oppervlaktegolven, onthullen gloed dat interne druk onder de aardkorst omhoog drukt, waardoor hete elementen de oppervlaktespanning van de lava breken om druk vrij te geven.

Het voorbeeld emuleert dit proces door een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  object te gebruiken om deeltjes uit te stoten met bewegingsonscherpte die in de textuur is gebakken. Terwijl de deeltjes stijgen en het einde van hun levensduur bereiken, vervormt de emitter de deeltjes in een 1:1 verhouding om de deeltjes opnieuw in cirkels te vormen. Deze techniek laat de deeltjes lijken alsof ze snel bewegen terwijl ze de caldera verlaten, en dan vertragen terwijl ze in de lucht verdwijnen.

![De 2D textuur die gloed vertegenwoordigt die uit de caldera barst.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Embers-Texture.jpg) Gloed Textuur = rbxassetid://17581858560

Bovendien, terwijl de deeltjes stijgen, veranderen ze van kleur, opaciteit en grootte om hun veranderende temperatuur weer te geven. Bijvoorbeeld, ze beginnen hun levensduur als grote, bruine deeltjes, maar transformeren snel in kleine oranje, en dan kastanjebruine deeltjes. Deze strategie heeft ook het voordeel van subtiel het licht door de kloof te reflecteren, waardoor de onderdompeling van een speler in de omgeving toeneemt.

Om de gloeiende gloed van het oppervlak van de caldera in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

Voeg een cilinder  onderdeel toe aan de Caldera  map, en hernoem het naar GloeiendeGloed .

2.

Positioneer GloeiendeGloed  zodat het bovenop de oppervlaktegolven ligt, en schaal het totdat het de binnenkant van de caldera vult. Het onderdeel lijkt te gloeien vanwege de nabijheid tot de lokale lichtbron van de caldera.

 ![Een close vooraanzicht van de caldera met een cilinder onderdeel dat geel gloeit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Embers-2.jpg)

3.

Selecteer GloeiendeGloed , en in het Properties  venster, stel Transparency  in op 1  om de cilinder onzichtbaar te maken.

4.

Voeg een ParticleEmitter  toe aan GloeiendeGloed , en hernoem de emitter naar Gloed .

5.

Selecteer Gloed , en in het Properties  venster,

1.

Stel Texture  in op rbxassetid://17581858560  om deeltjes weer te geven die eruit zien als een langwerpige ovaal horizontaal en verticaal.

2.

Stel Orientation  in op VelocityParallel  om deeltjes parallel aan hun bewegingsrichting uit te stoten.

3.

Stel Color  in op een kleursequentie waarin de deeltjes bruin zijn, oranje worden, en dan kastanjebruin worden.

-

Time  = 0 , RGB Value  = 130, 53, 2

-

Time  = 0.5 , RGB Value  = 224, 82, 0

-

Time  = 1 , RGB Value  = 147, 5, 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Embers-5Color.jpg)

1.

Stel Size  in op een nummersequentie waarin de deeltjes langzaam in grootte afnemen over hun levensduur.

-

Time  = 0 , Value  = 0.313 , Envelope  = 0.1

-

Time  = 1 , Value  = 0 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Embers-5Size.jpg)

1.

Stel Squash  in op een nummersequentie waarin de deeltjes iets uitrekken halverwege hun levensduur.

-

Time  = 0 , Value  = -3 , Envelope  = 0

-

Time  = 0.323 , Value  = -0.188 , Envelope  = 0

-

Time  = 1 , Value  = -0.5 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Embers-5Squash.jpg)

1.

Stel Transparency  in op een nummersequentie waarin de deeltjes willekeurig hun opaciteit veranderen om de gloed na te bootsen terwijl ze stijgen. De werkelijke waarden zijn niet belangrijk, alleen dat ze veel veranderen tijdens hun levensduur.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Embers-5Transparency.jpg)

1.

Stel ZOffset  in op 1  om de textuur iets van de caldera af te plaatsen.

2.

Stel Lifetime  in op 1, 5  om de levensduur van elk deeltje willekeurig in te stellen tussen 1 en 5 seconden.

3.

Stel Speed  in op 5, 8  om elk deeltje willekeurig tussen 5 en 8 studs per seconde uit te stoten.

4.

Stel SpreadAngle  in op 180, 180  om deeltjes in een hoek langs de X- en Z-as uit te stoten.

5.

Stel Acceleration  in op 0, 10, 0  om een opwaartse kracht te simuleren en de deeltjes naar de lucht te trekken.

6.

Stel Drag  in op 0.8  om de deeltjes hun snelheid te laten verliezen met exponentiële afname.

7.

Stel LightEmission  in op 1  om de deeltjes aanzienlijk te verlichten.

8.

Stel LightInfluence  in op 0  om te voorkomen dat het omgevingslicht de kleur van de deeltjes beïnvloedt.

9.

Stel Brightness  in op 20  om het licht dat van de emitter wordt uitgezonden te schalen.

### [Lava-spetters](#lava-spetters)[](#lava-spetters)

Lava-spetters  zijn uitbarstingen van dun gesmolten gesteente die omhoog uit de vulkaan komen als gevolg van interne magma en onder druk staande gassen die genoeg kracht uitoefenen om de oppervlaktespanning van de lava bovenop de caldera te breken. Deze kerncomponent van een vulkaan is een van de meest voorkomende tekenen om te bepalen dat een vulkaan niet langer slapend is en actief uitbarst.

Het voorbeeld vertegenwoordigt dit proces met twee [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  objecten die gebruik maken van [flipbooks](/docs/nl-nl/effects/particle-emitters#flipbooks)  om de textuur van elk deeltje over hun levensduur te animeren. De eerste deeltjesemitter stoot deeltjes uit die eruit zien als dichte, hoog-viskeuze spetters die zwaar en dik zijn, waardoor ze langzaam omhoog stijgen en weer terugvallen in de vulkaan. Omgekeerd, de tweede deeltjesemitter stoot deeltjes uit die eruit zien als webachtige, laag-viskeuze spetters die licht en dun zijn, waardoor ze snel omhoog stijgen en weer terugvallen.

![De 2D textuur die een dichte spettertextuur vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/DenseSplash-Texture.jpg) Dense Splash Textuur = rbxassetid:/17363669906

![De 2D textuur die een webachtige spettertextuur vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/WebbySplash-Texture.jpg) Webby Splash Textuur = rbxassetid://17363668312

Elke deeltjesemitter animeert hun textuur over 64 frames om soepel, levensecht fysiek gedrag na te bootsen. Terwijl je slechts één deeltjesemitter zou kunnen gebruiken, zou de herhaling van de animatie duidelijk worden en de onderdompeling voor je spelers breken omdat ze elke keer dezelfde animatie zouden zien. Echter, wanneer twee deeltjes flipbooks met iets verschillende aangepaste eigenschappen animeren, is het veel moeilijker om de herhaling op te merken.

Het voorbeeld biedt ook een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  object dat deeltjes uitstoott die eruit zien als geaëreerde spetters om zelfs nog lichtere webachtige spetters weer te geven. Deze techniek vult de ruimte met dynamische beweging en verbergt verder de herhaling van de flipbook-animaties. Als extra bonus, als je spel ook de waterval van [Watervallen Creëren](/docs/nl-nl/tutorials/use-case-tutorials/vfx/create-waterfalls)  bevat, kun je dezelfde textuur twee keer hergebruiken voor verschillende gameplay-gebieden, wat je geheugen bespaart en de prestaties op low-end apparaten verbetert.

![De 2D textuur die geaëreerde spetters vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-Droplets.png) Webby Textuur = rbxassetid://17082061238

Om de spetterende lava van het oppervlak van de caldera in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

Voeg een cilinder  onderdeel toe aan de Caldera  map, en hernoem het naar SpetterendeLava .

2.

Positioneer SpetterendeLava  zodat het bovenop de oppervlaktegolven ligt, en schaal het totdat het het midden van de caldera bedekt waar je wilt dat de lava spat. Het onderdeel lijkt te gloeien vanwege de nabijheid tot de lokale lichtbron van de caldera.

 ![Een close vooraanzicht van de caldera met een cilinder onderdeel dat geel gloeit.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-2.jpg)

3.

Selecteer SpetterendeLava , en in het Properties  venster, stel Transparency  in op 1  om de cilinder onzichtbaar te maken.

4.

Voeg een ParticleEmitter  toe aan SpetterendeLava , en hernoem de emitter naar WebbySpetters .

5.

Selecteer WebbySpetters , en in het Properties  venster,

1.

Stel Texture  in op rbxassetid://17363668312  om deeltjes weer te geven die eruit zien als webachtige spetters.

2.

Stel Orientation  in op FacingCameraWorldUp  om deeltjes uit te stoten die naar de camera gericht zijn, maar alleen roteren op de verticale opwaartse wereld Y-as.

3.

Stel Color  in op 255, 152, 79  om de deeltjes een lichte oranje tint te geven.

4.

Stel Size  in op een nummersequentie waarin de deeltjes in grootte toenemen over hun levensduur met een venster van variatie.

-

Time  = 0 , Value  = 4.31 , Envelope  = 0.762

-

Time  = 1 , Value  = 6.2 , Envelope  = 0.875

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-5Size.jpg)

1.

Stel Squash  in op een nummersequentie waarin de deeltjes iets uitrekken gedurende hun levensduur met een venster van variatie.

-

Time  = 0 , Value  = -0.075 , Envelope  = 0.263

-

Time  = 1 , Value  = -0.413 , Envelope  = 0.412

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-5Squash.jpg)

1.

Stel ZOffset  in op 1  om de textuur iets van de caldera af te plaatsen.

2.

Stel Lifetime  in op 1.5, 2  om de levensduur van elk deeltje willekeurig in te stellen tussen 1.5 en 2 seconden.

3.

Stel Rate  in op 0.37  om ongeveer elke 3 seconden een deeltje uit te stoten.

4.

Stel RotSpeed  in op -20, 20  om elk deeltje willekeurig tussen -20 en 20 graden per seconde uit te stoten.

5.

Stel Speed  in op 2  om elk deeltje 2 studs per seconde uit te stoten.

6.

Stel SpreadAngle  in op 5, 5  om deeltjes in een kleine hoek langs de X- en Z-as uit te stoten.

7.

Stel FlipbookLayout  in op Grid8x8  om de textuur over een duur van 64 frames te animeren.

8.

Stel FlipbookMode  in op Oneshot  om ervoor te zorgen dat de animatie slechts één keer tijdens zijn levensduur wordt afgespeeld.

9.

Stel Drag  in op 0.5  om de deeltjes hun snelheid te laten verliezen met exponentiële afname.

10.

Stel LightEmission  in op 0.1  om de deeltjes iets te verlichten.

11.

Stel LightInfluence  in op 0.25  om te verminderen hoezeer het omgevingslicht de kleur van de deeltjes beïnvloedt.

6.

Dupliceer DichteSpetters , en in het Properties  venster, wijzig de volgende eigenschappen om variatie aan de extra lava-spetters te bieden.

1.

Stel Name  in op DichteSpetters .

2.

Stel Texture  in op rbxassetid://17363669906  om deeltjes weer te geven die eruit zien als dichte spetters.

3.

Stel Size  in op een nummersequentie waarin de deeltjes in grootte toenemen over hun levensduur met een venster van variatie.

-

Time  = 0 , Value  = 5.75 , Envelope  = 0.762

-

Time  = 1 , Value  = 7.37 , Envelope  = 0.875

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-6Size.jpg)

1.

Stel Squash  in op een nummersequentie waarin de deeltjes iets uitrekken gedurende hun levensduur met een venster van variatie.

-

Time  = 0 , Value  = 0 , Envelope  = 0.225

-

Time  = 1 , Value  = -0.262 , Envelope  = 0.15

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-6Squash.jpg)

1.

Stel Rate  in op 0.289  om bijna elke vierde van een seconde een deeltje uit te stoten.

7.

Vul de caldera met extra spetters.

1.

Voeg een ParticleEmitter  toe aan SpetterendeLava , en hernoem de emitter naar VulFill .

2.

Selecteer VulFill , en in het Properties  venster,

1.

Stel Texture  in op rbxassetid://17082061238  om deeltjes weer te geven die eruit zien als lichtere webachtige spetters.

2.

Stel Orientation  in op FacingCameraWorldUp  om deeltjes uit te stoten die naar de camera gericht zijn, maar alleen roteren op de verticale opwaartse wereld Y-as.

3.

Stel Color  in op 255, 152, 33  om de deeltjes een oranje tint te geven.

4.

Stel Size  in op een nummersequentie waarin de deeltjes in grootte toenemen over hun levensduur met een venster van variatie.

-

Time  = 0 , Value  = 1.25 , Envelope  = 0.388

-

Time  = 1 , Value  = 6.38 , Envelope  = 0.563

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-7Size.jpg)

1.

Stel Transparency  in op een nummersequentie waarin de deeltjes beginnen als transparant, ondoorzichtig worden, en dan weer transparant worden aan het einde van hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.19 , Value  = 0 , Envelope  = 0

-

Time  = 0.795 , Value  = 0 , Envelope  = 0

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Splashes-7Transparency.jpg)

1.

Stel ZOffset  in op 1  om de textuur iets van de caldera af te plaatsen.

2.

Stel Lifetime  in op 1.5  om de levensduur van elk deeltje in te stellen op 1.5 seconden.

3.

Stel Rate  in op 8  om elke 8 seconden een deeltje uit te stoten.

4.

Stel Rotation  in op 0, 360  om elk deeltje willekeurig in een halve cirkel te oriënteren.

5.

Stel RotSpeed  in op -50, 50  om elk deeltje willekeurig tussen -50 en 50 graden per seconde uit te stoten.

6.

Stel Speed  in op 12, 20  om elk deeltje willekeurig tussen 12 en 20 studs per seconde uit te stoten.

7.

Stel SpreadAngle  in op 45, 45  om deeltjes in een hoek langs de X- en Z-as uit te stoten.

8.

Stel Acceleration  in op 0, -25, 0  om de zwaartekracht te simuleren en de deeltjes terug naar beneden te trekken.

9.

Stel Drag  in op 1  om de deeltjes hun snelheid te laten verliezen met exponentiële afname.

10.

Stel LightEmission  in op 1  om de deeltjes aanzienlijk te verlichten.

11.

Stel LightInfluence  in op 0  om te voorkomen dat het omgevingslicht de kleur van de deeltjes beïnvloedt.

12.

Stel Brightness  in op 8  om het licht dat van de emitter wordt uitgezonden te schalen.

Functies met aangepaste texturen zoals flipbooks kosten geheugen om te renderen. Als je veel flipbooks gebruikt met andere functies die veel geheugen gebruiken, deactiveert de client automatisch flipbooks wanneer ze weinig geheugen hebben, wat waarschijnlijk is voor oudere mobiele telefoons. Om het geheugenverbruik van flipbooks te verminderen, gebruik minder unieke geanimeerde deeltjeseffecten of kies een textuur van kleinere resolutie.

### [Lava-stroom](#lava-stroom)[](#lava-stroom)

Een lava-stroom  is een massa lava die uitbarst en wegvloeit van de caldera en over het aardoppervlak tijdens een vulkaanuitbarsting. Terwijl de lava afkoelt door blootstelling aan lucht, verhardt het en transformeert het in vast gesteente, waardoor nieuwe landmassa ontstaat.

Om dit proces te simuleren, stapelt het voorbeeld meerdere [Beam](/docs/nl-nl/reference/engine/classes/Beam)  objecten bovenop elkaar met naadloze texturen en eigenschapsconfiguraties die de gedragskenmerken van lava die afkoelt terwijl het verder van de caldera reist emuleren:

-

De onderste laag  rendert een vlakke kleur die verandert van een warme naar een koele kleur om te communiceren dat de lava begint te dalen in temperatuur, zoals felrood naar donker kastanjebruin.

-

De middenlaag  rendert een zwarte textuur die eruit ziet als donkere korst met gaten die de gloeiende lava eronder onthullen.

-

De bovenste laag  rendert dezelfde textuur als de middenlaag met een langzamere snelheid, omgekeerde bevestigingen, en tegenovergestelde eigenschapsconfiguraties. Dit zorgt ervoor dat de texturen nooit de kans krijgen om volledig op elkaar uit te lijnen terwijl ze in dezelfde richting worden gerenderd, wat zou toelaten dat spelers de onrealistische textuurherhaling gemakkelijk opmerken.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Bottom-Layer.jpg) Onderste laag

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Middle-Layer.jpg) Middenlaag

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Top-Layer.jpg) Bovenste laag

Het stapelen van drie [Beam](/docs/nl-nl/reference/engine/classes/Beam)  objecten creëert een illusie van parallax om de lava te laten lijken alsof het een gevoel van diepte en volume heeft waar de lava met verschillende snelheden stroomt, ook al zijn het slechts drie 2D afbeeldingen. Dit laat spelers weten dat er een gevoel van turbulentie binnen de kloof is, zowel op als onder het oppervlak van de lava.

![De 2D textuur die de korst bovenop de stromende lava vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Crust-Texture.jpg) Korst Textuur = rbxassetid://17023930265

Om de stromende magma van de caldera in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle stromende magma-objecten te bevatten, en hernoem de map naar StromendeMagma .

2.

Voeg een blok  onderdeel toe aan de StromendeMagma  map, en hernoem het naar MagmaRivierBeam .

3.

Verplaats MagmaRivierBeam  iets onder de rand van de caldera.

 ![Een schuin bovenaanzicht van de vulkaan met een gemarkeerd blokonderdeel.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LavaFlow-3.jpg)

4.

Configureer bevestigingen voor alle stromende magma-balken vanuit de caldera om hun texturen te renderen.

1.

Voeg een bevestiging toe aan MagmaRivierBeam , en draai de bevestiging totdat de gele visuele hulp naar de caldera wijst.

2.

Voeg een andere bevestiging toe aan MagmaRivierBeam , positioneer deze naar de splitsing in de kloof, en draai de bevestiging totdat de gele visuele hulp naar beneden in de grond wijst.

 ![Een schuin bovenaanzicht van de vulkaan met twee bevestigings visuele hulpmiddelen gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LavaFlow-4.jpg)

5.

Voeg een Beam  toe aan MagmaRivierBeam , en hernoem het naar Magma .

6.

Wijs de bevestigingen van het onderdeel toe aan Magma .

1.

In het Explorer  venster, selecteer Magma .

2.

In het Properties  venster,

1.

Stel Attachment0  in op de bevestiging aan de rand van de caldera.

2.

Stel Attachment1  in op de bevestiging bij de splitsing in de kloof. De balk rendert zijn standaard textuur tussen de twee bevestigingen.

 ![Een schuin bovenaanzicht van de vulkaan met twee blokonderdelen die de standaard balktextuur tussen de bevestigingen renderen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LavaFlow-6.jpg)

7.

Pas het visuele uiterlijk van de balk aan zodat het eruit ziet als stromende magma.

1.

In het Explorer  venster, zorg ervoor dat Magma  nog steeds is geselecteerd.

2.

In het Properties  venster,

1.

Stel Width0  in op 50  om de textuur vanaf de as waar het begint te renderen te verbreden.

2.

Stel Width1  in op 50  om de textuur te verbreden als deze de splitsing in de kloof bereikt.

3.

Stel CurveSize0  in op -50  om de textuur van de vloer van de kloof af te krommen.

4.

Stel CurveSize1  in op 5  om de textuur in de splitsing in de kloof te krommen.

5.

Stel Color  in op een kleursequentie die begint met felrood en donkerrood wordt over de levensduur van de balk om de afkoeling van de magma te simuleren.

-

Time  = 0 , RGB Value  = 255, 51, 0

-

Time  = 0.5 , RGB Value  = 211, 39, 0

-

Time  = 1 , RGB Value  = 118, 24, 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LavaFlow-7Color.jpg)

1.

Stel Transparency  in op een nummersequentie die de magma levendiger maakt tussen de bevestigingspunten.

-

Time  = 0 , Value  = 1

-

Time  = 0.0916 , Value  = 0

-

Time  = 0.867 , Value  = 0

-

Time  = 0.941 , Value  = 0.725

-

Time  = 1 , Value  = 1

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LavaFlow-7Transparency.jpg)

1.

Stel LightEmission  in op 1  om de balk aanzienlijk te verlichten.

2.

Stel LightInfluence  in op 0  om te voorkomen dat het omgevingslicht de kleur van de balk beïnvloedt.

3.

Stel Brightness  in op 8  om het licht dat van de balk wordt uitgezonden te schalen.

8.

Voeg een andere Beam  toe aan MagmaRivierBeam , hernoem het naar Korst1 , en koppel de bevestigingen van het onderdeel aan Korst1  met dezelfde procedure als stap 6.

9.

Pas het visuele uiterlijk van de balk aan zodat het eruit ziet als korst bovenop de magma.

1.

In het Explorer  venster, zorg ervoor dat Korst1  nog steeds is geselecteerd.

2.

In het Properties  venster,

1.

Stel Texture  in op rbxassetid://17023930265  om een nieuwe textuur te renderen die eruit ziet als stromende korst.

2.

Stel Width0  in op 35  om de textuur vanaf de as waar het begint te renderen te verbreden.

3.

Stel Width1  in op 25  om de textuur te verbreden als deze de splitsing in de kloof bereikt.

4.

Stel TextureSpeed  in op 0.01  om de stroom van de textuur aanzienlijk te vertragen.

5.

Stel TextureLength  in op 3  om de lengte van de textuur iets uit te rekken.

6.

Stel CurveSize0  in op -50  om de textuur van de vloer van de kloof af te krommen.

7.

Stel CurveSize1  in op 5  om de textuur in de splitsing in de kloof te krommen.

8.

Stel Color  in op 83, 83, 83  om de balk een grijze tint te geven.

9.

Stel Transparency  in op een nummersequentie die de korst levendiger maakt tussen de bevestigingspunten.

-

Time  = 0 , Value  = 1

-

Time  = 0.22 , Value  = 0

-

Time  = 0.85 , Value  = 0

-

Time  = 1 , Value  = 1

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/LavaFlow-9Transparency.jpg)

1.

Stel ZOffset  in op 1  om de textuur iets van de caldera af te plaatsen.

10.

Dupliceer Korst1 , hernoem het naar Korst2 , en in het Properties  venster,

1.

Stel Attachment0  in op de bevestiging bij de splitsing in de kloof.

2.

Stel Attachment1  in op de bevestiging aan de rand van de caldera.

3.

Stel Width0  in op 25  om de textuur vanaf de as waar het begint te renderen te verbreden.

4.

Stel Width1  in op 35  om de textuur te verbreden als deze de splitsing in de kloof bereikt.

5.

Stel TextureSpeed  in op -0.008  om de stroom van de textuur aanzienlijk te vertragen.

6.

Stel TextureLength  in op 2  om de lengte van de textuur iets te unstretchen.

7.

Stel CurveSize0  in op -5  om de textuur van de vloer van de kloof af te krommen.

8.

Stel CurveSize1  in op 50  om de textuur in de splitsing in de kloof te krommen.

9.

Stel ZOffset  in op 2  om de textuur van de andere korst af te plaatsen.

11.

OPTIONAL

 Gebruik dezezelfde procedure om meer balken rond de splitsing in de kloof te creëren om de magma af te leiden. Zorg ervoor dat je de eigenschappen aanpast om de texturen te vertragen en magma te simuleren die donkerder van kleur is naarmate het afkoelt.

### [Rookpluim](#rookpluim)[](#rookpluim)

Een rookpluim  van de caldera stoot warme onder druk staande gas, stoom, en vulkanische as de atmosfeer in. Deze mix van vulkanische emissie kan in de echte wereld kilometers ver worden gezien, dus vulkaanontwerpen bevatten vaak grote rookpluimen om een significant punt van interesse in de 3D-ruimte te zijn.

In plaats van dikke, pyroclastische rook uit te stoten die men onmiddellijk zou zien na een explosieve uitbarsting, gebruikt het voorbeeld een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  object om deeltjes uit te stoten die eruit zien als dunne rookdamp die van kleur verandert terwijl ze omhoog stijgen. Deze techniek bereikt twee doelen:

-

Het breekt de silhouet van de achtergrondkrater op, waardoor er meer visuele interesse rond de vulkaanuitbarsting ontstaat.

-

Het laat de rook eruit zien alsof het licht van de omgeving accepteert terwijl het nog steeds een donkere aanwezigheid uitstraalt alsof de rook onzuiverheden in de lucht verbrandt voordat het grijs wordt zoals de nachtelijke lucht.

![De 2D textuur die de rook vertegenwoordigt die uit de caldera stijgt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Mist-Texture.png) Rook Textuur = rbxassetid://16830667309

Om de rookpluim van de caldera in het voorbeeld [Vulkaan Eiland - Compleet](https://www.roblox.com/games/17374256579/Volcano-Island-Complete)  plaatsbestand opnieuw te creëren:

1.

Voeg een blok  onderdeel toe aan de Caldera  map, en hernoem het naar RookPluim .

2.

Positioneer RookPluim  onder de caldera, en schaal het tot ongeveer de grootte van het oppervlak van de caldera.

 ![Een schuin zijaanzicht van de vulkaan met een gemarkeerd blokonderdeel onder de caldera.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Plume-2.jpg)

3.

Voeg een ParticleEmitter  toe aan RookPluim , en hernoem de emitter naar Rook .

4.

Selecteer Rook , en in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16830673704  om deeltjes weer te geven die eruit zien als dikke rook.1. Stel Kleur  in op een kleurenschema waarin de deeltjes verlichting in de omgeving simuleren van de caldera naar de lucht door te beginnen met zwart, licht perzik te worden, en dan grijs.

-

Tijd  = 0 , RGB Waarde  = 0, 0, 0

-

Tijd  = 0.374 , RGB Waarde  = 195, 104, 76

-

Tijd  = 0.469 , RGB Waarde  = 225, 121, 86

-

Tijd  = 0.709 , RGB Waarde  = 111, 111, 111

-

Tijd  = 1 , RGB Waarde  = 113, 113, 113

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Plume-4Color.jpg)

1.

Stel Transparantie  in op een getallenreeks waarin de deeltjes beginnen als transparant, volledig ondoorzichtig worden in het begin van hun levensduur, en dan weer transparant worden tegen het einde van hun levensduur.

-

Tijd  = 0 , Waarde  = 1

-

Tijd  = 0.0622 , Waarde  = 0

-

Tijd  = 0.845 , Waarde  = 0

-

Tijd  = 0 , Waarde  = 1

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-volcanoes/Plume-4Transparency.jpg)

1.

Stel ZOffset  in op -10  om de textuur dichter bij de bovenkant van de caldera te plaatsen.

2.

Stel Levensduur  in op 50, 60  om willekeurig de levensduur van elk deeltje tussen 50 en 60 seconden in te stellen.

3.

Stel Snelheid  in op 0.3  om ongeveer elke 3 seconden een deeltje uit te stoten.

4.

Stel Rotatie  in op -360, 360  om elk deeltje willekeurig in een cirkel te oriënteren.

5.

Stel Rotatiesnelheid  in op -5, 5  om elk deeltje willekeurig tussen -5 en 5 graden per seconde uit te stoten.

6.

Stel Verspreidingshoek  in op 5, 5  om deeltjes in een kleine hoek langs de X- en Z-as uit te stoten.

7.

Stel Versnelling  in op 0, 7, 0  om een opwaartse kracht te simuleren en deeltjes naar de lucht te trekken.

8.

Stel Luchtweerstand  in op 1  zodat deeltjes hun snelheid verliezen met exponentiële afname.

9.

Schakel WindBeïnvloedtLuchtweerstand  in zodat de wind in de omgeving de rook rondduwt.

10.

Stel Lichtemissie  in op 0.1  om de deeltjes iets te verlichten.

11.

Stel Lichtinvloed  in op 0.06  om aanzienlijk te verminderen hoeveel het omgevingslicht de kleur van de deeltjes beïnvloedt.

5.

Voer in de Opdrachtbalk  de volgende string in om de grootte van elk deeltje van 40 naar 100 studs te vergroten gedurende hun levensduur met een kleine variatie:

```

workspace.Caldera.SmokePlume.Smoke.Size = NumberSequence.new{NumberSequenceKeypoint.new(0,40,5), NumberSequenceKeypoint.new(1,100,15)}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
