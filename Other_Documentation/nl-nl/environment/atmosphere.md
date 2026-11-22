<!-- Source: https://create.roblox.com/docs/nl-nl/environment/atmosphere -->

Atmosferische effecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Atmosferische effecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Atmosferische effecten  simuleren realistische omgevingen door zonlicht op unieke manieren te verstrooien op basis van eigenschappen die luchtdeeltjes controleren. Met het [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object kun je:

-

De deeltjesdichtheid controleren.

-

Een silhouet creëren of verre objecten met een offset mengen.

-

Een nevel of schittering simuleren.

-

De kleur of verval van een atmosfeer instellen.

 ![Atmosferische effecten gebruikt om een schitterende zonsondergangscène weer te geven](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Sahara-Sunset.jpg)

## [Atmosfeer eigenschappen](#atmosfeer-eigenschappen)[](#atmosfeer-eigenschappen)

Elke eigenschap van het [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object binnen de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service werkt samen om de algehele visie, thema's en sfeer van je spel te ondersteunen.

 ![Atmosfeerobject weergegeven in het Explorer-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Lighting-Atmosphere.png)

### [Dichtheid](#dichtheid)[](#dichtheid)

De [Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  eigenschap controleert hoeveel deeltjes er in de lucht van je spel aanwezig zijn; hoe hoger de dichtheid, hoe meer deeltjes, wat het zicht van een speler op objecten en terrein belemmert.

0 0.35

![Atmosfeer met Dichtheid waarde van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Density-A.jpg)

Dichtheid beïnvloedt alleen direct  objecten en terrein; echter, aangezien je een [skybox](/docs/nl-nl/environment/skybox)  door die objecten en terrein bekijkt, wordt de zichtbaarheid van een skybox ook beïnvloed.

### [Offset](#offset)[](#offset)

De [Offset](/docs/nl-nl/reference/engine/classes/Atmosphere#Offset)  eigenschap controleert hoe licht tussen de camera en de luchtachtergrond wordt overgedragen. Wanneer je deze waarde verhoogt, creëert het een silhouet van de horizon; wanneer je deze waarde verlaagt, mengt het verre objecten met de lucht voor een schijnbaar eindeloze en naadloze open wereld.

0 1

![Atmosfeer met Offset waarde van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Offset-A.jpg)

Balans de [Offset](/docs/nl-nl/reference/engine/classes/Atmosphere#Offset)  eigenschap zorgvuldig met de [Density](/docs/nl-nl/reference/engine/classes/Atmosphere#Density)  eigenschap. Een lage offsetwaarde kan ervoor zorgen dat de [skybox](/docs/nl-nl/environment/skybox)  door objecten en terrein zichtbaar is, en een hoge offsetwaarde kan ervoor zorgen dat verre objecten en terrein te veel detail hebben voor het gewenste lichteffect.

### [Nevel](#nevel)[](#nevel)

De [Haze](/docs/nl-nl/reference/engine/classes/Atmosphere#Haze)  eigenschap controleert de neveligheid van de atmosfeer om een zichtbaar effect te creëren zowel boven de horizon als ver in de verte vanaf de camera. Om omgevingssferen te creëren, zoals een rokerige tint voor een vervuilde alienplaneet of een mistige blauwe tint voor een somber spel, combineer je deze eigenschap met de [Kleur](#kleur)  eigenschap.

1 2.8

![Atmosfeer met Nevel waarde van 1](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Haze-A.jpg)

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/Atmosphere#Color)  eigenschap stelt de tint van de atmosfeer in voor subtiele omgevingssferen en thema's. Om het zichtbare effect van deze eigenschap uit te breiden, combineer je het met een hoge [Nevel](#nevel)  eigenschapswaarde.

[255, 255, 255] [255, 200, 255]

![Atmosfeer met Kleur waarde van [255, 255, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Color-A.jpg)

### [Schittering](#schittering)[](#schittering)

De [Glare](/docs/nl-nl/reference/engine/classes/Atmosphere#Glare)  eigenschap stelt een atmosferische schittering rond de zon in. Een hoge waarde resulteert in een verhoogd effect van zonlicht dat op de lucht en het spel wordt geworpen. Om het zichtbare effect van deze eigenschap te zien, moet je een schittering combineren met een [Nevel](#nevel)  waarde hoger dan 0.

0 1

![Atmosfeer met Schittering waarde van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Glare-A.jpg)

### [Verval](#verval)[](#verval)

De [Decay](/docs/nl-nl/reference/engine/classes/Atmosphere#Decay)  eigenschap stelt de tint van de atmosfeer weg van de zon in, die geleidelijk vervaagt van [Kleur](#kleur)  naar deze waarde. Om het zichtbare effect van deze eigenschap te zien, moet je een schittering combineren met [Nevel](#nevel)  en [Schittering](#schittering)  waarden hoger dan 0.

[255, 255, 255] [255, 90, 80]

![Atmosfeer met Verval waarde van [255, 255, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Decay-A.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
