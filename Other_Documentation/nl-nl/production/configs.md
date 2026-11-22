<!-- Source: https://create.roblox.com/docs/nl-nl/production/configs -->

Ervaringsconfiguraties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Ervaringsconfiguraties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Ervaringsconfiguraties  stellen je in staat om in-game waarden in realtime bij te werken zonder servers opnieuw op te starten:

-

Zet functies aan en uit, zoals het inschakelen of uitschakelen van een nieuwe onboarding dungeon.

-

Pas in-game waarden aan zoals de gezondheid van bazen, ervaringswinst of itemprijzen.

-

Lanceer tijdgebonden inhoud, zoals een Halloween-evenement dat om middernacht begint.

-

Geef verschillende waarden aan verschillende spelers, zoals het geven van extra pantser aan nieuwere spelers.

Configuraties nemen de vorm aan van sleutels en waarden. In plaats van hard-coded constanten in je code te gebruiken, kun je de sleutel gebruiken om een waarde (string, nummer, boolean of JSON-object) op te halen en die waarde vervolgens bij te werken wanneer je maar wilt zonder een nieuwe versie van je ervaring te publiceren. De vereiste codewijzigingen zijn minimaal:

```

local ConfigService = game:GetService("ConfigService")

local configSnapshot = ConfigService:GetConfigAsync()

local myValue = configSnapshot:GetValue("my_key_name")

```

Je kunt op elk moment tot 1.000 actieve configuraties hebben en ze beheren op Creator Hub of in Roblox Studio.

![Overzicht van de Configs-pagina op Creator Hub](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-overview.png)

## [Maak en bewerk configuraties](#maak-en-bewerk-configuraties)[](#maak-en-bewerk-configuraties)

1.

Ga naar de [Creator Hub](https://create.roblox.com/dashboard/creations)  Configs -pagina voor je ervaring en klik op Maak configuratie .

2.

Geef een sleutel, een type, een waarde en optioneel een beschrijving op om jou of je team later te helpen de bedoeling van de configuratie te identificeren. Ondersteunde types zijn string, nummer, boolean en JSON-object. Klik op Volgende .

3.

(Optioneel) Voeg targetingvoorwaarden en waarden toe. Voorwaarden stellen je in staat om configuratiewaarden toe te passen op gebruikers die voldoen aan (of niet voldoen aan) bepaalde criteria, zoals gebruikers die je spel nog nooit hebben gespeeld of degenen die Portugees spreken. Om meer te leren, zie [Target configuraties naar specifieke spelers](#target-configuraties-naar-specifieke-spelers) .

4.

Kopieer de gegenereerde codefragment in een server-script in je ervaring, waarschijnlijk in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) . Voor "globale" configuraties die niet verschillen per speler, kan de code er ongeveer zo uitzien:

```

local ConfigService = game:GetService("ConfigService")

local configSnapshot = ConfigService:GetConfigAsync()

local MY_KEY = "my_key" -- optioneel, sla de configuratiesleutel op als een constante

local myValue = configSnapshot:GetValue(MY_KEY)

```

Voor [voorwaardelijke configuraties](#target-configuraties-naar-specifieke-spelers)  en [experimenten](/docs/nl-nl/production/experiments)  is de code iets anders:

```

local ConfigService = game:GetService("ConfigService")

local Players = game:GetService("Players")

local MY_KEY = "my_key" -- optioneel, sla de configuratiesleutel op als een constante

local function onPlayerAdded(player)

    local playerConfigSnapshot = ConfigService:GetConfigForPlayerAsync(player)

    local myValue = playerConfigSnapshot:GetValue(MY_KEY)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

5.

Gebruik de waarde zoals je zou doen met elke andere variabele. Configuraties doen niets  tenzij je ze binnen je code gebruikt.

Voor meer informatie over het werken met configuraties in je scripts, zie [Voeg configuraties toe aan je code](#voeg-configuraties-toe-aan-je-code) .

Het bewerken van een configuratie is niet anders dan het maken ervan. Klik op de Bewerken -knop en werk de waarde en beschrijving naar wens bij.

### [Limieten](#limieten)[](#limieten)

Configuratiewaarden hebben de volgende limieten per type.

| Type | | Maximale grootte |
| --- | --- |
| String | | 100.000 tekens |
| Nummer | | ±1.7976931348623157e+308, ±2^53 voor exacte gehele getalrepresentaties |
| Boolean | | N.v.t. |
| JSON | | 100.000 tekens |

## [Publiceer configuraties](#publiceer-configuraties)[](#publiceer-configuraties)

Nadat je een configuratie hebt gemaakt, gaat deze naar een gestageerde  staat zodat je deze kunt testen voordat deze openbaar beschikbaar wordt. Gestageerde wijzigingen zijn beschikbaar voor jou en je team in Studio-spelsessies, niet voor spelers in live ervaringen. De Configs -pagina op Creator Hub toont alle actieve en gestageerde wijzigingen.

 ![De Configs-pagina die niet-gepubliceerde wijzigingen toont](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-publish.png)

1.

Nadat je je gestageerde wijzigingen hebt getest, klik je op Nu publiceren  om bijna onmiddellijk naar alle spelers te publiceren (ongeveer tussen 15 seconden en 1 minuut). Je kunt ook kiezen voor Publiceer over 15 min  als je een langere, geleidelijke uitrolperiode verkiest. In sommige gevallen kan het even duren voordat clients de wijzigingen na publicatie weergeven.

2.

(Aanbevolen) Voeg een beschrijvende publicatieboodschap toe die aangeeft wat je hebt bijgewerkt. Deze boodschap verschijnt op de Geschiedenis -pagina en kan jou en je team later helpen de bedoeling van de wijziging te identificeren.

## [Target configuraties naar specifieke spelers](#target-configuraties-naar-specifieke-spelers)[](#target-configuraties-naar-specifieke-spelers)

Standaard levert een configuratie dezelfde waarde aan iedereen. Voorwaardelijke configuraties  stellen je in staat om verschillende waarden aan verschillende spelers te leveren op basis van spelersattributen (land, anciënniteit, taal, betaalstatus, enz.).

Voorwaardelijke configuraties hebben drie onderdelen die bepalen welke waarde een speler ontvangt:

-

Voorwaardelijke regels  definiëren wie overeenkomt. Elke regel is een logische expressie, zoals "actieve betalende spelers in hun eerste 30 dagen," die de spelersattributen evalueert.

-

Regelordening  definieert hoe te kiezen wanneer een speler aan meer dan één regel voldoet. Roblox evalueert regels van boven naar beneden en past de eerste overeenkomende tak toe. Regels zijn globaal geordend, ongeacht de volgorde waarin je voorwaardelijke waarden aan een individuele sleutel toevoegt.

-

Voorwaardelijke waarden  definiëren wat een overeenkomende speler krijgt. Voor elke voorwaarde koppel je een waarde. Als een speler aan een regel binnen die voorwaarde voldoet, ontvangt hij de bijbehorende waarde; anders ontvangt hij de standaardwaarde van de configuratie.

### [Ondersteunde attributen](#ondersteunde-attributen)[](#ondersteunde-attributen)

Voorwaardelijke configuraties ondersteunen de volgende attributen. Deze attributen delen dezelfde definities als de equivalente [filters](/docs/nl-nl/production/analytics/analytics-dashboard#filteren-op-statistieken)  en [onderverdelingen](/docs/nl-nl/production/analytics/analytics-dashboard#bekijk-kpi-uitsplitsingen)  in de analysetabellen.

| Attribuut | | Beschrijving |
| Land | | De geografische locatie van de speler. |
| Taal | | De taalinstelling van de speler. |
| Nieuw vs terugkerend | | Of de speler je ervaring voor de eerste keer speelt of deze eerder heeft gespeeld. |
| Bron | | Hoe de speler je ervaring heeft gevonden, zoals een aanbeveling op de startpagina, zoeken of een gesponsorde advertentie. |
| Wanneer de gebruiker voor het eerst speelde | | Hoe lang geleden de speler voor het eerst je ervaring speelde, zoals 0-30 dagen geleden of 31-90 dagen geleden. Dagelijks berekend. |
| Betaalstatus binnen de ervaring | | De betalingsactiviteit van de speler binnen je ervaring, waarmee je verschillende segmenten van betalende gebruikers kunt targeten. Dagelijks berekend. |
| Activiteitsstatus binnen de ervaring | | Hoe recent de speler je ervaring heeft gespeeld, waarmee je nieuwe, actieve, inactieve en heractiverende spelers anders kunt behandelen. Dagelijks berekend. |
| Gebruikersbetrokkenheid | | Hoeveel de speler elke week je ervaring speelt, waarmee je je meest betrokken spelers kunt scheiden van meer casual spelers. Dagelijks berekend. |
| Platformuitgavenstatus | | Of de speler een actieve uitgavenaar is op het Roblox-platform. Dagelijks berekend. |
| Platformactiviteitsstatus | | Hoe recent de speler ergens op Roblox heeft gespeeld, en niet alleen in je ervaring. Dagelijks berekend. |

### [Maak voorwaardelijke waarden](#maak-voorwaardelijke-waarden)[](#maak-voorwaardelijke-waarden)

Je voegt voorwaarden toe wanneer je een configuratie maakt of bewerkt. Tijdens de stap Voeg targeting toe , voeg je een voorwaarde toe:

1.

Kies een bestaande voorwaarde of klik op Maak een nieuwe .

2.

Voeg een of meer regels toe.

3.

Stel de waarde in die overeenkomende spelers ontvangen.

Bijvoorbeeld, om een moeilijkere ervaring te geven aan de beste actieve betalende spelers die binnen de laatste 30 dagen zijn begonnen met spelen, kun je hun dynamicBossHealth -waarde verhogen.

![De stap Voeg targeting toe die voorwaardelijke regels voor een configuratie toont](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-targeting-conditions.png)

### [Toegang tot gerichte waarden in code](#toegang-tot-gerichte-waarden-in-code)[](#toegang-tot-gerichte-waarden-in-code)

Om gerichte waarden op te halen, gebruik je [ConfigService:GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync) , dat de regels en ordening voor een individuele speler evalueert. [ConfigService:GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  past geen  targeting toe omdat het niet specifiek is voor een enkele speler. Voor meer informatie, zie [Voeg configuraties toe aan je code](#voeg-configuraties-toe-aan-je-code) .

### [Best practices en limieten](#best-practices-en-limieten)[](#best-practices-en-limieten)

-

Elke voorwaardelijke waarde moet overeenkomen met het datatype (boolean, string, nummer of JSON) van de standaardwaarde van de configuratie.

-

Je kunt tot 100 voorwaarden per spel  hebben.

-

Elke configuratiesleutel ondersteunt tot 20 voorwaarden .

-

Controleer de regelordening voordat je publiceert. Omdat regels globaal zijn geordend, bevestig dat je evaluatievolgorde correct is geprioriteerd. Om de volgorde te bekijken, klik je op het tabblad Voorwaarden .

## [Maak en bewerk configuraties in Studio](#maak-en-bewerk-configuraties-in-studio)[](#maak-en-bewerk-configuraties-in-studio)

Als je dat wilt, kun je configuraties maken, bewerken, stagen en publiceren in Roblox Studio. Klik op Bestand  > Open Configs  om de widget te openen. De Studio-interface is bijzonder handig voor het stagen en testen van nieuwe waarden.

 ![Studio-venster voor het werken met configuraties](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-widget-staged.png)

### [Publiceer configuraties naar een andere ervaring](#publiceer-configuraties-naar-een-andere-ervaring)[](#publiceer-configuraties-naar-een-andere-ervaring)

In Studio kun je je configuraties naar een andere ervaring publiceren, wat de configuraties voor die ervaring volledig overschrijft. Dit kan vooral nuttig zijn voor het synchroniseren van configuraties van een staging- of ontwikkelervaring naar de live-ervaring.

1.

Ga in Roblox Studio naar het bovenste menu en selecteer Bestand  > Open Configs .

2.

Klik in het tabblad Gepubliceerd  van de Configs-widget op het ⋮-pictogram en selecteer Publiceer als .

 ![Studio-venster voor het werken met configuraties](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-widget-publish-as.png)

3.

Zoek in de dialoog die verschijnt de doelervaring in de lijst van groepen waar je bewerkingsrechten hebt.

 ![Publiceer configuraties naar ervaringen](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-widget-target-experience.png)

## [Bekijk geschiedenis en herstel configuraties](#bekijk-geschiedenis-en-herstel-configuraties)[](#bekijk-geschiedenis-en-herstel-configuraties)

Op de Configs -pagina klik je op Geschiedenis  om eerdere updates te zien. Elke update heeft de tijd en datum van de wijziging, wie de wijziging heeft aangebracht en de publicatieboodschap.

![De geschiedenis pagina met diff uitgebreid voor een configuratiewaarde](https://prod.docsiteassets.roblox.com/assets/analytics/configs/configs-history.png)

-

Vouw elke rij uit om de sleutel, de waarde vóór de wijziging en de waarde erna te zien.

-

Gebruik het Zoek sleutel -vak om naar sleutels te zoeken - niet naar beschrijvingen of waarden, alleen naar sleutels.

De Geschiedenis -pagina stelt je ook in staat om configuraties naar een vorige staat te herstellen:

1.

Klik op Herstellen  naast de wijziging om de "voor" waarde te stagen. Houd er rekening mee dat het herstellen van een configuratie bestaande gestageerde wijzigingen vervalt.

2.

Ga terug naar de Configs -pagina en [publiceer de configuratie](#publiceer-configuraties) .

## [Voeg configuraties toe aan je code](#voeg-configuraties-toe-aan-je-code)[](#voeg-configuraties-toe-aan-je-code)

De belangrijkste klasse voor het werken met configuraties is [ConfigService](/docs/nl-nl/reference/engine/classes/ConfigService) , die de nieuwste sleutels en waarden voor je ervaring ophaalt. ConfigService  is alleen beschikbaar voor server-scripts. Proberen om zijn methoden vanuit een client-script aan te roepen resulteert in een fout.

De eerste stap om met configuraties te werken is het ophalen van een [ConfigSnapshot](/docs/nl-nl/reference/engine/classes/ConfigSnapshot) , de nieuwste waarden voor alle configuraties op het huidige moment. Er zijn twee methoden om een snapshot te krijgen:

-

[ConfigService:GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  is voor globale configuraties die je wilt toepassen op alle spelers in de ervaring:

```

local ConfigService = game:GetService("ConfigService")

local configSnapshot = ConfigService:GetConfigAsync()

local bossHealth = configSnapshot:GetValue("bossHealth")

```

-

[ConfigService:GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync)  haalt speler-specifieke configuraties op zodat verschillende spelers verschillende waarden kunnen krijgen. Gebruik het voor [voorwaardelijke configuraties](#target-configuraties-naar-specifieke-spelers)  en [experimenten](/docs/nl-nl/production/experiments) .

```

local ConfigService = game:GetService("ConfigService")

local Players = game:GetService("Players")

local function onPlayerAdded(player)

    local playerConfigSnapshot = ConfigService:GetConfigForPlayerAsync(player)

    local bossHealth = playerConfigSnapshot:GetValue("bossHealth")

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

In beide gevallen, als de sleutel niet bestaat, retourneert [ConfigSnapshot:GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  nil.

### [Autocomplete](#autocomplete)[](#autocomplete)

Configuraties zijn geïntegreerd in de autocompletion van de Script Editor. Wanneer je [ConfigSnapshot:GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  aanroept, stelt de editor je configuratiesleutelnamen voor en toont het type van elke configuratie wanneer je met de muis over de variabelenaam beweegt.

Als je script de --!strict  modus gebruikt, kan de linter het type voor je oppikken en verifiëren.

Autocompletion werkt ook met configuraties die complexe geneste JSON-types gebruiken.

### [Vernieuw snapshots](#vernieuw-snapshots)[](#vernieuw-snapshots)

[ConfigSnapshots](/docs/nl-nl/reference/engine/classes/ConfigSnapshot)  vertegenwoordigen een moment in de tijd, de staat van de configuratie wanneer je de snapshot opvroeg. Om verstoring van de gameplay te voorkomen, worden updates aan een configuratie niet  automatisch doorgegeven aan snapshots. In een competitieve shooter, bijvoorbeeld, wil je misschien alleen nieuwe configuratiewaarden tussen rondes zodat wapenattributen niet fluctueren tijdens de wedstrijd.

Om de nieuwste waarden handmatig te krijgen, gebruik je de [ConfigSnapshot:Refresh()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#Refresh) -methode. Optioneel kun je een functie verbinden met het [ConfigSnapshot.UpdateAvailable](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#UpdateAvailable) -evenement om automatisch te vernieuwen:

```

configSnapshot.UpdateAvailable:Connect(function()

    configSnapshot:Refresh()

end)

```

Nadat je een snapshot hebt vernieuwd, kun je [ConfigSnapshot:GetValueChangedSignal()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValueChangedSignal)  gebruiken om te luisteren naar wijzigingen in een specifieke sleutel, zodat je de code van je ervaring kunt bijwerken:

```

configSnapshot:GetValueChangedSignal("bossHealth"):Connect(function(newHealthValue)

    spawnNewBoss(newHealthValue)

end)

```

### [Foutafhandeling](#foutafhandeling)[](#foutafhandeling)

In zeldzame gevallen wanneer de configuratie niet kan worden geladen en nog nooit eerder is geladen, gooit [ConfigService:GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  een fout.

Als [ConfigService](/docs/nl-nl/reference/engine/classes/ConfigService)  de verbinding met de Roblox-servers verliest nadat deze eerder was geladen, retourneert [ConfigService:GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  een snapshot met de laatst beschikbare waarden. Deze snapshots proberen opnieuw verbinding te maken en activeren het UpdateAvailable -evenement wanneer ze met succes nieuwe updates laden.

Hoe je met deze ongebruikelijke situaties omgaat, is aan jou. Je kunt de oproep in een [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  wikkelen en fallbackwaarden in je code hebben, de speler een foutmelding tonen en wachten tot de snapshot opnieuw verbinding maakt, of een andere oplossing.

## [Test configuraties](#test-configuraties)[](#test-configuraties)

[ConfigService](/docs/nl-nl/reference/engine/classes/ConfigService)  heeft ingebouwde methoden voor het tijdelijk testen van configuratiewijzigingen, zowel in Studio als op live servers, zonder de hele ervaring te beïnvloeden.

Om een lokale testwaarde in te stellen, roep je [ConfigService:SetTestingValue()](/docs/nl-nl/reference/engine/classes/ConfigService#SetTestingValue)  aan vanuit een server-script of via de [Developer Console](/docs/nl-nl/studio/developer-console) . Wijzigingen in testwaarden activeren een configuratie-update samen met het [ConfigSnapshot.UpdateAvailable](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#UpdateAvailable) -signaal. Net als bij een productie-update moet je bestaande snapshots vernieuwen om de testwaarde te krijgen:

```

local ConfigService = game:GetService("ConfigService")

ConfigService:SetTestingValue("bossHealth", 200)

local configSnapshot = ConfigService:GetConfigAsync()

local bossHealth = configSnapshot:GetValue("bossHealth") -- Nu 200!

```

Testwijzigingen zijn van toepassing voor de levensduur van de huidige server en worden niet doorgegeven aan andere servers. In Studio zijn ze van toepassing op de huidige speelsessie en beïnvloeden ze geen live servers. Je kunt testwijzigingen handmatig wissen met [ConfigService:ClearTestingValue()](/docs/nl-nl/reference/engine/classes/ConfigService#ClearTestingValue) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
