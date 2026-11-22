<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/reference/patterns -->

Patronen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Gemeenschappelijke componenten](/docs/nl-nl/cloud/reference/patterns)

# Patronen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze pagina behandelt veelvoorkomende patronen met de Open Cloud API's, met name rond het maken van verzoeken en het afhandelen van antwoorden.

## [Paden](#paden)[](#paden)

Om een verzoek te doen aan de Open Cloud API's, moet je eerst een URL vormen. Deze URL is een combinatie van de basis-URL (bijv. https://apis.roblox.com ), het Open Cloud API-pad (bijvoorbeeld, /cloud/v2/universes/{universe_id}/places/{place_id}/user-restrictions ), en eventuele queryparameters (bijvoorbeeld, ?maxPageSize=25 ). Een volledige verzoek-URL kan er als volgt uitzien:

```

https://apis.roblox.com/cloud/v2/users/4687549151/inventory-items?maxPageSize=100

```

Veel paden, waaronder het bovenstaande voorbeeld, hebben padparameters , aangeduid met accolades in de API-referentie. Padparameters zijn gewoon variabelen die je invoegt voordat je het verzoek doet en zijn bijna altijd ID's: gebruikers-ID's, groeps-ID's, plaats-ID's, enz. ID's zijn vaak numeriek, maar niet noodzakelijk; bijvoorbeeld, gegevensopslag- en geheugenopslag-ID's ondersteunen een breder tekenreeks.

## [Inhouds lengte en type](#inhouds-lengte-en-type)[](#inhouds-lengte-en-type)

Veel API-aanroepen, met name die welke aanmaken of bijwerken, vereisen een JSON-verzoeklichaam. Als je verzoek een lichaam heeft, zorg er dan voor dat je de headers Content-Length  en Content-Type  opneemt. De meeste HTTP-clients voegen deze headers automatisch toe.

## [Paginering](#paginering)[](#paginering)

Als je maxPageSize  in je verzoek opgeeft, retourneren sommige methoden gepagineerde resultaten—essentieel gedeeltelijke antwoorden:

```

GET /cloud/v2/users/{user_id}/inventory-items?maxPageSize=25

{

  "inventoryItems": [

    ...

  ],

  "nextPageToken": "aaaBBB"

}

```

```

GET /cloud/v2/universes/{universe_id}/data-stores?maxPageSize=25

{

  "dataStores": [

    ...

  ],

  "nextPageToken": "datastore1"

}

```

Als een antwoord een waarde voor nextPageToken  bevat, gebruik die waarde in de pageToken  parameter van het volgende verzoek om de volgende pagina op te halen. Wanneer nextPageToken  leeg of helemaal weggelaten is, heb je het einde van je resultaten bereikt:

```

GET /cloud/v2/users/{user_id}/inventory-items?maxPageSize=25&pageToken=aaaBBB

{

  "inventoryItems": [

    ...

  ],

  "nextPageToken": ""

}

```

```

GET /cloud/v2/universes/{universe_id}/data-stores?maxPageSize=25&pageToken=datastore1

{

  "dataStores": [

    ...

  ]

}

```

Afgezien van de pageToken , moet je dezelfde query gebruiken voor paginering om goed te functioneren. Het wijzigen van een filterparameter resulteert in een 400-fout.

## [Open Cloud v2](#open-cloud-v2)[](#open-cloud-v2)

### [Meerdere paden](#meerdere-paden)[](#meerdere-paden)

Sommige bronnen hebben meerdere padpatronen, zichtbaar onder de Resource Paths  kop in de API-referentie. Bijvoorbeeld, de URL voor [Lijst gebruikersbeperkingen](/docs/nl-nl/cloud/reference/UserRestriction#Cloud_ListUserRestrictions__Using_Universes)  kan een van de volgende zijn:

-

https://apis.roblox.com/cloud/cloud/v2/universes/{universe_id}/user-restrictions

-

https://apis.roblox.com/cloud/cloud/v2/universes/{universe_id}/places/{place_id}/user-restrictions

Je kunt waarschijnlijk het verschil tussen de twee afleiden: sommige gebruikersbeperkingen zijn van toepassing op een heel universum (spel), terwijl andere van toepassing zijn op specifieke plaatsen binnen een universum. Afgezien van de kleine toevoeging aan het pad en de extra padparameter, zijn de oproepen identiek.

Veel eindpunten retourneren een pad als onderdeel van hun antwoord, dat je kunt gebruiken om verdere verzoeken te doen. Als een API meer dan een paar seconden nodig heeft om een verzoek te vervullen, retourneert het vaak een [operatie](#langdurige-operaties)  in plaats van de bron of het antwoord zelf.

### [Langdurige operaties](#langdurige-operaties)[](#langdurige-operaties)

Sommige methoden retourneren een Operation  object dat een langdurig verzoek vertegenwoordigt dat later een asynchroon antwoord retourneert. Het object bevat de volgende velden:

-

path  - Het eindpunt pad om te bellen om de voltooiing van het verzoek te controleren. Voeg het pad toe aan de oorspronkelijke basis-URL van de bronmethode.

-

done  - Een boolean waarde die aangeeft of de operatie is voltooid of niet.

-

response  - Het antwoordobject. Dit veld is leeg totdat het done  veld een waarde van true  heeft.

-

metadata  - Aangepaste metadata specifiek voor het verzoek dat wordt gedaan.

Voorbeeld Operation Object

```

{

  "path": "v1/assets/12345/operation/xyz",

  "done": true,

  "response": {

    "value1": "mijnWaarde",

    "value2": 1234

  },

  "metadata": {

    "metadata1": "string",

    "metadata2": 5678

  }

}

```

Gebruik het pad van het Operation  object om te controleren wanneer de bron klaar is. Een goede strategie is om exponentiële backoff te gebruiken. Bijvoorbeeld, je kunt onmiddellijk controleren, dan na één seconde, twee seconden, vier seconden, enzovoort.

```

def PollForResults(operationPath):

    currentRetries = 0

    maxRetries = 10

    retryPollingDelay = 1

    retryPollingMultiplier = 2

    while (currentRetries < maxRetries):

        # Geen vertraging bij de eerste controle

        if (currentRetries == 0):

            results = GetOperation(operationPath)

        # Herhaal logica voor volgende controles

        else:

            time.sleep(retryPollingDelay)

            results = GetOperation(operationPath)

            # Exponentiële backoff

            retryPollingDelay *= retryPollingMultiplier

        # Controleer op resultaten en retourneer als ze bestaan

        if (results.status_code != 200 or results.json()[doneJSONKey]):

            return results

        # Anders, verhoog de retry-telling

        else:

           currentRetries += 1

```

Voor een completer codevoorbeeld dat een vaste retry-interval gebruikt in plaats van exponentiële backoff, zie [Poll for results](/docs/nl-nl/cloud/guides/instance#poll-for-results) .

### [Filteren](#filteren)[](#filteren)

Sommige methoden laten je de respons filteren door een filter  parameter in het verzoek op te nemen. De volgende secties beschrijven de filter syntaxis en richtlijnen voor de opgegeven eindpunten.

#### [Lijst groepslidmaatschappen](#lijst-groepslidmaatschappen)[](#lijst-groepslidmaatschappen)

Het wildcard-teken -  kan worden gebruikt in plaats van groeps-ID om lidmaatschappen over alle groepen te lijsten: groups/-/memberships .

Filteren voldoet aan de Common Expression Language (CEL). Slechts twee operatoren worden ondersteund:

-

==

-

in [...]

Als je een groeps-ID in het resourcepad opgeeft, kun je lidmaatschappen filteren op gebruiker of rol in de volgende formaten:

-

Gebruiker filter : filter=user == 'users/9876543210'

-

Rol filter : filter=role == 'groups/123/roles/7920705'

Als je het wildcard-teken voor de groeps-ID opgeeft, moet je lidmaatschappen filteren op gebruiker (tot 50) in het volgende formaat:

-

Gebruiker filter : filter=user in ['users/1', 'users/156', 'users/9876543210', ...]

#### [Lijst inventarisitems](#lijst-inventarisitems)[](#lijst-inventarisitems)

Je kunt filteren op verzamelobjectstatus, type inventarisitem en inventarisitem-ID. Als je geen filter opgeeft, wordt de volledige inventaris van de gebruiker geretourneerd.

Het filterformaat is een puntkomma-gescheiden lijst:

filter={field}={value};{field}={value},{value},...;{field}=...

-

{field}  kan een van de vooraf gedefinieerde typevelden of ID-velden in de volgende tabellen zijn.

-

{value}  kan een string, boolean of enum zijn. Afhankelijk van het veldtype kan dit een enkele waarde zijn (boolean velden) of meerdere waarden (lijstvelden).

Je kunt type- en ID-velden niet combineren in hetzelfde filter.

Typevelden

| Filter | | Type | | Beschrijving |
| --- | --- |
| badges | | boolean | | Neem badges op in de respons. Standaard is false. |
| gamePasses | | boolean | | Neem game passes op in de respons. Standaard is false. |
| inventoryItemAssetTypes | | Zie [assetDetails](/docs/nl-nl/cloud/reference/InventoryItem)  voor de volledige lijst van activatietypen. | | Komma-gescheiden lijst van activatietypen om op te nemen. Standaard is geen. Geef *  op voor alle activatietypen. Je moet de Inventory leesrechten hebben om te filteren op aangekochte plaatsen. |
| onlyCollectibles | | boolean | | Neem alleen  verzamelobjecten op in de respons. Standaard is false. Dit veld moet worden gebruikt met het inventoryItemAssetTypes  veld om items te retourneren en retourneert alleen niet-UGC beperkte items. |
| privateServers | | boolean | | Neem privéservers op in de respons. Standaard is false. Je moet de Inventory leesrechten hebben om op dit veld te filteren. |

ID-velden

| Filter | | Type | | Beschrijving |
| assetIds | | string | | Komma-gescheiden lijst van numerieke activatietypen om op te nemen. |
| badgeIds | | string | | Komma-gescheiden lijst van numerieke badge-ID's om op te nemen. |
| gamePassIds | | string | | Komma-gescheiden lijst van numerieke game pass-ID's om op te nemen. |
| privateServerIds | | string | | Komma-gescheiden lijst van numerieke privéserver-ID's om op te nemen. Je moet de Inventory leesrechten hebben om op dit veld te filteren. |

Voorbeelden

-

Retourneert alle verzamelobjecten die de gebruiker bezit:

filter=onlyCollectibles=true;inventoryItemAssetTypes=*

-

Retourneert alle items van de opgegeven types:

filter=inventoryItemAssetTypes=HAT,CLASSIC_PANTS,TSHIRT_ACCESSORY

-

Retourneert alle items van de vermelde types of enige game passes. Sluit badges uit van de resultaten (dezelfde gedraging als wanneer badges  niet in het filter was opgenomen):

filter=inventoryItemAssetTypes=HAT,CLASSIC_PANTS,TSHIRT_ACCESSORY;gamePasses=true;badges=false

-

Retourneert activa die overeenkomen met de opgegeven ID's:

filter=assetIds=1,2,3,4

-

Retourneert activa, badges, game passes en privéservers die overeenkomen met de opgegeven ID's:

filter=assetIds=1,2,3,4;badgeIds=1,2,3,4;gamePassIds=1,2,3,4;privateServerIds=1,2,3,4

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
