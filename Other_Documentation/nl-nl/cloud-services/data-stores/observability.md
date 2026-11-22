<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/observability -->

Gegevensopslag observability | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Gegevensopslag observability

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het gegevensopslag observability-dashboard biedt realtime grafieken over je aanvraaghoeveelheden en je gebruik ten opzichte van toekomstige gegevensopslaglimieten, en stelt je in staat om de aanvraaggegevens te filteren op standaard of geordende gegevensopslag.

![Een afbeelding die het aanvraag aantal per API-dashboard in de Creator Hub toont.](https://prod.docsiteassets.roblox.com/assets/data/data-store/Data-Store-API.png)

## [Toegang tot het dashboard](#toegang-tot-het-dashboard)[](#toegang-tot-het-dashboard)

Het gegevensopslagdashboard is beschikbaar voor elk spel dat [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  gebruikt, maar je moet ofwel de eigenaar van het spel zijn of [analytische groepsrechten](/docs/nl-nl/production/analytics/analytics-dashboard#grant-group-permission)  hebben om toegang te krijgen tot het dashboard.

1.

Navigeer naar de [Creations](https://create.roblox.com/dashboard/creations)  pagina op de Creator Hub .

2.

Selecteer onder het Creator Hub  dropdownmenu je account of de groep die het doelspel bezit.

3.

Selecteer het spel.

4.

Selecteer in het Monitoring  dropdownmenu Data Stores .

## [Beschikbare grafieken](#beschikbare-grafieken)[](#beschikbare-grafieken)

-

Opslaggebruik Bytes  over de hoeveelheid gegevensopslag en limiet die momenteel beschikbaar is voor het geselecteerde universum.

-

Aanvraag aantal per API  over het aantal API-aanvragen per minuut per API-methode, zoals [DataStore:SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync)  of [OrderedDataStore:GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync) .

-

Aanvraag aantal per Status  over het aantal API-aanvragen per [responsstatus](#responsstatuscodes) .

-

Aanvraag per API x Status  over responsstatussen die zijn teruggegeven door alle of een specifieke API-methode.

-

Lezen Aanvraag Type Quota Gebruik  over het aantal lees-API-methode-aanroepen tegen toekomstige leescategorie-limieten.

-

Schrijven Aanvraag Type Quota Gebruik  over het aantal schrijf-API-methode-aanroepen tegen toekomstige schrijfcategorie-limieten.

-

Lijst Aanvraag Type Quota Gebruik  over het aantal lijst-API-methode-aanroepen tegen toekomstige lijstcategorie-limieten.

-

Verwijder Aanvraag Type Quota Gebruik  over het aantal verwijder-API-methode-aanroepen tegen toekomstige verwijdercategorie-limieten.

Gebruik de selector bovenaan de pagina om te filteren op standaard of geordende gegevensopslag. De standaardweergave omvat alleen standaard gegevensopslag.

Gebruik de Verkennen  knop naast elke grafiek om die metriek in detail te bekijken, de huidige periode te vergelijken met eerdere periodes, of die metriek op te splitsen in de beschikbare categorieën.

Elke grafiek bevat gegevens voor de afgelopen 30 dagen, en je kunt kiezen om een aangepast tijdsbereik te bekijken met de selector bovenaan de pagina. Als je een tijdsbereik selecteert dat eerder is dan 30 dagen, retourneert het systeem een Aanvraag Mislukt  fout.

Gegevens van de meest recente drie minuten kunnen onvolledig zijn, dus het is normaal om een daling aan het einde van de grafieken te zien.

Opslaggebruik en limiet worden weergegeven in bytes, waarbij 1 kilobyte 1024 bytes is.

## [Responsstatuscodes](#responsstatuscodes)[](#responsstatuscodes)

De grafieken Aanvraag aantal per Status  en Aanvragen per API x Status  van het dashboard bevatten statuscodes van API-responsen die je kunt gebruiken om gebruik te begrijpen en fouten op te lossen. Voor een tabel die al deze statuscodes (behalve 200 OK ) opsomt en beschrijft, zie [Foutcodes](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#foutcode-referentie) .

## [Servicelimieten](#servicelimieten)[](#servicelimieten)

Voor informatie over huidige limieten, gebruiksquota en toekomstige limieten, zie [Limieten](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#limieten) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
