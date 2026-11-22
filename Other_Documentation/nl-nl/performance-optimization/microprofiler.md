<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/microprofiler -->

MicroProfiler | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)
6. /
7. [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)

# MicroProfiler

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De MicroProfiler  is een prestatie-optimalisatie- en probleemoplossingshulpmiddel in Roblox Studio en de Roblox-client. Het biedt gedetailleerde, visuele timinginformatie voor alle [engine-taken](/docs/nl-nl/performance-optimization/microprofiler/task-scheduler)  die tijdens een frame worden uitgevoerd, zoals het animeren van personages, het bijwerken van de fysica, het uitvoeren van scripts en het renderen van geometrie. Je kunt identificeren welke taken tijdens welk frame zijn uitgevoerd, hoe lang deze taken hebben geduurd en of ze ervoor hebben gezorgd dat je je frame-tijddoelen niet hebt gehaald.

## [Frame-tijden](#frame-tijden)[](#frame-tijden)

Om de MicroProfiler te gebruiken, moet je de relatie tussen frame-tijd  en frame-rate  begrijpen.

-

Frame-tijd is hoe lang een frame nodig had om op het scherm te worden weergegeven, meestal gemeten in milliseconden.

-

Frame-rate is het aantal frames dat op het scherm wordt weergegeven, meestal gemeten in frames per seconde (FPS).

Lagere frame-tijden betekenen een hogere frame-rate. Deel 1.000 milliseconden (1 seconde) door de frame-tijd om de frame-rate te krijgen.

| Gemiddelde frame-tijd | | Frames per seconde |
| --- | --- |
| 33,33 ms | | 30 FPS |
| 16,67 ms | | 60 FPS |
| 8,33 ms | | 120 FPS |
| 4,17 ms | | 240 FPS |

Voor een soepele gameplay is het echter niet genoeg om een hoge frame-rate te hebben. Je hebt consistente frame-tijden  nodig. Als bijvoorbeeld 59 frames in 10 milliseconden aankomen en één frame in 410 milliseconden, ervaren spelers een enorme, schokkende hapering, ook al draait het spel op 60 FPS. Als alle frames ongeveer dezelfde tijd nodig hebben om te renderen, zal je spel merkbaar soepeler aanvoelen door die consistentie, vooral bij lagere frame-rates.

De MicroProfiler richt zich volledig op frame-tijd . Het doel is om je te helpen frame-tijdspikes te identificeren en wat deze heeft veroorzaakt.

## [Open de MicroProfiler](#open-de-microprofiler)[](#open-de-microprofiler)

Het openen van de MicroProfiler verschilt per platform:

-

Op de mobiele client open je het Instellingen -menu en zet je de MicroProfiler op Aan . Navigeer vervolgens vanaf een ontwikkelingsmachine op hetzelfde netwerk  met je webbrowser naar het opgegeven IP-adres en poort.

 ![De MicroProfiler UI op mobiel.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-mobile.png)

Deze screenshot toont een IP-adres van 172.18.56.105  en een poort van 1338 , dus je navigeert naar 172.18.56.105:1338 . Afhankelijk van de netwerkconfiguratie van je apparaat, kun je meerdere IP-adressen zien. Als de ene niet werkt, probeer dan de volgende.

Standaard toont de MicroProfiler web UI de 30 meest recente frames van je mobiele apparaat. Voor een grotere set frames voeg je een schuine streep en een nummer toe aan de URL, zoals 172.18.56.105:1338/90 . Om een nieuwe set frames te krijgen, gebruik je de knop Her-capture .

-

Op de desktopclient druk je op Ctrl F6  (⌘ F6 ).

-

In Studio druk je op Ctrl F6  (⌘ F6 ).

Over het algemeen is de mobiele client de beste plek om je spel te profileren. De meeste spelers op Roblox gebruiken telefoons en tablets, en deze apparaten hebben ernstige thermische en energiebeperkingen die hun prestaties beperken. Als je spel goed draait op een midrange Android-tablet, presteert het vrijwel zeker veel beter op een gaming-desktop.

Krachtige apparaten zoals gaming-desktops kunnen prestatieproblemen zelfs verdoezelen, vooral als je een frame-rate limiet hebt ingesteld. Als je bijvoorbeeld de FPS op 60 op de client beperkt, merk je misschien het verschil niet tussen een frame-tijd van 4 milliseconden en 16 milliseconden, ook al is de laatste vier keer zo lang, omdat ze allemaal binnen 16,67 milliseconden aankomen. Op een mobiel apparaat dat moeite heeft om 30 FPS te halen, is een frame dat vier keer zo lang duurt (133 ms) moeilijk te missen.

## [MicroProfiler basisprincipes](#microprofiler-basisprincipes)[](#microprofiler-basisprincipes)

De MicroProfiler heeft twee belangrijke componenten: de frame-tijd staafgrafiek  en de gedetailleerde taak-tijdlijn .

-

De frame-tijd grafiek loopt langs de bovenkant van de interface en toont hoe lang elk frame nodig had om te renderen. Hogere staven betekenen langere frame-tijden.

-

De tijdlijn toont alle individuele taken die tijdens het frame zijn uitgevoerd. Brede staven vertegenwoordigen taken die langer nodig hadden om uit te voeren.

Een typische workflow in de MicroProfiler is om de frame-tijd grafiek te gebruiken om een piek (een hogere staaf) te identificeren en vervolgens de tijdlijn te gebruiken om te identificeren welke taken de piek hebben veroorzaakt. Vervolgens kun je de [Tag-referentie](/docs/nl-nl/performance-optimization/microprofiler/tag-table)  raadplegen voor informatie over de taak en hoe je de prestaties kunt verbeteren.

 ![Voorbeeld van een frame-tijdspiek.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-spike.png)

### [Frame-tijd grafiek](#frame-tijd-grafiek)[](#frame-tijd-grafiek)

De hoogte van elke staaf geeft het aantal milliseconden aan dat nodig was om het frame te voltooien. Meer recente frames bevinden zich aan de rechterkant. Beweeg de muis over een frame voor wat basisinformatie over CPU- en GPU-gebruik.

 ![De Microprofiler frame-grafiek, met blauwe frames en gedetailleerde frame-informatie.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-frames.png)

-

Oranje staven zijn frames waarin de Jobs Wall Time  de Render Wall Time  overschrijdt. In deze frames heeft ten minste één van de [werknemersdraad](#threads) , die dingen doet zoals scripts uitvoeren, fysica berekenen en animaties afspelen, langer geduurd dan de [hoofd renderdraad](#threads) .

Als het spel je frame-tijddoelen niet haalt en een groot aantal oranje frames heeft, zijn veelvoorkomende oorzaken scripts, fysica en animaties. Zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#scriptberekeningen) .

-

Blauwe staven zijn frames waarin de Render Wall Time  de Jobs Wall Time  overschrijdt. In deze frames heeft de hoofd renderdraad meer tijd nodig gehad dan een van de werknemersdraden.

Als het spel je frame-tijddoelen niet haalt en een groot aantal blauwe frames heeft, duidt dat op een render-bottleneck. Veelvoorkomende oorzaken zijn overmatige objectdichtheid, objectbeweging en verlichting. Zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#rendering) .

-

Rode staven zijn frames waarin twee voorwaarden waar zijn:

-

Render Wall Time  overschrijdt Jobs Wall Time

-

GPU Wait Time  is groter dan 2,5 milliseconden

Rode staven zijn minder gebruikelijk dan oranje en blauwe en zijn vaak het resultaat van overmatige objectcomplexiteit, textuurgrootte en visuele effecten. Optimalisatie is vergelijkbaar met blauwe staven. Zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#rendering) .

Kleine taken aan het einde van een frame kunnen soms de Jobs Wall Time  en Render Wall Time  verstoren, wat een goede reden is om je meer op frame-tijd te concentreren dan op frame-kleur. Er is geen "goede" kleur om naar te streven. Een mengeling van oranje, blauw en rood is niet problematisch zolang je je frame-tijddoelen haalt. Als je niet  je frame-tijddoelen haalt, kunnen de kleuren aangeven waar je moet optimaliseren.

### [Tijdlijn](#tijdlijn)[](#tijdlijn)

-

Klik met de linkermuisknop en sleep om de tijdlijn te verplaatsen. Op een machine met veel CPU-kernen moet je mogelijk behoorlijk omhoog of omlaag pannen om de [draad](#threads)  te vinden die een bepaalde taak uitvoert.

 ![De linkerkant van de Microprofiler gedetailleerd overzicht, met rijen voor threads.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-panning.png)

-

Scrollen zoomt de tijdlijn in en uit. In combinatie met de milliseconde-labels bovenaan de tijdlijn, kun je een idee krijgen van hoe lang een taak in absolute zin heeft geduurd, maar ook hoe lang het heeft geduurd ten opzichte van andere taken.

 ![De Microprofiler gedetailleerd overzicht met talrijke horizontale labels.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-timeline.png)

-

De groene overlay op de staafgrafiek geeft het aantal frames aan dat momenteel zichtbaar is op de tijdlijn—je zoomniveau. Klik met de linkermuisknop op een frame-staaf om naar die positie op de tijdlijn te springen.

Je moet mogelijk je zoomniveau aanpassen, maar als je met de muis over een staaf beweegt, wordt het frame op de tijdlijn gemarkeerd. Lichte grijze lijnen scheiden frames.

 ![De MicroProfiler staafgrafiek met groene overlay om het zoomniveau aan te geven.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-detailed.png)

-

Labels die direct onder een ander label verschijnen, geven taken aan die worden uitgevoerd als onderdeel van de hogere taak.

In plaats van de bovenliggende taak, wil je meestal de slecht presterende kindtaken oplossen; een bovenliggende taak kan niet korter zijn dan de som van zijn kindtaken.

-

Klik met de rechtermuisknop op een label om de tijdlijn precies naar de duur van die taak te zoomen.

-

Als de hoeveelheid informatie overweldigend is, gebruik dan het menu Groepen  of Threads  om de tijdlijn te filteren. Je wilt bijvoorbeeld misschien alleen Render -taken in de hoofdthread zien.

 ![De hover-weergave voor een label, met Groep gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-group.png)

-

Gebruik Ctrl F  (⌘ F ) om naar de gebeurtenis van een taak te springen die de meeste tijd in de dump in beslag neemt. Bijvoorbeeld, computeLightingPerform  draait in elk clientframe. Als je ernaar zoekt in een dump met 128 frames, kun je naar het frame springen waar het de meeste tijd nodig had om te voltooien.

## [Threads](#threads)[](#threads)

Net als veel programma's gebruikt Roblox meerdere threads om taken gelijktijdig uit te voeren. De MicroProfiler toont de threadnaam aan de linkerkant van de tijdlijn.

 ![De linkerkant van de Microprofiler gedetailleerd overzicht, met rijen voor threads.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-panning.png)

Er zijn drie belangrijke threadtypes:

-

Hoofd  ("RBX Hoofd"): Behandelt CPU-gebaseerde renderingstaken. Verwerkt invoer, [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid) , animaties/tweens, fysica-eigendom, geluid en wacht op script-hervattingen. Werkt ook Studio-interfaces bij en coördineert de andere threads.

-

Werknemer  ("RBX Werknemer"): Helpt de hoofdthread met netwerken, fysica en padfinding. Vanwege het aantal kernen in moderne CPU's heb je waarschijnlijk veel werknemersdraden, waarvan de meeste op elk moment in een slaaptoestand zijn.

-

Render  ("GPU"): Volgt een "voorbereiden, uitvoeren, presenteren" logica. Communiceert met de grafische verwerkingsunit (GPU) van het apparaat.

-

Voorbereiden: Informatie van de hoofdthread wordt gebruikt om rendermodellen bij te werken.

-

Uitvoeren: Geeft renderopdrachten uit, inclusief 2D-interfaces.

-

Presenteren: Synchroniseert met de GPU.

## [Aangepaste scriptprofielen](#aangepaste-scriptprofielen)[](#aangepaste-scriptprofielen)

Als je scripts ingewikkelde taken uitvoeren, kun je kritieke delen van de code profileren om ervoor te zorgen dat ze niet te lang duren. Wikkel code met [debug.profilebegin()](/docs/nl-nl/reference/engine/libraries/debug#profilebegin)  en [debug.profileend()](/docs/nl-nl/reference/engine/libraries/debug#profileend)  om alles te timen wat tussen die functieaanroepen wordt gedaan en een label op de MicroProfiler-tijdlijn te creëren.

```

local RunService = game:GetService("RunService")

local function onPreSimulation()

  debug.profilebegin("Hard Werk")

  -- Voorbeeld van hard werk: verwissel twee variabelen 200.000 keer

  local a, b = 0, 1

  for _ = 1, 200000 do

    a, b = b, a

  end

  debug.profileend()

end

RunService.PreSimulation:Connect(onPreSimulation)

```

 ![Veel labels op de MicroProfiler, met een aangepast label dat het grootste deel van de verwerkingstijd in beslag neemt.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/custom-profile.png)

Aan de duur op de tijdlijn kun je zien dat de functie veel verwerkingstijd gebruikt in vergelijking met andere taken.

## [Analyseer captures met Assistant](#analyseer-captures-met-assistant)[](#analyseer-captures-met-assistant)

In Studio kun je [Assistant](/docs/nl-nl/assistant/guide)  vragen om automatisch een gepauzeerde MicroProfiler-capture te analyseren, prestatieknelpunten te identificeren en oplossingen voor te stellen.

1.

Open in Studio de MicroProfiler met Ctrl F6  (⌘ F6 ).

2.

Wanneer je een frame-tijdspiek ziet, pauzeer je de capture door op Pauze  in het bovenste menu te drukken of door Ctrl P  (⌘ P ) te gebruiken.

3.

Open Assistant en vraag het om de capture te analyseren. Voorbeeldprompts zijn:

-

"Ik heb een frame-tijdspiek vastgelegd in de MicroProfiler—analyseer het."

-

"Wat veroorzaakte de piek?"

-

"Is het fysica-gebonden of script-gebonden?"

-

"Welke categorie heeft de hoogste exclusieve tijd?"

-

"Wanneer ik in de hangar ben, daalt de FPS. Reproduceer het probleem, gebruik MicroProfiler om de oorzaak te vinden, los het op en test opnieuw."

Assistant leest de gepauzeerde capture via de MicroProfiler API en retourneert een rapport over waarschijnlijke knelpunten, samen met voorgestelde script- of scènewijzigingen die je kunt toepassen.

Deze functionaliteit werkt ook via de [Studio MCP](/docs/nl-nl/studio/mcp)  server, zodat je MicroProfiler-analyses kunt integreren in je eigen AI-agent of agentische lus om geautomatiseerde feedback te krijgen over hoe nieuwe wijzigingen de prestaties van je spel beïnvloeden.

## [Sla framegegevens op](#sla-framegegevens-op)[](#sla-framegegevens-op)

Als je een set framegegevens wilt opslaan voor latere beoordeling (of om met iemand anders te delen), gebruik dan de knop Opslaan naar bestand . De MicroProfiler slaat framegegevens op in een standalone HTML-bestand met de naam microprofile-<datum>-<tijd>.html .

 ![De opslaan naar bestand knop in de web UI.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-save-to-file.png)

Op de desktopclient of in Studio gebruik je het menu Dump . In beide gevallen slaat de MicroProfiler automatisch het bestand op in de Roblox-logdirectory:

-

Op Windows, controleer %LOCALAPPDATA%\Roblox\logs .

Als je de Universal Windows Platform (UWP) app gebruikt, controleer dan \Users\<gebruikersnaam>\AppData\Local\Packages\ROBLOXCORPORATION.ROBLOX_<hash>\LocalState\logs\ .

-

Op macOS, controleer ~/Library/Logs/Roblox .

Dump bevat alleen gegevens voor het geselecteerde aantal frames, niet  de gehele duur dat het spel is uitgevoerd. De uitzondering is de [tellersmodus](/docs/nl-nl/performance-optimization/microprofiler/modes#counters-modus) , die gegevens bevat van wanneer Studio of de client begon te draaien tot het moment van de dump.

## [Profiel de server](#profiel-de-server)[](#profiel-de-server)

Naast het profileren van de client, kun je korte dumps van serveractiviteit vastleggen:

1.

Op de desktopclient, sluit je je aan bij een spel waarvoor je bewerkingsrechten hebt.

2.

Open de Ontwikkelaarsconsole met Ctrl F9  (⌘ F9 ).

3.

Selecteer in het dropdownmenu MicroProfiler .

4.

Geef in het Server -tabblad het aantal frames op dat je wilt vastleggen (maximaal 60) en het aantal seconden dat je wilt vertragen voordat je de capture start (maximaal 4).

5.

Klik op Begin serveropname .

 ![Het MicroProfiler-scherm van de Ontwikkelaarsconsole.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-server.png)

Na een paar seconden geeft de Ontwikkelaarsconsole het pad naar het bestand, dat hetzelfde pad is als een [standaard dump](#sla-framegegevens-op) .

## [Web-only functies](#web-only-functies)[](#web-only-functies)

De MicroProfiler heeft twee gebruikersinterfaces: de web UI (mobiel en dumps) en de desktop UI (client en Studio). We raden aan om de web UI zoveel mogelijk te gebruiken. Over het algemeen werken de twee op een vergelijkbare manier, maar de web UI heeft een paar extra functies:

-

Gebruik het menu X-Ray  om kleurcodering voor geheugenallocatie in of uit te schakelen.

 ![De MicroProfiler webweergave met röntgen zichtbaar.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-xray.png)

-

Lichtere frames binnen de hoofdstaafgrafiek geven hogere geheugenallocatie aan.

-

Lichtere delen van de preview-staaf en lichtere labels op de tijdlijn geven delen van het frame aan met hogere geheugenallocatie.

-

In de röntgenmodus, druk op C  om de totale grootte van de geheugenallocaties weer te geven in plaats van het aantal allocaties.

-

Gebruik het menu Exporteren  om een CPU- of geheugen-vlamgrafiek te exporteren, een gespecialiseerde visualisatie die alle oproepstapels in de dump aggregeert, de ouder-kind hiërarchie behoudt en ze op basis van duur dimensioneert. Vlamgrafieken zijn vooral nuttig voor het identificeren van taken die je niet laten missen je frame-tijddoelen (en daarom moeilijk te merken zijn), maar zo vaak draaien dat hun verwerkingstijd significant wordt.

 ![De MicroProfiler vlamgrafiek in de web UI.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-flame.png)

Je kunt ook vlamgrafieken in Studio maken, hoewel alleen voor scripts (uitvoertijd en geheugenallocaties). In vergelijking met de web-gebaseerde vlamgrafieken zijn de vlamgrafieken in Studio van boven naar beneden in plaats van van onder naar boven en ondersteunen ze dramatisch langere vastleg tijden.

 ![De MicroProfiler vlamgrafiek in Studio.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-studio-flame.png)

-

Sleep en zet een tweede dumpbestand in de web UI om een diff-vlamgrafiek te genereren, die je kan helpen verbeteringen of regressies in de prestaties van je spel in de loop van de tijd te identificeren. Klik op Combineer & Vergelijk  om een nieuw HTML-bestand te exporteren.

 ![De MicroProfiler diff-vlamgrafiek bouwer die de linker- en rechterzijde toont.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-flame-diff.png)

Je kunt verschillende dumpbestanden combineren—bijvoorbeeld vier aan elke kant, van voor en na een grote update—om een meer geaggregeerde vergelijking te krijgen. Het vergelijken van gegevens tussen verschillende plaatsen kan ook nuttig zijn, maar combineer geen gegevens van verschillende plaatsen!

De diff-vlamgrafiek benadrukt de dump (links of rechts) die meer CPU of geheugen verbruikt, met helderdere kleuren die een groter verschil aangeven.

 ![De MicroProfiler diff-vlamgrafiek.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-flame-diff2.png)

## [Desktop-only functies](#desktop-only-functies)[](#desktop-only-functies)

Op de desktoptijdlijn, klik met de linkermuisknop op een label om het toe te voegen aan een lijngrafiek in de rechterbenedenhoek. De grafiek toont de tijd die de taak elke frame in beslag neemt. Met deze grafiek kun je de prestaties van alleen bepaalde taken in je spel testen. Wanneer je klaar bent, klik met de rechtermuisknop op de grafiek om deze te verbergen.

 ![De grafiek die toont hoe lang taken per frame duren.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-graph.png)

Deze grafiek is gesynchroniseerd met de hoofdprofilerstaven. Het momenteel geselecteerde framebereik is groen gemarkeerd in de grafiek. Je kunt ook ergens op deze grafiek klikken om de hoofdprofilerweergave opnieuw te centreren op dat specifieke frame, wat nuttig is voor het vinden van pieken in de gedetailleerde weergave.

Gebruik het menu Opties  om de referentielijn op de grafiek naar een ander aantal milliseconden te wijzigen.

### [Zoek in de gedetailleerde weergave](#zoek-in-de-gedetailleerde-weergave)[](#zoek-in-de-gedetailleerde-weergave)

Op de desktopclient kun je naar taken zoeken op naam in de Gedetailleerd -weergave:

1.

Open de MicroProfiler met Ctrl F6  (⌘ F6 ) en schakel over naar de Gedetailleerd -modus.

2.

Druk op Ctrl F  (⌘ F ) om het zoekvak te openen.

3.

Typ een deel van een taak- of labelnaam. Overeenkomsten zijn niet hoofdlettergevoelig en vinden de tekst overal in de naam. Overeenkomende labels behouden hun kleur en alle andere labels worden gedimd. Frames die een overeenkomst bevatten, worden gemarkeerd in de frame-tijdgrafiek.

4.

Beweeg tussen overeenkomsten:

| Actie | | Sneltoets |
| Volgende overeenkomst | | F3  of Enter |
| Vorige overeenkomst | | Shift F3  of Shift Enter |

Je kunt ook op de <  en >  knoppen naast het zoekvak klikken. De huidige overeenkomst is omrand en gemarkeerd met een driehoek erboven, en een teller zoals 12 / 340  toont zijn positie onder alle overeenkomsten. Als de overeenkomst buiten het scherm is, scrollt de tijdlijn ernaartoe. Als je de tijdlijn hebt gepand, gaat de navigatie verder vanaf de overeenkomsten die momenteel zichtbaar zijn.

5.

Druk op Esc , of druk opnieuw op Ctrl F  (⌘ F ) om de zoekopdracht te sluiten. Het sluiten van de zoekopdracht sluit de MicroProfiler niet.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
