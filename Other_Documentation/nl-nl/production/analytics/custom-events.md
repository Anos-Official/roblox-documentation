<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/custom-events -->

Aangepaste evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)
4. /
5. Evenementtypes

# Aangepaste evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Aangepaste evenementen  stellen je in staat om statistieken te volgen die specifiek zijn voor je game en die andere evenementen niet volledig vastleggen. Dit omvat:

-

Adoptie  — Hoeveel gebruikers klikken op een specifieke UI-component?

-

Gebruikersgedrag  — Wat is de meest gebruikte vaardigheid op elke kaart?

-

Kernloop  — Hoe verhouden kill/death-ratio's zich tussen verschillende wapens?

Zodra je game begint met het volgen van aangepaste evenementen, ontgrendel je de Verken -pagina van het Analytics-dashboard op de Creator Hub. Je kunt tot 100 aangepaste evenementen aan je game toevoegen.

## [Volg aangepaste evenementen](#volg-aangepaste-evenementen)[](#volg-aangepaste-evenementen)

Om de Verken -pagina te ontgrendelen, moet je eerst aangepaste evenementen in je game volgen. Begin met het identificeren van welke statistieken het belangrijkst zijn voor het monitoren en verbeteren van je game. Evenementen worden dagelijks geaggregeerd, dus het kan tot 24 uur duren voordat grafieken op de pagina worden weergegeven.

Evenementen kunnen alleen vanaf de server en in gepubliceerde games worden verzonden. Evenementen kunnen niet vanaf de client of Studio worden verzonden.

### [Tellers](#tellers)[](#tellers)

Tellers zijn eenmalige evenementen die zonder waarde worden vastgelegd. Je kunt tellers gebruiken om het aantal keren dat een specifiek evenement heeft plaatsgevonden bij te houden. Gebruik tellers voor enkele acties zoals het klikken op een knop, het starten van een quest of het gebruiken van een tool.

Evenementen zullen automatisch zowel het aantal evenementen als het aantal unieke gebruikers bijhouden. Voor waarde-aggregaties worden teller-evenementen behandeld als evenementen met een standaardwaarde van 1 . Dit betekent dat aggregaties zoals max/min/gemiddelde altijd gelijk zullen zijn aan 1 , en de som zal gelijk zijn aan het totale aantal evenementen.

```

local AnalyticsService = game:GetService("AnalyticsService")

AnalyticsService:LogCustomEvent(

    player,

    "MissionStarted" -- Evenementnaam

)

```

### [Evenementen met waarden](#evenementen-met-waarden)[](#evenementen-met-waarden)

Je kunt ook evenementen met waarden volgen voor statistieken die meer kwantitatieve gegevens vereisen in je game, zoals kill/death-ratio's of de hoeveelheid tijd die een gebruiker aan een missie besteedt. Het kan ook worden gebruikt als een manier om evenementen in batches te verzenden om onder de snelheidslimieten te blijven, d.w.z. 10 doden van zombies verzenden in plaats van 1 zombie tien keer te doden.

```

local AnalyticsService = game:GetService("AnalyticsService")

AnalyticsService:LogCustomEvent(

    player,

    "MissionCompletedDuration", -- Evenementnaam

    120 -- Evenementwaarde

)

```

## [Evenementaggregaties](#evenementaggregaties)[](#evenementaggregaties)

Alle evenementenstatistieken omvatten de volgende aggregaties en bieden ondersteuning voor slice-and-dicing:

-

Aantal

-

Aantal unieke gebruikers

-

Gemiddelde waarde

-

Som waarde

-

Min waarde

-

Max waarde

-

Gemiddelde waarde per gebruiker

Bekijk je evenementaggregaties op de Verken -pagina door het aggregatietype te selecteren.

 ![Een lijst van alle verschillende aggregatie-opties om je aangepaste evenementgegevens te filteren.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Custom-Event-Aggregations.png)

## [Gebruik aangepaste velden](#gebruik-aangepaste-velden)[](#gebruik-aangepaste-velden)

Aangepaste evenementen stellen je ook in staat om op aangepaste velden te splitsen om een gemakkelijkere vergelijking tussen segmenten te ondersteunen. Je kunt bijvoorbeeld questnamen aan elk evenement geven om te zien welke gebruikers het meest verkiezen, of de spelersklasse bijvoegen om te zien of een klasse een significant hogere kill/death-ratio heeft.

Je kunt splitsen op aangepaste velden door de splitsselector te gebruiken.

 ![Een dropdown die de drie aangepaste velden aangeeft waarmee je kunt vergelijken, samen met standaard splits zoals leeftijd, geslacht, besturingssysteem en meer.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Custom-Event-Breakdown.png)

Je moet aangepaste velden gebruiken wanneer mogelijk in plaats van evenementnamen, aangezien er een veel striktere cardinaliteitslimiet is op evenementnamen dan op aangepaste velden. Het gebruik van aangepaste velden stelt je ook in staat om visualisaties van evenementen over veldwaarden te zien.

Bijvoorbeeld, in plaats van PlantCabbage , PlantTurnip , PlantPepper  als drie afzonderlijke evenementen, zou je een enkel evenement kunnen hebben met de naam PlantSeed  en aangepaste veldwaarden Plant - Cabbage , Plant - Turnip , en Plant - Pepper . Op deze manier kun je zowel het totale aantal geplante zaden visualiseren als elke plant in dezelfde visualisatie vergelijken. Dit vermindert ook je evenementnaamcardinaliteit.

Voor meer informatie, zie [Aangepaste velden](/docs/nl-nl/production/analytics/custom-fields) .

## [Gebruik aangepaste evenementen om je game te laten groeien](#gebruik-aangepaste-evenementen-om-je-game-te-laten-groeien)[](#gebruik-aangepaste-evenementen-om-je-game-te-laten-groeien)

Aangepaste evenementen stellen je in staat om statistieken te volgen die het belangrijkst zijn, en bieden inzicht in hoe spelers interactie hebben met specifieke functies en inhoud. Gebruik deze evenementen om patronen in het gedrag van spelers te ontdekken en je kernloop van de game te optimaliseren.

In de referentiespel [Plant](/docs/nl-nl/resources/plant-reference-project)  wordt de kernloop met een HarvestPlant -evenement geactiveerd telkens wanneer een speler een rijpe plant oogst. Met behulp van aangepaste evenementen kun je het gemiddelde aantal geplante planten per speler per dag volgen, uitgesplitst naar planttype als een aangepast veld:

 ![Aangepaste evenementgrafiek voor het referentiespel Plant.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Custom-Event-Graph.png)

-

Probeer de diversiteit van inhoud binnen je game te verbeteren en spelers aan te moedigen om andere opties te verkennen als onderdeel van de [kernloop](/docs/nl-nl/production/game-design/core-loops)  om repetitiviteit te voorkomen.

-

Onderzoek waarom gebruikers aanzienlijk de voorkeur geven aan knolrapen boven andere planten, en of er onevenwichtigheden zijn die knolrapen veroorzaken (zoals met [economische evenementen](/docs/nl-nl/production/analytics/economy-events) ).

-

Voeg meer evenementtracking binnen je loop toe, zoals het planten van zaden, het water geven van planten en het naar de winkel gaan, om het gedrag van spelers en andere verbeterpunten beter te volgen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
