<!-- Source: https://create.roblox.com/docs/nl-nl/projects/assets/manager -->

Asset Manager | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. [Beheren](/docs/nl-nl/projects/assets/manager)

# Asset Manager

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Asset Manager , toegankelijk vanuit het Venster  menu van Studio of het Start  tabblad, stelt je in staat om [plaatsen](/docs/nl-nl/production/publishing/publish-games-and-places)  te beheren en bulkgewijs assets in je game te importeren, waaronder [afbeeldingen](/docs/nl-nl/parts/textures-decals) , [mesh](/docs/nl-nl/parts/meshes) , [pakketten](/docs/nl-nl/projects/assets/packages) , [audio](/docs/nl-nl/audio/assets)  en [modellen](/docs/nl-nl/parts/models) .

## [Inventaris sorteren](#inventaris-sorteren)[](#inventaris-sorteren)

Assets worden gesorteerd op verschillende inventarissen  zoals geselecteerd via het uitklapmenu aan de linkerkant van het venster. Als je de sorteerlijst niet ziet, klik dan op de uitklapknop in de linkerbenedenhoek van het venster.

 ![Een voorbeeld van hoe inventarissen zijn gesorteerd in de linker navigatie van de Asset Manager.](https://prod.docsiteassets.roblox.com/assets/studio/asset-manager/Inventory-Sorts.png)

-

<Ervaringsnaam>  — De inventaris van de open game, weergegeven met zijn naam, met assets [gedeeld met de game](/docs/nl-nl/projects/assets/privacy#aan-games)  onder Project .

-

Plaatsen In Ervaring  — De [plaatsen](/docs/nl-nl/production/publishing/publish-games-and-places)  van de game.

-

Mijn Inventaris  — Assets geïmporteerd naar je eigen gebruikersaccount, [gedeeld met jou](/docs/nl-nl/projects/assets/privacy#to-creators) , of verkregen uit de [Creator Store](/docs/nl-nl/production/creator-store) .

-

Groep Inventarissen  — Assets geïmporteerd in [groepen](/docs/nl-nl/projects/groups)  die je bezit of groepen waartoe je behoort (ervan uitgaande dat je voldoende [machtigingen](/docs/nl-nl/projects/groups#rollen-en-machtigingen)  binnen de groep hebt), of assets [gedeeld met de groepen](/docs/nl-nl/projects/assets/privacy#to-groups) . Rechtsklikken op een groep toont een contextmenu met de volgende opties:

| Verberg Groep | | Verbergt de groep uit de zijbalk. |
| --- | --- |
| Pas Groepen Aan | | Stelt je in staat om de groepen te kiezen die in de zijbalk en zoekfilteropties verschijnen. |
| Vernieuw Groepen | | Vernieuwt de lijst van groepen die je kunt tonen of verbergen. |

## [Mappen](#mappen)[](#mappen)

Mappen stellen je in staat om assets en andere mappen te organiseren in een hiërarchie binnen een inventaris. Je kunt mappen maken binnen Mijn Inventaris , binnen Groep Inventarissen  die mapbewerkingen ondersteunen, en binnen de inventaris van een open game onder Project .

Mappen hebben de volgende limieten:

-

Tot 50.000 mappen  per account of hoofdinventaris.

-

Tot 100 submappen  in een enkele map of hoofdinventaris.

-

Tot 20.000 assets  per map.

-

Tot 20 niveaus  van mapnesting.

De eerste keer dat mappen worden geïnitialiseerd voor een account, kan er een korte opzetperiode van toepassing zijn. Als mapbewerkingen nog niet beschikbaar zijn, toont de zijbalk een waarschuwingspictogram naast het getroffen account; klik erop om de gereedheid te vernieuwen. De opzet is meestal binnen enkele minuten voltooid.

### [Maken, hernoemen en verwijderen](#maken-hernoemen-en-verwijderen)[](#maken-hernoemen-en-verwijderen)

Rechtsklik in de zijbalk of hoofdweergave om toegang te krijgen tot mapacties.

| Actie | | Beschrijving |
| Maak Map | | Maakt een nieuwe lege map op de huidige locatie. Een nieuwe invoer verschijnt met een inline naamveld; typ een naam en druk op Enter  om te bevestigen of Esc  om te annuleren. |
| Groep Selectie als Map | | Beschikbaar wanneer een of meer assets zijn geselecteerd. Maakt een nieuwe map en verplaatst de geselecteerde assets erin. |
| Hernoem | | Vervangt de naam van de map met een inline bewerkbaar veld dat is voorgevuld met de huidige naam. Druk op Esc  om te annuleren zonder wijzigingen aan te brengen. |
| Verwijder Map | | Verwijdert de map. Mappen moeten leeg zijn voordat ze kunnen worden verwijderd; verplaats of verwijder eerst de inhoud. Wanneer meerdere lege mappen zijn geselecteerd, toont het menu Verwijder Mappen . |

Mapnamen mogen geen \ , / , : , * , ? , " , < , > , of | bevatten, en mogen niet eindigen met een punt. Namen die beginnen met een punt (bijvoorbeeld, .hidden ) zijn toegestaan.

### [Navigeren](#navigeren)[](#navigeren)

Je kunt de map hiërarchie vanuit beide panelen navigeren:

-

Zijbalk  — Gebruik de uitklappijl om submappen te onthullen, of klik eenmaal op een map om deze te openen.

-

Hoofdweergave  — Dubbelklik op een map om erin te navigeren. Klik op de bovenliggende invoer in de zijbalk, of gebruik de terugpijl, om terug te keren.

### [Items verplaatsen](#items-verplaatsen)[](#items-verplaatsen)

Je kunt zowel assets als mappen verplaatsen, maar alleen binnen dezelfde inventaris. Verplaatsingen tussen inventarissen (bijvoorbeeld, van Mijn Inventaris  naar een groep  inventaris) worden niet ondersteund.

| Methode | | Beschrijving |
| Sleep en zet neer | | Sleep geselecteerde items naar een bestemmingsmap in zowel de hoofdweergave als de zijbalkboom. Geldige dropdoelen worden gemarkeerd terwijl je zweeft. |
| Verplaats dialoog | | Rechtsklik op een selectie en kies Verplaats  om een mapkiezer te openen. Gebruik de in-dubbelklikpijl of dubbelklik om een map binnen te gaan, Terug  om een niveau omhoog te gaan, selecteer vervolgens een bestemming en klik op Verplaats . Vernieuw  haalt de mappenlijst opnieuw op van de server. |

Je kunt meerdere items tegelijk verplaatsen. Het verplaatsen van een map in zichzelf of in een van zijn eigen afstammelingen is geblokkeerd, en ongeldige bestemmingen worden niet gemarkeerd als dropdoelen of zijn grijs weergegeven in de Verplaats  dialoog.

### [Zoeken en mappen](#zoeken-en-mappen)[](#zoeken-en-mappen)

Wanneer je een zoekopdracht typt, omvatten de resultaten een aparte Mappen  sectie die overeenkomende mappen naast assetresultaten opsomt. Dubbelklik op een mapresultaat om de zoekmodus te verlaten en in die map te navigeren.

Sleep-en-neerzetten en de Verplaats  dialoog zijn uitgeschakeld terwijl je zoekresultaten bekijkt. Navigeer eerst naar een map of inventaris, en reorganiseer dan.

### [Niet-ondersteunde scopes](#niet-ondersteunde-scopes)[](#niet-ondersteunde-scopes)

Mapbewerkingen zijn niet beschikbaar in de volgende weergaven:

-

Plaatsen In Ervaring  — Plaatsen kunnen niet in mappen worden georganiseerd.

-

Recente Uploads  — Alleen-lezen voor organisatorische doeleinden.

## [Asset weergave opties](#asset-weergave-opties)[](#asset-weergave-opties)

In het hoofdpaneel worden assets voor de geselecteerde [inventaris](#inventaris-sorteren)  weergegeven. Om het weergavetypen te wisselen, klik op de weergave type  knop en selecteer ofwel Lijst  of Raster . Terwijl je in rasterweergave bent, kunnen assettegels worden vergroot of verkleind via de schuifwidget.

 ![Diagram van de weergave type knop en opties in de Asset Manager.](https://prod.docsiteassets.roblox.com/assets/studio/asset-manager/Display-Options.png)

In Lijst  weergave, klik op een kolomkop om assets op dat detail te ordenen en kolommen te vergroten of verkleinen door de scheidingsbalk tussen hen te slepen.

 ![Diagram van hoe kolommen kunnen worden geordend en vergroot of verkleind in Lijstweergave binnen de Asset Manager.](https://prod.docsiteassets.roblox.com/assets/studio/asset-manager/List-View-Ordering.png)

Kolommen kunnen aan of uit worden gezet door rechts te klikken in de kopbalk. Terwijl kolommen niet kunnen worden herschikt door te slepen, kun je een kolom uitschakelen en vervolgens weer inschakelen om deze als de meest rechtse kolom toe te voegen.

In Raster  weergave wordt de ordening geregeld via de sorteren  knop:

 ![Locatie van de sorteerknop voor Rasterweergave binnen de Asset Manager.](https://prod.docsiteassets.roblox.com/assets/studio/asset-manager/Grid-View-Ordering.png)

## [Asset type filters](#asset-type-filters)[](#asset-type-filters)

De filter items  knop stelt je in staat om te bepalen welke assets worden weergegeven.

 ![Locatie van de filterknop in de Asset Manager.](https://prod.docsiteassets.roblox.com/assets/studio/asset-manager/Asset-Type-Filters.png)

| Filter Type | | Opties |
| Asset Type | | Animatie  | Audio  | Decal  | FontFamily  | Afbeelding  | Mesh  | MeshPart  | Model  | Plaats  | Plugin  | Video |
| Maker | |  |
| Bron | | Creator Store  | Gedeeld Met Mij  | Geüpload |
| Is Pakket | |  |
| Alleen Gearchiveerd | |  |

## [Asset import](#asset-import)[](#asset-import)

De asset import  knop stelt je in staat om een of meer assets van elk type asset te importeren. Geïmporteerde assets komen in de moderatiewachtrij en worden, na goedkeuring, toegevoegd aan de inventaris van de gebruiker/groep die de game bezit.

 ![Locatie van de importknop in de Asset Manager.](https://prod.docsiteassets.roblox.com/assets/studio/asset-manager/Import-Button.png)

Voor meer informatie over ondersteunde bestandstypen en andere functies, zie [Importer](/docs/nl-nl/studio/importer) .

## [Invoegen en snelle acties](#invoegen-en-snelle-acties)[](#invoegen-en-snelle-acties)

Snelle acties zijn toegankelijk door met de rechtermuisknop op een assetnaam/tegel te klikken en een optie uit het contextmenu te selecteren. Houd er rekening mee dat plaatsen unieke acties bieden in vergelijking met andere assets.

Algemeen Plaatsen

| Actie | | Beschrijving |
| Invoegen | | Stelt je in staat om te kiezen tussen Invoegen bij Camera  of Invoegen bij Asset Positie  voor ruimtelijke 3D-assets (niet-ruimtelijke assets zoals audio worden eenvoudigweg ingevoegd in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  of de momenteel geselecteerde [Explorer](/docs/nl-nl/studio/explorer)  instantie). Verschijnt niet voor FontFamily  of Plugin  assets. |
| Bewerk Asset | | Opent het configuratievenster van de asset om details zoals de assettitel, beschrijving en meer te bewerken. Verschijnt niet voor FontFamily  of Plugin  assets. |
| Verplaats | | Opent de [Verplaats dialoog](#items-verplaatsen)  om de asset naar een map binnen dezelfde inventaris te verplaatsen. Uitgeschakeld tijdens het bekijken van zoekresultaten. |
| Kopieer Asset ID | | Kopieert de asset ID naar het klembord, handig voor het plakken van de ID in een objecteigenschap zoals [AudioPlayer.AssetId](/docs/nl-nl/reference/engine/classes/AudioPlayer#AssetId)  of [MeshPart.MeshId](/docs/nl-nl/reference/engine/classes/MeshPart#MeshId) . |
| Bekijk in Browser | | Opent je browser naar de pagina van de asset. |
| Installeer  / Bijwerken  / Rapporteer | | Toepasbaar alleen voor Plugin  assets. Installeert, werkt bij of rapporteert de plugin, respectievelijk. |

## [Zoekopdracht taal](#zoekopdracht-taal)[](#zoekopdracht-taal)

Gebruik de zoekopdracht taal om te verfijnen hoe je assets in je Asset Manager inventaris vindt. Je kunt zoekwoorden, operatoren en tags combineren om resultaten te filteren, prioriteren of uit te sluiten.

Bij het combineren van meerdere functies worden zoektermen in de volgende volgorde verwerkt (hoogste naar laagste prioriteit): Exacte zoekopdracht → Uitsluitingen → Optionele termen → Asset ID tag → Gemaakt voor → Gemaakt na → Geüpdatet voor → Geüpdatet na → Maker naam → Maker ID → Groep naam → Groep ID → Numerieke asset ID → Audio type.

##### Query functies

De volgende functies kunnen in een enkele query worden gecombineerd:

| Functie | | Syntax | | Hoe het werkt |
| Exacte zoekopdracht | | "..." | |

Komt een zin exact overeen. Exacte overeenkomsten hebben de hoogste prioriteit en omzeilen andere tagverwerking.
 Gebruik aanhalingstekens om te zoeken naar tekst die eruitziet als een tag (bijvoorbeeld, "asset_id:123" ). Je kunt geciteerde zinnen mengen met reguliere termen en meerdere geciteerde zinnen in één query opnemen.

 |
| Uitsluitingen | | -term
exclude:term | |

Sluit resultaten uit die specifieke termen bevatten.
 Je kunt meerdere -  voorvoegsels en exclude  tags in dezelfde query gebruiken, of beide syntaxes mengen.

 |
| Optionele termen | | term?
term!
optional:term | |

Standaard zijn alle termen vereist. Optionele termen verhogen de overeenkomende resultaten zonder resultaten uit te sluiten die ze niet bevatten.
 Je kunt ? , ! , of de optional  tag gebruiken, en deze syntaxes mengen.

 |
| Asset ID zoekopdracht | | asset_id:123456
assetId:123456
123456 | |

Pinned overeenkomende assets naar de top van de resultaten.
 Een op zichzelf staand nummer wordt behandeld als een asset ID als het overeenkomt. Meerdere ID's worden ondersteund en worden automatisch samengevoegd.

 |
| Datum filters | | created_before
created_after
updated_before
updated_after
 | |

Filter resultaten op basis van creatie- of update datum.
 Data gebruiken het Amerikaanse formaat (MM/DD/JJJJ) en moeten in haakjes worden geplaatst als ze spaties bevatten. Natuurlijke taaldata (bijvoorbeeld, "gisteren") worden niet ondersteund.
 Elke tag ondersteunt ook een camelCase alternatief: createdBefore , createdAfter , updatedBefore , updatedAfter .

 |
| Maker filters | | creator_name
creator_id
group_name
group_id | |

Filter resultaten op basis van de maker gebruiker of maker groep op basis van hun naam of ID. Wanneer meerdere maker of groep filters worden opgegeven, worden resultaten die overeenkomen met een van hen opgenomen.
 Elke tag ondersteunt ook een camelCase alternatief: creatorName , creatorId , groupName , groupId .
 Namen die spaties bevatten moeten in haakjes worden geplaatst (bijvoorbeeld, group_name:[Groep Met Spatie] ). Als een opgegeven naam of ID ongeldig is, wordt alleen die specifieke filter genegeerd; andere geldige maker of groep filters in dezelfde query worden nog steeds toegepast.

 |
| Audio type | | music
sfx
geluidseffecten | |

Filter audio assets op type. Om resultaten te beperken tot een specifiek audiotype, voeg het type aan het einde van je query toe.
 Om naar het letterlijke woord te zoeken in plaats van te filteren, plaats het woord tussen aanhalingstekens.

 |

##### Tags

Tags wijzigen hoe de zoekopdracht werkt, maar worden zelf niet behandeld als zoektermen. Ze filteren of rangschikken alleen je resultaten. Als een tag een typfout of een ongeldige datum heeft, wordt deze behandeld als een reguliere zoekterm.

Tags kunnen de formaten tag:value  of tag=value  gebruiken, en zijn niet hoofdlettergevoelig.

Sommige tags accepteren meerdere waarden wanneer je haakjes gebruikt. Bijvoorbeeld, exclude:[roestig, gebroken]  en asset_id:[123, 456] .

##### Datumformaten

Datumfilters ondersteunen de volgende formaten:

| Formaat | | Voorbeeld |
| ISO 8601 | | 2026-03-10 |
| ISO met tijd | | 2026-03-10T14:30:00Z |
| Amerikaans formaat | | 03/10/2026 |
| Lang formaat (vereist haakjes) | | [10 maart 2026] |
| Met tijd (vereist haakjes) | | [03/10/2026 14:30] |

##### Voorbeeld zoekopdrachten

-

"houten kist" asset_id:99887766 created_after:2023-06-01 -beschadigd optional:geverfd : Komt exact overeen met "houten kist", pin een specifieke asset op ID, filter op datum, sluit "beschadigd" uit, en rangschik "geverfd" resultaten hoger.

-

explosie sfx -loop created_before:[31 december 2023] : Filter geluidseffecten met de naam "explosie", sluit loopvarianten uit, en beperkt de resultaten op datum.

-

125447393891114 zwaard gloeiend? -roestig : Pin een specifieke asset op ID, zoek naar "zwaard", verhoog "gloeiend", en sluit "roestig" uit.

-

boom creator_name:bouwmeester group_id:9876543 : Zoek naar "boom", gefilterd op assets van maker "bouwmeester" of de groep met ID 9876543.

-

zwaard creator_id:1000001,2000002 group_name:[Studio Bouwers] : Zoek naar "zwaard", gefilterd op assets van makers met ID's 1000001 of 2000002, of de groep "Studio Bouwers".

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
