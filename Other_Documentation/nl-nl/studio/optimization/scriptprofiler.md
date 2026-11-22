<!-- Source: https://create.roblox.com/docs/nl-nl/studio/optimization/scriptprofiler -->

Script Profiler | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Ontwikkelaarsforum](/docs/nl-nl/studio/developer-console)

# Script Profiler

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Script Profiler  is een tool binnen de [Developer Console](/docs/nl-nl/studio/developer-console)  waarmee je profileringssessies van alle draaiende scripts kunt registreren en hun CPU-tijdkosten kunt bekijken met aangepaste opname- en weergave-instellingen. Het kan alle soorten functieaanroepen registreren, inclusief Luau-functies, methode-aanroepen en eigenschaps-toegangen. Deze tool is nuttig voor het identificeren van scripts die de meeste CPU-bronnen verbruiken en de prestaties vertragen.

Script Profiler registreert alleen functieaanroepen die CPU-bronnen verbruiken, dus het registreert geen threads die slapen of wachten op resultaten.

## [Registreer profileringssessies](#registreer-profileringssessies)[](#registreer-profileringssessies)

Voordat je begint met registreren, moet je de opnameomgeving selecteren uit:

-

Client  (Standaard) — Registreert client-side scripts, inclusief [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  en [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) .

-

Server  — Registreert server-side scripts, inclusief [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Server](/docs/nl-nl/reference/engine/enums/RunContext#Server)  of [Legacy](/docs/nl-nl/reference/engine/enums/RunContext#Legacy) . Script Profiler wist alle verzamelde server-side gegevens aan het einde van elke sessie.

Je kunt ook de volgende opname-opties instellen:

| Gedrag | | Opties | | Standaard | | Beschrijving |
| --- | --- |
| Frequentie | | 1000 keer per seconde (1 KHz)
10.000 keer per seconde (10 KHz) | | 1 KHz | | De 10 KHz frequentie heeft een hogere precisie, omdat Script Profiler mogelijk geen API-aanroepen oppikt die vaker worden uitgevoerd dan de geselecteerde frequentie, maar het heeft ook een hogere prestatiekost. |
| Sessieduur | | 1 minuut
5 minuten
10 minuten
Handmatig | | Handmatig | | De handmatige optie vereist dat je handmatig stopt met opnemen. |
| Live Polling Gedrag | | Aan
Uit | | Uit | | Dit gedrag pollt en ververst profileringsgegevens elke seconde tijdens een profileringssessie. |

Om een nieuwe profileringssessie te registreren:

1.

Open de [Developer Console](/docs/nl-nl/studio/developer-console#opening-the-developer-console) .

2.

Vouw het gereedschappen dropdownmenu uit om ScriptProfiler  te selecteren.

 ![Dropdownmenu van alle Developer Console-tools met de ScriptProfiler-optie gemarkeerd voor selectie.](https://prod.docsiteassets.roblox.com/assets/studio/console/ScriptProfiler-Open.png)

3.

Vouw het client-server dropdownmenu uit om Client  of Server  te selecteren.

 ![Dropdownmenu met Client- en Server-opties voor selectie.](https://prod.docsiteassets.roblox.com/assets/studio/console/Client-Server-Dropdown.png)

4.

OPTIONEEL

 Vink het Live  vakje aan om het live polling gedrag in te schakelen.

5.

OPTIONEEL

 Selecteer Freq  en Tijd  om de opnamefrequentie en de duur van de sessie te kiezen als je de standaardwaarden niet wilt gebruiken.

6.

Klik op Start  om de profileringssessie te beginnen. Als je een duur hebt ingesteld, toont Script Profiler een countdown timer met de resterende tijd in de sessie.

7.

Klik op Stop  of wacht tot de opname is voltooid om de profileringsgegevens weer te geven.

## [Lees profileringsgegevens](#lees-profileringsgegevens)[](#lees-profileringsgegevens)

Nadat een sessie stopt, genereert Script Profiler een tabel die laat zien hoeveel tijd elke functieaanroep kost in CPU-tijd. De tabel sorteert functieaanroepen van de meeste tijd besteed naar de minste tijd besteed, en stelt je in staat om naar specifieke functies te zoeken op naam. Het biedt de volgende twee weergaven:

-

Callgraph  (Standaard): Categoriseert en toont functieaanroepen in een boomstructuur op basis van frame-taken. Deze weergave toont elke taakcategorie als knooppunten onder dezelfde root en stelt je in staat om ze uit te vouwen om functies te bekijken. Je kunt ook met de muis over elk knooppunt in de boom bewegen om bestand- en regelinformatie te bekijken. Bijvoorbeeld, Stepped/CameraInput/<anonymous>  kan onthullen Players.[LocalPlayer].PlayerScripts.PlayerModule.CameraModule.CameraInput:125 .  ![Voorbeeld callgraph-weergave van een profileringssessie.](https://prod.docsiteassets.roblox.com/assets/studio/console/Callgraph.jpeg)

-

Functies : Lijst alle functies op zonder ze te categoriseren op taken.  ![Voorbeeld functies-weergave van een profileringssessie.](https://prod.docsiteassets.roblox.com/assets/studio/console/Functions.jpeg)

Je kunt ook kiezen uit de volgende weergave-opties om je debugbehoeften aan te passen:

| Naam | | Opties | | Standaard | | Beschrijving |
| Eenheid | | Milliseconden (ms)
Percentage (%) | | ms | | Toont de tijd die aan elke API-aanroep is besteed in milliseconden of percentages van de totale opname-sessie. |
| Gemiddelde | | Uit
1 seconde
1 minuut
5 minuten
10 minuten | | Uit | | Berechnet de gemiddelde tijd die aan elke API-aanroep is besteed op basis van de geselecteerde waarde. Als je een optie selecteert die langer is dan de sessieduur, extrapoleert Script Profiler de sessieduur om het gemiddelde te berekenen. Bijvoorbeeld, je kunt de 5 minuten optie selecteren voor een sessie van 1 minuut om de verwachte gemiddelde waarde te zien als je de code 5 minuten uitvoert. |

## [Exporteer profileringsgegevens](#exporteer-profileringsgegevens)[](#exporteer-profileringsgegevens)

Script Profiler stelt je in staat om geregistreerde profileringsgegevens te exporteren als een JSON-bestand. Om geregistreerde gegevens na een profileringssessie te exporteren:

1.

Klik op het Script Profiler-venster op Export .

2.

Selecteer in het exportvenster de profileringssessie die je wilt exporteren. Hernoem de standaard bestandsnaam als je een aangepaste naam wilt instellen.

3.

Klik op Export  om het JSON-bestand op te slaan.

 ![Voorbeeld exportvenster.](https://prod.docsiteassets.roblox.com/assets/studio/console/Export-Window.jpeg)

Het geëxporteerde JSON-bestand bevat de volgende velden:

-

Versie : Het versienummer.

-

SessionStartTime : Een tijdstempel in milliseconden die de starttijd van de sessie registreert.

-

SessionEndTime : Een tijdstempel in milliseconden die de eindtijd van de sessie registreert.

-

Categorieën : Een array van frame-taakcategorieën die zijn geregistreerd in de profileringssessie. Elke invoer bevat:

-

Naam : De naam van elke frame-taakcategorie.

-

NodeId : De unieke identificatie van een taakcategorie (knooppunt). Het is een 1-gebaseerde index in de Nodes  array. Bijvoorbeeld, je kunt het knooppunt met de NodeId  van 123  opzoeken door het 123e element in Nodes  op te halen.

-

Nodes : Een array van knooppunten die zijn geregistreerd in de profileringssessie. Elke invoer bevat:

-

TotalDuration : De hoeveelheid tijd die het knooppunt kost in CPU-tijd in microseconden.

-

FunctionIds : Een array van unieke identificaties van functies.

-

NodeIds : Een array van Node IDs.

-

Functies : Een array van functies die zijn geregistreerd in de profileringssessie.

-

TotalDuration : De hoeveelheid tijd die de functie kost in CPU-tijd in microseconden.

-

Naam : De naam van de functie, indien beschikbaar.

-

Bron : De bron van de functie, indien beschikbaar.

-

Regel : Het regelnummer van de functie, indien beschikbaar.

-

Vlaggen : Een bitveld dat een specifieke uitvoeringsomgeving van de functie aangeeft. Momenteel kan het de volgende waarden hebben:

-

0 : De 0e bit vertegenwoordigt IsNative  voor uitvoering onder Native CodeGen.

-

1 : De 1e bit vertegenwoordigt IsPlugin  voor uitvoering als onderdeel van een plugin.

Voorbeeld Geëxporteerde Profileringsgegevens

```

{

  "Version":2,

  "SessionStartTime":1704850750514,

  "SessionEndTime":1704850751198,

  "Categories":

  [

    {"Name":"Parallel Luau","NodeId":4},

    {"Name":"Heartbeat","NodeId":1}

  ],

  "Nodes":

  [

      {"TotalDuration":2530,"FunctionIds":[1],"NodeIds":[2]},

      {"TotalDuration":2530,"FunctionIds":[2,5],"NodeIds":[3,7]},

      {"TotalDuration":1267},

      {"TotalDuration":7746,"FunctionIds":[3],"NodeIds":[5]},

      {"TotalDuration":7746,"FunctionIds":[4],"NodeIds":[6]},

      {"TotalDuration":7746},

      {"TotalDuration":1263,"FunctionIds":[6],"NodeIds":[8]},

      {"TotalDuration":1263,"FunctionIds":[7],"NodeIds":[9]},

      {"TotalDuration":1263,"FunctionIds":[8],"NodeIds":[10]},

      {"TotalDuration":1263}

  ],

  "Functions":

  [

    {"Name":"main","TotalDuration":2530},

    {"Source":"builtin_ManageCollaborators.rbxm.ManageCollaborators.Packages._Index.roblox_rodux-3.0.0.rodux.Store","Line":81,"TotalDuration":1267},

    {"Name":"Script","TotalDuration":7746},

    {"Source":"Workspace.Actor.Script","Line":1,"TotalDuration":7746},

    {"Source":"builtin_DeveloperInspector.rbxm.DeveloperInspector.Packages._Index.DeveloperFramework.DeveloperFramework.UI.Components.Grid","Line":221,"TotalDuration":1263},

    {"Source":"builtin_DeveloperInspector.rbxm.DeveloperInspector.Packages._Index.DeveloperFramework.DeveloperFramework.UI.Components.Grid","Name":"_update","Line":236,"TotalDuration":1263},

    {"Source":"builtin_DeveloperInspector.rbxm.DeveloperInspector.Packages._Index.DeveloperFramework.DeveloperFramework.UI.Components.Grid","Name":"_getRange","Line":277,"TotalDuration":1263},

    {"Source":"[C]","Name":"ScrollingFrame.CanvasPosition","TotalDuration":1263}

  ]

}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
