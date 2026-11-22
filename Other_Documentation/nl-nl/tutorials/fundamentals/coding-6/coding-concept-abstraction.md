<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-6/coding-concept-abstraction -->

Codering concept - abstractie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Code ordenen](/docs/nl-nl/tutorials/fundamentals/coding-6/landing)

# Codering concept - abstractie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Abstracties  in de informatica bieden een vereenvoudigde representatie van iets groters. Ze halen alleen de meest noodzakelijke informatie naar voren en verbergen de rest.

Functies  zijn herbruikbare abstracties. Wanneer ze worden aangeroepen, krijgen gebruikers de voordelen van de functie zonder de code voor de hele functie opnieuw te hoeven schrijven of zelfs maar te bekijken.

Een veelvoorkomend voorbeeld in programmeertalen is print() . Het grootste deel van de code is verborgen, zodat de programmeur zich kan concentreren op wat er moet worden afgedrukt en niet op de rest van de code.

## [Waarom abstracties creëren](#waarom-abstracties-creëren)[](#waarom-abstracties-creëren)

Abstracties houden programma's georganiseerd, verminderen complexiteit en maken de code gemakkelijker te updaten.

### [Voorbeeld van een winkel](#voorbeeld-van-een-winkel)[](#voorbeeld-van-een-winkel)

Stel dat je een in-game winkel hebt die slechts twee verschillende rugzakken verkoopt. De code voor de tweede rugzak is gekopieerd met kleine wijzigingen, zoals een andere naam en verkoopprijs.

![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/backpack-yellow.png) Geel Backpack - 10 Robux

![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/backpack-violet.png) Violet Backpack - 25 Robux

Hier is de code niet  geabstraheerd. Elke rugzak heeft een eigen script. Wat zou er gebeuren als je het volgende zou proberen toe te voegen?

-

20 extra rugzakken.

-

De mogelijkheid voor sommige tassen om meer items te bevatten dan andere tassen.

-

Een feestdaguitverkoop, 25% korting op alle rugzakken.

## [Ontwerp abstracties](#ontwerp-abstracties)[](#ontwerp-abstracties)

Het hebben van aparte rugzak-scripts maakt het toevoegen en bijwerken van rugzakken tijdrovend. Maak in plaats daarvan een abstractie zodat je niet op zoveel verschillende plaatsen updates hoeft te maken.

Om een abstractie te ontwerpen, beslis:

-

Welke delen van de code zullen worden hergebruikt.

-

Welke elementen elke keer anders zullen zijn.

De abstractie moet de informatie die verandert naar voren halen en de rest verbergen. In het voorbeeld van de rugzak zijn de verschillen de naam van de rugzak, de prijs en het aantal items dat het kan dragen. Een voorbeeld van een abstractie die je kunt ontwerpen is een functie die de naam van de rugzak accepteert en de prijs en capaciteit retourneert.

| ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/no-abstraction-backpacks.png) | | ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/abstraction-backpacks.png) |
| --- | --- |
|

Geen Abstractie

 | |

Abstractie

 |
|

Vier verschillende rugzakken, vier verschillende plaatsen om bij te werken.

 | |

Gebruik een functie om een tabel te doorzoeken naar unieke informatie. Slechts één plaats om bij te werken.

 |

Controleer op Begrip - Het Gebruik van Abstracties

 Welke andere game-mechanica kun je abstracties voor creëren?

Mogelijke Voorbeelden

-

Valstrikonderdelen - Toestaan van verschillende schadewaarden

-

Een functie maken voor het toekennen van willekeurige power-ups

-

Het creëren van karakterklassen

## [Samenvatting](#samenvatting)[](#samenvatting)

Abstracties  bieden een vereenvoudigde representatie van iets groters door details weg te laten. Wanneer je beslist of je een abstractie moet creëren, zoek dan naar code die vaak wordt hergebruikt maar met kleine wijzigingen elke keer. Bijvoorbeeld, een generiek item zoals een rugzak kan worden geabstraheerd naar een herbruikbare functie die prijs en capaciteit opzoekt.

Tijd nemen om code te plannen en te structureren met abstracties helpt programmeurs zich te concentreren op wat belangrijk is. Deze investering in tijd houdt programma's beter georganiseerd en maakt het gemakkelijker om ze bij te werken.

Galactic Speedway - Het instellingen-script heeft alleen de variabelen voor unieke kenmerken van de driftspeeder. De rest van de code is verborgen. Dit stelt studenten die nieuw zijn in coderen in staat om gefocust te blijven zonder de weg kwijt te raken.

Story Game Creator Challenge - Studenten roepen getInput()  aan vanuit het StoryMaker-module-script om vragen te creëren voor spelers om te beantwoorden. Studenten kunnen oefenen met het typen van strings en zoveel vragen stellen als ze willen, maar hoeven de code in de StoryMaker-module niet te zien.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-6/coding-concept-algorithms)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-6/create-with-module-scripts)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
