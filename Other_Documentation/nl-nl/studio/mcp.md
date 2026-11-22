<!-- Source: https://create.roblox.com/docs/nl-nl/studio/mcp -->

Verbinden met de Roblox Studio MCP-server | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [MCP-server](/docs/nl-nl/studio/mcp)

# Verbinden met de Roblox Studio MCP-server

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Roblox Studio MCP-server is ingebouwd in Roblox Studio. Het implementeert het [Model Context Protocol (MCP)](https://modelcontextprotocol.io/docs/getting-started/intro) , een open standaard die AI-tools in staat stelt veilig te communiceren met externe applicaties. Zodra je verbonden bent, kan je AI-client direct interactie hebben met je open Studio-sessie, de datamodel verkennen, scripts schrijven, Luau-code uitvoeren en je game testen in speelmodus.

Deze gids laat je zien hoe je de Studio MCP-server kunt verbinden met populaire AI-clients. Hoewel de setup per client verschilt, is het kernidee hetzelfde: je configureert je client om verbinding te maken met de MCP-server en vervolgens stuur je opdrachten van de client naar je actieve Studio-sessie.

Om Open Cloud API's vanuit je MCP-client aan te roepen zonder een API-sleutel, zie [Gebruik Open Cloud met de Studio MCP-server](/docs/nl-nl/studio/mcp-open-cloud) .

## [Vereisten](#vereisten)[](#vereisten)

Voordat je verbinding kunt maken met de server, zorg ervoor dat je de laatste versie van Roblox Studio  en je voorkeurs MCP-client  op je computer hebt geïnstalleerd.

## [Hoe de Studio MCP-server werkt](#hoe-de-studio-mcp-server-werkt)[](#hoe-de-studio-mcp-server-werkt)

De server draait als een lokaal proces op je machine en communiceert met de AI-client via stdio  transport , dat gebruikmaakt van standaard invoer/uitvoer streams. Alle acties worden geïnitieerd via je AI-client, die vervolgens een verzoek via dit kanaal verzendt om acties binnen je Studio-sessie uit te voeren.

De server biedt de volgende tools:

| Scripts | |  |
| --- | --- |
| script_read | | Leest een script uit de game met behulp van dot-notatie paden (bijvoorbeeld, game.ServerScriptService.MyScript ). Ondersteunt het lezen van volledige scripts of specifieke regelbereiken. |
| multi_edit | | Past meerdere bewerkingen toe op een script in één operatie. Als het doelpad niet bestaat, wordt er een nieuw script aangemaakt. Vereist het specificeren van een datamodel_type  (Bewerken). |
| script_search | | Zoekt naar scripts op naam met behulp van fuzzy matching. Geeft maximaal 10 resultaten terug. |
| script_grep | | Zoekt naar een tekenreeks patroon in alle scripts in de game. Geeft maximaal 50 overeenkomsten terug. |
| Asset- en contentgeneratie | |  |
| generate_animation | | Genereert een R15-animatie vanuit een tekstprompt, of converteert een bestaande R6-animatie naar R15 vanuit de asset-ID. Ondersteunt het richten op een specifieke rig en het instellen van een duur van maximaal 10 seconden. |
| generate_mesh | | Genereert een getextureerde 3D-mesh vanuit een tekstprompt met behulp van AI. |
| generate_material | | Genereert een aangepaste materiaalvariant. Geeft het basismateriaal en de naam van de materiaalvariant terug die op onderdelen kan worden toegepast. |
| generate_procedural_model | | Creëert 3D-objecten opgebouwd uit primitieve onderdelen (blokken, bollen, cilinders, wiggen) als een ProceduralModel met configureerbare attributen. Ondersteunt referentieafbeeldingen en aangepaste onderdeel-schema's. |
| wait_job_finished | | Wacht tot een procedurele modelgeneratiejob is voltooid en geeft de uiteindelijke status terug. |
| generate_avatar | | Genereert een nieuwe rigged, animeerbare R15-avatar (lichaam, hoofd en kleding) vanuit een tekstprompt. |
| search_asset | | Zoekt naar assets in de Creator Store (openbare marktplaats) en Creator Inventory (gebruiker, groep of universum). Ondersteunt filteren op assettype, prijs, tags en scope. |
| insert_asset | | Voegt een asset toe aan de game op basis van de numerieke Roblox asset-ID. Ondersteunt modellen, meshes, afbeeldingen, audio, video, animaties en pakketten. |
| upload_image | | Uploadt een batch afbeeldingen van HTTP-URL's naar de Roblox assetserver en geeft een afbeeldingspad naar asset-ID-mapping terug. |
| store_image | | Laadt een afbeelding van een lokaal bestandspad en geeft een afbeeldings-URI terug die aan andere tools kan worden doorgegeven (bijvoorbeeld als een referentieafbeelding voor generate_procedural_model ). |
| Data model verkenning | |  |
| subagent | | Start een gespecialiseerde subagent om complexe, meerstaps taken autonoom af te handelen. Beschikbare types zijn explore  (voor codebase-onderzoek en game-statusvragen) en playtest  (voor het uitvoeren van gameplay-scenario's en het verifiëren van uitkomsten). |
| search_game_tree | | Verken de instantieshiërarchie als een platte JSON-array. Ondersteunt filteren op pad, instantie-type en trefwoorden, met configureerbare dieptebeperkingen. |
| inspect_instance | | Geeft gedetailleerde informatie over een specifieke instantie, inclusief alle leesbare eigenschappen, aangepaste attributen en een samenvatting van zijn kinderen en afstammelingen. |
| Luau uitvoering | |  |
| execute_luau | | Voert Luau-code uit in Studio. Geeft ofwel het resultaat of een fout terug. Vereist het specificeren van een datamodel_type  (Bewerken, Client of Server). |
| Playtesting | |  |
| get_studio_state | | Geeft de huidige staat van Studio terug, inclusief de speelstatus en beschikbare datamodeltypes. |
| start_stop_play | | Start of stopt playtesting. |
| get_console_output | | Haal output op uit het Studio-outputlog. |
| screen_capture | | Vangt het huidige Studio-viewport en geeft de afbeeldingsgegevens terug. Accepteert optioneel een aangepaste camerapositie en kijkdoel. |
| Spelerinvoersimulatie | |  |
| character_navigation | | Verplaatst de speler naar een gegeven positie of instantie-pad. Ondersteunt een configureerbare snelheidsvermenigvuldiger. |
| user_keyboard_input | | Stuurt een of meer toetsenbordinvoeren in volgorde: toets omlaag, toets omhoog, toets indrukken, tekstinvoer of wachten. Ondersteunt het richten op specifieke UI-instanties. |
| user_mouse_input | | Stuurt een of meer muisacties in volgorde: verplaatsen, klikken, knop omlaag/omhoog, scrollen of wachten. Ondersteunt het richten op specifieke instanties of schermcoördinaten. |
| Documentatie en vaardigheden | |  |
| http_get | | Haal inhoud op van toegestane Roblox documentatie-URL's (Engine API-referentie, Creator-docs, Cloud API, prestatieoptimalisatiegidsen). Ondersteunt trefwoordzoekopdrachten binnen de opgehaalde inhoud. |
| skill | | Haal gedetailleerde kennis, best practices of referentiemateriaal op voor specifieke vaardigheden zoals debuggen, apparaatsimulatie en documentatiezoekopdrachten. |
| Plaatsbeheer | |  |
| save_place | | Slaat de open plaats op dezelfde manier op als Bestand  ⟩ Opslaan : als een nieuwe plaatsversie voor plaatsen geopend vanuit Roblox, of terug naar het bestand voor lokale .rbx  en .rbxlx  plaatsen. Opent geen dialoogvensters. |
| Sessiebeheer | |  |
| list_roblox_studios | | Geeft alle verbonden Studio-instanties weer, inclusief hun naam, Studio-instantie-ID en plaats-ID. Lokale plaatsen zonder plaats-ID worden alleen op naam vermeld. Handig wanneer meerdere Studio-vensters open zijn; als twee open Studio-instanties dezelfde naam delen, laat de plaats-ID je ze onderscheiden. |
| Feedback | |  |
| submit_feedback | | Stuurt feedback naar Roblox wanneer een tool faalt, een mogelijkheid ontbreekt, of een workflow in Studio meer stappen vereist dan nodig is, zodat het team Studio en zijn MCP-tools kan verbeteren. |

Elke toolaanroep vereist een studio_id  parameter die de Studio-instantie benoemt waarop deze gericht is, zodat agenten Studio-instanties expliciet adresseren in plaats van te vertrouwen op sessiestatus. Gebruik list_roblox_studios  om de ID van de instantie die je wilt op te zoeken.

Playtestautomatisering werkt over teleportaties. Tijdens een playtest kan een agent een speler naar een andere plaats in dezelfde ervaring teleporteren, de output van de bestemmingsserver lezen en de problemen die het vindt oplossen, allemaal zonder te publiceren. Voor ondersteunde teleportmethoden en testbeperkingen, zie [Test teleportaties in Studio](/docs/nl-nl/projects/teleport#test-teleportaties-in-studio) .

## [Schakel de MCP-server in Studio in](#schakel-de-mcp-server-in-studio-in)[](#schakel-de-mcp-server-in-studio-in)

Om de MCP-server in Studio in te schakelen:

1.

Open Assistant .

2.

Klik op …  ⟩ Beheer MCP-servers .

3.

Zet Studio inschakelen als MCP-server  aan.

Zodra deze is ingeschakeld, toont het instellingenpaneel de snelle verbindingsoptie en installatie-instructies voor verschillende clients. Wanneer een client succesvol verbinding maakt, toont een groene indicator het aantal verbonden clients.

## [Verbind je client](#verbind-je-client)[](#verbind-je-client)

Je kunt je client verbinden met de Studio MCP-server met behulp van snelle verbinding, een JSON-configuratie of een CLI-opdracht.

-

Gebruik snelle verbinding  als je client wordt ondersteund.

-

Zo niet, gebruik dan een JSON-configuratie  als je client MCP-configuratiebestanden ondersteunt.

-

Anders, gebruik een CLI-opdracht .

De Studio MCP-server werkt met elke client die stdio  transport ondersteunt. Nadat je de configuratie hebt toegevoegd, volg je de documentatie van je client om de installatie te voltooien, en herstart je de client om je wijzigingen toe te passen.

MCP-clients kunnen inhoud lezen en wijzigen in je open Roblox-plaatsen. Zorg ervoor dat je alleen clients verbindt die je vertrouwt.

### [Snelle verbinding](#snelle-verbinding)[](#snelle-verbinding)

Snelle verbinding ondersteunt de volgende clients:

-

Antigravity

-

Codex CLI

-

Claude Code

-

Claude Desktop

-

Cursor

-

Gemini CLI

-

Visual Studio Code

Om verbinding te maken met behulp van snelle verbinding:

1.

Ga naar Assistant-instellingen  ⟩ MCP-servers .

2.

Vouw de Snelle verbinding  dropdown uit om ondersteunde clients te bekijken die op je computer zijn geïnstalleerd.

3.

Zet je gekozen client aan.

Als de client die je wilt niet verschijnt in de lijst Snelle verbinding , installeer deze dan en herstart Roblox Studio.

### [JSON-configuratie](#json-configuratie)[](#json-configuratie)

De meeste MCP-clients ondersteunen JSON-configuratiebestanden. De volgende voorbeelden tonen complete configuraties die je kunt gebruiken.

Als Roblox Studio je enige MCP-server is, gebruik deze configuraties zoals ze zijn. Als je meerdere MCP-servers gebruikt, kopieer dan de Roblox_Studio -vermelding en voeg deze toe aan je bestaande mcpServers -woordenboek.

Je mcp.json -bestand bevat mogelijk al andere vermeldingen. Zorg ervoor dat elke vermelding gescheiden is door een komma wanneer je de Roblox_Studio -configuratie toevoegt. Ontbrekende komma's resulteren in ongeldige JSON en voorkomen dat de configuratie wordt geladen.

Configuraties variëren per besturingssysteem:

Windows

```

{

  "mcpServers": {

    "Roblox_Studio": {

      "command": "cmd.exe",

      "args": ["/c", "%LOCALAPPDATA%\\Roblox\\mcp.bat"]

    }

  }

}

```

macOS

```

{

  "mcpServers": {

    "Roblox_Studio": {

      "command": "/Applications/RobloxStudio.app/Contents/MacOS/StudioMCP"

    }

  }

}

```

### [CLI-opdracht](#cli-opdracht)[](#cli-opdracht)

Sommige MCP-clients vereisen een CLI-opdracht in plaats van een JSON-configuratie. Gebruik de juiste opdracht voor je besturingssysteem:

Windows

```

cmd.exe /c %LOCALAPPDATA%\Roblox\mcp.bat

```

macOS

```

/Applications/RobloxStudio.app/Contents/MacOS/StudioMCP

```

## [Gebruik meerdere Studio-instanties](#gebruik-meerdere-studio-instanties)[](#gebruik-meerdere-studio-instanties)

Je kunt een enkele MCP-client verbinden met meerdere draaiende instanties van Studio tegelijkertijd. Elke toolaanroep bevat een studio_id  die de Studio-instantie identificeert waarop je je richt, wat workflows met meerdere Studio-instanties en meerdere agenten of clients betrouwbaar maakt.

Gebruik list_roblox_studios  om de verbonden instanties met hun namen, Studio-instantie-ID's en plaats-ID's te vermelden. Geef vervolgens de ID van de instantie die je wilt door als studio_id  bij volgende aanroepen.

## [Verifieer je verbinding](#verifieer-je-verbinding)[](#verifieer-je-verbinding)

Na het instellen van je client, verifieer of de verbinding werkt in Roblox Studio:

1.

Open Assistant .

2.

Klik op …  ⟩ Beheer MCP-servers .

3.

Onder Studio inschakelen als MCP-server , controleer de groene indicator om te bevestigen dat de client succesvol is verbonden.

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

Als de server niet verschijnt, of de tools niet beschikbaar zijn:

-

Herstart zowel Roblox Studio als je MCP-client.

-

Controleer of het commando of het binaire pad correct is en of het bestand bestaat.

-

Controleer je JSON-syntaxis. Zelfs een ontbrekende komma of haakje kan voorkomen dat de configuratie wordt geladen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
