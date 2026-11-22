<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/economy-events -->

Economie evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)
4. /
5. Evenementtypes

# Economie evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Economie evenementen  stellen je in staat om de economie in je game bij te houden, zoals:

-

Top afvoeren  — Waar geven gebruikers in-game middelen aan uit?

-

Top bronnen  — Waar verdienen gebruikers middelen?

-

Gemiddelde portemonnee balans  — Hoeveel middelen houden gebruikers vast?

Zodra je game begint met het bijhouden van economie evenementen, ontgrendel je de Economie pagina van het Analytics dashboard op de Creator Hub.

## [Volg economie evenementen](#volg-economie-evenementen)[](#volg-economie-evenementen)

Om het Economie dashboard te ontgrendelen, moet je enkele economie evenementen in je game bijhouden. Begin met het identificeren waar gebruikers bronnen  (d.w.z. verdienen) en afvoeren  (d.w.z. uitgeven) middelen in je game. Deze worden in de code weergegeven door [Enum.AnalyticsEconomyFlowType](/docs/nl-nl/reference/engine/enums/AnalyticsEconomyFlowType) , dat ofwel Source  of Sink  kan zijn.

Evenementen kunnen alleen vanaf de server en in gepubliceerde games worden verzonden. Evenementen kunnen niet vanaf de client of Studio worden verzonden.

### [Transactietypen](#transactietypen)[](#transactietypen)

Elke bron- en afvoer gebeurtenis vereist een transactietype, gecodeerd met [Enum.AnalyticsEconomyTransactionType](/docs/nl-nl/reference/engine/enums/AnalyticsEconomyTransactionType) . Standaard zijn de opties:

-

IAP  (bron) - In-app aankopen waarbij Robux worden ingewisseld voor middelen, bijv. starterspakket.

-

TimedReward  (bron) - Verdien middelen volgens een schema, bijv. dagelijkse bonus.

-

Onboarding  (bron) - Krijg middelen bij het starten, bijv. welkomstbonus.

-

Shop  (bron of afvoer) - Ruil middelen in de winkel, bijv. aankoop van een item.

-

Gameplay  (bron of afvoer) - Verdien of geef middelen uit tijdens gameplay, bijv. voltooiing van een quest.

-

ContextualPurchase  (afvoer) - Geef middelen uit voor een contextspecifieke impuls, bijv. extra levens.

Deze types verschijnen op het dashboard. Het is een goed idee om te beginnen met de standaardcategorieën, maar als je dat nodig hebt, kun je ook je eigen transactietypen namen opgeven bij het loggen van een evenement.

### [Volg bronnen](#volg-bronnen)[](#volg-bronnen)

Het volgende voorbeeld gebruikt [AnalyticsService.LogEconomyEvent](/docs/nl-nl/reference/engine/classes/AnalyticsService#LogEconomyEvent)  om twee verschillende economie evenementen te loggen wanneer gebruikers de eerste en tweede niveaus in de game voltooien en enkele munten verdienen.

Een bron Gameplay evenement volgen

```

local AnalyticsService = game:GetService("AnalyticsService")

-- Na voltooiing van niveau 1

AnalyticsService:LogEconomyEvent(

    player,

    Enum.AnalyticsEconomyFlowType.Source,

    "Munten", -- Valuta naam

    50, -- Bedrag verdiend

    50, -- Huidige balans

    Enum.AnalyticsEconomyTransactionType.Gameplay.Name -- Transactietype

)

-- Na voltooiing van niveau 2

AnalyticsService:LogEconomyEvent(

    player,

    Enum.AnalyticsEconomyFlowType.Source,

    "Munten", -- Valuta naam

    50, -- Bedrag verdiend

    100, -- Balans na transactie

    Enum.AnalyticsEconomyTransactionType.Gameplay.Name -- Transactietype

)

```

Het volgende voorbeeld volgt een Robux aankoop van een 1000-munt bundel, met gebruik van het IAP  (in-app aankoop) transactietype, dit keer met een itemSKU , jouw unieke identificatie voor het item. itemSKU  is optioneel. Als je het niet opgeeft, toont het Economie dashboard N/B  in de bronnen en afvoeren tabel.

Een in-app aankoop volgen

```

local AnalyticsService = game:GetService("AnalyticsService")

AnalyticsService:LogEconomyEvent(

    player,

    Enum.AnalyticsEconomyFlowType.Source,

    "Munten",

    1000, -- Hoeveelheid munten in de bundel

    1020, -- Balans na transactie

    Enum.AnalyticsEconomyTransactionType.IAP.Name,

    "1000MuntBundel" -- Unieke item SKU identificatie van de munt bundel

)

```

In dit voorbeeld, als je veel munt bundels hebt, wil je misschien ook een [aangepast veld](/docs/nl-nl/production/analytics/custom-fields)  toevoegen om de munt bundel categorie te volgen ten opzichte van andere categorieën.

### [Volg afvoeren](#volg-afvoeren)[](#volg-afvoeren)

Het volgende voorbeeld logt een evenement wanneer gebruikers munten uitgeven om een DoubleJumpUpgrade  te kopen. Let op het Sink  flow type en het Shop  transactietype in vergelijking met de bron tracking voorbeelden.

Houd er rekening mee dat het bedrag (kosten) altijd een positief getal moet zijn, ongeacht of het evenement een bron of een afvoer is. De grafieken op het economie dashboard tonen automatisch afvoeren als negatieve getallen.

Een afvoer Gameplay evenement volgen

```

local AnalyticsService = game:GetService("AnalyticsService")

-- Na voltooiing van niveau 2

AnalyticsService:LogEconomyEvent(

    player,

    Enum.AnalyticsEconomyFlowType.Sink,

    "Munten", -- Valuta naam

    80, -- Kosten

    20, -- Balans na transactie

    Enum.AnalyticsEconomyTransactionType.Shop.Name,

    "DoubleJumpUpgrade" -- Item SKU

)

```

Voor informatie over de beperkingen van [AnalyticsService](/docs/nl-nl/reference/engine/classes/AnalyticsService) , zie [Beperkingen van evenement tracking](/docs/nl-nl/production/analytics/event-types#beperkingen-van-evenementtracking) .

## [Gebruik aangepaste velden](#gebruik-aangepaste-velden)[](#gebruik-aangepaste-velden)

Economie evenementen stellen je ook in staat om op aangepaste velden te splitsen om een gemakkelijkere vergelijking tussen segmenten te ondersteunen. Bijvoorbeeld, je kunt questnamen aan elk evenement geven om te zien welke gebruikers het meeste geld opleveren, of winkel locaties toevoegen om te zien of gebruikers de voorkeur geven aan de ene locatie boven de andere.

Je kunt splitsen op aangepaste velden door de splitsselector te gebruiken.

 ![Een dropdown die de drie aangepaste velden aangeeft die je kunt vergelijken, samen met standaard splitsingen zoals leeftijd, geslacht, besturingssysteem en meer.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Custom-Event-Breakdown.png)

Voor meer informatie, zie [Aangepaste velden](/docs/nl-nl/production/analytics/custom-fields) .

## [Gebruik economie om je game te laten groeien](#gebruik-economie-om-je-game-te-laten-groeien)[](#gebruik-economie-om-je-game-te-laten-groeien)

Het Economie dashboard bevat vijf grafieken om je te helpen actie te ondernemen om je inkomsten te laten groeien. Je kunt tot vijf valuta's van middelen toevoegen, en alle grafieken kunnen worden gefilterd op verschillende gebruikerscategorieën (geslacht, leeftijd, platform, enz.) en tot drie aangepaste velden die specifiek zijn voor jouw game.

-

Totaal bronnen en afvoeren per categorie  - Gebruik deze grafiek om je in-game economie in balans te houden. Totaal bronnen min totaal afvoeren zou dicht bij nul moeten zijn. Je kunt ook je top bronnen en afvoeren per categorie zien. Als je netto totaal groeit, overweeg dan om meer afvoeren toe te voegen.

 ![Totaal Bronnen en Afvoeren per Categorie grafiek gevuld met gegevens.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Total-Sources-Sinks.png)

-

Gemiddelde portemonnee balans  - Gebruik deze grafiek om te zien hoeveel middelen gebruikers, betalende en niet-betalende gebruikers gemiddeld vasthouden. Als de gemiddelde balans groeit, vooral voor betalende gebruikers, overweeg dan om nieuwe afvoeren toe te voegen.

 ![Gemiddelde Portemonnee Balans grafiek gevuld met gegevens.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Average-Wallet.png)

-

Top bronnen en afvoeren  - Gebruik dit om te identificeren waar je gebruikers hun middelen verdienen en uitgeven. Als gebruikers geen middelen verkrijgen uit in-app aankopen, overweeg dan om prijzen te verlagen of nieuwe opties aan te bieden. Als gebruikers niet genoeg van een bepaalde bron uitgeven, overweeg dan om nieuwe afvoeren voor die bron toe te voegen.

 ![Top Bronnen en Afvoeren grafiek gevuld met gegevens, open op het Bronnen tabblad.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Top-Sources-Sinks.png)

-

Alle bronnen en afvoeren  - Gebruik dit om een gecombineerde weergave per categorie te krijgen voor de geselecteerde datumbereik.

 ![Alle Bronnen en Afvoeren grafiek gevuld met gegevens.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/All-Sources-Sinks.png)

Voor meer tips over hoe je je in-ervaring economie in balans kunt houden, zie [Balans virtuele economieën](/docs/nl-nl/production/game-design/balance-virtual-economies) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
