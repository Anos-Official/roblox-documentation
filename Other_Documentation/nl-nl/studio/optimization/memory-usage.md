<!-- Source: https://create.roblox.com/docs/nl-nl/studio/optimization/memory-usage -->

Geheugengebruik | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Ontwikkelaarsforum](/docs/nl-nl/studio/developer-console)

# Geheugengebruik

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Elke bouw- en scriptcomponent die je aan je game toevoegt, verbruikt geheugen. Wanneer het geheugengebruik de limieten van de engine bereikt, kan het apparaat of de server van de gebruiker crashen, dus je moet het gebruik actief monitoren.

De Ontwikkelaarsconsole  biedt twee tools voor het monitoren van geheugengebruik:

-

[Geheugen](#geheugen)  — Bekijk het realtime geheugengebruik per gebruikscategorie, inclusief je aangepaste componenten en de interne processen van de engine.

-

[Luau-heap](#luau-heap)  — Maak snapshots van heapgeheugen, wat verwijst naar de geheugentoewijzing van je scripts. Deze tool biedt verschillende weergaven om je te helpen bij het identificeren van de huidige geheugentoewijzing en problemen vanuit verschillende perspectieven, zoals objecttypen en engineklassen. Het stelt je ook in staat om meerdere snapshots te maken om verschillen in geheugengebruik in de loop van de tijd te vergelijken.

Je kunt de console openen tijdens een test- of live game-sessie met een van de volgende manieren:

-

Druk op F9 .

-

Typ /console  in de chat.

-

Gebruik het in-game menu:

1.

Open het in-game Roblox Menu .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Roblox-Menu-Button.png)

2.

Selecteer het tabblad Instellingen .

3.

Scroll naar beneden naar Ontwikkelaarsconsole  en klik op Openen .

## [Geheugen](#geheugen)[](#geheugen)

De Geheugen  tool categoriseert en toont het realtime geheugengebruik. Het toont het geheugengebruik in MB van elke categorie en genereert een grafiek over de verandering in gebruik in de loop van de tijd.

Om geheugentoewijzing te bekijken:

1.

Open de Ontwikkelaarsconsole .

2.

Vouw het dropdownmenu voor tools uit om Geheugen  te selecteren.

 ![Dropdownmenu van alle tools in de Ontwikkelaarsconsole met de optie Geheugen gemarkeerd voor selectie.](https://prod.docsiteassets.roblox.com/assets/studio/console/Memory-Open.png)

3.

Vouw het dropdownmenu voor client-server uit om Client  of Server  te selecteren.

4.

Blader door de geheugengebruikcategorieën en items. Als je het gebruik in de loop van de tijd wilt zien, vouw dan de categorie uit om een grafiek weer te geven.

-

CoreMemory  — Geheugengebruik door de kernbouwprocessen van de engine, inclusief netwerken, avatars en GUI-elementen waar je geen directe controle over hebt.

-

PlaceMemory  — Geheugengebruik op basis van hoe je je game bouwt, inclusief modellen, terrein, onderdelen, scripts en alle andere aangepaste elementen die je aan je game toevoegt.

Referentie PlaceMemory

| Categorie | | Beschrijving |
| --- | --- |
| HttpCache | | Assets (afbeeldingen, meshes, enz.) geladen van Roblox-servers en nu in een cache in het geheugen opgeslagen. |
| Instances | | [Instances](/docs/nl-nl/reference/engine/classes/Instance)  in de plaats. |
| Signals | | Signalen die tussen instanties worden geactiveerd (een gebeurtenis die op de ene instantie wordt geactiveerd om een gebeurtenis op een andere instantie te triggeren). |
| LuaHeap | | Heapgeheugen voor zowel kernscripts (scripts die met de Roblox-client worden meegeleverd) als aangepaste scripts. |
| Script | | Luau-scripts. |
| PhysicsCollision | | Botsgegevens voor fysicasimulaties. |
| PhysicsParts | | Fysische geometrie en kinetiek. |
| GraphicsSolidModels | | Grafische gegevens om solide modellen weer te geven. |
| GraphicsMeshParts | | Grafische gegevens voor [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten. |
| GraphicsParticles | | Grafische gegevens voor deeltjesystemen. |
| GraphicsParts | | Grafische gegevens voor onderdelen. |
| GraphicsSpatialHash | | Algemene rendering. |
| GraphicsTerrain | | Grafische gegevens voor terrein. |
| GraphicsTexture | | Textuurgeheugen. |
| GraphicsTextureCharacter | | Textuurgeheugen voor personages. |
| Sounds | | Geluiden in het geheugen. |
| StreamingSounds | | Streaminggeluiden. |
| TerrainVoxels | | Terraingeluiden. |
| TerrainPhysics | | Terreinfysica. |
| Gui | | Geheugen gebruikt door veelvoorkomende GUI-elementen. |
| Animation | | Geheugen gebruikt voor animatiedata, zoals poses en [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence)  gecachte gegevens voor avataranimaties. |
| Navigation | | Geheugen gebruikt door ondersteunende structuren voor [PathfindingService](/docs/nl-nl/reference/engine/classes/PathfindingService) . |

-

UntrackedMemory  — Geheugentoewijzingen die het systeem niet gemakkelijk aan een specifieke bron kan toeschrijven.

-

PlaceScriptMemory  — Geheugengebruik van je scripts met inzichten in hoe individuele scripts en aangepaste geheugentags bijdragen aan het totale geheugengebruik.

-

CoreScriptMemory  — Geheugengebruik door interne enginescripts waar je geen directe controle over hebt.

Onder deze categorieën zijn PlaceMemory  en PlaceScriptMemory  de belangrijkste voor prestatieoptimalisatie, omdat ze je helpen begrijpen hoe je bouw- en scriptkeuzes het geheugengebruik beïnvloeden en potentiële gebieden voor optimalisatie. Voor meer inzichten in PlaceScriptMemory , gebruik de [Luau-heap](#luau-heap)  tool om snapshots te maken en de geheugentoewijzing te analyseren op basis van verschillende metrics.

Voor meer informatie over veelvoorkomende problemen met geheugengebruik en best practices, zie [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization/improve#memory-usage) .

## [Luau-heap](#luau-heap)[](#luau-heap)

De Luau-heap  tool stelt je in staat om snapshots te maken van de huidige toewijzing van heapgeheugen, wat verwijst naar het geheugen dat Luau-scripts gebruiken om variabelen, tabellen, functies en andere runtime-gegevensstructuren op te slaan. Deze tool biedt verschillende weergaven om je te helpen bij het identificeren van problemen vanuit verschillende perspectieven, zoals objecttypen en engineklassen. Het stelt je ook in staat om meerdere snapshots te maken om verschillen in geheugengebruik in de loop van de tijd te vergelijken.

### [Snapshots maken](#snapshots-maken)[](#snapshots-maken)

Om een snapshot van je geheugentoewijzing te maken:

1.

Open de Ontwikkelaarsconsole .

2.

Vouw het dropdownmenu voor tools uit om LuauHeap  te selecteren.

 ![Dropdownmenu van alle tools in de Ontwikkelaarsconsole met de optie LuauHeap gemarkeerd voor selectie.](https://prod.docsiteassets.roblox.com/assets/studio/console/LuauHeap-Open.png)

3.

Vouw het dropdownmenu voor client-server uit om Client  of Server  te selecteren.

4.

Klik op de knop Snapshot maken .

### [Geheugengebruik analyseren](#geheugengebruik-analyseren)[](#geheugengebruik-analyseren)

De tool biedt veel weergaven van Luau-geheugengebruik:

-

Grafiek  — Toont een geaggregeerde geheugengebruikboom, waarbij elke knoop een object met toegewezen geheugen vertegenwoordigt.

-

Objecttags  — Toont geheugengroottes en -aantallen op basis van runtime-typen, zoals function , table  en thread .

-

Geheugencategorieën  — Toont geheugengroottes en -aantallen op basis van door de engine toegewezen geheugencategorieën. De engine wijst een geheugencategorie toe aan een object op het moment van toewijzing.

-

Objectklassen  — Toont geheugengroottes en -aantallen op basis van engineklassen die je scripts gebruiken en hun instanties opslaan, zoals EnumItem , Animation , CFrame . Kritisch is dat deze weergave geen geheugengebruik binnen de engine zelf toont, alleen de Luau VM.

-

Unieke referenties  en Ongeparented instanties  — Toont aantallen en totale aantallen instanties voor unieke referenties  of alle overige referenties  die geen ouder in het datamodel hebben en alleen bereikbaar zijn via scripts. Toont ook alle paden die het instantieobject vastpinnen.

#### [Grafiek](#grafiek)[](#grafiek)

De Grafiek  weergave is de meest gedetailleerde en complexe weergave onder alle Luau-heapweergaven. Het toont een geaggregeerde geheugengebruikboom waarbij elke knoop een object met toegewezen geheugen vertegenwoordigt. De boom toont hoe objecten met elkaar verbonden zijn en afgeleid de kortste weg tussen objectreferenties. Het heeft de volgende kolommen van geheugengrootte:

-

Grootte — Het eigen geheugengebruik plus het geheugengebruik door inhoud binnen de gegevensstructuur.

-

Eigen — Het geheugen dat direct is toegewezen voor de gegevensstructuur zelf, exclusief het geheugengebruik door enige inhoud die het bevat.

De grafiekweergave toont elementen kleiner dan 2 KB als een enkele …  knoop.

 ![Een voorbeeld van de Grafiekweergave](https://prod.docsiteassets.roblox.com/assets/studio/console/Graph-View.jpeg)

De wortel van de boomgrafiek is registry , die alle engine- en Luau-referenties opslaat, zoals functies die zijn verbonden met signalen of de taakbibliotheek, tabellen die door modulescripts worden geretourneerd, en globale functies, tabellen en klassen. Het heeft meestal de volgende veelvoorkomende vermeldingen als ouder:

-

Module @Path.To.Module  is de tabel die door een modulescript wordt geretourneerd.

-

name:123 =Path.To.Module  is een functie binnen een specifiek script. Anonieme functies hebben geen namen. De bovenste knoop verwijst vaak naar de globale scriptfunctie. Voorbeeld: :1= Workspace.[Username].Animate .

-

upvalue  is een referentie voor gevangen functies. Zie [Capture local scope](/docs/nl-nl/luau/scope#vangen)  voor meer informatie.

-

env  verwijst naar de omgeving van een functie. In de meeste gevallen is het een tabel die de globale scope van een script vertegenwoordigt.

-

globals  verwijst naar de omgeving van een thread.

-

[key]  vertegenwoordigt objecten die als tabelsleutels dienen.

-

array  vertegenwoordigt een array.

-

stack  verwijst naar de array die alle functie-lokalen opslaat.

-

constants  vertegenwoordigt alle constante waarden die functies gebruiken.

#### [Geheugencategorieën](#geheugencategorieën)[](#geheugencategorieën)

De Geheugencategorieën  weergave toont geheugengroottes en -aantallen op basis van geheugencategorieën, die de engine aan objecten toewijst op het moment van toewijzing. Standaard heeft de geheugencategorie dezelfde naam als het script, of je kunt aangepaste geheugencategorienamen toewijzen met de functie debug.setmemorycategory .

#### [Unieke referenties en ongeparented instanties](#unieke-referenties-en-ongeparented-instanties)[](#unieke-referenties-en-ongeparented-instanties)

De weergaven Unieke Referenties  en Ongeparented Instanties  zijn gerelateerd. Beide tonen het geheugengebruik van instanties die geen ouder in het datamodel hebben en alleen bereikbaar zijn via scripts, samen met alle paden die het instantieobject vastpinnen. Als een instantie alleen binnen Luau-scripts wordt gerefereerd, verschijnt deze onder Unieke Referenties . Anders wordt deze ook gebruikt door Roblox-systemen en verschijnt deze onder Ongeparented Instanties . Beide weergaven tonen twee metrics:

-

Aantal  — Het aantal instanties met dezelfde naam die bereikbaar zijn vanaf hetzelfde pad, zoals meerdere instanties genaamd Dragon  in dezelfde tabel.

-

Totale Instanties  — Het totale aantal objecten binnen die wortels, zoals alle onderdelen, scripts en geluidsobjecten die een Dragon  instantie construeren.

 ![Een voorbeeld van de Unieke Referentie weergave](https://prod.docsiteassets.roblox.com/assets/studio/console/Unique-Reference-View.jpeg)

Deze weergaven zijn nuttig voor het identificeren van onnodige verbonden instanties, die je moet ontkoppelen wanneer je ze niet langer nodig hebt. Als je veel onverwachte instanties in deze weergave ziet, controleer dan de paden die ze vasthouden en evalueer of ze nodig zijn.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
