<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/inventory -->

Gebruikersinventarissen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Gebruikersinventarissen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Inventory API](/docs/nl-nl/cloud/reference/InventoryItem)  stelt je in staat om toegang te krijgen tot de meeste van dezelfde informatie als de Roblox Mijn Inventaris  pagina. Je kunt controleren of een gebruiker individuele items bezit en de volledige lijst van items ophalen die een speler bezit.

Antwoorden van de [Inventory API](/docs/nl-nl/cloud/reference/InventoryItem)  bevatten items uit de volgende categorieën:

-

Kleding (accessoires, onderkleding, klassieke kleding, schoenen, bovenkleding)

-

Aankopen en beloningen (insignes, passen, aangekochte plaatsen, privéservers)

-

Avataritems (avataranimaties, klassieke hoofden, emotes, gezichten, haar, hoofden)

Voordat je de [Inventory API](/docs/nl-nl/cloud/reference/InventoryItem)  gebruikt, moet je [een API-sleutel genereren](/docs/nl-nl/cloud/auth/api-keys)  of [OAuth 2 configureren](/docs/nl-nl/cloud/auth/oauth2-overview)  voor je app. De voorbeelden op deze pagina gebruiken API-sleutels.

## [Controleer itembezit](#controleer-itembezit)[](#controleer-itembezit)

Als je wilt controleren of een gebruiker een bepaald item bezit (bijvoorbeeld een beperkt item, insigne, pas of privéserver), gebruik dan de filter  parameter om te controleren op een door komma's gescheiden lijst van een of meer ID's. Dit codevoorbeeld controleert op drie asset-ID's:

Node.js Python

```

const https = require('node:https');

const userId = 11111111111;

const hostname = 'apis.roblox.com';

const path = `/cloud/v2/users/${userId}/inventory-items`;

const params = '?filter=assetIds=62724852,1028595,4773588762';

const url = 'https://' + hostname + path + params;

const apiKey = '123456789012345678901234567890123456789012345678';

const options = {

  headers: {

    'x-api-key': `${apiKey}`,

  },

};

https

  .get(url, options, (response) => {

    console.log('statusCode:', response.statusCode);

    let data = '';

    response.on('data', (d) => {

      data += d;

    });

    response.on('end', () => {

      if (response.statusCode === 200) {

        const jsonData = JSON.parse(data);

        console.log('Response Data:', JSON.stringify(jsonData, null, 2));

      } else {

        console.error('Error:', response.statusCode, response.statusMessage);

      }

    });

  })

  .on('error', (e) => {

    console.error(e);

  });

```

Het volgende antwoord geeft aan dat de gebruiker een van de drie items bezit:

```

{

  "inventoryItems": [

    {

      "path": "users/11111111111/inventory-items/VVNFUl9BU1NFVF9JRD0yMDAxMDUxMTkzODg",

      "assetDetails": {

        "assetId": "1028595",

        "inventoryItemAssetType": "CLASSIC_TSHIRT",

        "instanceId": "200105119388"

      }

    }

  ],

  "nextPageToken": ""

}

```

## [Filter items](#filter-items)[](#filter-items)

Als je bijvoorbeeld alleen de verzamelobjecten wilt weergeven die een gebruiker bezit, gebruik dan dezelfde code als hierboven, maar met een andere filter  parameter.

Node.js Python

```

const params = '?filter=onlyCollectibles=true;inventoryItemAssetTypes=*';

```

Mix en match filters met een door puntkomma's gescheiden lijst. Hier zijn een paar voorbeelden:

```

filter=onlyCollectibles=true;inventoryItemAssetTypes=HAT,CLASSIC_PANTS

filter=badgeIds=111111,222222;gamePassIds=777777;privateServerIds=999999

filter=gamePasses=true;badges=true

```

De meeste oproepen naar de API vereisen geen specifieke machtigingen, maar verschillende filters vereisen leesmachtigingen voor de Inventaris. Voor meer informatie, zie [Filteren](/docs/nl-nl/cloud/reference/patterns#lijst-inventarisitems) .

## [Pagineer resultaten](#pagineer-resultaten)[](#pagineer-resultaten)

Als een antwoord een waarde voor nextPageToken  bevat, gebruik dan die waarde in de pageToken  parameter van de volgende aanvraag om de volgende pagina op te halen. Voor meer informatie, zie [Paginering](/docs/nl-nl/cloud/reference/patterns#paginering) .

Als het aantal resultaten deelbaar is door maxPageSize  (bijvoorbeeld, je hebt 50 resultaten en een maxPageSize  van 25), kun je een situatie tegenkomen waarin je antwoord een waarde voor nextPageToken  bevat, maar een aanvraag met die token geen resultaten retourneert:

```

GET /cloud/v2/users/{userId}/inventory-items?maxPageSize=25&pageToken=cccDDD

{

    "inventoryItems": [],

    "nextPageToken": ""

}

```

Bij het implementeren van paginering in je app is het beste om niet alleen te controleren op een niet-lege nextPageToken , maar ook op een niet-lege inventoryItems  array.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
