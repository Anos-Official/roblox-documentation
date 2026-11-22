<!-- Source: https://create.roblox.com/docs/nl-nl/ai/coding-harness -->

Bouw met een code-harnas | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [AI accelerated workflows](/docs/nl-nl/ai/accelerated-workflows)

# Bouw met een code-harnas

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze gids en de bijbehorende video begeleiden je bij het verbinden van een AI-gestuurde code-harnas met Roblox Studio via MCP, zodat je agent namens jou kan lezen, schrijven en playtesten.

Aan het einde heb je een projectmap die synchroniseert met Studio via Script Sync  (een functie waarmee je je eigen editor kunt gebruiken om code te schrijven), een MCP -verbinding waarmee je agent Studio direct kan aansturen, en een Git-repository die klaar is voor ontwikkeling.

## [Stap 1: Installeer de vereisten](#stap-1-installeer-de-vereisten)[](#stap-1-installeer-de-vereisten)

Je hebt de volgende componenten nodig voordat je begint:

1.

Een AI-gestuurde teksteditor  - De meest populaire opties zijn [Visual Studio Code](https://code.visualstudio.com)  en [Cursor](https://cursor.com) . Cursor heeft zijn AI-assistent ingebouwd, terwijl VS Code een extensie zoals [Claude Code](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code)  nodig heeft. Beide werken hier goed, dus gebruik degene die je verkiest.

2.

Roblox Studio  - Download het van [create.roblox.com](https://create.roblox.com/docs/studio/setup) .

3.

Git  - Installeer het van [git-scm.com](https://git-scm.com/install) .

-

Op Windows kun je [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/)  gebruiken: winget install --id Git.Git -e --source winget .

-

Op macOS kun je [Homebrew](https://brew.sh/)  gebruiken: brew install git .

## [Stap 2: Meld je aan bij alles](#stap-2-meld-je-aan-bij-alles)[](#stap-2-meld-je-aan-bij-alles)

1.

Je teksteditor:

-

VS Code  — Aanmelden varieert per extensie. Voor Claude Code, klik op het Claude-pictogram in de activiteitsbalk, meld je aan met je Anthropic-account en bevestig dat het chatpaneel opent. Andere aanbieders zijn vergelijkbaar.

-

Cursor  — Open Cursor, meld je aan met je Cursor-account en bevestig dat het chatpaneel opent. Je kunt elk model gebruiken dat je verkiest.

2.

Roblox Studio  — Open Studio, meld je aan met je Roblox-account en bevestig dat je een nieuwe plaats kunt maken.

## [Stap 3: Download de starterrepository](#stap-3-download-de-starterrepository)[](#stap-3-download-de-starterrepository)

De starterrepository geeft je de mapindeling en een .gitignore -bestand zodat Git alleen de delen van je project commit die belangrijk zijn. Het meeste handmatige werk is al voor je gedaan.

1.

Download de [starterrepository](https://prod.docsiteassets.roblox.com/assets/solutions/WaveSurvival.zip)  en pak deze uit. Het bevat al een map genaamd WaveSurvival .

2.

Kies in je editor Bestand → Map openen  en selecteer WaveSurvival . Je zou drie mappen binnenin moeten zien:

-

ServerScriptService/  bevat serverscripts, zoals game-logica, vijand-AI en golfbeheer.

-

ReplicatedStorage/  bevat gedeelde modules die zowel de server als de client kunnen gebruiken.

-

StarterPlayerScripts/  bevat clientscripts die voor elke speler draaien.

De .gitkeep -bestanden in elke map zijn tijdelijke bestanden zodat Git de mappen bijhoudt terwijl ze nog leeg zijn.

## [Stap 4: Maak een leeg project in Roblox Studio](#stap-4-maak-een-leeg-project-in-roblox-studio)[](#stap-4-maak-een-leeg-project-in-roblox-studio)

1.

Open Roblox Studio en klik op Nieuwe ervaring .

2.

Kies Bestand → Opslaan naar bestand , navigeer naar je WaveSurvival -map en sla de plaats op als WaveSurvival.rbxlx . Het .gitignore -bestand van de starterrepository sluit al .rbxlx -bestanden uit van Git.

3.

Houd Studio open. Je hebt het nodig voor Script Sync en MCP.

## [Stap 5: Schakel de Script Sync-bèta in](#stap-5-schakel-de-script-sync-bèta-in)[](#stap-5-schakel-de-script-sync-bèta-in)

Script Sync is een bètafunctie, dus je moet deze inschakelen voordat je deze kunt gebruiken.

Studio wordt vaak bijgewerkt. Als je Script Sync  niet in de lijst ziet, installeer dan de [laatste versie van Studio](https://create.roblox.com/download)  en probeer het opnieuw.

1.

Kies in Studio Bestand → Bèta-functies .

2.

Zoek Script Sync , schakel het in en klik op Opslaan .

3.

Herstart Studio wanneer daarom wordt gevraagd.

## [Stap 6: Verbind Script Sync](#stap-6-verbind-script-sync)[](#stap-6-verbind-script-sync)

Je verbindt Script Sync één keer per project door elke Studio-service te koppelen aan de bijbehorende map op de schijf.

1.

Klik met de rechtermuisknop op ServerScriptService  in de Verkenner.

2.

Kies Script Sync → Synchroniseren naar , en blader naar je WaveSurvival -map.

3.

Herhaal dit voor ReplicatedStorage  en StarterPlayerScripts .

Selecteer de bovenliggende WaveSurvival -map, niet de mappen erin. Omdat de mappen al de juiste namen hebben, koppelt Script Sync elke service automatisch aan de juiste.

Alle .luau -bestanden die je in die mappen maakt, verschijnen nu automatisch als scripts in Studio.

## [Stap 7: Verifieer Script Sync](#stap-7-verifieer-script-sync)[](#stap-7-verifieer-script-sync)

Vraag je agent in het chatpaneel van je editor:

Maak een testscript aan in ServerScriptService/Test.server.luau  dat 'Hallo van Script Sync!' naar de uitvoer print.

Controleer in Studio de Verkenner. Je zou Test  onder ServerScriptService  moeten zien verschijnen. Je zult een diepere, agent-gestuurde controle uitvoeren nadat MCP is verbonden.

## [Stap 8: Schakel de MCP-verbinding in](#stap-8-schakel-de-mcp-verbinding-in)[](#stap-8-schakel-de-mcp-verbinding-in)

De Studio MCP-server stelt je AI-agent in staat om direct met Studio te communiceren, de gameboom te lezen, objecten te maken, scripts uit te voeren en de uitvoer te controleren. Het dekt alles wat Script Sync niet kan bereiken, zoals StarterGui  en StarterPack .

1.

Open in Studio het Assistent-venster met de Assistent -knop rechtsboven.

2.

Klik op ⋯ → Beheer MCP-servers .

3.

Bevestig dat MCP is ingeschakeld.

4.

Onder Snelle verbinding , schakel Cursor of Visual Studio Code in.

Als je je editor hebt geïnstalleerd terwijl Studio open was, moet je mogelijk Studio, je editor of beide opnieuw opstarten om de verbinding tot stand te brengen. Voor meer details, zie [Verbind met de Roblox Studio MCP-server](/docs/nl-nl/studio/mcp) .

## [Stap 9: Verifieer de MCP-verbinding](#stap-9-verifieer-de-mcp-verbinding)[](#stap-9-verifieer-de-mcp-verbinding)

Vraag je agent:

Gebruik de Roblox MCP om de huidige gameboom in Roblox Studio te lezen. Lijst wat er in Workspace staat.

Je moet mogelijk het commando goedkeuren of de MCP-tool aan een whitelist toevoegen. Voor een vers Baseplate-sjabloon beschrijft de reactie de standaard Camera , Terrain , Baseplate  en SpawnLocation  en bevestigt dat er nog geen andere inhoud is.

## [Stap 10: Voer een end-to-end controle uit](#stap-10-voer-een-end-to-end-controle-uit)[](#stap-10-voer-een-end-to-end-controle-uit)

Vraag je agent om de volledige setup in één keer te verifiëren:

Gebruik de Roblox MCP-verbinding om te verifiëren of Script Sync goed werkt. Maak enkele wijzigingen in Test.server.luau, voeg nieuwe scripts toe in de andere twee mappen en verifieer de uitvoer van elk. Voer game:GetService("InstanceFileSyncService"):GetStatus(instance)  uit in elk script om de synchronisatiestatus te verifiëren. Wanneer je klaar bent, verwijder je alle drie de scripts.

Kijk in Studio en je zult zien dat de agent een playtest start om de uitvoer te bevestigen.

## [Stap 11: Commit naar Git](#stap-11-commit-naar-git)[](#stap-11-commit-naar-git)

Je hebt nu een schone, werkende configuratie, wat dit een goed moment maakt om te committen. Voer vanuit je terminal uit:

```

git add .

git commit -m "Script sync verbonden en MCP geverifieerd"

```

## [Volgende stappen](#volgende-stappen)[](#volgende-stappen)

Je project is nu gesynchroniseerd met Studio, je AI-agent kan er direct mee communiceren, en je hebt een Git-repository om wijzigingen en voortgang bij te houden.

Van hieruit kun je het WAVE_SURVIVAL.md -bestand van het starterproject gebruiken als context voor je agent om een golfoverlevingsspel te bouwen. Volg de bijbehorende video om het spel fase voor fase te bouwen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
