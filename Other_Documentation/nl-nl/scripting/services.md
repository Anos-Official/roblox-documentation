<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/services -->

Diensten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)

# Diensten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In [Herbruik code](/docs/nl-nl/scripting/module)  heb je misschien de frequente toepassing van de game:GetService() -methode opgemerkt. Roblox-diensten stellen je in staat om toegang te krijgen tot de ingebouwde functies van de engine, zoals het verkopen van in-game items, het inschakelen van chat, het afspelen van geluiden, het animeren van objecten en het beheren van instanties.

In feite zijn diensten de eerste stap in het meest fundamentele, veelvoorkomende patroon van Roblox-ontwikkeling :

1.

Verkrijg diensten.

2.

Vereis modulescripts.

3.

Voeg lokale functies toe.

4.

Voeg de [evenementen](/docs/nl-nl/scripting/events)  toe die die functies activeren.

Bijvoorbeeld, je wilt misschien de posities van spelers in de wereld opslaan wanneer ze je spel verlaten:

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local SaveManager = require(ReplicatedStorage:WaitForChild("SaveManager"))

-- Lokale functie die een herbruikbare functie in het modulescript aanroept.

local function saveProgress(character)

	-- Verkrijg de positie van het karakter van de speler.

	local position = character:FindFirstChild("HumanoidRootPart").Position

	-- Gebruik de saveData-functie in het modulescript, die schrijft naar de

	-- DataStoreService.

	SaveManager.saveData(character, position)

end

-- Een andere lokale functie die saveProgress() aanroept wanneer een karakter wordt verwijderd

-- uit het spel (in dit geval, wanneer de speler vertrekt).

local function onPlayerAdded(player)

	player.CharacterRemoving:Connect(saveProgress)

end

-- Roept onPlayerAdded aan wanneer een speler voor het eerst verbinding maakt met het spel.

Players.PlayerAdded:Connect(onPlayerAdded)

```

Enkele belangrijke details zijn:

-

Omdat je een dienst slechts één keer per script moet ophalen, is de conventie om de variabele dezelfde naam te geven als de dienst. Deze conventie geldt ook voor modulescripts.

-

Je haalt diensten op met de globale variabele [game](/docs/nl-nl/reference/engine/classes/DataModel) , een verwijzing naar de wortel van het datamodel.

-

Roblox geeft geen garanties over de laadvolgorde (en [instanties streaming](/docs/nl-nl/workspace/streaming)  compliceren verder wat wel en niet op elk gegeven moment is geladen), dus het gebruik van [Instance:WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  is een belangrijke veiligheidsmaatregel.

In plaats van [standaardbibliotheken](/docs/nl-nl/reference/engine/libraries) , [globale functies en variabelen](/docs/nl-nl/reference/engine/globals) , of derde-partij bibliotheken te vergelijken, is een groot deel van de Roblox-ontwikkeling het identificeren van welke van de vele, vele diensten je kunnen helpen om de gewenste functionaliteit aan je spellen toe te voegen. In het bovenstaande voorbeeld, in plaats van een standaard I/O-bibliotheek te gebruiken om naar schijf te schrijven, gebruik je [cloudservices](#cloud-diensten)  om gegevens op te slaan.

## [Container diensten](#container-diensten)[](#container-diensten)

Container diensten kunnen andere objecten bevatten en beïnvloeden. Deze container diensten bevinden zich aan de wortel van het datamodel en zijn zichtbaar in het Explorer-venster van Studio. Gezamenlijk vormen deze container diensten een gestructureerde hiërarchie voor het datamodel, zodat de Roblox Engine je plaats correct kan interpreteren en weergeven. De volgende tabel bevat enkele veelvoorkomende container diensten.

| Dienst | | Beschrijving |
| --- | --- |
| [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) | | Bevat alle objecten die in de 3D-wereld worden weergegeven, zoals onderdelen en terrein. |
| [Lighting](/docs/nl-nl/reference/engine/classes/Lighting) | | Bevat objecten voor het instellen van universele lichteffecten, zoals [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  en [Sky](/docs/nl-nl/reference/engine/classes/Sky) . |
| [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  en [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) | | Bevatten inhoud en logica die repliceren tussen de server en de client. |

Om het datamodel verder te onderzoeken, kun je deze methoden gebruiken:

-

[game:FindService()](/docs/nl-nl/reference/engine/classes/DataModel#FindService)  zoekt naar de instantie van de opgegeven dienst.

-

[game:GetChildren()](/docs/nl-nl/reference/engine/classes/DataModel#GetChildren)  retourneert een array van alle rootkinderen van het datamodel, wat de top-level container diensten zijn.

-

[game:GetDescendants()](/docs/nl-nl/reference/engine/classes/DataModel#GetDescendants)  retourneert een array van alle afstammelingen van het datamodel, inclusief alle container diensten en hun kinderen.

Voor meer informatie over container diensten, zie de [data model](/docs/nl-nl/projects/data-model#object-organization)  documentatie.

## [Scripting diensten](#scripting-diensten)[](#scripting-diensten)

Scripting diensten bieden standaardfunctionaliteit in de Roblox Engine die je aanroept binnen scripts. De volgende tabel bevat enkele veelvoorkomende scripting diensten.

| Dienst | | Beschrijving |
| [TweenService](/docs/nl-nl/reference/engine/classes/TweenService) | | Wordt gebruikt om numerieke eigenschappen van andere instanties van een start- naar eindwaarde te interpoleren, met opties voor versnellingsrichting en stijl, herhaling en vertraging. |
| [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService) | | De dienst die verantwoordelijk is voor in-game transacties, zoals het vragen aan de speler om een ontwikkelaarsproduct, abonnement, pas, Roblox Premium, enz. aan te schaffen. |
| [RunService](/docs/nl-nl/reference/engine/classes/RunService) | | Bevat methoden en evenementen voor frame-voor-frame tijdbeheer, evenals voor het controleren van de context (server, client, Studio-modus) waarin het spel draait. Nuttig voor het uitvoeren van elk proces of update op elk runtime-frame. |
| [SoundService](/docs/nl-nl/reference/engine/classes/SoundService) | | Beheert verschillende globale aspecten van hoe audio in een spel wordt afgespeeld, zoals de doppler-schaal en volumetrische audio. Kan ook geluidsgroepen bevatten om het volume en de dynamische effecteigenschappen van meerdere audiosignalen tegelijk te regelen. |
| [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) | | Beheert groepen (collecties) van instanties met tags die repliceren van de server naar de client, waardoor je gemakkelijker groepen van gerelateerde instanties kunt toewijzen en ermee kunt werken. |

## [Cloud diensten](#cloud-diensten)[](#cloud-diensten)

Roblox heeft ook speciale cloud diensten voor het afhandelen van taken en processen die plaatsvinden in de Roblox-cloud. De volgende tabel bevat enkele veelvoorkomende cloud diensten.

| Dienst | | Beschrijving |
| [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) | | Voor het opslaan van persistente gegevens over sessies heen. |
| [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService) | | Voor het opslaan van frequente en vluchtige gegevens die snel veranderen. |
| [MessagingService](/docs/nl-nl/reference/engine/classes/MessagingService) | | Voor communicatie tussen meerdere servers tijdens live sessies. |

Cloud diensten hebben ook bijbehorende web-API's; ze zijn toegankelijk vanuit externe scripts of tools. Voor meer informatie, zie [Open Cloud](/docs/nl-nl/cloud/guides) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
