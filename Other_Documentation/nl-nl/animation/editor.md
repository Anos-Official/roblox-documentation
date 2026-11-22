<!-- Source: https://create.roblox.com/docs/nl-nl/animation/editor -->

Animatie-editor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)
6. /
7. Animaties maken
8. /
9. [Animatie-editor](/docs/nl-nl/animation/editor)

# Animatie-editor

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Animatie-editor , toegankelijk vanuit het Avatar -tabblad van Studio of het Venster  ⟩ Avatar -menu, stelt je in staat om aangepaste animaties op rigs te ontwerpen en publiceren. Een rig is een object met individuele secties die door gewrichten zijn verbonden. Je kunt deze gewrichten bewegen om [poses te creëren](#maak-poses)  en vervolgens de rig soepel van pose naar pose animeren.

 ![Animatie-editor aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Animation.png)

## [Interface](#interface)[](#interface)

Het venster van de Animatie-editor is verdeeld in drie primaire secties:

![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Editor-Sections-Labeled.png)

Media / Afspeelbesturing Tracklijst Tijdlijn

![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Editor-Media-Playback.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A-Grey.png)

Naam van de animatie.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B-Grey.png)

Mediakeuze en afspeelopties.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C-Grey.png)

Positie-indicator die de tijdseenheid voor de positie van de scrubber in seconden:frames  weergeeft.

## [Maak een animatie](#maak-een-animatie)[](#maak-een-animatie)

Je kunt alleen animaties maken met rigs .

1.

Als je nog geen rig in de werkruimte hebt, voeg dan een vooraf gebouwde rig toe met behulp van de [Rig Generator](/docs/nl-nl/studio/rig-builder)  tool. De vooraf gebouwde rigs hebben alle basisdelen en mechanismen om een karakteranimatie te bouwen.

 ![Karakterknop gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Character.png)

Voor een aangepaste rig met [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  gewrichten, controleer of [AssemblyRootPart](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyRootPart)  het onderdeel is dat je wilt dat stationair blijft wanneer de gewrichten animeren. [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  stelt de assemblageroot niet in. Als een ander onderdeel is geselecteerd, zie [selectie van assemblagerootonderdeel](/docs/nl-nl/physics/assemblies#wortelonderdeel-van-de-assemblage) .

2.

Selecteer in de 3D-weergave of het Explorer -venster de rig.

Van hieruit kun je beginnen met [het creëren van poses](#maak-poses)  voor je rig en de animatie-instellingen aanpassen, zoals [het herhalen van de animatie](#herhaal-een-animatie)  of [het instellen van de prioriteit](#stel-een-prioriteit-in) .

## [Maak poses](#maak-poses)[](#maak-poses)

Een animatie bestaat uit verschillende poses , of specifieke posities en oriëntaties van [Bone](/docs/nl-nl/reference/engine/classes/Bone)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten binnen een rig. Je kunt poses creëren door botten of meshes te verplaatsen of te roteren, zoals de handen, voeten of torso van de rig. Nadat je meerdere poses op verschillende posities van de tijdlijn hebt gemaakt, draait de animatie-editor tussen hen in met je [easing-instellingen](#easing)  om de rig soepel van pose naar pose te animeren.

Bijvoorbeeld, een eenvoudige animatie waarbij een humanoïde karakter zich omdraait om 45° naar links te kijken, heeft twee poses: De initiële positie die naar voren kijkt, en de gedraaide positie die naar links kijkt.

Om een pose te creëren:

1.

Selecteer in het Explorer -venster de rig en breid de kindinstanties uit om toegang te krijgen tot de botten of meshes.

2.

Selecteer in de 3D-weergave of het Explorer -venster een bot of mesh.

3.

Klik en verplaats in de tijdlijn de scrubber  naar de framepositie waar je de pose wilt instellen. Standaard geeft Roblox tijdlijn-eenheden weer als seconden:frames  en animaties draaien op 30 frames per seconde. Bijvoorbeeld, 0:15  geeft ½ seconde aan.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Scrubber-0-15.png)

Standaard toont de tijdlijn een duur van 1 seconde (1:00). Om meer tijd aan de tijdlijn toe te voegen, voer je een nieuwe waarde in het vak aan de rechterkant van de positie-indicator in.

4.

Verplaats of roteer het bot of mesh naar een nieuwe oriëntatie. Voor botten kun je ze roteren om de rig langs de gemaakte botgewrichten te poseren.

Wanneer je een specifiek bot of mesh aanpast, wordt er een nieuwe track weergegeven in de tracklijst en verschijnt er een nieuw keyframe  op de tijdlijn voor dat bot of mesh op die specifieke framepositie.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Track-Keyframe-Added.png)

Bij het creëren van poses kun je schakelen tussen Verplaatsen  en Roteer  modi door op R  te drukken. Deze modi werken precies zoals het verplaatsen en roteren van basisobjecten, inclusief de snap-instellingen en incrementele waarden die zich in de werkbalk van Studio bevinden.

5.

Wanneer je klaar bent om de animatie te bekijken, klik je op de Afspelen -knop in de afspeelbesturing van de editor of druk je op de Spatiebalk .

## [Keyframes](#keyframes)[](#keyframes)

Zodra je [basisposes hebt gemaakt](#maak-poses)  voor een rig, kan het fijn afstemmen van individuele keyframes de uiteindelijke animatie aanzienlijk verbeteren. Je kunt ofwel:

-

Werken op een specifieke track of keyframe door op die track/keyframe te klikken of met de rechtermuisknop te klikken.

-

Werken op alle  tracks door in het bovenste gedeelte van de tracklijst te klikken of met de rechtermuisknop te klikken.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Editor-Keyframe-Operations.png)

| Operatie | | Workflow |
| --- | --- |
| Voeg keyframe(s) toe | | Rechtermuisklik en selecteer Voeg Keyframe Hier Toe . Let op dat de keyframe(s) worden ingevoegd op de tijdspositie die het dichtst bij je klik ligt, niet op de positie van de scrubber. |
| Verplaats keyframe(s) | | Selecteer een of meer keyframes en sleep ze naar een nieuwe tijdspositie. |
| Dupliceer keyframe(s) | | Selecteer een of meer keyframes en kopieer ze (Ctrl C  of ⌘ C ). Verplaats vervolgens de scrubber naar de doel tijdspositie en plak de gekopieerde frames (Ctrl V  of ⌘ V ). |
| Verwijder keyframe(s) | | Selecteer een of meer keyframes en druk op Delete  of Backspace . |

### [Easing](#easing)[](#easing)

Voor elk keyframe in de animatie-editor kun je zowel een [easing-stijl](#easing-stijl)  als een [easing-richting](#easing-richting)  kiezen.

#### [Easing-stijl](#easing-stijl)[](#easing-stijl)

Easing stijl  is de snelheid waarmee een animatie beweegt tussen verschillende frame posities binnen de animatie. Standaard zal een onderdeel bewegen en/of roteren van het ene keyframe naar het andere in een gelijkmatige, constante beweging die bekend staat als lineaire easing . In de volgende video maakt lineaire easing de draaiende animatie van het karakter stijf en robotachtig lijken.

Lineaire easing

Hoewel dat misschien geschikt lijkt voor sommige bewegingen, vergelijk de volgende video waar kubieke easing  de animatie van de beweging van het karakter natuurlijker laat lijken.

Kubieke easing

Om de easing-stijl voor een of meer keyframes te wijzigen:

1.

Selecteer een of meer keyframes. Elk geselecteerd keyframe is nu omringd door een blauwe rand.

2.

Klik met de rechtermuisknop op een keyframe met een rand. Een pop-upmenu verschijnt.

3.

Beweeg de muis over Easing-stijl  en kies uit de volgende opties:

-

Lineair  — Beweegt met een constante snelheid.

-

Constant  — Verwijdert interpolatie tussen het geselecteerde keyframe en het volgende keyframe. De animatie zal "snappen" van keyframe naar keyframe.

-

KubischV2  — Eased in of uit met kubieke interpolatie.

-

Elastisch  — Beweegt alsof het object aan een rubberen band is bevestigd.

-

Bounce  — Beweegt alsof de start- of eindpositie van de tween stuiterend is.

#### [Easing-richting](#easing-richting)[](#easing-richting)

Easing richting  definieert welk uiteinde van de animatiebeweging wordt beïnvloed door de [easing-stijl](#easing-stijl) . Standaard is de beweging langzamer aan het begin en sneller naar het einde van de animatie.

Om de easing-richting voor een of meer keyframes te wijzigen:

1.

Selecteer een of meer keyframes. Elk geselecteerd keyframe is nu omringd door een blauwe rand.

2.

Klik met de rechtermuisknop op een keyframe met een rand. Een pop-upmenu verschijnt.

3.

Beweeg de muis over Easing-richting  en kies uit de volgende opties:

-

In  — De beweging zal langzamer zijn aan het begin en sneller naar het einde.

-

Uit  — De beweging zal sneller zijn aan het begin en langzamer naar het einde.

-

InUit  — In  en Uit  op dezelfde tween, met In  aan het begin en Uit  die halverwege in werking treedt.

### [Optimaliseer keyframes](#optimaliseer-keyframes)[](#optimaliseer-keyframes)

Animators kunnen vaak veel keyframes genereren tijdens het animeren, vooral bij het gebruik van verschillende animatietools en -functies. Om het aantal onnodige keyframes te verminderen en het gemakkelijker te maken om op de tijdlijn te animeren, biedt de animatie-editor tools voor [automatische](#automatisch)  en [on-demand](#on-demand)  keyframe-optimalisatie.

#### [Automatisch](#automatisch)[](#automatisch)

De animatie-editor detecteert en verwijdert automatisch onnodige keyframes bij het maken van [gezichtsanimaties](/docs/nl-nl/art/characters/facial-animation/animate-heads)  en bij het [promoten van een keyframe-animatie naar een curve-animatie](/docs/nl-nl/animation/curve-editor#open-de-curveneditor) .

Als 3 of meer opeenvolgende keyframes dezelfde waarde hebben in een track, verwijdert de editor de tussenliggende keyframes en houdt alleen de eerste en laatste keyframes.

Als de track alleen keyframes met standaardwaarden bevat, zoals een [identity](/docs/nl-nl/reference/engine/datatypes/CFrame#identity)  coördinaatframe, of een 0  waarde voor een curve-animatie, wordt de hele track verwijderd uit de animatie.

#### [On-demand](#on-demand)[](#on-demand)

Tijdens het animeren kun je de Keyframe-optimalisatie  tool van de editor gebruiken om snel het aantal onnodige keyframes te verminderen. Keyframe-optimalisatie prioriteert eerst de minst impactvolle keyframes. Je kunt het aantal keyframes aanpassen met de schuifregelaar.

Tijdens het gebruik van de schuifregelaar kun je de animatie bekijken en door de tijdlijn scrubben om je animatie te controleren, maar je kunt geen bewerkingsoperaties uitvoeren, zoals het wijzigen van keyframewaarden of het toevoegen van tracks.

Om de Optimaliseer Keyframes  tool te openen:

1.

Klik op de ⋯  knop in de afspeelbesturing van de editor en selecteer Optimaliseer Keyframes .

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Controls-File-Menu.png)

2.

Verplaats in het pop-upvenster de schuifregelaar naar het gewenste aantal keyframes. Je kunt de animatie bekijken en afspelen om de optimalisatie te verifiëren.

3.

Klik op OK  wanneer je klaar bent.

## [Herhaal een animatie](#herhaal-een-animatie)[](#herhaal-een-animatie)

Om een animatie automatisch te laten herhalen, ga je naar de mediabesturing en klik je op de Herhalings -knop.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Controls-Looping.png)

Een herhalende animatie interpoleert niet tussen de laatste keyframes en eerste keyframes. Om de animatie soepel te laten herhalen, dupliceer je de eerste keyframes en gebruik je ze als de laatste keyframes.

## [Stel een prioriteit in](#stel-een-prioriteit-in)[](#stel-een-prioriteit-in)

De prioriteit  van een animatie ([Enum.AnimationPriority](/docs/nl-nl/reference/engine/enums/AnimationPriority) ) bepaalt wanneer deze in een spel wordt afgespeeld. Als je bijvoorbeeld een animatie met een hogere prioriteit afspeelt dan een andere animatie die al wordt afgespeeld, zal de nieuwe animatie de oude overschrijven. Bijvoorbeeld, een "springen" animatie moet prioriteit hebben boven een "stilzitten" animatie, zodat een karakter niet beide tegelijkertijd uitvoert.

Roblox gebruikt zeven niveaus van prioriteit, hier gerangschikt van hoog naar laag:

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Highest.png)

Actie4

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Higher.png)

Actie3

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-High.png)

Actie2

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Neutral.png)

Actie

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Low.png)

Beweging

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Lower.png)

Stilzitten

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Lowest.png)

Kern

Om een animatie een andere prioriteit te geven:

1.

Ga naar de mediabesturing van de editor en klik op de ⋯  knop.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Controls-File-Menu.png)

2.

Beweeg de muis over Stel Animatieprioriteit In  en kies de gewenste prioriteitsinstelling.

## [Sla een animatie op](#sla-een-animatie-op)[](#sla-een-animatie-op)

Wanneer je een animatie opslaat, slaat Studio deze op als een [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  object in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  en voegt een referentie toe aan je rig-object. Het opslaan van je animatie is bedoeld om je voortgang en werk te behouden. Als je van plan bent een animatie te gebruiken, [exporteer deze](#exporteer-een-animatie)  voordat je de gepubliceerde animatie in je spel verwijst.

Om een animatie op te slaan:

1.

Ga naar de mediabesturing van de editor en klik op de ⋯  knop.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Controls-File-Menu.png)

2.

Selecteer Opslaan  of Opslaan Als  om de animatie op te slaan in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) .

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Saved-Animation.png)

Toegang tot lokale animatiegegevens

Roblox slaat animatiegegevens lokaal op in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  om je animatiewerk te behouden. In de meeste gevallen zou je spel deze lokale gegevens niet rechtstreeks moeten benaderen en in plaats daarvan een gepubliceerde animatie moeten verwijzen.

In de zeldzame gevallen dat je spel toegang tot lokale gegevens vereist, verwijs je naar de waarde van de [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue)  in de AnimSaves -map van je rig in plaats van rechtstreeks toegang te krijgen tot de [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) .

Correcte toegang tot lokale animatiegegevens

```

local rig = workspace.Rig

-- Toegang tot je lokale animatiegegevens met de waarde referentie in je rig

local anim = rig.AnimSaves.Value.[SavedAnimation]

```

Aangezien lokale gegevens zijn opgeslagen in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) , worden ze niet gerepliceerd en zijn ze niet beschikbaar voor clients. Als je clients toegang tot die gegevens nodig hebben, moet je de [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  of [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation)  objecten en hun afstammelingen naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  verplaatsen.

## [Exporteer een animatie](#exporteer-een-animatie)[](#exporteer-een-animatie)

Wanneer je een animatie naar Studio exporteert, wordt deze beschikbaar voor gebruik in alle spellen. Dit betekent dat je slechts één keer een animatie hoeft te maken, en deze vervolgens zo vaak kunt hergebruiken als je wilt.

Als je animatie zal worden gebruikt voor een standaard  Roblox karakteranimatie zoals springen of rennen, zorg er dan voor dat je de laatste keyframe hernoemt zoals beschreven in de eerste stap hieronder.

Om een animatie te exporteren:

1.

BELANGRIJK

 Als de animatie zal worden gebruikt om een standaard karakteranimatie te [vervangen](/docs/nl-nl/animation/using#standaardanimaties-vervangen)  zoals rennen of springen, hernoem de laatste keyframe naar Einde  als volgt:

1.

Klik met de rechtermuisknop op het laatste keyframe-symbool in de bovenste balk en kies Hernoem Key Keyframe  uit het contextmenu.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Select-Final-Keyframe.png)

2.

Typ Einde  (hoofdlettergevoelig ) in het invoerveld.

3.

Klik op de Opslaan -knop.

2.

Ga naar de mediabesturing van de editor en klik op de ⋯  knop.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Controls-File-Menu.png)

3.

Selecteer Publiceren naar Roblox  uit het contextmenu.

4.

Voer in het Assetconfiguratievenster  een animatietitel en optionele beschrijving in.

5.

BELANGRIJK

 Als de animatie in een [groep-bezit](/docs/nl-nl/projects/groups)  spel zal worden gebruikt, selecteer dan de groep in het Maker -veld.

6.

Klik op de Indienen -knop.

Zodra de upload is voltooid, kun je de asset-ID van de animatie kopiëren uit de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  voor het script van aangepaste animaties of om standaard karakteranimaties te vervangen, zoals beschreven in [Gebruik animaties](/docs/nl-nl/animation/using) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
