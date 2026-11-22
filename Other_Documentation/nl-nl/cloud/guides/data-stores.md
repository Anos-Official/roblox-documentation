<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/data-stores -->

Open Cloud-databases | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Gegevensopslag](/docs/nl-nl/cloud/guides/data-stores)

# Open Cloud-databases

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Naast het verkrijgen van toegang tot databases via de Engine API in Studio of live games ([DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) ), kun je de Open Cloud-API's gebruiken om toegang te krijgen tot [standaard](/docs/nl-nl/cloud/reference/DataStoreEntry)  en [geordende databases](/docs/nl-nl/cloud/reference/OrderedDataStoreEntry)  vanuit externe scripts en andere tools.

Toegang tot je databases via Open Cloud ontgrendelt veel potentiële gebruiksscenario's, waaronder:

-

Een klantenserviceportaal waarmee je team rechtstreeks ondersteuning kan bieden, zoals het wijzigen van gebruikersinventarissen of het uitgeven van terugbetalingen

-

Wereldwijde ranglijsten die je op een externe website kunt weergeven

-

Schema-updates met scripts die invoer uit de huidige database lezen, deze mappen naar het nieuwe schema en invoer terugschrijven naar een nieuwe database

De voorbeelden op deze pagina demonstreren hoe je een [gebruikersinventaris ondersteuningsportaal](#gebruikersinventaris-ondersteuningsportaal)  en een [externe ranglijst](#externe-persistente-ranglijst)  kunt bouwen met Node.js en Python, maar gebruik welke taal je ook verkiest; de Open Cloud-API's ondersteunen elke programmeertaal die een HTTP-verzoek kan verzenden.

## [Verschillen met de Engine API](#verschillen-met-de-engine-api)[](#verschillen-met-de-engine-api)

Hoewel de Open Cloud-API's toegang hebben tot dezelfde onderliggende databases en vergelijkbaar zijn met het werken met [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) , zijn er een paar belangrijke verschillen:

-

Universum-ID : In tegenstelling tot de Engine API zijn Open Cloud-API's stateless en kunnen ze van overal komen, dus je moet altijd de universum-ID  opgeven, de unieke identificatie van je game.

-

Gescheiden machtigingen voor creëren en bijwerken : De Engine API maakt nieuwe invoer aan als deze niet bestaat wanneer je [DataStore:SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync)  aanroept, maar de Open Cloud-methoden voor het creëren en bijwerken van invoer zijn gescheiden. Gescheiden machtigingen kunnen in bepaalde situaties veiliger en flexibeler zijn. Je wilt bijvoorbeeld misschien dat je klantenservicetool alleen een bestaand gebruikersprofiel kan bewerken, niet een nieuwe kan aanmaken.

-

Gegevensserialisatie : Alle Open Cloud-eindpunten vereisen dat je gegevens serialiseert voordat je ze verzendt. Serialisatie betekent het omzetten van een object in een string. Deserialisatie is het tegenovergestelde, het omzetten van een string in een object. De Engine API serialiseert en deserialiseert de inhoud van invoer automatisch, maar voor Open Cloud moet je je invoer zelf genereren of parseren naar en van JSON.

## [Niet-eindige getallen](#niet-eindige-getallen)[](#niet-eindige-getallen)

Invoeren in databases die via de Engine API zijn geschreven, kunnen niet-eindige Luau-getallen bevatten. Omdat JSON deze getallen niet kan weergeven, vervangen Open Cloud-antwoorden ze door getagde JSON-objecten in de geretourneerde invoerwaarde:

-

Positieve oneindigheid (inf ): {"m": null, "t": "numeric", "v": "inf"}

-

Negatieve oneindigheid (-inf ): {"m": null, "t": "numeric", "v": "-inf"}

-

NaN (nan ): {"m": null, "t": "numeric", "v": "nan"}

## [Machtigingen](#machtigingen)[](#machtigingen)

Databases bevatten vaak gevoelige informatie, zoals gebruikersprofielen en virtuele valuta. Om de beveiliging te waarborgen, heeft elke Open Cloud-methode bijbehorende machtigingen, genaamd scopes , die je aan je API-sleutel moet toevoegen, zoals de universe-datastores.control:list  scope voor de [Lijst Databases](/docs/nl-nl/cloud/reference/DataStore#Cloud_ListDataStores)  methode. Als je de vereiste machtigingen niet toevoegt, retourneert je API-aanroep een fout. Zie de referentiedocumentatie voor de vereiste scopes voor elk eindpunt.

Voor meer informatie over het beheren van machtigingen, zie [Beheer API-sleutels](/docs/nl-nl/cloud/auth/api-keys) .

## [Gebruikersinventaris ondersteuningsportaal](#gebruikersinventaris-ondersteuningsportaal)[](#gebruikersinventaris-ondersteuningsportaal)

Dit voorbeeld gebruikt een database genaamd Inventory  en een schema voor elke invoer van "userId": {"currency": number, "weapon": string, "level": number} . De sleutel is userId .

### [Vereiste scopes](#vereiste-scopes)[](#vereiste-scopes)

Wanneer je [een API-sleutel aanmaakt](/docs/nl-nl/cloud/auth/api-keys)  voor dit voorbeeld, voeg je de volgende scopes toe aan je sleutel:

-

universe-datastores.objects:list

-

universe-datastores.objects:read

-

universe-datastores.objects:update

Optioneel kun je de machtigingen voor alleen de Inventory -database toevoegen, een IP-adresbeperking instellen en een vervaldatum instellen.

### [Voeg scripts toe voor het gebruikersinventaris ondersteuningsportaal](#voeg-scripts-toe-voor-het-gebruikersinventaris-ondersteuningsportaal)[](#voeg-scripts-toe-voor-het-gebruikersinventaris-ondersteuningsportaal)

Nadat je de API-sleutel met de vereiste machtigingen voor de voorbeeldapp hebt aangemaakt, kun je een script maken om verzoeken naar de eindpunten te doen. Deze scripts halen de eerste 10 invoeren in de database op, verhogen de currency -waarde voor elk met 10 en werken vervolgens elke invoer bij. Voor een grotere database moet je omgaan met [paginering](/docs/nl-nl/cloud/reference/patterns#paginering)  met de maxPageSize  en pageToken  queryparameters.

Node.js Python

incrementCurrency.js

```

const apiKey = process.env.API_KEY;

if (!apiKey) {

    throw new Error('De API_KEY-omgeving variabele is niet ingesteld.');

}

const apiHeaderKey = 'x-api-key';

const universeId = '';

const dataStoreId = 'Inventory';

const baseUrl = 'https://apis.roblox.com/cloud/v2/';

async function listEntries(universe, dataStore) {

    const listPath = `universes/${universe}/data-stores/${dataStore}/entries`;

    const url = baseUrl + listPath;

    const response = await fetch(url, {

        headers: { [apiHeaderKey]: apiKey }

    });

    return response.json();

}

async function getEntry(path) {

    const url = baseUrl + path;

    const response = await fetch(url, {

        headers: { [apiHeaderKey]: apiKey }

    });

    return response.json();

}

async function updateEntry(path, payload) {

    const url = baseUrl + path;

    const response = await fetch(url, {

        method: 'PATCH',

        headers: {

            [apiHeaderKey]: apiKey,

            'Content-Type': 'application/json'

        },

        body: JSON.stringify(payload) // De body moet een string zijn

    });

    return response;

}

(async () => {

    try {

        const entries = await listEntries(universeId, dataStoreId);

        for (const entry of entries.dataStoreEntries) {

            const path = entry.path;

            console.log(`\nVerwerken invoer: ${path}`);

            const currentData = await getEntry(path);

            currentData.value.currency += 10;

            const payload = { value: currentData.value };

            const updateResponse = await updateEntry(path, payload);

            console.log(`Status: ${updateResponse.status}`);

            console.log(`Antwoord: ${await updateResponse.text()}`);

        }

    } catch (error) {

        console.error('Er is een fout opgetreden tijdens de uitvoering:', error);

    }

})();

```

Om te testen, stel de API_KEY -omgeving variabele in, installeer afhankelijkheden en voer het script uit:

```

export API_KEY=<your_key>

node incrementCurrency.js

```

## [Externe persistente ranglijst](#externe-persistente-ranglijst)[](#externe-persistente-ranglijst)

Dit voorbeeld maakt een vooraf gedefinieerde lijst van gebruikers voor demonstratiedoeleinden, maar om nuttig te zijn in een echte game, zou je een daadwerkelijke database van gebruikers nodig hebben.

### [Vereiste scopes](#vereiste-scopes-1)[](#vereiste-scopes-1)

Wanneer je [een API-sleutel aanmaakt](/docs/nl-nl/cloud/auth/api-keys)  voor dit voorbeeld, voeg je de volgende scopes toe aan je sleutel:

-

universe.ordered-data-store.scope.entry:read

-

universe.ordered-data-store.scope.entry:write

### [Voeg scripts toe voor de ranglijst](#voeg-scripts-toe-voor-de-ranglijst)[](#voeg-scripts-toe-voor-de-ranglijst)

Nadat je de API-sleutel met de vereiste machtigingen voor de voorbeeldapp hebt aangemaakt, kun je een script maken om verzoeken naar de eindpunten te doen. Deze scripts voegen enkele voorbeeldinvoeren toe aan de geordende database met willekeurige getallen en halen ze vervolgens op van hoogste naar laagste waarde. Voor een grotere database moet je omgaan met [paginering](/docs/nl-nl/cloud/reference/patterns#paginering)  met de maxPageSize  en pageToken  queryparameters.

Node.js Python

leaderboard.js

```

const apiKey = process.env.API_KEY;

const apiHeaderKey = 'x-api-key';

const universeId = '';

const orderedDataStoreId = 'PlayerScores';

const scopeId = 'global';

const baseUrl = 'https://apis.roblox.com/cloud/v2/';

async function createOrderedEntry(universe, orderedDataStore, entryId, payload) {

  const createPath = `universes/${universe}/ordered-data-stores/${orderedDataStore}/scopes/${scopeId}/entries`;

  const url = new URL(baseUrl + createPath);

  url.searchParams.append('id', entryId);

  const response = await fetch(url, {

    method: 'POST',

    headers: {

      [apiHeaderKey]: apiKey,

      'Content-Type': 'application/json',

    },

    body: JSON.stringify(payload),

  });

  if (!response.ok) {

    const errorText = await response.text();

    throw new Error(`API-fout (${response.status}): ${errorText}`);

  }

  return response.text();

}

async function listOrderedEntries(universe, orderedDataStore) {

  const listPath = `universes/${universe}/ordered-data-stores/${orderedDataStore}/scopes/${scopeId}/entries`;

  const url = new URL(baseUrl + listPath);

  url.searchParams.append('orderBy', 'value desc');

  return fetch(url, {

    headers: {

      [apiHeaderKey]: apiKey,

    },

  });

}

async function main() {

  if (!apiKey) {

    console.error('Fout: De API_KEY-omgeving variabele is niet ingesteld.');

    process.exit(1);

  }

  const entryNames = ['Ragdoll', 'Balinese', 'Tabby', 'Siamese'];

  console.log('Voorbeeldgegevens aanmaken...');

  for (const name of entryNames) {

    try {

      const randomValue = Math.floor(Math.random() * 50) + 1;

      const payload = { value: randomValue };

      const responseText = await createOrderedEntry(universeId, orderedDataStoreId, name, payload);

      console.log(responseText);

    } catch (error) {

      console.error(`Kon invoer voor "${name}" niet aanmaken: ${error.message}`);

    }

  }

  console.log('\nGesorteerde lijst van invoeren ophalen...');

  try {

    const playerScoresResponse = await listOrderedEntries(universeId, orderedDataStoreId);

    console.log(playerScoresResponse.status);

    const responseText = await playerScoresResponse.text();

    console.log(responseText);

  } catch (error) {

    console.error(`Kon invoeren niet opsommen: ${error.message}`);

  }

}

main();

```

Om te testen, stel de API_KEY -omgeving variabele in, installeer afhankelijkheden en voer het script uit:

```

export API_KEY=<your_key>

node leaderboard.js

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
