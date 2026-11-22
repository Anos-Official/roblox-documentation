<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/lighting/enhance-indoor-environments -->

Verbeter binnenomgevingen met realistische verlichting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Licht

# Verbeter binnenomgevingen met realistische verlichting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting is de meest geavanceerde en krachtige [LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  die je kunt gebruiken voor het renderen van de 3D-omgeving binnen je games. Het biedt pixel-perfecte lichtemissie, gedetailleerde schaduwen en speculaire highlights die de verlichting in de echte wereld nabootsen voor zowel binnen- als buitenruimtes.

Met het [Lighting Indoors - Start](https://www.roblox.com/games/17561948176/UCT-Lighting-Indoors)  .rbxl  bestand als startpunt en [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  als referentie, laat deze tutorial je zien hoe je realistische verlichting kunt gebruiken met strategische globale en lokale lichtbronconfiguraties om realistisch, meeslepend binnenverlichtingsgedrag te produceren dat spelers naar de uitgang van de cabine leidt, inclusief richtlijnen over:

-

Zorgen dat glanzende oppervlakken nauwkeurige reflecties hebben die periodiek worden bijgewerkt terwijl de omgeving dynamisch verandert.

-

De zon en de aarde naar nieuwe posities verplaatsen om zonlicht vanuit ramen op specifieke oppervlakken te richten.

-

De omgevingskleur en dichtheid van de atmosfeer aanpassen.

-

Lichtbronnen kiezen om unieke omgevingsproblemen op te lossen met prestaties en optimalisatie in gedachten.

-

Je lichtbronnen in balans brengen met hoe de camera hun verlichtingsgedrag waarneemt.

Als je op enig moment vastloopt in het proces, kun je Lighting Indoors - Complete  gebruiken als referentie om je voortgang te vergelijken.

![De start binnenomgeving die je kunt gebruiken om deze tutorial te voltooien.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Sample-Start.jpg) Lighting Indoors - Start

![De complete binnenomgeving met globale en lokale verlichting die je aan het einde van deze tutorial zult creëren.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Sample-Complete.jpg) Lighting Indoors - Complete

## [Configureer globale verlichting](#configureer-globale-verlichting)[](#configureer-globale-verlichting)

Globale verlichting is de luminescentie van de zon of de maan in een game. Terwijl deze tutorial zich richt op het verbeteren van de verlichting binnen de cabine die van de zon is afgeschermd, is het belangrijk om globale verlichting te configureren omdat het de luchtdeeltjes binnen de algemene atmosfeer van de game beïnvloedt, ongeacht of ze binnen of buiten zijn.

Door een paar belangrijke standaard eigenschappen in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service en zijn kind [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object aan te passen, kun je dramatisch veranderen hoe zowel de atmosfeer als het zonlicht dat door het raam komt, aan spelers verschijnt, evenals hoe deze verlichting interactie heeft met elk ander object dat je in de game plaatst.

### [Schakel realistische verlichting in](#schakel-realistische-verlichting-in)[](#schakel-realistische-verlichting-in)

De [LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  eigenschap bepaalt het gedrag van zowel globale als lokale verlichting in je game. Studio begint elke game met [Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting die een plattere uitstraling met zachtere lichten en schaduwen weergeeft. Om echter de omgeving te verbeteren en ervoor te zorgen dat je lokale lichtbronnen ook nauwkeurige schaduwen, verlichting en speculaire highlights produceren, moet je [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting inschakelen.

Deze verlichtingsconfiguratie stelt zowel je globale als lokale verlichting in staat om samen te werken en meer realistische en meeslepende visuals te bieden. Om dit te demonstreren, bekijk hoe het verlichtingsgedrag voor de radio verandert wanneer Lighting Indoors - Complete  verschillende verlichtingsstijlen gebruikt. De lokale verlichting van het kaarslicht en de radio met de [Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingsstijl produceert geen schaduwen zoals de globale verlichting van de zon, en de details van de leren en houten materialen van de radio verdwijnen.

![Een close-up van de radio verlicht met de Soft verlichtingsstijl.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Radio-Soft.jpg)[Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingsstijl

![Een close-up van de radio verlicht met de Realistic verlichtingsstijl.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Radio-Realistic.jpg)[Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingsstijl

Het is belangrijk op te merken dat vanwege de manier waarop het [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingssysteem binnenruimtes detecteert om toepasselijke schaduwen te berekenen en weer te geven, het het beste is om binnenruimtes te omringen met [Part](/docs/nl-nl/reference/engine/classes/Part)  objecten met een dikte van ten minste 1 stud om ongewenst buitenlicht te voorkomen dat in de cabine lekt. Om bijvoorbeeld te voorkomen dat de binnen- en buitenverlichting zich vermengen, gebruikt het voorbeeld Lighting Indoors - Start  delen met een minimale dikte van 2,5 studs om alle [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  muren en plafondobjecten te omringen zonder het raam te blokkeren, zodat het zonlicht nog steeds de kamer kan binnenkomen.

![Een bovenaanzicht van de cabine die de mesh muren en plafonds niet omringt met delen. Het buitenlicht sijpelt de cabine binnen.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Cabin-NoParts.jpg) Cabine die de mesh muren en het plafond niet omringt met delen

![Een bovenaanzicht van de cabine die de mesh muren en plafonds omringt met delen. Het binnenlicht is niet beïnvloed door de buitenverlichting.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Cabin-WithParts.jpg) Cabine die de mesh muren en het plafond omringt met delen

Om Realistic  verlichting in te schakelen:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, klik op de LightingStyle  dropdown, en selecteer Realistic .

 ![Een volledig beeld van de startcabine met realistische verlichting.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/LightingStyle-Realistic.jpg)

### [Verhoog metalen reflecties](#verhoog-metalen-reflecties)[](#verhoog-metalen-reflecties)

Een belangrijk voordeel van het gebruik van realistische verlichting is het vermogen om speculaire highlights te produceren op glanzende, metalen oppervlakken. Dit verhoogt de realiteit van binnenomgevingen omdat het het gedrag van verlichting in de echte wereld nabootst, en het biedt een gevoel van diepte aan objecten in de 3D-ruimte.

Standaard gebruiken alle materialen [fysiek-gebaseerde rendering](/docs/nl-nl/art/modeling/surface-appearance)  (PBR) texturen die je in staat stellen om realistische oppervlakken weer te geven in verschillende verlichtingsscenario's door meerdere textuurkaarten op een enkel object te gebruiken. Dit betekent dat wanneer je de ingebouwde materialen van Studio gebruikt:

-

De metalness en ruwheid van een bepaald oppervlak zijn al voor je gedefinieerd zonder extra stappen.

-

Objecten met de ingebouwde materialen van Studio reageren van nature nauwkeuriger op de verlichting in je omgeving met realistische reflecties.

Je kunt dit effect verbeteren met de realistische verlichtingsstijl door de globale verlichting's [Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  eigenschappen te verhogen, vooral wanneer je elke eigenschap op 1  instelt. Deze stap is bijzonder belangrijk in deze tutorial omdat het ervoor zorgt dat alle PBR-texturen in de game, inclusief die van [MaterialVariants](/docs/nl-nl/reference/engine/classes/MaterialVariant)  of [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten, er op hun best uitzien en hun omgeving nauwkeurig reflecteren.

Om dit concept te demonstreren, bekijk de metalen bases van de kaarsen met verschillende waarden voor [Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  eigenschappen. Wanneer je deze waarden verhoogt, reflecteert het metaal de verlichting van zowel de globale als lokale lichtbronnen nauwkeuriger, waardoor het materiaal tastbaarder wordt voor spelers terwijl ze de omgeving verkennen.

![Een close-up van een standbeeld en kaarsengroep met doffe metalen reflecties.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/WithoutReflections.jpg)[Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  = 0

![Een close-up van een standbeeld en kaarsengroep met glanzende metalen reflecties.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/WithReflections.jpg)[Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  = 1

Om de metalen reflecties in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, zorg ervoor dat EnvironmentalDiffuseScale  en EnvironmentSpecularScale  zijn ingesteld op 1 . Als dat zo is, is het metaal in de game nauwkeurig reflecterend.

### [Verander de tijd van de dag](#verander-de-tijd-van-de-dag)[](#verander-de-tijd-van-de-dag)

Naast het aanpassen van de algemene atmosfeer van de 3D-ruimte, is globale verlichting een krachtig hulpmiddel bij het creëren van aandachtspunten binnen de omgeving die je wilt dat spelers verkennen. Wanneer je deze techniek koppelt aan lokale lichtbronnen, kun je spelers indirect naar elk gedeelte van het speelgebied leiden en voorkomen dat ze iets belangrijks missen.

Om dit proces te demonstreren, verplaatst het voorbeeld Lighting Indoors - Complete  strategisch de zon zodat het licht onder een hoek de cabine binnenkomt, waarbij de enige deur van de cabine wordt belicht. Terwijl spelers de kamer scannen, trekt elke lichtbron indirect de aandacht van de speler en trekt ze met de klok mee: eerst naar de lokale lichtbron van de open haard, vervolgens naar de globale en lokale lichtbronnen nabij het raam, en tenslotte naar de globale lichtbron die op de uitgang schijnt.

 ![Een volledig beeld van de binnenruimte van de cabine met alle zichtbare lichtbronnen.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Cabin-Final.jpg)

Om de tijd van de dag in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster,

1.

Stel ClockTime  in op 15.6 . De zon beweegt naar de geschatte positie die het zou hebben om 15:45 uur.

2.

OPTIONAL

 Stel GeographicLatitude  in op 323 .

 ![Een volledig beeld van de cabine met de zon in zijn nieuwe positie.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/TimeOfDay-2.jpg)

### [Versterk de zonnestralen](#versterk-de-zonnestralen)[](#versterk-de-zonnestralen)

Nu de zon op een ideale positie aan de hemel staat om zijn licht door het raam te laten schijnen en een aandachtspunt te creëren, kun je het kindobject [SunRays](/docs/nl-nl/reference/engine/classes/SunRaysEffect)  van de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service gebruiken om de verlichting van de zon te overdrijven door zijn individuele zonnestralen te versterken. In tegenstelling tot andere statische atmosferische effecten, veranderen zonnestralen dynamisch van vorm wanneer objecten tussen de camera van de speler en de zon komen, waardoor realistische licht- en schaduwvisuals ontstaan.

Om dit te demonstreren, bekijk hoe de vorm van de zonnestralen verandert wanneer je hun intensiteit en spreiding verhoogt. Terwijl de zonnestralen met de standaardconfiguratie subtiel naar het raam toe komen, schijnen de zonnestralen met de aangepaste configuratie de cabine binnen. Naast het verbeteren van je visuals, verbetert dit effect ook het effect van de luchtdeeltjesdichtheid later in de tutorial omdat de zonnestralen de dichte luchtdeeltjes vanuit bijna elke hoek benadrukken terwijl spelers de ruimte doorkruisen.

![Een vooraanzicht van het raam met de zonnestralen nauwelijks zichtbaar.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SunRays-Default.jpg) Standaard zonnestralen

![Een vooraanzicht van het raam met de zonnestralen volledig zichtbaar en die de cabine binnen schijnen.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SunRays-Custom.jpg) Aangepaste zonnestralen

Om de zonnestralen in de atmosfeer in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer het kindobject SunRays  van de Lighting  service.

2.

In het Properties  venster,

1.

Stel Intensity  in op 0.023  om de opaciteit van de zonneschijn te verhogen.

2.

Stel Spread  in op 0.266  om de spreiding van de zonnestralen over de lucht te verbreden.

### [Pas de kleur van het omgevingslicht aan](#pas-de-kleur-van-het-omgevingslicht-aan)[](#pas-de-kleur-van-het-omgevingslicht-aan)

Het aanpassen van de kleur van het omgevingslicht, of het algemene, indirecte licht in de 3D-ruimte, is een veelgebruikte methode om zowel de sfeer van een omgeving te bepalen als te bepalen of de verlichting warm of koel is. Er zijn twee [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  eigenschappen die de kleur van het omgevingslicht regelen:

-

[Lighting.OutdoorAmbient](/docs/nl-nl/reference/engine/classes/Lighting#OutdoorAmbient)  regelt het omgevingslicht waar de lucht zichtbaar is.

-

[Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  regelt het omgevingslicht binnen ruimtes waar iets de lucht blokkeert, zoals binnenomgevingen.

Standaard zijn beide eigenschappen ingesteld om een koele grijze tint te produceren, maar dit komt niet overeen met de lichtbronnen binnen de cabine. Om dit probleem op te lossen, past het voorbeeld Lighting Indoors - Complete  de [Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  aan om een warme, oranje tint te produceren die overeenkomt met de warmte van het vuur in de open haard en de kaarsen, evenals de gloed van de ondergang. Hoewel deze verandering subtiel is, kun je het verschil aanzienlijk zien in indirect verlichte gebieden, zoals de schaduwen op de vloer.

![Een schuin bovenaanzicht van schaduwen op de vloer die een koele omgevingskleur hebben.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Ambient-Default.png)[Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  = 70, 70, 70

![Een schuin bovenaanzicht van schaduwen op de vloer die een warme omgevingskleur hebben.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Ambient-Custom.png)[Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  = 83, 70, 57

Om de kleur van het omgevingslicht in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer Lighting.

2.

In het Properties  venster, stel Ambient  in op 83, 70, 57 . Het omgevingslicht verandert in een warmere en donkerdere oranje tint.

 ![Een volledig beeld van de cabine met de nieuwe warme omgevingsverlichting.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Ambient-2.jpg)

### [Kies een complementaire skybox](#kies-een-complementaire-skybox)[](#kies-een-complementaire-skybox)

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service heeft een kindobject [Sky](/docs/nl-nl/reference/engine/classes/Sky)  met zes individuele eigenschappen die samen de skybox creëren die de lucht van een game vormt. Skyboxes kunnen een grote impact hebben op de uitstraling en het gevoel van wat er in je omgeving is, dus het is belangrijk om zorgvuldig te overwegen hoe je een skybox kunt kiezen die de visuele kwaliteit van je game verbetert, vooral omdat het de algehele sfeer beïnvloedt die in binnenruimtes sijpelt.

Omdat het voorbeeld Lighting Indoors - Complete  een warme sfeer vereist, gebruikt het een skybox die voornamelijk warme tinten nabij de skyline prioriteert, zoals heldere gele, levendige oranje en enkele lichte groene tinten. Voor informatie over hoe je skyboxes kunt maken en aanpassen, zie [Skyboxes](/docs/nl-nl/environment/skybox) .

![De 2D-textuur die de achterste kubusvormige zijde van de skybox vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SkyboxBk.png) SkyboxBk

![De 2D-textuur die de onderkant van de skybox vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SkyboxDn.png) SkyboxDn

![De 2D-textuur die de voorkant van de skybox vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SkyboxFt.png) SkyboxFt

![De 2D-textuur die de linker kubusvormige zijde van de skybox vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SkyboxLf.png) SkyboxLf

![De 2D-textuur die de rechter kubusvormige zijde van de skybox vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SkyboxRt.png) SkyboxRt

![De 2D-textuur die de bovenste kubusvormige zijde van de skybox vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/SkyboxUp.png) SkyboxUp

Om de skybox in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer het kindobject Sky  van de Lighting  service.

2.

In het Properties  venster,

1.

Stel SkyboxBk  in op rbxassetid://162001887 .

2.

Stel SkyboxDn  in op rbxassetid://161998893 .

3.

Stel SkyboxFt  in op rbxassetid://162001897 .

4.

Stel SkyboxLf  in op rbxassetid://162001904 .

5.

Stel SkyboxRt  in op rbxassetid://162001919 .

6.

Stel SkyboxUp  in op rbxassetid://162001926 .

 ![Een volledig beeld van de cabine met de nieuwe skybox.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Skybox-2.jpg)

### [Verhoog de dichtheid van luchtdeeltjes](#verhoog-de-dichtheid-van-luchtdeeltjes)[](#verhoog-de-dichtheid-van-luchtdeeltjes)

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service heeft een kindobject [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  met eigenschappen die je in staat stellen om realistische omgevingen te simuleren door zonlicht op unieke manieren te verstrooien. Terwijl sommige van deze eigenschappen meer evident zijn in buitenomgevingen, zoals die welke de silhouetten en menging van verre objecten nabij de skyline beïnvloeden, beïnvloeden andere de dichtheid en kleur van de luchtdeeltjes die door de 3D-ruimte aanwezig zijn, ongeacht of ze binnen of buiten zijn.

Bijvoorbeeld, de [Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  eigenschap regelt hoeveel deeltjes er in de lucht van je game bestaan. Wanneer je deze eigenschap verhoogt, creëren de extra deeltjes een gevoel van dikte en gewicht in de 3D-ruimte dat tastbaar is voor spelers die je wereld verkennen. Dit is nuttig voor het toevoegen van textuur en indirecte verlichting aan een omgeving zonder duidelijke lokale verlichtingsobjecten.

Om deze techniek te illustreren, bekijk de volgende twee afbeeldingen van de Lighting Indoors - Complete  cabine met verschillende luchtdeeltjesdichtheden. Wanneer [Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  is ingesteld op 0 , is de cabine koud en donker ondanks de lokale lichtbronnen, maar wanneer [Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  is ingesteld op 0.5 , is de cabine warm en mistig. Dit effect is bijzonder impactvol omdat het [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object een warme oranje tint aan luchtdeeltjes toevoegt op basis van de kleuren van zijn skybox.

![Een schuin zijaanzicht van de cabine die donker is met heldere lucht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/LowDensity.jpg)[Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  = 0

![Een schuin zijaanzicht van de cabine die helder is met mistige lucht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/HighDensity.jpg)[Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  = 0.5

Om de dichtheid van de luchtdeeltjes in de atmosfeer in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer het kindobject Atmosphere  van de Lighting  service.

2.

In het Properties  venster, stel Density  in op 0.5 . De lucht wordt mistig.

 ![Een volledig beeld van de cabine met dichte luchtdeeltjes.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Density-2.jpg)

## [Configureer lokale verlichting](#configureer-lokale-verlichting)[](#configureer-lokale-verlichting)

Lokale verlichting is de luminescentie van lokale [lichtbronnen](/docs/nl-nl/effects/light-sources)  in je game, zoals [PointLight](/docs/nl-nl/reference/engine/classes/PointLight) , [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) , en [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight)  objecten. Nadat je je globale verlichting hebt geconfigureerd om te voldoen aan de algemene verlichtings- en atmosfeervereisten van de game, is het belangrijk om deze lokale lichtbronnen te gebruiken om te voldoen aan de specifieke verlichtingsbehoeften van alles in de scène dat je wilt verlichten binnen de 3D-ruimte.

De volgende secties demonstreren hoe je elk type lokale lichtbron kunt creëren en een paar van zijn standaard eigenschappen kunt aanpassen om significant te veranderen hoe de lokale verlichting je globale verlichting aanvult en interactie heeft met de algehele omgeving.

### [Verlicht de kaarsen](#verlicht-de-kaarsen)[](#verlicht-de-kaarsen)

De eerste objecten in de scène die de ruimte moeten verlichten zijn de groepen kaarsen op de dressoir nabij het raam. Hun standaardconfiguratie in het Lighting Indoors - Start  voorbeeld omvat de volgende [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  objecten om zachte beweging aan hun vlammen toe te voegen:

-

CandleFire  - Produceert lichttaperde deeltjes om de vlam van de kaars na te bootsen.

-

CandleSmoke  - Produceert donkere taperde deeltjes om de rook van de kaars na te bootsen.

-

CandleFillLight  - Produceert cirkelvormige deeltjes om de zachte gloed van de kaars na te bootsen.

Hoewel dit een uitstekende start is, produceren de kaarsen nog steeds geen realistisch verlichtingsgedrag dat het nabijgelegen gebied volledig verlicht of weerkaatst van omliggende objecten. Om deze verlichtingsbehoefte op te lossen, introduceert het voorbeeld Lighting Indoors - Complete  een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  object in het midden van de kaarsengroep.

[PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  objecten stoten licht sferisch uit vanuit een enkel punt in alle richtingen, vergelijkbaar met een kleine zon. Dit verlichtingsgedrag maakt ze nuttig voor objecten die omnidirectioneel licht produceren, zoals onbedekte gloeilampen, fakkels en kaarslicht. Om dit te illustreren, bekijk de volgende twee afbeeldingen van hoe de scène verandert met en zonder een puntlicht. De scène zonder een puntlicht produceert een zachte verlichting die alleen de kaars zelf verlicht, maar de scène met een puntlicht produceert sterkere verlichting die de kaars, nabijgelegen muren en de subtiele details van het standbeeld verlicht.

![Een schuin zicht op de radio van de cabine, standbeeld en een kaarsengroep zonder een puntlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Candles-WithoutPL.jpg) Zonder puntlicht

![Een schuin zicht op de radio van de cabine, standbeeld en een kaarsengroep met een puntlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Candles-WithPL.jpg) Met puntlicht

Puntlichten kunnen meer prestatie-intensief zijn op low-end apparaten dan andere lokale lichtbronnen omdat puntlichten in alle richtingen projecteren. Om je game te optimaliseren, overweeg hoeveel puntlichten nodig zijn zonder je ideale verlichtingsgedrag in gevaar te brengen. Bijvoorbeeld, het voorbeeld plaatst slechts één puntlicht in het midden van de kaars omdat elke kaarsvlam klein genoeg is dat individuele puntlichten de visuals binnen het speelgebied niet merkbaar verbeteren.

Om lokale kaarsverlichting in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

Voeg een puntlicht toe aan een van de kaarsengroepen.

1.

In het Explorer  venster, breid het Candle_Group_A  model uit.

2.

Beweeg de muis over het FillLight  deel, klik vervolgens op het ⊕ pictogram. Een contextmenu verschijnt.

3.

Kies in het contextmenu om een PointLight  in te voegen.

2.

Selecteer het nieuwe puntlicht, en in het Properties  venster,

1.

Stel Brightness  in op 0.7  om de intensiteit van het licht te verlagen zodat het beter past bij kaarslicht.

2.

Stel Color  in op 255, 202, 156  om het licht een perzikkleur te geven en de warmte van de kaarsbron na te bootsen.

3.

Schakel Shadows  in om de kaarslicht schaduwen te laten produceren.

3.

Herhaal dit proces voor Candle_Group_B .

4.

OPTIONAL

 Gebruik dezelfde techniek van de vorige stappen om een puntlicht met je eigen configuratie toe te voegen om het vuur in de open haard te verlichten.

### [Zet de bureaulamp aan](#zet-de-bureaulamp-aan)[](#zet-de-bureaulamp-aan)

Het tweede object in de scène dat de ruimte moet verlichten is de bureaulamp in de achterste hoek van de cabine. Wanneer je beslist welk lokaal lichtobject je wilt gebruiken, is het belangrijk om te bekijken hoe het type en de vorm van de lichtbron beïnvloeden hoe het licht in de echte wereld schijnt. Bijvoorbeeld, omdat de bureaulamp in het Lighting Indoors - Start  voorbeeld een witte gloeilamp onder een gebogen, donkergroene kap heeft, moet de lamp twee verschillende soorten licht produceren:

-

Helder wit licht dat alleen in de richting van het bureau verlicht.

-

Subtiel groen licht dat door de donkergroene kap in alle andere richtingen lekt, behalve het heldere witte licht.

Om de eerste verlichtingsbehoefte op te lossen, introduceert het voorbeeld Lighting Indoors - Complete  een [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight)  in de bureaulamp om naar buiten te schijnen vanuit waar het niet bedekt is door de kap van de lamp. [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight)  objecten stoten licht uit in een enkele richting in de vorm van een kegel met een sferische basis, en ze bevatten een [Face](/docs/nl-nl/reference/engine/classes/SpotLight#Face)  eigenschap die bepaalt van welke zijde/axis het licht wordt uitgestraald. Dit maakt hun verlichtingsgedrag nuttig voor objecten die directioneel licht produceren, zoals straatlantaarns, zaklampen en koplampen.

Om de tweede verlichtingsbehoefte op te lossen, gebruikt het voorbeeld een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  die een zacht groen licht produceert dat de hele hoek van de cabine verlicht zonder significant op te vallen binnen het heldere witte licht. Om dit te illustreren, bekijk de volgende twee afbeeldingen van hoe de scène verandert met en zonder een extra puntlicht. Beide scènes bevatten vergelijkbaar helder wit licht, maar de scène met het puntlicht creëert realistisch verlichtingsgedrag dat weerkaatst van het nabijgelegen standbeeld en de boekenkasten om de hoek van de cabine zichtbaar te maken en een aandachtspunt te creëren.

![Een close-up van de bureaulamp zonder een puntlicht om de ruimte achter de lamp te verlichten.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Lamp-2.jpg) Zonder puntlicht

![Een close-up van de bureaulamp met een puntlicht om de ruimte achter de lamp te verlichten.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Lamp-4.jpg) Met puntlicht

Om de lamp lokale verlichting in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

Voeg een spotlight toe aan een van de kaarsengroepen.

1.

In het Explorer  venster, breid het Bankers_Lamp  model uit, en vervolgens het Lamp_Hood  mesh.

2.

Beweeg de muis over het Lightbulb  mesh, klik vervolgens op het ⊕ pictogram. Een contextmenu verschijnt.

3.

Kies in het contextmenu om een SpotLight  in te voegen.

 ![Een close-up van de bureaulamp met een standaard spotlight.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Lamp-1.jpg)

2.

Selecteer de nieuwe spotlight, en in het Properties  venster,

1.

Stel Face  in op Bottom  om de spotlight naar het bureau te richten.

2.

Stel Angle  in op 140  om het licht in een halve bolvorm te projecteren in plaats van een kegelvorm.

3.

Stel Brightness  in op 4  om de intensiteit van het licht te verhogen.

4.

Stel Color  in op 255, 238, 202  om het licht een lichte tan kleur te geven en de subtiele warmte van de lampbron na te bootsen.

5.

Stel Range  in op 12  om de grootte van het gebied dat de spotlight verlicht te verkleinen zodat het de vloer raakt.

6.

Schakel Shadows  in om de lamplicht schaduwen te laten produceren en een dramatisch effect te creëren.

 ![Een close-up van de bureaulamp met een aangepaste spotlight.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Lamp-2.jpg)

3.

Voeg een puntlicht toe dat het indirecte groene licht van de kap van de lamp nabootst.

1.

In het Explorer  venster, beweeg de muis over het FillLight  deel, klik vervolgens op het ⊕ pictogram. Een contextmenu verschijnt.

2.

Kies in het contextmenu om een PointLight  in te voegen.

 ![Een close-up van de bureaulamp met een aangepaste spotlight en een standaard puntlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Lamp-3.jpg)

4.

Selecteer het nieuwe puntlicht, en in het Properties  venster,

1.

Stel Range  in op 12  om de grootte van het gebied dat het puntlicht verlicht te vergroten zodat het de muren achter het bureau kan verlichten.

2.

Stel Color  in op 142, 157, 125  om het licht een lichte mosgroene tint te geven en indirect de helderheid te verminderen.

 ![Een close-up van de bureaulamp met een aangepaste spotlight en puntlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Lamp-4.jpg)

### [Verlicht het radioscherm](#verlicht-het-radioscherm)[](#verlicht-het-radioscherm)

Het laatste object in de scène dat de ruimte moet verlichten is de klassieke radio in het midden van de standbeelden op de dressoir. Net als in de vorige sectie, wanneer je beslist welk lokaal lichtobject je wilt gebruiken, is het belangrijk om te bekijken hoe het type en de vorm van de lichtbron geen  licht in de echte wereld uitstraalt. Bijvoorbeeld, geen van de vorige lokale lichtobjecten werkt voor deze radio omdat het scherm geen licht in elke richting zou uitstralen zoals een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  object, noch vanuit een enkel punt in één richting zoals een [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) .

![Een vooraanzicht van de radio van de cabine en standbeelden. De radio bevat een puntlicht dat in elke richting verlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Radio-PointLight.jpg) Radio met een puntlicht

![Een vooraanzicht van de radio van de cabine en standbeelden. De radio bevat een spotlight die vanuit een enkel punt in één richting verlicht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Radio-SpotLight.jpg) Radio met een spotlight

In plaats daarvan introduceert het voorbeeld Lighting Indoors - Complete  een [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight)  object in de radio om naar buiten te schijnen vanuit het gehele oppervlak van het scherm. [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight)  objecten stoten licht uit van een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of een zijde van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , en ze bevatten een [Face](/docs/nl-nl/reference/engine/classes/SurfaceLight#Face)  eigenschap die bepaalt van welke zijde/axis het licht wordt uitgestraald. Dit maakt hun verlichtingsgedrag nuttig voor objecten die directioneel licht produceren vanuit een bijna vlak oppervlak, zoals TV- of computerschermen, billboards en fluorescentiepanelen.

Het is belangrijk op te merken dat ondanks dat zowel oppervlakteverlichting als spotlights een Face  eigenschap gebruiken om te bepalen van welk kubusvormig oppervlak licht wordt uitgestraald, oppervlakteverlichting zich onderscheidt van spotlights omdat hun lichtemissie verandert afhankelijk van de grootte van hun ouderobject. Om dit te demonstreren, bekijk de volgende afbeeldingen om te zien hoe de oppervlakteverlichting verandert in hoe het licht uitstraalt in verhouding tot de grootte van zijn ouderblokdeel.

![Een schuin zicht op het hert met een blokdeel ervoor. Het blokdeel bevat een spotlight die alleen vanuit het midden van het deel verlicht, en het verlicht het hert slechts gedeeltelijk.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Deer-SpotLight.jpg) De spotlight verlicht het hert vanuit het midden van zijn ouderdeel.

![Een schuin zicht op het hert met een blokdeel ervoor. Het blokdeel bevat een oppervlakteverlichting die vanuit de zijde van het deel verlicht, en het verlicht het hert en de nabijgelegen muur volledig.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Deer-SurfaceLight.jpg) De oppervlakteverlichting verlicht het hert vanuit het gehele oppervlak van zijn ouderdeel.

Om de radiosurfaceverlichting in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

Voeg een oppervlakteverlichting toe aan het scherm van de radio.

1.

In het Explorer  venster, breid het Radio_Noise  model uit, en vervolgens zijn kindmodel Radio .

2.

Beweeg de muis over het Radio_Backglow  mesh, klik vervolgens op het ⊕ pictogram. Een contextmenu verschijnt.

3.

Kies in het contextmenu om een SurfaceLight  in te voegen.

 ![Een vooraanzicht van de radio van de cabine en standbeelden. De radio bevat een oppervlakteverlichting, maar het lijkt niets te verlichten.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Radio-1.jpg)

2.

Selecteer de nieuwe oppervlakteverlichting, en in het Properties  venster,

1.

Stel Face  in op Left  om het licht van het oppervlak van de klok af te laten schijnen.

2.

Stel Brightness  in op 2  om de intensiteit van het licht iets te verhogen.

3.

Stel Color  in op 146, 255, 251  om het licht een tealblauwe tint te geven.

4.

Stel Range  in op 4  om de grootte van het gebied dat de oppervlakteverlichting verlicht te verkleinen zodat het alleen de tafel raakt.

 ![Een vooraanzicht van de radio van de cabine en standbeelden. De radio bevat een oppervlakteverlichting die de tafel zachtjes verlicht met een tealblauw licht.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Radio-2.jpg)

## [Balans lichtbronnen](#balans-lichtbronnen)[](#balans-lichtbronnen)

Het verlichten van een omgeving is een balans tussen je lichtbronnen en de perceptie van de camera van hun verlichting. Zelfs als je lichtbronnen geschikte instellingen hebben voor hoe ze de ruimte in de echte wereld zouden verlichten, moet je mogelijk aanpassen en opnieuw in balans brengen hoe de camera die verlichting waarneemt om je ideale verlichtingsgedrag te bereiken.

Bijvoorbeeld, de scène in zijn huidige staat heeft een opzettelijk warme gloed door de cabine, maar de kleuren en schaduwen lijken zowel dof als verzadigd. Om dit probleem op te lossen, past het voorbeeld Lighting Indoors - Complete  zijn globale verlichting aan om de rijkdom ervan in de camera van de speler te verhogen zonder details of contrast tussen lichte en donkere tinten in de 3D-ruimte te verliezen.

### [Pas de belichting aan](#pas-de-belichting-aan)[](#pas-de-belichting-aan)

Vergelijkbaar met het aanpassen van hoe lang de lens van een echte camera open blijft voor een foto, stelt de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service's [ExposureCompensation](/docs/nl-nl/reference/engine/classes/Lighting#ExposureCompensation)  eigenschap je in staat om aan te passen hoeveel licht de camera bereikt. Het gebruik van deze eigenschap is uniek in vergelijking met het aanpassen van de [Brightness](/docs/nl-nl/reference/engine/classes/Lighting#Brightness)  eigenschap omdat [ExposureCompensation](/docs/nl-nl/reference/engine/classes/Lighting#ExposureCompensation)  een bias toepast om het effect van de helderdere delen van de omgeving te verhogen.

Bijvoorbeeld, bekijk de volgende afbeeldingen om te zien hoe de verlichting verandert afhankelijk van of je de cabine verheldert door ofwel de globale verlichting's [Brightness](/docs/nl-nl/reference/engine/classes/Lighting#Brightness)  of [ExposureCompensation](/docs/nl-nl/reference/engine/classes/Lighting#ExposureCompensation)  eigenschap te verhogen. De cabine met een hogere [Brightness](/docs/nl-nl/reference/engine/classes/Lighting#Brightness)  eigenschap verhoogt alle helderheid van de ruimte, inclusief helderheid binnen de schaduwen, wat leidt tot een onbedoelde troebelheid in de cabine. Omgekeerd, de cabine met een hogere [ExposureCompensation](/docs/nl-nl/reference/engine/classes/Lighting#ExposureCompensation)  eigenschap verhoogt de helderheid van licht en schaduwen niet gelijkmatig, waardoor de ruimte helderder lijkt zonder de donkere kleuren volledig te verwashen.

![Een schuin zicht op een globe. De verlichting toont de huidige stap in de tutorial.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Exposure-NoChange.jpg) Cabine zoals het is

![Een schuin zicht op een globe. De verlichting is dof en gewassen.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Exposure-Brightness.jpg) Cabine met een hogere helderheid

![Een schuin zicht op een globe. De verlichting is rijker en schaduwen zijn duidelijker.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Exposure-ExposureCompensation.jpg) Cabine met een hogere belichting

Om de belichtingsniveaus in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand te recreëren:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, stel ExposureCompensation  in op 0.5  om extra belichting op de scène toe te passen.

 ![Een volledig beeld van de cabine met een hoger belichtingsniveau.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Exposure-2.jpg)

### [Pas de kleurcontrast aan](#pas-de-kleurcontrast-aan)[](#pas-de-kleurcontrast-aan)

Vergelijkbaar met het toepassen van een filter over een camera, kun je een [ColorCorrectionEffect](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect)  post-processing object aan de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service toevoegen om aan te passen hoe de camera kleur waarneemt. Dit is nuttig wanneer je kleurcorrecties wilt maken die de hele omgeving beïnvloeden in plaats van slechts een enkel object of speelgebied.

Het voorbeeld Lighting Indoors - Complete  gebruikt [ColorCorrectionEffect](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect)  om de levendigheid en het contrast tussen alle donkere en lichte kleuren te verhogen. Dit is nuttig voor het creëren van een warme, verzadigde ruimte die uitnodigend is voor spelers.

Om te recreëren hoe de camera kleur waarneemt in het voorbeeld [Lighting Indoors - Complete](https://www.roblox.com/games/17562253150/UCT-Lighting-Indoors-After)  plaatsbestand:

1.

In het Explorer  venster, beweeg de muis over de Lighting  service, klik vervolgens op het ⊕ pictogram. Een contextmenu verschijnt.

2.

Kies in het contextmenu om een ColorCorrectionEffect  in te voegen.

3.

Selecteer het nieuwe post-processing effect, en in het Properties  venster,

1.

Stel Contrast  in op 0.05  om het contrast tussen donkere en lichte kleuren te verhogen.

2.

Stel Saturation  in op 0.1  om alle kleuren levendiger te maken.

 ![Een volledig beeld van de cabine met meer kleurcontrast.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-indoor-environments/Contrast-2.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
