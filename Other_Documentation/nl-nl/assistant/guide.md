<!-- Source: https://create.roblox.com/docs/nl-nl/assistant/guide -->

Assistent voor Studio | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Assistant](/docs/nl-nl/assistant/guide)

# Assistent voor Studio

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Assistent  is een AI-hulp die je helpt om sneller games te bouwen door vragen te beantwoorden, inhoud te genereren en acties direct in Studio uit te voeren. Het kan het volgende doen en nog veel meer:

-

Vragen beantwoorden over Roblox-ontwikkeling

-

Objecten en scripts in het datamodel van je plaats maken en wijzigen

-

Activa uit de Creator Store invoegen

-

Geselecteerde code in de Script Editor uitleggen

-

Materialen genereren om je objecten opnieuw te stylen

-

3D-meshes en procedurele modellen genereren om je scène te vullen

In Studio combineert de Assistent een groot taalmodel (LLM) met een run-commando systeem dat direct op je datamodel kan handelen. Het kan objecten invoegen en wijzigen, scripts maken en repetitieve taken automatiseren, zoals het in bulk bijwerken van eigenschappen.

Voor een diepgaandere kijk op wat de Assistent kan doen en hoe je deze kunt gebruiken, zie de [Promptgids en voorbeelden](/docs/nl-nl/assistant/prompt-engineering)  en de volgende Roblox Staff livestream voor tips, trucs en inspiratie.

## [Toegang tot de Assistent vanuit Studio](#toegang-tot-de-assistent-vanuit-studio)[](#toegang-tot-de-assistent-vanuit-studio)

Om toegang te krijgen tot de Assistent vanuit Studio:

1.

Klik op Assistent  aan de rechterkant van de mezzaninebalk.

 ![Assistent-knop aangegeven aan de rechterkant van de mezzaninebalk.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Assistant.png)

2.

Voer een verzoek in het Assistent-venster in.

-

Om een nieuw antwoord te genereren, klik op het opnieuw doen-pictogram.

-

Om het antwoord te beoordelen en toekomstige resultaten te verbeteren, klik op duim omhoog of duim omlaag.

 ![Algemene gebruikersinterface voor Assistent in Studio.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-General-UI.png)

## [Chats en chatgeschiedenis](#chats-en-chatgeschiedenis)[](#chats-en-chatgeschiedenis)

De Assistent ondersteunt meerdere chatthreads per plaats, en je chatgeschiedenis wordt in de cloud opgeslagen, zodat gesprekken behouden blijven over Studio-sessies, machine-herstarts en apparaten heen.

-

Klik op de chatlijstknop en selecteer Nieuwe Chat  bovenaan de lijst om een apart gesprek te starten. Elke chat heeft zijn eigen contextvenster, zodat een lang gesprek in één chat geen ruimte in een andere chat verbruikt. Concepten in het invoerveld worden per chat bewaard.

-

Klik op het takpictogram onder elk Assistent-antwoord om een nieuwe chat van dat bericht te starten. De originele chat blijft zoals hij is, zodat je een andere richting kunt verkennen zonder je huidige plaats te verliezen.

-

Chats zijn beperkt tot de plaats waar je aan werkt, niet de ervaring. Elke plaats heeft zijn eigen set gesprekken, en er is geen harde limiet aan het aantal chats per plaats.

-

Verwijderde chats worden permanent verwijderd en kunnen niet worden hersteld.

Als je Studio op meerdere apparaten open hebt, raden we aan om in één chat tegelijk te werken om conflicten te voorkomen, aangezien de chatgeschiedenis via de cloud synchroniseert.

## [Schermopname subagent](#schermopname-subagent)[](#schermopname-subagent)

De Assistent bevat een schermopname subagent die kan vastleggen wat momenteel zichtbaar is in je 3D-viewport (zowel in Bewerken als Spelen-modus) en dit terug kan beschrijven aan de Assistent. Deze functionaliteit stelt de Assistent in staat om over je scène na te denken zonder dat je deze hoeft te beschrijven. Je kunt vragen stellen zoals "Ziet dit er goed uit?" of "Is de verlichting ingesteld voor de nacht?" en de Assistent zal een screenshot van de viewport maken en antwoorden op basis van wat hij ziet.

Als je een derde partij client gebruikt via MCP of je eigen API-sleutel, heb je nog steeds directe toegang tot de onderliggende screenshot-tool.

## [Stel vragen en leg code uit](#stel-vragen-en-leg-code-uit)[](#stel-vragen-en-leg-code-uit)

Als je algemene kennis of hulp nodig hebt tijdens het maken van een game, kun je de Assistent vragen stellen zoals hoe je een teamsysteem maakt, hoe je een game-loop ontwerpt, hoe je specifieke Studio-tools gebruikt, en nog veel meer. Het kan zelfs code uitleggen die het heeft gegenereerd of die je zelf hebt geschreven.

 ![Code-uitleg gegeven door de Assistent in Studio.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-Explain-Code.png)

## [Bewerk je plaats](#bewerk-je-plaats)[](#bewerk-je-plaats)

### [Scripts](#scripts)[](#scripts)

De Assistent kan nieuwe scripts invoegen, bestaande scripts wijzigen en deze acties indien nodig over meerdere objecten uitvoeren. Als je bijvoorbeeld vraagt om een remote event te maken, kan het een lokaal script, een serverscript en het event allemaal tegelijk maken.

Als je een scriptgeneratieverzoek invoert zoals "Laat het personage van de speler springen wanneer ze dit onderdeel aanraken," toont de Assistent de inhoud van het script en voegt het nieuwe scriptinstance toe aan het momenteel geselecteerde object in het datamodel. Als er niets is geselecteerd, beslist de Assistent waar het moet worden geplaatst op basis van je prompts.

 ![Aangevraagd script ingevoegd in geselecteerd onderdeel.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-Script-Insert.png)

Het gegenereerde script werkt mogelijk niet perfect. In deze gevallen kun je verdere bewerkingen maken in de [Script Editor](/docs/nl-nl/studio/script-editor)  of de Assistent vragen om het script dat het net heeft gemaakt te bewerken. Het kan zelfs handelen op bestaande scripts die het niet heeft gemaakt als je hulp nodig hebt met code die je zelf hebt geschreven.

### [Objecten en Creator Store-activa](#objecten-en-creator-store-activa)[](#objecten-en-creator-store-activa)

De Assistent kan instanties in je datamodel maken, bewerken, verwijderen en itereren, inclusief het invoegen van items uit de Creator Store.

 ![Assistent voegt objecten toe via de Studio-prompt.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-Object-Insert.png)

Als je de code bekijkt, zie je dat de Assistent [InsertService:GetFreeModels()](/docs/nl-nl/reference/engine/classes/InsertService#GetFreeModels)  aanroept om de Creator Store te raadplegen voor een model van een kruiwagen en [Model:PivotTo()](/docs/nl-nl/reference/engine/classes/Model#PivotTo)  gebruikt om het nabij een boom te plaatsen.

#### [Zoek en voeg activa toe](#zoek-en-voeg-activa-toe)[](#zoek-en-voeg-activa-toe)

De Assistent inferreert wanneer hij naar activa op de Creator Store of in je inventarissen moet zoeken op basis van je prompt, en presenteert vervolgens relevante opties waaruit je kunt kiezen voordat er iets in je werkruimte wordt geplaatst. Zoek en voeg toe ondersteunt:

-

Zowel gratis als betaalde  activa op de Creator Store.

-

Je persoonlijke en groepsinventarissen .

-

Filteren op activatype, inclusief Model , Audio , Mesh , MeshPart , Image , Decal , Video , en Package .

-

Creator Store-filters voor prijs, audioduur en geverifieerde makers.

Om een specifiek activum rechtstreeks op basis van zijn ID in te voegen, gebruik je de /insert_asset  slash-opdracht in de Assistent.

## [Genereer inhoud](#genereer-inhoud)[](#genereer-inhoud)

### [Materialen](#materialen)[](#materialen)

Wanneer je een verzoek doet om een materiaal te genereren, kan de Assistent in Studio snel bestaande onderdelen stylen met een lichte versie van de [Material Generator](/docs/nl-nl/studio/material-generator) .

 ![Materiaalvariaties weergegeven in de Assistent voor snelle styling.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-Quick-Styling-Material.png)

### [Meshes](#meshes)[](#meshes)

Om een getextureerde 3D-mesh te genereren:

-

Gebruik de /generate  opdracht gevolgd door je prompt. Bijvoorbeeld, /generate_mesh een rode buggy met knobbelige banden .

-

Vraag de Assistent om een mesh direct te maken. Bijvoorbeeld, "Maak een futuristische kist."

-

Geef een referentieafbeelding in plaats van tekst. /generate_mesh  accepteert ofwel een tekstprompt of een afbeelding, maar niet beide in hetzelfde verzoek.

Je kunt een Onderdeel in je werkruimte gebruiken als een omtrekdoos . Als je een Onderdeel selecteert voordat je een prompt invoert, gebruikt de Assistent de grootte en locatie van het Onderdeel als invoer en zorgt ervoor dat de gegenereerde mesh binnen de gedefinieerde ruimte past.

Je kunt ook een maximaal aantal driehoeken  voor het geretourneerde model definiëren. Lagere waarden resulteren in meer facetteerde en low-poly generaties. Dit is een optionele invoer, die standaard op 10.000 staat.

 ![Een gegenereerde groene draak geleverd door de Assistent in Studio.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-Generated-Green-Dragon.jpg)

### [Procedurele modellen](#procedurele-modellen)[](#procedurele-modellen)

Je kunt tot 50 procedurele modellen genereren binnen een rollend tijdsbestek van 24 uur . Deze limiet reset niet op een vast tijdstip; in plaats daarvan wordt deze continu bijgewerkt op basis van het aantal verzoeken dat in de afgelopen 24 uur is gedaan.

Gebruik de /generate_procedural_model  opdracht om [procedurele modellen](/docs/nl-nl/parts/procedural-models)  te genereren die automatisch schalen en zich aanpassen.

Procedurele modellen stellen je in staat om:

-

Flexibele 3D-modellen te maken met minimale invoer en parameters aan te passen zonder je modellen opnieuw te hoeven bouwen.

-

Automatisch te integreren met engine-functies zoals ongedaan maken/redo, Team Create, netwerkreplicatie, schaling en sleepgereedschappen.

-

Hoge prestaties te behouden, waarbij modellen zich gedragen als standaardobjecten totdat hun parameters veranderen. Dit betekent dat deze modellen bijna geen overhead aan je game toevoegen.

-

Geproduceerde inhoud georganiseerd te houden in een speciale GeneratedFolder , die bron en output scheidt.

Om een procedureel model te genereren, typ je een opdracht zoals /generate_procedural_model een stapel boeken  of voeg je een referentieafbeelding aan je prompt toe. De Assistent genereert vervolgens het procedurele model en voegt het direct toe aan je werkruimte voor verdere aanpassing.

 ![Een gegenereerd reuzenrad met de Assistent in Studio.](https://prod.docsiteassets.roblox.com/assets/assistant/Studio-Procedural-Generation-Ferris-Wheel.png)

### [Segmentatie](#segmentatie)[](#segmentatie)

Segmentatie verdeelt een gegenereerd activum in individuele onderdelen, waardoor je meer controle hebt over hoe je het aanpast. Je kunt verschillende materialen toepassen, scripts bevestigen of individuele componenten vervangen zonder het hele model opnieuw te genereren.

Wanneer je /generate_mesh  of /generate_procedural_model  uitvoert met een tekstprompt, stelt de Assistent een segmentatieplan voor dat definieert hoe het model zal worden verdeeld. Voordat je het model genereert, kun je:

-

De Prompt  bewerken om je beschrijving te verfijnen.

-

OPTIONEEL

 Een Hintafbeelding  uploaden om als visuele referentie te gebruiken. Als je een hintafbeelding uploadt, slaat de Assistent de preview-stap over en genereert het eindmodel direct.

-

Invoeren of verwijderen onder Deelnamen  om te bepalen hoe het model wordt gesegmenteerd. Elk gegenereerd model kan tot acht onderdelen hebben.

-

Suggestie voor segmentatie  aanvinken om de Assistent de onderdelenlijst opnieuw te laten genereren op basis van je prompt.

Wanneer je tevreden bent met de configuratie, klik je op Bevestigen  om vier preview-afbeeldingen te genereren. Als geen van de previews overeenkomt met wat je in gedachten had, klik je op Terug  om het segmentatieplan aan te passen en een nieuwe set previews te maken. Zodra je er een vindt die je leuk vindt, selecteer je deze en klik je op Bevestigen  om het eindmodel te maken. Wanneer het klaar is, klik je op Toevoegen aan plaats  om het activum in je game in te voegen.

Bijvoorbeeld, als je een skateboard genereert en vijf onderdelen definieert (lichaam , linker achterwiel , rechter achterwiel , linker voorwiel , en rechter voorwiel ), verdeelt de Assistent het model in die componenten, zodat je elk afzonderlijk kunt aanpassen.

![...](https://prod.docsiteassets.roblox.com/assets/assistant/Segmentation_Example.png)

![...](https://prod.docsiteassets.roblox.com/assets/assistant/Segmentation_Generation.png)

![...](https://prod.docsiteassets.roblox.com/assets/assistant/Segmentation_List.png)

#### [Segmenteer geïmporteerde meshes](#segmenteer-geïmporteerde-meshes)[](#segmenteer-geïmporteerde-meshes)

Je kunt ook individuele meshes segmenteren die je in Studio importeert met de [3D Importer](/docs/nl-nl/studio/importer) . Het segmenteren van een geïmporteerde mesh stelt je in staat om individuele onderdelen aan te passen zonder het originele model te bewerken en opnieuw te importeren. Bijvoorbeeld, je kunt verschillende materialen of scripts toepassen op specifieke onderdelen, of individuele componenten zoals de wielen van een auto, de handgreep van een zwaard, of de armen van een robot vervangen.

Mesh-segmentatie is in vroege preview, en de resultaten zijn afhankelijk van de topologie van de invoermesh. Voor de meest betrouwbare resultaten, gebruik de [aanbevolen deelnamen](#aanbevolen-deelnamen)  voor ondersteunde objecttypes.

Om een geïmporteerde mesh te segmenteren:

1.

Selecteer de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  in de werkruimte. Zorg ervoor dat je de mesh zelf selecteert, niet een bovenliggende [Model](/docs/nl-nl/reference/engine/classes/Model)  of andere instantie.

2.

Open de Assistent en voer /segment_mesh  in.

3.

Voer tot vijf namen in voor de onderdelen die je wilt maken. Je kunt elke deelnamen gebruiken, maar de [aanbevolen deelnamen](#aanbevolen-deelnamen)  voor veelvoorkomende objecttypes leveren de meest betrouwbare resultaten op.

4.

Klik op Bevestigen . De Assistent segmenteert de mesh in de opgegeven onderdelen en vervangt de originele mesh in de werkruimte door de gesegmenteerde versie.

Om meer dan vijf onderdelen te maken, voer je /segment_mesh  opnieuw uit op de gesegmenteerde mesh.

#### [Aanbevolen deelnamen](#aanbevolen-deelnamen)[](#aanbevolen-deelnamen)

Hoewel elk gegenereerd activum kan worden gesegmenteerd, produceren de onderstaande aanbevolen deelnamen momenteel de meest betrouwbare resultaten voor hun overeenkomstige objecttypes.

Wanneer je je eigen segmentatie definieert, gebruik deze deelnamen als uitgangspunt en pas ze aan indien nodig.

| Objecttype | | Aanbevolen deelnamen |
| --- | --- |
| auto | | lichaam, linker voorwiel, rechter voorwiel, linker achterwiel, rechter achterwiel |
| ambulance / politieauto | | lichaam, linker voorwiel, rechter voorwiel, linker achterwiel, rechter achterwiel, sirene lichtbalk |
| gevechtsauto | | lichaam, linker voorwiel, rechter voorwiel, linker achterwiel, rechter achterwiel, kanon |
| sleepwagen | | lichaam, linker voorwiel, rechter voorwiel, linker achterwiel, rechter achterwiel, sleephaak |
| aanhangwagen | | lichaam, linker wiel, rechter wiel, koppeling |
| motorfiets | | frame, stuur, voorvork, voorwiel, achterwiel |
| skateboard | | lichaam, linker voorwiel, rechter voorwiel, linker achterwiel, rechter achterwiel |
| propeller vliegtuig | | lichaam, propeller |
| gevechtspropeller vliegtuig | | lichaam, propeller, kanon |
| jet vliegtuig | | lichaam, duwer |
| helikopter | | lichaam, hoofdrotorblad |
| gevechtshelikopter | | lichaam, hoofdrotorblad, kanon |
| dron | | lichaam, linker voorpropeller, rechter voorpropeller, linker achterpropeller, rechter achterpropeller |
| jetpack | | rugzak, duwer |
| motorboot | | lichaam, motor |
| gevechtsmotorboot | | lichaam, motor, kanon |
| onderzeeër | | romp, propeller |
| zaklamp | | handgreep, kop, lens |
| schatkist | | lichaam, deksel |
| houweel | | handgreep, kop |
| wapen | | greep, frame, loop |
| snipergeweer | | greep, frame, loop, richtkijker |
| toren | | driepotige basis, draaibare bevestiging, wapenlichaam, loop, schildplaat |
| kanon | | loopbasis, loop, linker wiel, rechter wiel |
| toverstok | | handgreep, punt |
| zwaard | | handgreep, handbeschermer, lemmet, pommel |
| honkbalbat | | handgreep, loop |
| granaat | | granaatlichaam, veiligheidshevel, trekpen |

Voor meer voorbeelden van het werken met gesegmenteerde modellen, zie het [Gedragingen Referentiespel](https://www.roblox.com/games/105116507559995/Behaviors-Reference-Experience)  .rbxl  bestand.

## [Planningsmodus](#planningsmodus)[](#planningsmodus)

Planningsmodus stelt je in staat om de volgende stappen van de Assistent te bekijken voordat ze worden uitgevoerd. Wanneer je een complex verzoek indient, genereert de Assistent een plan dat je kunt bekijken en aanpassen.

Je kunt Planningsmodus activeren door:

-

Op de dropdown in het invoerpaneel van de Assistent te klikken en Plan  te selecteren.

-

De opdracht /plan  in de Assistent in te voeren.

 ![Voorbeeld van Planningsmodus in de Assistent.](https://prod.docsiteassets.roblox.com/assets/assistant/PlanningMode.png)

### [Bewerkbare Markdown-plannen](#bewerkbare-markdown-plannen)[](#bewerkbare-markdown-plannen)

Gegenereerde plannen worden opgeslagen als bewerkbare Markdown-documenten die behouden blijven over chatsessies heen, zodat je workflows kunt verfijnen voordat ze worden uitgevoerd.

-

Cross-sessie cloudopslag : Plannen worden in de cloud opgeslagen en zijn gekoppeld aan zowel je ervaring als je makerprofiel in plaats van aan een enkele chatsessie. Net als de chatgeschiedenis van de Assistent zijn plannen privé en niet zichtbaar voor samenwerkers.

-

Geïntegreerde Markdown-editor : Nadat de Assistent een plan heeft gemaakt, klik je op Open Plan  in de chatinterface om de speciale Markdown-editor te openen, waar je het opgemaakte document kunt bekijken of de inhoud direct kunt wijzigen.

-

Opslaan en bijwerken van plannen : Klik op Opslaan  om een diff van je handmatige bewerkingen terug te sturen naar de Assistent, die zijn onderliggende takenlijst bijwerkt. Omgekeerd, het aanroepen van de Assistent in de chat werkt automatisch het plan Markdown-bestand bij.

-

Expliciete goedkeuringspoort : Plannen worden nooit automatisch uitgevoerd of verlopen naar acceptatie. De workflow wordt alleen uitgevoerd wanneer je op Bouwen  in de chat van de Assistent klikt.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
