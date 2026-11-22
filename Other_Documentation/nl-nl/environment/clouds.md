<!-- Source: https://create.roblox.com/docs/nl-nl/environment/clouds -->

Dynamische wolken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Dynamische wolken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox's dynamische wolken  zijn realistische wolken die langzaam over de lucht drijven. Je kunt hun uiterlijk aanpassen via het [Clouds](/docs/nl-nl/reference/engine/classes/Clouds)  object om unieke sferen te creëren, zoals stormachtige luchten, prachtige zonsondergangen en buitenaardse werelden. Je kunt ook hun richting en snelheid aanpassen via [globale wind](/docs/nl-nl/environment/global-wind) .

## [Wolken inschakelen](#wolken-inschakelen)[](#wolken-inschakelen)

Je kunt dynamische wolken in een spel beheren via het [Clouds](/docs/nl-nl/reference/engine/classes/Clouds)  object. Hoewel je dit object overal kunt plaatsen voor organisatie- of replicatiedoeleinden, worden wolken alleen gerenderd als je het object onder de [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  klasse plaatst.

Om dynamische wolken in te schakelen:

1.

In het Explorer  venster, beweeg over Terrain  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu Clouds .

 ![Wolkenobject weergegeven in het Explorer-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Terrain-Clouds.png)

3.

Pas het uiterlijk van de wolken aan via de eigenschappen van het nieuwe object.

4.

Zet de wolken in beweging via [globale wind](/docs/nl-nl/environment/global-wind) .

## [Wolken eigenschappen](#wolken-eigenschappen)[](#wolken-eigenschappen)

Vanuit het [Clouds](/docs/nl-nl/reference/engine/classes/Clouds)  object onder [Terrain](/docs/nl-nl/reference/engine/classes/Terrain) , kun je het uiterlijk van de wolken aanpassen via het Eigenschappen  venster.

### [Bedekking](#bedekking)[](#bedekking)

De [Cover](/docs/nl-nl/reference/engine/classes/Clouds#Cover)  eigenschap controleert hoeveel de wolken zich uitstrekken over de algehele luchtlaag, van een waarde van 0 (spaarzame wolkenbedekking) tot 1 (volledige wolkenbedekking).

0.65 0.8

![Wolken met een Bedekking waarde van 0.65](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/clouds/Cover-A.jpg)

### [Dichtheid](#dichtheid)[](#dichtheid)

De [Density](/docs/nl-nl/reference/engine/classes/Clouds#Density)  eigenschap controleert de intensiteit van de deeltjes die elke wolk vormen, wat voornamelijk hun transparantie beïnvloedt. Bijvoorbeeld, lagere waarden produceren lichte, semi-transparante wolken, en hogere waarden produceren zware, donkere wolken met een stormachtige uitstraling.

0.1 0.3

![Wolken met een Dichtheid waarde van 0.05](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/clouds/Density-A.jpg)

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/Clouds#Color)  eigenschap controleert de materiaal kleur van wolkdeeltjes. Het is belangrijk op te merken dat verschillende [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  en [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  eigenschappen ook de kleur van de wolken beïnvloeden, dus als je specifieke sferen wilt simuleren, experimenteer dan met meerdere eigenschappen totdat je het gewenste effect hebt.

[255, 255, 255] [75, 50, 255]

![Wolken met een Kleur waarde van [255, 255, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/clouds/Color-A.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
