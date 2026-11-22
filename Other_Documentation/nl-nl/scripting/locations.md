<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/locations -->

Scripttypes en locaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)

# Scripttypes en locaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor veel ontwikkelaars is de fundamentele uitdaging van het aanpassen aan Roblox-scripting het belang van de bestandslocatie en de [Script.RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext) -eigenschap. Afhankelijk van het type script, de locatie in de Explorer  en de uitvoeringscontext, kunnen scripts heel verschillend gedrag vertonen. Bepaalde methode-aanroepen kunnen mislukken, objecten in je spel kunnen ontoegankelijk zijn, of scripts kunnen helemaal niet draaien.

De reden voor deze complexiteit is dat Roblox-spellen standaard multiplayer zijn. Scripts moeten de mogelijkheid hebben om alleen op de server te draaien, alleen op de client, of gedeeld te worden tussen beide. De evolutie van het Roblox-platform in de loop der tijd heeft de situatie verder gecompliceerd.

## [Scripttypes](#scripttypes)[](#scripttypes)

Roblox heeft drie soorten scripts:

-

[Script](/docs/nl-nl/reference/engine/classes/Script)  - Code die draait op de server of de client, afhankelijk van de locatie en de [Script.RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext) -eigenschap.

-

[LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  - Code die alleen op de client draait. Heeft geen uitvoeringscontext.

-

[ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  - Code die je kunt hergebruiken in andere scripts. Heeft geen uitvoeringscontext.

Wanneer je een [Script](/docs/nl-nl/reference/engine/classes/Script)  aanmaakt, is de standaard uitvoeringscontext Legacy , wat betekent dat het a) een server-side script is en b) alleen draait als het zich in een servercontainer bevindt, zoals [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  of [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) .

-

Als je de uitvoeringscontext van het script wijzigt naar Server , kan het nu ook draaien in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , maar we raden dit niet aan. De inhoud van die locatie wordt gerepliceerd naar clients, dus het is een slechte locatie voor server-side scripts.

-

Als je de uitvoeringscontext van het script wijzigt naar Client , kan het draaien in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Het kan ook draaien in [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  en [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) . Startercontainers worden gekopieerd naar clients, dus het originele script en  de kopie draaien, wat niet wenselijk is.

Om de uitvoeringscontext van een script te wijzigen, selecteer je het in de [Explorer](/docs/nl-nl/studio/explorer)  en wijzig je de waarde in het [Properties](/docs/nl-nl/studio/properties)  venster.

 ![RunContext-eigenschap aangegeven voor een Script.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Script-RunContext.png)

## [Aanbevelingen](#aanbevelingen)[](#aanbevelingen)

-

Plaats een enkele [Script](/docs/nl-nl/reference/engine/classes/Script)  met een RunContext  van Client  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

-

Plaats een enkele [Script](/docs/nl-nl/reference/engine/classes/Script)  met een RunContext  van Server  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) .

-

Gebruik [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  voor zoveel mogelijk client- en servercode. Vereis deze modules vanuit je clientscript en je serverscript.

Deze aanpak geeft je code een enkel toegangspunt aan de client- en serverzijde, wat de organisatie vereenvoudigt en het gemakkelijk maakt om problematische modules te isoleren of uit te schakelen. Voeg een start() -functie toe aan elke [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) , zodat alle modules kunnen laden voordat je begint met het uitvoeren van hun code:

Voorbeeld server script

```

--!strict

local ServerScriptService = game:GetService("ServerScriptService")

local SampleModule = require(ServerScriptService.SampleModule)

local AnotherSampleModule = require(ServerScriptService.AnotherSampleModule)

SampleModule.start()

AnotherSampleModule.start()

```

Voorbeeld module

```

--!strict

local CollectionService = game:GetService("CollectionService")

local NPC_TAG = "npc"

local SampleModule = {}

local function setUpNpc(npc: Instance)

    -- initialiseer elke NPC

end

local function cleanUpNpc(npc: Instance)

    -- voer uit wanneer het evenement afgaat

end

function SampleModule.start() -- voeg de functie toe aan de tabel

    -- voorbeeld lus voor setup op basis van tags

    for _, npc in CollectionService:GetTagged(NPC_TAG) do

        setUpNpc(npc)

    end

    -- voer functies uit wanneer evenementen afgaan

    CollectionService:GetInstanceAddedSignal(NPC_TAG):Connect(setUpNpc)

    CollectionService:GetInstanceRemovedSignal(NPC_TAG):Connect(cleanUpNpc)

end

return SampleModule

```

-

Om code te delen, gebruik [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  in ReplicatedStorage  en vereis ze in zowel je clientscript als je serverscript.

-

Indien nodig voor je spel, herhaal hetzelfde patroon in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  met een enkel clientscript en een minimaal aantal [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  om een laadscherm te implementeren. Om meer te leren over ReplicatedFirst , zie [Replicatievolgorde](/docs/nl-nl/scripting/attributes#replicatievolgorde) .

-

Gebruik [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  spaarzaam. Als je ze moet gebruiken, plaats ze dan in StarterCharacterScripts , StarterPlayerScripts , StarterGui  of StarterPack .

Scripts in deze containers worden gekloond naar spelerscontainers in plaats van dat ze vanuit één locatie draaien, wat het debuggen kan compliceren. Het gebruik van ReplicatedStorage  voor clientcode stelt je in staat om regels in het Output  venster aan te klikken en naar ReplicatedStorage.YourScript  (de stabiele locatie van het script) te gaan in plaats van Players.YourName.PlayerScripts.YourLocalScript  (de vluchtige locatie waar het script tijdens runtime naartoe is gekopieerd).

-

Vermijd het direct aanhechten van scripts aan instanties in [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Tag in plaats daarvan [instanties](/docs/nl-nl/studio/properties#instantie-tags)  en gebruik [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  om met hen te werken vanuit een enkele [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) .

De belangrijkste uitzondering is als je modellen of pakketten op de Creator Store distribueert. In dat geval moet je mogelijk scripts binnen de instantiehiërarchie opnemen; specificeer een RunContext  voor elk script om ambiguïteit over hoe het draait te verwijderen. Het expliciet instellen van deze eigenschap maakt modellen en pakketten waarschijnlijker om goed te functioneren vanuit verschillende locaties.

### [Voorbeeld projectstructuur](#voorbeeld-projectstructuur)[](#voorbeeld-projectstructuur)

Het [Plant](/docs/nl-nl/resources/plant-reference-project)  referentieproject toont hoe je je code in een groot, complex spel kunt organiseren. Het slaat het grootste deel van zijn code op als herbruikbare [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) .

## [Scriptlocaties](#scriptlocaties)[](#scriptlocaties)

| Location | | Description |
| --- | --- |
| [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) | | Vertegenwoordigt de 3D-wereld van het spel. Kan serverscripts uitvoeren die direct aan objecten zijn gekoppeld en hun gedrag controleren. |
| [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) | | Bevat objecten die als eerste naar de client worden gerepliceerd. Deze locatie is ideaal voor de absoluut minimale set objecten en clientscripts die nodig zijn om een laadscherm weer te geven. |
| [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) | | Bevat objecten die naar zowel de client als de server worden gerepliceerd. Deze locatie is ideaal voor [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  van [Client](/docs/nl-nl/reference/engine/enums/RunContext) , client [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) , en [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  die je op zowel de server als de client wilt gebruiken. [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  worden niet vanuit deze locatie uitgevoerd. |
| [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) | | Bevat serverscripts. Deze locatie is ideaal voor scripts die toegang nodig hebben tot server-side functionaliteit of objecten, zoals spel-logica en cloudopslag. |
| [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) | | Bevat server-side objecten. Deze locatie is ideaal voor grote objecten die niet onmiddellijk naar clients hoeven te worden gerepliceerd wanneer ze een spel joinen. Scripts worden niet vanuit deze locatie uitgevoerd, maar je kunt hier server-side [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  opslaan. |
| [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  ⟩ [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) | | Bevat [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  die worden uitgevoerd wanneer het personage spawnt. |
| [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  ⟩ [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) | | Bevat [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  die worden uitgevoerd wanneer de speler het spel joinet. |
| [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) | | Bevat GUI-elementen die de client weergeeft wanneer het spel wordt geladen. [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  kunnen vanuit deze locatie worden uitgevoerd. |
| [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack) | | Bevat over het algemeen alleen [Tools](/docs/nl-nl/reference/engine/classes/Tool) , maar kan ook [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  bevatten voor het instellen van spelersrugzakken. |

Deze afbeelding toont welke locaties in het Explorer  venster client scripts kunnen bevatten. Vergeet niet dat ReplicatedFirst  en ReplicatedStorage  [Scripts](/docs/nl-nl/reference/engine/classes/Script)  kunnen bevatten met een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  van [Client](/docs/nl-nl/reference/engine/enums/RunContext) , terwijl de Starter[]  containers [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  zouden moeten gebruiken.

 ![Diagram dat toont welke scriptlocaties op clients draaien.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Client-Script-Containers.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
