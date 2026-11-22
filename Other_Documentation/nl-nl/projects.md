<!-- Source: https://create.roblox.com/docs/nl-nl/projects -->

Projecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)

# Projecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een Roblox-project is een verzameling van [plaatsen](#plaatsen) , [assets](#assets) , [instellingen](#instellingen)  en andere bronnen die samen een game  vertegenwoordigen. Roblox slaat je projecten op in de cloud voor gemakkelijke samenwerking, bewerking en versiebeheer. Je maakt en beheert projecten met [Roblox Studio](/docs/nl-nl/studio) , een alles-in-één IDE die bouw-, script-, test- en publicatietools biedt.

## [Plaatsen](#plaatsen)[](#plaatsen)

Games op Roblox bestaan uit individuele plaatsen , vergelijkbaar met scènes in Unity of kaarten in Unreal Engine. Elke plaats bevat alle componenten voor dat deel van de game, inclusief de specifieke omgeving, onderdelen, meshes, scripts en gebruikersinterface.

Zie de pagina's voor [het maken en publiceren](/docs/nl-nl/production/publishing/publish-games-and-places) , [configureren](/docs/nl-nl/projects/configure-games)  en [bijwerken](/docs/nl-nl/projects/update-games)  van games en plaatsen voor details.

![Een game-groepering van drie individuele plaatsen met unieke omgevingen.](https://prod.docsiteassets.roblox.com/assets/publishing/experiences-places-assets/Experience-Hierarchy.png)

Elke plaats wordt vertegenwoordigd door een datamodel , een hiërarchie van objecten die alles over de plaats beschrijft. De Roblox Engine gebruikt het datamodel als de bron van waarheid voor de status van een plaats, zodat het deze kan simuleren en renderen op clientapparaten. Voor meer informatie over hoe de engine het datamodel interpreteert, zie [Client-server runtime](/docs/nl-nl/projects/client-server) .

Juiste, opzettelijke objectorganisatie binnen het datamodel is essentieel voor de functionaliteit en het onderhoud van je project. Voor meer informatie over welke objecten beschikbaar zijn en hoe je ze kunt organiseren en gebruiken, zie [Datamodel](/docs/nl-nl/projects/data-model) .

## [Assets](#assets)[](#assets)

In Roblox worden assets zoals afbeeldingen, meshes en audio opgeslagen als cloud-gebaseerde assets , zodat je geen lokale kopieën in een opgeslagen Studio-game hoeft te bundelen. Elk asset in de cloud krijgt een unieke asset ID  toegewezen waarvan meerdere games gebruik kunnen maken. Je kunt assets rechtstreeks in Studio maken, zoals modellen, of assets zoals afbeeldingen, audio en meshes uit andere tools importeren.

rbxassetid://7229442422

![Een decal asset van een jonge vrouw met een knop voor een oog.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Example-Grafitti04.png)

rbxassetid://6768917255

![Een ongetextureerde schatkist MeshPart asset.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Base-Mesh-In-Marketplace.png)

rbxassetid://9125402735

Standaard zijn assets privé voor je game en kun je een asset in elke plaats gebruiken door naar zijn ID te verwijzen. Je kunt ze ook verspreiden naar de community in de [Creator Store](https://create.roblox.com/store/) , zodat anderen ze ook kunnen gebruiken.

Voor meer informatie over hoe je assets kunt importeren en publiceren, zie [Assets](/docs/nl-nl/projects/assets) .

## [Pakketten](#pakketten)[](#pakketten)

[Pakketten](/docs/nl-nl/projects/assets/packages)  zijn herbruikbare objecthiërarchieën die je kunt definiëren en hergebruiken in meerdere plaatsen in meerdere games. Voor elk groot project bieden pakketten de volgende voordelen:

-

Pakketten kunnen worden gebruikt als assetkits, waardoor je een set objecten naar behoefte kunt dupliceren.

-

Pakketten maken het gemakkelijker om assets bij te werken. Bijvoorbeeld, een pakket kan een boom bevatten die meerdere keren in een omgeving is gedupliceerd. Als je een wijziging moet aanbrengen, zoals het verwisselen van texturen voor de boom, kan dit eenmaal in het pakket worden bijgewerkt in plaats van voor elke individuele instantie.

-

Een pakket kan beginnen met graybox-assets en uiteindelijk worden vervangen door definitieve kunst-assets. Wanneer assets worden vervangen, behouden ze alle oorspronkelijke posities en oriëntaties.

## [Instellingen](#instellingen)[](#instellingen)

Game-instellingen worden beheerd vanuit het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  of binnen Studio, inclusief:

-

Basisinformatie  — Basisinformatie over de game, zoals de naam, beschrijving en genre. Veel van de informatie hier wordt gebruikt in de vermelding van je game.

-

Communicatie  — Instellingen die het mogelijk maken voor in aanmerking komende gebruikers om [stemchat](/docs/nl-nl/chat/voice-chat)  te gebruiken of hun avatar te animeren via hun camera binnen jouw game.

-

Toestemmingen  — Configureert wie toegang heeft tot je game. Wanneer games voor het eerst worden gepubliceerd, zijn ze alleen toegankelijk voor jou als maker, gebruikers met Bewerken  of Playtest  toegang, en groepsleden met de juiste [rollen en toestemmingen](/docs/nl-nl/projects/groups#rollen-en-machtigingen) . Wanneer je er klaar voor bent, kun je de game [uitbrengen](/docs/nl-nl/production/publishing/publish-games-and-places#vrijgeven-van-games)  voor een breder publiek.

-

Monetisatie  — Opties voor het verdienen van inkomsten uit je game, zoals uiteengezet in [Monetisatie](/docs/nl-nl/production/monetization) .

-

Lokalisatie  — Configuratie voor verschillende [talen en regio's](/docs/nl-nl/production/localization) .

-

Avatar  — Instellingen met betrekking tot avatars, zoals avatar-schaal en kledingoverrides.

## [Samenwerking](#samenwerking)[](#samenwerking)

Met de ingebouwde samenwerkingshulpmiddelen  van Studio kunnen teamleden onafhankelijk bijdragen aan games op hun eigen tijd, of samen met anderen. Belangrijke functies zijn onder andere:

-

Groepsbeheerders kunnen beheren welke leden toegang hebben om samen te werken en welke niet, waardoor ze effectief de juiste rollen binnen een groot team behouden.

-

Samenwerkers kunnen in realtime naast andere teamleden bouwen en automatisch wijzigingen zien die door anderen zijn aangebracht.

-

Samenwerkers kunnen onafhankelijk dezelfde scripts bewerken die anderen mogelijk aan het bewerken zijn, lokaal testen en hun wijzigingen naar het cloud-gebaseerde project verzenden wanneer ze er klaar voor zijn.

Voor meer informatie, zie [Samenwerking](/docs/nl-nl/projects/collaboration) .

## [Testen](#testen)[](#testen)

Je [team](/docs/nl-nl/projects/groups)  kan onmiddellijk een game testen op pc, mobiel, VR en andere apparaten die je wilt ondersteunen via de Roblox-app; er is geen noodzaak om builds te compileren, naar app-winkels te implementeren of te wachten op goedkeuring van de app-winkel.

Studio biedt een reeks opties voor het testen van een game voordat deze aan het publiek wordt vrijgegeven:

-

Snelle playtesting  die een nauwkeurige simulatie van de game biedt die draait op de Roblox-applicatie.

-

Multi-client simulatie  voor het vergelijken van hoe elke client "andere" clients binnen de game "ziet".

-

Apparaatemulatie  die inzicht biedt in hoe de bedieningselementen werken op een mobiel apparaat of hoe de on-screen UI wordt weergegeven op verschillende schermen en beeldverhoudingen.

-

Samenwerkende playtesting  met leden van je team.

Voor meer informatie over elke testoptie, zie [Studio testmodi](/docs/nl-nl/studio/testing-modes) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
