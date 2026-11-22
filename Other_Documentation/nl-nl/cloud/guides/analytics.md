<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/analytics -->

Analyse | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Analytics](/docs/nl-nl/cloud/guides/analytics)

# Analyse

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Analytics Query API stelt je in staat om geaggregeerde ervaringsstatistieken over een datumbereik op te vragen. Deze API ondersteunt:

-

Het opvragen van dagelijkse actieve gebruikers (DAU), inkomsten, retentie en andere statistieken voor jouw ervaring.

-

Het filteren en groeperen van resultaten op dimensies zoals platform, land en leeftijdsgroep.

-

Het automatisch afhandelen van langzame queries als langlopende bewerkingen waarvoor je resultaten kunt opvragen.

Voordat je deze API gebruikt, moet je een [API-sleutel genereren](/docs/nl-nl/cloud/auth/api-keys)  voor jouw ervaring. Voeg bij het maken van de sleutel jouw ervaring toe aan Toegangsrechten  en geef toegang tot de universe.analytics:read  bewerking binnen het universe-analytics  systeem. Voeg de sleutel toe aan de x-api-key  aanvraagheader bij elke aanvraag.

Alle eindpunten gebruiken jouw universum-ID, die je kunt vinden op het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  door jouw ervaring te selecteren en de Universum-ID  van de overzichtspagina te kopiëren.

## [Vraag een statistiek op](#vraag-een-statistiek-op)[](#vraag-een-statistiek-op)

Om een statistiek voor jouw ervaring op te vragen:

1.

Kopieer de API-sleutel naar de x-api-key  aanvraagheader.

2.

Vervang ${UniverseId}  in de URL door de universum-ID van jouw ervaring.

3.

Stel metric  in op de statistiek die je wilt opvragen, zoals DailyActiveUsers .

4.

Stel granularity  in op een ondersteunde tijdsperiode, zoals OneDay . Zie [Granulariteitsopties](#granulariteitsopties) .

5.

Stel startTime  en endTime  in op het datumbereik dat je wilt, met behulp van RFC 3339 UTC-timestamps.

6.

Stuur de aanvraag.

Vraag dagelijkse actieve gebruikers op

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyActiveUsers",

    "granularity": "OneDay",

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

De meeste queries worden onmiddellijk voltooid en geven 200 OK  terug:

Antwoord (200 OK)

```

{

  "path": "v1/universes/1234567890/operations/metrics/abc123",

  "done": true,

  "metadata": {

    "createdTime": "2026-01-15T00:00:00Z"

  },

  "response": {

    "values": [

      {

        "breakdowns": [],

        "dataPoints": [

          { "time": "2026-01-01T00:00:00Z", "value": 10000 },

          { "time": "2026-01-02T00:00:00Z", "value": 10500 }

        ]

      }

    ]

  }

}

```

Voor grote datumbereiken kan de API 202 Accepted  retourneren met "done": false . Zie [Langlopende bewerkingen](#langlopende-bewerkingen) .

### [Aanvraaglichaam velden](#aanvraaglichaam-velden)[](#aanvraaglichaam-velden)

| Veld | | Type | | Vereist | | Beschrijving |
| --- | --- |
| metric | | string | | Ja | | De statistiek die je wilt opvragen. Bijvoorbeeld, DailyActiveUsers . Voor de volledige lijst, zie [Ondersteunde statistieken](/docs/nl-nl/cloud/guides/analytics/metrics) . |
| granularity | | string | | Ja | | De tijdsperiode voor elk datapunt. Zie [Granulariteitsopties](#granulariteitsopties) . |
| startTime | | string | | Ja | | Begin van het aanvraagvenster, als een RFC 3339 timestamp. Inclusief. Elke UTC-offset is geaccepteerd; resultaten worden altijd in UTC gegroepeerd. |
| endTime | | string | | Ja | | Einde van het aanvraagvenster, als een RFC 3339 timestamp. Exclusief. Bijvoorbeeld, "2026-02-01T00:00:00Z"  omvat gegevens tot en met 31 januari. |
| breakdown | | string[] | | Nee | | Dimensies om resultaten op te groeperen. Elke invoer is een enkele dimensienaam, zoals "Platform" . Laat weg voor geen opsplitsing. Zie [Gebruik opsplitsingen](#gebruik-opsplitsingen) . |
| filter | | object[] | | Nee | | Filters om resultaten te beperken tot specifieke dimensiewaarden. Elke invoer heeft dimension , values  en operation . Laat weg voor geen filtering. Zie [Filter resultaten](#filter-resultaten) . |
| limit | | integer | | Nee | | Maximale aantal opsplitsingsseries om terug te geven, gerangschikt op totale statistiekwaarde in aflopende volgorde. Alleen ondersteund wanneer granularity  "None"  is en breakdown  is ingesteld. Het weglaten van dit veld of het instellen op 0  past een standaardlimiet afhankelijk van de statistiek toe. |

De vroegste startTime  die je kunt gebruiken, hangt af van het type statistiek:

-

Standaardstatistieken  (betrokkenheid, monetisatie, acquisitie, retentie): tot 4 jaar geschiedenis.

-

Prestatiestatistieken  (crashpercentage, frame rate, enz.): tot 28 dagen geschiedenis.

Het opvragen van gegevens buiten de retentieperiode retourneert een 400  fout met code 2001 .

### [Langlopende bewerkingen](#langlopende-bewerkingen)[](#langlopende-bewerkingen)

De meeste queries worden onmiddellijk voltooid en geven 200 OK  terug met "done": true . Voor queries met grote datumbereiken of veel opsplitsingsseries retourneert de API 202 Accepted  met "done": false  en een path  om op te vragen.

In afwachting (202):

```

{

  "path": "path/to/poll",

  "done": false,

  "metadata": {

    "createdTime": "2026-01-15T00:00:00Z"

  }

}

```

Wanneer done  false  is, stuur je een GET-aanvraag naar https://apis.roblox.com/analytics-query-api/{path}  — vervang {path}  door de path  waarde uit de reactie — met dezelfde x-api-key  header. Herhaal totdat done  true  is.

Voltooid (200):

```

{

  "path": "path/to/poll",

  "done": true,

  "metadata": {

    "createdTime": "2026-01-15T00:00:00Z"

  },

  "response": {

    "values": [

      {

        "breakdowns": [],

        "dataPoints": [

          {

            "time": "2026-01-01T00:00:00Z",

            "value": 10000

          }

        ]

      }

    ]

  }

}

```

Een lege breakdowns  array geeft aan dat er geen opsplitsing is aangevraagd. Wanneer een opsplitsing wordt gebruikt, komt elke invoer in response.values  overeen met één dimensiewaarde. Zie [Gebruik opsplitsingen](#gebruik-opsplitsingen) .

Wanneer de bewerking mislukt, bevat het lichaam error  in plaats van response :

```

{

  "path": "path/to/poll",

  "done": true,

  "metadata": {

    "createdTime": "2026-01-15T00:00:00Z"

  },

  "error": {

    "code": 2001,

    "message": "De gevraagde granulariteit wordt niet ondersteund voor deze statistiek."

  }

}

```

| Veld | | Type | | Beschrijving |
| path | | string | | Het bewerkingspad, dat overeenkomt met de waarde die in de initiële reactie is geretourneerd. |
| done | | boolean | | Altijd true  wanneer er een fout aanwezig is. |
| metadata.createdTime | | string | | RFC 3339 timestamp van wanneer de bewerking is aangemaakt. |
| error.code | | integer | | Numerieke foutcode. Zie [Veelvoorkomende fouten](#veelvoorkomende-fouten) . |
| error.message | | string | | Menselijk leesbare beschrijving van de fout. |

Elke invoer in response.values  vertegenwoordigt één serie, één per dimensiewaarde wanneer een opsplitsing wordt gebruikt, of een enkele invoer met breakdowns: []  wanneer er geen opsplitsing is aangevraagd. Elk datapunt in dataPoints  heeft:

| Veld | | Beschrijving |
| time | | UTC-timestamp voor het begin van de tijdsperiode. |
| value | | De numerieke statistiekwaarde. |
| stringValues | | Tekstwaarden voor het datapunt, als een array van strings. Alleen aanwezig voor tekstgebaseerde statistieken. Zie [Tekstgebaseerde statistieken](#tekstgebaseerde-statistieken)  hieronder. |
| status | | Statusindicator voor het datapunt. Weggelaten wanneer er geen status van toepassing is voor de serie. Zie [Status van datapunt](#status-van-datapunt)  hieronder. |

### [Tekstgebaseerde statistieken](#tekstgebaseerde-statistieken)[](#tekstgebaseerde-statistieken)

De meeste statistieken zijn numeriek en rapporteren hun resultaat in value . Een paar statistieken beschrijven in plaats daarvan elk datapunt met tekst in plaats van een nummer. Voor deze statistieken worden de gegevens geretourneerd in een stringValues  array en is value  niet betekenisvol. Het stringValues  veld wordt volledig weggelaten voor numerieke statistieken.

Bijvoorbeeld, ThumbnailWinningSegments  rapporteert de winnende thumbnailsegmenten voor elke tijdsperiode als een lijst van strings:

```

{

  "time": "2026-01-01T00:00:00Z",

  "value": 0,

  "stringValues": ["TopEngagement", "HighCTR"]

}

```

### [Status van datapunt](#status-van-datapunt)[](#status-van-datapunt)

| Status | | Beschrijving | | Voorbeeld |
| Valid | | Het datapunt is compleet en dekt de volledige tijdsperiode. | | Voltooide Creator Rewards uitbetaling. |
| Projected | | De waarde is een schatting en kan veranderen. | | Geschatte Creator Rewards uitbetaling voor een periode die nog niet is afgerond. |
| NotStatisticallySignificant | | De steekproefgrootte is onvoldoende om een betrouwbare waarde te produceren. | | Crashpercentage voor een klein land waar een ruisachtige waarde verward kan worden met een echte regressie. |

## [Granulariteitsopties](#granulariteitsopties)[](#granulariteitsopties)

Het veld granularity  bepaalt de grootte van elke tijdsperiode in de reactie. Periodegrenzen zijn uitgelijnd op UTC. Bijvoorbeeld, OneDay  perioden lopen van middernacht UTC tot middernacht UTC, zodat elke UTC-offset in startTime  of endTime  naar UTC wordt genormaliseerd voordat de groepering plaatsvindt.

Niet elke statistiek ondersteunt elke granulariteit. Zie [Ondersteunde statistieken](/docs/nl-nl/cloud/guides/analytics/metrics)  voor details.

| Granulariteit | | Beschrijving | | Opmerkingen |
| OneMinute | | 1-minuut perioden | | Alleen prestatiestatistieken. |
| HalfHour | | 30-minuten perioden | | Alleen prestatiestatistieken. |
| OneHour | | 1-uur perioden | | Prestatiestatistieken, plus enkele monetisatie- en aanbevolen evenementenstatistieken. |
| OneDay | | 1-dag perioden | | Ondersteund door alle statistieken. |
| OneWeek | | 1-week perioden | | De meeste betrokkenheid, monetisatie en acquisitiestatistieken. |
| OneMonth | | 1-maand perioden | | De meeste betrokkenheid, monetisatie en acquisitiestatistieken. |
| None | | Enkel datapunt voor het gehele bereik | | De meeste betrokkenheid, monetisatie en acquisitiestatistieken. |

Datumbereiken langer dan twee jaar ondersteunen alleen OneWeek , OneMonth  of None .

## [Gebruik opsplitsingen](#gebruik-opsplitsingen)[](#gebruik-opsplitsingen)

Niet elke statistiek ondersteunt elke opsplitsing. Zie [Ondersteunde statistieken](/docs/nl-nl/cloud/guides/analytics/metrics)  voor welke opsplitsingen beschikbaar zijn voor elke statistiek.

Opsplitsingen groeperen statistiekresultaten op een dimensie, waarbij één serie per unieke dimensiewaarde wordt geretourneerd. Voeg een breakdown  array met een of meer dimensienamen toe aan jouw aanvraag.

Vraag inkomsten op opgesplitst per platform

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyRevenue",

    "granularity": "OneDay",

    "breakdown": ["Platform"],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

Elke invoer in response.values  bevat een breakdowns  array die de dimensiewaarde voor die serie identificeert:

```

{

  "response": {

    "values": [

      {

        "breakdowns": [{ "dimension": "Platform", "value": "Computer" }],

        "dataPoints": [{ "time": "2026-01-01T00:00:00Z", "value": 8200 }]

      },

      {

        "breakdowns": [{ "dimension": "Platform", "value": "Phone" }],

        "dataPoints": [{ "time": "2026-01-01T00:00:00Z", "value": 3400 }]

      }

    ]

  }

}

```

Elk object in breakdowns  heeft:

| Veld | | Beschrijving |
| dimension | | De dimensienaam, die overeenkomt met de invoer in het breakdown  aanvraagveld. |
| value | | De ruwe dimensiewaarde. Gebruik dit bij het construeren van filter  queries. |
| displayValue | | Een menselijk leesbaar label voor de dimensiewaarde. Weggelaten wanneer er geen weergavelabel bestaat. Kan verschillen van value  voor dimensies zoals product-ID's of funnelstapnamen. |

## [Filter resultaten](#filter-resultaten)[](#filter-resultaten)

Filters beperken de queryresultaten tot specifieke dimensiewaarden. Voeg een filter  array toe aan jouw aanvraag, waarbij elke invoer een dimension , de values  om op te matchen, en de operation  die moet worden toegepast specificeert.

Vraag DAU voor mobiele apparaten alleen op

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyActiveUsers",

    "granularity": "OneDay",

    "filter": [

        {

            "dimension": "Platform",

            "values": ["Phone", "Tablet"],

            "operation": "In"

        }

    ],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

### [Filterbewerkingen](#filterbewerkingen)[](#filterbewerkingen)

| Bewerking | | Beschrijving |
| In | | Inclusief resultaten waarbij de dimensiewaarde in de opgegeven set zit. |
| NotIn | | Exclusief resultaten waarbij de dimensiewaarde in de opgegeven set zit. |
| GreaterThan | | Inclusief resultaten waarbij de numerieke dimensiewaarde groter is dan de opgegeven waarde. |
| GreaterThanOrEqual | | Inclusief resultaten waarbij de numerieke dimensiewaarde groter dan of gelijk aan de opgegeven waarde is. |
| LessThan | | Inclusief resultaten waarbij de numerieke dimensiewaarde kleiner is dan de opgegeven waarde. |
| LessThanOrEqual | | Inclusief resultaten waarbij de numerieke dimensiewaarde kleiner dan of gelijk aan de opgegeven waarde is. |
| Match | | Inclusief resultaten waarbij de dimensiewaarde overeenkomt met het opgegeven tekenreeks patroon. |

Je kunt filters combineren met opsplitsingen in dezelfde aanvraag.

## [Ontdek dimensiewaarden](#ontdek-dimensiewaarden)[](#ontdek-dimensiewaarden)

Het eindpunt voor dimensiewaarden geeft de beschikbare waarden voor een of meer dimensies van een statistiek over een datumbereik weer, zonder de statistiek zelf te berekenen. Gebruik het om geldige waarden voor filter  en breakdown  queries te ontdekken — bijvoorbeeld, landen, product-ID's of funnelstap-ID's.

Om dimensiewaarden voor jouw ervaring op te vragen:

1.

Kopieer de API-sleutel naar de x-api-key  aanvraagheader.

2.

Vervang ${UniverseId}  in de URL door de universum-ID van jouw ervaring.

3.

Stel metric  in op de statistiek die context biedt voor de dimensies.

4.

Stel dimensions  in op de dimensienamen waarvoor je waarden wilt.

5.

Stel startTime  en endTime  in op het datumbereik dat je wilt, met behulp van RFC 3339 UTC-timestamps.

6.

Stuur de aanvraag.

Ontdek landwaarden voor DAU

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/dimension-values' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyActiveUsers",

    "dimensions": ["Country"],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

### [Aanvraaglichaam velden](#aanvraaglichaam-velden-1)[](#aanvraaglichaam-velden-1)

| Veld | | Type | | Vereist | | Beschrijving |
| metric | | string | | Ja | | De statistiek waarvan de dimensies moeten worden opgelost. Biedt namespace-context voor dimensie-opzoeking. |
| dimensions | | string[] | | Ja | | De dimensienamen waarvoor je waarden wilt ophalen. Elke invoer is een enkele dimensienaam, zoals "Country" . |
| startTime | | string | | Ja | | Begin van het aanvraagvenster, als een RFC 3339 timestamp. Inclusief. Elke UTC-offset is geaccepteerd; resultaten worden altijd in UTC gegroepeerd. |
| endTime | | string | | Ja | | Einde van het aanvraagvenster, als een RFC 3339 timestamp. Exclusief. Bijvoorbeeld, "2026-02-01T00:00:00Z"  omvat gegevens tot en met 31 januari. |
| filter | | object[] | | Nee | | Filters om resultaten te beperken tot specifieke dimensiewaarden. Elke invoer heeft dimension , values  en operation . Laat weg voor geen filtering. Zie [Filter resultaten](#filter-resultaten) . |
| granularity | | string | | Nee | | De tijdsperiode. In tegenstelling tot het statistieken-eindpunt is dit veld optioneel. Zie [Granulariteitsopties](#granulariteitsopties) . |
| limit | | integer | | Nee | | Maximale aantal waarden om per dimensie terug te geven, gerangschikt op totale statistiekwaarde in aflopende volgorde. Alleen ondersteund wanneer granularity  weggelaten of "None"  is. Het weglaten van dit veld of het instellen op 0  past een standaardlimiet afhankelijk van de statistiek toe. |

De meeste queries worden onmiddellijk voltooid en geven 200 OK  terug met "done": true . Voor queries met grote datumbereiken retourneert de API 202 Accepted  met "done": false  en een path  om op te vragen. Zie [Langlopende bewerkingen](#langlopende-bewerkingen)  voor de pollingstroom. Gebruik bij het polleren de path  waarde uit de reactie — deze wijst naar v1/universes/{universeId}/operations/dimension-values/{operationId} , distinct van het metrics poll pad.

Voltooid (200):

```

{

  "path": "path/to/poll",

  "done": true,

  "metadata": {

    "createdTime": "2026-01-15T00:00:00Z"

  },

  "response": {

    "values": [

      {

        "dimension": "Country",

        "values": [{ "value": "US" }, { "value": "GB" }]

      }

    ]

  }

}

```

Elke invoer in response.values  vertegenwoordigt één aangevraagde dimensie. Elk object in values  heeft:

| Veld | | Beschrijving |
| value | | De ruwe dimensiewaarde. Gebruik dit bij het construeren van filter  queries. |
| displayValue | | Een menselijk leesbaar label voor de dimensiewaarde. Alleen aanwezig voor ID-achtige dimensies zoals product-ID's. Weggelaten voor de meeste dimensies, inclusief Country . Kan verschillen van value  voor dimensies zoals product-ID's of funnelstapnamen. |

Fouten gebruiken dezelfde done: true  en error  envelop als het statistieken-eindpunt. Een niet-ondersteunde dimensie voor de opgegeven statistiek retourneert 400  met code 2001 . Zie [Veelvoorkomende fouten](#veelvoorkomende-fouten) .

## [Veelvoorkomende queries](#veelvoorkomende-queries)[](#veelvoorkomende-queries)

De volgende voorbeelden tonen veelvoorkomende queries, inclusief statistieken die beschikbaar zijn op de analytics-pagina's van het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

### [Inkomsten](#inkomsten)[](#inkomsten)

Vraag dagelijkse inkomsten in Robux op

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyRevenue",

    "granularity": "OneDay",

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

### [D1 retentie](#d1-retentie)[](#d1-retentie)

Vraag D1 retentie op

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "ForwardD1Retention",

    "granularity": "OneDay",

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

### [Nieuwe gebruikers vs. terugkerende gebruikers](#nieuwe-gebruikers-vs-terugkerende-gebruikers)[](#nieuwe-gebruikers-vs-terugkerende-gebruikers)

Vraag DAU op opgesplitst in nieuwe vs. terugkerende

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyActiveUsers",

    "granularity": "OneDay",

    "breakdown": ["IsNewUser"],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

### [Wekelijkse aggregatie](#wekelijkse-aggregatie)[](#wekelijkse-aggregatie)

Gebruik een grovere granulariteit voor een langere kijk met minder datapoints. Bij OneWeek  granulariteit telt elke periode unieke gebruikers over de volledige zeven dagen — niet een som van dagelijkse waarden.

Vraag DAU op met wekelijkse granulariteit

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyActiveUsers",

    "granularity": "OneWeek",

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-04-01T00:00:00Z"

}'

```

### [Top-N opsplitsing](#top-n-opsplitsing)[](#top-n-opsplitsing)

Om te rangschikken op één statistiek en een andere voor dezelfde set waarden weer te geven, gebruik je twee aanvragen. Bijvoorbeeld, om de conversie van betalende gebruikers voor de top 5 landen op DAU te zien:

Stap 1:  Ontdek de top N dimensiewaarden. Gebruik granularity: "None"  voor een enkele geaggregeerde resultaat en limit  om het aantal geretourneerde series te beperken:

Ontdek de top 5 landen op basis van DAU

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "DailyActiveUsers",

    "granularity": "None",

    "breakdown": ["Country"],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z",

    "limit": 5

}'

```

Stap 2:  Vraag de weergavestatistiek op, gefilterd op de waarden die in stap 1 zijn geretourneerd:

Conversie van betalende gebruikers voor de top 5 landen

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "PayingUsersCVR",

    "granularity": "OneDay",

    "breakdown": ["Country"],

    "filter": [

        {

            "dimension": "Country",

            "values": ["US", "GB", "PH", "VN", "DE"],

            "operation": "In"

        }

    ],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

### [Funnelstappen](#funnelstappen)[](#funnelstappen)

Funnels tonen hoe gebruikers vorderen door een gedefinieerde reeks stappen in jouw ervaring. Het opvragen van funnelstatistieken vereist twee aanvragen, omdat de stap-ID's dynamisch zijn.

Stap 1:  Ontdek de funnelstappen. Een funnelstap verschijnt alleen in resultaten voor dagen waarop ten minste één gebruiker die stap heeft bereikt. Het gebruik van een langere terugblik (90 dagen is een veilige standaard) zorgt ervoor dat infrequent bereikte stappen nog steeds in de ontdekkingsreactie verschijnen. Gebruik granularity: "None"  om een enkele geaggregeerde resultaat per stap te krijgen:

Ontdek funnelstappen voor de Levels funnel

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "FunnelUserTotalCount",

    "granularity": "None",

    "breakdown": ["FunnelStep"],

    "filter": [

        {

            "dimension": "FunnelName",

            "values": ["Levels"],

            "operation": "In"

        }

    ],

    "startTime": "2025-11-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

Stap 2:  Vraag de funnelstatistiek voor elke stap op, gefilterd op de stap-ID's die in stap 1 zijn geretourneerd:

Verliespercentage per stap voor de Levels funnel

```

curl --location 'https://apis.roblox.com/analytics-query-api/v1/universes/${UniverseId}/metrics' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

    "metric": "FunnelUserChurnRate",

    "granularity": "None",

    "breakdown": ["FunnelStep"],

    "filter": [

        {

            "dimension": "FunnelStep",

            "values": ["1", "2", "3", "4", "5"],

            "operation": "In"

        },

        {

            "dimension": "FunnelName",

            "values": ["Levels"],

            "operation": "In"

        }

    ],

    "startTime": "2026-01-01T00:00:00Z",

    "endTime": "2026-02-01T00:00:00Z"

}'

```

## [Veelvoorkomende fouten](#veelvoorkomende-fouten)[](#veelvoorkomende-fouten)

De meeste fouten worden geretourneerd als query-bewerkingsfouten: het antwoordlichaam bevat "done": true  en een error  object met een numerieke code  en message  string. Authenticatie- en resourcefouten (401, 404) zijn gewone HTTP-antwoorden zonder lichaam envelop, wat de reden is dat de tabel hieronder —  voor hun foutcodes toont.

| Status | | Code | | Oorzaak | | Oplossing |
| 400 | | 2001 | | Een vereist veld ontbreekt of een veldwaarde is ongeldig (bijvoorbeeld, een niet-herkende metric  of granularity ). | | Controleer de [Aanvraaglichaam velden](#aanvraaglichaam-velden)  tabel en verifieer of alle waarden correct zijn gespeld. |
| 400 | | 2001 | | De gevraagde granulariteit wordt niet ondersteund voor de opgegeven statistiek of datumbereik. | | Zie [Granulariteitsopties](#granulariteitsopties) . Voor datumbereiken van meer dan twee jaar, gebruik OneWeek , OneMonth , of None . |
| 400 | | 2001 | | Een dimensie in filter  of breakdown  wordt niet ondersteund voor de opgegeven statistiek. | | Zie [Ondersteunde statistieken](/docs/nl-nl/cloud/guides/analytics/metrics) . |
| 400 | | 2001 | | De startTime  overschrijdt de gegevensretentieperiode voor de statistiek. | | Standaardstatistieken behouden gegevens tot vier jaar. Prestatiestatistieken behouden gegevens voor 28 dagen. |
| 401 | | — | | De x-api-key  header ontbreekt, is ongeldig of ingetrokken, of de sleutel heeft geen universum analytics toestemming voor dit universum. | | Verifieer de sleutelwaarde en bevestig dat de API-sleutel de juiste machtigingen heeft op het [Creator Dashboard](https://create.roblox.com/dashboard/credentials) . |
| 404 | | — | | De bewerkings-ID bestaat niet. | | Bevestig de bewerkings-ID die in de initiële reactie is geretourneerd, en verifieer of de universum-ID correct is. |
| 429 | | 3000 | | De query overschreed het gegevenspuntbudget. | | Verminder het datumbereik, gebruik een grovere granulariteit, of verminder het aantal opsplitsingsseries met behulp van limit . |
| 500 | | 2000 | | Er is een onverwachte serverfout opgetreden. | | Probeer de aanvraag opnieuw. Als de fout aanhoudt, maak dan een nieuwe DevForum-post. |
| 503 | | 2002 | | Er is een tijdelijke fout opgetreden. | | Probeer de aanvraag opnieuw na een korte vertraging. |
| 504 | | 1000 | | De query is verlopen na het maximale aantal herhalingen. | | Probeer een korter datumbereik, minder opsplitsingen, of een grovere granulariteit. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
