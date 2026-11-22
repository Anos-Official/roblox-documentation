<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/error-report -->

Foutrapport | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Foutrapport

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Foutrapport  stelt je in staat om de meest actuele Luau-systeemfouten en waarschuwingen voor zowel server als client te bekijken. Houd je foutrapport in de gaten voor en na het bijwerken van je spel om potentiële problemen vroegtijdig te identificeren.

## [Bekijk je foutrapport](#bekijk-je-foutrapport)[](#bekijk-je-foutrapport)

Om het foutrapport van je spel te bekijken:

-

Navigeer naar je [Creations](https://create.roblox.com/dashboard/creations)  pagina in het Creator Dashboard  en selecteer je spel.

-

Onder Monitoring , selecteer Foutrapport .

Je kunt analyses bekijken voor individuele of groepsbezit ervaringen. Om de laatste te bekijken, moet je [groepsmachtigingen voor analyses](/docs/nl-nl/production/analytics/analytics-dashboard)  hebben.

## [Fouten en waarschuwingen monitoren](#fouten-en-waarschuwingen-monitoren)[](#fouten-en-waarschuwingen-monitoren)

Je kunt de volgende filters en schakelaars op je foutrapport toepassen:

-

Datumbereik  — Filter op de laatste 1 uur, laatste 1 dag, laatste 7 dagen of laatste 30 dagen.

-

Plaats  — Filter op plaats.

-

Toon versie  — Voegt plaatsversieannotaties toe aan de fouten- en waarschuwingen grafiek.

-

Ernst  — Filter om fouten, waarschuwingen of beide te tonen.

-

Platform  — Filter om clientfouten van specifieke apparaten te tonen.

-

OS  — Filter om clientfouten van specifieke besturingssystemen te tonen.

-

Nieuwe fouten sinds  — Filter om alleen nieuwe fouten en waarschuwingen sinds een bepaalde versie te tonen.

Onder de filters en schakelaars toont een grafiek het aantal fouten en waarschuwingen voor server, client en totaal. Gebruik deze grafiek om naar stijgingen in fouten en waarschuwingen in de loop van de tijd te kijken. Als je een grote piek in fouten en waarschuwingen ziet, gebruik dan de foutrapporttabel om problemen op te lossen.

![](https://prod.docsiteassets.roblox.com/assets/analytics/error-report/error-report-graph.png) Fouten en waarschuwingen in de loop van de tijd per categorie weergegeven

## [Fouten en waarschuwingen oplossen](#fouten-en-waarschuwingen-oplossen)[](#fouten-en-waarschuwingen-oplossen)

De Fouten en waarschuwingen  tabel heeft de volgende kolommen:

| Kolom | | Beschrijving |
| --- | --- |
| Aantal | | Aantal fouten of waarschuwingen. |
| Ernst | | Fout- of waarschuwingslabel. |
| Type | | Server- of clientlabel. |
| Bericht | | Fout- of waarschuwingsbericht. |
| Voor het eerst gezien op | | Tijdstempel van de eerste keer dat het bericht werd gezien. |
| Eerste versie gezien | | Alleen beschikbaar wanneer een plaats is gekozen. Toont de eerste versie waarin het bericht werd geregistreerd. |

![](https://prod.docsiteassets.roblox.com/assets/analytics/error-report/error-report-table.png) De foutrapporttabel

### [Bekijk de stacktrace voor een fout of waarschuwing](#bekijk-de-stacktrace-voor-een-fout-of-waarschuwing)[](#bekijk-de-stacktrace-voor-een-fout-of-waarschuwing)

Als je een dropdown ziet op een fout of waarschuwing, klik dan om deze uit te vouwen en de bijbehorende stacktrace  te zien. Een stacktrace is een lijst van de aanroepen die je spel aan het uitvoeren was toen de uitzondering werd opgegooid. Dit kan je helpen uit te vinden wat er misgaat.

## [Aangepaste regels](#aangepaste-regels)[](#aangepaste-regels)

Aangepaste regels stellen je in staat om regex of exacte tekenreeks patronen te definiëren om automatisch fouten en waarschuwingen te negeren of te groeperen. Dit helpt je om de signaal-ruisverhouding van je foutrapporten te beheren. Je kunt tot 100 regels per ervaring maken. Regels worden van boven naar beneden geëvalueerd in prioriteitsvolgorde. Zodra een fout overeenkomt met een regel, stopt verdere verwerking.

### [Acties van regels](#acties-van-regels)[](#acties-van-regels)

Elke regel heeft een van de twee acties:

| Actie | | Gedrag |
| Negeer | | Verbergt overeenkomende fouten uit de grafiek en tabel. Gebruik dit voor permanente ruis zoals onvermijdelijke motor geluidfouten of legacy printstatements. |
| Groep | | Consolidateert alle overeenkomende fouten onder een aangepaste groepsnaam (bijv. "Netwerkproblemen", "Audio Spam"). De groepsnaam verschijnt als een enkele rij in de tabel. |

### [Maak een regel](#maak-een-regel)[](#maak-een-regel)

Er zijn twee manieren om een regel te maken:

Vanuit de fouttabel (inline):

1.

Klik op het contextmenu (drie stippen) op een foutregel.

2.

Selecteer Negeer .

![](https://prod.docsiteassets.roblox.com/assets/analytics/error-report/create-a-rule.png) Een fout negeren vanuit de fouttabel

Vanuit het regels tabblad:

1.

Navigeer naar het Regels  tabblad op de Foutrapporten pagina.

2.

Klik op Regel maken .

3.

Voer een patroon in (exacte tekenreeks of regex).

4.

Selecteer een actie: Negeer  of Groep  → [Groepsnaam].

5.

Sla de regel op.

![](https://prod.docsiteassets.roblox.com/assets/analytics/error-report/rules-tab.png) Het Regels tabblad met voorbeeldregels

### [Velden voor regelcreatie](#velden-voor-regelcreatie)[](#velden-voor-regelcreatie)

| Veld | | Beschrijving |
| Patroon | | De exacte tekenreeks of reguliere expressie om tegen foutberichten te matchen. |
| Actie | | Kies Negeer  (verberg de fout) of Groep  → voer een aangepaste groepsnaam in. |

![](https://prod.docsiteassets.roblox.com/assets/analytics/error-report/rule-creation-fields.png) Het dialoogvenster Regel maken

Regels worden van boven naar beneden geëvalueerd op basis van de prioriteitsvolgorde in het Regels tabblad. Zodra een fout overeenkomt met een regel, wordt de actie van die regel uitgevoerd en worden er geen verdere regels geëvalueerd voor die fout. Dit voorkomt conflicten zoals een fout die door de ene regel wordt gegroepeerd en vervolgens door een volgende regel wordt genegeerd.

Regels hebben alleen invloed op fouten die worden geregistreerd nadat ze zijn opgeslagen. Een annotatie verschijnt op je grafiek wanneer regels worden gewijzigd.

### [Basisprincipes van reguliere expressies](#basisprincipes-van-reguliere-expressies)[](#basisprincipes-van-reguliere-expressies)

Een reguliere expressie (regex) is een patroon dat tekst matcht:

| Syntax | | Betekenis | | Voorbeeld |
| . | | Elk enkel teken | | H.t  matcht "Hoed", "Hit", "Heet" |
| * | | Nul of meer van het voorgaande teken | | go*d  matcht "gd", "god", "goed" |
| + | | Een of meer van het voorgaande teken | | go+d  matcht "god", "goed", maar niet "gd" |
| .* | | Elke reeks van tekens (wildcard) | | Failed.*load  matcht "Failed to load" en "Failed xyz load" |
| \d | | Elk cijfer (0-9) | | v\d+  matcht "v1", "v123", "v4488" |
| \w | | Elk woordteken (letters, cijfers, underscore) | | \w+  matcht "Speler123", "mijn_var" |
| ^ | | Begin van de tekenreeks | | ^HTTP  matcht fouten die beginnen met "HTTP" |
| \/ | | Een ontsnapte schuine streep | | rbxassetid:\/\/  matcht "rbxassetid://" |
| \[ en \] | | Ontsnapte vierkante haken (letterlijke match) | | \[Knit\]  matcht "[Knit]" |
| (a|b) | | Match "a" of "b" | | (Fout|Waarschuwing):.*  matcht zowel "Fout: ..." als "Waarschuwing: ..." |

Snelle tips:

-

Begin met een exacte match (de volledige fouttekenreeks) als je alleen één specifieke fout wilt vangen.

-

Gebruik een regex wanneer je een familie van soortgelijke fouten wilt vangen (bijv. alle geluidslaadfouten ongeacht de asset-ID).

-

Test je patroon tegen een paar echte fouttekenreeksen voordat je opslaat om ervoor te zorgen dat het vangt wat je verwacht.

Het systeem handhaaft twee regels op je regex-patronen:

-

Je kunt geen herhalingssymbool (+  of * ) binnen een herhalende groep plaatsen. Bijvoorbeeld, (a+)*  of (\w+)+  worden afgewezen.

-

Moet beginnen met verankerde tekst: Patronen mogen niet beginnen met een wildcard zoals .*  of .+ . Je patroon moet beginnen met een concreet teken of anker (zoals ^  of een letterlijke tekenreeks).

### [Regelvoorbeelden om je foutrapporten te organiseren](#regelvoorbeelden-om-je-foutrapporten-te-organiseren)[](#regelvoorbeelden-om-je-foutrapporten-te-organiseren)

In plaats van tientallen afzonderlijke foutregels te zien, consolideer gerelateerde fouten onder één groepsnaam:

| Gebruikscase | | Voorbeeldfouten | | Patroon | | Actie |
| Alle netwerkfouten | | HttpError: ConnectFail , HttpError: Timedout | | HttpError:.* | | Groep → "Netwerkproblemen" |
| DataStore waarschuwingen | | DataStore request was added to queue , DataStoreService: ... | | DataStore | | Groep → "DataStore Waarschuwingen" |
| Speler GUI fouten | | Players.Player1.PlayerGui.Shop:12: attempt to index nil | | Players\.\w+\.PlayerGui | | Groep → "PlayerGui Fouten" |
| Aangepaste UI-framework | | [UIManager] Button render failed , [UIManager] Layout overflow | | \[UIManager\].* | | Groep → "UI Systeem" |

## [Limieten voor fouttracking](#limieten-voor-fouttracking)[](#limieten-voor-fouttracking)

Het systeem houdt tot 500 unieke fouten en 500 unieke waarschuwingen bij op basis van aantal en de top 100 nieuwe fouten per versie. Deze tellingen worden elke 6 uur gereset. Om nuttige fouttracking binnen deze limieten te maximaliseren:

-

Verwijder unieke identificatoren uit foutberichten, zoals gebruikers-ID's, coördinaten of tijdstempels. Fouten zoals Speler 12345 kon niet laden  en Speler 67890 kon niet laden  tellen als twee afzonderlijke vermeldingen. Als je ze registreert als Speler kon niet laden , worden ze samengevoegd tot één vermelding met een hoger aantal.

-

Gebruik aangepaste regels om gerelateerde fouten te groeperen die alleen verschillen door dynamische waarden.

## [Fouten en waarschuwingen oplossen](#fouten-en-waarschuwingen-oplossen-1)[](#fouten-en-waarschuwingen-oplossen-1)

Bij het onderzoeken van fouten vanuit de Foutrapporten pagina, gebruik de volgende benaderingen:

1.

Bekijk stacktraces  — Vouw foutregels uit om het aanroep pad te zien en het exacte script en regelnummer te identificeren waar de fout zich voordeed.

2.

Controleer op recente updates  — Houd nieuwe fouten in de gaten sinds je meest recente update.

3.

Gebruik ingebouwde tools :

-

[Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console)  (F9  in-game): Bekijk live fouten in real-time en test oplossingen.

-

[Script Profiler](/docs/nl-nl/studio/optimization/scriptprofiler) : Identificeer prestatiegerelateerde fouten veroorzaakt door dure bewerkingen.

-

Outputvenster in Studio  — Vang fouten tijdens de ontwikkeling voordat je publiceert.

4.

Gebruik uitsplitsingen  — Controleer of de fout specifiek is voor een platform (Desktop, Mobiel, Console) of OS (Windows, macOS, iOS, Android).

5.

Verzamel feedback van de gemeenschap  — Als je een community Discord of DevForum-post hebt, controleer dan of spelers het probleem melden en welke apparaten of regio's zijn getroffen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
