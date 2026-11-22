<!-- Source: https://create.roblox.com/docs/nl-nl/projects/rojo/fully-managed -->

Volledig beheerde Rojo | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Op bestanden gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows)
8. /
9. [Rojo](/docs/nl-nl/projects/rojo)

# Volledig beheerde Rojo

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een teamworkflow voor Roblox-projecten waar alles in Git leeft : code, configuratie, kunst en niveau-indeling. Plaatsen worden gebouwd vanuit de repo, nooit met de hand bewerkt, en elke build kan worden herleid naar een commit.

## [Hoe dit de rol van Studio verandert](#hoe-dit-de-rol-van-studio-verandert)[](#hoe-dit-de-rol-van-studio-verandert)

Deze workflow beschouwt Roblox Studio als precies twee dingen:

1.

Een implementatiedoel.  Rojo assembleert het .rbxl  plaatsbestand vanuit de repo. Studio opent het, draait het en publiceert het, maar de plaats is nooit de bron van waarheid.

2.

Een hulpmiddel voor het bouwen van .rbxm  modellen.  Je bouwt of bewerkt één asset of één gebied in Studio, en exporteert het vervolgens naar de repo met Opslaan als bestand . Rojo voegt de geëxporteerde bestanden samen in de plaats.

De repo, niet Studio, definieert hoe het spel wordt samengesteld.  Het projectbestand en de mapindeling geven aan welke .rbxm  bestanden waar gaan. Je exporteert die bestanden vanuit Studio één voor één.

Vanwege dit, zijn de gebruikelijke Studio-workflows niet van toepassing :

-

Geen Team Create.  Niemand bewerkt een gedeelde plaats samen. Samenwerking gebeurt via branches en PR's.

-

Geen iteratieve wereldbewerking in een live plaats.  Je kunt een niveau niet in de loop van de tijd opbouwen in Dev en de plaats opslaan. Elke bewerking die niet is geëxporteerd naar een .rbxm  en gecommit, wordt weggegooid bij de volgende build.

-

Geen pakketten.  Git biedt de versiebeheer en delen die pakketten zouden bieden.

Als je team afhankelijk is van Team Create en het bewerken van niveaus in plaats, gebruik dan in plaats daarvan de Rojo + Pakketten workflow.

## [De korte versie](#de-korte-versie)[](#de-korte-versie)

-

Code, configuratie, kunst en niveaus  leven in Git onder src/ . Kunst- en niveauonderdelen zijn .rbxm  bestanden.

-

[Rojo](https://rojo.space)  bouwt de plaats  vanuit de repo. Code iteraties live met rojo serve . Kunstwijzigingen komen binnen door de plaats opnieuw te bouwen.

-

Iedereen werkt in hun eigen gebruikersplaats  en dient wijzigingen in via PR's.

-

CI bouwt en publiceert  Dev bij elke samenvoeging naar main , en Stabiel vanuit release-tags.

-

Prod  is het live spel.

## [Plaatsen](#plaatsen)[](#plaatsen)

Alle plaatsen zijn eigendom van de project groep .

| Plaats | | Doel | | Wie verandert het | | Hoe | | Naam |
| --- | --- |
| Gebruiker | | Jouw persoonlijke werkruimte, gebouwd vanuit jouw branch | | Jij | | rojo build  + rojo serve | | GEBRUIKER / [Naam] - [Project] - [Niveau] |
| Dev | | Laatste main , gebruikt voor teamtesten | | Alleen CI | | Gebouwd en gepubliceerd bij elke samenvoeging | | DEV - [Project] |
| Stabiel | | Een getagde build, gebruikt voor playtests | | Alleen CI | | Gebouwd en gepubliceerd vanuit een release-tag | | STABIEL / [Project] |
| Prod | | Het publieke spel | | Release-eigenaar, met goedkeuring | | CI publiceert een goedgekeurde Stabiele build | | [Project] |

Bewerk Dev of Stabiel nooit met de hand.  De volgende CI-publicatie overschrijft ze. Als er iets moet worden gewijzigd, wijzig het dan in Git.

## [Waar dingen gaan](#waar-dingen-gaan)[](#waar-dingen-gaan)

| Wat | | Waar | | Formaat |
| Code (systemen, bibliotheken) | | src/…/Systems , src/…/Libraries | | .luau |
| Getypte configuratie en definities | | src/…/ManagedContent/ | | .luau , .model.json |
| Kunstassets (props, kitstukken, personages, VFX) | | src/…/ManagedContent/Art/ | | .rbxm , één bestand per asset |
| Niveau-indeling | | src/Workspace/Areas/ | | .rbxm , één bestand per gebied |
| Verlichting, Workspace en service-instellingen | | default.project.json | | $properties |
| Bronkunst (FBX, PSD, texturen) | | Git LFS of Perforce | | Natuurlijke formaten |

Enkele regels voor het organiseren van bestanden:

-

Één bestand per asset of gebied  houdt diffs klein en merge-conflicten zeldzaam. De bestandsnaam wordt de instantienaam in de gebouwde plaats.

-

Gebruik .rbxm  voor kunst en niveaus.  Binaire bestanden zijn veel kleiner dan XML wanneer ze meshes bevatten. Gebruik [rbx-merge](https://github.com/kennethloeffler/rbx-merge)  om ze te diffen en samen te voegen; zie hieronder.

-

Elke instelling moet in Git staan.  Een gebouwde plaats bevat alleen wat in de repo staat. Instellingen zoals Verlichting, Workspace.StreamingEnabled  en Players.CharacterAutoLoads  gaan in het projectbestand. Alles wat alleen in Studio is ingesteld, gaat verloren bij de volgende build.

-

Terrein is binair , en Rojo kan het niet live synchroniseren. Houd het in zijn eigen bestand, eigendom van één persoon. Bevestig dat het een rojo build  overleeft voordat je erop vertrouwt.

### [Projectbestand](#projectbestand)[](#projectbestand)

```

{

  "name": "MyGame",

  "tree": {

    "$className": "DataModel",

    "ReplicatedStorage": { "$path": "src/ReplicatedStorage" },

    "ServerScriptService": { "$path": "src/ServerScriptService" },

    "Workspace": {

      "$path": "src/Workspace",

      "$properties": { "StreamingEnabled": true }

    },

    "Lighting": {

      "$properties": { "Technology": "Future", "ClockTime": 14 }

    }

  }

}

```

### [Repo-indeling](#repo-indeling)[](#repo-indeling)

```

src/

├── ReplicatedStorage/

│   ├── Systems/

│   ├── Libraries/

│   └── ManagedContent/

│       ├── ItemDefinitions/

│       └── Art/

│           ├── Props/Crate.rbxm

│           └── Characters/Hero.rbxm

├── ServerScriptService/

│   ├── Systems/

│   └── ManagedContent/

└── Workspace/

    └── Areas/

        ├── Town.rbxm

        └── Forest.rbxm

```

## [Waarom kunst opnieuw wordt gebouwd, niet live-synchronisatie](#waarom-kunst-opnieuw-wordt-gebouwd-niet-live-synchronisatie)[](#waarom-kunst-opnieuw-wordt-gebouwd-niet-live-synchronisatie)

Rojo's live synchronisatie (rojo serve ) gaat via de Studio-plugin API, en die API kan sommige eigenschappen niet instellen: MeshPart.MeshId , terrein en CSG-onderdelen. rojo build  schrijft het plaatsbestand rechtstreeks en heeft deze beperking niet. Zie [Rojo synchronisatie details](https://rojo.space/docs/v7/sync-details/) .

Dus de regels zijn:

-

Code- en configuratiewijzigingen:  rojo serve  + Verbinden, zoals normaal.

-

Kunst- en niveauwijzigingen:  bouw de plaats opnieuw met rojo build , en open het vervolgens opnieuw.

## [Setup (een keer per project)](#setup-een-keer-per-project)[](#setup-een-keer-per-project)

1.

Clone de repo  en installeer de toolchain met [Rokit](https://github.com/rojo-rbx/rokit) : voer rokit install  uit.

2.

Stel rbx-merge in  zodat .rbxm  bestanden correct diffen en samenvoegen:

-

Een keer per repo, één persoon voert dit uit en commit het resultaat: rbx-merge install --write-gitattributes .

-

Een keer per clone, iedereen voert rbx-merge install  uit, en vervolgens rbx-merge doctor  om te controleren of het werkte.

3.

Stel opslag voor bronkunst in:  installeer Git LFS (git lfs install ), of stel toegang in tot de Perforce-depot van het project.

4.

Bouw je gebruikersplaats:

-

Voer rojo build default.project.json -o build/place.rbxl  uit, en open vervolgens build/place.rbxl  in Studio.

-

Om met anderen te testen, kies Bestand → Publiceren als , selecteer de projectgroep, en noem het GEBRUIKER / [Naam] - [Project] - [Niveau] .

5.

Verbind Rojo:  voer rojo serve  uit, en klik vervolgens op Verbinden  in de Studio Rojo-plugin.

## [Ingenieurs: de code-loop](#ingenieurs-de-code-loop)[](#ingenieurs-de-code-loop)

1.

Maak een branch van main .

2.

Bouw je gebruikersplaats (Setup stap 4) en verbind rojo serve .

3.

Werk zoals normaal. Wanneer je kunstwijzigingen binnenhaalt, bouw de plaats opnieuw en open het opnieuw.

4.

Voer stylua  (opmaak) en selene  (linting) uit voordat je een PR opent.

5.

Open een PR en laat deze beoordelen. CI zou een test rojo build  op elke PR moeten uitvoeren.

6.

Samenvoegen naar main . CI publiceert de nieuwe build naar Dev.

## [Artiesten: de asset-loop](#artiesten-de-asset-loop)[](#artiesten-de-asset-loop)

### [Importeren van bronkunst](#importeren-van-bronkunst)[](#importeren-van-bronkunst)

1.

Houd de bronbestanden (FBX, PSD, texturen) in Git LFS of Perforce.

2.

Importeer ze met de 3D-importeur van Studio, uploadend naar de projectgroep . De assets behoren dan tot de groep, en elke plaats die vanuit de repo is gebouwd kan ze gebruiken. Zie [Asset privacy](https://create.roblox.com/docs/projects/assets/privacy) .

3.

Het wijzigen van een mesh of textuur betekent dat je het opnieuw moet uploaden, wat een nieuwe asset-ID geeft. Werk de instantie die het gebruikt bij en sla de .rbxm  opnieuw op.

### [Een asset toevoegen of wijzigen](#een-asset-toevoegen-of-wijzigen)[](#een-asset-toevoegen-of-wijzigen)

1.

Maak een branch, bouw je gebruikersplaats en open deze.

2.

Bouw of bewerk de asset in Studio. Houd elke asset als een enkele Model .

3.

Klik met de rechtermuisknop, kies Opslaan als bestand  → .rbxm , en sla het op zijn pad onder ManagedContent/Art/… . Gebruik hetzelfde pad om een bestaande asset te overschrijven.

4.

Bouw de plaats opnieuw en controleer of de asset er goed uitziet.

5.

Commit en open een PR. Beoordelaars kunnen zien wat er is veranderd met git diff , wat rbx-merge omzet in leesbare tekst.

6.

Samenvoegen. CI publiceert de wijziging naar Dev.

### [Niveau-indeling](#niveau-indeling)[](#niveau-indeling)

-

Elk gebied is één .rbxm  onder src/Workspace/Areas/ .

-

Bewerk het gebied in je gebruikersplaats, en sla het vervolgens terug op met Opslaan als bestand  over hetzelfde bestand.

-

Het opnieuw bouwen gooit alle niet-opgeslagen Studio-wijzigingen weg.  Sla op als bestand voordat je opnieuw bouwt of pullt.

-

Stem af wie elk gebied bezit. Twee mensen die hetzelfde gebied bewerken, zullen meestal conflicteren.

### [Assets plaatsen in niveaus](#assets-plaatsen-in-niveaus)[](#assets-plaatsen-in-niveaus)

-

Gebouwde plaatsen hebben geen links zoals in pakketten. Een kopie van een asset die in een gebied is geplaatst, wordt niet bijgewerkt wanneer je het originele assetbestand wijzigt.

-

Optie 1 (aanbevolen):  voor kitstukken die je vaak hergebruikt, plaats markers  in het niveau in plaats van kopieën, bijvoorbeeld een gemarkeerd onderdeel genaamd Crate . Een script vervangt elke marker door de asset uit ManagedContent/Art  tijdens runtime. Het wijzigen van het assetbestand werkt dan elke plaatsing bij.

-

Optie 2:  plaats volledige kopieën, en werk ze met de hand bij wanneer het originele asset verandert.

## [Samenvoegen en conflicten](#samenvoegen-en-conflicten)[](#samenvoegen-en-conflicten)

-

rbx-merge  voegt .rbxm  bestanden instance voor instance samen. Als twee mensen * verschillende*  dingen in hetzelfde bestand wijzigen, wordt de samenvoeging automatisch voltooid.

-

Als beide zijden dezelfde eigenschap wijzigen,  meldt Git een conflict en schrijft rbx-merge een rapport naar .rbxmerge/<bestand>/conflicts.txt . Om het op te lossen:

1.

Stel in het rapport resolution = ours | theirs | base  in voor elk conflict.

2.

Voer rbx-merge resolve --stash-dir .rbxmerge/<bestand> --out <bestand>  uit.

3.

Voer git add <bestand>  uit en ga verder met de samenvoeging.

-

Bronkunst kan niet worden samengevoegd.  Gebruik LFS-bestandsluiting (git lfs lock ) of Perforce exclusieve checkout zodat slechts één persoon een bestand tegelijk bewerkt.

## [CI: bouwen en publiceren](#ci-bouwen-en-publiceren)[](#ci-bouwen-en-publiceren)

De pipeline heeft een [Open Cloud](https://create.roblox.com/docs/cloud/guides/usage-place-publishing)  API-sleutel nodig met de assets  toestemming en Lezen  en Schrijven  toegang, plus de ID van elke plaats. Bewaar ze als CI-geheimen.

| Trigger | | Stappen |
| Elke PR | | rojo build , stylua --check , selene . Faalt de PR als een van hen faalt. |
| Samenvoegen naar main | | rojo build -o build/place.rbxl , en publiceer het naar Dev . |
| Release-tag | | Bouw de getagde commit en publiceer het naar Stabiel . |
| Goedgekeurde release | | Publiceer dezelfde getagde build naar Prod . |

Elke build komt van een commit, zodat je elke eerdere versie opnieuw kunt bouwen en opnieuw kunt publiceren, inclusief na een slechte release.

## [Communicatie](#communicatie)[](#communicatie)

Geef elk project een algemeen kanaal, een engineeringkanaal (PR-links, technische discussie) en een kunstkanaal (WIPs, beoordelingen).

## [Referentie](#referentie)[](#referentie)

-

[Rojo projectformaat](https://rojo.space/docs/v7/project-format/)

-

[Rojo synchronisatie details](https://rojo.space/docs/v7/sync-details/)

-

[rbx-merge](https://github.com/kennethloeffler/rbx-merge)

-

[Git LFS](https://git-lfs.com)

-

[Asset privacy](https://create.roblox.com/docs/projects/assets/privacy)

-

[Open Cloud plaats publicatie](https://create.roblox.com/docs/cloud/guides/usage-place-publishing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
