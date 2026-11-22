<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-6/coding-concept-algorithms -->

Coderen concept - algoritmen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Code ordenen](/docs/nl-nl/tutorials/fundamentals/coding-6/landing)

# Coderen concept - algoritmen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een algoritme  gebruikt een reeks stappen om een uitkomst te bepalen. Stappen kunnen een set van richtlijnen, vergelijkingen of zelfs een wiskundige formule zijn.

Je dagelijkse leven zit vol algoritmen die je gebruikt zonder erover na te denken. Ze helpen je bij het nemen van beslissingen, het creëren van dingen en het oplossen van problemen.

Voorbeelden uit het echte leven:

-

Controleren of je genoeg geld hebt om een snack te kopen.

-

Je aankleden in de ochtend.

-

Stickfiguren tekenen.

Voorbeelden van coderen:

-

Controleren of een vaardigheidsniveau hoog genoeg is om een item te gebruiken.

-

Een lijst met items in alfabetische volgorde sorteren.

-

Een speler die op lava staat verliest elke seconde 5 gezondheid. Als ze 0 bereiken, respawnen ze.

Voor een offline activiteit, probeer deze combinatie van kunst en informatica om een algoritme te creëren dat stickfiguren maakt.

-

Laat iedereen een stickfiguur tekenen.

-

Laat iedereen de stappen opschrijven die ze hebben genomen.

-

Koppel studenten en laat de ene student de tweede student aansturen met de richtlijnen die ze eerder hebben opgeschreven.

## [Maak algoritmen in code](#maak-algoritmen-in-code)[](#maak-algoritmen-in-code)

In het echte leven denken we meestal niet na over de algoritmen die we dagelijks gebruiken. Computers hebben echter algoritmen nodig die stap voor stap worden gecodeerd en gebruiken ten minste een van de drie methoden om een probleem op te lossen of een uitkomst te produceren.

| Methodologie | | Voorbeeld |
| --- | --- |
| Selectie  - Gebruikt voorwaardelijke uitspraken zoals if/then om een output te bepalen. | |

```

if time == 0 then

	stopLightColor = red

end

```

 |
|

Sequencing  - Een set van precieze stappen.

 | |

```

local function createBridge()

  create new block

  size block

  set color

  rotate

  set location

  parent to workspace

end

```

 |
|

Iteratie  - Herhaalt delen van de code indien nodig, zoals in for-lussen of vermenigvuldiging.

 | |

```

for countDown = 10, 1, -1 do

	time -= 1

	task.wait(1)

end

```

 |

## [Combineer algoritmen](#combineer-algoritmen)[](#combineer-algoritmen)

Net zoals grotere problemen kunnen worden opgesplitst in kleinere problemen, kunnen sommige algoritmen worden opgesplitst in een reeks kleinere algoritmen.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-algorithms/square-and-child-squares.png)

Denk aan je ochtendalgoritme om je aan te kleden. Als dat je hoofdalgoritme is, kan het één algoritme gebruiken voor het uitkiezen van je kleren, en een tweede algoritme voor het aantrekken van kleren.

Aankleden Pseudocode

```

-- Eerste algoritme voor het kiezen van kleren

local function pickClothes()

    pick top clothing

    pick bottom clothing

    pick Socks

    pick Shoes

end

-- Tweede algoritme voor het aantrekken van kleren

local function putOnClothes()

    put on top clothing

    put on bottom clothing

    put on socks

    put on shoes

end

-- Hoofdalgoritme, roept pickClothes() en putOnClothes() aan

local function getDressed()

    pickClothes()

    putOnClothes()

end

```

Voor een optionele uitdaging, probeer uit te zoeken welke aanvullende algoritmen pickClothes()  zou kunnen gebruiken?

-

Controleer het weer.

-

Controleer of de kleren schoon zijn.

-

Controleer of de kleren bij elkaar passen.

## [Samenvatting](#samenvatting)[](#samenvatting)

Algoritmen  zijn vooraf gedefinieerde stappen die een uitkomst bieden. In het dagelijks leven lossen algoritmen problemen op zoals je aankleden, naar je werk gaan of een taart bakken. In code lossen algoritmen problemen op zoals het beheren van websites, het omgaan met verkeersdrukte of het uitvoeren van spelmechanica. Om hun doel te bereiken, zullen algoritmen vaak andere algoritmen aanroepen.

Algoritmen gebruiken drie verschillende manieren om tot een conclusie te komen; selectie , iteratie  en sequencing . Selectie gebruikt voorwaardelijke uitspraken zoals if/then. Iteratie herhaalt delen van de code indien nodig. Sequencing gebruikt een reeks stappen om een resultaat te produceren.

[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-6/coding-concept-abstraction)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
