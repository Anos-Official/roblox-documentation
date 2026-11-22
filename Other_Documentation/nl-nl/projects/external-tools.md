<!-- Source: https://create.roblox.com/docs/nl-nl/projects/external-tools -->

Derde-partijtools | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Op bestanden gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows)

# Derde-partijtools

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor professionele ontwikkelstudio's kan het opzetten van derde-partijtools en investeren in automatisering de productiviteit van ontwikkelaars aanzienlijk verbeteren. De cloud-first benadering van Roblox heeft veel voordelen, maar het verplaatsen van bepaalde delen van de ontwikkelworkflow buiten  de cloud kan grotere teams helpen om veranderingen in de loop van de tijd bij te houden, code te beoordelen en de talen en tools te gebruiken waarmee ze al vertrouwd zijn.

-

Als je gewoon een externe teksteditor wilt gebruiken of code in versiebeheer wilt houden, is [Script Sync](/docs/nl-nl/scripting/sync)  een geweldige keuze.

-

Als je je hele project als een set lokale bestanden wilt beheren, behandelt deze pagina enkele tools en strategieën.

-

Om volledige teamworkflows en hun afwegingen te vergelijken, zie [Vergelijk op bestandsbasis gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows) .

Hoewel deze pagina verschillende populaire tools behandelt, moet het niet worden opgevat als een strikte aanbeveling voor deze tools. Elk team heeft verschillende behoeften, dus deze pagina is bedoeld om je te helpen manieren te onderzoeken om je workflow te verbeteren in plaats van je te vertellen dat je iets specifieks moet downloaden.

De tools op deze pagina worden niet onderhouden door Roblox en kunnen op elk moment veranderen of stoppen met werken.

## [Het synchronisatieprobleem](#het-synchronisatieprobleem)[](#het-synchronisatieprobleem)

In wezen is het gebruik van externe tools met Roblox een * synchronisatie*  probleem:

-

Je wilt dat je Roblox-instanties bestaan als bestanden op de schijf, zodat je je eigen tools kunt gebruiken om eraan te werken.

-

Je moet je bestanden terug in je Roblox-project krijgen nadat je klaar bent met werken.

-

Als iemand anders in de tussentijd diezelfde bestanden heeft gewijzigd, moet je eventuele conflicten oplossen.

Om de hele oplossing naadloos en automatisch te laten aanvoelen, moet je a) luisteren naar wijzigingen in bestanden en b) deze wijzigingen weer in Studio opnemen.

In plaats van de cloud-first benadering van Roblox, staat [Rojo](https://rojo.space/)  een "bestandsysteem-eerst" benadering toe. Het draait een server op je machine die communiceert met een [Studio-plugin](/docs/nl-nl/studio/plugins)  om je bestanden en het datamodel van Studio te synchroniseren.

## [Rojo](#rojo)[](#rojo)

Rojo is de meest voorkomende tool voor het synchroniseren van bestanden met Studio. Voor installatie en uitvoering, en om te kiezen tussen gedeeltelijk en volledig beheerde projecten, zie [Rojo](/docs/nl-nl/projects/rojo) .

## [Rokit](#rokit)[](#rokit)

Verschillende teamleden die verschillende versies van dezelfde tool gebruiken, veroorzaken moeilijk te diagnosticeren problemen. Een toolchain-manager zoals [Rokit](https://github.com/rojo-rbx/rokit)  lost dit op met een rokit.toml -bestand dat elke tool en zijn versie opsomt, zodat rokit install  dezelfde versies op elke machine instelt. Omdat het je basisontwikkelomgeving beheert in plaats van de pakketten binnen je project, is Rokit meer vergelijkbaar met [nvm](https://github.com/nvm-sh/nvm)  dan met [npm](https://www.npmjs.com/) . Voor een voorbeeld van rokit.toml , zie [Installeer Rojo](/docs/nl-nl/projects/rojo#installeer-rojo) .

## [Pakketbeheerders](#pakketbeheerders)[](#pakketbeheerders)

Roblox heeft een robuuste set inbegrepen API's, maar als je gebruik wilt maken van softwarepakketten van de gemeenschap op een consistente, reproduceerbare manier, heb je een pakketbeheerder nodig. [Wally](https://wally.run/)  is een populaire optie. Je kunt het installeren via Rokit, net als Rojo.

Voer binnen de Rojo-directory van je game wally init  uit. Voeg vervolgens je gewenste pakketten toe aan wally.toml . Het bestand kan er als volgt uitzien:

```

[package]

name = "my-home-directory/my-new-experience"

version = "0.1.0"

registry = "https://github.com/UpliftGames/wally-index"

realm = "shared"

[dependencies]

react = "jsdotlua/react@17.2.1"

react-roblox = "jsdotlua/react-roblox@17.2.1"

cryo = "phalanxia/cryo@1.0.3"

```

Voer vervolgens wally install  uit. Wally maakt een Packages -directory aan en downloadt de opgegeven pakketten daar. De laatste stap is om de Packages -directory aan Rojo toe te voegen, zodat de inhoud weer naar Roblox synchroniseert. Open default.project.json  en voeg het pad toe. Voor de eenvoud voegt dit voorbeeld de hele directory toe aan [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , zodat alle pakketten beschikbaar zijn voor alle scripts, maar je kunt er ook voor kiezen om specifieke pakketten toe te voegen aan [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  of [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) :

```

{

  "name": "my-new-experience",

  "tree": {

    "$className": "DataModel",

    "ReplicatedStorage": {

      "Shared": {

        "$path": "src/shared"

      },

      "Packages": {

        "$path": "Packages"

      }

    },

    ...

  }

}

```

Vervolgens kun je pakketten binnen je scripts vereisen, net als elke andere [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) :

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local React = require(ReplicatedStorage.Packages.react)

local ReactRoblox = require(ReplicatedStorage.Packages["react-roblox"])

local handle = Instance.new("ScreenGui", Players.LocalPlayer.PlayerGui)

local root = ReactRoblox.createRoot(handle)

local helloFrame = React.createElement("TextLabel", {

	Text = "Hallo Wereld!",

	Size = UDim2.new(0, 200, 0, 200),

	Position = UDim2.new(0.5, 0, 0.5, 0),

	AnchorPoint = Vector2.new(0.5, 0.5),

	BackgroundColor3 = Color3.fromRGB(248, 217, 109),

	Font = Enum.Font.LuckiestGuy,

	TextSize = 24

})

root:render(helloFrame)

```

Net als bij de meeste andere softwareprojecten is het doel dat bijdragers een repository kunnen klonen, Rokit kunnen installeren, een paar commando's kunnen uitvoeren en dezelfde ontwikkelomgeving hebben als de rest van het team.

Voor een gedetailleerde walkthrough van het gebruik van React om een Roblox UI te maken, zie [React + Roblox](https://devforum.roblox.com/t/how-to-react-roblox/2964543) .

## [Versiebeheer](#versiebeheer)[](#versiebeheer)

Het hebben van een set platte tekstbestanden op je computer ontgrendelt een verscheidenheid aan mogelijkheden, maar de primaire is * versiebeheer* . Je kunt je bestanden opslaan in een [Git](https://git-scm.com/)  of [Mercurial](https://www.mercurial-scm.org/)  repository; externe repositories hosten en codewijzigingen beoordelen in [GitHub](https://github.com) , [GitLab](https://gitlab.com)  of [Bitbucket](https://bitbucket.org) ; en de teksteditor gebruiken die je wilt.

[Visual Studio Code](https://code.visualstudio.com)  en [Cursor](https://cursor.com)  hebben het grootste ecosysteem van extensies, maar [Sublime Text](https://www.sublimetext.com)  en [Notepad++](https://notepad-plus-plus.org) , en [Vim](https://www.vim.org)  zijn ook populaire keuzes. Welke editor je ook kiest, het afstemmen van de mogelijkheden van de Studio-scripteditor vereist enkele extensies.

Je kunt ook overwegen om toe te voegen:

-

Een linter zoals [selene](https://github.com/Kampfkarren/selene)  om veelvoorkomende problemen op te sporen en codestandaarden af te dwingen

-

Een codeformatter zoals [StyLua](https://github.com/JohnnyMorganz/StyLua)

-

Een taalsserver zoals [Luau Language Server](https://github.com/JohnnyMorganz/luau-lsp)  voor autocompletion, typechecking en meer

-

[Open Cloud](/docs/nl-nl/cloud/guides)  scripts (niet gesynchroniseerd met Studio) om [een gepubliceerd spel bij te werken](/docs/nl-nl/cloud/reference/Universe#Cloud_UpdateUniverse)  of [servers opnieuw te starten](/docs/nl-nl/cloud/reference/Universe#Cloud_RestartUniverseServers)

## [Build-, asset- en samenvoegtools](#build--asset--en-samenvoegtools)[](#build--asset--en-samenvoegtools)

-

[Lune](https://github.com/lune-org/lune)  is een zelfstandige Luau-runtime die veel teams gebruiken voor build-, deploy- en automatiseringsscripts.

-

[Tarmac](https://github.com/Roblox/tarmac)  uploadt afbeeldingen van de schijf naar Roblox en genereert een module die bestands paden naar asset-ID's map.

-

[rbx-merge](https://github.com/kennethloeffler/rbx-merge)  laat Git leesbare diffs van Roblox-plaats- en modelbestanden zien en samenvoegen van wijzigingen die niet conflicteren. Voor setup, zie [Volledig beheerd Rojo](/docs/nl-nl/projects/rojo/fully-managed#setup-een-keer-per-project) .

## [Ongedaan maken van alles](#ongedaan-maken-van-alles)[](#ongedaan-maken-van-alles)

Omdat derde-partijtools wijzigingen terug synchroniseren naar Roblox Studio in plaats van het te vervangen, omvat geen enkel deel van deze workflow enige lock-in. Op elk moment kun je stoppen met het gebruik van een of al deze tools en teruggaan naar het exclusief bewerken van je game in Studio. Het gebrek aan risico maakt het experimenteren met derde-partijtools bijzonder aantrekkelijk.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
