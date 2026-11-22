<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/usage-messaging -->

Gids voor het gebruik van Messaging | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Gids voor het gebruik van Messaging

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Messaging Service API](/docs/nl-nl/cloud/reference/Universe#Cloud_PublishUniverseMessage)  is de Open Cloud-equivalent van de Engine [MessagingService](/docs/nl-nl/reference/engine/classes/MessagingService) , waarmee je kunt communiceren tussen de servers en clients van je game. De Engine API staat alleen toe dat je scripts handmatig schrijft en bijwerkt in Studio voor het publiceren van berichten, maar de Open Cloud API stelt je in staat om berichten naar live servers te sturen vanuit externe tools om je operationele workflows te automatiseren en te verbeteren.

## [Gebruik](#gebruik)[](#gebruik)

Er zijn verschillende handige tools die je kunt bouwen door cross-server communicatie met de Messaging Service API te ondersteunen, waaronder:

-

Aankondigingsportalen : Een webportaal kan nuttig zijn om aankondigingen naar alle gebruikers op servers in je game te sturen, zoals het aankondigen van een aankomend evenement, een update en de winnaar van een competitie. Op het portaal kun je een bericht bewerken en op een knop klikken die de API aanroept om het bericht naar alle gebruikers of geselecteerde gebruikers te verzenden.

-

Moderatiesysteem : Een moderatiesysteem kan helpen om je game veilig en beveiligd te houden. Wanneer je een gebruiker met ongepast gedrag detecteert, kun je een bericht publiceren om de game server te waarschuwen of de specifieke gebruiker te verbannen. Je kunt ook [gegevensopslag](/docs/nl-nl/cloud/reference/DataStore)  in het moderatiesysteem gebruiken om gebruikersaccounts aan een blokkade-lijst toe te voegen die voorkomt dat ze opnieuw deelnemen.

-

LiveOps Dashboard : LiveOps dashboards zijn nuttige tools voor het beheren van live evenementen, zoals een Halloween-feest. Op het dashboard kun je een evenement vooraf coderen, evenementberichten bijwerken, het evenement activeren wanneer het klaar is, en geselecteerde gebruikers belonen met speciale items zoals een virtuele kroon zonder enige code van de game bij te werken.

Momenteel kan de API alleen live game servers via HTTP targeten.

## [Limieten](#limieten)[](#limieten)

De Messaging Service API volgt dezelfde limieten als de Engine [MessagingService](/docs/nl-nl/reference/engine/classes/MessagingService) . Snelheidslimieten worden gedeeld tussen beide API's, en het gebruik van beide API's wordt geteld tegen dezelfde limieten.

| Limiet | | Beschrijving |
| --- | --- |
| Berichten verzonden per game server | | 600 + 240 * (aantal spelers in deze game server)  per minuut |
| Berichten ontvangen per onderwerp | | (40 + 80 * aantal servers)  per minuut |
| Berichten ontvangen voor de gehele game | | (400 + 200 * aantal servers)  per minuut |
| Abonnementen toegestaan per game server | | 20 + 8 * (aantal spelers in deze game server) |
| Abonneer verzoeken per game server | | 240 verzoeken per minuut |
| Onderwerp grootte | | 80 tekens |
| Bericht grootte | | 1.024 tekens (1 KiB) |

## [Stel een onderwerp in voor messaging](#stel-een-onderwerp-in-voor-messaging)[](#stel-een-onderwerp-in-voor-messaging)

Voordat je een bericht naar de live servers van je game kunt publiceren, moet je een onderwerp  instellen, wat een aangepast berichtkanaal is dat toegankelijk is vanaf meerdere servers. Nadat je een onderwerp hebt gedefinieerd, abonneer je gebruikers op het onderwerp om je binnenkomende berichten te ontvangen.

Momenteel kun je alleen een onderwerp definiëren in Studio en de Luau API [MessagingService:SubscribeAsync()](/docs/nl-nl/reference/engine/classes/MessagingService#SubscribeAsync)  gebruiken om gebruikers erop te abonneren. Het volgende codevoorbeeld abonneert elke gebruiker op een onderwerp wanneer ze de game betreden:

Stel een onderwerp in en abonneer gebruikers

```

local MessagingService = game:GetService("MessagingService")

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	-- Definieer en abonneer op het onderwerp

	local topic = "YourTopic"

	local connection = MessagingService:SubscribeAsync(topic, function(message)

		print(message.Data)

	end)

	player.AncestryChanged:Connect(function()

		-- Unsubscribe van het onderwerp bij verandering van spelerafstamming

		connection:Disconnect()

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Publiceer berichten naar live servers](#publiceer-berichten-naar-live-servers)[](#publiceer-berichten-naar-live-servers)

Na het [instellen](#stel-een-onderwerp-in-voor-messaging)  van een onderwerp, publiceer je een bericht naar de live servers van je game:

1.

[Maak een API-sleutel](/docs/nl-nl/cloud/auth/api-keys#api-sleutels-maken)  op het [Creator Dashboard](https://create.roblox.com/dashboard/credentials?activeTab=ApiKeysTab)  en kopieer deze naar een veilige plek. Zorg ervoor dat je de volgende instellingen uitvoert:

1.

Voeg messaging-service  toe aan Toegangsrechten .

2.

Selecteer een game en voeg de universe-messaging-service:publish  operatie toe.

2.

Verkrijg de Universe ID  voor je game:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Zoek de game waarvoor je je berichten wilt publiceren.

3.

Beweeg over de thumbnail van een game, klik op de ⋯  knop en selecteer Kopieer Universe ID .

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Experience-Public.png)

3.

Voeg de API-sleutel en het universum toe aan een POST  verzoek, zoals in dit voorbeeld:

Voorbeeldverzoek voor het publiceren van een bericht

```

curl -L -X POST 'https://apis.roblox.com/cloud/v2/universes/{universe}:publishMessage' \

-H 'x-api-key: {api-key}' \

-H 'Content-Type: application/json' \

--data '{

 "topic": "your-topic",

 "message": "Hallo, iedereen!"

}'

```

4.

Stuur het HTTP-verzoek om het bericht te publiceren.

Als je verzoek succesvol is, retourneert het HTTP 200 met een lege responsbody.

## [Voeg de Messaging Service API toe aan OAuth 2.0-apps](#voeg-de-messaging-service-api-toe-aan-oauth-20-apps)[](#voeg-de-messaging-service-api-toe-aan-oauth-20-apps)

Je kunt [OAuth 2.0-applicaties](/docs/nl-nl/cloud/auth/oauth2-overview)  maken waarmee je gebruikers berichten naar hun eigen live servers kunnen publiceren.

Ondersteuning voor derde partijen via OAuth 2.0 is een bèt Kenmerk dat onderhevig kan zijn aan wijzigingen voor toekomstige releases.

Om de Messaging Service API voor je applicatie te gebruiken en toestemming van je gebruikers aan te vragen, voer je de volgende instellingen uit:

1.

Wanneer je [je applicatie registreert](/docs/nl-nl/cloud/auth/oauth2-registration#registreer-je-app) , selecteer onder Toestemmingen  de universe-messaging-service:publish  scope.

2.

Wanneer je [de autorisatiestroom implementeert](/docs/nl-nl/cloud/auth/oauth2-overview) , voeg universe-messaging-service:publish  toe aan de scope  parameter van de autorisatie-URL die gebruikers terug naar je applicatie omleidt, zoals in het volgende voorbeeld:

```

https://apis.roblox.com/oauth/v1/authorize?client_id=816547628409595165403873012&redirect_uri=https://my-app.com/redirect&scope=openid+universe-messaging-service:publish&response_type=Code&prompts=login+consent&nonce=12345&state=6789

```

3.

Vraag toegang tot de universeId  van de game waarvoor de gebruiker hun berichten wil publiceren. Je applicatie kan een POST  verzoek sturen naar de [token resources endpoint](/docs/nl-nl/cloud/auth/oauth2-reference#tokenuitwisseling)  met de toegangstoken, client-ID en geheim of de code challenge , afhankelijk van je [implementatie van je autorisatiestroom](/docs/nl-nl/cloud/auth/oauth2-overview#implementing-authorization-flows) , als aanvraagparameters om een lijst van universeIds  van games te krijgen waarvoor de gebruiker toestemming heeft gegeven:

Voorbeeldverzoek

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token/resources' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'token=<access_token>' \

--data-urlencode 'client_id=<client_id>' \

--data-urlencode 'client_secret=<client_secret>'

```

Dit eindpunt retourneert een lijst van universeIds  zoals het volgende voorbeeldantwoord:

Voorbeeldantwoord

```

{

  "resource_infos": [

    {

      "owner": {

        "id": "1516563360",

        "type": "User"

      },

      "resources": {

        "universe": {

          "ids": ["3828411582"]

        }

      }

    }

  ]

}

```

4.

Je applicatie kan nu berichten naar elke game sturen waarvoor een gebruiker toestemming heeft gegeven. Bij het verzenden van het verzoek, voeg de toegangstoken toe aan de autorisatieheader en de universeId  en onderwerp in de aanvraag-URI in het volgende formaat:

Voorbeeldverzoek

```

curl --location --request POST 'https://apis.roblox.com/cloud/v2/universes/{universe}:publishMessage' \

--header 'Authorization: Bearer <access_token>' \

--header 'Content-Type: application/json' \

--data-raw '{"topic": "some-topic","message":"bericht om te publiceren"}'

```

## [Gebruik met HTTPService](#gebruik-met-httpservice)[](#gebruik-met-httpservice)

Deze API is een van de [Open Cloud-eindpunten die worden ondersteund](/docs/nl-nl/cloud-services/http-service#ondersteunde-open-cloud-eindpunten)  door [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) . Je kunt het gebruiken om berichten tussen verschillende games te publiceren vanuit een game.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
