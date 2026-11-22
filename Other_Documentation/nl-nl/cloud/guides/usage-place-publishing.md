<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/usage-place-publishing -->

Gebruiksgids voor het publiceren van plaatsen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Gebruiksgids voor het publiceren van plaatsen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Assets API](/docs/nl-nl/cloud/reference/features/assets)  biedt vergelijkbare functionaliteit als [publiceren naar Roblox](/docs/nl-nl/production/publishing/publish-games-and-places)  in Studio, met extra toegangscontrole en automatisering in continue release-workflows. Je kunt deze API gebruiken om bestaande plaatsen van een spel naar een nieuwe versie bij te werken, wat handig is voor het automatiseren van je publicatieworkflow. Je kunt bijvoorbeeld deze API aanroepen vanuit een GitHub-actie en het automatisch een binaire plaatsbestand naar Roblox laten pushen na succesvolle integratietests.

Omdat de Assets API uploads asynchroon verwerkt, retourneert het publiceren van een plaats een Operation ID  in plaats van een onmiddellijke versienummer. Je moet de operatie vervolgens polsen totdat deze is voltooid om te bevestigen dat de publicatie is geslaagd.

## [Beperkingen](#beperkingen)[](#beperkingen)

-

Deze API ondersteunt alleen HTTPS-verzoeken.

-

De plaats publicatie-API werkt bepaalde instantie types niet bij. Als je spel [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh) , [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation) , [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of [BaseWrap](/docs/nl-nl/reference/engine/classes/BaseWrap)  instanties bevat, publiceer dan vanuit Studio nadat je ze hebt aangepast.

## [Plaatsen op Roblox](#plaatsen-op-roblox)[](#plaatsen-op-roblox)

Spellen op Roblox kunnen meerdere plaatsen hebben, met één startplaats  als het toegangspunt voor gebruikers van je spel en optionele andere plaatsen waar je [gebruikers tussen kunt teleporteren](/docs/nl-nl/projects/teleport) . Je kunt de API gebruiken om ofwel de startplaats of andere plaatsen van je spel met versiebeheer te publiceren.

Voordat je een bestaande plaats van een spel kunt bijwerken, heb je de Place ID  van de plaats nodig. De Assets API beschouwt een plaats als een asset, dus de Place ID  is ook de asset ID  van de plaats.

## [Publiceer een plaats](#publiceer-een-plaats)[](#publiceer-een-plaats)

Om een bestaande plaats van een spel te publiceren met de [Update Asset](/docs/nl-nl/cloud/reference/features/assets#Assets_UpdateAsset)  eindpunt:

1.

[Maak een API-sleutel](/docs/nl-nl/cloud/auth/api-keys#api-sleutels-maken)  op het Creator Dashboard . Zorg ervoor dat je de volgende instellingen uitvoert:

1.

Voeg assets  toe aan Toegangsrechten .

2.

Voeg Lezen  en Schrijven  operaties toe aan je geselecteerde spel.

2.

Verkrijg de Place ID  van de plaats die je wilt bijwerken.

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Zoek het spel met de plaats die je wilt bijwerken en klik op de miniatuur.

3.

Klik in het linkernavigatiemenu op het tabblad Plaatsen .

4.

Zoek de plaats die je wilt bijwerken en klik op de miniatuur.

5.

De Place ID  staat in de omgeleide URL. Bijvoorbeeld, in de URL https://create.roblox.com/dashboard/creations/experiences/0000000/places/111111/configure , is de **Place ID** 111111`.

3.

Voeg de API-sleutel toe in de x-api-key  header van een PATCH  verzoek naar het eindpunt. Geef het plaatsbestand door in het fileContent  formulier veld, en stel assetType  in op Place  en published  op true  in het request  formulier veld. Je moet published  expliciet op true  instellen  om de nieuwe inhoud te publiceren; anders wordt de upload opgeslagen als een nieuwe, niet-gepubliceerde assetversie. De volgende twee voorbeeldverzoeken verwijzen naar een Roblox XML plaatsbestand (.rbxlx ) en een binaire plaatsbestand (.rbxl ).

XML Plaatsbestand Verzoek

```

$ curl --verbose --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/{placeId}' \

--header 'x-api-key: <your-api-key>' \

--form 'request={"assetId": {placeId}, "assetType": "Place", "published": true}' \

--form 'fileContent=@/home/placefiles/place1.rbxlx;type=application/xml'

```

Binaire Plaatsbestand Verzoek

```

$ curl --verbose --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/{placeId}' \

--header 'x-api-key: <your-api-key>' \

--form 'request={"assetId": {placeId}, "assetType": "Place", "published": true}' \

--form 'fileContent=@/home/placefiles/place1.rbxl;type=application/octet-stream'

```

Om de opdrachten uit te voeren, vervang je {placeId}  door de werkelijke Place ID  van de plaats die je wilt publiceren, en werk je het fileContent  pad bij om naar je plaatsbestand te verwijzen.

4.

Als je je verzoek correct verzendt, ontvang je een succesrespons met een Operation ID  in het volgende formaat:

Voorbeeld Responsbody

```

{ "path": "operations/{operationId}" }

```

Dit geeft aan dat Roblox je upload heeft geaccepteerd en deze asynchroon verwerkt. Ga verder naar de volgende sectie om het resultaat te controleren.

## [Controleer de status van de publicatie-operatie](#controleer-de-status-van-de-publicatie-operatie)[](#controleer-de-status-van-de-publicatie-operatie)

Omdat het Update Asset eindpunt je plaatsupload asynchroon verwerkt, gebruik je de geretourneerde Operation ID  om te bevestigen dat de publicatie succesvol is voltooid:

1.

Voeg de API-sleutel toe in de x-api-key  header van een GET  verzoek naar het [Get Operation](/docs/nl-nl/cloud/reference/features/assets#Assets_GetOperation)  eindpunt:

Voorbeeld Verzoek voor Get Operation

```

$ curl --verbose --location 'https://apis.roblox.com/assets/v1/operations/{operationId}' \

--header 'x-api-key: <your-api-key>'

```

Vervang {operationId}  door de Operation ID  van de vorige stap.

2.

Pols dit eindpunt totdat het done  veld in de respons true  is. Terwijl done  false  is, is de operatie nog steeds bezig.

Voorbeeld Responsbody

```

{

  "path": "operations/{operationId}",

  "done": true,

  "response": {

    "path": "assets/{placeId}",

    "revisionId": "{versionNumber}",

    "isPublished": true

  }

}

```

-

Als de operatie succesvol is, bevat response  de bijgewerkte plaats. revisionId  is het nieuwe versienummer, en isPublished  is true  wanneer die versie is gepubliceerd.

-

Als de operatie mislukt, bevat het een error  veld in plaats van response . Het error  veld is een Status  object waarvan de code  en message  uitleggen waarom de publicatie is mislukt.

3.

OPTIONEEL

 Verifieer de upload in Studio of op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
