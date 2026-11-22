<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/right-to-be-forgotten -->

Recht om vergeten te worden (RTBF) voor gegevensopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Recht om vergeten te worden (RTBF) voor gegevensopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Recht om vergeten te worden (RTBF)  voor gegevensopslag stelt je in staat om aan te geven welke sleutels en gegevensopslagplaatsen de gegevens van een gebruiker bevatten. Wanneer Roblox een RTBF-verzoek voor jouw game verwerkt, gebruikt het systeem die templates om de bijbehorende gegevens automatisch te verwijderen. Je kunt templates visueel configureren via de [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager)  in de Creator Hub, of programmatisch via de Open Cloud [Configs API](/docs/nl-nl/cloud/reference/features/configs) .

## [Geautomatiseerde RTBF](#geautomatiseerde-rtbf)[](#geautomatiseerde-rtbf)

Om gebruik te maken van geautomatiseerde RTBF-verwerking, moet je verwijderingstemplates definiëren. Deze templates vertellen Roblox welke gegevensopslagplaatsen of sleutels tot een specifieke gebruiker behoren. Je kunt tot 100 templates hebben om je gebruikersgegevens te identificeren.

### [Verwijderingstemplates](#verwijderingstemplates)[](#verwijderingstemplates)

Geautomatiseerde RTBF werkt door patronen te matchen. Je definieert een template voor je gebruikersgegevens met behulp van een {UserId}  token. Wanneer Roblox een verzoek om vergeten te worden ontvangt, vervangt het systeem die token door de werkelijke ID van de aanvrager en scant het je gegevensopslagplaatsen op overeenkomsten om te verwijderen.

### [Geschiktheidseisen](#geschiktheidseisen)[](#geschiktheidseisen)

Om in aanmerking te komen voor automatische verwijdering, moet een invoer voldoen aan de volgende criteria:

-

Opslagtype  — Gebruikersgegevens moeten worden opgeslagen in een standaard gegevensopslagplaats of een geordende gegevensopslagplaats. Verwijdering van een hele gegevensopslagplaats wordt alleen ondersteund voor standaard gegevensopslagplaatsen.

-

Identificator  — De gebruikers-ID moet deel uitmaken van de Name  of de Scope  van de gegevensopslagplaats of sleutel.

-

Formaat  — De ID moet identificeerbaar zijn via een statisch tekenpatroon (bijvoorbeeld, User_{UserId} ).

## [Configureer geautomatiseerde RTBF via Data Stores Manager](#configureer-geautomatiseerde-rtbf-via-data-stores-manager)[](#configureer-geautomatiseerde-rtbf-via-data-stores-manager)

De Creator Hub biedt een visuele interface om je RTBF-templates te beheren zonder de opdrachtregel te gebruiken.

Voor groepsgames moet je de Bekijk Analytics -machtiging toevoegen om configuraties te bekijken, en de Bewerken en publiceren ervaring -machtiging om configuraties te bekijken, bewerken en publiceren. Bovendien moet de gebruiker zelf [in aanmerking komen om games te publiceren](https://en.help.roblox.com/hc/en-us/articles/203313890-How-to-Publish-Public-Experiences-on-Roblox) .

1.

Selecteer een game op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Ga in de navigatie aan de linkerkant naar Configuraties  > Data stores manager .

3.

Selecteer het tabblad RTBF Verwijdering .

4.

Klik op Template Aanmaken .

5.

Selecteer het Type  (Standaard Gegevensopslagplaats , Standaard Sleutel  of Geordende Sleutel ).

6.

Vul de bijbehorende velden in met je template met behulp van de {UserId}  token (bijvoorbeeld, PlayerInventory_{UserId} ). Deze token is hoofdlettergevoelig.

7.

Controleer de voorbeeldoutput en klik op Aanmaken .

 ![Dialoogvenster voor het maken van een template met Type, Gegevensopslagplaats, Sleutelpatroon en Scope-velden, en een voorbeeld van het resulterende gegevensopslagpad.](https://prod.docsiteassets.roblox.com/assets/data/data-store/Data-Stores-RTBF-Template.png)

## [Configureer geautomatiseerde RTBF via Configs API](#configureer-geautomatiseerde-rtbf-via-configs-api)[](#configureer-geautomatiseerde-rtbf-via-configs-api)

Je kunt ook RTBF-templates programmatisch beheren met behulp van de Open Cloud Configs API. Dit is nuttig voor automatisering of het beheren van templates op grote schaal.

1.

Ga naar het Creator Dashboard, [maak of bewerk een API-sleutel](https://create.roblox.com/dashboard/credentials)  om de universe:read  en universe:write  machtigingen op te nemen voor elk universum waar je de RTBF-verwijdering wilt automatiseren. Voor meer details, zie [Beheer API-sleutels](/docs/nl-nl/cloud/auth/api-keys) .

2.

Templates worden opgeslagen als een JSON-configuratie genaamd user_data_templates . Er zijn twee hoofdtypen:

-

Sleuteltemplate  — Identificeert specifieke sleutels. Vereist data_store_type  (STANDARD  of ORDERED ), data_store_name , en key_pattern . scope_pattern  is optioneel maar aanbevolen.

-

Gegevensopslagtemplate  — Identificeert een hele gegevensopslagplaats. Vereist data_store_type  (momenteel ondersteunt alleen STANDARD ) en data_store_pattern .

Voor beide template soorten wordt de {UserId}  token vervangen door de ID van de gebruiker wanneer een RTBF-verzoek wordt verwerkt.

Voorbeeldconfiguratie

```

{

	"user_data_templates": [

		{

			"key_template": {

				"data_store_type": "STANDARD",

				"data_store_name": "PlayerInventory",

				"key_pattern": "User_{UserId}",

				"scope_pattern": "Scope_{UserId}"

			}

		},

		{

			"key_template": {

				"data_store_type": "ORDERED",

				"data_store_name": "PlayerLeaderboard",

				"key_pattern": "User_{UserId}",

				"scope_pattern": "global"

			}

		},

		{

			"data_store_template": {

				"data_store_type": "STANDARD",

				"data_store_pattern": "Player_{UserId}_Save"

			}

		}

	]

}

```

De {UserId}  token is hoofdlettergevoelig . Als scope_pattern  wordt weggelaten of leeg is, wordt het standaard ingesteld op global .

3.

Dien vervolgens in via de Open Cloud [Configs API](/docs/nl-nl/cloud/reference/features/configs) . In de volgende voorbeelden, vervang <API_KEY>  en <UNIVERSE_ID>  in elk verzoek, en stuur alle verzoeken naar de DataStoresConfig  repository.

Voor aanvullende eindpunten en gedrag, zie de [Cloud API-referentie](/docs/nl-nl/cloud/reference/features/configs)  en de [ervaring configuraties](/docs/nl-nl/cloud/guides/configs)  gids.

1.

Maak een concept via een PUT  verzoek dat je configuratie definieert. Als er al een concept bestaat, overschrijft dit verzoek het.

```

curl --location --request PUT 'https://apis.roblox.com/creator-configs-public-api/v1/configs/universes/<UNIVERSE_ID>/repositories/DataStoresConfig/draft:overwrite' \

	--header 'x-api-key: <API_KEY>' \

	--header 'Content-Type: application/json' \

	--data-raw '{

	"entries": {

		"user_data_templates": [

			{

				"key_template": {

					"data_store_type": "STANDARD",

					"data_store_name": "PlayerInventory",

					"key_pattern": "User_{UserId}",

					"scope_pattern": "Scope_{UserId}"

				}

			},

			{

				"key_template": {

					"data_store_type": "ORDERED",

					"data_store_name": "PlayerLeaderboard",

					"key_pattern": "User_{UserId}",

					"scope_pattern": "global"

				}

			},

			{

				"data_store_template": {

					"data_store_type": "STANDARD",

					"data_store_pattern": "Player_{UserId}_Save"

				}

			}

		]

	}

}'

```

2.

Verifieer je concept via een GET  verzoek om het concept op te halen en te bekijken voordat het live gaat.

```

curl --location --request GET 'https://apis.roblox.com/creator-configs-public-api/v1/configs/universes/<UNIVERSE_ID>/repositories/DataStoresConfig/draft' \

	--header 'x-api-key: <API_KEY>'

```

3.

Na verificatie, stuur dit POST  verzoek om te publiceren. De enige manier om deze actie ongedaan te maken, is door een eerdere versie te herstellen. Deze actie vereist ook dat het account dat aan de API-sleutel is gekoppeld, [in aanmerking komt om games te publiceren](https://en.help.roblox.com/hc/en-us/articles/203313890-How-to-Publish-Public-Experiences-on-Roblox) .

```

curl --location --request POST 'https://apis.roblox.com/creator-configs-public-api/v1/configs/universes/<UNIVERSE_ID>/repositories/DataStoresConfig/publish' \

	--header 'x-api-key: <API_KEY>' \

	--header 'Content-Type: application/json' \

	--data-raw '{

	"deploymentStrategy": "Immediate"

}'

```

4.

Na publicatie, bevestig dat de configuratie live is met dit GET  verzoek.

```

curl --location --request GET 'https://apis.roblox.com/creator-configs-public-api/v1/configs/universes/<UNIVERSE_ID>/repositories/DataStoresConfig/full' \

	--header 'x-api-key: <API_KEY>'

```

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

-

Hoofdlettergevoeligheid  — Gebruik de exacte {UserId}  token in je patronen. Varianten zoals {userId}  worden niet geaccepteerd.

-

Handmatige verificatie  — Vergelijk je patronen met je live Luau-gebruik met behulp van de [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager)  in de Creator Hub voordat je de configuratie publiceert.

-

Standaard scopes  — Als een gegevensopslagplaats de standaard scope gebruikt, stel scope_pattern  in op "global"  in de sleuteltemplate.

-

Test end-to-end flow op een testgame  — Voor volledige validatie van je templates, overweeg om een testgame en dummy-account te maken, deze te vullen met dummy-gegevens voor de User ID van dat account, RTBF aan te vragen op het dummy-account, en ervoor te zorgen dat de gegevens worden verwijderd zodra het account is verwerkt.

-

Bevestig verwijderingen  — Na onboarding op je live game, wanneer een RTBF-verzoek verschijnt in je Roblox-berichten, verifieer dat de bijbehorende gegevens binnen 30 dagen zijn verwijderd.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
