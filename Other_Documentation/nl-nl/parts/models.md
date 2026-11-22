<!-- Source: https://create.roblox.com/docs/nl-nl/parts/models -->

Modellen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# Modellen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Modellen  zijn containers voor fysieke objecten die je kunt gebruiken om je werkruimte te organiseren en je middelen, zoals onderdelen, lasverbindingen of gewrichten, te groeperen. Terwijl modellen vaak verbonden onderdelen bevatten die bekend staan als een [assemblage](/docs/nl-nl/physics/assemblies) , kunnen ze ook een onbeperkt aantal individuele onderdelen of objecten bevatten, zoals scripts, bijlagen of andere modellen.

Om dit te demonstreren, zijn avatarpersonages een enkele [Model](/docs/nl-nl/reference/engine/classes/Model)  die de juiste humanoïde onderdelen, gewrichten en scripts bevat die nodig zijn voor runtime-gedrag:

![Een voorbeeld van een personagemodel van een humanoïde monstermeisje in een donkerpaarse jurk.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-3D.jpg) Een model genaamd Octavia

![De groeperingen die het Octavia-model in het Explorer-venster van Studio vormen.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-Hierarchy.png) De groeperingen die het model vormen

## [Modellen maken](#modellen-maken)[](#modellen-maken)

Je kunt modellen maken met behulp van elk open gebruik of beperkt middel, maar alle beperkte middelen waarvoor je geen [expliciete toestemming](/docs/nl-nl/projects/assets/privacy#bekijk-machtigingen)  hebt om te gebruiken, zijn niet  zichtbaar of hoorbaar tijdens runtime, tenzij het spel zelf toestemming heeft om die middelen te gebruiken.

Er zijn twee manieren om modellen te maken:

-

Groepeer objecten samen om automatisch een [Model](/docs/nl-nl/reference/engine/classes/Model)  object te vormen.

-

Voeg een leeg [Model](/docs/nl-nl/reference/engine/classes/Model)  object toe aan de Workspace en voeg vervolgens handmatig kindobjecten aan het model toe.

Om een model te maken met de groepeer-methode:

1.

Selecteer in het Explorer -venster of de 3D-weergave elk object dat je in een model wilt groeperen.

2.

Klik met de rechtermuisknop op een van de objecten en selecteer Groeperen , of druk op Ctrl G  op Windows of ⌘ G  op Mac. Een nieuw [Model](/docs/nl-nl/reference/engine/classes/Model)  object wordt weergegeven met al de objecten die het model vormen genest eronder.

 ![Een close-up van het Explorer-venster. Een Model-object is gemarkeerd met drie geneste kinderen.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Group-Simple.png)

Om een model volledig terug te groeperen naar zijn oorspronkelijke objecten, klik je met de rechtermuisknop en selecteer je Ungroeperen , of druk op Ctrl U  op Windows of ⌘ U  op Mac.

### [Stel een primair onderdeel in](#stel-een-primair-onderdeel-in)[](#stel-een-primair-onderdeel-in)

Als je een model hebt met onderdelen die zijn verbonden door fysieke gewrichten zoals [WeldConstraints](/docs/nl-nl/reference/engine/classes/WeldConstraint)  of [Motor6Ds](/docs/nl-nl/reference/engine/classes/Motor6D) , moet je een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen het model specificeren om een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  te worden. Een model's [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  is de fysieke referentie die aangeeft met welk [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  het draaipunt en de begrenzingsdoos moeten bewegen wanneer het model van positie of oriëntatie verandert.

Om een primair onderdeel in te stellen:

1.

Selecteer in het Explorer -venster een model.

2.

Selecteer in het Eigenschappen -venster de eigenschap PrimaryPart . Je cursor verandert.

3.

Ga terug naar het Explorer -venster en selecteer het onderdeel dat je je primaire onderdeel wilt maken.

## [Modellen selecteren](#modellen-selecteren)[](#modellen-selecteren)

Wanneer je over modellen in de viewport beweegt, worden ze omrand om hun potentiële selectie aan te geven. Je kunt een omrand model selecteren door erop te klikken, of je kunt meerdere modellen selecteren door Shift , Ctrl  of ⌘  ingedrukt te houden terwijl je eroverheen beweegt en erop klikt.

 ![Een magazijnweergave in de 3D-weergave. Meerdere modellen zijn geselecteerd en gemarkeerd met een lichtblauwe omranding.](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window-Object-Selection.jpg)

Aangezien modellen doorgaans meerdere kind [onderdelen](/docs/nl-nl/parts)  of [mesh](/docs/nl-nl/parts/meshes)  bevatten, kunnen sommige kinderen verborgen zijn. Om een specifiek kind te selecteren zonder de camera te verplaatsen of het kind in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie te lokaliseren, klik je terwijl je Alt  ingedrukt houdt op Windows of ⌥  op Mac om [selectiecycli](/docs/nl-nl/studio/overview#selection-cycling)  uit te voeren.

Selectiecycli

## [Modellen transformeren](#modellen-transformeren)[](#modellen-transformeren)

Je kunt een model verplaatsen, schalen of roteren met behulp van de Studio [transform](/docs/nl-nl/parts#onderdelen-transformeren)  tools. Tenzij je een [primair onderdeel](#stel-een-primair-onderdeel-in)  hebt ingesteld, transformeert een model op basis van het midden van zijn begrenzingsdoos.

Bovendien kun je binnen een [Script](/docs/nl-nl/reference/engine/classes/Script)  of [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  een model verplaatsen of roteren via de volgende methoden:

| Methode | | Beschrijving |
| --- | --- |
| [MoveTo()](/docs/nl-nl/reference/engine/classes/Model#MoveTo) | | Verplaatst het [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  van het model naar de opgegeven positie. Als er geen primair onderdeel is opgegeven, wordt het hoofdonderdeel van het model gebruikt. |
| [PivotTo()](/docs/nl-nl/reference/engine/classes/PVInstance#PivotTo) | | Transformeert het model samen met al zijn afgeleide [PVInstances](/docs/nl-nl/reference/engine/classes/PVInstance)  zodat het draaipunt zich op de opgegeven [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  bevindt. |
| [TranslateBy()](/docs/nl-nl/reference/engine/classes/Model#TranslateBy) | | Verschuift een model met de opgegeven [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  offset, waarbij de oriëntatie van het model behouden blijft. |

## [Modelgedragingen](#modelgedragingen)[](#modelgedragingen)

Hoewel modellen voor de meeste doeleinden in je spel vergelijkbaar functioneren als [Folder](/docs/nl-nl/reference/engine/classes/Folder)  objecten, vertonen ze ook enkele unieke gedragingen.

### [Personagemodellen](#personagemodellen)[](#personagemodellen)

Wanneer een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  aanwezig is in een model dat een [Part](/docs/nl-nl/reference/engine/classes/Part)  genaamd Hoofd  bevat, toont Roblox een naam en/of gezondheidsbalk boven dat onderdeel. Voor meer informatie, zie [Karakter Naam/Gezondheidsweergave](/docs/nl-nl/characters/name-health-display) .

 ![Karakterweergave-informatie boven een in-game avatar.](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Display-Indicated.jpg)

### [Vernietigingshoogte](#vernietigingshoogte)[](#vernietigingshoogte)

Om te voorkomen dat onderdelen die van de kaart van een spel zijn gevallen, voor altijd blijven vallen, vernietigt Studio automatisch onderdelen die onder de waarde van [Workspace.FallenPartsDestroyHeight](/docs/nl-nl/reference/engine/classes/Workspace#FallenPartsDestroyHeight)  vallen. Als een onderdeel dat om deze reden is vernietigd het laatste onderdeel in een model is, wordt dat model ook vernietigd.

## [Modelstreaming](#modelstreaming)[](#modelstreaming)

Instance [streaming](/docs/nl-nl/workspace/streaming)  laadt en ontlaadt dynamisch [Models](/docs/nl-nl/reference/engine/classes/Model)  op het apparaat van een speler terwijl hun karakter de 3D-wereld verkent. Met streaming ingeschakeld, kun je specificeren hoe elk model moet worden behandeld onder streaminggedrag. Bijvoorbeeld, een model dat is ingesteld op [Persistent](/docs/nl-nl/workspace/streaming#persistent)  zal nooit worden gestreamd, of een model dat is ingesteld op [Atomic](/docs/nl-nl/workspace/streaming#atomisch)  zal in en uit streamen als een enkele eenheid met al zijn afgeleiden. Voor meer informatie, zie [per-model streamingcontroles](/docs/nl-nl/workspace/streaming#per-model-streaming-controls) .

Omdat de 3D-inhoud die op de client bestaat dynamisch verandert in een streaming-ingeschakeld spel, kunnen modellen plotseling verdwijnen, wat visueel schokkend kan zijn voor de speler. Om deze situatie te vermijden, kun je specifieke modellen instellen om te renderen als geoptimaliseerde "SLIM" meshes of als lagere resolutie "imposter" meshes wanneer ze worden gestreamd. Zie [modelniveau van detail](/docs/nl-nl/workspace/streaming/techniques#model-niveau-van-detail) .

## [Modellen uploaden](#modellen-uploaden)[](#modellen-uploaden)

Wanneer je een .gltf , .fbx  en .obj  modelbestand naar de cloud uploadt of importeert met behulp van de [Importer](/docs/nl-nl/art/accessories/creating-rigid/importing) , vertegenwoordigt Roblox het als een cloud-gebaseerd middel met een unieke bijbehorende ID. Dit cloud-gebaseerde middelensysteem stelt je in staat om modellen op te slaan via Roblox en ze opnieuw te gebruiken op het platform in verschillende contexten zonder lokale kopieën te onderhouden als onderdeel van elk opgeslagen Studio-spel.

Om een model dat je in Studio hebt gemaakt te uploaden:

1.

Klik met de rechtermuisknop op je model in het Explorer -venster. Een contextmenu wordt weergegeven.

2.

Selecteer Opslaan naar Roblox . Het Asset Configuratievenster  wordt weergegeven.

3.

In het Asset Configuratievenster ,

1.

Stel Inhoudstype  in op Ontwikkelingsitem .

2.

Stel Middelcategorie  in op Model .

3.

Vul de volgende velden in:

-

Titel  - De naam van je model.

-

Beschrijving  - Een korte beschrijving van je model.

-

Maker  - Gebruik de dropdown om te selecteren of je dit middel als individu of als onderdeel van een bijbehorende groep wilt publiceren.

-

Genre  - Het genre van je model.

4.

Klik op de Opslaan -knop. Na een moment toont het Asset Configuratievenster  de asset-ID van je model die je kunt gebruiken in je projecten of delen met andere makers, groepen of spellen. Voor meer informatie over het verlenen van toestemming aan samenwerkers en spellen zodat zij je modellen kunnen gebruiken, zie [Middelprivacy](/docs/nl-nl/projects/assets/privacy)

## [Modellen distribueren en verkopen](#modellen-distribueren-en-verkopen)[](#modellen-distribueren-en-verkopen)

Je kunt je eigen modellen openbaar distribueren en verkopen in de Creator Store voor Amerikaanse dollars (USD), zolang de modellen minder dan 15.000 afhankelijkheden hebben. Elk van deze afhankelijkheden moet een zijn:

-

Open gebruiksasset of een beperkt middel dat je hebt gemaakt, exclusief audio en video.

-

Audio- of videoasset die je hebt verkregen uit de Creator Store.

Deze monetisatiemethode stelt je in staat om 100% van de netto-opbrengsten van transacties te verdienen, waarbij platformkosten en DevEx-tarieven worden omzeild. Voor meer informatie over middelen en verkoperseisen, inclusief hoe je een verkopersaccount kunt instellen om prijzen in te stellen en betalingen te ontvangen, zie [Creator Store - Middelen distribueren en verkopen](/docs/nl-nl/production/creator-store#verspreiden-en-verkopen-van-assets) .

Als je een model wilt distribueren met een kind-audioasset dat je hebt gemaakt, moet je het audioasset op de Creator Store * voordat*  je het een kind van het model maakt, distribueren zodat de audio hoorbaar is tijdens runtime.

Bij het maken van modellen voor de Creator Store, zorg ervoor dat:

-

Het model en zijn afhankelijkheden voldoen aan de [Gemeenschapsregels](https://en.help.roblox.com/hc/articles/203313410) , [Gebruiksvoorwaarden](https://en.help.roblox.com/hc/articles/115004647846) , [Intellectuele Eigendomsrichtlijnen](/docs/nl-nl/production/publishing/ip-guidelines)  en vereisten van de Creator Store.

-

Het model is ingesteld op een redelijke schaal en oriëntatie zodat het direct bruikbaar is wanneer het vanuit de Creator Store wordt ingevoegd.

-

Alle afhankelijkheden van het model worden zonder waarschuwingen in Studio geïmporteerd.

-

Elke mesh-afhankelijkheid bevat niet meer dan 20.000 driehoeken.

-

Elke textuurafhankelijkheid voldoet aan de [textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications)  van Roblox.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
