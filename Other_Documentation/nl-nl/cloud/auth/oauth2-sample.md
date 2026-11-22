<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/auth/oauth2-sample -->

OAuth 2.0 voorbeeldapp | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)

# OAuth 2.0 voorbeeldapp

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox biedt een Node.js voorbeeldapp die laat zien hoe je OAuth 2.0 kunt gebruiken om gebruikers in te laten loggen op hun Roblox-accounts en berichten te verzenden in hun games. Deze app gebruikt de [autorisatiecode-stroom * zonder*  PKCE](/docs/nl-nl/cloud/auth/oauth2-overview#grant-types)  en is dus alleen geschikt voor vertrouwelijke clients, zoals privéservers.

 [Krijg de Code](https://prod.docsiteassets.roblox.com/assets/open-cloud/open-cloud-nodejs-sample-oauth2-main.zip)

Na het downloaden van het .zip -bestand, pak het uit naar een eigen map.

## [Registreer de app](#registreer-de-app)[](#registreer-de-app)

De eerste stap om de app in te stellen is om deze te [registreren op de Roblox-website](/docs/nl-nl/cloud/auth/oauth2-registration)  en de client-ID en het geheim ergens veilig te kopiëren. Volg vervolgens de standaardregistratiestappen met deze instellingen:

1.

Onder Machtigingen , voeg de openid , profile  en universe-messaging-service:publish  scopes toe.

2.

Onder Redirect-URL's , voeg de http://localhost:3000/oauth/callback  redirect toe. Als je een niet-standaardpoort voor je app wilt gebruiken, geef deze hier op.

## [Stel omgevingsvariabelen in](#stel-omgevingsvariabelen-in)[](#stel-omgevingsvariabelen-in)

In plaats van ze in de code op te slaan (niet aanbevolen), gebruikt de app omgevingsvariabelen voor je client-ID en geheim. Het proces voor het toevoegen van omgevingsvariabelen verschilt per besturingssysteem.

Op Windows, voer de volgende PowerShell-opdrachten uit:

```

$env:ROBLOX_CLIENT_ID='your_client_id_here'

$env:ROBLOX_CLIENT_SECRET='your_client_secret_here'

$env:ROBLOX_PORT=3000 # Optioneel. Standaard is 3000.

```

Op Mac en de meeste Linux-distributies, voer deze opdrachten uit in de terminal:

```

export ROBLOX_CLIENT_ID=your_client_id_here

export ROBLOX_CLIENT_SECRET=your_client_secret_here

export ROBLOX_PORT=3000 # Optioneel. Standaard is 3000.

```

Als je een niet-standaardpoort hebt opgegeven in de redirect-URL bij het registreren van je app, zorg er dan voor dat je de ROBLOX_PORT  variabele toevoegt.

Deze opdrachten stellen alleen omgevingsvariabelen in voor de duur van je terminalsessie. Als je deze variabelen elke keer wilt laden wanneer je een nieuw terminalvenster opent, voeg de opdrachten toe aan je shell-configuratiebestand, zoals .zshrc  of .bashrc . Veel hostingdiensten hebben functies om je te helpen omgevingsvariabelen aan je servers toe te voegen.

## [Installeer afhankelijkheden](#installeer-afhankelijkheden)[](#installeer-afhankelijkheden)

De app heeft een aantal afhankelijkheden, zichtbaar in package.json . Om ze te installeren, voer uit:

```

npm ci

```

## [Voer de app uit](#voer-de-app-uit)[](#voer-de-app-uit)

Om de app te starten, voer uit:

```

npm start

```

Navigeer vervolgens naar http://localhost:3000  (of je niet-standaardpoort) in een webbrowser.

De app leidt je onmiddellijk om naar het inlogscherm van Roblox, waar je kunt inloggen, de machtigingen die de app aanvraagt kunt verifiëren en op Bevestigen en Toegang Geven  kunt klikken.

Roblox leidt je vervolgens terug naar localhost , waar je kunt zien dat de app nu enkele minimale gebruikersinformatie weergeeft, een link terug naar je profiel op Roblox, en velden die je kunt gebruiken om berichten in je games te verzenden.

### [Over de app](#over-de-app)[](#over-de-app)

In grote lijnen voert index.js  de volgende bewerkingen uit:

1.

Start een nieuwe webserver met express .

2.

Haalt de Roblox OpenID Connect (OIDC) configuratie op, die eindpunten voor autorisatie, gebruikersinformatie, enz. bevat. Voor meer informatie over deze eindpunten, zie [OAuth 2.0 authenticatie](/docs/nl-nl/cloud/auth/oauth2-reference) .

3.

Creëert een nieuwe Open ID-client met openid-client  en je opgeslagen referenties. Deze client vereenvoudigt het proces van het correct vormen en verzenden van HTTP-verzoeken naar de OAuth 2.0 eindpunten aanzienlijk.

4.

Definieert de routes voor de app, inclusief omleidingen voor de inlog- en uitlogstromen en de OAuth 2.0 callback.

5.

Na een succesvolle login, slaat het de verschillende tokens op als cookies, samen met enkele minimale gebruikersinformatie die het weergeeft als HTML met hulp van getHomeHtml.js .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
