<!-- Source: https://create.roblox.com/docs/nl-nl/characters/r6-only-to-r15-only -->

Converteer spellen van R6 Alleen naar R15 Alleen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Converteer spellen van R6 Alleen naar R15 Alleen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gebruikers sluiten zich aan bij spellen met hun [speler personages](/docs/nl-nl/characters#speler-personages)  die ze besturen om het spel te spelen. Terwijl sommige spelontwikkelaars aangepaste speler personages vanaf nul creëren die passen bij hun spelontwerp esthetiek, kiezen velen ervoor om spelers hun [platform avatar](/docs/nl-nl/avatar)  als hun speler personage te laten behouden, hetzij met een R6 of R15 rig:

-

R6 rigs  hebben zes lichaamsdelen en vijf poseerbare gewrichten voor karakterbeweging.

-

R15 rigs  hebben ten minste 15 lichaamsdelen en 15 hoofdgewrichten om een breder scala aan lichaamsproporties, accessoires en animaties te ondersteunen.

Speler personages met R6 rigs zijn een fundamentele pijler van de platformgeschiedenis en definiëren veel van Roblox's meest iconische spellen. Echter, speler personages met ten minste [standaard R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  bieden mogelijkheden die de R6 rig niet kan, zoals diepere aanpassing, expressieve beweging en compatibiliteit met moderne engine-functies.

![](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Birdcaller-Imported.jpeg) Speler personage

![](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Rig-Hierarchy-Birdcaller-Blender-Bones.png) R15 gewrichtstructuur (Blender)

Terwijl nieuwe spellen standaard alleen spelers met R15 rigs toestaan, kan het converteren van live spellen om alleen R15 rigs te ondersteunen een complexe onderneming zijn, gezien het aantal scripts, animaties, tools en gameplay-functies die ervan uitgaan dat spelers R6 rigs kunnen gebruiken. Een succesvolle overgang behoudt de kernidentiteit terwijl de onderliggende karaktertechnologie wordt gemoderniseerd.

De volgende richtlijnen kunnen je team helpen tijdens het conversieproces, met inbegrip van het auditen van R6-specifieke aannames, het converteren van essentiële animaties, het valideren van gameplay-geometrie en het monitoren van de uitrol.

Elk Roblox-spel is anders opgebouwd. Deze stappen dienen als basis voor conversie en dekken mogelijk niet elke unieke technische vereiste van jouw conversie.

## [Waarom spellen converteren naar R15?](#waarom-spellen-converteren-naar-r15)[](#waarom-spellen-converteren-naar-r15)

-

Avatar aanpassing  - Spellen die R15 rigs toestaan, laten spelers het spel betreden met hun avatar zoals deze is vanuit de Marketplace, wat vereist dat alle lichamen ten minste standaard R15 rigs bevatten. R15 ondersteunt een breder scala aan lichaamstypes, aanpassingen, accessoires en moderne animatiesystemen.

-

Expressieve beweging  - De extra gewrichten die R15 rigs bieden, kunnen gedetailleerde animaties, emotes, gevechtsbewegingen en beweging mogelijk maken, terwijl ze beter ondersteuning bieden voor motion capture.

-

Ecosysteemgroei  - Terwijl Roblox de mogelijkheden voor het platform blijft uitbreiden, stellen R15 rigs makers in staat om gebruik te maken van die nieuwe technologie in de toekomst.

-

Monetisatie  - Een spel instellen op R15 Alleen  in [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings)  is een van de kwalificaties voor het verhoogde [VS 18+ DevEx-tarief](/docs/nl-nl/production/monetization/18-plus-devex-rate#spelerskarakters) .

## [Conversieproces](#conversieproces)[](#conversieproces)

De stappen van het conversieproces hieronder zijn ontworpen om je team zorgvuldig te laten bewegen, problemen vroegtijdig te signaleren en de ervaring vertrouwd te laten aanvoelen voor spelers. Je kunt sommige stappen combineren, maar het is nuttig om ze allemaal door te nemen voordat je lanceert. Het wordt aanbevolen dat jij en je team:

1.

[Voorbereiden op de conversie](#voorbereiden-op-de-conversie)

2.

[Audit R6-specifieke scripts](#audit-r6-specifieke-scripts)

3.

[Herbouw of converteer animaties](#herbouw-of-converteer-animaties)

4.

[Update tools, wapens en accessoires](#update-tools-wapens-en-accessoires)

5.

[Herwerk hitdetectie en gameplay-geometrie](#herwerk-hitdetectie-en-gameplay-geometrie)

6.

OPTIONEEL

 [Review niet-speler personages](#review-niet-speler-personages)

7.

OPTIONEEL

 [Review camera en presentatie](#review-camera-en-presentatie)

8.

[Test prestaties en apparaatsdekking](#test-prestaties-en-apparaatsdekking)

9.

[Voer een gefaseerde uitrol uit](#voer-een-gefaseerde-uitrol-uit)

### [Voorbereiden op de conversie](#voorbereiden-op-de-conversie)[](#voorbereiden-op-de-conversie)

Voordat je begint, is het belangrijk om de omvang van de conversie in te schatten, zodat je de middelen kunt plannen:

-

Eenvoudige conversie  - Het spel gebruikt standaardanimaties, heeft geen aangepaste NPC's die een specifieke rig vereisen, en verwijst niet rechtstreeks naar lichaamsdelen in scripts.

-

Gemiddelde conversie  - Het spel heeft enkele scripts die naar R6-onderdelen verwijzen, een paar aangepaste NPC's, enkele aangepaste animaties en objecten die aan specifieke lichaamsdelen zijn gelast.

-

Complexe conversie  - Het spel heeft uitgebreide scripting van lichaamsdelen, een aangepast ragdoll-systeem, een volledige set aangepaste animaties, veel R6 NPC's of limb-specifieke hitdetectie.

Zodra je de schaal van je conversie hebt bepaald, is het essentieel om vroege testbenchmarks vast te stellen. Testen met een paar representatieve avatars kan veel herwerk later besparen, vooral rond niveau-geometrie en karakterinteracties. Dit geeft het team een betrouwbaar referentiemodel om vroegtijdig verschillen in proporties, gewrichten, bijlagen en beweging op te sporen.

Het wordt aanbevolen om een [standaard R15 rig](/docs/nl-nl/avatar/resources#standaard-r15-rigs)  in Studio in te voegen en deze als referentie voor ontwikkeling te gebruiken. Test met meer dan één lichaamsvorm en een scala aan avatarproporties als je spel spelerskeuze toestaat.

Veronderstel niet dat een karakter met een R15 rig dezelfde afmetingen heeft als een karakter met een R6 rig. Je kunt meer lezen over hoe verschillen in geometrie, interactiebereik en camera-alignment kritische factoren zijn in de volgende conversiestappen.

### [Audit R6-specifieke scripts](#audit-r6-specifieke-scripts)[](#audit-r6-specifieke-scripts)

Veel conversieproblemen komen voort uit code die ervan uitgaat dat gebruikers spellen spelen met speler personages met R6 lichaamsdelen of proporties, dus het vroegtijdig vinden van deze scripts helpt om gebroken interacties, fouten en inconsistente gameplay te voorkomen.

Doorzoek je codebase naar aannames over R6-onderdeelnamen, zesdelige geometrie of R6-only [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  eigenschappen. Wanneer je verwijzingen van R6 naar R15 bijwerkt, onthoud dan dat één R6 lichaamsdeel kan overeenkomen met verschillende R15 [lichaamsdelen](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen) . In dergelijke gevallen, kies het R15 onderdeel dat overeenkomt met het doel van de code.

Je kunt [Alles Vinden / Alles Vervangen](/docs/nl-nl/studio/script-editor#zoeken-en-vervangen)  in de Script Editor gebruiken om alle toepasselijke R6-verwijzingen te vinden.

#### [Lichaamsdeel mappings](#lichaamsdeel-mappings)[](#lichaamsdeel-mappings)

| R6 onderdeel | | R15 onderdelen | | Wat te updaten |
| --- | --- |
| Torso | | UpperTorso  en LowerTorso | | Map borstbijlagen naar UpperTorso , en taillebijlagen en het Root  gewricht naar LowerTorso . |
| Rechter Arm | | RightUpperArm , RightLowerArm , en RightHand | | Map schouderbijlagen naar RightUpperArm , polsbijlagen naar RightLowerArm , en toolgrepen naar RightHand . |
| Linker Arm | | LeftUpperArm , LeftLowerArm , en LeftHand | | Map schouderbijlagen naar LeftUpperArm , polsbijlagen naar LeftLowerArm , en toolgrepen naar LeftHand . |
| Rechter Been | | RightUpperLeg , RightLowerLeg , en RightFoot | | Map bovenbeenbijlagen naar RightUpperLeg , onderbeenbijlagen naar RightLowerLeg , en voetbijlagen naar RightFoot . |
| Linker Been | | LeftUpperLeg , LeftLowerLeg , en LeftFoot | | Map bovenbeenbijlagen naar LeftUpperLeg , onderbeenbijlagen naar LeftLowerLeg , en voetbijlagen naar LeftFoot . |

Hoofd  en HumanoidRootPart  behouden dezelfde namen op beide rigs.

#### [Motor6D gewricht wijzigingen](#motor6d-gewricht-wijzigingen)[](#motor6d-gewricht-wijzigingen)

Voor deze stap van het conversieproces moet je de gewrichtnaam en het onderdeel dat de [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  ouders bijwerken. Scripts die Torso.Neck , Torso["Right Shoulder"] , of HumanoidRootPart.RootJoint  lezen, breken nog steeds na een hernoeming omdat R15 die gewrichten aan verschillende onderdelen koppelt.

Neck  behoudt zijn naam en verschuift van Torso  naar Head . Right Shoulder , Left Shoulder , Right Hip , en Left Hip  verschuiven van Torso  naar de bovenarm- en bovenbeenonderdelen, en de R15-namen laten de spatie weg.

| R6 gewricht | | R6 ouderonderdeel | | R15 gewricht | | R15 ouderonderdeel |
| RootJoint | | HumanoidRootPart | | Root | | LowerTorso |
| Geen | | Geen | | Waist | | UpperTorso |
| Neck | | Torso | | Neck | | Head |
| Right Shoulder | | Torso | | RightShoulder | | RightUpperArm |
| Geen | | Geen | | RightElbow | | RightLowerArm |
| Geen | | Geen | | RightWrist | | RightHand |
| Left Shoulder | | Torso | | LeftShoulder | | LeftUpperArm |
| Geen | | Geen | | LeftElbow | | LeftLowerArm |
| Geen | | Geen | | LeftWrist | | LeftHand |
| Right Hip | | Torso | | RightHip | | RightUpperLeg |
| Geen | | Geen | | RightKnee | | RightLowerLeg |
| Geen | | Geen | | RightAnkle | | RightFoot |
| Left Hip | | Torso | | LeftHip | | LeftUpperLeg |
| Geen | | Geen | | LeftKnee | | LeftLowerLeg |
| Geen | | Geen | | LeftAnkle | | LeftFoot |

Ragdoll- en procedurele animatiecode die gewrichten manipuleert op basis van R6-namen moet opnieuw worden bekeken voor de extra R15 gewrichten.

Geef de voorkeur aan op capaciteit gebaseerde code boven rig-naam aannames. Gebruik bijvoorbeeld een gedeelde bijlage, getagde hitbox of geconfigureerd referentieobject wanneer mogelijk in plaats van aan te nemen dat een wapen op een bepaald R6-limb behoort.

Als [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings)  R15 en R6  zijn, of als een NPC een andere rig gebruikt dan het speler personage, tak dan expliciet gebruikmakend van [Humanoid.RigType](/docs/nl-nl/reference/engine/classes/Humanoid#RigType)  en houd de R6- en R15-implementaties voldoende geïsoleerd om onafhankelijk te testen.

### [Herbouw of converteer animaties](#herbouw-of-converteer-animaties)[](#herbouw-of-converteer-animaties)

Het herbouwen of converteren van animaties van R6 rigs naar R15 rigs helpt om ervoor te zorgen dat karakters responsief en natuurlijk blijven aanvoelen met hun nieuwe gewrichtstructuur. Bovendien, om in aanmerking te komen voor het [VS 18+ DevEx-tarief](/docs/nl-nl/production/monetization/18-plus-devex-rate#spelerskarakters) , vereisen animaties elleboog- en kniebogen; R6-animatiepakketten op een R15 rig komen niet in aanmerking.

R6-animaties kunnen niet altijd soepel overgaan naar R15, dus het wordt aanbevolen om ze individueel te evalueren om ervoor te zorgen dat ze hun bedoelde uiterlijk en gevoel behouden. Aangezien animaties rechtstreeks zijn gekoppeld aan een rig's [lichaamsdeel](/docs/nl-nl/avatar/character-bodies#lichaamsdelen)  en [gewricht hiërarchie](/docs/nl-nl/avatar/character-bodies#rigging-armatuur) , moet je belangrijke animaties evalueren of opnieuw maken op een R15 rig.

Prioriteer het volgende:

-

Stilstand, lopen, rennen, springen, vallen, klimmen, zwemmen en landen cycli

-

Gevechtsaanvallen en reacties

-

Tool- en wapenanimaties

-

Emotes en sociale animaties

-

Cutscene-animaties

-

NPC-animatiesets

-

Animatie blending en prioriteit

Maak en bekijk animaties met de [Animatie-editor](/docs/nl-nl/tutorials/use-case-tutorials/animation/create-an-animation)  op een [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs) , publiceer vervolgens de nieuwe animatie-assets. Om een animatie over rigs te testen, bekijk gewricht mappings en stel de rig's T-pose in voordat je afspeelt, gebruik [Adaptieve Animatie](/docs/nl-nl/characters/adaptive-animation) . Vergeet niet om animaties vanuit verschillende camera-hoeken en met verschillende lichaamsproporties te valideren. Schouder-, heup- en nekgewrichten kunnen verschillen met 90 graden tussen rigs. Bevestig dat ledematen niet draaien, voeten blijven staan, en dat het hoofd en de nek correct volgen.

### [Update tools, wapens en accessoires](#update-tools-wapens-en-accessoires)[](#update-tools-wapens-en-accessoires)

#### Tools

Bij het updaten van tools voor R15 is het belangrijk om je te concentreren op handplaatsing en gripuitlijning:

-

Herpositioneer elke tool zodat deze correct in de hand van het karakter zit.

-

Controleer of de grip van de tool uitgelijnd is met de RightHand  of LeftHand  in plaats van de R6-arm.

-

Update alle lasverbindingen, beperkingen of [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  verwijzingen die naar R6-ledematen wijzen.

-

Test tools opnieuw tijdens verschillende animaties om verschuiving, clipping of onjuiste rotaties op te sporen.

-

Verifieer elke UI die uitgeruste tools, karakter slots of lichaamslocaties weergeeft.

#### Wapens

Wapens vereisen de volgende extra controles omdat hun grepen, effecten en lanceerpunten vaak afhankelijk zijn van nauwkeurige hand- en lichaamsposities:

-

Herpositioneer wapen grepen voor de specifieke R15 handonderdelen.

-

Controleer handplaatsing terwijl het karakter stil staat, loopt, rent, springt en aanvalt.

-

Update lasverbindingen, beperkingen en [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  verwijzingen voor de nieuwe R15 lichaamsstructuur.

-

Herpositioneer VFX-emitteren en de oorsprongen van de deeltjes zodat effecten op de juiste locatie verschijnen.

-

Update sporen, stralen, mondflitsen en projectiel lanceerpunten.

-

Test projectielen en andere effecten opnieuw tijdens animaties om ervoor te zorgen dat ze afkomstig zijn van de juiste bijlage of gewricht.

-

Verifieer elke uitrusting UI die wapen slots of lichaamslocaties weergeeft.

#### Accessoires

Karakter met R6 en R15 rigs gebruiken verschillende bevestigingslocaties. Op R6 worden veel accessoires aan de enkele Torso  bevestigd. Op R15 zijn die bevestigingspunten verdeeld over meerdere lichaamsdelen. Houd dit in gedachten en bekijk het volgende:

-

NeckAttachment , kraagbijlagen en voor- of achterlichaamsbijlagen verplaatsen naar UpperTorso .

-

Taillebijlagen verplaatsen naar LowerTorso .

-

ShoulderAttachment  bevindt zich op de juiste bovenarm.

-

GripAttachment  verplaatst naar het specifieke handonderdeel, dat niet bestaat op R6.

-

Hoofdbijlagen, inclusief HatAttachment , HairAttachment , en FaceFrontAttachment , blijven op Head .

-

Controleer schouder-, taille-, rug- en hoofaccessoires op correcte plaatsing.

-

Herpositioneer en test aangepaste kleding en gelaagde accessoires opnieuw.

-

Test accessoires op verschillende lichamen en animaties en kijk naar clipping of pasproblemen.

Wanneer mogelijk, bevestig items via hun [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  en [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten in plaats van handmatige lasverbindingen te gebruiken. Dit stelt de engine in staat om veel van het rig-specifieke bevestigingsgedrag automatisch af te handelen.

Gelaagde accessoires moeten gewogen en gebonden zijn aan een R15 rig, en vereisen een binnen- en buitenkooi. Voor meer informatie, zie [Specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications#rigging-en-skinning) .

### [Herwerk hitdetectie en gameplay-geometrie](#herwerk-hitdetectie-en-gameplay-geometrie)[](#herwerk-hitdetectie-en-gameplay-geometrie)

Karakterproporties veranderen bereik, dekking, botsing, targeting en aanvalafstand, zelfs wanneer de onderliggende code hetzelfde blijft. Test systemen die afhankelijk zijn van lichaamspositie of -grootte opnieuw om de gameplay eerlijk en consistent te houden, zoals:

-

Melee hitboxen

-

Projectiel targeting

-

Raycasts en zichtlijnen

-

Area-of-effect vaardigheden

-

Aim offsets en camera-relatieve targeting

-

Interactie prompts

-

Aanraak- en overlap evenementen

-

Animatie-gedreven schadevensters

-

Concurrentiële beweging en dekking

Gebruik gameplay colliders die zijn ontworpen voor de mechaniek, zodat hitdetectie niet de zichtbare mesh volgt. Bereik en botsing blijven dan stabiel wanneer avatarproporties veranderen. Je kunt de Consistente Gameplay  preset in [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings#algemeen)  gebruiken om elke avatar op dezelfde hoogte en dezelfde box collider in te stellen.

### [Review niet-speler personages](#review-niet-speler-personages)[](#review-niet-speler-personages)

Het beoordelen van NPC rigs stelt je in staat om ervoor te zorgen dat het hele karakter ecosysteem samen vooruitgaat. NPC's gebruiken vaak hun eigen scripts, animaties en rig-sjablonen, dus ze nu controleren helpt om gebroken gedrag of een visueel inconsistente wereld later te vermijden.

Het converteren van NPC's is vaak optioneel. De rigtype-instelling in [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings)  regelt speler avatars, niet NPC's, dus NPC's met R6 rigs blijven normaal laden en animeren naast speler personages met R15 rigs. Je hoeft meestal alleen een NPC te converteren wanneer dezelfde rig-specifieke code, zoals gedeelde hitdetectie, lassen of ragdoll-systemen, zowel NPC's als spelers verwerkt. Het achterlaten van NPC's met R6 rigs beïnvloedt ook het [VS 18+ DevEx-tarief](/docs/nl-nl/production/monetization/18-plus-devex-rate#spelerskarakters)  niet, dat afhankelijk is van de avatar type-instelling van het spel in plaats van individuele NPC rigs.

Voor elk NPC-type dat je converteert, controleer:

-

Rigstructuur en lichaamsdeelverwijzingen

-

Animatie-afspeelkwaliteit

-

Padvinding en beweging

-

Spawn- en despawn-gedrag

-

Doelselectie en afstandscontroles

-

Hitdetectie

-

Dood, ragdoll en respawn-gedrag

-

Replicatie en netwerkbezit

Speel NPC's in Studio en gebruik de [Animatie-editor](/docs/nl-nl/tutorials/use-case-tutorials/animation/create-an-animation)  om beweging, gevecht, dood en emote-animaties te beoordelen. Herbruikbare NPC rigs en testscènes maken herhaalde controles sneller.

### [Review camera en presentatie](#review-camera-en-presentatie)[](#review-camera-en-presentatie)

Het beoordelen van camera en presentatie helpt om het gevoel te behouden dat spelers al kennen en waarderen. Zelfs wanneer een karakter technisch werkt, veranderen R15 rigs hun hoogte, proporties en beweging, en veranderingen in het gezichtspunt, de framing of de animatie kunnen het spel langzamer, krap, desoriënterend of gewoon niet zoals het origineel laten aanvoelen.

Om deze reden is het belangrijk om het volgende te overwegen:

-

Cameradoel en offset

-

Zichtbaarheid van eerste-persoonsarmen of -lichaam

-

Schoudercamera-framing

-

Hoofdbeweging en cameratrilling

-

Cutscene-compositie

-

UI-markeringen boven het karakter

-

Naamplaten en gezondheidsbalken

-

Cinematische animatietiming

Gebruik de playtest-modi van Studio en de [Apparaatsimulator](/docs/nl-nl/studio/testing-modes#apparaatsimulatie)  om camera-framing, UI-plaatsing en bedieningselementen over schermformaten en apparaattype te beoordelen.

### [Test prestaties en apparaatsdekking](#test-prestaties-en-apparaatsdekking)[](#test-prestaties-en-apparaatsdekking)

Het testen van prestaties op een breed scala aan apparaten helpt ervoor te zorgen dat de update goed werkt voor zoveel mogelijk spelers. Testen op verschillende apparaten kan crashes of frame rate-problemen onthullen en je helpen R15 rig-gerelateerde problemen te scheiden van wijzigingen in nieuwe assets, lassen, animaties of scripts.

Het is belangrijk om te testen op de laagste apparaten en netwerkcondities die je spelers gebruiken. Voer dezelfde scenario's uit met Avatar-instellingen ingesteld op R6 Alleen , en vervolgens op R15 Alleen . Vergelijk die resultaten voordat je een wijziging aan de rig toeschrijft. Nieuwe lassen, effecten, scripts en asset-laden kunnen de cijfers op zichzelf veranderen.

Meet:

-

Frame rate en frame-tijd pieken

-

Geheugengebruik

-

Client- en server CPU-tijd

-

Join-tijd en karakter spawn-tijd

-

Crashpercentage

-

Animatie- of fysica-fouten

-

Netwerkreplicatie

-

Batterij- of thermale impact, wanneer die gegevens beschikbaar zijn

Gebruik de [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console)  om geheugen-, netwerk- en scriptactiviteit te beoordelen. Gebruik de [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler/use-microprofiler)  wanneer je een beter inzicht nodig hebt in frame tijd of CPU-kosten.

### [Voer een gefaseerde uitrol uit](#voer-een-gefaseerde-uitrol-uit)[](#voer-een-gefaseerde-uitrol-uit)

Het uitvoeren van een gefaseerde uitrol geeft je team ruimte om te leren en verbeteringen aan te brengen voordat de update iedereen bereikt. Bovendien maakt het het gemakkelijker om metrics te vergelijken, problemen op te lossen, feedback te verzamelen en te bevestigen dat de R15-versie nog steeds levert wat spelers het meest waarderen.

Een veiligere uitrol kan omvatten:

-

Interne tests met representatieve apparaten en avatars

-

Een privé testplaats of beperkte toegang release

-

Een kleine percentage uitrol of een gecontroleerd publiek

-

In-game feedbackverzameling

-

Monitoring van gameplay, crashes, prestaties, retentie en sentiment

Houd analytics in staat om deze conversie te onderscheiden van niet-verwante updates.

## [Veelvoorkomende fouten om te vermijden](#veelvoorkomende-fouten-om-te-vermijden)[](#veelvoorkomende-fouten-om-te-vermijden)

#### Vervangen van Torso  met UpperTorso  overal zonder gameplay-geometrie te beoordelen

R15 rigs splitsen de torso van de R6 rig in UpperTorso  en LowerTorso , veranderen afmetingen en bevestigingspunten, en gebruiken verschillende heup- en schouderrelaties. Een directe hernoeming kan raycasts, hitboxen, lassen, offsets, zitten, camera-framing en ruimtelijke gameplay breken.

In plaats daarvan : Audit elk gebruik van Torso , beslis of het moet verwijzen naar UpperTorso , LowerTorso , de karakterwortel of een bijlage, en valideer alle geometrie-afhankelijke offsets opnieuw.

#### Hard-coderen van limb-namen in nieuwe systemen

Karakter met R6 en R15 rigs gebruiken verschillende onderdeel hiërarchieën en namen, dus systemen voor schade, IK, animatie, accessoires, interactie of procedurele beweging kunnen falen of het verkeerde lichaamsdeel targeten.

In plaats daarvan : Gebruik [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  verwijzingen, of creëer een rig abstractielaag die logische lichaamsregio's aan de actieve rig koppelt.

#### Negeren van NPC's, tools, VFX en cutscenes

Een conversie van speler avatars update niet automatisch niet-speler personages of inhoud die aan de oude R6 hiërarchie is gekoppeld. Toolgrepen, effect-emitteren, gescripte gewrichten, camera-beats en geauthoreerde cutscenes kunnen visueel of functioneel niet goed uitgelijnd zijn op karakters met R15 rigs.

In plaats daarvan : Inventariseer elk karakter-gedreven asset en test spelers, NPC's, uitgeruste tools, effecten, gescripte gewrichten en cinematische sequenties tegen representatieve R15 rigs voordat je publiceert.

#### Testen alleen met één avatar lichaams type

R15 ondersteunt gevarieerde proporties, dus een pose of mechaniek die op één lichaam werkt, kan voet sliding, limb-intersecties, schouder- of heup-offsets, camera-clipping of onjuiste interactie-afstanden op een ander veroorzaken.

In plaats daarvan : Bouw een validatiematrix die meerdere R15 lichaams types, schalen en proporties dekt, en omvat extreme gevallen in geautomatiseerde of herhaalbare controles.

#### Publiceren van de conversie met niet-verwante gameplay wijzigingen

Wanneer migratie en functie wijzigingen samen worden verzonden, wordt het moeilijk om regressies te isoleren en te diagnosticeren.

In plaats daarvan : Gebruik een gefaseerde migratie: stel eerst R15-compatibiliteit in achter een vlag of testplaats, valideer de geconverteerde systemen, en verzend vervolgens niet-verwante gameplay wijzigingen afzonderlijk.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
