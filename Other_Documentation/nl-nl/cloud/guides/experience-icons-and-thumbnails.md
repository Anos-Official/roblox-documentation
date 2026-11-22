<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/experience-icons-and-thumbnails -->

Beheer ervaring pictogrammen en miniaturen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Beheer ervaring pictogrammen en miniaturen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Ervaringen zijn gekoppeld aan verschillende media voor pictogrammen/miniaturen. Het [plaats pictogram](/docs/nl-nl/production/publishing/experience-icons)  is een enkele vierkante afbeelding. [Miniaturen van de detailpagina van de ervaring](/docs/nl-nl/production/publishing/thumbnails)  zijn een geordende lijst op de spelpagina. [Miniaturen van de startpagina](/docs/nl-nl/production/publishing/thumbnails#personalisatie-van-de-startpagina)  zijn de afbeeldingen die Roblox op de startpagina kan roteren. De termen 'miniatuur' en 'voorbeeld' zijn uitwisselbaar.

| Afbeelding | | Identificator | | Verzoek |
| --- | --- |
| [Plaats pictogram](#update-the-place-icon) | | Plaats ID | | [Update Asset](/docs/nl-nl/cloud/reference/features/assets#Assets_UpdateAsset)  met updateMask=icon |
| [Vertaald pictogram](#update-a-translated-icon) | | Universum ID en taalcodes | | [Update een spel pictogram](/docs/nl-nl/cloud/reference/features/localization#post_legacy_game_internationalization_v1_game_icon_games__gameId__language_codes__languageCode_) |
| [Miniaturen van de detailpagina van de ervaring](#update-experience-detail-page-thumbnails) | | Plaats ID | | [Update Asset](/docs/nl-nl/cloud/reference/features/assets#Assets_UpdateAsset)  met updateMask=previews |
| [Miniaturen van de startpagina](#update-homepage-thumbnails) | | Universum ID en miniatuur ID's van de startpagina | | [Thumbnail Personalization API](/docs/nl-nl/cloud/reference/features/thumbnail-personalization) |

## [Voordat je de API aanroept](#voordat-je-de-api-aanroept)[](#voordat-je-de-api-aanroept)

[Maak een API-sleutel](/docs/nl-nl/cloud/auth/api-keys)  en stuur deze in de x-api-key  header.

-

Voor het plaats pictogram en miniaturen van de detailpagina van de ervaring, voeg assets  toe aan Toegangsrechten  en geef Lezen  en Schrijven  op het spel. Deze oproepen gebruiken de [asset:read](/docs/nl-nl/cloud/reference/scopes#asset:read)  en [asset:write](/docs/nl-nl/cloud/reference/scopes#asset:write)  scopes.

-

Oproepen voor miniaturen van de startpagina vereisen de [universe.thumbnail:read](/docs/nl-nl/cloud/reference/scopes#universe.thumbnail:read)  en [universe.thumbnail:write](/docs/nl-nl/cloud/reference/scopes#universe.thumbnail:write)  scopes op dat spel.

-

Oproepen voor vertaald pictogram vereisen de [legacy-universe:manage](/docs/nl-nl/cloud/reference/scopes#legacy-universe:manage)  scope.

De pictogram- en detailpagina-oproepen nemen de Plaats ID . Startpagina-oproepen nemen de Universum ID . Kopieer beide van het [Creator Dashboard](https://create.roblox.com/dashboard/creations) :

1.

Beweeg over de miniatuur van het spel, klik op de ⋯  knop en selecteer Kopieer Universum ID .

2.

Open het spel, open vervolgens Configuraties  > Plaatsen .

3.

Open de startplaats. De Plaats ID  staat in de URL. Bijvoorbeeld, in https://create.roblox.com/dashboard/creations/experiences/0000000/places/111111/configure , is de Plaats ID 111111 .

Dezelfde pictogram- en voorbeeldoproepen werken voor een plaats anders dan de startplaats. Geef de ID van die plaats door wanneer de afbeelding bij die plaats hoort.

## [Upload de afbeelding](#upload-de-afbeelding)[](#upload-de-afbeelding)

Het plaats pictogram en de miniaturen van de detailpagina van de ervaring slaan een pad op naar een bestaande Afbeelding  asset, zoals assets/2205400862 . Upload het bestand met [Maak Asset](/docs/nl-nl/cloud/reference/features/assets#Assets_CreateAsset) , en poll [Krijg Operatie](/docs/nl-nl/cloud/reference/features/assets#Assets_GetOperation)  totdat done  is true . Lees response.assetId  van die operatie. Voor de volledige uploadstroom, limieten en groepsbezit, zie de [gebruikershandleiding voor assets](/docs/nl-nl/cloud/guides/usage-assets) .

Gebruik userId  wanneer je het spel bezit. Gebruik groupId  in plaats daarvan wanneer een groep het bezit.

Voorbeeldverzoek voor het uploaden van een afbeelding

```

curl --location 'https://apis.roblox.com/assets/v1/assets' \

--header 'x-api-key: ${ApiKey}' \

--form 'request="{

  \"assetType\": \"Image\",

  \"displayName\": \"Ervaring afbeelding\",

  \"description\": \"Afbeelding voor een ervaring pictogram of miniatuur\",

  \"creationContext\": {

    \"creator\": {

      \"userId\": \"${UserId}\"

    },

    \"assetPrivacy\": \"OpenUse\"

  }

}";type=application/json' \

--form 'fileContent=@"/filepath/image.png";type=image/png'

```

Bereid het bestand voor voordat je het uploadt. Een plaats pictogram moet vierkant zijn, en een niet-vierkant bestand wordt afgewezen. Voor de aanbevolen afmetingen en andere afbeeldingsvereisten, zie [Pictogrammen](/docs/nl-nl/production/publishing/experience-icons#beste-praktijken)  en [Miniaturen](/docs/nl-nl/production/publishing/thumbnails#beste-praktijken) .

De afbeelding moet zijn ingesteld op Open Gebruik . Afbeeldingen zijn standaard Open Gebruik als [Asset Privacy](/docs/nl-nl/projects/assets/privacy)  niet is ingeschakeld. Om ervoor te zorgen dat een nieuwe afbeelding Open Gebruik is, stel creationContext.assetPrivacy  in op OpenUse , zoals in het voorbeeldverzoek. Om een bestaande afbeelding te wijzigen, zie [Open permissies](/docs/nl-nl/projects/assets/privacy#open-machtigingen) .

Spelers zien de afbeelding nadat de moderatie deze heeft goedgekeurd. De respons van de operatie bevat moderationResult.moderationState .

## [Update het plaats pictogram](#update-het-plaats-pictogram)[](#update-het-plaats-pictogram)

Hoofdartikel:  [Pictogrammen](/docs/nl-nl/production/publishing/experience-icons)

Stuur Update Asset  op de plaats. Stel updateMask  in op icon  en stel icon  in op het afbeeldingsasset pad. Laat fileContent  weg. Deze oproep vervangt het pictogram in de brontaal.

Voorbeeldverzoek voor het instellen van het plaats pictogram

```

curl --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/${PlaceId}?updateMask=icon' \

--header 'x-api-key: ${ApiKey}' \

--form 'request="{

  \"assetId\": \"${PlaceId}\",

  \"icon\": \"assets/${ImageAssetId}\"

}";type=application/json'

```

Om het pictogram te verwijderen, stuur je hetzelfde verzoek met icon  ingesteld op een lege string.

## [Update een vertaald pictogram](#update-een-vertaald-pictogram)[](#update-een-vertaald-pictogram)

Hoofdartikel:  [Pictogrammen](/docs/nl-nl/production/publishing/experience-icons)

De [gelokaliseerde game-pictogram eindpunt](/docs/nl-nl/cloud/reference/features/localization#post_legacy_game_internationalization_v1_game_icon_games__gameId__language_codes__languageCode_)  werkt een pictogram bij voor een taal anders dan de brontaal. Een verzoek voor de brontaal wordt afgewezen. Gebruik [Update het plaats pictogram](#update-het-plaats-pictogram)  voor het pictogram dat spelers zien voordat er enige vertaling is.

gameId  is de Universum ID . Files  is de vierkante pictogram afbeelding.

Voorbeeldverzoek voor het instellen van een vertaald pictogram

```

curl --location --request POST 'https://apis.roblox.com/legacy-game-internationalization/v1/game-icon/games/${UniverseId}/language-codes/${LanguageCode}' \

--header 'x-api-key: ${ApiKey}' \

--form 'Files=@"/filepath/icon.png"'

```

## [Update miniaturen van de detailpagina van de ervaring](#update-miniaturen-van-de-detailpagina-van-de-ervaring)[](#update-miniaturen-van-de-detailpagina-van-de-ervaring)

Hoofdartikel:  [Miniaturen](/docs/nl-nl/production/publishing/thumbnails)

Detailpagina miniaturen zijn de previews  lijst van de plaats asset. Elke invoer is een afbeeldingsasset pad plus optionele alt-tekst. De volgorde van de array is de volgorde op de spelpagina.

updateMask=previews  vervangt de hele lijst. Neem elke miniatuur op die moet blijven, inclusief miniaturen die alleen naar een nieuwe positie verhuizen. Laat een miniatuur weg om deze te verwijderen. Stuur één invoer om die afbeelding de enige detailpagina miniatuur te maken.

Lees de huidige lijst voordat je deze wijzigt:

Voorbeeldverzoek voor het lezen van detailpagina miniaturen

```

curl --location 'https://apis.roblox.com/assets/v1/assets/${PlaceId}?readMask=previews' \

--header 'x-api-key: ${ApiKey}'

```

Upload eerst eventuele nieuwe bestanden, en stuur dan de volledige lijst:

Voorbeeldverzoek voor het vervangen van detailpagina miniaturen

```

curl --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/${PlaceId}?updateMask=previews' \

--header 'x-api-key: ${ApiKey}' \

--form 'request="{

  \"assetId\": \"${PlaceId}\",

  \"previews\": [

    {

      \"asset\": \"assets/${FirstImageAssetId}\",

      \"altText\": \"Spelers racen door de stad\"

    },

    {

      \"asset\": \"assets/${SecondImageAssetId}\",

      \"altText\": \"Een close-up van het nieuwe voertuig\"

    }

  ]

}";type=application/json'

```

Dit verzoek werkt de afbeeldingslijst bij. Voor hoeveel afbeeldingen of video's een spel kan tonen, en voor video miniaturen en alt-tekst, zie [Miniaturen](/docs/nl-nl/production/publishing/thumbnails) .

## [Update miniaturen van de startpagina](#update-miniaturen-van-de-startpagina)[](#update-miniaturen-van-de-startpagina)

Hoofdartikel:  [Personalisatie van de startpagina](/docs/nl-nl/production/publishing/thumbnails#personalisatie-van-de-startpagina)

Miniaturen van de startpagina gebruiken de [Thumbnail Personalization API](/docs/nl-nl/cloud/reference/features/thumbnail-personalization) , niet previews . Upload via die API, wacht op een startpagina miniatuur ID , en sla vervolgens de actieve set op. De ID in homepageThumbnailIds  is de startpagina miniatuur ID, niet de afbeeldingsasset ID en niet een pad zoals assets/2205400862 .

Volg de afbeeldingsvereisten en activeringsregels in [Personalisatie van de startpagina](/docs/nl-nl/production/publishing/thumbnails#personalisatie-van-de-startpagina) .

### [Upload een startpagina miniatuur](#upload-een-startpagina-miniatuur)[](#upload-een-startpagina-miniatuur)

Voorbeeldverzoek voor het uploaden van een startpagina miniatuur

```

curl --location --request POST 'https://apis.roblox.com/thumbnail-personalization-api/v1/universes/${UniverseId}/thumbnails/uploads' \

--header 'x-api-key: ${ApiKey}' \

--form 'files=@"/filepath/thumbnail.png"'

```

De respons koppelt elke bestandsnaam aan een operatie-ID in fileToOperationIdDict . Poll die operatie totdat uploadThumbnailStatusDict  deze bevat, en kopieer dan homepageThumbnailId :

Voorbeeldverzoek voor uploadstatus

```

curl --location 'https://apis.roblox.com/thumbnail-personalization-api/v1/universes/${UniverseId}/thumbnails/uploads/status?operationIds=${OperationId}' \

--header 'x-api-key: ${ApiKey}'

```

Om een miniatuur die al op de startpagina staat opnieuw te gebruiken, lijst ze en match assetId . Een goedgekeurde video miniatuur wordt op dezelfde manier opgenomen als een afbeelding: de lijstinvoer's assetId  is de video asset, en homepageThumbnailIds  neemt die invoer's homepageThumbnailId . Het uploadverzoek op deze API accepteert afbeeldingsbestanden. Voor video regels en de maandelijkse quotum, zie [Miniaturen](/docs/nl-nl/production/publishing/thumbnails#videos) .

Voorbeeldverzoek voor het opsommen van startpagina miniaturen

```

curl --location 'https://apis.roblox.com/thumbnail-personalization-api/v1/universes/${UniverseId}/thumbnails' \

--header 'x-api-key: ${ApiKey}'

```

### [Kies de actieve startpagina miniaturen](#kies-de-actieve-startpagina-miniaturen)[](#kies-de-actieve-startpagina-miniaturen)

[Maak een configuratie](/docs/nl-nl/cloud/reference/features/thumbnail-personalization#HomepageThumbnail_CreateThumbnailPersonalization)  wanneer je een nieuwe actieve set wilt. Dit deactiveert de vorige configuratie en start nieuwe statistieken. De lijst kan tot vijf startpagina miniatuur ID's bevatten. Dit voorbeeld laat een enkele miniatuur actief:

Voorbeeldverzoek voor een nieuwe startpagina configuratie

```

curl --location --request POST 'https://apis.roblox.com/thumbnail-personalization-api/v1/universes/${UniverseId}/personalization/create' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

  "homepageThumbnailIds": ["${HomepageThumbnailId}"]

}'

```

[Update de actieve configuratie](/docs/nl-nl/cloud/reference/features/thumbnail-personalization#HomepageThumbnail_UpdateThumbnailPersonalization)  om de actieve set te wijzigen zonder de statistieken opnieuw in te stellen. Lees eerst de actieve configuratie en stuur de id  terug:

Voorbeeldverzoek voor het lezen van de actieve configuratie

```

curl --location 'https://apis.roblox.com/thumbnail-personalization-api/v1/universes/${UniverseId}/personalization?status=Active' \

--header 'x-api-key: ${ApiKey}'

```

Voorbeeldverzoek voor het vervangen van miniaturen in de actieve configuratie

```

curl --location --request POST 'https://apis.roblox.com/thumbnail-personalization-api/v1/universes/${UniverseId}/personalization/update' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

  "id": "${ConfigurationId}",

  "homepageThumbnailIds": ["${HomepageThumbnailId}"]

}'

```

homepageThumbnailIds  specificeert de actieve miniaturen. De volgorde in de lijst doet er niet toe. Personalisatie kiest welke actieve miniatuur elke speler ziet.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
