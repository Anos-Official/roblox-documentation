<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/auth/oauth2-develop -->

OAuth 2.0 app-implementatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)

# OAuth 2.0 app-implementatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Open Cloud ondersteunt de OAuth 2.0-autorisatiestroom met en zonder [PKCE](/docs/nl-nl/cloud/auth/oauth2-overview#autorisatie-code-flow-met-pkce) , afhankelijk van of uw clients vertrouwelijk of openbaar zijn.

-

* Vertrouwelijke clients*  zijn apps die in staat zijn om inloggegevens vertrouwelijk te houden, zoals een website die veilig geheimen kan opslaan en ophalen op zijn backend.

-

* Openbare clients*  zijn apps die geen geheimen kunnen bewaren, zoals mobiele en webbrowser-apps.

We raden de OAuth 2.0-autorisatiecode-stroom met PKCE aan voor * alle*  clients en vereisen het voor openbare clients.

Bewaar het clientgeheim op een veilige plaats en stel het nooit bloot aan het publiek. Slechte actoren kunnen het gebruiken om uw applicatie te imiteren.

Om de autorisatiecode-stroom te implementeren, voert uw app de volgende stappen uit:

1.

Genereer een codeverifier en code-uitdaging (alleen PKCE). Dit stelt u in staat om een uitdaging in uw verzoeken op te nemen in plaats van het clientgeheim, wat de beveiliging verbetert.

2.

Stuur een GET -verzoek naar het autorisatie-eindpunt met de juiste parameters.

3.

Verwerk de autorisatiecallback. Nadat u autorisatie hebt verkregen, gebruikt u de autorisatiecode van Roblox in een omleidingsverzoek naar de URL die u hebt opgegeven tijdens het maken van de app. Parse de autorisatiecode voor later gebruik.

4.

Stuur een POST -verzoek naar het token-eindpunt met de autorisatiecode. Als het succesvol is, ontvangt u toegangstokens en vernieuwingstokens waarmee u API -aanroepen kunt doen.

5.

Roep een Open Cloud API aan die OAuth 2.0-authenticatie ondersteunt op basis van de referentiedocumentatie voor de bronnen die u wilt openen.

De volgende secties beschrijven elke stap in meer detail.

## [Genereer een code-uitdaging (alleen voor PKCE)](#genereer-een-code-uitdaging-alleen-voor-pkce)[](#genereer-een-code-uitdaging-alleen-voor-pkce)

Voordat u het autorisatieproces start, moet u een code-uitdaging genereren vanuit een codeverifier. U kunt bibliotheken of ingebouwde functies in de programmeertaal van uw keuze gebruiken om de codeverifier te maken, de hash te berekenen en Base64-codering uit te voeren om de code-uitdaging te genereren.

Bij het maken van de codeverifier, gebruik alleen niet-gereserveerde tekens, waaronder hoofdletters en kleine letters (A-Z, a-z), decimale cijfers (0-9), koppelteken (-), punt (.), onderstrepingsteken (_), en tilde (~), met een minimale lengte van 43 tekens en een maximale lengte van 128 tekens.

Het volgende voorbeeld laat zien hoe u Javascript kunt gebruiken om een codeverifier te maken en de code-uitdaging te genereren met behulp van het SHA-256-hashingalgoritme:

Genereer Code-uitdaging

```

const crypto = require('crypto');

// base64URL encode de verifier en uitdaging

function base64URLEncode(str) {

  return str.toString('base64')

      .replace(/\+/g, '-')

      .replace(/\//g, '_')

      .replace(/=/g, '');

}

// maak sha256-hash van de codeverifier

function sha256(buffer) {

  return crypto.createHash('sha256').update(buffer).digest(`base64`);

}

// maak een willekeurige codeverifier

var code_verifier = base64URLEncode(crypto.randomBytes(32));

// genereer een uitdaging vanuit de codeverifier

var code_challenge = base64URLEncode(sha256(code_verifier));

```

Voor PKCE heeft u zowel de codeverifier als de uitdaging nodig in latere stappen.

## [Constructie van de autorisatie-URL](#constructie-van-de-autorisatie-url)[](#constructie-van-de-autorisatie-url)

Zie de [referentiedocumentatie voor het autorisatie-eindpunt](/docs/nl-nl/cloud/auth/oauth2-reference#get-v1authorize)  voor volledige informatie over hoe u de autorisatie-URL kunt construeren.

Om het autorisatieproces voor de gebruiker te starten, construeert u een autorisatie-URL met de vereiste parameters:

-

client_id : De client-ID van uw app die u hebt verkregen na [het registreren van uw app](/docs/nl-nl/cloud/auth/oauth2-registration) .

-

redirect_uri : De omleidings-URI van uw app, het herinvoerpunt van uw app.

-

scope : De gevraagde scopes die de toegangsrechten definiëren die uw app nodig heeft in een spatie-gescheiden lijst.

-

response_type : Stel dit in op code  om de autorisatiecode-stroom aan te geven.

Vereist voor alleen PKCE

-

code_challenge : De code-uitdaging die is gegenereerd vanuit een codeverifier.

-

code_challenge_method : Stel deze parameterwaarde in op S256  om aan te geven dat de code-uitdaging is getransformeerd met behulp van het SHA-256-algoritme, de meest breed ondersteunde en veilige methode voor code-uitdaging.

-

state : Een ondoorzichtige, veilige willekeurige waarde om de status tussen het verzoek en de callback te behouden.

Vereist voor alleen niet-PKCE

-

client_secret : Het clientgeheim van uw app dat u hebt verkregen na [het registreren van uw app](/docs/nl-nl/cloud/auth/oauth2-registration) . Als u authenticatie met PKCE gebruikt, laat deze parameter dan weg. Uw autorisatieverzoek-URL moet goed geformatteerd zijn, zoals in het volgende voorbeeld:

Voorbeeld PKCE Autorisatie-URL

```

https://apis.roblox.com/oauth/v1/authorize?client_id=7290610391231237934964

    &code_challenge=PLEKKVCjdD1V_07wOKlAm7P02NC-LZ_1hQfdu5XSXEI

    &code_challenge_method=S256

    &redirect_uri=https://example.com/redirect

    &scope=openid%20profile

    &response_type=code

    &state=abc123

```

Wanneer gebruikers de URL bezoeken, worden ze door de autorisatie-stroom geleid. Als het succesvol is, leidt Roblox de gebruiker om naar de opgegeven redirect_uri .

## [Verwerk autorisatiecallbacks](#verwerk-autorisatiecallbacks)[](#verwerk-autorisatiecallbacks)

Wanneer een autorisatie-stroom succesvol is, ontvangt uw app een GET -verzoek van de Roblox-autorisatieserver op de redirect_uri  die u hebt opgegeven. In het verzoek ontvangt u de parameters code  (autorisatiecode) en state  (als u eerder een waarde hebt opgegeven).

-

De parameter code  bevat een autorisatiecode die de app kan inwisselen voor een toegangstoken van de autorisatieserver. De meeste backend servertalen hebben standaard manieren om queryparameters als gedecodeerde objecten te benaderen. U moet de parameter code  verkrijgen en deze gebruiken om toegangstokens in te wisselen.

-

De parameter state  is een ondoorzichtige waarde die u aanvankelijk in de autorisatieaanvraag hebt opgegeven. U kunt deze parameter gebruiken om de status of context van het autorisatieproces te behouden.

Bijvoorbeeld, u kunt een GET -verzoek ontvangen met de volgende URL als u uw omleidings-URI hebt opgegeven als https://example.com/redirect .

Voorbeeld Omleidings-URL

```

https://example.com/redirect?code=10c45PNuquKnFJ6pUcy5-fHkghEM6lSegm-7hj9mVEprub1dSDuStuKK_EAUXY7AHTD63xcnmvxSLthp-C8g3jzIGZVzuXSd20Y2dEYI9hx0LZmPg95ME4z2K03UheiZbroyXUjYyB3ReoMqobzDVPzyx6IS8kj2Uu-11Xq_0JiTYxtDatuqXRNIAmJT8gMJmbSyOLOP_vnDvbeMUiBsqCRrkTGVbWSwYSc8sTVVE-535kYdqQOgNjH1ffCoZLGl8YYxLnpb2CXJlRQPrcjkA&state=6789

```

Als de autorisatie mislukt, ontvangt uw app een GET -verzoek naar de opgegeven omleidings-URL met de parameters error , error_description  en state  (indien van toepassing).

-

De parameter error  geeft de specifieke OAuth 2.0-fout aan die is opgetreden tijdens het autorisatieproces.

-

De parameter error_description  biedt aanvullende details over de fout.

-

De parameter state  helpt uw app de status te behouden in het geval van een fout.

## [Wissel een autorisatiecode in voor toegangstokens](#wissel-een-autorisatiecode-in-voor-toegangstokens)[](#wissel-een-autorisatiecode-in-voor-toegangstokens)

Wanneer u de autorisatie code  hebt geparsed, wissel deze dan in voor tokens om toegang te krijgen tot gewenste Roblox-bronnen:

1.

Vraag een toegangstoken en vernieuwings-token aan door een POST -verzoek te sturen naar het [tokenwissel-eindpunt](/docs/nl-nl/cloud/auth/oauth2-reference#post-v1token) . Het verzoek moet de autorisatiecode, client-ID en de waarde van de codeverifier (PKCE) of clientgeheim (niet-PKCE) bevatten in x-www-form-urlencoded  formaat.

2.

Parse de toepasselijke tokens uit de ontvangen reactie. Het toegangstoken is 15 minuten geldig. Bewaar het vernieuwings-token veilig, meestal aan de serverzijde, zodat u het in de toekomst kunt gebruiken om nieuwe tokens te verkrijgen.

Voorbeeld Token Eindpunt Reactie

```

{

  "access_token": "eyJhbGciOiJFUzI1NiIsImtpZCI6IlBOeHhpb2JFNE8zbGhQUUlUZG9QQ3FCTE81amh3aXZFS1pHOWhfTGJNOWMiLCJ0eXAiOiJKV11234.eyJzdWIiOiIyMDY3MjQzOTU5IiwiYWlkIjoiM2Q2MWU3NDctM2ExNS00NTE4LWJiNDEtMWU3M2VhNDUyZWIwIiwic2NvcGUiOiJvcGVuaWQ6cmVhZCBwcm9maWxlOnJlYWQiLCJqdGkiOiJBVC5QbmFWVHpJU3k2YkI5TG5QYnZpTCIsIm5iZiI6MTY5MTYzOTY5OCwiZXhwIjoxNjkxNjQwNTk4LCJpYXQiOjE2OTE2Mzk2OTgsImlzcyI6Imh0dHBzOi8vYXBpcy5yb2Jsb3guY29tL29hdXRoLyIsImF1ZCI6IjcyOTA2MTAzOTc5ODc5MzQ5Nj1234.BjwMkC8Q5a_iP1Q5Th8FrS7ntioAollv_zW9mprF1ats9CD2axCvupZydVzYphzQ8TawunnYXp0Xe8k0t8ithg",

  "refresh_token": "eyJhbGciOiJkaXIiLCJlbmMiOiJBMjU2Q0JDLUhTNTEyIiwia2lkIjoidGpHd1BHaURDWkprZEZkREg1dFZ5emVzRWQyQ0o1NDgtUi1Ya1J1TTBBRSIsInR5cCI6IkpXVCJ9..nKYZvjvXH6msDG8Udluuuw.PwP-_HJIjrgYdY-gMR0Q3cabNwIbmItcMEQHx5r7qStVVa5l4CbrKwJvjY-w9xZ9VFb6P70WmXndNifnio5BPZmivW5QkJgv5_sxLoCwsqB1bmEkz2nFF4ANLzQLCQMvQwgXHPMfCK-lclpVEwnHk4kemrCFOvfuH4qJ1V0Q0j0WjsSU026M67zMaFrrhSKwQh-SzhmXejhKJOjhNfY9hAmeS-LsLLdszAq_JyN7fIvZl1fWDnER_CeDAbQDj5K5ECNOHAQ3RemQ2dADVlc07VEt2KpSqUlHlq3rcaIcNRHCue4GfbCc1lZwQsALbM1aSIzF68klXs1Cj_ZmXxOSOyHxwmbQCHwY7aa16f3VEJzCYa6m0m5U_oHy84iQzsC-_JvBaeFCachrLWmFY818S-nH5fCIORdYgc4s7Fj5HdULnnVwiKeQLKSaYsfneHtqwOc_ux2QYv6Cv6Xn04tkB2TEsuZ7dFwPI-Hw2O30vCzLTcZ-Fl08ER0J0hhq4ep7B641IOnPpMZ1m0gpJJRPbHX_ooqHol9zHZ0gcLKMdYy1wUgsmn_nK_THK3m0RmENXNtepyLw_tSd5vqqIWZ5NFglKSqVnbomEkxneEJRgoFhBGMZiR-3FXMaVryUjq-N.Q_t4NGxTUSMsLVEppkTu0Q6rwt2rKJfFGuvy3s12345",

  "token_type": "Bearer",

  "expires_in": 899,

  "id_token": "eyJhbGciOiJFUzI1NiIsImtpZCI6IkNWWDU1Mi1zeWh4Y1VGdW5vNktScmtReFB1eW15YTRQVllodWdsd3hnNzgiLCJ0eXAiOiJKV11234.eyJzdWIiOiIyMDY3MjQzOTU5IiwibmFtZSI6ImxpbmtzZ29hdCIsIm5pZ2tuYW1lIjoibGlua3Nnb2F0IiwicHJlZmVycmVkX3VzZXJuYW1lIjoibGlua3Nnb2F0IiwiY3JlYXRlZF9hdCI6MTYwNzM1NDIzMiwicHJvZmlsZSI6Imh0dHBzOi8vd3d3LnJvYmxveC5jb20vdXNlcnMvMjA2NzI0Mzk1OS9wcm9maWxlIiwib25jZWUiOiIxMjM0NSIsImp0aSI6IklELnltd3ZjTUdpOVg4azkyNm9qd1I5IiwibmJmIjoxNjkxNjM5Njk4LCJleHAiOjE2OTE2NzU2OTgsImlhdCI6MTY5MTYzOTY5OCwiaXNzIjoiaHR0cHM6Ly9hcGlzLnJvYmxveC5jb20vb2F1dGgvIiwiYXVkIjoiNzI5MDYxMDM5Nzk4NzkzNDk2NCJ9.kZgCMJQGsariwCi8HqsUadUBMM8ZOmf_IPDoWyQY9gVX4Kx3PubDz-Q6MvZ9eU5spNFz0-PEH-G2WSvq2ljDyg",

  "scope": "openid profile"

}

```

## [Maak een oproep naar een resource-methode](#maak-een-oproep-naar-een-resource-methode)[](#maak-een-oproep-naar-een-resource-methode)

Nu u het vereiste toegangstoken heeft, kunt u het gebruiken om geauthenticeerde oproepen naar resource-methoden te doen. Neem het toegangstoken op in de header van alle API-verzoeken om ze te autoriseren.

Bijvoorbeeld, u kunt testen of uw app correct functioneert door door de hele autorisatie-stroom te gaan en vervolgens een GET -verzoek te doen naar het [gebruikersinformatie-eindpunt](/docs/nl-nl/cloud/auth/oauth2-reference#get-v1userinfo)  met een toegangstoken. Zorg ervoor dat u de openid  of zowel de openid  als profile  scopes heeft voordat u dit eindpunt aanroept. Als het succesvol is, ziet de reactie van dat eindpunt er als volgt uit:

Voorbeeld Reactie Gebruikersinformatie

```

{

  "sub": "12345678",

  "name": "Jane Doe",

  "nickname": "robloxjanedoe",

  "preferred_username": "robloxjanedoe",

  "created_at": 1607354232,

  "profile": "https://www.roblox.com/users/12345678/profile"

}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
