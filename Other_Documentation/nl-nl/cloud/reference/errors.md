<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/reference/errors -->

Fouten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Gemeenschappelijke componenten](/docs/nl-nl/cloud/reference/patterns)

# Fouten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende secties beschrijven de foutafhandeling voor Open Cloud API's. Vanwege implementatieverschillen tussen eindpunten en validatielagen, kunnen foutreacties aanzienlijk variëren in formaat.

## [Gatewayfouten](#gatewayfouten)[](#gatewayfouten)

Bij authenticatie- of routeringsproblemen kunnen zowel Open Cloud v1 als v2 API's fouten in dit formaat retourneren:

Voorbeeld gatewayfout

```

{

  "errors": [

    {

      "code": 0,

      "message": "Ongeldige API-sleutel"

    }

  ]

}

```

## [Open Cloud v2](#open-cloud-v2)[](#open-cloud-v2)

Open Cloud v2 API's volgen over het algemeen een consistent foutformaat wanneer de fout zich binnen het API-eindpunt zelf voordoet.

### [Standaard v2 foutformaat](#standaard-v2-foutformaat)[](#standaard-v2-foutformaat)

Open Cloud v2 API's retourneren fouten in dit formaat:

-

code  - Een string die het fouttype vertegenwoordigt (bijv. ONGELDIG_ARGUMENT , NIET_GEVONDEN ).

-

message  - Een menselijk leesbare boodschap die de fout uitlegt.

-

details  - Een optionele array met aanvullende foutspecifieke informatie.

Voorbeeld v2 fout

```

{

  "code": "ONGELDIG_ARGUMENT",

  "message": "Ongeldige gebruikers-ID in het verzoek."

}

```

Voorbeeld v2 fout met details

```

{

  "code": "ONGELDIG_ARGUMENT",

  "message": "De opgegeven filter is ongeldig.",

  "details": [

    {

      ...

    }

  ]

}

```

### [v2 foutcodes](#v2-foutcodes)[](#v2-foutcodes)

De volgende tabel beschrijft mogelijke waarden voor code  in v2 API-reacties.

| Code | | HTTP Status | | Beschrijving |
| --- | --- |
| ONGELDIG_ARGUMENT | | 400 | | Je hebt een ongeldig argument doorgegeven, zoals een ongeldig universeId . Je hebt mogelijk ook ontbrekende of ongeldige headers, zoals Content-Length  en Content-Type . |
| PERMISSIE_GEWEIGERD | | 403 | | Je verzoek heeft niet voldoende machtigingen of scopes om de bewerking uit te voeren. |
| NIET_GEVONDEN | | 404 | | Het systeem kan je opgegeven bronnen niet vinden, zoals een gegevensopslagvermelding. |
| AFGEROND | | 409 | | De bewerking is afgebroken. |
| HULPBRON_UITPUTTING | | 429 | | Je hebt niet genoeg quotum om de bewerking uit te voeren, meestal vanwege het verzenden van te veel verzoeken. |
| GEANNULEERD | | 499 | | Het systeem beëindigt het verzoek, meestal vanwege een time-out aan de clientzijde. |
| INTERN | | 500 | | Interne serverfout, meestal door een serverbug. |
| NIET_GEÏMPLENTEERD | | 501 | | De server implementeert de API-methode niet. |
| ONBESCHIKBAAR | | 503 | | Dienst is niet beschikbaar, meestal geretourneerd wanneer de server is uitgevallen. |

## [Open Cloud v1](#open-cloud-v1)[](#open-cloud-v1)

Open Cloud v1 API's hebben inconsistente foutreactieformaten. Het formaat hangt af van het specifieke eindpunt, het type fout en waar de fout zich in de aanvraagverwerkingspijplijn voordoet.

De meeste v1-eindpunten retourneren fouten in een van deze drie formaten:

Voorbeeld v1 fout met foutveld

```

{

  "error": "ONGELDIG_ARGUMENT",

  "message": "Ongeldige cursor.",

  "errorDetails": [

    {

      "errorDetailType": "DatastoreErrorInfo",

      "datastoreErrorCode": "OngeldigeCursor"

    }

  ]

}

```

Voorbeeld v1 fout met codeveld

```

{

  "code": "ONGELDIG_ARGUMENT",

  "message": "Ongeldige cursor."

}

```

Voorbeeld v1 gedetailleerde validatiefout

```

{

  "errors": {

    "assetId": ["De waarde 'a' is niet geldig."]

  },

  "type": "https://tools.ietf.org/html/rfc9110#section-15.5.1",

  "title": "Er zijn een of meer validatiefouten opgetreden.",

  "status": 400,

  "extensions": {

    "traceId": "00-427917f0fc3b8375ee33e4603a7f0693-f3f6ad560ff1a122-00"

  }

}

```

### [v1 foutcodes](#v1-foutcodes)[](#v1-foutcodes)

De volgende tabel beschrijft mogelijke waarden voor error  of code  in v1 API-reacties:

| HTTP Statuscode | | Fout | | Beschrijvingen |
| 400 | | ONGELDIG_ARGUMENT | | Je hebt een ongeldig argument doorgegeven, zoals een ongeldig universeId . Je hebt mogelijk ook ontbrekende of ongeldige headers, zoals Content-Length  en Content-Type . |
| 403 | | ONVOLDOENDE_SCOPE | | Het verzoek vereist hogere privileges dan die door het toegangstoken worden geboden. |
| 403 | | PERMISSIE_GEWEIGERD | | Je verzoek heeft niet voldoende scope om de bewerking uit te voeren. |
| 404 | | NIET_GEVONDEN | | Het systeem kan je opgegeven bronnen niet vinden, zoals een gegevensopslag. |
| 409 | | AFGEROND | | De bewerking is afgebroken vanwege een conflict, zoals het publiceren van een plaats die geen deel uitmaakt van het universum. |
| 429 | | HULPBRON_UITPUTTING | | Je hebt niet genoeg quotum om de bewerking uit te voeren, meestal vanwege het verzenden van te veel verzoeken. |
| 499 | | GEANNULEERD | | Het systeem beëindigt het verzoek, meestal vanwege een time-out aan de clientzijde. |
| 500 | | INTERN | | Interne serverfout. Meestal een serverbug. |
| 501 | | NIET_GEÏMPLENTEERD | | De server implementeert de API-methode niet. |
| 503 | | ONBESCHIKBAAR | | Dienst niet beschikbaar. Meestal is de server uitgevallen. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
