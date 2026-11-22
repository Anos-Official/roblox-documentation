<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/experience-notifications -->

Gebruikersmeldingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Gebruikersmeldingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Ervaringsmeldingen  zijn een manier voor [ingeschreven](https://en.help.roblox.com/hc/en-us/articles/24769602332692-Out-of-Experience-Notifications)  gebruikers van 13 jaar en ouder om op de hoogte te blijven van hun favoriete games via tijdige, gepersonaliseerde meldingen. Als ontwikkelaar kun je bepalen welke soorten in-game activiteiten het belangrijkst zijn om je gebruikers over te informeren, evenals de inhoud van de meldingen.

Asynchrone Activiteit Vooruitgang / Prestatie Gebruikersvermeldingen

![Voorbeeldmelding](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Example-Notification-A.png)

![Voorbeeldmelding](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Example-Notification-D.png)

Nadat ze een melding hebben ontvangen, kunnen gebruikers direct via de Deelnemen -knop de ervaring betreden en spawnen volgens jouw [lanceringsgegevens](#inclusief-lancerings--en-analysem-gegevens) .

Voor meer informatie over functies, geschiktheidseisen, gebruiksrichtlijnen en de bijbehorende Engine API, zie de [Ervaringenhandleiding](/docs/nl-nl/production/promotion/experience-notifications) .

## [Implementatie](#implementatie)[](#implementatie)

De [UserNotification](/docs/nl-nl/cloud/reference/UserNotification)  resource stelt je in staat om ervaringsmeldingen naar gebruikers te sturen. Voordat je deze kunt gebruiken, moet je een [API-sleutel genereren](/docs/nl-nl/cloud/auth/api-keys)  of [OAuth 2.0 configureren](/docs/nl-nl/cloud/auth/oauth2-overview)  voor je app. De voorbeelden op deze pagina gebruiken API-sleutels.

Om een ervaringsmelding naar een gebruiker te sturen:

1.

[Maak een meldingsstring aan](/docs/nl-nl/production/promotion/experience-notifications#maak-een-meldingsstring)  in het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  (deze stap moet in het Creator Dashboard worden uitgevoerd; er is geen Open Cloud API voor).

2.

Vorm het verzoek:

1.

Kopieer de API-sleutel naar de x-api-key  verzoekheader.

2.

Kopieer de asset-ID van de meldingsstring als de waarde van de payload.message_id  eigenschap.

3.

Stel payload.type  in op "MOMENT" .

4.

Stel source.universe  in op de universum resource-URL "universes/${UniverseID}" .

Stuur een ervaringsmelding

```

curl --location 'https://apis.roblox.com/cloud/v2/users/${UserId}/notifications' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

	"source": {

		"universe": "universes/${UniverseID}"

	},

	"payload": {

		"message_id": "${AssetID}",

		"type": "MOMENT"

	}

}'

```

Voorbeeldreactie die de melding-ID in het id -veld retourneert:

```

{

  "path": "users/505306092/notifications/6ca4d981-36fa-4255-82a1-14d95c116889",

  "id": "6ca4d981-36fa-4255-82a1-14d95c116889"

}

```

### [Pas meldingen aan met parameters](#pas-meldingen-aan-met-parameters)[](#pas-meldingen-aan-met-parameters)

Om de melding voor elke ontvanger aan te passen, voeg parameters  toe in de [meldingsstring](#implementatie) . Pas vervolgens de parameters aan bij het aanroepen van de API. Je kunt bijvoorbeeld de meldingsstring definiëren als:

{userId-vriend} heeft je hoogste score met {punten} punten verslagen! Tijd om te levelen?

Voeg de userId-vriend  en punten  parameters toe in het script:

Pas melding aan met parameters

```

curl --location 'https://apis.roblox.com/cloud/v2/users/${UserId}/notifications' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

	"source": {

		"universe": "universes/${UniverseID}"

	},

	"payload": {

		"message_id": "${AssetID}",

		"type": "MOMENT",

		"parameters": {

			"userId-vriend": {"int64_value": 3702832553},

			"punten": {"string_value": "5"}

		}

	}

}'

```

### [Inclusief lancerings- en analysem gegevens](#inclusief-lancerings--en-analysem-gegevens)[](#inclusief-lancerings--en-analysem-gegevens)

Om de gebruikerservaring verder te verbeteren, kun je lanceringsgegevens  in de melding opnemen, nuttig voor scenario's zoals het routeren van gebruikers naar een coördinaatlocatie of het personaliseren van de deelname-ervaring. Daarnaast kun je [analysedata](/docs/nl-nl/production/promotion/experience-notifications#analytics)  opnemen om de prestaties van verschillende categorieën meldingen te segmenteren.

Inclusief lanceringsgegevens en analysem gegevens

```

curl --location 'https://apis.roblox.com/cloud/v2/users/${UserId}/notifications' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

	"source": {

		"universe": "universes/${UniverseID}"

	},

	"payload": {

		"message_id": "${AssetID}",

		"type": "MOMENT",

		"join_experience": {

			"launch_data": "Test_Launch_Data"

		},

		"analytics_data": {

			"category": "Test_Analytics_Category"

		}

	}

}'

```

## [Snelheidslimieten en levering](#snelheidslimieten-en-levering)[](#snelheidslimieten-en-levering)

Elke gebruiker kan één  melding per dag van een bepaalde ervaring ontvangen, en je ontvangt transparante feedback wanneer de snelheidslimiet van een gebruiker is bereikt.

Er zijn veel andere redenen waarom een melding mogelijk niet wordt afgeleverd. Voor meer informatie, zie [Leveringssysteem](/docs/nl-nl/production/promotion/experience-notifications#leveringssysteem)  in de Engine-handleiding.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
