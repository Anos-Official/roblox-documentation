<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/auth/oauth2-reference -->

OAuth 2.0-authenticatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)

# OAuth 2.0-authenticatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

OAuth 2.0-authenticatie is een bèt Kenmerk dat onderhevig kan zijn aan wijzigingen voor toekomstige releases. Alle Open Cloud-eindpunten ondersteunen ook [API-sleutelauthenticatie](/docs/nl-nl/cloud/auth/api-keys) .

Voor complete implementatiehandleidingen en informatie over OAuth 2.0, inclusief een voorbeeldapp, zie de [OAuth 2.0-overzicht](/docs/nl-nl/cloud/auth/oauth2-overview) .

Dit document beschrijft eindpunten die je aanroept om de OAuth 2.0 autorisatiecode-stroom te implementeren, evenals andere eindpunten die nuttig zijn voor het implementeren van authenticatie in je apps.

Basis-URL

```

https://apis.roblox.com/oauth

```

Eindpunten

```

GET v1/authorize

POST v1/token

POST v1/token/introspect

POST v1/token/resources

POST v1/token/revoke

GET v1/userinfo

GET .well-known/openid-configuration

```

## [Autorisatie](#autorisatie)[](#autorisatie)

### [GET  v1/authorize](#get-v1authorize)[](#get-v1authorize)

Verkrijgt autorisatie van de gebruiker om zich te authentiseren met hun Roblox-account. Verwacht een geldige autorisatie-URL die is opgebouwd met de gespecificeerde parameters. Dit eindpunt ondersteunt PKCE-autorisatie.

#### Queryparameters

| Naam | | Beschrijving | | Vereist | | Voorbeeld |
| --- | --- |
| client_id | | De client-ID van de app. | | ja | | 816547628409595165403873012 |
| redirect_uri | | De URL waar gebruikers naartoe worden omgeleid na het voltooien van de autorisatie-stroom. | | ja | | https://www.roblox.com/example-redirect |
| scope | | De gevraagde scopes, gescheiden door spaties. Gebruik de openid  scope om een ID-token te ontvangen. Gebruik de openid  en profile  scope om meer gebruikersinformatie te verkrijgen. | | ja | | openid profile |
| response_type | | De referenties die de app wil terugkrijgen. De standaard is het autorisatiecode-granttype. | | ja | | none , code |
| prompt | | Geeft aan welke authenticatie- en toestemmingspagina's aan gebruikers worden getoond. Bepaalde schermen zijn vereist voor apps van derden en kunnen niet worden overgeslagen. | | nee | | none , login , consent , select_account |
| nonce | | Het cryptografische nummer dat de token aan de client bindt. | | nee | | <random_value_1> |
| state | | Een ondoorzichtig waarde die cross-site request forgery voorkomt, een type kwaadaardige aanval. Wordt teruggegeven aan de app na autorisatie. | | nee | | <app-provided-opaque-value> |
| code_challenge | | De resulterende string van het toepassen van de code_challenge_method  op de code_verifier . | | nee | | Base64-URL-gecodeerde string |
| code_challenge_method | | De functie die wordt toegepast op de code_verifier . | | nee | | S256 |

#### Verzoek

Voorbeeldverzoek voor het doorverwijzen naar de autorisatie-stroom

```

https://apis.roblox.com/oauth/v1/authorize?client_id=816547628409595165403873012&redirect_uri=https://my-app.com/redirect&scope=openid&response_type=code&nonce=12345&state=6789

```

#### Antwoord

Na het aanroepen van dit eindpunt, wordt de gebruiker omgeleid naar de opgegeven omleidings-URL met de autorisatiecode in een code  queryparameter. De autorisatiecode:

-

Heeft een levensduur van één minuut.

-

Kan slechts één keer worden ingewisseld.

-

Is ongeldig na één gebruik.

## [Tokenuitwisseling](#tokenuitwisseling)[](#tokenuitwisseling)

Om tokens te verkrijgen voor toegang tot API's, wissel een autorisatiecode  in voor een set van vertrouwelijke tokens. Alle token-eindpunten ondersteunen twee soorten clientauthenticatie:

1.

HTTP Basic Authentication Scheme met een autorisatieheader: Authorization: Basic Base64 encoded(<client_id>:<client_secret>) .

2.

Client-ID en geheim in de aanvraagbody als parameters.

De volgende lijst beschrijft de verschillende tokens die je van dit eindpunt ontvangt.

-

Toegangstoken  - Vertegenwoordigt de autorisatie van een maker of gebruiker voor een app van derden om toegang te krijgen tot hun beschermde Roblox-resources. Het is een string die een specifieke scope, levensduur en andere toegangseigenschappen aangeeft. Zodra de Roblox-autorisatieserver een toegangstoken aan een app uitgeeft, is het token:

-

Geldig voor 15 minuten.

-

Kan meerdere keren worden gebruikt voordat het verloopt.

-

Kan ongeldig worden gemaakt voordat het verloopt als een app-gebruiker de autorisatie intrekt.

-

Vernieuwtoken  - Vernieuwt een autorisatiesessie. Een app kan het vernieuwtoken gebruiken om een nieuwe set tokens te verkrijgen, die een toegangstoken, een vernieuwtoken en een ID-token omvat. Een vernieuwtoken:

-

Is geldig voor 90 dagen.

-

Kan slechts één keer worden gebruikt voordat het verloopt om tokens te vernieuwen.

-

Kan ongeldig worden gemaakt voordat het verloopt als een app-gebruiker de autorisatie intrekt.

-

ID-token  - Biedt bewijs dat de identiteit van een gebruiker is geverifieerd. De inhoud hangt af van de gevraagde scopes en kan basisgebruikersinformatie bevatten, inclusief de Roblox-weergavenaam en gebruikersnaam van een gebruiker. Het ID-token is alleen voor identiteitsauthenticatiedoeleinden en biedt geen toegang tot enige Roblox-resources.

### [POST  v1/token](#post-v1token)[](#post-v1token)

Verkrijg een set tokens met een autorisatiecode.

#### Verzoek

(x-www-form-urlencoded)

| Sleutel | | Waarde |
| code | | <autorisatiecode> |
| code_verifier | | <pkce code verifier waarde> |
| grant_type | | authorization_code |
| client_id | | <client_id> |
| client_secret | | <client_secret> |

Voorbeeldverzoek voor het verkrijgen van een token

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'client_id=840974200211308101' \

--data-urlencode 'client_secret=RBX-CR9...St12L' \

--data-urlencode 'grant_type=authorization_code' \

--data-urlencode 'code=yCnq4ofX1...XmGpdx'

```

#### Antwoord

Voorbeeldantwoord voor het verkrijgen van een token

```

{

  "access_token": "...",

  "refresh_token": "...",

  "token_type": "Bearer",

  "expires_in": 899,

  "scope": "universe-messaging-service:publish"

}

```

### [POST  v1/token](#post-v1token-1)[](#post-v1token-1)

Verkrijg een set tokens met een vernieuwtoken.

#### Verzoek

(x-www-form-urlencoded)

| Sleutel | | Waarde |
| grant_type | | refresh_token |
| refresh_token | | <refresh_token> |
| client_id | | <client_id> |
| client_secret | | <client_secret> |

Voorbeeldverzoek voor het vernieuwen van een token

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'grant_type=refresh_token' \

--data-urlencode 'refresh_token=Ujfstayclfdlbm...BGydlsnU' \

--data-urlencode 'client_id=840974200211308101' \

--data-urlencode 'client_secret=RBX-CR9...St12L'

```

#### Antwoord

Voorbeeldantwoord voor het vernieuwen van een token

```

{

  "access_token": "...",

  "refresh_token": "...",

  "token_type": "Bearer",

  "expires_in": 899,

  "scope": "universe-messaging-service:publish"

}

```

### [POST  v1/token/introspect](#post-v1tokenintrospect)[](#post-v1tokenintrospect)

Ontvang informatie over een token. Verifieert of het token momenteel geldig is en nog niet is verlopen. Nuttig voor stateless validatie. Gebruik alleen als de API waar je toegang toe hebt geen resource vereist, zoals de Assets API, of als je gewoon specifieke claims van het token wilt zien.

Zelfs als de gebruiker de autorisatie die aan het toegangstoken is gekoppeld, heeft ingetrokken, toont het eindpunt het toegangstoken nog steeds als valid: true  omdat het controleert of het token actief is op basis van de levensduur (typisch 15 minuten voor toegangstokens).

#### Verzoek

(x-www-form-urlencoded)

| Sleutel | | Waarde |
| token | | <access_token> , <refresh_token>  of <id_token> |
| client_id | | <client_id> |
| client_secret | | <client_secret> |

Voorbeeldverzoek voor het introspecteren van een token

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token/introspect' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'token=eyjlflabtfl...4gxqYBG' \

--data-urlencode 'client_id=840974200211308101' \

--data-urlencode 'client_secret=RBX-CR9...St12L'

```

#### Antwoord

Voorbeeldantwoord voor het introspecteren van een token

```

{

  "active": true,

  "jti": "RT.2GcjvTduKzk6QY9tjTfm",

  "iss": "https://apis.roblox.com/oauth/",

  "token_type": "Bearer",

  "client_id": "840974200211308101",

  "aud": "4239311013248676173",

  "sub": "1516563360",

  "scope": "universe-messaging-service:publish",

  "exp": 1676394509,

  "iat": 1660842510

}

```

### [POST  v1/token/resources](#post-v1tokenresources)[](#post-v1tokenresources)

Controleer of een token toegang kan krijgen tot een specifieke resource door de lijst van gebruikersresources te verkrijgen waarvoor de gebruiker toestemming heeft gegeven. Dit is nuttig voor stateful validatie.

#### Verzoek

(x-www-form-urlencoded)

| Sleutel | | Waarde |
| token | | <access_token> |
| client_id | | <client_id> |
| client_secret | | <client_secret> |

Voorbeeldverzoek voor het verkrijgen van tokenresources

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token/resources' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'token=eyjlflabtfl...4gxqYBG' \

--data-urlencode 'client_id=840974200211308101' \

--data-urlencode 'client_secret=RBX-CR9...St12L'

```

#### Antwoord

De waarde U  in ids  geeft aan dat een scope toegang heeft verleend tot een resource die eigendom is van de autoriserende owner .

Voorbeeldantwoord voor het verkrijgen van tokenresources

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

        },

        "creator": {

          "ids": ["U"]

        }

      }

    }

  ]

}

```

### [POST  v1/token/revoke](#post-v1tokenrevoke)[](#post-v1tokenrevoke)

Intrek een autorisatiesessie met behulp van het verstrekte vernieuwtoken.

#### Verzoek

(x-www-form-urlencoded)

| Sleutel | | Waarde |
| token | | <refresh_token> |
| client_id | | <client_id> |
| client_secret | | <client_secret> |

Voorbeeldverzoek voor het intrekken van een token

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token/revoke' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'token=Ujfstayclfdlbm...BGydlsnU' \

--data-urlencode 'client_id=840974200211308101' \

--data-urlencode 'client_secret=RBX-CR9...St12L'

```

#### Antwoord

200 OK  met een leeg antwoord

## [Gebruikersinformatie](#gebruikersinformatie)[](#gebruikersinformatie)

### [GET  /v1/userinfo](#get-v1userinfo)[](#get-v1userinfo)

Krijgt de Roblox-gebruikers-ID en andere gebruikersmetadata.

#### Verzoek

Autorisatieheader : Authorization: Bearer <access_token>

Voorbeeldverzoek voor het verkrijgen van gebruikersinformatie

```

curl --location --request GET 'https://apis.roblox.com/oauth/v1/userinfo' \

--header 'Authorization: Bearer eyjlflabtfl...4gxqYBG'

```

#### Antwoord

Je kunt de sub  waarde gebruiken om de gebruiker uniek te identificeren. Gebruikers kunnen hun Roblox-gebruikersnaam en weergavenaam wijzigen, dus gebruik ze niet als unieke identificatoren om naar gebruikers in je app te verwijzen.

| Claim | | Beschrijving |
| sub | | Roblox-gebruikers-ID. |
| name | | Roblox-weergavenaam. |
| nickname | | Roblox-weergavenaam. |
| preferred_username | | Roblox-gebruikersnaam. |
| created_at | | Aanmaaktijd van het Roblox-account als een Unix-timestamp. |
| profile | | URL van het Roblox-accountprofiel. |
| picture | | Afbeelding van de Roblox-avatar. Kan null zijn als de afbeelding van de avatar nog niet is gegenereerd of is gemodereerd. |

Voorbeeldgebruiker met profielscope

```

{

  "sub": "1516563360",

  "name": "exampleuser",

  "nickname": "exampleuser",

  "preferred_username": "exampleuser",

  "created_at": 1584682495,

  "profile": "https://www.roblox.com/users/1516563360/profile",

  "picture": "https://tr.rbxcdn.com/03dc2a9abe7b1aacaaf93ea46d5c0646/150/150/AvatarHeadshot/Png"

}

```

Voorbeeldgebruiker zonder profielscope

```

{

  "sub": "1516563360"

}

```

## [Ontdekking](#ontdekking)[](#ontdekking)

Het OpenID Connect (OIDC) Discovery Document is een JSON-document dat metadata bevat over de configuratiedetails van Open Cloud, inclusief een lijst van identiteitsgerelateerde scopes en claims die worden ondersteund. Je kunt het gebruiken om informatie over Open Cloud OAuth 2.0-eindpunten en configuratie dynamisch te ontdekken, zoals het autorisatie-eindpunt, token-eindpunt en openbare sleutelset.

Nadat je het Discovery Document hebt opgehaald en opgehaald van de Discovery document URI, kun je ofwel handmatig velden in de respons inspecteren om de informatie te verifiëren, of je kunt je eigen aangepaste bibliotheek maken die velden in de responschema aan velden in de responschema koppelt om je workflow te automatiseren.

### [GET  .well-known/openid-configuration](#get-well-knownopenid-configuration)[](#get-well-knownopenid-configuration)

#### Antwoord

Alle Discovery Document-antwoorden volgen hetzelfde schema als het volgende voorbeeldantwoord.

Niet alle onderstaande scopes en claims zijn beschikbaar voor makers van apps van derden, aangezien sommige alleen door officiële Roblox-apps kunnen worden gebruikt.

Voorbeeldantwoord Discovery Document

```

{

  "issuer": "https://apis.roblox.com/oauth/",

  "authorization_endpoint": "https://apis.roblox.com/oauth/v1/authorize",

  "token_endpoint": "https://apis.roblox.com/oauth/v1/token",

  "introspection_endpoint": "https://apis.roblox.com/oauth/v1/token/introspect",

  "revocation_endpoint": "https://apis.roblox.com/oauth/v1/token/revoke",

  "resources_endpoint": "https://apis.roblox.com/oauth/v1/token/resources",

  "userinfo_endpoint": "https://apis.roblox.com/oauth/v1/userinfo",

  "jwks_uri": "https://apis.roblox.com/oauth/v1/certs",

  "registration_endpoint": "https://create.roblox.com/dashboard/credentials",

  "service_documentation": "https://create.roblox.com/docs/reference/cloud",

  "scopes_supported": [

    "openid",

    "profile",

    "email",

    "verification",

    "credentials",

    "age",

    "premium",

    "roles"

  ],

  "response_types_supported": ["none", "code"],

  "subject_types_supported": ["public"],

  "id_token_signing_alg_values_supported": ["ES256"],

  "claims_supported": [

    "sub",

    "type",

    "iss",

    "aud",

    "exp",

    "iat",

    "nonce",

    "name",

    "nickname",

    "preferred_username",

    "created_at",

    "profile",

    "email",

    "email_verified",

    "verified",

    "age_bracket",

    "premium",

    "roles",

    "internal_user"

  ],

  "token_endpoint_auth_methods_supported": [

    "client_secret_post",

    "client_secret_basic"

  ]

}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
