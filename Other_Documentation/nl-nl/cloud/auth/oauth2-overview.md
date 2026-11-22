<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/auth/oauth2-overview -->

OAuth 2.0 overzicht | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)

# OAuth 2.0 overzicht

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt apps bouwen of autoriseren die Open Cloud API's gebruiken om toegang te krijgen tot Roblox bronnen. Open Cloud biedt authenticatie voor deze apps met behulp van OAuth 2.0.

Als game-creator of groeps eigenaar

Je kunt veilig tools gebruiken die door anderen zijn gemaakt om je creatie productiviteit te verbeteren. De OAuth 2.0 autorisatielaag stelt je in staat om toestemming te geven aan apps van derden om toegang te krijgen tot jouw of de games van jouw groep zonder je inloggegevens en persoonlijke informatie te geven. Je selecteert de toegangsrechten van jouw specifieke Roblox-bronnen, en Roblox regelt het autorisatieproces voor jou met het OAuth 2.0 framework.

Je moet een 13+ account hebben om OAuth 2.0 apps te autoriseren.

Als app-ontwikkelaar

Je kunt apps maken voor jezelf en anderen in de Roblox-gemeenschap. OAuth 2.0 definieert de rollen die betrokken zijn bij het autorisatieproces, het protocol van hoe rollen met elkaar omgaan, en de autorisatieflows die je moet volgen om veilige en compatibele apps te ontwikkelen.

Je moet [ID geverifieerd](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie)  zijn om OAuth 2.0 apps te registreren en publiceren.

## [Rollen](#rollen)[](#rollen)

Het Open Cloud OAuth 2.0 protocol heeft de volgende rollen. Het is nuttig om de specifieke rollen te begrijpen voordat je leert hoe ze met elkaar omgaan in autorisatieflows.

-

Resource eigenaar : Een entiteit die in staat is toegang te verlenen tot een beschermde bron. Bijvoorbeeld, een creator die een app van derden toestaat om toegang te krijgen tot hun Roblox-bronnen via Open Cloud Web API's.

-

Resource server : Een Roblox-service die beschermde bronnen host en reageert op verzoeken van een resource eigenaar.

-

Client : Een app die toegang krijgt tot beschermde bronnen namens de resource eigenaar (met de toestemming van de eigenaar).

-

Autorisatie server : De Roblox-server die de identiteit van de resource eigenaar verifieert en toegangstokens aan de client uitgeeft.

## [Grant types](#grant-types)[](#grant-types)

Autorisatieflows, of grant types, zijn de stappen van acties die rollen uitvoeren tijdens het autorisatieproces. Roblox ondersteunt de OAuth 2.0 autorisatie code flow en de Proof Key for Code Exchange (PKCE) extensie, met verschillende implementatievereisten voor apps die in staat zijn of niet in staat zijn om client secrets op te slaan.

### [Autorisatie code flow](#autorisatie-code-flow)[](#autorisatie-code-flow)

Via de autorisatie code flow wisselt een client een autorisatiecode voor een toegangstoken en een verversingstoken om het autorisatieproces te voltooien in de volgende stappen:

1.

De client stuurt een autorisatieverzoek naar de Roblox autorisatie server.

2.

De autorisatie server verifieert de identiteit van de resource eigenaar.

3.

De autorisatie server ontvangt toestemming voor toegang tot specifieke Roblox bronnen van de resource eigenaar.

4.

De autorisatie server leidt de resource eigenaar terug naar de client met een autorisatiecode.

5.

De client vraagt een toegangstoken aan met de autorisatiecode bij de token endpoint.

6.

De client ontvangt een reactie van de token endpoint met een toegangstoken, een ID-token en een verversingstoken.

7.

De client haalt de toegestane bronnen op nadat hij het toegangstoken heeft ontvangen.

De volgende afbeelding beschrijft de interacties tussen rollen in de autorisatie code flow die je in de volgende secties zult lezen:

 ![](https://prod.docsiteassets.roblox.com/assets/open-cloud/protocol-flow.png)

### [Autorisatie code flow met PKCE](#autorisatie-code-flow-met-pkce)[](#autorisatie-code-flow-met-pkce)

De [PKCE extensie](https://www.rfc-editor.org/rfc/rfc7636)  van de autorisatie code flow helpt het risico te verminderen dat de autorisatiecode lekt en voorkomt cross-site request forgery (CSRF), een aanval die gebruikers misleidt om onbedoelde webverzoeken in te dienen. Deze flow voltooit het autorisatieproces met de volgende stappen:

1.

De client genereert een unieke en cryptografisch willekeurige sleutel genaamd een * code verifier*  voor elk autorisatieverzoek.

2.

De client voert een SHA-256 hash-algoritme uit op de code verifier om een * code challenge*  te genereren.

3.

Als de client:

-

Een [publieke client](/docs/nl-nl/cloud/auth/oauth2-develop#public-clients)  is, in plaats van de client secret te gebruiken, geeft hij de client ID en de code challenge door in het autorisatieverzoek.

-

Een [confidentiële client](/docs/nl-nl/cloud/auth/oauth2-develop#confidential-clients)  is, voegt hij de code challenge samen met de client ID en secret toe in het verzoek.

4.

De client stuurt een autorisatieverzoek naar de Roblox autorisatie server.

5.

De autorisatie server verifieert de identiteit van de resource eigenaar.

6.

De autorisatie server ontvangt toestemming voor toegang tot specifieke Roblox bronnen van de resource eigenaar.

7.

De autorisatie server leidt de resource eigenaar terug naar de client met een autorisatiecode.

8.

De client voegt de autorisatiecode en de originele code verifier toe aan het tokenverzoek naar de [token endpoint](/docs/nl-nl/cloud/auth/oauth2-reference#tokenuitwisseling) .

9.

De autorisatie server verifieert de autorisatiecode en de bijbehorende code verifier.

10.

De client ontvangt een reactie van de token endpoint met een toegangstoken, een ID-token en een verversingstoken.

11.

De client haalt de toegestane bronnen op nadat hij het toegangstoken heeft ontvangen.

## [OpenID Connect ondersteuning](#openid-connect-ondersteuning)[](#openid-connect-ondersteuning)

Roblox gebruikt [OpenID Connect (OIDC)](https://openid.net/connect/)  als een identiteitslaag bovenop het OAuth 2.0 protocol voor authenticatie om gevoelige accountinformatie te beschermen. OIDC stelt applicaties in staat om de identiteit van gebruikers te verifiëren en hun basis openbare profielinformatie te verkrijgen, zoals gebruikers-ID, gebruikersnamen, weergavenamen en profiel links.

Wanneer je [toestemmingsscopes toevoegt](/docs/nl-nl/cloud/auth/oauth2-registration#register-an-app)  aan je app op Creator Dashboard , zorg ervoor dat je de openid  identiteitscope selecteert voor het ontvangen van een ID-token in de tokenrespons als onderdeel van het authenticatieproces.

## [Registratie en implementatie](#registratie-en-implementatie)[](#registratie-en-implementatie)

Om een web- of mobiele app te implementeren die gebruikmaakt van de autorisatiecodeflow, moet je:

1.

[Registreer](/docs/nl-nl/cloud/auth/oauth2-registration)  je app bij Roblox. Dit stelt je in staat om een client ID en secret te verkrijgen om je app bij Roblox te registreren en oproepen naar je endpoints te doen.

2.

[Implementeer](/docs/nl-nl/cloud/auth/oauth2-develop)  de autorisatiecode flow. Voor een complete referentie van de OAuth 2.0 endpoints die je moet aanroepen, zie de [Authenticatie](/docs/nl-nl/cloud/auth/oauth2-reference)  referentie.

3.

Doorloop het [beoordelingsproces](/docs/nl-nl/cloud/auth/oauth2-registration#dien-in-voor-beoordeling)  om meer gebruikersquota te krijgen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
