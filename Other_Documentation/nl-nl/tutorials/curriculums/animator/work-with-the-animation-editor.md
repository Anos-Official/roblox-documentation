<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/animator/work-with-the-animation-editor -->

Werken met de Animatie-editor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Werken met de Animatie-editor

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Animatie-editor  stelt je in staat om de lichaamsdelen van je personages te verplaatsen en te draaien, zoals een actiefiguur, in unieke poses op verschillende keyframes van een animatie. Studio maakt vervolgens automatisch keyframes tussen die poses die samen vloeien, zodat je personages lijken te bewegen.

In dit hoofdstuk verkennen we hoe je de Animatie-editor  opent, je instellingen aanpast om te helpen bij het poseren van je personage, en een animatie maakt met twee unieke poses die Studio samenvoegt zodat het lijkt alsof het personage in het water zwemt.

## [Open Animatie-editor](#open-animatie-editor)[](#open-animatie-editor)

De Animatie-editor  is de primaire animatietool van Studio. Hoewel het veel functionaliteit biedt, zoals [animatie-opname](/docs/nl-nl/animation/capture)  en [inverse kinematica](/docs/nl-nl/animation/inverse-kinematics)  tools, richt deze les zich op de basisgereedschappen om je te helpen beginnen met het leren maken van animaties.

1.

Ga bovenaan de werkbalk naar het tabblad Avatar .

2.

Klik op de knop Clip-editor . De Animatie-editor  wordt onderaan Studio weergegeven.

## [Bereid rig voor](#bereid-rig-voor)[](#bereid-rig-voor)

De Animatie-editor  vereist een rig , of poseerbaar figuur, om karakteranimaties te maken, omdat rigs de interne structuur bevatten die je nodig hebt om lichaamsdelen in verschillende poses te verplaatsen en te draaien. Hoewel je je eigen rigs kunt maken of toegang kunt krijgen tot verschillende vooraf gebouwde rigs via de tool Rig Generator , biedt deze les een rig bovenop het voetstuk in het spel.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/creating-animations/highlight-figure.jpg)

Om je rig voor te bereiden:

1.

Selecteer de Figure  rig bovenop het voetstuk. De part-namen die de lichaamsdelen van de rig vormen, worden weergegeven in de Animatie-editor .

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/creating-animations/rig-selected.jpg)

2.

Zoek in de werkbalk de snap-tools en zorg ervoor dat Draaien  en Verplaatsen  niet zijn aangevinkt.

 ![](https://prod.docsiteassets.roblox.com/assets/education/general/Snap-Settings-C.png)

3.

Gebruik de camerabesturingen om de camera te verplaatsen voor een goed zicht op het deel dat je wilt animeren. Houd tijdens het verplaatsen Shift  ingedrukt om de camerabewegingen te vertragen.

| Actie | | Besturing |
| --- | --- |
| Verplaatsen | | W  A  S  D |
| Draaien | | Houd de rechtermuisknop ingedrukt om rond het geselecteerde object te draaien. |
| Inzoomen | | Gebruik het scrollwiel van je muis. |
| Focus | | Druk op F  om op het geselecteerde object te focussen. |

Kun je de camera niet verplaatsen?

 Als de camera niet beweegt wanneer je op W  A  S  D  drukt, klik dan ergens binnen het 3D-viewport.

## [Maak de eerste pose](#maak-de-eerste-pose)[](#maak-de-eerste-pose)

Nu de Animatie-editor  is geopend en je rigvoorbereiding is voltooid, is het tijd om je personage te poseren voor de eerste pose van je animatie. Deze les richt zich op een zwemanimatie, maar voel je vrij om de lessen aan te passen voor je eigen poses. Afhankelijk van de animatie die je wilt maken, kan je eerste pose heel anders zijn.

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/create-the-first-pose/example-swim.jpeg) Zwemmend

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/create-the-first-pose/example-crouch.jpeg) In elkaar gedoken

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/create-the-first-pose/example-dance.jpeg) Dansen

Het creëren van poses is een kunstvorm, en het kost tijd om uit te vinden hoe je lichaamsdelen moet verplaatsen en draaien om aan de behoeften van je animatie te voldoen. Het is normaal en te verwachten dat je poses er anders uitzien en aanvoelen dan de video-voorbeelden in de les.

Om je eerste pose voor een zwemanimatie te maken:

1.

Ga terug naar de werkbalk, selecteer de Draaien  tool en klik vervolgens op de LeftUpperArm  van de rig. Een set handgrepen wordt rond het lichaamsdeel weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/education/general/Rotate-Tool.png)

2.

Klik en sleep de handgrepen om de linkerarm van de rig te draaien, en let op hoe elke handgreep de arm in een andere richting draait. Je kunt elke wijziging ongedaan maken door op Ctrl Z  of ⌘ Z  te drukken, afhankelijk van je computer.

3.

Draai verschillende lichaamsdelen totdat je eerste pose compleet is. Zorg ervoor dat je de camerahoek verandert terwijl je werkt, zodat je de pose vanuit meerdere hoeken kunt zien.

Als je problemen ondervindt bij het proberen te draaien van de lichaamsdelen van je rig, bekijk dan de volgende probleemoplossingstips:

Probleem:  Je kunt niet op de draaigrepen klikken.

-

Een ander deel kan je klik blokkeren.

-

Probeer rond je camera te draaien totdat je een blauwe doos ziet telkens wanneer je boven het deel waar je op wilt klikken zweeft.

Probleem:  Je kunt de draaigrepen niet zien.

-

Als je een set pijlen ziet in plaats van de cirkels, moet je de Draaien  tool in de werkbalk selecteren.

## [Dupliceer keyframes](#dupliceer-keyframes)[](#dupliceer-keyframes)

Voordat je aan je tweede pose begint, laten we even de tijd nemen om je eerste pose aan het einde van je animatie te dupliceren. Dit proces zorgt ervoor dat je animatie soepel herhaalt terwijl deze in een lus draait.

Om je eerste pose naar het einde van de animatie te verplaatsen, moet je de scrubber  die de huidige keyframepositie markeert naar het einde van de tijdlijn verplaatsen. De tijdlijn  is de genummerde lijn bovenaan de Animatie-editor  die je animatie in seconden vertegenwoordigt.

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/looping-animations/Scrubber.png) Scrubber

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/looping-animations/Timeline.png) Tijdlijn

Om de keyframes van je eerste pose naar het einde van de animatie te dupliceren:

1.

Klik in de Animatie-editor  op de witte diamant  bovenaan de tijdlijn. Deze diamant vertegenwoordigt de rotatiegegevens van elk lichaamsdeel voor je eerste pose op 0:00  op de tijdlijn. Let op dat de witte diamant met een blauwe rand wordt weergegeven wanneer je deze stap correct hebt uitgevoerd.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/looping-animations/select-first-pose-diamond.png)

2.

Kopieer de eerste pose door op Ctrl C  of ⌘ C  te drukken, afhankelijk van je computer.

3.

Klik op de scrubber  en sleep deze naar het einde van de animatie op 1:00  op de tijdlijn.

4.

Plak je eerste pose op deze nieuwe tijdlijnpositie door op Ctrl V  of ⌘ V  te drukken, afhankelijk van je computer. Een nieuwe set diamanten wordt aan het einde van de keyframe weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/looping-animations/added-last-pose.png)

5.

Om de animatie in een lus te laten draaien, klik je op het Loop -icoon. Je animatie zal nu naadloos herhalen.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/adding-the-second-pose/press-loop-button.png)

## [Maak de tweede pose](#maak-de-tweede-pose)[](#maak-de-tweede-pose)

Met hetzelfde proces als eerder in de les, is het tijd om je tweede pose te maken! Nadat je deze unieke pose hebt ontworpen, zal Studio automatisch keyframes tussen die poses creëren die samen vloeien, zodat je personages lijken te zwemmen.

Om je tweede pose voor een zwemanimatie te maken:

1.

Zet de scrubber in het midden van de animatie. Je kunt de scrubber naar ongeveer het midden van de tijdlijn slepen, of je kunt deze handmatig instellen op 0.5  in de positie-indicator  links van de tijdlijn.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-island-of-move/adding-the-second-pose/set-timeline-middle.png)

2.

Met de Draaien  tool nog steeds actief, draai je verschillende lichaamsdelen totdat je tweede pose compleet is. Vergeet niet de camerahoek te veranderen terwijl je werkt, zodat je de pose vanuit meerdere hoeken kunt zien.

Sneller Posen

 Versnel het poseren door eerst de lichaamsdelen die aan de romp zijn verbonden te draaien, zoals de bovenarm en dij, en werk vervolgens naar buiten om de handen en voeten te poseren.

Begin een Pose vanaf Nul

 Vind je een pose niet leuk en wil je gewoon opnieuw beginnen? Je kunt je personage resetten naar de standaardpose met het volgende proces:

1.

Klik met de rechtermuisknop op de bovenste witte diamant van de pose die je wilt resetten. Er verschijnt een menu.

2.

Selecteer in het menu Reset Selected .

3.

Klik in de Animatie-editor  op de Afspelen -knop om je animatie te testen. Voel je vrij om aanpassingen aan een van je poses te maken totdat het lijkt alsof het personage soepel in het water zwemt.

Gefeliciteerd met het poseren van je personage voor je eerste animatie! De volgende les gaat in op hoe je je animatie kunt opslaan en exporteren, zodat je deze binnen games kunt gebruiken.

[Volgende](/docs/nl-nl/tutorials/curriculums/animator/play-your-animation)[Vorige](/docs/nl-nl/tutorials/curriculums/animator/get-started)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
