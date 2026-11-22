<!-- Source: https://create.roblox.com/docs/nl-nl/studio/debugging -->

Foutopsporing | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Foutopsporing

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Studio biedt veel foutopsporingshulpmiddelen en workflows die vaak worden aangetroffen in geïntegreerde ontwikkelomgevingen (IDE's). Deze helpen je om fouten in scripts te inspecteren en op te lossen terwijl ze worden uitgevoerd.

## [Breakpoint-foutopsporing](#breakpoint-foutopsporing)[](#breakpoint-foutopsporing)

Breakpoints zijn controlepunten die de uitvoering van je scripts op specifieke regels pauzeren of "onderbreken". Je kunt de pauzes gebruiken om je spel te inspecteren en te debuggen, [toezicht](#toezicht)  te houden op variabelen en de [aanroepstack](#aanroepstack)  te inspecteren. Breakpoints zijn een van de meest effectieve manieren om functies te debuggen, dus ze zijn een van de belangrijkste foutopsporingshulpmiddelen.

### [Beheer](#beheer)[](#beheer)

In de [Script Editor](/docs/nl-nl/studio/script-editor)  kun je [invoegen](#invoegen)  verschillende soorten breakpoints en de configuratie van een breakpoint op elk moment bewerken, ook tijdens playtest-sessies. Als je breakpoints tijdens een playtest-sessie bewerkt, blijven de bewerkingen bestaan, zelfs nadat je deze hebt beëindigd. Je kunt ook een breakpoint bewerken dat actief je playtest-sessie pauzeert, maar wijzigingen worden pas toegepast tijdens de volgende playtest-sessie.

#### [Invoegen](#invoegen)[](#invoegen)

Breakpoints hebben meerdere variaties en kunnen op elke regel van uitvoerbare code worden ingevoegd, zoals volgt:

Standaard Voorwaardelijk Logpoint Tijdelijk

Om een standaard breakpoint op een regel code in te voegen, klik je in de marge direct rechts van het regelnummer. Alternatief kun je met de rechtermuisknop in de marge klikken en Invoegen Breakpoint  selecteren. Het breakpoint-pictogram verschijnt als een rode cirkel.

![Standaard breakpoint weergegeven in de scriptmarge](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint.png)

#### [Uitschakelen](#uitschakelen)[](#uitschakelen)

Om een breakpoint tijdelijk uit te schakelen zonder het te [verwijderen](#verwijderen) , gebruik je een van de volgende workflows:

-

Klik op het pictogram van het breakpoint.

-

Klik met de rechtermuisknop op het pictogram van het breakpoint en selecteer Breakpoint Uitschakelen .

-

[Bewerk](#bewerken)  het breakpoint en schakel het Ingeschakeld  selectievakje uit.

Een uitgeschakeld breakpoint verschijnt als een holle versie van het ingeschakelde pictogram, bijvoorbeeld een holle cirkel voor een uitgeschakeld standaard breakpoint, of een holle diamant voor een uitgeschakeld logpoint.

![Uitgeschakeld standaard breakpoint weergegeven in de scriptmarge](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint-Disabled.png) Uitgeschakeld standaard breakpoint

![Uitgeschakeld logpoint weergegeven in de scriptmarge](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint-Logpoint-Disabled.png) Uitgeschakeld logpoint

#### [Verwijderen](#verwijderen)[](#verwijderen)

Om een breakpoint te verwijderen, klik je met de middelste muisknop op het pictogram of klik je met de rechtermuisknop op het pictogram en selecteer je Breakpoint Verwijderen .

Het verwijderen van een breakpoint verwijdert de Voorwaarde  en Logbericht . Als je deze informatie wilt behouden voor toekomstige foutopsporing, [schakel](#uitschakelen)  het breakpoint dan in plaats daarvan uit.

#### [Bewerken](#bewerken)[](#bewerken)

Je kunt de configuratie van een breakpoint op elk moment bewerken, ook tijdens playtest-sessies. Als je breakpoints tijdens een playtest-sessie bewerkt, blijven de bewerkingen bestaan, zelfs nadat je deze hebt beëindigd. Je kunt ook een breakpoint bewerken dat actief je playtest-sessie pauzeert, maar wijzigingen worden pas toegepast tijdens de volgende playtest-sessie.

Om een breakpoint te bewerken:

1.

Klik met de rechtermuisknop op het pictogram van het breakpoint en selecteer Breakpoint Bewerken .

2.

In het Breakpoint Bewerken  venster, configureer je het breakpoint zoals gewenst. Je kunt deze configuraties combineren om het beste aan je foutopsporingsbehoeften te voldoen.

| Optie | | Beschrijving |
| --- | --- |
| Voorwaarde | | Een optionele expressie die bepaalt of het breakpoint wordt geactiveerd. Als de voorwaarde leeg is, wordt het breakpoint altijd geactiveerd. Als de voorwaarde bestaat, wordt het breakpoint een [voorwaardelijk breakpoint](#invoegen)  en wordt het alleen geactiveerd als de voorwaarde waar is. Bijvoorbeeld, als je wilt dat het breakpoint alleen wordt geactiveerd als de variabele var  gelijk is aan 10 , stel je de voorwaarde in op var == 10 . |
| Log bericht | | Een expressie die naar het [Output](/docs/nl-nl/studio/output)  venster wordt afgedrukt wanneer het breakpoint wordt geraakt. Het formaat van het logbericht is hetzelfde als dat van een [print()](/docs/nl-nl/reference/engine/globals/LuaGlobals#print)  statement. Stel bijvoorbeeld het logbericht in als "De waarde van var:", var  om hetzelfde bericht uit te voeren als print("De waarde van var:", var) . |
| Voortzetten uitvoering | | Bepaalt of het breakpoint het script pauzeert als het wordt geactiveerd. Deze optie is standaard uitgeschakeld, tenzij het ingevoegde breakpoint een [logpoint](#invoegen)  is. |
| Verwijder Breakpoint bij Hit | | Als aangevinkt, verwijdert het breakpoint zichzelf automatisch na de eerste playtest-sessie, waardoor het effectief een [tijdelijk](#invoegen)  breakpoint wordt. |
| Trigger Bij | | De context  van een breakpoint bepaalt of het moet worden geactiveerd op de Client  (client-side scripts), Server  (server-side scripts) of Bewerken  (debugging [plugin](/docs/nl-nl/studio/plugins)  scripts). Als je Aangepaste Context  kiest, geeft het venster de huidige triggercontexten aan. |

### [Workflow](#workflow)[](#workflow)

De typische workflow voor breakpoint-foutopsporing is als volgt:

1.

Open het script dat je wilt debuggen en [voeg breakpoints](#invoegen)  in op de regels code die je wilt onderzoeken.

2.

Start vanuit de mezzanine van Studio een [playtest](/docs/nl-nl/studio/testing-modes#spelen-testen)  om te beginnen met debuggen.

 ![Testoptie in de dropdown voor testmodi van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

3.

Wanneer het script een breakpoint raakt, pauzeert  de playtest-sessie, tenzij dat breakpoint is [geconfigureerd](#bewerken)  om de uitvoering voort te zetten. Een gele pijl boven het breakpoint geeft aan welke regel code als volgende wordt uitgevoerd.

 ![Actief breakpoint in de debugger met gele pijl](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Gutter-Breakpoint-Active.png)

4.

Terwijl het script pauzeert, inspecteer je het [Breakpoints](#breakpoints)  venster, [Toezicht](#toezicht)  venster, [Aanroepstack](#aanroepstack)  venster, [Output](/docs/nl-nl/studio/output)  venster en [Script Editor](#script-editor)  om informatie te vinden over variabele waarden en functie-uitvoeringen.

5.

Om de uitvoering van de code na het raken van een breakpoint voort te zetten, klik je op Scripts Hervatten  in de mezzanine.

 ![Hervatten Scripts-knop aangegeven in de mezzanine van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Resume-Scripts.png)

Je kunt ook code regel voor regel uitvoeren met de stapknoppen in de mezzanine:

 ![Breakpoint stapknoppen aangegeven in de mezzanine van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Tools.png)

| Actie | | Sneltoets | | Beschrijving |
| Stap In | | F11 | | De Stap In  knop verplaatst de debugger naar de code van de functie op de huidige regel. Als er geen functie op de huidige regel is, verplaatst de debugger zich naar de volgende regel. |
| Stap Over | | F10 | | De Stap Over  knop verplaatst de debugger naar de volgende regel code, zonder  in functies te gaan. |
| Stap Uit | | Shift F11 | | De Stap Uit  knop verplaatst de debugger uit de huidige functie en naar de volgende regel code na de functieaanroep. Als de huidige regel zich niet binnen een functie bevindt, verplaatst de debugger zich naar de volgende regel. |

6.

Wanneer je klaar bent met debuggen in de huidige sessie, klik je op de Stop  knop.

 ![Stopknop aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Stop.png)

### [Monitoring](#monitoring)[](#monitoring)

Studio bevat meerdere vensters en hulpmiddelen om variabele waarden en functie-uitvoeringen te monitoren tijdens het debuggen. Met deze informatie kun je de oorzaak van de meeste problemen in je scripts vinden.

 ![Breakpoint-knop aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Debugging-Tools.png)

#### [Breakpoints](#breakpoints)[](#breakpoints)

Het Breakpoints  venster is een uniforme weergave die alle breakpoints binnen alle scripts toont. Om het te openen, klik je op Breakpoints  in de werkbalk van het Script  tabblad van Studio, of navigeer naar het Venster  ⟩ Debug  menu en schakel Breakpoints  in.

In het venster worden de kolommen Script  en Regel  altijd weergegeven, en je kunt andere [configuratie](#bewerken)  kolommen in- of uitschakelen via het ⋮  menu in de rechterbovenhoek. Binnen de Script  kolom kun je met de rechtermuisknop op een breakpoint klikken om een optiesmenu te onthullen om te [bewerken](#bewerken) , [uitschakelen/inschakelen](#uitschakelen) , [verwijderen](#verwijderen)  of naar de regel van het breakpoint binnen het script te springen.

 ![Breakpoints venster in Studio](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Breakpoints-Window.png)

Tijdens een debug-sessie toont de meest linkse kolom (x3)  wat de meerdere contexten (Client , Server , Bewerken ) voor het breakpoint aangeeft. Door een tak van een breakpoint uit te vouwen, kun je vervolgens op het pictogram naast een specifieke context klikken om deze voor die context te [deactiveren/activeren](#uitschakelen) , zoals het uitschakelen van een breakpoint alleen in de Client  context terwijl deze ingeschakeld blijft in de Server  context.

 ![Breakpoint uitgebreid om contexten te tonen](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Breakpoints-Window-Contexts.png)

#### [Aanroepstack](#aanroepstack)[](#aanroepstack)

Het Aanroepstack  venster, toegankelijk vanuit de werkbalk van het Script  tabblad van Studio of het Venster  ⟩ Debug  menu, toont welke regel code als volgende zal worden uitgevoerd wanneer de debugger een breakpoint bereikt. Als je functies vanuit andere functies aanroept, geeft het aan van welke regels die functies zijn aangeroepen, zodat je kunt bevestigen of de werkelijke aanroepstroom overeenkomt met de verwachte stroom.

 ![Aanroepstackstroom in een script](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Call-Stack-Flow-Script.png)  ![Aanroepstackstroom in het Aanroepstack venster](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Call-Stack-Flow-Window.png)

Terwijl het script pauzeert bij breakpoints, gebruik je de stapknoppen in de mezzanine om in, over of uit een functie/regel te stappen zoals beschreven in de [workflow](#workflow) .

 ![Breakpoint stapknoppen aangegeven in de mezzanine van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Debug-Tools.png)

#### [Toezicht](#toezicht)[](#toezicht)

Het Toezicht  venster, toegankelijk vanuit de werkbalk van het Script  tabblad van Studio of het Venster  ⟩ Debug  menu, stelt je in staat om actief variabele en expressiewaarden te bekijken terwijl je door breakpoints stapt.

Variabelen Mijn Toezicht

Het Variabelen  tabblad toont informatie over de huidige variabelen in [scope](/docs/nl-nl/luau/scope) , filterbaar door op de knop Alle Scopes  in de bovenste balk van het venster te klikken. Het uitbreiden van een tak toont de leden van die variabele of instantie en hun waarden. Je kunt ook elke variabele in de gaten houden door deze dubbel te klikken in de [Script Editor](/docs/nl-nl/studio/script-editor) , met de rechtermuisknop te klikken en Toevoegen Toezicht  uit het pop-upmenu te selecteren.

![Variabelen om in de gaten te houden binnen een script](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Watch-Variables-Script.png)![Informatie over variabelen in het Toezicht venster](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Watch-Variables-Window.png)

#### [Script Editor](#script-editor)[](#script-editor)

De debugger is geïntegreerd met de [Script Editor](/docs/nl-nl/studio/script-editor) . Wanneer je spel pauzeert bij een breakpoint in een script, kun je met de muis over de naam van een variabele zweven om de waarde ervan te zien. Bijvoorbeeld, je kunt de samenstelling van een tabel en de daarin opgenomen sleutels/waarden zien.

 ![Muisover een variabele in Script Editor om waarde te tonen](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Script-Editor-Mouseover-Table.png)

## [Aanvullende foutopsporingshulpmiddelen](#aanvullende-foutopsporingshulpmiddelen)[](#aanvullende-foutopsporingshulpmiddelen)

Naast de debugger biedt Studio aanvullende foutopsporingshulpmiddelen om problemen en bugs in je spel op te lossen.

### [Opdrachtbalk](#opdrachtbalk)[](#opdrachtbalk)

De [Opdrachtbalk](/docs/nl-nl/studio/overview#opdrachtbalk)  stelt je in staat om Luau-opdrachten uit te voeren terwijl het spel draait. Het is beschikbaar in Studio via het Venster  ⟩ Script  menu en in de [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console) .

### [Ontwikkelaarsconsole](#ontwikkelaarsconsole)[](#ontwikkelaarsconsole)

De [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console)  biedt een breed scala aan details, waaronder client- en serveruitvoer, geheugengebruik, netwerkprestaties en meer. Om de console te openen tijdens het testen of spelen van een spel, typ je /console  in de chat of druk je op F9 .

### [Logbestanden](#logbestanden)[](#logbestanden)

Wanneer een script afdrukt of fouten in Studio of de speler-app, registreert de app het bericht in een logbestand in het lokale bestandssysteem. Deze bestanden bevinden zich op verschillende plaatsen, afhankelijk van het besturingssysteem.

#### [Windows](#windows)[](#windows)

Om logbestanden op Windows te openen:

1.

Open Verkenner .

2.

Navigeer naar de %LOCALAPPDATA%\Roblox\logs  directory.

3.

Dubbelklik op een log om deze te openen. Logs met dezelfde XXXXX  waarde zijn afkomstig van dezelfde Studio-sessie.

#### [Mac](#mac)[](#mac)

Om logbestanden op Mac te openen:

1.

Open Finder .

2.

Selecteer in de menubalk Ga  ⟩ Ga naar map... .

3.

Voer in het dialoogvenster ~/Library/Logs/Roblox  in.

4.

Dubbelklik op het resultaat om naar de Roblox logs directory te navigeren.

5.

Dubbelklik binnen de directory op een log om deze te openen.

#### [iOS](#ios)[](#ios)

Je kunt iOS-logs verzamelen met een Mac of met een iOS-apparaat.

Mac Apparaat

Om iOS-logbestanden op een Mac te openen:

1.

Verbind het iOS-apparaat met een Mac.

2.

Open Finder .

3.

Navigeer naar Hulpprogramma's  en open de Console  applicatie.

4.

Om realtime logs in de Console-applicatie te populeren, selecteer je het iOS-apparaat in de zijbalk, klik je op de Start  knop en reproduceer je het probleem op het iOS-apparaat.

5.

Om gearchiveerde logs in de Console-applicatie te populeren, voer je sudo log collect --device-name "[iOS Device Name]"  in de Terminal  uit. Zorg ervoor dat er geen apostrofs in de naam van het apparaat staan, anders krijg je mogelijk een foutmelding bij het uitvoeren van de opdracht.

#### [Android](#android)[](#android)

Om logbestanden op Android te openen:

1.

Navigeer naar Instellingen  ⟩ Systeem  ⟩ Ontwikkelaarsopties .

2.

Zet Ontwikkelaarsopties  aan.

3.

Download en installeer op een computer [Android Studio](https://developer.android.com/studio) .

4.

Klik in Android Studio op Logcat .

5.

Verbind het Android-apparaat met de computer om automatisch Logcat  met logs te vullen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
