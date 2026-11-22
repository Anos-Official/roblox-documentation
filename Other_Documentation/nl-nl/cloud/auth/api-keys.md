<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/auth/api-keys -->

Beheer API-sleutels | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Beheer API-sleutels

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Open Cloud authenticates en autoriseert API-toegang met behulp van API-sleutels, die je in staat stellen om gedetailleerde machtigingen en beveiligingscontrole toe te voegen voor het toegang krijgen tot en het gebruiken van bepaalde bronnen in je game, zoals gegevensopslag en plaatsen.

Alle Open Cloud API's vereisen dat je een API-sleutel maakt met geldige machtigingen en een x-api-key  header in je verzoek opneemt, waarmee de applicatie zich namens jou bij Open Cloud kan authentiseren.

## [API-sleutels maken](#api-sleutels-maken)[](#api-sleutels-maken)

Alle verwijzingen naar API-sleutels in de onderstaande tekst verwijzen naar door de gebruiker beheerde sleutels.

Je kunt API-sleutels maken en configureren om toegang te krijgen tot je bronnen. De toegang van een API-sleutel wordt bepaald door de machtigingen van de gebruiker die deze bezit. Dit betekent dat het over het algemeen toegang kan krijgen tot elke bron waarvoor de gebruiker machtigingen heeft, inclusief hun individuele games en eventuele [door groepen beheerde](/docs/nl-nl/projects/groups)  games waar ze de juiste rol hebben. Sommige scopes kunnen beperkt zijn tot specifieke games, maar niet allemaal.

Voor details over hoe je API-sleutels kunt maken voor het beheren van groepsbronnen, zie de sectie [API-sleutels maken voor het beheren van groepsbezit bronnen](#api-sleutels-maken-voor-het-beheren-van-groepsbezit-bronnen)  hieronder.

Om een API-sleutel te maken:

1.

Ga in het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  naar de [API-sleutels](https://create.roblox.com/dashboard/credentials?activeTab=ApiKeysTab)  pagina.

2.

Klik op de knop API-sleutel maken .

3.

Voer een unieke naam in voor je API-sleutel. Gebruik een naam die je kan helpen om het doel later te herinneren, zoals PLACE_PUBLISHING_KEY  voor het publiceren van plaatsen naar je game.

4.

Selecteer in de sectie Toegangsrechten  een API uit het menu Selecteer API-systeem . Herhaal deze stap als je meerdere API's aan de sleutel moet toevoegen.

5.

Indien van toepassing, selecteer de game die je wilt openen met de API-sleutel.

Je kunt optioneel Beperk op ervaring  uitschakelen. Wanneer dit is uitgeschakeld, heeft je API-sleutel toegang tot al je door de gebruiker beheerde games en eventuele door groepen beheerde games waar je de juiste machtigingen voor hebt, inclusief eventuele games die je in de toekomst maakt.

6.

Selecteer in de dropdown Selecteer bewerkingen  de bewerkingen die je wilt inschakelen voor de API-sleutel.

De meeste bewerkingen in de [API-referentie](/docs/nl-nl/cloud)  bevatten de vereiste machtigingsscopes. Bijvoorbeeld, de [flush memory store](/docs/nl-nl/cloud/reference/MemoryStore#Cloud_FlushMemoryStore)  bewerking vereist de universe.memory-store:flush  machtiging.

Voor een lijst van alle scopes en de API's die ze ondersteunen, zie [Scopes](/docs/nl-nl/cloud/reference/scopes) .

7.

OPTIONEEL

 In de sectie Beveiliging , beperk expliciet de IP-toegang tot de sleutel met behulp van [CIDR-notatie](#cidr-formaat) . Je kunt het IP-adres van je lokale machine vinden en dit toevoegen aan de sectie Geaccepteerde IP-adressen  samen met aanvullende IP-adressen voor degenen die toegang nodig hebben. Als je geen vast IP hebt, of je gebruikt de API-sleutel alleen in een lokale omgeving, kun je de schakelaar Beperk IP-adressen  ongecheckt laten om elke IP toegang te geven tot je API-sleutel.

8.

OPTIONEEL

 Om extra bescherming voor je bronnen toe te voegen, stel je een vervaldatum in voor je sleutel.

9.

Klik op de knop Opslaan en sleutel genereren .

10.

Kopieer en sla de API-sleutelstring op een veilige locatie op, niet  in een openbaar repository voor je code.

11.

Controleer de status van je API-sleutel op de [API-extensies](https://create.roblox.com/dashboard/credentials)  pagina van het Creator Dashboard .

De API-sleutelstring is gelijk aan een wachtwoord voor je applicatie. Deel het nooit met onbetrouwbare partijen, zoals iemand buiten je ontwikkelingsteam.

## [API-sleutels maken voor het beheren van groepsbezit bronnen](#api-sleutels-maken-voor-het-beheren-van-groepsbezit-bronnen)[](#api-sleutels-maken-voor-het-beheren-van-groepsbezit-bronnen)

Een API-sleutel geeft toegang tot alle bronnen waarvoor het gebruikersaccount machtigingen heeft, inclusief persoonlijke games buiten de groep. Als je de API-sleutel van je persoonlijke account gebruikt voor groepsautomatisering en die sleutel wordt gecompromitteerd, zijn ook andere bronnen waartoe je toegang hebt in gevaar.

Om dit te voorkomen, aanbevelen we sterk  om een aparte API-sleutel te maken op een speciaal alternatieve account met toegang die strikt beperkt is tot de doelgroep. Dit nieuwe account dat is gewijd aan automatiseringsdoeleinden, moet alleen toegang krijgen tot de doelgroep en de minimale machtigingen krijgen die nodig zijn voor zijn taak.

1.

Maak een nieuw, speciaal Roblox-account voor je automatisering.

2.

Nodig het nieuwe account uit voor je groep.

3.

Ken het een groepsrol toe met alleen de machtigingen die nodig zijn voor zijn taak.

4.

Log in op het nieuwe account en volg de stappen in de bovenstaande sectie om [een API-sleutel te maken](#api-sleutels-maken) .

5.

Gebruik de gegenereerde API-sleutel voor groepsresource-automatisering.

## [Beste praktijken voor het beheren van API-sleutels](#beste-praktijken-voor-het-beheren-van-api-sleutels)[](#beste-praktijken-voor-het-beheren-van-api-sleutels)

API-sleutels zijn gevoelige referenties die veilig moeten worden bewaard om ongeautoriseerde toegang tot je gegevens te voorkomen. Hier zijn enkele beste praktijken voor het beheren van API-sleutels.

-

Maak aparte sleutels voor elke applicatie : Maak aparte API-sleutels voor elke applicatie of gebruiksgeval om toegang te isoleren en de impact te verminderen als een sleutel wordt gecompromitteerd.

-

Selecteer de minimale benodigde machtigingen : Wanneer je scopes configureert, selecteer dan de minimale machtigingen die nodig zijn voor het beoogde gebruik van de sleutel. Voor die scopes die je toestaan om de toegang tot de scope per game te beperken, beperk de toegang tot alleen de specifieke games die nodig zijn.

-

Gebruik IP-adresbeperkingen : Beperk de toegang tot de API-sleutel tot specifieke IP-adressen of CIDR-bereiken om ongeautoriseerd gebruik vanuit onbekende locaties te voorkomen. Gebruik geen IP-adresbeperkingen wanneer je je API-sleutel in Roblox-plaatsen gebruikt om ervoor te zorgen dat je sleutel kan worden gebruikt met Roblox-servers.

-

Stel vervaldatums in : Voor kortetermijngebruik, configureer vervaldatums om sleutels automatisch uit te schakelen na een bepaalde periode, waardoor het risico wordt verminderd als een sleutel wordt gecompromitteerd. Het instellen van vervaldatums wordt niet aanbevolen voor langdurige gebruiksgevallen, tenzij je een sleutelrotatieproces hebt, omdat je automatisering onverwacht kan falen wanneer de sleutel verloopt.

-

Gebruik speciale alternatieve accounts voor het beheren van groepsbronnen : Gebruik een speciaal account met minimale machtigingen voor het beheren van groepsbronnen, zoals beschreven in de sectie [API-sleutels maken voor het beheren van groepsbezit bronnen](#api-sleutels-maken-voor-het-beheren-van-groepsbezit-bronnen) .

-

Bewaar API-sleutels veilig : Bewaar API-sleutels nooit direct in je broncode, versiebeheersystemen of scripts waar ze blootgesteld kunnen worden. Gebruik een geheimenbeheersysteem voor het opslaan en controleren van de toegang tot je sleutels. In Roblox-plaatsen, gebruik een [Secrets Store](/docs/nl-nl/cloud-services/secrets) .

-

Deel API-sleutels niet via openbare kanalen : Deel API-sleutels nooit via openbare communicatiekanalen, forums of sociale media. Deel sleutels alleen via veilige, privékanalen met vertrouwde teamleden. Beperk de toegang tot wie je sleutels deelt om de impact te minimaliseren als een sleutel wordt gecompromitteerd.

## [CIDR-formaat](#cidr-formaat)[](#cidr-formaat)

Om je bronnen verder te beschermen, wanneer je [een API-sleutel maakt](#api-sleutels-maken) , specificeer IP-adressen die toegang kunnen krijgen tot de API-sleutel met normale IP-adressen of met behulp van de [CIDR-notatie](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation) . Een CIDR-IP-adres lijkt op een normaal IP-adres, behalve dat het eindigt met een schuine streep en een decimaal dat aangeeft hoeveel bits van het IP-adres significant zijn voor netwerkrouting:

-

Normaal : 192.168.0.0

-

CIDR : 192.168.0.0/24

Het eerste deel is het IP-adres en het laatste deel is de netmasker , waarbij de bits van 1's in binaire vorm worden geteld. In het vorige voorbeeld betekent 24  255.255.255.0  (24 1's) dat alle IP's tussen 192.168.0.0  en 192.168.0.255  zijn toegestaan. Het begrijpen van het CIDR-formaat is bijzonder nuttig als je van plan bent je applicaties op een server uit te voeren.

## [Status van de API-sleutel](#status-van-de-api-sleutel)[](#status-van-de-api-sleutel)

API-sleutels hebben aanvankelijk een actieve status, maar ze kunnen inactief worden gedurende hun levensduur. Om te leren waarom een API-sleutel van status is veranderd en hoe je de API-sleutel weer naar een actieve status kunt terugbrengen, zie de volgende tabel.

 Als jij of je groep een API-sleutel 60 dagen lang niet gebruiken of bijwerken, verloopt deze automatisch, zelfs als er geen vervaldatum is ingesteld. Dit vermindert het risico dat kwaadwillenden oude API-sleutels gebruiken. Als je een API-sleutel niet meer gebruikt, moet je deze handmatig uitschakelen of verwijderen.

| Status | | Reden | | Oplossing |
| --- | --- |
| Actief | | Geen problemen. De gebruiker kan de sleutel gebruiken om API-aanroepen te authentiseren. | | N.v.t. |
| Uitgeschakeld | | De gebruiker heeft de sleutel uitgeschakeld door de ** Schakel sleutel in**  schakelaar uit te schakelen. | | Schakel de ** Schakel sleutel in**  schakelaar in. |
| Verlopen | | De vervaldatum van de sleutel is verstreken. | | Verwijder of stel een nieuwe vervaldatum in. |
| Automatisch verlopen | | De gebruiker heeft de sleutel in de afgelopen 60 dagen niet gebruikt of bijgewerkt. | | Je kunt de ** Schakel sleutel in**  schakelaar uitschakelen en vervolgens weer inschakelen, of je kunt een van de eigenschappen van de sleutel bijwerken, zoals de naam, beschrijving of vervaldatum. |
| Herroepen | | Alleen voor groepssleutels. Het account dat de sleutel heeft gegenereerd, heeft niet langer de voldoende toegangsrechten om de sleutels van de groep te beheren. | | Klik op de ** Genereer sleutel opnieuw**  om een nieuw geheim te krijgen. |
| Gemodereerd | | Een Roblox-beheerder heeft het geheim van de sleutel om beveiligingsredenen gewijzigd. | | Klik op de ** Genereer sleutel opnieuw**  om een nieuw geheim te krijgen. |
| Gebruiker gemodereerd | | Het account dat de sleutel heeft gegenereerd, staat onder moderatie door Roblox. | | Los het moderatieprobleem op het account op. |

## [API-sleutels introspecteren](#api-sleutels-introspecteren)[](#api-sleutels-introspecteren)

### [POST  api-keys/v1/introspect](#post-api-keysv1introspect)[](#post-api-keysv1introspect)

Haal informatie op over een API-sleutel. Verifieert of de sleutel kan worden gebruikt vanaf het IP-adres van de aanvrager en of de sleutel of de laatst gegenereerde gebruiker gemodereerd is.

#### Verzoek

(application/json)

| Sleutel | | Waarde |
| apiKey | | <api_key> |

Voorbeeld Introspect API Sleutel Verzoek

```

curl --location --request POST 'https://apis.roblox.com/api-keys/v1/introspect' \

--header 'Content-Type: application/json' \

--data '{

    "apiKey": "your-api-key"

}'

```

#### Antwoord

Er zijn vier mogelijke resource-identificatoren die in elk scope-object aanwezig kunnen zijn:

-

userId

-

groupId

-

universeId

-

universeDatastore

De userId en groupId identificatoren zijn alleen relevant voor scopes met het creator-doel. De universeDatastore identificator is alleen relevant voor scopes met het universe-datastore doel. De resource-identificator wordt weggelaten voor scopes die geen resource-selectie ondersteunen.

Een asterisk (* ) in de lijst van resource-identificatoren geeft aan dat de scope toestemming heeft voor alle bronnen van dat type.

Voorbeeld Introspect API Sleutel Antwoord

```

{

  "name": "test key",

  "authorizedUserId": 234,

  "scopes": [

    {

      "name": "universe-datastores.objects",

      "operations": [

        "create"

      ],

      "universeDatastores": [

        {

          "universeId": "123",

          "datastoreName": "playerData"

        }

      ]

    },

    {

      "name": "asset",

      "operations": [

        "write"

      ],

      "groupIds": [

        "*"

      ],

      "userIds": [

        "*"

      ]

    }

  ],

  "enabled": true,

  "expired": false,

  "expirationTimeUtc": "2026-01-01T12:00:00.000Z"

}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
