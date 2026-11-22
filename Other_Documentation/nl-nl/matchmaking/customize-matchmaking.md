<!-- Source: https://create.roblox.com/docs/nl-nl/matchmaking/customize-matchmaking -->

Pas je matchmakingconfiguratie aan | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Matchmaking](/docs/nl-nl/matchmaking)

# Pas je matchmakingconfiguratie aan

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met een aangepaste matchmakingconfiguratie kun je competitieve, coöperatieve en unieke games bouwen door spelers aan servers te koppelen op basis van kenmerken zoals vaardigheidsniveau, latentie en speelvoorkeuren.

Standaard biedt Roblox je een matchmakingconfiguratie die gebruikmaakt van vooraf gedefinieerde Roblox-signalen. Om matchmaking aan te passen, kun je nieuwe matchmakingconfiguraties maken door [de gewichten van bestaande Roblox-signalen aan te passen](#aangepaste-configuratie-met-roblox-signalen) , [nieuwe aangepaste signalen te creëren](#aangepaste-configuratie-met-aangepaste-signalen) , of beide. Je kunt vervolgens je configuratie bekijken door [server scores te previewen met mock servers](#preview-en-test-server-scores) .

## [Aangepaste configuratie met Roblox-signalen](#aangepaste-configuratie-met-roblox-signalen)[](#aangepaste-configuratie-met-roblox-signalen)

Je kunt de gewichten van bestaande Roblox-signalen aanpassen om de matchmaking van je game aan te passen. Voor meer informatie over Roblox-signalen en hoe hun formules worden berekend, zie [Bestaande signalen](/docs/nl-nl/matchmaking/attributes-and-signals#bestaande-signalen) .

Om een aangepaste matchmakingconfiguratie te maken met alleen Roblox-signalen:

1.

Selecteer een game op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Navigeer in de linkernavigatie naar Configuraties  > Aangepaste matchmaking .

3.

Selecteer het tabblad Configuratie  en klik op Configuratie maken .

4.

Voer op de pagina Een aangepaste matchmakingconfiguratie maken  een naam in voor je configuratie.

5.

Wijzig de gewichten van de Roblox-signalen die je wilt bijwerken.

6.

Klik op Configuratie opslaan .

7.

Selecteer de plaatsen waarop je deze configuratie wilt toepassen.

8.

Klik opnieuw op Configuratie opslaan .

De nieuwe matchmakingconfiguratie verschijnt in de lijst Configuraties  van het tabblad Configuratie .

 ![De lijst met configuraties van het tabblad Configuratie.](https://prod.docsiteassets.roblox.com/assets/matchmaking/CustomConfiguration_List.png)

## [Aangepaste configuratie met aangepaste signalen](#aangepaste-configuratie-met-aangepaste-signalen)[](#aangepaste-configuratie-met-aangepaste-signalen)

Om een aangepaste matchmakingconfiguratie te maken met aangepaste signalen:

1.

Selecteer een game op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Navigeer in de linkernavigatie naar Configuraties  > Aangepaste matchmaking .

3.

Selecteer het tabblad Configuratie  en klik op Configuratie maken .

4.

Voer op de pagina Een aangepaste matchmakingconfiguratie maken  een naam in voor je configuratie.

5.

Klik op Aangepast signaal toevoegen  en [maak een aangepast signaal](#maak-een-aangepast-signaal) .

6.

Wijzig de gewichten van de signalen die je wilt bijwerken.

7.

Klik op Configuratie opslaan .

8.

Selecteer de plaatsen waarop je deze configuratie wilt toepassen.

9.

Klik opnieuw op Configuratie opslaan .

De nieuwe matchmakingconfiguratie verschijnt in de lijst Configuraties  van het tabblad Configuratie .

### [Maak een aangepast signaal](#maak-een-aangepast-signaal)[](#maak-een-aangepast-signaal)

Je kunt in totaal 2 aangepaste signalen per game maken.

Aangepaste signalen gebruiken aangepaste attributen om toegang te krijgen tot speler- en servergegevens. Om een aangepast signaal te maken, moet je eerst een [aangepast attribuut](#maak-een-aangepast-attribuut)  maken.

Aangepaste signalen kunnen numeriek voor spelers, numeriek voor servers, categorisch voor spelers of categorisch voor servers zijn. Voor meer informatie over aangepaste signalen en hoe hun formules worden berekend, zie [Aangepaste signalen](/docs/nl-nl/matchmaking/attributes-and-signals#aangepaste-signalen) .

Om een aangepast signaal te maken:

1.

Klik op de pagina Een aangepaste matchmakingconfiguratie maken  op Aangepast signaal toevoegen .

2.

Voer onder Signaalgegevens  een signaalnaam en beschrijving in.

3.

Onder Signaalconfiguratie :

-

Voor een numeriek attribuut voor spelers :

1.

Kies het [attribuut](#maak-een-aangepast-attribuut)  dat je wilt verwijzen.

2.

Selecteer hoe je het attribuut in elke server wilt aggregeren.

-

Gemiddelde : Het gemiddelde van alle spelers' attribuutwaarden in de server. Minimaliseert het verschil tussen de gemiddelde spelerattribuut van de server en het attribuut van de toetredende speler.

-

Mediaan : De mediaan van alle spelers' attribuutwaarden in de server. Minimaliseert het verschil tussen de mediaan spelerattribuut van de server en het attribuut van de toetredende speler.

-

Som : De som van alle spelers' attribuutwaarden in de server, inclusief die van de toetredende speler. Minimaliseert het verschil tussen de totale attribuutwaarde van de spelers in de server, inclusief de toetredende speler, en een constante waarde.

3.

Pas de waarden onder de aggregatie aan.

-

Voor een numeriek attribuut voor servers :

1.

Kies het [attribuut](#maak-een-aangepast-attribuut)  dat je wilt verwijzen.

2.

Pas de waarden onder het attribuut aan.

-

Voor een categorisch attribuut voor spelers :

1.

Kies het [attribuut](#maak-een-aangepast-attribuut)  dat je wilt verwijzen.

2.

Selecteer hoe je de attribuutwaarde over servers wilt verdelen:

-

Cluster : Groepeert spelers met dezelfde attribuutwaarde. Maximaliseert de verhouding van spelers in de server die dezelfde attribuutwaarde hebben als de toetredende speler.

-

Diversifiëren : Groepeert spelers met verschillende attribuutwaarden. Maximaliseert de verhouding van spelers in de server die een andere attribuutwaarde hebben dan de toetredende speler.

-

Voor een categorisch attribuut voor servers :

1.

Kies het [attribuut](#maak-een-aangepast-attribuut)  dat je wilt verwijzen.

2.

Pas de waarden onder het attribuut aan.

4.

OPTIONEEL

 Vouw Preview en Test Signaal  uit om de signaalscore te previewen. Je kunt de waarden van Test Signaal  aanpassen om het previewresultaat te optimaliseren.

 ![Een preview van de signaalscore in Preview en Test Signaal.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Preview_Custom_Signal.png)

5.

Klik op Signaal maken .

Het nieuwe aangepaste signaal verschijnt in de lijst Configuratie  van de pagina Een aangepaste matchmakingconfiguratie maken .

### [Maak een aangepast attribuut](#maak-een-aangepast-attribuut)[](#maak-een-aangepast-attribuut)

Je kunt in totaal 5 serverattributen en 5 spelerattributen per game maken.

Attributen zijn eigenschappen die zijn gekoppeld aan spelers en servers, zoals vaardigheidsniveau en voorkeuren voor spelmodi. Als je aangepaste signalen wilt maken en gebruiken, moet je eerst aangepaste attributen maken. Je kunt speler- of serverattributen maken.

Voor meer informatie over het verschil tussen speler- en serverattributen, zie [Aangepaste attributen](/docs/nl-nl/matchmaking/attributes-and-signals#aangepaste-attributen) .

##### Spelerattributen

Om een spelerattribuut te maken:

1.

Selecteer op de pagina Aangepaste matchmaking  het tabblad Attributen  en klik op Attribuut maken .

2.

Selecteer op de pagina Attribuut maken  Spelerattribuut  en voer een unieke naam in.

3.

Kies een Gegevenstype  en een Standaardwaarde  voor het attribuut.

4.

Onder Instellingen voor gegevensopslag  selecteer je de gegevensopslag waarin de attribuutgegevens zich bevinden.

5.

Voer een Sjabloon voor gegevensopslag-sleutel  in om de waarden van de spelerattributen op te slaan. Tijdens runtime wordt de {UserId}  vervangen door de werkelijke gebruikers-ID van de speler.

6.

Voer een Pad voor gegevensopslag-waarde  in zodat matchmaking de waarde van het spelerattribuut kan vinden in een JSON-object in de geselecteerde gegevensopslag.

7.

Voer een Bereik voor gegevensopslag  in om het bereik op te geven. Als je geen bereik invoert, is het standaard globaal.

8.

Klik op Wijzigingen opslaan  om je spelerattribuut op te slaan.

 ![De attribuutkenmerken en instellingen voor gegevensopslag voor de creatie van een spelerattribuut.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Player_Attribute.png)

Het nieuwe attribuut verschijnt in de lijst Spelerattributen  van het tabblad Attributen .

##### Serverattributen

Om een serverattribuut te maken:

1.

Selecteer op de pagina Aangepaste matchmaking  het tabblad Attributen  en klik op Attribuut maken .

2.

Selecteer op de pagina Attribuut maken  Serverattribuut  en voer een unieke naam in.

3.

Kies een Gegevenstype  en een Standaardwaarde  voor het attribuut.

4.

Klik op Wijzigingen opslaan  om je serverattribuut op te slaan.

 ![De attribuutkenmerken voor de creatie van een serverattribuut.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Server_Attribute.png)

Het nieuwe attribuut verschijnt in de lijst Serverattributen  van het tabblad Attributen .

## [Preview en test server scores](#preview-en-test-server-scores)[](#preview-en-test-server-scores)

Voorbeeldserver scores zijn slechts voorbeelden en weerspiegelen geen daadwerkelijke game servers.

Preview en test server scoring om te zien hoe de gewichten van je configuratie invloed hebben op de serverselectie. Je kunt experimenteren met verschillende gewichtcombinaties om je matchmakingconfiguratie te optimaliseren.

Wanneer je een preview maakt, mockt de preview server scores en identificeert welke mockserver de hoogste totale score heeft en de beste match is voor de speler.

Om te previewen en te testen, klik je op Preview en Test  op de pagina Een aangepaste matchmakingconfiguratie maken . De preview toont je drie mockservers met verschillende scores en markeert de winnende server. Om details over de formules die voor scoring zijn gebruikt te zien, beweeg je de muis over elk signaal score resultaat voor elke mockserver.

 ![](https://prod.docsiteassets.roblox.com/assets/matchmaking/Matchmaking_Simulation.png)

Voor meer informatie over scoring en gewichten, zie [Scoring](/docs/nl-nl/matchmaking/scoring) .

## [Pas een configuratie toe op plaatsen](#pas-een-configuratie-toe-op-plaatsen)[](#pas-een-configuratie-toe-op-plaatsen)

Je kunt een matchmakingconfiguratie toepassen op zoveel plaatsen als je wilt binnen je game.

Om een configuratie op plaatsen toe te passen:

1.

Klik op de pagina Aangepaste matchmaking  op Toevoegen aan Plaats .

2.

Selecteer een configuratie en de plaats of plaatsen waarop je deze wilt toepassen.

3.

Klik op Configuratie opslaan .

De geselecteerde plaatsen verschijnen in de lijst Toegepaste Plaatsen  van het tabblad Configuratie . Je kunt ook een configuratie aan plaatsen toevoegen tijdens de creatie van die matchmakingconfiguratie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
