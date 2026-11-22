<!-- Source: https://create.roblox.com/docs/cloud/guides/inventory -->

User inventories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/inventory.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# User inventories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/inventory.md)

The [Inventory API](/docs/cloud/reference/InventoryItem)  lets you access most of the same information as the Roblox My Inventory  page. You can check whether a user owns individual items and retrieve the full list of items that a player owns.

Responses from the [Inventory API](/docs/cloud/reference/InventoryItem)  include items from the following categories:

-

Clothing (accessories, bottoms, classic clothing, shoes, tops)

-

Purchases and rewards (badges, passes, purchased places, private servers)

-

Avatar items (avatar animations, classic heads, emotes, faces, hair, heads)

Before using the [Inventory API](/docs/cloud/reference/InventoryItem) , you must [generate an API key](/docs/cloud/auth/api-keys)  or [configure OAuth 2](/docs/cloud/auth/oauth2-overview)  for your app. The examples on this page use API keys.

## [Check item ownership](#check-item-ownership)[](#check-item-ownership)

If you want to check whether a user owns a particular item (for example, a limited, badge, pass, or private server), use the filter  parameter to check for a comma-separated list of one or more IDs. This code sample checks for three asset IDs:

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

The following response indicates that the user owns one of the three items:

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

If you want to display, for example, only the collectibles that a user owns, use the same code as above, just with a different filter  parameter.

Node.js Python

```

const params = '?filter=onlyCollectibles=true;inventoryItemAssetTypes=*';

```

Mix and match filters using a semicolon-separated list. Here are a few examples:

```

filter=onlyCollectibles=true;inventoryItemAssetTypes=HAT,CLASSIC_PANTS

filter=badgeIds=111111,222222;gamePassIds=777777;privateServerIds=999999

filter=gamePasses=true;badges=true

```

Most calls to the API do not require any specific permissions, but several filters require Inventory read permissions. For more information, see [Filtering](/docs/cloud/reference/patterns#list-inventory-items) .

## [Paginate results](#paginate-results)[](#paginate-results)

If a response includes a value for nextPageToken , use that value in the pageToken  parameter of the subsequent request to retrieve the next page. For more information, see [Pagination](/docs/cloud/reference/patterns#pagination) .

If the number of results is divisible by maxPageSize  (for example, you have 50 results and a maxPageSize  of 25), you can encounter a situation in which your response includes a value for nextPageToken , but a request using that token returns no results:

```

GET /cloud/v2/users/{userId}/inventory-items?maxPageSize=25&pageToken=cccDDD

{

    "inventoryItems": [],

    "nextPageToken": ""

}

```

When implementing pagination in your app, best practice is to check not just for a non-empty nextPageToken , but also for a non-empty inventoryItems  array.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
