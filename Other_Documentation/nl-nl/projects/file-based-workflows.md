<!-- Source: https://create.roblox.com/docs/nl-nl/projects/file-based-workflows -->

Vergelijk bestand-gebaseerde workflows | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Op bestanden gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows)

# Vergelijk bestand-gebaseerde workflows

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox-spellen leven standaard in de cloud. Studio slaat je plaatsen, assets en scripts op in Roblox, en [Versiegeschiedenis](/docs/nl-nl/projects/version-history)  houdt wijzigingen bij voor elke plaats. Veel teams willen ook hun spel in een versiebeheersysteem  zoals [Git](https://git-scm.com/)  zodat ze wijzigingen kunnen bekijken voordat ze worden doorgevoerd, een volledige geschiedenis kunnen bijhouden en builds en deploys kunnen automatiseren.

Elke versiebeheersworkflow voor Roblox beantwoordt één vraag: waar bevindt de bron van waarheid  zich voor elk onderdeel van je spel? De drie gebruikelijke antwoorden zijn:

-

Studio-native:  De plaats op Roblox is de bron van waarheid voor alles. Script Sync kopieert scripts naar Git zodat je ze kunt bekijken en bijhouden.

-

Deels beheerd:  Git is de bron van waarheid voor code. De plaats op Roblox is de bron van waarheid voor alles wat betreft modellen, terrein en UI.

-

Volledig beheerd:  Git is de bron van waarheid voor het hele spel. Plaatsen op Roblox zijn build-output die CI publiceert vanuit de repository.

Deze pagina vergelijkt deze workflows, beschrijft de tools die elk gebruikt en behandelt de omgevingen die teams eromheen opzetten. Om een workflow in te stellen, zie [Stel een workflow in](#stel-een-workflow-in) .

Derden-tools op deze pagina worden niet onderhouden door Roblox en kunnen op elk moment veranderen of stoppen met werken. Voor volledige referentie, zie de documentatie van elke tool.

## [Roadmap voor bestand-gebaseerde workflows](#roadmap-voor-bestand-gebaseerde-workflows)[](#roadmap-voor-bestand-gebaseerde-workflows)

Roblox werkt aan first-party, bestand-gebaseerde workflows zodat teams versiebeheer kunnen gebruiken zonder dat ze derde-partijtools hoeven samen te stellen. Totdat deze workflows worden uitgebracht, weerspiegelen de setups op deze pagina wat vandaag de dag voor teams werkt.

## [Workflow vergelijking](#workflow-vergelijking)[](#workflow-vergelijking)

#### Studio-native

#### Deels beheerd

#### Volledig beheerd

|  | | Studio-native | | Deels beheerd | | Volledig beheerd |
| --- | --- |
| ** Goed geschikt voor** | | Teams van minder dan vijf makers die aan een enkel-plaats spel werken | | Teams met meerdere programmeurs en multi-plaats spellen | | Teams die beoordeling en geschiedenis vereisen voor elke instantie en asset |
| ** In versiebeheer** | | Scripts | | Scripts, projectconfiguratie en tooling | | Alles, inclusief modellen en afbeeldingen |
| ** Contentbewerking** | | Team Create | | Team Create en pakketten | | Bestanden in Git, gebouwd door CI |
| ** Tools om te onderhouden** | | Geen behalve Studio en een editor | | Rojo plus linting en CI-tools | | Rojo, merge- en asset-tools, en een volledige CI-pijplijn |

### [Kies een workflow](#kies-een-workflow)[](#kies-een-workflow)

Begin met de eenvoudigste workflow die aan je behoeften voldoet. Je kunt later naar een meer beheerde workflow overstappen, omdat geen van deze tools je vastlegt. De meeste teams hebben geen volledig beheerd Rojo nodig, en het voegt aanzienlijke complexiteit toe.

## [Tools](#tools)[](#tools)

De meeste setups combineren een paar tools van Roblox met een paar van de community.

### [Roblox-tools](#roblox-tools)[](#roblox-tools)

| Tool | | Wat het doet | | Gebruikt in |
| [Team Create](/docs/nl-nl/projects/collaboration) | | Realtime collaboratieve bewerking in Studio, het beste geschikt voor bouwen, levelontwerp en kunst. | | Alle workflows |
| [Script Sync](/docs/nl-nl/scripting/sync) | | Synchroniseert scripts in Studio met bestanden op je lokale schijf, in beide richtingen. | | Studio-native |
| [Pakketten](/docs/nl-nl/projects/assets/packages) | | Herbruikbare, versiegebonden groepen van instanties die je kunt bijwerken over plaatsen en spellen. | | Studio-native, deels beheerd |
| [Versiegeschiedenis](/docs/nl-nl/projects/version-history) | | Opgeslagen versies van elke plaats die je kunt bekijken, vergelijken en herstellen. | | Alle workflows |
| [Plaats publicatie API](/docs/nl-nl/cloud/guides/usage-place-publishing) | | Open Cloud API die een plaatsbestand naar Roblox publiceert. Gebruik het om te deployen vanuit CI. | | Deels beheerd, volledig beheerd |
| [Luau-executie API](/docs/nl-nl/cloud/reference/LuauExecutionSessionTask) | | Open Cloud API die Luau uitvoert in een plaats op Roblox-servers. Gebruik het om tests vanuit CI uit te voeren. | | Deels beheerd, volledig beheerd |
| [Assets API](/docs/nl-nl/cloud/guides/usage-assets) | | Open Cloud API die assets zoals afbeeldingen, audio en modellen uploadt en bijwerkt. | | Volledig beheerd |

### [Community-tools](#community-tools)[](#community-tools)

| Tool | | Wat het doet | | Gebruikt in |
| [Rojo](https://rojo.space/) | | Synchroniseert bestanden op schijf naar Studio via een lokale server en Studio-plugin, en bouwt plaats- en modelbestanden vanuit een projectbestand. De rojo syncback -opdracht, in Rojo 7.7 en later, converteert een bestaande plaats naar projectbestanden. | | Deels beheerd, volledig beheerd |
| [Rokit](https://github.com/rojo-rbx/rokit) | | Toolchain manager. Bevestigt toolversies zodat iedereen in het team dezelfde gebruikt. | | Deels beheerd, volledig beheerd |
| [Wally](https://wally.run/) | | Pakketbeheerder voor community Luau-bibliotheken. | | Deels beheerd, volledig beheerd |
| [Lune](https://github.com/lune-org/lune) | | Standalone Luau-runtime, vaak gebruikt voor build-, deploy- en automatiseringsscripts. | | Deels beheerd, volledig beheerd |
| [selene](https://github.com/Kampfkarren/selene) | | Luau-linter. | | Alle workflows |
| [StyLua](https://github.com/JohnnyMorganz/StyLua) | | Luau-code formatter. | | Alle workflows |
| [Luau Language Server](https://github.com/JohnnyMorganz/luau-lsp) | | Autocompletion en typechecking in externe editors. | | Alle workflows |
| [Tarmac](https://github.com/Roblox/tarmac) | | Uploadt afbeeldingen van schijf naar Roblox en genereert een module die bestandslocaties aan asset-ID's koppelt. | | Volledig beheerd |
| [rbx-merge](https://github.com/kennethloeffler/rbx-merge) | | Git diff en merge-driver voor .rbxl , .rbxlx , .rbxm , en .rbxmx -bestanden. Toont leesbare diffs en voegt niet-conflicterende wijzigingen samen op het niveau van eigenschappen. | | Volledig beheerd |

Om Rojo te installeren en uit te voeren, zie [Rojo](/docs/nl-nl/projects/rojo) . Voor Rokit, Wally, linters en andere tools, zie [Derden-tools](/docs/nl-nl/projects/external-tools) .

## [Omgevingen](#omgevingen)[](#omgevingen)

Teams die versiebeheer gebruiken, scheiden meestal ook hun werk in omgevingen , zodat onafgemaakte wijzigingen nooit bij spelers komen. In plaats van één plaats die iedereen bewerkt, is elke omgeving zijn eigen plaats.

We raden aan om elke omgeving als een aparte game  onder dezelfde [groep](/docs/nl-nl/projects/groups)  te creëren, in plaats van als aparte plaatsen binnen één game. Databases, geheimen en andere cloudservices zijn beperkt tot de game, dus aparte games houden testgegevens uit de productie.

Een typische setup heeft deze omgevingen:

| Omgeving | | Doel | | Wie werkt het bij |
| ** Persoonlijke dev** | | Elke maker's eigen kopie van de dev-plaats voor dagelijkse werkzaamheden. | | Die maker |
| ** Gedeelde dev** | | De gecombineerde, onstabiele set van functies waar het team aan werkt. | | Programmeurs synchroniseren beoordeelde code, en kunstenaars kopiëren goedgekeurde content. |
| ** Assets** | | De canonieke versies van pakketten, zoals personages, bouwkits en set dressing. | | Kunstenaars |
| ** Stabiel** | | Een momentopname van gedeelde dev op een regelmatig interval, zoals voor wekelijkse playtests. | | CI alleen |
| ** Productie** | | Het live, openbare spel. | | Gekopieerd van stabiel na goedkeuring van de release |

### [Maak een persoonlijke dev-plaats](#maak-een-persoonlijke-dev-plaats)[](#maak-een-persoonlijke-dev-plaats)

1.

Open de gedeelde dev-plaats in Studio.

2.

Selecteer Bestand  ⟩ Publiceren als .

3.

Selecteer de groep die jouw dev-games bezit.

4.

Publiceer de plaats als een nieuw spel met een naam die jou en het project identificeert, zoals USER / JouwNaam - ProjectNaam .

5.

Sluit de gedeelde dev-plaats en open je nieuwe persoonlijke kopie.

Gebruik consistente namen voor elke omgeving, zoals DEV - ProjectNaam , ASSET / ProjectNaam , en STABLE / ProjectNaam , zodat het team ze kan onderscheiden op het Creator Dashboard .

## [Stel een workflow in](#stel-een-workflow-in)[](#stel-een-workflow-in)

| Workflow | | Setup-gids |
| Studio-native | | [Gebruik Script Sync met een team](/docs/nl-nl/scripting/sync#use-script-sync-with-a-team) |
| Deels beheerd | | [Deels beheerd Rojo](/docs/nl-nl/projects/rojo/partially-managed) |
| Volledig beheerd | | [Volledig beheerd Rojo](/docs/nl-nl/projects/rojo/fully-managed) |

## [Probleemoplossing voor veelvoorkomende problemen](#probleemoplossing-voor-veelvoorkomende-problemen)[](#probleemoplossing-voor-veelvoorkomende-problemen)

| Probleem | | Oplossing |
| Testen in een dev-plaats verandert productiedata. | | Dev en productie zijn plaatsen in dezelfde game, dus ze delen databasens. Verplaats elke omgeving naar zijn eigen game. |
| Teamgenoten overschrijven elkaars scriptwijzigingen. | | Twee mensen synchroniseren dezelfde scripts in één Team Create-sessie. Synchroniseer code naar persoonlijke dev-plaatsen en merge via Git. |
| Een fix voor één kopie van een script wordt niet toegepast op de anderen. | | Het kopiëren van een script creëert een onafhankelijke kopie. Plaats gedeeld gedrag in een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  en koppel het aan instanties met [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) -tags. |
| Server-only code is zichtbaar voor clients. | | Modules in containers die repliceren naar clients, zoals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , worden naar clients verzonden. Houd server-only modules in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  of [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) . |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
