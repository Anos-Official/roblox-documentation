<!-- Source: https://create.roblox.com/docs/nl-nl/matchmaking -->

Matchmaking | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Matchmaking](/docs/nl-nl/matchmaking)

# Matchmaking

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Matchmaking is het proces van het koppelen van spelers aan servers op basis van spelerskenmerken zoals leeftijd, taal, vaardigheidsniveau en andere voorkeuren voor gameplay.

## [Hoe matchmaking werkt](#hoe-matchmaking-werkt)[](#hoe-matchmaking-werkt)

Wanneer een speler probeert je game te betreden, zoekt de matchmakingservice naar alle geschikte servers die de speler kan betreden, beoordeelt deze servers met behulp van signalen en koppelt de speler aan de server met de hoogste score.

De matchmakingflow werkt als volgt:

1.

Een speler vraagt om een plaats te betreden.

2.

Matchmaking vindt geschikte servers die de speler kan betreden, waarbij servers die vol, privé, gereserveerd of op het punt staan om te worden afgesloten, worden gefilterd.

3.

Matchmaking beoordeelt alle geschikte servers om de meest compatibele server voor de speler te bepalen.

4.

Matchmaking koppelt de speler aan de server met de hoogste score.

5.

De speler betreedt de winnende server.

 Standaard matchmaking van Roblox  ![De standaard matchmakingflow van Roblox.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Default_Matchmaking.png)  Aangepaste matchmaking  ![De aangepaste matchmakingflow.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Custom_Matchmaking.png)

## [Scoring](#scoring)[](#scoring)

Het matchmaking scoringalgoritme gebruikt de gewogen som (WS) van signaalwaarden om scores aan servers toe te wijzen.

Voor meer informatie over scoring, zie [Server scoring](/docs/nl-nl/matchmaking/scoring) .

## [Attributen](#attributen)[](#attributen)

Attributen zijn eigenschappen die worden gebruikt in matchmaking scoring. Een attribuut kan een getal zijn, zoals de leeftijd en het vaardigheidsniveau van een speler, of een string, zoals de taal van een speler.

Attributen kunnen numeriek of categorisch zijn:

-

Numerieke attributen  vergelijken het verschil tussen het attribuut van de toetredende speler en de geaggregeerde waarde van de server, waarbij grotere verschillen de score verlagen of verhogen. Bijvoorbeeld, hoe dichter het vaardigheidsniveau van een speler bij het gemiddelde vaardigheidsniveau van de server ligt, hoe hoger de score van het numerieke signaal is. Deze score wordt vervolgens vermenigvuldigd met het gewicht van het signaal.

-

Categorische attributen  zijn gebaseerd op hoe gebruikelijk het attribuut van de toetredende speler is in vergelijking met de andere spelers op de server. Bijvoorbeeld, als een hoog percentage van de spelers op een server dezelfde voorkeurstaal heeft als de toetredende speler, neemt de score toe. Deze score wordt ook vermenigvuldigd met het gewicht van het signaal.

Voor een lijst van alle bestaande attributen, zie [Bestaande attributen](/docs/nl-nl/matchmaking/attributes-and-signals#bestaande-attributen) . Voor meer informatie over aangepaste attributen, zie [Aangepaste attributen](/docs/nl-nl/matchmaking/attributes-and-signals#aangepaste-attributen) .

## [Signalering](#signalering)[](#signalering)

Signalen die worden gebruikt in server scoring kunnen ofwel de standaardsignalen zijn die al door Roblox worden geleverd, of aangepaste signalen die je zelf maakt.

Roblox-signalen gebruiken bestaande attributen waar Roblox al toegang toe heeft, zoals spelerslocatie, leeftijdsgroep en latentie. Aangepaste signalen moeten echter aangepaste attributen gebruiken om gegevens uit je gegevensopslag te verkrijgen. Om een aangepast signaal te maken, moet je eerst een aangepast attribuut maken.

Voor een lijst van alle bestaande Roblox-signalen, zie [Bestaande signalen](/docs/nl-nl/matchmaking/attributes-and-signals#bestaande-signalen) . Voor meer informatie over aangepaste signalen, zie [Aangepaste signalen](/docs/nl-nl/matchmaking/attributes-and-signals#aangepaste-signalen) .

## [Aangepaste matchmaking](#aangepaste-matchmaking)[](#aangepaste-matchmaking)

Wanneer een speler je game betreedt, wijst matchmaking een score toe aan elke actieve server op basis van de gewogen som van de signaalwaarden van de server. Je kunt dit proces aanpassen door het gewicht van elk van je signalen aan te passen om te veranderen hoe belangrijk elk signaal is in de scoring van servers. Het verhogen van het gewicht van het latentiesignaal betekent bijvoorbeeld dat het matchmaking-algoritme servers met een lagere ping prioriteert voor een soepelere gameplay.

Na het aanpassen van signaalgewichten kun je de impact van deze nieuwe gewichten op de selectie van matchmakingservers bekijken door ze te evalueren op mockservers.

Voor meer informatie over hoe je matchmaking kunt aanpassen en de resultaten kunt simuleren, zie [Pas je matchmakingconfiguratie aan](/docs/nl-nl/matchmaking/customize-matchmaking) .

## [Analytics](#analytics)[](#analytics)

Matchmaking-analyse helpt je de effectiviteit van je matchmakingconfiguraties te volgen en kansen te vinden om ze te optimaliseren.

Voor meer informatie over matchmaking-analyse, zie [Analytics](/docs/nl-nl/matchmaking/analytics) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
