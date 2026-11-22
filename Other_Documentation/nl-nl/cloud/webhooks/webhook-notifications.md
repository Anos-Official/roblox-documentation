<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/webhooks/webhook-notifications -->

Webhookmeldingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Webhookmeldingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In plaats van handmatig alle gebeurtenissen in je game en verzoeken van gebruikers te monitoren, kun je webhooks instellen om real-time meldingen te ontvangen op een derde-partij messagingtool of je eigen aangepaste eindpunt dat HTTP-verzoeken kan ontvangen. Dit helpt je om je meldingsbeheerworkflow te automatiseren en de handmatige inspanning bij het afhandelen van meldingen te verminderen.

Momenteel ondersteunt Roblox volledig webhookmeldingen voor Discord en Slack. Het gebruik van webhooks met andere derde-partij tools brengt het risico met zich mee dat niet alle meldingen worden ontvangen.

## [Webhookworkflow](#webhookworkflow)[](#webhookworkflow)

Webhooks verzenden real-time meldingen of gegevens tussen twee verschillende applicaties of diensten, zoals Roblox en een derde-partij messagingtool. In tegenstelling tot traditionele API's, die vereisen dat je een clientapplicatie instelt om verzoeken naar een server te sturen om gegevens te ontvangen, verzenden webhooks gegevens naar je client-eindpunt zodra er een gebeurtenis plaatsvindt. Ze zijn nuttig voor het automatiseren van workflows tussen Roblox en derde-partij applicaties die je gebruikt voor samenwerking met je team, omdat ze real-time gegevensdeling en verwerking mogelijk maken.

Zodra je een webhook hebt ingesteld, wanneer een doelgebeurtenis zich voordoet, stuurt Roblox een verzoek naar de webhook-URL die je hebt opgegeven. De webhook-URL leidt het verzoek vervolgens door naar je ontvangende applicatie of aangepaste eindpunt, die actie kan ondernemen op basis van de gegevens die in de webhookpayload zijn opgenomen. Dit kan het wissen van gegevens voor [RTBF](/docs/nl-nl/production/publishing/RTBF-and-creators)  naleving omvatten, het verzenden van een bevestiging naar de gebruiker, of het activeren van een andere gebeurtenis.

## [Ondersteunde triggers](#ondersteunde-triggers)[](#ondersteunde-triggers)

Roblox ondersteunt momenteel de volgende gebeurtenistriggers.

### [Abonnement](#abonnement)[](#abonnement)

-

Abonnement Herbevestigd  - Wanneer een gebruiker zich opnieuw abonneert op een abonnement, wordt er een bericht verzonden met het abonnement en de abonnee.

-

Abonnement Verlengd  - Wanneer een gebruiker een abonnement verlengt, wordt er een bericht verzonden met het abonnement en de abonnee.

-

Abonnement Terugbetaald  - Wanneer een gebruiker een terugbetaling voor hun abonnement ontvangt, wordt er een bericht verzonden met het abonnement en de abonnee.

-

Abonnement Aangekocht  - Wanneer een gebruiker een abonnement aanschaft, wordt er een bericht verzonden met het abonnement en de abonnee.

-

Abonnement Geannuleerd  - Wanneer een gebruiker een [abonnement](/docs/nl-nl/production/monetization/subscriptions)  annuleert, wordt er een bericht verzonden met het abonnement en de abonnee, evenals de reden die voor de annulering is opgegeven.

Voor meer informatie over abonnementsevents en hun velden, zie de [Abonnement](/docs/nl-nl/cloud/reference/Subscription)  referentie.

### [Naleving](#naleving)[](#naleving)

-

Recht op Verwijdering / Verzoek om Verwijdering  - Wanneer een gebruiker zijn recht uitoefent om zijn persoonlijke informatie permanent te laten verwijderen onder toepasselijke wereldwijde gegevensbeschermings- en privacyregelgeving. Meer informatie is te vinden in [RTBF en Creators](/docs/nl-nl/production/publishing/RTBF-and-creators) .

### [Handel](#handel)[](#handel)

-

Handelsproductorder Terugbetaald  - Wanneer een gebruiker een terugbetaling voor zijn handelsproductorder heeft ontvangen, of de bestelling is geannuleerd.

-

Handelsproductorder Betaald  - Wanneer een gebruiker voor zijn handelsproductorder heeft betaald. Houd er rekening mee dat dubbele webhookgebeurtenissen mogelijk zijn, dus je moet gebeurtenissen dedupliceren met behulp van de unieke handelsorder-ID.

### [Terugbetalingen](#terugbetalingen)[](#terugbetalingen)

-

Transactie Terugbetaald  - Wanneer een gebruiker een transactie terugbetaalt, wordt er een bericht verzonden met de transactie en de terugbetaalde gebruiker. Deze trigger dekt ontwikkelaarsproducten, passen, privéservers en betaalde toegang. Het omvat geen abonnementen. De EventPayload  bevat:

-

De gebruikers-ID van de koper.

-

Het producttype en product-ID.

-

Het bedrag in Robux. Dit is de oorspronkelijke prijs van het product, niet het bedrag dat de koper heeft betaald.

-

Het universum en de plaats waar de aankoop is gedaan.

-

De transactie- of ontvangst-ID.

-

De tijd van de terugbetaling.

Wanneer een pas of avataritem wordt terugbetaald via de Roblox Klantenservice, trekt Roblox automatisch het eigendom van het item in. Voor ontwikkelaarsproducten bestaat het voordeel alleen in de code van je ervaring, dus je moet deze melding gebruiken om het verleende voordeel, zoals valuta of boosts, zelf uit de opgeslagen gegevens van de speler te verwijderen. Hetzelfde geldt voor eventuele extra functionaliteit die je ervaring biedt bovenop de basispas of het item.

### [Experimenten](#experimenten)[](#experimenten)

-

Vroeg Schade Detectie  - Wanneer een experiment [kritische schade](/docs/nl-nl/production/experiments#vroegtijdige-schade-metrics)  ervaart tijdens de eerste 24 uur, wordt er een bericht verzonden met het experiment, de schadelijke metriek en de lift.

## [Webhooks configureren op Creator Dashboard](#webhooks-configureren-op-creator-dashboard)[](#webhooks-configureren-op-creator-dashboard)

Om meldingen via webhooks te ontvangen, moet je een webhook configureren die zich abonneert op bepaalde gebeurtenissen voor het triggeren van meldingen. Voor groepsbezit games kunnen alleen groepsleden de webhookmeldingen configureren en ontvangen.

Als je webhooks instelt en persoonlijke gegevens verwerkt, zorg er dan voor dat ze voldoen aan de toepasselijke gegevensbeschermings- en privacyregelgeving. Zie [RTBF en Creators](/docs/nl-nl/production/publishing/RTBF-and-creators)  voor meer informatie.

Om een webhook in te stellen:

1.

Selecteer je ervaring op [Creator Hub](https://create.roblox.com/) .

2.

Navigeer in de linker navigatie naar Configuraties  > Webhooks .

3.

Klik op de knop Webhook Toevoegen .

De webhook-URL komt van je provider. Een Slack-URL ziet er bijvoorbeeld waarschijnlijk zo uit:

```

https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX

```

4.

Voer je webhook-URL en een naam in.

5.

OPTIONEEL

 Voeg een geheim toe, wat helpt om ervoor te zorgen dat de meldingen die je ontvangt van Roblox komen. Voor meer informatie, zie [Verifieer webhookbeveiliging](#verifieer-webhookbeveiliging) .

6.

Kies een of meer opties uit de lijst van [ondersteunde triggers](#ondersteunde-triggers)  van gebeurtenissen waarvoor je meldingen wilt ontvangen.

7.

OPTIONEEL

 Gebruik de knop Testrespons  om te controleren of je service een voorbeeldverzoek kan ontvangen.

8.

Klik op Wijzigingen Opslaan .

Momenteel kun je in totaal tot 5 webhooks configureren.

## [Webhook-URL's instellen](#webhook-urls-instellen)[](#webhook-urls-instellen)

Je kunt een aangepast HTTP-service-eindpunt instellen als je webhook-URL, op voorwaarde dat het aan de volgende vereisten voldoet:

-

Het moet openbaar toegankelijk zijn voor het afhandelen van verzoeken.

-

Het moet POST-verzoeken kunnen afhandelen.

-

Het moet binnen 5 seconden op het verzoek kunnen reageren met een 2XX-respons.

-

Het moet HTTPS-verzoeken kunnen afhandelen.

Wanneer je eindpunt een POST-verzoek ontvangt, moet het in staat zijn om:

-

De details die nodig zijn over de melding uit de body van het POST-bericht te extraheren.

-

De body van het POST-bericht te lezen met de algemene details over de melding en specifieke details met betrekking tot het type gebeurtenis op de melding.

Voor meer informatie over het schema van POST-verzoeken die je moet afhandelen, zie het [Payloadschema](#payloadschema) .

### [Beleid voor herhaalde afleverfouten](#beleid-voor-herhaalde-afleverfouten)[](#beleid-voor-herhaalde-afleverfouten)

Wanneer een webhookmelding niet op je opgegeven URL kan aankomen vanwege fouten zoals onbeschikbaarheid van het eindpunt, probeert Roblox het bericht 5 keer opnieuw te verzenden naar de geconfigureerde URL met een vaste venstergrootte. Als de melding na 5 pogingen nog steeds niet kan worden afgeleverd, stopt Roblox met het proberen te verzenden van de melding en gaat ervan uit dat de URL niet langer geldig is. In deze situatie moet je je webhookconfiguratie bijwerken met een nieuwe URL die bereikbaar is en meldingen kan ontvangen. Om te troubleshooten en te bevestigen dat je webhook-URL succesvol meldingen kan ontvangen, zie [Test webhooks](#test-webhooks) .

### [Vereisten van derden](#vereisten-van-derden)[](#vereisten-van-derden)

Derde-partij tools hebben meestal hun eigen vereisten voor webhooks die je moet volgen bij het instellen van je webhook-URL. Je kunt deze vereisten vinden door te zoeken naar het trefwoord "webhook" op de ondersteunings- of documentatiesite van de doeltool. Voor de ondersteunde derde-partij tools, zie het volgende:

-

[Discord Helpcentrum](https://support.discord.com/hc/en-us)

-

[Slack API Referentie](https://api.slack.com/)

## [Test webhooks](#test-webhooks)[](#test-webhooks)

Je kunt testen of de webhook die je hebt geconfigureerd succesvol meldingen kan ontvangen op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) :

1.

Navigeer naar de configuratiepagina voor [Webhooks](https://create.roblox.com/settings/webhooks) .

2.

Selecteer de webhook die je wilt testen uit de lijst van geconfigureerde webhooks.

3.

Klik op het potloodpictogram naast de doelwebhook.

4.

Klik op de knop Testrespons .

Het systeem verzendt dan een SampleNotification  evenement, dat de Gebruikers-ID  van de gebruiker die de melding heeft getriggerd, bevat, zoals hier weergegeven:

SampleNotification schema

```

{

  "NotificationId": "string",

  "EventType": "SampleNotification",

  "EventTime": "2023-12-30T16:24:24.2118874Z",

  "EventPayload": {

    "UserId": 1

  }

}

```

Als je je webhook integreert met een derde-partij service, kun je deze testen met de derde-partij URL om te bevestigen dat de service succesvol meldingen kan ontvangen van je webhook. Als je een geheim opgeeft bij het configureren van de webhook, genereert het ook een roblox-signature  die je kunt gebruiken om de roblox-signature  logica te testen.

## [Verifieer webhookbeveiliging](#verifieer-webhookbeveiliging)[](#verifieer-webhookbeveiliging)

Nadat je je server hebt geconfigureerd om payloads te ontvangen, begint deze te luisteren naar elke payload die naar het eindpunt wordt verzonden. Als je een geheim hebt ingesteld bij het configureren van je webhook, stuurt Roblox een roblox-signature  in elke webhookmelding om ervoor te zorgen dat het verzoek daadwerkelijk van Roblox komt. De handtekening bevindt zich in de payloadheader voor aangepaste eindpunten en in de voettekst voor derde-partij servers.

Handtekeningformaat met een geheim voor aangepaste eindpunten

```

t=<timestamp>,v1=<signature>

```

Als je geen geheim voor je webhook hebt ingesteld, bevat de handtekening alleen de tijdstempel van wanneer de melding is verzonden:

Handtekeningformaat zonder geheim voor aangepaste eindpunten

```

t=<timestamp>

```

Om een handtekening te verifiëren:

Aangepaste eindpunten Derde-partij servers

1.

Extraheer de tijdstempel- en handtekeningwaarden. Alle handtekeningen voor webhooks met geheimen delen hetzelfde formaat als een CSV-string met deze twee waarden gevolgd door de prefixen:

-

t : De tijdstempel van wanneer de melding is verzonden.

-

v1 : De handtekeningwaarde die is gegenereerd met behulp van het geheim dat is opgegeven in de configuratie van het Creator Dashboard.

2.

Maak de basisstring van roblox-signature  opnieuw aan door te concatenateren:

1.

De tijdstempel als een string.

2.

Het puntteken . .

3.

De JSON-string van de aanvraagbody.

3.

Bereken een hash-gebaseerde berichtauthenticatiecode (HMAC) met de SHA256-hashfunctie met behulp van het geheim dat je tijdens de configuratie hebt gedefinieerd als de sleutel en de basisstring die je in stap 2 hebt gegenereerd als het bericht. Zet het resultaat om naar Base64-formaat om de verwachte handtekening te krijgen.

4.

Vergelijk de geëxtraheerde handtekeningwaarde met de verwachte handtekening. Als je de handtekening correct hebt gegenereerd, zou de waarde hetzelfde moeten zijn.

5.

OPTIONEEL

 Om herhalingsaanvallen te voorkomen, een type cyberaanval waarbij aanvallers gegevens onderscheppen en opnieuw verzenden om ongeautoriseerde toegang te krijgen of kwaadaardige acties uit te voeren, is het nuttig om de geëxtraheerde tijdstempelwaarde te vergelijken met de huidige tijdstempel en ervoor te zorgen dat deze binnen een redelijke tijdslimiet valt. Bijvoorbeeld, een venster van 10 minuten is meestal een goede redelijke tijdslimiet.

## [Payloadschema](#payloadschema)[](#payloadschema)

Wanneer de doelgebeurtenis van je webhook wordt getriggerd, wordt er een verzoek naar je webhook-URL verzonden, inclusief informatie over de gebeurtenis in de payload. Alle payloads van verzoeken delen hetzelfde schema dat bestaat uit vaste en variabele velden. Dit zorgt ervoor dat de gegevens die in de payload worden verzonden gestructureerd en consistent zijn, waardoor het voor de ontvangende applicatie gemakkelijker wordt om de gegevens te verwerken en te gebruiken.

De vaste payloadschema-velden  kunnen helpen om consistentie te behouden over alle webhookverzoeken, met de volgende beschikbare velden:

1.

NotificationId  (string): Een unieke identificatie voor elke verzonden melding. Als dezelfde NotificationId  twee keer wordt ontvangen, wordt deze als een duplicaat beschouwd.

2.

EventType  (string): Geeft het type gebeurtenis aan waarvoor de melding is getriggerd.

3.

EventTime  (string): De tijdstempel van wanneer de gebeurtenis is getriggerd.

De variabele payloadschema-velden  bieden flexibiliteit voor webhooks om verschillende soorten gebeurtenissen te accommoderen, die omvatten:

1.

EventPayload  (object): Bevat informatie die specifiek is voor het EventType  dat de webhook heeft getriggerd. De structuur van het EventPayload -schema varieert op basis van het type gebeurtenis.

Het volgende voorbeeld toont het payloadschema van het Recht op Verwijdering verzoek  evenement:

Voorbeeldschema voor een Recht op Verwijdering verzoek

```

{

  "NotificationId": "string",

  "EventType": "RightToErasureRequest",

  "EventTime": "2023-12-30T16:24:24.2118874Z",

  "EventPayload": {

    "UserId": 1,

    "GameIds": [1234, 2345]

  }

}

```

## [Meldingen afhandelen](#meldingen-afhandelen)[](#meldingen-afhandelen)

Als je enige Persoonlijk Identificeerbare Informatie (PII)  van je gebruikers opslaat, zoals hun Gebruikers-ID's, moet je het verzoek evalueren in het licht van je wettelijke verplichtingen. Meer informatie is te vinden in [RTBF en Creators](/docs/nl-nl/production/publishing/RTBF-and-creators) . Je kunt een bot maken om webhookmeldingen af te handelen en te helpen bij het automatiseren van gegevensverwijdering, op voorwaarde dat je PII in een gegevensopslag opslaat. Zie [Automatiseren van Verzoeken om Verwijdering](/docs/nl-nl/cloud/webhooks/automate-right-to-erasure)  voor een voorbeeld van hoe je een bot binnen Discord kunt maken die de [Open Cloud API voor gegevensopslag](/docs/nl-nl/cloud/guides/data-stores)  gebruikt om PII-gegevens als een automatiseringsoplossing te verwijderen. Dit voorbeeld kan worden aangepast voor het afhandelen van andere meldingen, zoals abonnementsevents.

Als je een aangepast eindpunt als je webhookserver gebruikt in plaats van een derde-partij tool, kun je de gegevens die voor verwijdering in aanmerking komen uit de webhookpayload extraheren en je eigen automatiseringsoplossing bouwen. Het volgende codevoorbeeld is een voorbeeld van een server die bescherming biedt tegen herhalingsaanvallen door de tijdstempel te verifiëren en ervoor te zorgen dat het verzoek van Roblox komt:

PII uit Payload extraheren

```

const crypto = require('crypto');

const express = require('express');

const secret = '<your_secret>'; // Dit kan als een omgevingsvariabele worden ingesteld

let app = express();

app.use(express.json());

app.all('/*', function (req, res) {

  console.log('Nieuw verzoek ontvangen');

  // Extraheer de tijdstempel en handtekening uit de header

  const signatureHeader = req.headers['roblox-signature'].split(',');

  const timestamp = signatureHeader

    .find((e) => e.startsWith('t='))

    .substring(2);

  const signature = signatureHeader

    .find((e) => e.startsWith('v1='))

    .substring(3);

  // Zorg ervoor dat het verzoek binnen een venster van 300 seconden is gekomen om herhalingsaanvallen te voorkomen

  const requestTimestampMs = timestamp * 1000;

  const windowTimeMs = 300 * 1000;

  const oldestTimestampAllowed = Date.now() - windowTimeMs;

  if (requestTimestampMs < oldestTimestampAllowed) {

    return res.status(403).send('Verzoek is verlopen');

  }

  // Valideer handtekening

  const message = `${timestamp}.${JSON.stringify(req.body)}`;

  const hmac = crypto.createHmac('sha256', secret);

  const calculatedSignature = hmac.update(message).digest('base64');

  if (signature !== calculatedSignature) {

    return res.status(401).send('Ongeautoriseerd Verzoek');

  }

  // Jouw logica om payload af te handelen

  const payloadBody = req.body;

  const eventType = payloadBody['EventType'];

  if (eventType === 'RightToErasureRequest') {

    const userId = payloadBody['EventPayload']['UserId'];

    const gameIds = payloadBody['EventPayload']['GameIds'];

    console.log(`Payloadgegevens: UserId=${userId} en GameIds=${gameIds}`);

    // Als je PII in gegevensopslag opslaat, gebruik dan de UserId en GameIds om de informatie uit gegevensopslag te verwijderen.

  }

  return res.json({ message: 'Bericht succesvol verwerkt' });

});

app.listen(8080, function () {

  console.log('Server gestart');

});

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
