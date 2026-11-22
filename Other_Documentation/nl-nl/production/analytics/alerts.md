<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/alerts -->

Meldingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Meldingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Meldingen  stellen u in staat om proactief kritieke prestatie- en gegevensopslagmetingen voor uw ervaring te monitoren en real-time meldingen te ontvangen wanneer ze uw gedefinieerde drempels overschrijden. In plaats van handmatig dashboards te controleren, kunt u meldingen instellen die u automatisch waarschuwen wanneer metingen zoals crashpercentages stijgen, het geheugengebruik te hoog wordt of de framerates dalen.

Meldingen zijn beschikbaar voor elke ervaring die voldoet aan de geschiktheidseisen voor [prestatiemetingen](/docs/nl-nl/production/analytics/performance)  (100+ dagelijkse actieve gebruikers).

Bijvoorbeeld, de volgende workflow is een typische manier om meldingen te gebruiken om prestatieregressies op te vangen:

1.

Maak een melding  - Stel een melding in voor "Client crashpercentage is boven de 5%" met een duur van 5 minuten en kritieke ernst.

2.

Voeg een webhook toe  - Verbind met de PagerDuty of Discord webhook van uw team.

3.

Duw uw update  - Zet uw nieuwe versie live.

4.

Ontvang de melding  - Als het crashpercentage gedurende 5 opeenvolgende minuten boven de 5% stijgt, wordt uw team onmiddellijk op de hoogte gesteld met de meetwaarde en een link naar het dashboard.

5.

Onderzoek en los op  - Klik op de dashboardlink in de webhookpayload om de prestatiegrafieken te bekijken en het probleem te diagnosticeren.

U kunt tot 20 meldingen per ervaring maken. Het maken van meldingen vereist de Meldingen maken en configureren  toestemming.

## [Bekijk de meldingenpagina](#bekijk-de-meldingenpagina)[](#bekijk-de-meldingenpagina)

Om toegang te krijgen tot de meldingenpagina, moet u ofwel de eigenaar van de ervaring zijn of de Bekijk alle analyses  [toestemmingen](#toestemmingen)  hebben.

1.

Selecteer een spel op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Navigeer in de navigatie aan de linkerkant naar Configuraties  > Meldingen .

Het Configuratie  tabblad stelt u in staat om meldingsregels te maken en te beheren. Gebruik de Analyses  pagina om de meldingsgeschiedenis, actieve meldingen en gebeurtenissen te bekijken.

## [Toestemmingen](#toestemmingen)[](#toestemmingen)

Meldingen vereisen specifieke toestemmingen voor verschillende acties:

| Actie | | Vereiste toestemming |
| --- | --- |
| Meldingen maken, bewerken, verwijderen of in- en uitschakelen | | Meldingen maken en configureren |
| Bekijk de meldingenanalyses pagina | | Bekijk alle analyses |
| Maak ervaring-niveau webhooks | | Lijst, maak, update en verwijder webhooks |

Voor groepsbezit ervaringen krijgt iedereen met Ervaringen bewerken  toestemming standaard de Meldingen maken en configureren  toestemming, zodat teams onmiddellijk meldingen kunnen instellen. Als u wilt beperken wie meldingen kan maken of beheren, intrekt u de toestemming voor specifieke rollen onder de ervaring Toestemmingen  pagina. Gebruikers die Meldingen maken en configureren  hebben, ontvangen ook standaard de toestemming voor het beheren van webhooks.

## [Maak meldingen](#maak-meldingen)[](#maak-meldingen)

Om een melding te maken, klikt u op Maak  op de meldingsconfiguratiepagina. U kunt ook een melding rechtstreeks vanuit een grafiek op het [Prestatie dashboard](/docs/nl-nl/production/analytics/performance)  maken door het overflow-menu van de grafiek te openen en Maak een melding  te selecteren, wat de melding vooraf invult met de meetwaarde en filters van die grafiek.

 ![Bestaande meldingen dashboard met maak knop.](https://prod.docsiteassets.roblox.com/assets/analytics/alerts/create.png)

### [Meldingsvelden](#meldingsvelden)[](#meldingsvelden)

Elke melding heeft de volgende configuratieopties.

| Veld | | Beschrijving |
| Naam | | Een unieke naam voor de melding die wordt weergegeven op meldingen, annotaties en dashboards. |
| Beschrijving | | Een optionele beschrijving om extra context te bieden. |
| Meetwaarde | | De doelmeetwaarde om te monitoren. |
| Tijd granulariteit | | Hoe vaak de meetwaarde wordt geëvalueerd (minuut, half uur, per uur of dagelijks). |
| Triggerconditie | | De voorwaarde die de melding activeert (bijv. waarde > 500) |
| Filters | | Optionele filters om de meetwaarde te verfijnen, zoals plaatsversie, besturingssysteem of platform. Alle filters die beschikbaar zijn op het dashboard worden ondersteund. |
| Opsplitsing | | Optionele opsplitsing om te controleren of de voorwaarde voor elk segment afzonderlijk is voldaan. |
| Duur | | Hoe vaak de voorwaarde opeenvolgend moet worden voldaan voordat de melding afgaat (1-10). |
| Ernst | | Het ernstniveau (kritiek, gemiddeld of laag). |
| Leveringskanaal | | Waar meldingsmeldingen naartoe moeten worden gestuurd. Zie [Webhook levering](#webhook-levering) . |

### [Ondersteunde meetwaarden](#ondersteunde-meetwaarden)[](#ondersteunde-meetwaarden)

Meldingen ondersteunen alle prestatiemetingen die beschikbaar zijn op het [Prestatie dashboard](/docs/nl-nl/production/analytics/performance) , inclusief:

-

Client framerate

-

Client crashpercentage

-

Client geheugengebruik (GB)

-

Client geheugengebruik percentage

-

Onverwachte out-of-memory exits

-

Server CPU-tijd

-

Server framerate

-

Server geheugengebruik (GB)

-

Gelijktijdige gebruikers

-

Sessietijd

Meldingen ondersteunen ook gegevensopslagmetingen, zodat u het opslaggebruik en de prestaties van de gegevensopslag naast de runtime-prestaties van uw ervaring kunt monitoren.

### [Triggercondities](#triggercondities)[](#triggercondities)

U kunt een van de twee types triggercondities instellen:

-

Meetwaarde  - Activeert wanneer de meetwaarde een statische numerieke drempel overschrijdt. De waarde gebruikt dezelfde eenheid als de meetwaarde (percentage, milliseconden, MB, enz.).

-

Periode-over-periode verandering  - Activeert wanneer de wijzigingssnelheid van de meetwaarde een percentage drempel overschrijdt.

-

Week-over-week  - Controleert de procentuele verandering tussen dezelfde tijd vorige week (bijv. 17:00 deze vrijdag vs. 17:00 vorige vrijdag).

-

Dag-over-dag  - Controleert de procentuele verandering tussen dezelfde tijd gisteren (bijv. 9:00 vandaag vs. 9:00 gisteren).

-

Uur-over-uur  - Controleert de procentuele verandering tussen het meest recente uur en het vorige uur (bijv. 9:05 vs. 8:05).

Bijvoorbeeld, u kunt een meetwaardeconditie instellen zoals "client crashpercentage is boven de 5%" of een periode-over-periode conditie zoals "uurlijkse verandering is boven de 50%."

### [Duur](#duur)[](#duur)

De duurinstelling bepaalt hoe lang de triggerconditie continu moet worden voldaan voordat de melding afgaat. Dit helpt om ruis van momentane fluctuaties te verminderen. Als u 1 kiest, gaat de melding af zodra één datapunt aan uw voorwaarde voldoet. Als u 5 kiest, moeten vijf opeenvolgende datapunten aan de voorwaarde voldoen. Voor meldingen met minutengranulariteit is de minimale duur 5 minuten om ruis te verminderen.

### [Ernstniveaus](#ernstniveaus)[](#ernstniveaus)

Elke melding heeft een ernstniveau dat is opgenomen in het meldingsbericht en wordt weergegeven met een onderscheidende kleur.

| Ernst | | Gebruiksscenario |
| Kritiek | | Urgente problemen die onmiddellijke actie vereisen, zoals een piek in het crashpercentage. |
| Gemiddeld | | Opmerkelijke regressies die snel moeten worden onderzocht. |
| Laag | | Kleine veranderingen die het waard zijn om te volgen, maar niet onmiddellijk actie vereisen. |

## [Webhook levering](#webhook-levering)[](#webhook-levering)

Meldingen komen binnen via ervaring-niveau webhooks. Wanneer een melding afgaat of herstelt, wordt er een HTTP POST-verzoek verzonden naar uw geconfigureerde webhook-URL met een JSON-payload. Het bericht zelf is ook JSON, gewikkeld in het AlertMessage  veld als een enkele string, zoals:

```

{

  "NotificationId": "11111abc-111a-1a2a-ab1a-abc1a1a111a1",

  "EventType": "AnalyticsAlert",

  "EventTime": "2026-06-15T22:05:10.8590762Z",

  "EventPayload": {

    "TargetType": "Universe",

    "TargetId": "1234567890",

    "AlertMessage": "{\n  \"summary\": \"[♟️] Spel is hersteld\",\n  \"metric\": \"PeakConcurrentPlayers\",\n  \"universe_id\": \"1234567890\",\n  \"evaluation_time_utc\": \"2026-06-15T22:04:47Z\",\n  \"alert_history\": \"https://create.roblox.com/dashboard/creations/experiences/1234567890/alerts?tab=AlertConfiguration-Analytics&utm_medium=webhook&utm_campaign=alert_resolved\"\n}"

  }

}

```

Het AlertMessage.summary  veld bevat ofwel het woord "afgegaan" wanneer de melding wordt geactiveerd of het woord "hersteld" wanneer de meetwaarde terugkeert naar een normale staat.

U kunt webhooks gebruiken om te integreren met externe tools zoals PagerDuty of Slack voor team-brede zichtbaarheid.

### [Stel een webhook in](#stel-een-webhook-in)[](#stel-een-webhook-in)

1.

Selecteer een spel op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Navigeer in de navigatie aan de linkerkant naar Configuraties  > Webhooks , en klik vervolgens op de knop Webhook toevoegen .

De webhook-URL komt van uw provider. Bijvoorbeeld, een Slack-URL ziet er waarschijnlijk zo uit:

```

https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX

```

3.

Voer uw webhook-URL en een naam in.

4.

OPTIONEEL

 Voeg een geheim toe, wat kan helpen om ervoor te zorgen dat de verzoeken die u ontvangt van Roblox komen.

5.

OPTIONEEL

 Gebruik de knop Testrespons  om te controleren of uw service een voorbeeldverzoek kan ontvangen.

6.

Klik op Wijzigingen opslaan .

7.

Bij het maken of bewerken van een melding, selecteert u uw webhook onder het veld Leveringskanaal .

Het maken van ervaring-niveau webhooks vereist de Lijst, maak, update en verwijder webhooks  [toestemming](#toestemmingen) .

## [Monitor meldingen](#monitor-meldingen)[](#monitor-meldingen)

Het Analyses  tabblad op de meldingenpagina biedt een gecentraliseerd overzicht van uw meldingsgeschiedenis en huidige status:

-

Geactiveerde gebeurtenissen  - Een grafiek die het aantal meldingen dat in de loop van de tijd afgaat toont. U kunt het tijdsbereik aanpassen, zoeken op meldingsnaam en filteren op ernst.

-

Actieve meldingen  - Een tabel die momenteel actieve (afgaande) meldingen toont.

-

Geschiedenis  - Een chronologische log van alle meldingsgebeurtenissen binnen het geselecteerde tijdsbereik.

 ![Screenshot van het analyses tabblad dat een geschiedenis van geactiveerde gebeurtenissen toont.](https://prod.docsiteassets.roblox.com/assets/analytics/alerts/monitor.png)

### [Grafiekannotaties](#grafiekannotaties)[](#grafiekannotaties)

Wanneer een melding actief afgaat, verschijnt er een bereikannotatie op de bijbehorende meetwaarde grafiek op het Prestatie dashboard. De annotatie toont de naam van de melding en beslaat de duur van de afgaande periode.

Annotaties verschijnen alleen wanneer de grafiek dezelfde filters heeft toegepast als de melding. Als uw melding opsplitsingsfilters heeft, worden annotaties alleen voor de totale lijn weergegeven.

 ![Screenshot die grafiekannotaties toont.](https://prod.docsiteassets.roblox.com/assets/analytics/alerts/annotations.png)

## [Ervaringsoverzicht](#ervaringsoverzicht)[](#ervaringsoverzicht)

Actieve meldingen (meldingen die zijn afgegaan en nog niet zijn hersteld) verschijnen in de meldingslade op uw ervaring Overzicht  pagina. De lade toont de vijf meest recente actieve meldingen met hun tijdstempel, naam en huidige meetwaarde. Klik op Bekijk alles  om naar de volledige meldingenanalyses pagina te navigeren.

 ![Overzicht pagina van de ervaring met actieve meldingen](https://prod.docsiteassets.roblox.com/assets/analytics/alerts/experience-overview.png)

## [Beste praktijken voor meldingen](#beste-praktijken-voor-meldingen)[](#beste-praktijken-voor-meldingen)

Deze tips kunnen u helpen het meeste uit meldingen te halen en te voorkomen dat uw webhook-eindpunten worden overspoeld met meldingen:

-

Voorkom valse alarmen met duur  - Vermijd het instellen van uw duur op 1 voor zeer volatiele meetwaarden zoals sessietijd. Een plotselinge toestroom van spelers die zich aanmelden of assets tegelijkertijd laden kan tijdelijke pieken veroorzaken. Een duur van 5 instellen zorgt ervoor dat een melding alleen afgaat als het probleem aanhoudt.

-

Gebruik segmentopsplitsingen efficiënt  - In plaats van meerdere individuele meldingen voor Android, iOS en PC te maken, kunt u een enkele melding maken en de Opsplitsing  functie gebruiken. De melding evalueert elk platform afzonderlijk en specificeert waar het probleem zich voordoet in de webhookpayload.

-

Stel eerst een basislijn vast  - Voordat u uw drempels instelt, bekijk uw bestaande analyses grafieken over de afgelopen 7 tot 14 dagen. Als uw normale crashpercentage rond de 1,2% schommelt, overweeg dan om uw meldingsdrempel in te stellen op 2,5% of 3%. Uw meetwaarden ruimte geven voor natuurlijke fluctuaties voorkomt valse alarmen.

-

Gebruik beschrijvende, gestructureerde namen  - Omdat meldingsnamen direct in uw webhookpayloads en annotaties worden geïnjecteerd, maakt het gebruik van een duidelijke formule zoals meetwaarde - context  (bijv. Hoog client crashpercentage - mobiel) het gemakkelijk voor uw team om problemen in één oogopslag te triageren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
