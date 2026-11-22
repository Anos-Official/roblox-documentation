<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/usage-assets -->

Gebruiksgids voor assets | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Gebruiksgids voor assets

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Assets API](/docs/nl-nl/reference/cloud/assets/v1)  van Open Cloud stelt je in staat om assets te uploaden en bij te werken met een enkele HTTP-aanroep in plaats van ze handmatig naar Studio te importeren. Deze API ondersteunt:

-

Het uploaden van nieuwe assets.

-

Het bijwerken van bestaande assets met versiebeheer.

-

Het bijwerken van assetmetadata, inclusief beschrijvingen, weergavenamen, pictogrammen en previews. Voor plaatspictogrammen en thumbnails van detailpagina's van ervaringen, zie [Beheer ervaring pictogrammen en thumbnails](/docs/nl-nl/cloud/guides/experience-icons-and-thumbnails) .

-

Het beheren van assetversies, zoals terugrollen naar een specifieke vorige versie.

-

Het controleren van bestaande informatie van een asset, inclusief metadata, versies en eventuele lopende bijwerkingsoperaties.

Deze API bevat beta-eindpunten die onderhevig kunnen zijn aan wijzigingen voor toekomstige releases.

## [Ondersteunde assettypes en limieten](#ondersteunde-assettypes-en-limieten)[](#ondersteunde-assettypes-en-limieten)

Voor eindpunten die geen nieuwe asset creëren of de inhoud van bestaande assets bijwerken, zijn er geen beperkingen en limieten. De functionaliteit voor het uploaden van assetinhoud, aangedreven door de Create Asset  en Update Asset  eindpunten, ondersteunt echter alleen beperkte types assets met beperkingen. Voor elke aanroep kun je slechts één asset creëren of bijwerken met een bestandsgrootte tot 20 MB met de volgende limieten:

Het bijwerken van assetmetadata met behulp van het Update Asset  eindpunt is niet onderhevig aan de volgende limieten.

| Assettype | | Formaat | | Inhoudstype | | Beperkingen |
| --- | --- |
| [Animatie](/docs/nl-nl/animation) | |
-

.rbxm

-

.rbxmx

 | |
-

model/x-rbxm

-

model/x-rbxm

 | |
-

.rbxm  of .rbxmx  bestanden die buiten [Roblox Studio](/docs/nl-nl/studio/setup)  zijn bewerkt, kunnen mogelijk niet worden geüpload of functioneren.

 |
| [Audio](/docs/nl-nl/audio/assets) | |
-

.mp3

-

.ogg

-

.wav

-

.flac

 | |
-

audio/mpeg

-

audio/ogg

-

audio/wav

-

audio/flac

 | |
-

Tot 7 minuten duur.

-

Tot 100 uploads per maand als je ID-geverifieerd bent.

-

Tot 10 totale uploads per maand als je niet ID-geverifieerd bent.

-

Niet beschikbaar voor bijwerken.

 |
| [Decal, Afbeelding](/docs/nl-nl/parts/textures-decals) | |
-

.png

-

.jpeg

-

.bmp

-

.tga

 | |
-

image/png

-

image/jpeg

-

image/bmp

-

image/tga

 | |
-

Moet kleiner zijn dan 8000x8000 pixels.

-

Niet beschikbaar voor bijwerken.

 |
| [Mesh](/docs/nl-nl/parts/meshes) | |

Alleen Roblox

 | |
-

model/x-file-mesh-data

 | |
-

Alleen inhoud die is gedownload van de [Asset delivery API](/docs/nl-nl/cloud/reference/domains/assetdelivery)  wordt geaccepteerd. Als je niet probeert om meshes te downloaden en opnieuw te uploaden, gebruik dan de [Importer](/docs/nl-nl/studio/importer)  om meshes te importeren.

-

Niet beschikbaar voor bijwerken.

 |
| [Model](/docs/nl-nl/parts/models) | |
-

.fbx

-

.gltf

-

.glb

-

.rbxm

-

.rbxmx

 | |
-

model/fbx

-

model/gltf+json

-

model/gltf-binary

-

model/x-rbxm

-

model/x-rbxm

 | |
-

Importeert aangepaste 3D-modellen als een [Model](/docs/nl-nl/reference/engine/classes/Model)  container die een of meer [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten bevat.

-

Afhankelijk van je gebruiksdoel, overweeg om aangepaste 3D-modellen handmatig te uploaden met behulp van de [Importer](/docs/nl-nl/studio/importer) .

-

De Importer biedt een 3D-preview, verschillende foutcontroles en veel aanpasbare importinstellingen.

-

.rbxm  of .rbxmx  bestanden die buiten [Roblox Studio](/docs/nl-nl/studio/setup)  zijn bewerkt, kunnen mogelijk niet worden geüpload of functioneren.

-

Wordt geüpload als [pakketten](/docs/nl-nl/projects/assets/packages)

 |
| [Video](/docs/nl-nl/ui/video-frames) | |
-

.mp4

-

.mov

 | |
-

video/mp4

-

video/mov

 | |
-

Tot 5 minuten duur.

-

Tot 4096x2160 resolutie.

-

Tot 3,75 GB.

-

Tot 20 uploads per dag als je 13+ bent en ID-geverifieerd.

-

Niet beschikbaar voor bijwerken.

 |

## [Beveiligingsmachtigingen](#beveiligingsmachtigingen)[](#beveiligingsmachtigingen)

De API ondersteunt zowel gebruik door de eerste partij met [API-sleutelautorisatie](/docs/nl-nl/cloud/auth/api-keys)  als gebruik door derden in [OAuth 2-toepassingen](/docs/nl-nl/cloud/auth/oauth2-overview) . Elke manier vereist verschillende instellingen voor beveiligingsmachtigingen.

### [API-sleutels](#api-sleutels)[](#api-sleutels)

Om de API in je eigen scripts of tools te gebruiken, moet je een [API-sleutel maken](/docs/nl-nl/cloud/auth/api-keys#api-sleutels-maken)  voor autorisatie en beveiliging.

Om een API-sleutel te maken voor het beheren van groepsassets, moet je de bijbehorende machtigingen hebben. Voor meer informatie over het verlenen van groepsmachtigingen, zie [Groepsrollen en machtigingen](/docs/nl-nl/projects/groups#rollen-en-machtigingen) .

Bij het maken van een API-sleutel, zorg ervoor dat je de volgende machtigingen toevoegt:

1.

Voeg assets  toe aan Toegangsrechten .

2.

Voeg Lezen  en Schrijven  operationele machtigingen toe aan je geselecteerde game, afhankelijk van de vereiste scopes van de eindpunten die je van plan bent aan te roepen.

Zodra je de API-sleutel hebt, kopieer je deze naar de x-api-key  aanvraagheader. Alle eindpunten vereisen de x-api-key  aanvraagheader.

Voorbeeld API-aanvraagheader

```

--header 'x-api-key: ${ApiKey}' \

```

### [OAuth 2.0-apps](#oauth-20-apps)[](#oauth-20-apps)

Om de API te gebruiken voor een derde partij OAuth 2.0-toepassing, voeg de asset:read  en asset:write  machtigingsscopes toe bij het [registreren van je app](/docs/nl-nl/cloud/auth/oauth2-registration#voeg-machtigingen-toe) . Kies deze scopes op basis van de vereisten van de eindpunten die je van plan bent te gebruiken.

## [Maak een nieuwe asset](#maak-een-nieuwe-asset)[](#maak-een-nieuwe-asset)

Om een nieuwe asset te uploaden via een HTTP-aanroep:

1.

Kopieer de API-sleutel naar de x-api-key  aanvraagheader van het [Create Asset](/docs/nl-nl/reference/cloud/assets/v1#POST-v1-assets)  eindpunt.

2.

In je aanvraag:

1.

Geef het doel [assettype](#ondersteunde-assettypes-en-limieten)  op.

2.

Voeg je assetnaam en beschrijving toe.

3.

Voeg de informatie van de maker toe.

-

Als je de asset namens jezelf  wilt maken, voeg dan je gebruikers-ID toe. Je kunt je gebruikers-ID vinden in de URL van je Roblox-profiel. Bijvoorbeeld, voor https://www.roblox.com/users/1234567/profile , is je gebruikers-ID 1234567 .

-

Als je de asset als een groepsasset  wilt maken, voeg dan de groeps-ID van je groep toe. Je kunt de groeps-ID vinden in de URL van de pagina van je groep. Bijvoorbeeld, voor https://www.roblox.com/groups/7654321/example-group#!/ , is de groeps-ID 7654321 .

4.

Voeg het bestandspad en het inhoudstype van je asset toe.

Voorbeeldaanvraag voor het maken van een asset

```

curl --location 'https://apis.roblox.com/assets/v1/assets' \

--header 'x-api-key: ${ApiKey}' \

--form 'request="{

  \"assetType\": \"Model\",

  \"displayName\": \"Naam\",

  \"description\": \"Dit is een beschrijving\",

  \"creationContext\": {

    \"creator\": {

      \"userId\": \"${userId}\" # Gebruik groupId voor het maken van een groepsasset

    }

  }

}"' \

--form 'fileContent=@"/filepath/model.fbx";type=model/fbx'

```

## [Update een bestaande asset](#update-een-bestaande-asset)[](#update-een-bestaande-asset)

Het bijwerken van assets wordt aangedreven door beta-eindpunten die onderhevig kunnen zijn aan wijzigingen voor toekomstige releases.

Om een bestaande asset bij te werken via een HTTP-aanroep:

1.

Kopieer de API-sleutel naar de x-api-key  aanvraagheader van het [Update Asset](/docs/nl-nl/reference/cloud/assets/v1#PATCH-v1-assets-_asset_)  eindpunt.

2.

Voeg het assettype en de asset-ID toe in je aanvraag. Om je asset-ID te kopiëren:

1.

Navigeer naar de [Creatie](https://create.roblox.com/dashboard/creations)  pagina van het Creator Dashboard .

2.

Selecteer de categorie Ontwikkelingsitems .

3.

Selecteer de categorie van je asset en vind de doelasset.

4.

Beweeg met de muis over de thumbnail van de doelasset en klik op de ⋯  knop om een lijst met opties weer te geven, selecteer vervolgens Kopieer Asset-ID  uit de lijst.

Assetinhoud Metadata Inhoud en metadata

Momenteel kun je alleen de assetinhoud voor .fbx  bestanden bijwerken. De update creëert een nieuwe versie.

Voorbeeldaanvraag voor het bijwerken van assetinhoud

```

curl --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/{assetId}' \

--header 'x-api-key: {apiKey}' \

--form 'request={

    \"assetType\": \"{assetType}\",

    \"assetId\": \"{assetId}\",

    \"creationContext\": {

        \"creator\": {

            \"userId\": {userId}

        },

        \"expectedPrice\":{expectedPrice}

    },

}' \

--form 'fileContent=@"{file-path}"'

```

Om een plaatspictogram of thumbnails van detailpagina's van ervaringen bij te werken, zie [Beheer ervaring pictogrammen en thumbnails](/docs/nl-nl/cloud/guides/experience-icons-and-thumbnails) .

## [Haal de status van de assetoperatie op](#haal-de-status-van-de-assetoperatie-op)[](#haal-de-status-van-de-assetoperatie-op)

Als je aanvraag voor het creëren van een nieuwe asset of het bijwerken van een bestaande asset succesvol is, retourneert deze een Operation ID  in het formaat van { "path": "operations/${operationId}" } . Je kunt het gebruiken om de status en het resultaat van je upload te controleren met de volgende stappen:

1.

Kopieer de API-sleutel naar de x-api-key  aanvraagheader van de [Get Operation](/docs/nl-nl/reference/cloud/assets/v1#GET-v1-operations-_operationId_)  methode en stuur de aanvraag, zoals het volgende codevoorbeeld laat zien:

Voorbeeldaanvraag voor het ophalen van de operatie

```

curl --location 'https://apis.roblox.com/assets/v1/operations/{operationId}' \

--header 'x-api-key: {$ApiKey}'

```

2.

Als je aanvraag succesvol is, retourneert deze een Operation  object, dat ofwel een response  bevat die de geüploade assetinformatie vertegenwoordigt of een status  die uitlegt waarom de assetupload mislukt, zoals het volgende codevoorbeeld laat zien:

Voorbeeldantwoord voor het ophalen van de operatie

```

{

  "path": "operations/{operationId}",

  "done": true,

  "response": {

    "@type": "type.googleapis.com/roblox.open_cloud.assets.v1.Asset",

    "path": "assets/2205400862",

    "revisionId": "1",

    "revisionCreateTime": "2023-03-02T22:27:04.062164400Z",

    "assetId": "2205400862",

    "displayName": "Naam",

    "description": "Dit is een beschrijving",

    "assetType": "ASSET_TYPE_DECAL",

    "creationContext": {

      "creator": {

        "userId": "11112938575"

      }

    },

    "moderationResult": {

      "moderationState": "MODERATION_STATE_APPROVED"

    }

  }

}

```

3.

OPTIONEEL

 Controleer de gemaakte asset op je Roblox-account.

1.

Navigeer naar de Inventaris  pagina van je [Roblox-account](https://www.roblox.com/home) .

2.

Selecteer de Categorie  van de asset die je wilt controleren.

3.

Zoek de doelasset en klik op de thumbnail om de asset te bekijken.

## [Gebruik geüploade assets in Studio](#gebruik-geüploade-assets-in-studio)[](#gebruik-geüploade-assets-in-studio)

Een asset die je uploadt, behoort tot de gebruiker of groep in de creationContext  van je aanvraag, dus het is beschikbaar in Studio zoals elke andere asset die de maker bezit:

-

Voeg het toe vanuit de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of de [Asset Manager](/docs/nl-nl/projects/assets/manager#inventaris-sorteren) .

-

Modellen worden geüpload als [pakketten](/docs/nl-nl/projects/assets/packages) , dus controleer Inventaris  ⟩ Mijn Pakketten  in de Toolbox (of Creaties  ⟩ Groepspakketten  als een groep ze bezit).

-

Om een asset in een eigenschap te gebruiken, voer rbxassetid://  in, gevolgd door de assetId  uit de operatieantwoord in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster. Wijs die string in een script toe aan een stringeigenschap zoals [AudioPlayer.Asset](/docs/nl-nl/reference/engine/classes/AudioPlayer#Asset) , of geef de assetId  door aan [Content.fromAssetId()](/docs/nl-nl/reference/engine/datatypes/Content#fromAssetId)  voor een eigenschap van het type [Content](/docs/nl-nl/reference/engine/datatypes/Content) , zoals [Decal.ColorMapContent](/docs/nl-nl/reference/engine/classes/Decal#ColorMapContent) . Voor meer informatie, zie [rbxassetid](/docs/nl-nl/projects/assets#rbxassetid) .

## [Voeg assets API toe aan OAuth 2.0-apps](#voeg-assets-api-toe-aan-oauth-20-apps)[](#voeg-assets-api-toe-aan-oauth-20-apps)

Je kunt [OAuth 2.0-toepassingen](/docs/nl-nl/cloud/auth/oauth2-overview)  maken die de Assets API ondersteunen om je gebruikers in staat te stellen om assets naar Roblox te uploaden en bij te werken.

Ondersteuning voor derde partijen via OAuth 2.0 is een bèt Kenmerk dat onderhevig kan zijn aan wijzigingen voor toekomstige releases.

Om de Assets API voor je toepassing te gebruiken en machtigingen van je gebruikers aan te vragen, voer je de volgende instellingen uit:

1.

Wanneer je [je toepassing registreert](/docs/nl-nl/cloud/auth/oauth2-registration#registreer-je-app) , selecteer onder Machtigingen  de scopes asset:read  en asset:write .

2.

Wanneer je [de autorisatieflow implementeert](/docs/nl-nl/cloud/auth/oauth2-overview#implement-authorization-flows) , voeg asset:read  en asset:write  toe als de scopeparameters van de autorisatie-URL die gebruikers terugleidt naar je toepassing, zoals het volgende voorbeeld:

```

https://apis.roblox.com/oauth/v1/authorize?client_id=819547628404595165403873012&redirect_uri=https://my-app.com/redirect&scope=asset:read+asset:write&response_type=Code&prompts=login+consent&nonce=12345&state=6789

```

3.

Bij het verzenden van de aanvraag, voeg het toegangstoken toe in de autorisatieheader en de formuliergegevens van de assetinhoud die je wilt creëren of bijwerken in de aanvraag-URI. Het volgende voorbeeld toont een voorbeeldaanvraag voor het uploaden van een nieuwe asset:

Voorbeeldaanvraag

```

curl --location --request POST 'https://apis.roblox.com/assets/v1/assets' \

--header 'Authorization: Bearer <access_token>' \

--header 'Content-Type: application/json' \

--form 'request="{

  \"assetType\": \"Decal\",

  \"displayName\": \"DecalDemo123\",

  \"description\": \"Dit is een beschrijving\",

  \"creationContext\": {

    \"creator\": {

    \"userId\": \"<user_id>\"

    }

  }

}"' \

--form 'fileContent=@"/filepath/p1.png"'

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
