<!-- Source: https://create.roblox.com/docs/nl-nl/projects/rojo -->

Rojo | Documentatie - Roblox Creator Hub

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

# Rojo

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Rojo](https://rojo.space/)  is een communitytool die een "bestandsysteem-eerst" benadering hanteert voor Roblox-projecten. Het draait een server op je machine die communiceert met een [Studio-plugin](/docs/nl-nl/studio/plugins)  om bestanden op je schijf te synchroniseren met het Studio-datamodel, en het kan plaats- en modelbestanden bouwen vanuit die bestanden. Met je project op schijf kun je Git, je eigen editor en CI gebruiken.

Rojo wordt niet onderhouden door Roblox en kan op elk moment veranderen of stoppen met werken. Voor volledige referentie, zie de [Rojo-documentatie](https://rojo.space/docs/v7/) .

Hoe je Rojo gebruikt, hangt af van hoeveel van je game je wilt dat het beheert:

-

[Deels beheerd](/docs/nl-nl/projects/rojo/partially-managed) :  Rojo beheert je code, en Git is de bron van waarheid. Plaatsen en assets blijven op Roblox, waar artiesten ze bewerken met Team Create en pakketten. We raden dit aan voor de meeste teams die Git gebruiken.

-

[Volledig beheerd](/docs/nl-nl/projects/rojo/fully-managed) :  Rojo beheert je hele game, inclusief modellen en afbeeldingen. Git is de bron van waarheid voor alles, en CI bouwt en publiceert je plaatsen.

Om deze te vergelijken met een Studio-native workflow, zie [Vergelijk bestandsgebaseerde workflows](/docs/nl-nl/projects/file-based-workflows) .

## [Installeer Rojo](#installeer-rojo)[](#installeer-rojo)

Je kunt handmatig een Rojo-binaire downloaden en uitvoeren, maar die aanpak loopt het risico dat verschillende mensen in je team verschillende Rojo-versies gebruiken. Een betere oplossing is om een toolchain-manager zoals [Rokit](https://github.com/rojo-rbx/rokit)  te gebruiken, die een configuratiebestand en een lijst van repositories en versies gebruikt om het installatie- en upgradeproces consistent te maken op verschillende machines.

Omdat het je basisontwikkelomgeving beheert in plaats van de pakketten binnen je project, is Rokit meer vergelijkbaar met [nvm](https://github.com/nvm-sh/nvm)  dan met [npm](https://www.npmjs.com/) , maar de vergelijking is niet perfect. Een eenvoudig rokit.toml -bestand ziet er als volgt uit:

```

[tools]

rojo = "rojo-rbx/rojo@7.6.1"

wally = "upliftgames/wally@0.3.2"

lune = "lune-org/lune@0.10.4"

```

Vervolgens installeer je deze tools met rokit install . Naast een globaal rokit.toml -bestand ondersteunt Rokit per-projectbestanden, zodat je gemakkelijk verschillende versies van Rojo, Wally of een andere tool voor verschillende projecten kunt gebruiken en je hele team op diezelfde versies kunt houden.

Wanneer een tool een nieuwe versie uitbrengt, verhoog je expliciet het versienummer in je .toml -bestand, gebruik je Rokit om de upgrade uit te voeren, test je de nieuwe versie en downgraden als het problemen veroorzaakt. Voor commando's en installatie-instructies, zie [Rokit](https://github.com/rojo-rbx/rokit#-rokit) .

## [Voer Rojo uit](#voer-rojo-uit)[](#voer-rojo-uit)

Nadat je Rojo met Rokit hebt geïnstalleerd, wat je eigenlijk hebt geïnstalleerd is de Rojo-server. De volgende stap is om de Rojo-plugin voor Roblox Studio te installeren.

Je kunt het installeren vanuit de [Creator Store](https://create.roblox.com/store/asset/13916111004/Rojo)  of lokaal installeren met dit commando:

```

rojo plugin install

```

Genereer vervolgens de projectstructuur voor je nieuwe game en bouw deze:

```

rojo init my-new-experience

cd my-new-experience

rojo build -o my-new-experience.rbxl

```

Alternatief kun je [een bestaand spel porteren](https://rojo.space/docs/v7/getting-started/existing-game/) . Hoe dan ook, nadat je een project hebt, start je de Rojo-server:

```

rojo serve

```

Open in Roblox Studio het .rbxl -bestand dat je zojuist hebt gebouwd, open de Rojo-plugin en maak verbinding met je nu draaiende server, waarna je kunt beginnen met het aanbrengen van wijzigingen in je favoriete teksteditor en die wijzigingen automatisch kunt laten synchroniseren met Studio.

![Visual Studio Code met een geopend Rojo-project.](https://prod.docsiteassets.roblox.com/assets/scripting/external-tools/external-tools-vscode.png)

![De Rojo-plugin en Studio Explorer naast elkaar.](https://prod.docsiteassets.roblox.com/assets/scripting/external-tools/external-tools-rojo-plugin.png)

Rojo-projecten hebben bepaalde naamvereisten voor bestanden, talrijke configuratieopties en enkele beperkingen, die allemaal worden behandeld in de [Rojo-documentatie](https://rojo.space/docs/v7/) .

Voor richtlijnen over het organiseren van je code, zie [Scripttypes en locaties](/docs/nl-nl/scripting/locations#aanbevelingen)  en de projecten in [Roblox/resources](https://github.com/Roblox/resources) .

## [Probleemoplossing Rojo](#probleemoplossing-rojo)[](#probleemoplossing-rojo)

| Probleem | | Oplossing |
| --- | --- |
| Rojo synchroniseert niet, of gedraagt zich anders op verschillende machines. | | Teamleden gebruiken verschillende Rojo- of pluginversies. Pin versies in rokit.toml  en voer rokit install  uit. |
| Code gesynchroniseerd op de verkeerde plaats. | | Voeg servePlaceIds  toe aan je projectbestand zodat Rojo alleen synchroniseert naar de plaatsen die je vermeldt. |
| Rojo heeft inhoud verwijderd die artiesten hebben toegevoegd. | | Stel $ignoreUnknownInstances  in op true  op de services die zowel Rojo als artiesten gebruiken. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
