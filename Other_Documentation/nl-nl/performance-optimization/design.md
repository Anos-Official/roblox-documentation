<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/design -->

Ontwerpen voor prestaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)

# Ontwerpen voor prestaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Ontwerpen voor prestaties betekent het volgen van een handvol beste praktijken terwijl je  je spel bouwt. In vergelijking met het vinden en oplossen van prestatieproblemen later in het ontwikkelingsproces, kan het vroeg ontwerpen voor prestaties je veel tijd en moeite besparen.

## [Apparaten met lage specificaties](#apparaten-met-lage-specificaties)[](#apparaten-met-lage-specificaties)

Apparaten met lagere specificaties, met name mobiele apparaten, hebben ernstige geheugenbeperkingen en zijn gevoelig voor crashes door out of memory (OOM) fouten:

-

Als je lagere apparaten wilt ondersteunen, kies dan ten minste één "basislijn" apparaat, [test je spel op dat apparaat](/docs/nl-nl/performance-optimization/test-on-hardware)  gedurende het ontwikkelingsproces, en let goed op de frame rate en het geheugengebruik. Terwijl je probleemgebieden in je spel vindt, gebruik die gebieden om de limieten van je apparaat te identificeren.

Bijvoorbeeld, je zou een spel kunnen testen met de Render  (Shift F2 ) en Samenvatting  (Shift F2 ) debugstatistieken ingeschakeld. Als de frame rate begint te dalen in een bijzonder rommelige omgeving, kun je de Draw (scene)  cijfers bekijken en bepalen dat je onder de 1.000 draw calls en 1.000.000 driehoeken moet blijven om het spel goed te laten draaien op je basislijn apparaat.

Of je zou de Ontwikkelaarsconsole  (F9 ) kunnen bekijken en opmerken dat het geheugengebruik een beetje hoog is, tenzij je [streaming](/docs/nl-nl/workspace/streaming)  inschakelt. Een duidelijk begrip van de apparaatlimieten kan je helpen om daaronder te blijven terwijl je verder bouwt aan je spel.

![Een Roblox-spel met drie overlays actief.](https://prod.docsiteassets.roblox.com/assets/optimization/perf-hud.png)

-

De apparaatemulator in Roblox Studio is nuttig voor het controleren van de beeldverhouding en de bedieningselementen, maar is niet nauwkeurig voor geheugengebruik; wanneer je een spel in Studio test, draait het de server en de client, waardoor het geheugengebruik aanzienlijk hoger is.

Roblox heeft geen toegang tot al het geheugen van een apparaat. Een deel is vereist voor het besturingssysteem en andere toepassingen.

### [Grafische kwaliteitsniveaus](#grafische-kwaliteitsniveaus)[](#grafische-kwaliteitsniveaus)

Roblox schaalt automatisch de renderkwaliteit naar de mogelijkheden van elk apparaat. Op lagere kwaliteitsniveaus vermindert de engine functies zoals de tekenafstand, maar zelfs op het laagste kwaliteitsniveau is de tekenafstand minstens 500 studs. Terrainen blijven transparant en stralen behouden hun segmentaantal op alle kwaliteitsniveaus. Roblox past deze waarden voortdurend aan, dus vermijd het ontwerpen rond exacte tekenafstanden.

-

Om je spel op verschillende kwaliteitsniveaus in Studio te bekijken, open [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) , selecteer Rendering  en wijzig Editor Quality Level . Test je visuals op zowel de laagste als de hoogste niveaus.

-

Als het verhogen van het kwaliteitsniveau niet meer van je scène onthult, zijn de objecten mogelijk niet gestreamd. Controleer je [streaming](/docs/nl-nl/workspace/streaming)  [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius)  instelling.

-

Vermijd het wijzigen van visuele effecten in scripts op basis van [UserGameSettings.SavedQualityLevel](/docs/nl-nl/reference/engine/classes/UserGameSettings#SavedQualityLevel) . Dit maakt het moeilijker voor de automatische schaling van de engine om te werken.

Algemener kan [testen op verschillende apparaten](/docs/nl-nl/performance-optimization/test-on-hardware)  je helpen te controleren of het spel overeenkomt met je visuele en prestatieverwachtingen op verschillende grafische kwaliteitsniveaus. Voor een veel gedetailleerder voorbeeld van hoe je zou kunnen nadenken over het optimaliseren van je spel voor apparaten met lage specificaties, zie [Real World Building and Scripting Optimization](https://devforum.roblox.com/t/real-world-building-and-scripting-optimization-for-roblox/3127146) .

## [Streaming en teleportatie](#streaming-en-teleportatie)[](#streaming-en-teleportatie)

-

[Instance streaming](/docs/nl-nl/workspace/streaming)  stelt Roblox in staat om 3D-inhoud dynamisch te laden en te ontladen en is een geweldige optie voor de meeste plaatsen, vooral grotere. Streaming verbetert de join-tijden, vermindert de geheugendruk en verhoogt de frame rate.

Bijvoorbeeld, wanneer je [Workspace.EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars)  inschakelt en de [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  eigenschap van je wereldmodellen instelt op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM) , kun je werelden creëren met sociale ruimtes en drukke evenementen die visueel bevolkt blijven terwijl ze schalen over een breed scala aan apparaatspecificaties. Voor meer informatie, zie [SLIM](/docs/nl-nl/workspace/streaming/slim)  en [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#instantie-streaming) .

-

Overweeg om grote plaatsen op te splitsen in meer beheersbare en gebruik [teleportatie](/docs/nl-nl/projects/teleport)  om spelers tussen hen te verplaatsen. Deze aanpak kan de initiële  join-tijden verminderen, maar legt extra join-tijden op wanneer spelers van plaats naar plaats teleporteren. Voordelen voor geheugengebruik variëren afhankelijk van de grootte van de plaats en of je streaming hebt ingeschakeld.

Zelfs zonder prestatieoverwegingen, kun je ontdekken dat het hebben van meerdere plaatsen het ontwikkelingsproces vereenvoudigt, vooral als je regelmatig nieuwe inhoud aan je spel toevoegt of deel uitmaakt van een groter team.

## [Materialen en duplicatie](#materialen-en-duplicatie)[](#materialen-en-duplicatie)

-

Standaardmaterialen gebruiken veel minder geheugen dan aangepaste texturen, maar komen mogelijk niet overeen met je artistieke visie. Probeer materialen zoveel mogelijk te gebruiken om het geheugengebruik voor de texturen die centraal staan in je spel te behouden.

-

Terwijl je activa maakt, zet ze om in [pakketten](/docs/nl-nl/projects/assets/packages) . Pakketten onderdeel maken van je workflow helpt om het veelvoorkomende probleem van dubbele activa met verschillende ID's te vermijden, wat de prestaties kan schaden.

-

Wanneer je meshes en texturen toevoegt, gebruik en hergebruik ze in plaats van dubbele kopieën te importeren. Door te schalen, roteren en overlappen, kun je rijke, gevarieerde omgevingen creëren die zeer weinig [draw calls](/docs/nl-nl/performance-optimization/improve#tekenopdrachten)  vereisen. Voor meer informatie, zie [Verwijder dubbele texturen](/docs/nl-nl/tutorials/curriculums/environmental-art/optimize-your-experience#verwijder-dubbele-texturen) .

## [Transparantie](#transparantie)[](#transparantie)

-

Vermijd transparantiewaarden anders dan 0 (zichtbaar) en 1 (onzichtbaar). Wanneer je gedeeltelijke transparantie gebruikt, wees dan vooral voorzichtig om [hoge transparantie-overdraw](/docs/nl-nl/tutorials/curriculums/environmental-art/optimize-your-experience#verwijder-gelaagde-transparanties)  te vermijden.

## [Scripting](#scripting)[](#scripting)

-

Schrijf waar mogelijk gebeurtenisgestuurde code in plaats van per-frame berekeningen. Bij 60 FPS is het totale budget voor elk frame 16,67 milliseconden (ms). Zelfs schijnbaar kleine per-frame berekeningen kunnen een aanzienlijk deel van dat budget gebruiken.

-

Zoek manieren om langlopende code op te splitsen in beheersbare stukken. Als een stuk code 100 ms nodig heeft om uit te voeren en je het elke frame uitvoert, kan je spel slechts 10 FPS draaien. Als je besluit om de code slechts één keer per seconde uit te voeren in een spel dat anders op 60 FPS draait, komen 59 van je frames na 16,67 ms... en dan één na 100 ms, wat een schokkende hapering veroorzaakt.

Onderzoek in plaats daarvan hoe je de code kunt opsplitsen. Misschien kun je 5 ms werk per frame uitvoeren, [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  gebruiken, en de voltooide berekening elke 20 frames hebben terwijl je nog steeds 60 FPS behoudt. [Multithreading](/docs/nl-nl/scripting/multithreading) , soms Parallel Luau genoemd, kan ook helpen.

-

Gebruik de [RBXScriptConnection:Disconnect()](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection#Disconnect)  methode om te voorkomen dat functies onnodig worden aangeroepen de volgende keer dat een gebeurtenis wordt geactiveerd.

-

Roep niet dezelfde methode elke keer aan wanneer je een waarde nodig hebt. Roep de methode één keer aan, sla de waarde op en overschrijf deze later indien nodig.

-

Sla niet alles op in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . De client laadt alles wat in deze container staat. Gebruik in plaats daarvan [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  voor alles waar de client geen toegang toe hoeft te hebben.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
