<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/lighting/enhance-outdoor-environments -->

Verbeter buitenomgevingen met realistische verlichting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Licht

# Verbeter buitenomgevingen met realistische verlichting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting is de meest geavanceerde en krachtige [LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  die je kunt gebruiken voor het renderen van de 3D-omgeving binnen je games. Het biedt pixel-perfecte lichtemissie, gedetailleerde schaduwen en speculaire highlights die de verlichting in de echte wereld nabootsen voor zowel binnen- als buitenruimtes.

Met het [Lighting Outdoors - Start](https://www.roblox.com/games/17835285085/Lighting-Outdoors-Start)  .rbxl  bestand als startpunt en [Lighting Outdoors - Complete](https://www.roblox.com/games/17835194683/Lighting-Outdoors-Complete)  als referentie, laat deze tutorial je zien hoe je realistische verlichting kunt gebruiken met strategische globale en lokale lichtbronconfiguraties om realistisch, meeslepend buitenverlichtingsgedrag te produceren voor een avondkampvuur scène, inclusief richtlijnen over:

-

Zorgen dat metalen oppervlakken nauwkeurige reflecties produceren terwijl lichtbronnen continu verschuiven in de omgeving, zoals dynamische beweging van het knetterende kampvuur.

-

De zon naar een nieuwe positie verplaatsen die realistisch is voor het tijdstip van de dag in de echte wereld.

-

De gelaagde tinten, dichtheid en nevel van de atmosfeer aanpassen.

-

Lokale verlichting van puntbronnen configureren om te beïnvloeden hoe deze interactie heeft met de algehele omgeving.

Als je op enig moment vastloopt in het proces, kun je Lighting Outdoors - Complete  gebruiken als referentie om je voortgang te vergelijken.

![De start buitenomgeving die je kunt gebruiken om deze tutorial te voltooien.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Intro-Before.png) Lighting Outdoors - Start

![De complete buitenomgeving met globale en lokale verlichting die je aan het einde van deze tutorial zult creëren.](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Intro-After.png) Lighting Outdoors - Complete

## [Configureer globale verlichting](#configureer-globale-verlichting)[](#configureer-globale-verlichting)

Globale verlichting is de luminescentie van de zon of de maan in een game. Door een paar belangrijke standaard eigenschappen in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service aan te passen, kun je dramatisch veranderen hoe dat licht verschijnt voor spelers, evenals hoe het interactie heeft met elk ander object dat je in de game plaatst.

### [Schakel realistische verlichting in](#schakel-realistische-verlichting-in)[](#schakel-realistische-verlichting-in)

De [LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  eigenschap bepaalt het gedrag van zowel globale als lokale verlichting in je game. Studio begint elke game met [Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting die een plattere uitstraling met zachtere lichten en schaduwen weergeeft. Om echter de omgeving te verbeteren en je lokale lichtbronnen in staat te stellen ook nauwkeurige schaduwen en verlichting te produceren, zoals het licht van het kampvuur, moet je [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting inschakelen.

Om dit concept te demonstreren, zie de volgende twee afbeeldingen van hetzelfde kampvuur met verschillende verlichtingsstijlen. De lokale verlichting van het kampvuur met [Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting produceert geen schaduwen op dezelfde manier als de globale verlichting van de zon, waardoor dit gebied van de omgeving ongelijkmatig verlicht is met onrealistische schaduwen. In tegenstelling hiermee interacteert de lokale verlichting van het kampvuur met [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichting met het brandhout, de stenen en de begroeiing rondom de omgeving, waardoor scherpe en realistische schaduwen voor de avond ontstaan.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/LightingStyle-Soft.jpg)[Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingsstijl

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/LightingStyle-Realistic.jpg)[Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  verlichtingsstijl

Om realistische verlichting in te schakelen:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, klik op de LightingStyle  dropdown, en selecteer Realistic .

### [Verhoog metalen reflecties](#verhoog-metalen-reflecties)[](#verhoog-metalen-reflecties)

Standaard gebruiken alle materialen fysiek-gebaseerde rendering (PBR) texturen die je in staat stellen realistische oppervlakken weer te geven in verschillende verlichtingsscenario's door meerdere afbeeldingsbestanden op een enkel object te gebruiken. Dit betekent dat wanneer je de ingebouwde materialen van Studio gebruikt, de metaliteit en ruwheid van een bepaald oppervlak al voor je zijn gedefinieerd, en de objecten met die materialen natuurlijk nauwkeuriger reageren op de verlichting in je omgeving met realistische reflecties. Je kunt dit effect verbeteren door de [Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  eigenschappen in te stellen op 1  om echt te profiteren van metalen reflecties van [Enum.LightingStyle.Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle#Realistic)  verlichting.

Deze stap is belangrijk omdat het ervoor zorgt dat alle PBR-texturen in je game, inclusief die van [MaterialVariants](/docs/nl-nl/reference/engine/classes/MaterialVariant)  of [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten, er op hun best uitzien en beter hun omgeving reflecteren. Bekijk bijvoorbeeld de volgende twee afbeeldingen van dezelfde pan en keukengerei nabij het kampvuur met verschillende waarden voor de [Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  eigenschappen. Wanneer je deze waarden aanpast, wordt het metaal duidelijker en reflecteert het de verlichting van zowel de globale als lokale lichtbronnen aanzienlijk meer dan voorheen.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/EnvironmentScale-0.jpg)[Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  = 0

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/EnvironmentScale-1.jpg)[Lighting.EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale)  en [Lighting.EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale)  = 1

Om metalen reflecties te verhogen:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, stel EnvironmentalDiffuseScale  en EnvironmentSpecularScale  in op 1 . Het metaal in de game wordt reflectiever.

### [Verander het tijdstip van de dag](#verander-het-tijdstip-van-de-dag)[](#verander-het-tijdstip-van-de-dag)

Nu je game gebruikmaakt van de [Enum.LightingStyle.Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle#Realistic)  verlichtingsstijl en materialen realistisch reageren op de lichtbronnen in je game, is het tijd om de zon naar een andere positie te verplaatsen volgens waar deze zou zijn in de echte wereld voor het tijdstip van de dag. De standaardpositie van de zon is hoog aan de hemel, wat rond het middaguur in de echte wereld emuleert, dus het is het beste om deze dichter bij de skyline te verplaatsen, net boven de bergen. Deze stap laat ook het licht naar het pad naar het kampvuur bewegen en zorgt voor een mooie gouden zon.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Default-Sun-Position.png) De standaardzon is hoog aan de hemel. Hoewel deze plaatsing geweldig is als het kampvuur rond het middaguur plaatsvond, is het niet realistisch voor de avond.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/New-Sun-Position.png) De nieuwe zonpositie is veel geschikter voor het tijdstip van de dag net voor zonsondergang.

Om het tijdstip van de dag te veranderen:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, stel ClockTime  in op 17 . De zon beweegt naar de geschatte positie die deze om 17:00 zou hebben.

### [Pas de kleur van omgevingslicht aan](#pas-de-kleur-van-omgevingslicht-aan)[](#pas-de-kleur-van-omgevingslicht-aan)

Er zijn twee [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  eigenschappen die de kleur van omgevingsverlichting regelen:

-

[Lighting.OutdoorAmbient](/docs/nl-nl/reference/engine/classes/Lighting#OutdoorAmbient)  regelt de omgevingsverlichting waar de lucht zichtbaar is.

-

[Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  regelt de omgevingsverlichting binnen ruimtes waar iets de lucht blokkeert, zoals binnenruimtes of onder boombedekking.

Standaard zijn deze eigenschappen ingesteld om grijze omgevingsverlichting te produceren, maar om de avondlucht aan te vullen, moet je deze waarden aanpassen om een realistische tint en helderheid in de donkerdere ruimtes van de game voor de avondtijd toe te voegen. Bijvoorbeeld, een avondlucht heeft veel meer paars dan grijs, dus het kiezen van een paarse tint voor omgevingsverlichting creëert een realistische omgeving.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Ambient-Default.png)[Lighting.OutdoorAmbient](/docs/nl-nl/reference/engine/classes/Lighting#OutdoorAmbient)  en [Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  = 70, 70, 70

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Ambient-New.png)[Lighting.OutdoorAmbient](/docs/nl-nl/reference/engine/classes/Lighting#OutdoorAmbient)  en [Lighting.Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient)  = 156, 136, 176

Om de kleur van omgevingslicht aan te passen:

1.

In het Explorer  venster, selecteer Lighting .

2.

In het Properties  venster, stel Outdoor Ambient  en Ambient  in op 156, 136, 176 . De omgevingsverlichting verandert naar een lichte paarse tint.

### [Kies een skybox](#kies-een-skybox)[](#kies-een-skybox)

Een skybox is een kubus die bestaat uit zes afzonderlijke afbeeldingen die de lucht van een game creëren, inclusief wat boven en onder de horizon is. Skyboxes kunnen een grote impact hebben op de uitstraling en het gevoel van wat er in je omgeving is, dus het is belangrijk om zorgvuldig te overwegen hoe je een skybox kunt kiezen die de visuele kwaliteit van je game verbetert. Bijvoorbeeld:

-

De onderste hemisfeer van een skybox moet vergelijkbaar zijn met de kleur van je algemene terrein. Dit zorgt ervoor dat de onderste hemisfeer nauwkeurig gerelateerd is aan het grondoppervlak, en dat de kleuren die van objecten reflecteren ongeveer overeenkomen met de skybox.

-

De onderste hemisfeer van een skybox moet donkerder zijn dan de bovenste hemisfeer omdat een donkerdere onderste hemisfeer de natuurlijke occlusie van licht van onder de grond nabootst, waardoor je verlichting meeslepender wordt.

-

Een skybox heeft geen wolken nodig, omdat je gemakkelijk [dynamische wolken](/docs/nl-nl/environment/clouds)  kunt toevoegen om hetzelfde effect te bereiken en je skybox aan te vullen.

Om deze concepten te illustreren, bekijk de volgende twee afbeeldingen om te zien hoe dezelfde chrome bol twee verschillende skyboxes reflecteert. De eerste skybox heeft hetzelfde niveau van helderheid voor zowel de bovenste als onderste hemisferen, waardoor het lijkt alsof de bol de wereld om zich heen niet goed reflecteert. In tegenstelling hiermee heeft de tweede skybox een donkerdere onderste hemisfeer dan zijn bovenste hemisfeer, wat een natuurlijker uiterlijk bereikt. Voor informatie over hoe je skyboxes kunt maken en aanpassen, zie [Skyboxes](/docs/nl-nl/environment/skybox) .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Bad-Skybox.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Good-Skybox.png)

### [Atmosferische effecten](#atmosferische-effecten)[](#atmosferische-effecten)

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service heeft een kind [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object met eigenschappen die je in staat stellen realistische omgevingen te simuleren door zonlicht op unieke manieren te verstrooien. Deze eigenschappen kunnen zeer nuttig zijn bij het creëren van een dikte in de lucht van de game, waardoor de omgeving een tastbaar gevoel van diepte krijgt. Het [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object haalt de meeste van zijn kleuren rechtstreeks uit de skybox, wat de eerdere beslissingen over je skybox zo belangrijk maakt.

#### [Verhoog de dichtheid van luchtdeeltjes](#verhoog-de-dichtheid-van-luchtdeeltjes)[](#verhoog-de-dichtheid-van-luchtdeeltjes)

De [Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  eigenschap regelt hoeveel deeltjes er in de lucht van je game bestaan. Wanneer je deze eigenschap verhoogt, belemmeren de extra deeltjes het zicht van de speler op objecten op de achtergrond. Bijvoorbeeld, wanneer [Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  0  is, zijn de achtergrondbomen, de zon en de skybox duidelijk zichtbaar, maar wanneer je deze eigenschap verhoogt naar 0.391 , beginnen de deeltjes het licht te verstrooien en verbergen ze de bomen.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Density-0.jpg)[Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  = 0

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Density-0.3.jpg)[Atmosphere.Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  = 0.391

Om de dichtheid van de luchtdeeltjes in de atmosfeer te verhogen:

1.

In het Explorer  venster, selecteer Atmosphere .

2.

In het Properties  venster, stel Density  in op 0.272 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Density-0.272.png)

#### [Voeg een nevel toe](#voeg-een-nevel-toe)[](#voeg-een-nevel-toe)

De [Atmosphere.Haze](/docs/nl-nl/reference/engine/classes/Atmosphere#Haze)  eigenschap regelt de algehele neveligheid van de atmosfeer om een zichtbaar effect te creëren zowel boven de horizon als ver in de verte vanaf de camera. Wanneer je deze eigenschap verhoogt, beïnvloedt het niet alleen de algehele omgeving, maar ook objecten die een bijzonder krachtige fresnel-effect hebben, zoals metalen objecten die de omgeving om hen heen reflecteren.

Om nevel aan de atmosfeer toe te voegen:

1.

In het Explorer  venster, selecteer Atmosphere .

2.

In het Properties  venster, stel Haze  in op 1 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Haze-1.png)

#### [Pas de kleur van de atmosfeer aan](#pas-de-kleur-van-de-atmosfeer-aan)[](#pas-de-kleur-van-de-atmosfeer-aan)

De [Atmosphere.Color](/docs/nl-nl/reference/engine/classes/Atmosphere#Color)  eigenschap stelt de tint van de atmosfeer in voor subtiele omgevingsstemingen en thema's, en het kan de nevel binnen je game echt verbeteren. Je kunt dit instellen op elke kleur die je wilt om bij je game te passen, maar het wordt aanbevolen om het in te stellen op een kleurwaarde die dicht bij het gemiddelde van de objecten in de omgeving ligt.

Om de kleur van de atmosfeer aan te passen:

1.

In het Explorer  venster, selecteer Atmosphere .

2.

In het Properties  venster, stel Color  in op 85, 78, 54 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Color-85-78-54.png)

## [Configureer lokale verlichting](#configureer-lokale-verlichting)[](#configureer-lokale-verlichting)

Lokale verlichting is de luminescentie van lokale [lichtbronnen](/docs/nl-nl/effects/light-sources)  in je game, zoals [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight) , en [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  objecten. De belangrijkste lokale lichtbron die je voor deze game kunt creëren is de gloed van het kampvuur, en door een paar van zijn standaard eigenschappen aan te passen, kun je aanzienlijk veranderen hoe deze lokale verlichting interactie heeft met de algehele omgeving en je globale verlichtingsconfiguratie aanvult.

### [Voeg een PointLight toe](#voeg-een-pointlight-toe)[](#voeg-een-pointlight-toe)

In tegenstelling tot [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight)  of [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight)  objecten die alleen licht vanuit één richting projecteren, stellen [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  objecten je in staat om omnidirectionele verlichting te projecteren. Dit betekent dat wanneer je een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  aan je kampvuur mesh toevoegt, het in alle richtingen naar buiten vanuit de bron projecteert, vergelijkbaar met een echt kampvuur, en het verlicht alle omringende objecten in schaduwen en stelt spelers in staat om de ruwheid van hun oppervlakken veel duidelijker te zien.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/No-PointLight.png) De scène zonder een lokale lichtbron

![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Yes-PointLight.jpg) Dezelfde scène met een lokale lichtbron

Om een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  aan het kampvuur toe te voegen:

1.

In het Explorer  venster, beweeg over FireLight  en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Selecteer PointLight  uit het menu. Het [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  object verschijnt als een kind van de kampvuur mesh.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/New-PointLight-Values.png)

### [Verhoog het bereik van de PointLight](#verhoog-het-bereik-van-de-pointlight)[](#verhoog-het-bereik-van-de-pointlight)

De standaard eigenschappen van de [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  zijn niet genoeg om de objecten rondom het kampvuur volledig te verlichten, dus je moet het bereik dat het licht kan bereiken verhogen. Omdat het vuur groot en helder is, moet het licht ver genoeg uitstralen om de nabijgelegen bomen, stenen en begroeiing te verlichten. Dit helpt ook om de ruimte warm en gezellig te laten aanvoelen, alsof de hitte van het vuur natuurlijk naar buiten uitbreidt.

Om het bereik van de [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  te verhogen:

1.

In het Explorer  venster, selecteer de PointLight  van het kampvuur.

2.

In het Properties  venster, stel Range  in op 48 . Het maximale verlichtingsbereik van het licht breidt zich uit.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Increasing-Range.png)

### [Schakel schaduwen in](#schakel-schaduwen-in)[](#schakel-schaduwen-in)

Hoewel het bereik van de verlichting realistisch is voor zijn grootte, is het onrealistisch dat de omringende bomen en stenen geen schaduwen werpen van het licht van het kampvuur. Soms is dit nuttig als je een paar puntlichten moet toevoegen om donkere ruimtes binnen je game te verlichten, maar wanneer je probeert de echte wereld na te bootsen, kun je de mogelijkheid van lokale verlichting inschakelen om schaduwen te werpen. Het is belangrijk op te merken dat extra schaduwen de prestaties van je game op low-end apparaten kunnen beïnvloeden, dus schakel schaduwen alleen in wanneer ze significant bijdragen aan de scène.

Om schaduwen van de lokale verlichting van het kampvuur in te schakelen:

1.

In het Explorer  venster, selecteer de PointLight  van het kampvuur.

2.

In het Properties  venster, schakel Shadows  in.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Enabling-Shadows.png)

### [Pas de helderheid en kleur van de verlichting aan](#pas-de-helderheid-en-kleur-van-de-verlichting-aan)[](#pas-de-helderheid-en-kleur-van-de-verlichting-aan)

Hoewel de lokale verlichting er al realistischer uitziet en aanvoelt, is deze nog steeds zwak in sterkte en te wit voor een warme gloed. Wanneer je de helderheid van het kampvuur verhoogt en een warmere tint toevoegt, brengt dit echt leven in het vuur en draagt het bij aan de gezelligheid van de scène.

Om de helderheid en kleur van de lokale verlichting van het kampvuur aan te passen:

1.

In het Explorer  venster, selecteer de PointLight  van het kampvuur.

2.

In het Properties  venster,

1.

Stel Brightness  in op 2 .

2.

Stel Color  in op 255, 179, 73 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/enhancing-outdoor-environments/Adjusting-Brightness-Color.png)

Je hebt nu een kampvuur scène die compleet en uitnodigend is voor spelers om te ontspannen. Met de vaardigheden in deze tutorial kun je de realistische verlichtingsstijl combineren met de beschikbare PBR-materialen om rijke en meeslepende games te creëren. Het kost alleen het instellen van de juiste eigenschappen en het nemen van beslissingen over deze functies die bij je omgeving passen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
