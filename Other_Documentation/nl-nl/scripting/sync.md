<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/sync -->

Script Synchronisatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Op bestanden gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows)

# Script Synchronisatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox Studio heeft een ingebouwde [scripteditor](/docs/nl-nl/studio/script-editor)  voor het bewerken van de code in je Roblox-project. De editor bevat belangrijke functies zoals linting, typechecking, autocompletion en samenwerkingsbewerking.

Veel ontwikkelaars hebben echter een voorkeur voor een teksteditor of geïntegreerde ontwikkelomgeving (IDE), zoals [Visual Studio Code](https://code.visualstudio.com) , [Cursor](https://cursor.com) , [Sublime Text](https://www.sublimetext.com)  of [Notepad++](https://notepad-plus-plus.org) . Populaire ontwikkelomgevingen hebben vaak functies of plugins die niet in Studio aanwezig zijn. Om een externe editor of IDE met Studio te gebruiken, schakel je de Script Synchronisatie -functie in.

Script Synchronisatie werkt door de scripts in je [datamodel](/docs/nl-nl/projects/data-model)  te synchroniseren met tekstbestanden op je lokale schijf. Wijzigingen die in de Luau-bestanden op de schijf worden aangebracht, worden toegepast op de scripts in Studio, en vice versa. Deze synchronisatie betekent dat je een script in een externe editor zoals VS Code kunt bewerken en de wijziging onmiddellijk in Studio kunt zien.

## [Wanneer Script Synchronisatie te gebruiken](#wanneer-script-synchronisatie-te-gebruiken)[](#wanneer-script-synchronisatie-te-gebruiken)

-

Als je je favoriete teksteditor wilt gebruiken of code in versiebeheer wilt controleren, maar Studio voor de rest wilt gebruiken, is Script Synchronisatie een goede keuze. Het werkt ook met Roblox's [ingebouwde samenwerkingstools](/docs/nl-nl/projects/collaboration) , die vaak niet beschikbaar zijn in externe tools.

Script Synchronisatie werkt goed met bestaande Roblox-projecten, aangezien het een extra functie is in plaats van een totale verschuiving in hoe je het project beheert.

-

Als je je hele project (niet alleen de code) in versiebeheer wilt controleren of je bestandssysteem als de bron van waarheid voor je project wilt gebruiken, zijn [derde partij tools](/docs/nl-nl/projects/external-tools)  zoals Rojo een betere keuze. Om setups voor teams te vergelijken, zie [Vergelijk bestand-gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows) .

Het is momenteel niet mogelijk om de debugger van Roblox Studio vanuit een externe ontwikkelomgeving te bedienen.

## [Script Synchronisatie instellen](#script-synchronisatie-instellen)[](#script-synchronisatie-instellen)

1.

Selecteer in de Explorer  een of meer mappen die je wilt synchroniseren.

2.

Klik met de rechtermuisknop en selecteer Script Synchronisatie  ⟩ Synchroniseren met Directory… .

 ![Het Explorer-venster met het Script Synchronisatie-menu uitgebreid.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Script-Sync.png)

3.

Kies een directory op je computer (of maak een nieuwe aan) en klik op Opslaan .

4.

Klik in Studio opnieuw met de rechtermuisknop op de map en selecteer Script Synchronisatie  ⟩ Toon in Explorer  (Windows) of Toon in Finder  (macOS).

5.

Open de directory in je favoriete teksteditor.

Als alternatief kun je met de rechtermuisknop op een individueel script in Studio klikken en Openen in Externe Editor  selecteren.

Je kunt individuele scripts synchroniseren, maar we raden ten zeerste aan om mappen te synchroniseren; als je een map synchroniseert, synchroniseert Script Synchronisatie automatisch de submappen en scripts, waardoor je scripts kunt maken, verwijderen en hernoemen zonder elke keer de synchronisatie in te schakelen.

Nadat je Script Synchronisatie hebt ingesteld, wil je bijna zeker een [LSP-extensie toevoegen](#stel-een-taalsserver-in)  aan je teksteditor. Voor richtlijnen over het organiseren van je code, zie [Scripttypes en locaties](/docs/nl-nl/scripting/locations#aanbevelingen) .

Je hoeft de synchronisatie maar één keer in te stellen. Wanneer je Studio opnieuw opstart en je plaats opent, onthoudt Script Synchronisatie wat je aan het synchroniseren was en hervat automatisch.

## [Limieten](#limieten)[](#limieten)

Script Synchronisatie ondersteunt tot 10.000 scripts per top-level gesynchroniseerde instantie en tot 128 top-level gesynchroniseerde instanties, zodat het kan schalen naar grote codebases.

## [Conflictoplossing](#conflictoplossing)[](#conflictoplossing)

Wanneer je de synchronisatie start of hervat, als er verschillen zijn tussen Studio en je bestanden op de schijf, toont Script Synchronisatie een gedetailleerde oplossingsdialoog. De dialoog toont welke scripts aan elke kant zullen worden toegevoegd, gewijzigd of verwijderd, zodat je de impact van het kiezen van Studio behouden  versus Schijf behouden  kunt begrijpen.

## [Selectieve verwijdering](#selectieve-verwijdering)[](#selectieve-verwijdering)

Wanneer je een gesynchroniseerd script of een map in Studio of op de schijf verwijdert, verwijdert Script Synchronisatie alleen Luau-scripts en ondersteunde bestanden. Het verwijdert geen niet-Luau-bestanden of mappen die het niet beheert; niet-scriptactiva zoals modellen en onderdelen blijven behouden, zelfs als je gesynchroniseerde items eromheen verwijdert of reorganiseert.

## [Team Create](#team-create)[](#team-create)

Script Synchronisatie werkt met [Team Create](/docs/nl-nl/projects/collaboration) . De Explorer  toont een pictogram op instanties die een medewerker momenteel synchroniseert. Om dubbele namen te voorkomen, voegt Script Synchronisatie automatisch een numerieke suffix toe aan de naam van elke nieuwe instantie die onder een boom wordt toegevoegd die jij of een medewerker aan het synchroniseren is.

Vermijd workflows waarbij meerdere mensen hetzelfde gesynchroniseerde script synchroniseren en de bestanden tegelijkertijd bewerken. Script Synchronisatie blijft functioneren, maar medewerkers kunnen elkaars wijzigingen overschrijven.

## [Gebruik Script Synchronisatie met een team](#gebruik-script-synchronisatie-met-een-team)[](#gebruik-script-synchronisatie-met-een-team)

In een Studio-native workflow werkt het team direct in een gedeelde plaats met Team Create, en elke programmeur gebruikt Script Synchronisatie om code in een Git-repository te houden. Niets aan de manier waarop de plaats wordt opgeslagen verandert, zodat je deze workflow op elk moment in een bestaand spel kunt aannemen. Om dit te vergelijken met andere workflows, zie [Vergelijk bestand-gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows) .

 ![Drie medewerkers bewerken dezelfde plaats in een Team Create-sessie, elk met een gekleurde selectieomtrek.](https://prod.docsiteassets.roblox.com/assets/studio/collaboration/Collaborative-Session.jpg)

1.

Zet [Team Create](/docs/nl-nl/projects/collaboration)  aan voor je spel en voeg je medewerkers toe.

2.

[Stel Script Synchronisatie in](#script-synchronisatie-instellen)  voor de mappen die je scripts bevatten, en kies een directory binnen je lokale Git-repository.

3.

Open de directory in je favoriete editor en [stel een taalsserver in](#stel-een-taalsserver-in) .

4.

Commit en review codewijzigingen in Git zoals je normaal zou doen.

Voor het organiseren van gesynchroniseerde code, zie [Scripttypes en locaties](/docs/nl-nl/scripting/locations#aanbevelingen) .

### [Afwegingen](#afwegingen)[](#afwegingen)

| Voordelen | | Nadelen |
| --- | --- |
|
-

Geen tools te installeren behalve een editor.

-

Werkt met Team Create, inclusief medewerkers die verschillende mappen tegelijk synchroniseren.

-

Geen conversiestap voor bestaande spellen.

 | |
-

Alleen scripts en mappen worden gesynchroniseerd, dus modellen, onderdelen, attributen en tags zijn niet in Git.

-

Twee mensen die hetzelfde gesynchroniseerde script tegelijk bewerken, kunnen elkaars wijzigingen overschrijven.

-

Het samenvoegen van een branch in Git werkt de plaats voor de rest van het team niet bij.

 |

## [Belangrijke tips](#belangrijke-tips)[](#belangrijke-tips)

-

Script Synchronisatie synchroniseert alleen [Script](/docs/nl-nl/reference/engine/classes/Script) , [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  en [Folder](/docs/nl-nl/reference/engine/classes/Folder)  instanties. Alle andere instanties in een gesynchroniseerde map worden genegeerd. Vermijd het synchroniseren van mappen die scripts naast andere instanties bevatten.

-

Je kunt pakketten synchroniseren, hoewel de [PackageLink](/docs/nl-nl/reference/engine/classes/PackageLink)  zelf niet naar de schijf wordt geschreven.

-

Synchroniseer geen scripts die attributen of tags hebben. Script Synchronisatie negeert deze, wat kan leiden tot gegevensverlies als je scripts maakt of verwijdert of begint met synchroniseren met een oudere versie van je bestanden op de schijf.

-

Script Synchronisatie vereist dat de namen van scripts compatibel zijn met je bestandssysteem—geen dubbele namen of niet-ondersteunde tekens. Als Studio een van deze problemen tegenkomt, geeft het een foutmelding en vraagt je om de situatie op te lossen voordat je de synchronisatie hervat.

-

Als er gesynchroniseerde bestanden of mappen veranderen terwijl Studio gesloten is, vraagt Studio je hoe je de situatie wilt oplossen wanneer je de plaats opnieuw opent.

-

Het verwijderen van een top-level (of "root") instantie—de instantie die je aanvankelijk hebt gesynchroniseerd—op je lokale schijf kan ervoor zorgen dat Studio een foutmelding geeft. Om een top-level instantie te verwijderen:

1.

Klik in Studio met de rechtermuisknop op het script of de map en selecteer Script Synchronisatie  ⟩ Stop Synchronisatie .

2.

Kies de optie Verwijder bestand(en)  of Verwijder map(pen)  om de instantie van je lokale schijf te verwijderen.

3.

Verwijder het script of de map in Studio.

Je kunt kindinstanties in Studio of op je lokale schijf verwijderen zonder de synchronisatie uit te schakelen, en de verwijdering synchroniseert zoals je zou verwachten.

## [Stel een taalsserver in](#stel-een-taalsserver-in)[](#stel-een-taalsserver-in)

Taalservers geven je teksteditor taal-specifieke functies zoals autocompletion, typechecking, "ga naar definitie," en meer. Voor VS Code raden we [Luau Language Server](https://marketplace.visualstudio.com/items?itemName=JohnnyMorganz.luau-lsp)  aan.

Taalserverprotocol (LSP) extensies moeten de datamodelhiërarchie van een project begrijpen om goed te functioneren. De VS Code-extensie wordt geleverd met een bijbehorende Studio-plugin ([Luau Language Server Companion](https://create.roblox.com/store/asset/10913122509/Luau-Language-Server-Companion) ) die deze gegevens levert.

We raden ten zeerste aan om beide te installeren.  Als je de VS Code-extensie en de bijbehorende Studio-plugin gebruikt, zullen taalfuncties correct werken in VS Code terwijl je Script Synchronisatie gebruikt.

## [Aanbevolen extensies](#aanbevolen-extensies)[](#aanbevolen-extensies)

De gemeenschap onderhoudt deze extensies. We raden ze aan op basis van hun functionaliteit, maar kunnen geen garanties bieden over prestaties of beveiliging. Controleer voordat je een extensie installeert of deze afkomstig is van een betrouwbare bron en niet kwaadaardig is.

-

[Roblox Luau LSP](https://marketplace.visualstudio.com/items?itemName=JohnnyMorganz.luau-lsp)  en [Luau Language Server Companion](https://create.roblox.com/store/asset/10913122509/Luau-Language-Server-Companion)  - Taalfuncties (zie hierboven)

-

[selene](https://marketplace.visualstudio.com/items?itemName=Kampfkarren.selene-vscode)  - Statische code-analyse (linting)

-

[StyLua](https://marketplace.visualstudio.com/items?itemName=JohnnyMorganz.stylua)  - Automatische code-opmaak

## [Synchronisatieregels](#synchronisatieregels)[](#synchronisatieregels)

Bij het synchroniseren van een instantie met kinderen met een directory op de schijf, zal Studio automatisch aanmaak-, hernoem-, verplaats- en verwijderbewerkingen op kinderen synchroniseren met de overeenkomstige bestanden en mappen op de schijf. Deze aanpak stelt je in staat om je code te onderhouden zonder handmatig de synchronisatie op individuele scripts te stoppen en te starten.

Op de schijf gebruikt Script Synchronisatie de volgende regels om de verschillende soorten scripts van elkaar te onderscheiden.

| Naamgevingsconventie op schijf | | Instantietype in Studio |
| name.luau | | [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) |
| name.server.luau | | Script met Server  [Script.RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext) |
| name.client.luau | | Script met Client  [Script.RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext) |
| name.local.luau | | [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) |
| name.legacy.luau | | Script met Legacy  [Script.RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext) |
| name.plugin.luau | | Script met Plugin  [Script.RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext) |
| name/  (directory) | | [Folder](/docs/nl-nl/reference/engine/classes/Folder) |
| name/init.*.luau | | Scriptinstantie met kinderen. Type (* ) wordt bepaald door de bovenstaande regels. |

## [Instellingen](#instellingen)[](#instellingen)

Script Synchronisatie heeft verschillende instellingen in het [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  venster (Alt S  of ⌥ S ). De standaardopties zijn een goede keuze voor de meeste gebruikssituaties.

| Instelling | | Beschrijving |
| Automatisch synchroniseren bij openen plaats | | Of Studio moet synchroniseren wanneer je een plaats opent. Het uitschakelen van deze instelling vermindert de bruikbaarheid van Script Synchronisatie aanzienlijk. |
| Hervat conflicterende synchronisatie bij openen plaats | | Hoe Studio conflicten moet afhandelen wanneer je een plaats opent. De standaardoptie, Niet hervatten , dwingt je om conflicten handmatig op te lossen om gegevensverlies te voorkomen. Je kunt ook kiezen om de versie op de schijf of de versie in Studio te verkiezen. |
| Houd lokale bestanden/mappen na synchronisatie | | Hoe om te gaan met bestanden op de schijf nadat je Script Synchronisatie  > Stop Synchronisatie  in Studio hebt geselecteerd. |
| Bestandsuitbreiding | | De bestandsuitbreiding die moet worden gebruikt voor scripts op de schijf. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
