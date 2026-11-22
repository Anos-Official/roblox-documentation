<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/custom-fields -->

Aangepaste velden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)
4. /
5. Evenementtypes

# Aangepaste velden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt tot drie aangepaste velden  gebruiken om je [economie](/docs/nl-nl/production/analytics/economy-events) , [trechter](/docs/nl-nl/production/analytics/funnel-events)  en [aangepaste](/docs/nl-nl/production/analytics/custom-events)  evenementen te filteren op unieke dimensies die specifiek zijn voor jouw game. Enkele voorbeelden zijn:

-

Niveaus — 1, 2, 3, . . .

-

Speler klasse — Krijger, Magiër, Boogschutter

-

Wapen type — SMG, Pistool, Raketwerper

De customFields  parameter is een woordenboek waarmee je tot drie aangepaste waarden kunt verzenden met behulp van de gegeven [Enum.AnalyticsCustomFieldKeys](/docs/nl-nl/reference/engine/enums/AnalyticsCustomFieldKeys)  als sleutels door ze te benaderen als Enum.AnalyticsCustomFieldKeys.CustomField{01, 02, 03}.Name . Alles behalve CustomField01.Name , CustomField02.Name  en CustomField03.Name  wordt genegeerd. Je kunt tot 8.000 unieke combinaties van waarden hebben over de drie aangepaste velden.

De waarden  die aan aangepaste velden zijn toegewezen, moeten strings  zijn. Als je een ander gegevenstype zoals een boolean of nummer wilt loggen, geef het dan door in stringformaat.

Als voorbeeld van een fantasiegerelateerde game kun je een economie-evenement bijhouden met betrekking tot het type uitrusting, de speler klasse en het niveau met het volgende:

Tracking Custom Fields

```

local AnalyticsService = game:GetService("AnalyticsService")

AnalyticsService:LogEconomyEvent(

    player,

    Enum.AnalyticsEconomyFlowType.Sink,

    "Muntstukken", -- Valuta naam

    80, -- Kosten

    20, -- Saldo na transactie

    Enum.AnalyticsEconomyTransactionType.Shop.Name,

    "Obsidiaans Zwaard", -- Item SKU

    {

        [Enum.AnalyticsCustomFieldKeys.CustomField01.Name] = "Categorie - Wapen",

        [Enum.AnalyticsCustomFieldKeys.CustomField02.Name] = "Klasse - Krijger",

        [Enum.AnalyticsCustomFieldKeys.CustomField03.Name] = "Niveau - 10",

    } -- Aangepast veld woordenboek

)

```

Het opnemen van de dimensienaam in de waarde is niet vereist, maar kan je helpen om de context later te onthouden bij het bekijken van je grafieken. Andere sleutels in de customFields  tabel worden genegeerd.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
