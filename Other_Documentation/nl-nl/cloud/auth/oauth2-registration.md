<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/auth/oauth2-registration -->

OAuth 2.0 app registratie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)

# OAuth 2.0 app registratie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het registreren van je OAuth 2.0-app stelt deze in staat om toegang te krijgen tot Roblox-resources. Na registratie wijst Roblox de app een unieke client-ID en geheim toe die je kunt gebruiken om autorisatie van gebruikers te verkrijgen om toegang te krijgen tot hun Roblox-informatie en -resources.

Je kunt alleen apps registreren voor individuele accounts of groepen die je bezit.

## [Registreer je app](#registreer-je-app)[](#registreer-je-app)

Om een app te registreren:

1.

Ga in het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  naar de [OAuth 2.0 Apps](https://create.roblox.com/dashboard/credentials?activeTab=OAuthTab)  pagina.

2.

Klik op de knop App Aanmaken .

3.

Voer een geldige en wereldwijd unieke Applicatienaam  in.

4.

Lees en ga akkoord met de Roblox Gebruiksvoorwaarden  en klik op Aanmaken .

5.

Kopieer en bewaar de Client-ID  en Geheim  op een veilige plaats. Na het sluiten van de pagina heb je geen toegang meer tot het geheim en kun je alleen een nieuwe genereren. Nadat je een app hebt geregistreerd, kun je nog steeds toegang krijgen tot en de andere eigenschappen van de app bewerken.

6.

Klik op Doorgaan naar Bewerken  om je app te configureren, wat in de volgende secties wordt beschreven.

## [Configureer algemene informatie](#configureer-algemene-informatie)[](#configureer-algemene-informatie)

Zodra je je app hebt [geregistreerd](#registreer-je-app) , moet je de algemene informatie configureren, inclusief:

-

Een beschrijving, die zichtbaar is voor iedereen in de Roblox-gemeenschap.

-

Een thumbnail-afbeelding voor je app. De aanbevolen bestandsgrootte is minimaal 150x150 pixels.

-

Een Invoerl link  als toegangspunt van je app, zoals de homepage van de website van de app.

-

Een Privacyvoorwaarden-URL  en een Gebruiksvoorwaarden-URL  voor eindgebruikers om te lezen voordat ze je app autoriseren. Elke URL moet HTTPS zijn en mag niet meer dan 256 tekens bevatten.

Je kunt deze sectie overslaan tijdens de ontwikkeling en het testen van de app, maar je moet deze tijdens het beoordelingsproces voltooien om je app aan gebruikers te publiceren.

## [Voeg machtigingen toe](#voeg-machtigingen-toe)[](#voeg-machtigingen-toe)

Om een goede toegangscontrole en beveiliging binnen je app te waarborgen, moet je Machtigingsscopes  toevoegen. Er zijn twee soorten machtigingsscopes beschikbaar:

-

Identiteits-scopes  voor authenticatie, zoals openid  voor gebruikers-ID's en profile  voor de volledige profielen. Als je de profile  scope selecteert, moet je ook openid  selecteren.

-

API-specifieke machtigingsscopes , zoals asset:read  voor de leesmachtiging van assets. Selecteer alleen het minimum aantal scopes dat je nodig hebt voor je app.

Selecteer eerst de App-categorie  die het beste bij je app past:

-

Accountkoppelingshulpmiddelen  helpen bij het vergemakkelijken van accountkoppeling tussen Roblox en een externe app voor het in kaart brengen van gebruikersprofielen.

-

Creatie- en productiviteits-tools  zijn digitale diensten of producten die voornamelijk worden gebruikt voor het creëren en bewerken van inhoud, en het beheren van de levenscyclus van ervaringen.

-

Analyse- en inzichttools  stellen ontwikkelaars in staat om gegevens over hun apps, ervaringen, assets of gebruikers te analyseren.

-

Gebruikershulpmiddelen  verbeteren de UI, toegankelijkheid of algehele ervaring van het gebruik van Roblox.

De beschikbare machtigingsscopes worden bijgewerkt om alleen de scopes voor de geselecteerde categorie weer te geven. Van elke app wordt verwacht dat deze het minimum aantal scopes aanvraagt dat nodig is voor zijn functie. De set scopes voor een app moet onder een enkele app-categorie vallen die is vermeld in het [Creator Third-Party App-beleid](https://en.help.roblox.com/hc/en-us/articles/37924211313044-Creator-Third-Party-App-Policy) .

## [Voeg omleidings-URL's toe](#voeg-omleidings-urls-toe)[](#voeg-omleidings-urls-toe)

Omleidings-URL's  zijn de herinvoerpunt van je app waar gebruikers naartoe worden omgeleid wanneer ze hun app hebben geautoriseerd. Zorg ervoor dat je omleidings-URL's aan de volgende vereisten voldoen:

-

Alle omleidings-URL's moeten in een van de volgende vormen zijn:

-

Gewone HTTPS, bijvoorbeeld: https://www.example.com .`

-

Paden op localhost met HTTP of HTTPS (zelfondertekend certificaat) voor lokale debugdoeleinden, bijvoorbeeld:

-

http://localhost:80

-

https://localhost:80

-

Aangepaste schema's voor specifieke applicaties of doeleinden, bijvoorbeeld:

-

my-app-scheme:/

-

my-app-scheme://foo/bar/...

-

my-app://action?param1=value1&param2=value2

-

De maximale lengte van een omleidings-URL is 256 tekens.

-

Je kunt tot 10 omleidings-URL's toevoegen. Met meerdere omleidings-URL's kun je testomgevingen hebben en gebruikers toestaan om tussen twee sites te migreren zonder downtime.

Je kunt deze stap overslaan tijdens de app-registratie en later de omleidings-URL's toevoegen wanneer je een testbare versie van je app hebt.

## [Dien in voor beoordeling](#dien-in-voor-beoordeling)[](#dien-in-voor-beoordeling)

Om de kans te minimaliseren dat kwaadaardige apps de gemeenschap schaden, maakt het registreren van een app deze niet breed toegankelijk. In plaats daarvan blijft het in privémode  met een limiet van 10 unieke gebruikers. Deze modus is nuttig voor testen en debuggen binnen je team.

Als je de gebruikersbasis voor je app wilt uitbreiden, moet je deze in de openbare modus publiceren door deze ter beoordeling in te dienen:

1.

Ga naar de [OAuth 2.0 apps](https://create.roblox.com/dashboard/credentials?activeTab=OAuthTab)  pagina.

2.

Klik op de knop Bewerken en Publiceren  voor de app die je wilt publiceren.

3.

Vul alle vereiste informatie in, inclusief de demovideo en beschrijving, en klik vervolgens op de knop Beoordelen en Publiceren . Een bericht met beperkingen op de machtigingen van je app tijdens de wachtperiode voor beoordeling verschijnt.

4.

Klik op Indienen voor Beoordeling .

De volgende informatie is vereist voor je indiening:

-

Een openbare Demovideo  link die niet langer is dan 1 minuut en voldoet aan de volgende vereisten:

-

Begint met de gebruiker die is uitgelogd en toont de exacte gebruikersactie, zoals het klikken op Inloggen met Roblox , die de OAuth-toestemmingsdialoog activeert. De video moet de volledige autorisatiestroom tonen via de omleiding terug naar je app, inclusief inhoud in je oorspronkelijke app na de omleiding.

-

Toont dezelfde registratiedetails die je met je indiening verstrekt.

-

Een rechtvaardiging waarin wordt uitgelegd waarom je app in de geselecteerde categorie hoort en hoe deze de aangevraagde machtigingsscopes gebruikt.

Roblox gebruikt je demovideo en rechtvaardiging alleen om je indiening te beoordelen en maakt ze niet openbaar. Vraag alleen de minimum machtigingsscopes aan die je app nodig heeft. Roblox keurt scopes voor geplande of toekomstige functionaliteit niet goed.

Terwijl je app-beoordeling in behandeling is, kun je geen andere verzoeken indienen of bewerken totdat het huidige beoordelingsverzoek is goedgekeurd of afgewezen. Je app blijft in privémode tijdens de beoordeling. Wanneer je app is goedgekeurd, schakelt deze over naar de openbare modus, en kun je deze niet terugzetten naar de privémode.

Ongeacht of je app is goedgekeurd of afgewezen, ontvang je een e-mailmelding van het resultaat wanneer de beoordeling is voltooid.

## [Bewerk en verwijder je app](#bewerk-en-verwijder-je-app)[](#bewerk-en-verwijder-je-app)

Je kunt je app bewerken of verwijderen met de volgende stappen als deze niet onder beoordeling staat:

1.

Ga naar de [OAuth 2.0 apps](https://create.roblox.com/dashboard/credentials?activeTab=OAuthTab)  pagina.

2.

Klik op Bewerken  of Verwijderen  voor de gewenste app.

-

Als je ervoor kiest om een app te bewerken, volg dan dezelfde stappen en vereisten van [registratie](#registreer-je-app) .

-

Als je ervoor kiest om een app te verwijderen, klik dan op Ja, Verwijderen  om de verwijdering te bevestigen. Nadat je een app hebt verwijderd, kun je deze niet herstellen.

Het wijzigen van de algemene informatie van je app of omleidings-URL's vereist niet dat gebruikers de app opnieuw autoriseren. Als je echter machtigingsscopes toevoegt of wijzigt, moet je autorisatie voor de nieuwe machtigingen van je gebruikers verkrijgen en een nieuwe set tokens verwerven. Als je geen autorisatie voor de nieuwe scopes verkrijgt, kan je app de bestaande tokens blijven gebruiken, maar is deze beperkt tot de vorige scopes.

Voor apps in privémode werkt het systeem automatisch je bewerkingen bij met je gebruikers. Voor apps in openbare modus moet je de app opnieuw [indienen voor beoordeling](#dien-in-voor-beoordeling)  om deze wijzigingen weer te geven. Anders slaat het systeem de niet-gepubliceerde wijzigingen voor je op zonder deze aan de gemeenschap vrij te geven.

 Je kunt een kopie van je openbare app klonen en deze in privémode houden voor iteratief testen en debuggen. Dit zorgt voor een gecontroleerde omgeving waarin je veilig wijzigingen kunt aanbrengen en eventuele problemen kunt oplossen voordat je de app ter beoordeling indient.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
