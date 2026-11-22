<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/data-stores-manager -->

Data Stores Manager | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Data Stores Manager

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met de Data Stores Manager kun je je datastores, hun sleutelvermeldingen en hun opslaggebruik rechtstreeks op de Creator Hub doorbladeren en monitoren.

## [Toegang tot de Data Stores Manager](#toegang-tot-de-data-stores-manager)[](#toegang-tot-de-data-stores-manager)

Als je de eigenaar bent van een spel of de groeps eigenaar van een groepsspel, heb je standaard al volledige toegang tot de Data Stores Manager.

Om leden van je groep toegang te geven tot de Data Stores Manager, kun je [hen een van de volgende machtigingen geven](/docs/nl-nl/projects/groups#rollen-en-machtigingen) :

-

Data Stores bekijken  laat hen de pagina van de Data Stores Manager in de Creator Hub bekijken.

-

Data Stores bewerken  laat hen sleutels verwijderen.

-

Data Stores verwijderen  laat hen datastores verwijderen.

-

Ervaringen bewerken  geeft hen volledige toegang tot alle functionaliteit van de Data Stores Manager.

Om toegang te krijgen tot de Data Stores Manager:

1.

Selecteer een spel op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Ga naar Configuraties  > Data stores manager .

 ![Overzicht van de Data Stores Manager pagina met de Samenvatting sectie, de lijst met Data Stores en de lijst met Sleutels.](https://prod.docsiteassets.roblox.com/assets/data/data-store/Data-Stores-Manager-Page.png)

De Samenvatting  sectie van de Data Stores Manager pagina bevat de Totale Grootte  en de Opslaglimiet  van je datastores. Totale Grootte wordt berekend door het aantal bytes op te tellen dat door alle bestaande sleutels in je spel wordt verbruikt, en Opslaglimiet wordt berekend op basis van het aantal gebruikers gedurende de levensduur van je spel. Voor meer informatie over opslaglimieten, zie [Limieten](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#limieten) .

Als je Totale Grootte je Opslaglimiet overschrijdt, worden je Geschatte Maandelijkse Kosten  weergegeven in je Samenvatting en toont het een schatting van de impact van het gebruik dat je quotum heeft overschreden. Voor tips over hoe je je opslagverbruik kunt verminderen, zie [Best practices](/docs/nl-nl/cloud-services/data-stores/best-practices) .

## [Bekijk datastores en sleutels](#bekijk-datastores-en-sleutels)[](#bekijk-datastores-en-sleutels)

Als je spel meer dan 100 datastores heeft, zijn de grootte van de datastore en het aantal sleutels niet beschikbaar in de lijst met datastores.

De Data Stores  lijst toont de naam, grootte en het aantal sleutels voor alle datastores in je spel. Je kunt deze lijst filteren door een prefix in de zoekbalk in te voeren.

Om verder in te zoomen op elke specifieke datastore, kun je:

-

Een datastore selecteren uit de lijst met datastores om een lijst van alle sleutels in die datastore weer te geven.

-

Een prefix in de zoekbalk invoeren om de lijst met sleutels te filteren. De prefix moet beginnen met de scope naam.

-

Een sleutelvermelding selecteren om de waarde, metadata, versiegeschiedenis, status en wanneer deze voor het laatst is bijgewerkt weer te geven.

-

Zowel een sleutelvermelding als een versie selecteren en op Versies vergelijken  klikken om de huidige sleutelvermelding versie te vergelijken met de versie die je hebt geselecteerd.

-

Een eerdere versie van een sleutel selecteren en op Terugzetten  klikken om naar die versie terug te gaan. Je moet bewerkingsrechten hebben om dit te doen. Terugzetten naar een eerdere versie werkt de lijst voorwaardelijk bij en schrijft een nieuwe versie met de waarde van de versie die je eerder hebt geselecteerd.

 ![Vergelijking van twee sleutelvermeldingen in een datastore.](https://prod.docsiteassets.roblox.com/assets/data/data-store/Data-Stores-Manager-Compare-Versions.png)

## [Verwijder datastores en sleutels](#verwijder-datastores-en-sleutels)[](#verwijder-datastores-en-sleutels)

Wanneer je een datastore of sleutel plant voor permanente verwijdering, zullen pogingen om te lezen of te schrijven naar de vermeldingen falen nadat de backend caches zijn verlopen. Vanwege caching in de backend service kunnen pogingen om vermeldingen van verwijderde datastores te lezen tot 24 uur na verwijdering blijven slagen, en pogingen om vermeldingen te schrijven kunnen enkele minuten blijven slagen.

Om een datastore of sleutel voor permanente verwijdering te plannen:

1.

Selecteer een spel op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Ga in de navigatie aan de linkerkant naar Configuraties  > Data stores manager .

3.

Klik op het Actie  menu naast het item dat je wilt verwijderen.

4.

Klik op Markeren voor Verwijdering .

Er is een cooldown-periode tussen het moment dat je een datastore of sleutel verwijdert en wanneer dat item daadwerkelijk wordt verwijderd. Tijdens deze cooldown-periode kun je de verwijdering ongedaan maken en het item terugzetten naar zijn normale staat.

Om een datastore te herstellen, klik je op het Actie  menu naast de datastore die je wilt herstellen en klik je vervolgens op Herstellen , of roep de [UndeleteDataStore](/docs/nl-nl/cloud/reference/DataStore#Cloud_UndeleteDataStore)  methode aan vanuit de Open Cloud API.

Om een sleutel te herstellen, roep je de [UpdateAsync](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  methode aan vanuit de Engine API of de [UpdateDataStoreEntry](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_UpdateDataStoreEntry__Using_Universes_DataStores)  methode vanuit de Open Cloud API aan.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
