<!-- Source: https://create.roblox.com/docs/nl-nl/studio/explorer -->

Verkenner venster | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Verkenner venster

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Verkenner  venster, toegankelijk via het Venster  menu of de Start  tab werkbalk in Studio, toont een hiërarchische lijst van elke instantie binnen een spel. Op het hoogste niveau van de hiërarchie bevinden zich de services; [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , bijvoorbeeld, is waar zichtbare 3D-inhoud zoals [onderdelen](/docs/nl-nl/parts)  wordt opgeslagen.

 ![Verkenner gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Explorer.png)

## [Ouder-kind hiërarchie](#ouder-kind-hiërarchie)[](#ouder-kind-hiërarchie)

Alle kinderen van een ouderobject verschijnen onder zijn tak wanneer deze is uitgeklapt. Klik op de pijl naast een oudertak — of druk op de → / ←  pijltoetsen wanneer een ouder is geselecteerd — om alleen die tak uit te vouwen of in te klappen.

![Verkenner hiërarchie die Camera, Terrain en SignModel toont als kinderen van Workspace; Board en Post als kinderen van SignModel](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Parent-Child-Hierarchy.png)

![Alleen de bovenste ouder is uitgeklapt met een klik](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Branch-Expanded.png)

Om alle  takken binnen een multi-geneste hiërarchie uit te vouwen of in te klappen, houd Shift  ingedrukt terwijl je op de uitvouw-/inklappijl klikt.

Om de ouder van een of meer kinderen te veranderen (herstructureren), sleep je ze eenvoudig naar de nieuwe ouder.

 ![Een object over een ander slepen om het te herstructureren](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Reparent-Object.png)

## [Objectinvoeging](#objectinvoeging)[](#objectinvoeging)

Terwijl primitieve [onderdelen](/docs/nl-nl/parts)  kunnen worden [ingevoegd](/docs/nl-nl/parts#onderdelen-invoegen)  vanuit de werkbalken van de Start  of Model  tab, kun je kiezen uit een volledige reeks objecten door over de bedoelde ouder te zweven en op de ⊕ knop te klikken (sneltoets van Ctrl I  op Windows of ⌘ I  op Mac).

 ![Over het Workspace-object zweven om de invoegknop te onthullen](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Add-Object.png)

Je kunt het invoeggedrag verder aanpassen door op de ⋯  knop rechts van het zoekveld te klikken:

 ![Extra aanpassingsopties voor het invoegproces](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Insert-Object-Options.png)

| Optie | | Beschrijving |
| --- | --- |
| Namen voor nieuwe instanties verhogen | | Wanneer ingeschakeld, zullen ingevoegde/geplakte/gekopieerde instanties van hetzelfde type genummerde namen hebben ter differentiatie. |
| Hiërarchie uitbreiden bij selectie | | Wanneer ingeschakeld, zal het invoegen/plakken van een instantie of het selecteren van een object in de [3D viewport](/docs/nl-nl/studio/overview#3d-viewport)  de Verkenner  hiërarchie uitbreiden om die instantie te onthullen. Wanneer uitgeschakeld, zal de bovenste ouder binnen de hiërarchie worden gemarkeerd, maar deze zal niet uitbreiden om de geselecteerde instantie te onthullen. |

Om de hiërarchie netter te houden, zijn services zoals [VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)  standaard verborgen. Je kunt verborgen services tonen door met de rechtermuisknop in het venster te klikken en Toon Services…  te selecteren in het contextmenu. Evenzo kun je een zichtbare service verbergen door er met de rechtermuisknop op te klikken en Verberg Service in Verkenner  te selecteren.

## [Dupliceer en plak](#dupliceer-en-plak)[](#dupliceer-en-plak)

Objecten kunnen snel worden gedupliceerd in dezelfde tak, terwijl items die naar het klembord zijn gekopieerd, kunnen worden geplakt in de bovenste [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  tak of rechtstreeks in een of meer bestaande ouders.

| Actie | | Windows | | Mac | | Beschrijving |
| Dupliceer | | Ctrl D | | ⌘ D | | Dupliceert de geselecteerde objecten in dezelfde tak. |
| Plak | | Ctrl V | | ⌘ V | | Plakt de inhoud van het klembord in de bovenste [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  tak. |
| Plak In | | Ctrl Shift V | | ⌘ Shift V | | Plakt de inhoud van het klembord in het geselecteerde object(en). Deze actie gebruiken op meerdere geselecteerde objecten is een handige manier om dezelfde klemborditems in meerdere ouders te plakken, zoals een gemeenschappelijke [Texture](/docs/nl-nl/reference/engine/classes/Texture)  in verschillende [Parts](/docs/nl-nl/reference/engine/classes/Part) . |

Bij het plakken van 3D-objecten die naar het klembord zijn gekopieerd, kun je hun oorspronkelijke [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  positie behouden door met de rechtermuisknop op de doelouderinstantie in de hiërarchie te klikken en Plak Opties  ⟩ Plak In Op Oorspronkelijke Locatie  te selecteren.

## [Contextuele opties](#contextuele-opties)[](#contextuele-opties)

Met de rechtermuisknop op een instantie klikken opent het optiesmenu, contextueel aangepast voor het objecttype. Bijvoorbeeld, met de rechtermuisknop op een [Model](/docs/nl-nl/reference/engine/classes/Model)  klikken onthult standaardopties zoals Kopieer  en Dupliceer , en ook opties specifiek voor [Models](/docs/nl-nl/reference/engine/classes/Model)  zoals Groeperen . In tegenstelling hiermee onthult met de rechtermuisknop op een service zoals [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  een beknopter menu van acties die geldig zijn voor services.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Context-Menu-Model.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Context-Menu-Service.png)

## [Maporganisatie](#maporganisatie)[](#maporganisatie)

Net als mappen op een computer is het [Folder](/docs/nl-nl/reference/engine/classes/Folder)  object een nuttige manier om objecten te organiseren. Als je bijvoorbeeld alle omgevingsgeluidsassets op een logische plaats wilt opslaan, kun je een map maken en meerdere [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  objecten erin plaatsen.

 ![Meerdere Geluid-objecten gegroepeerd binnen een Map-object](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Folder-Children.png)

Je kunt objecten als volgt in mappen organiseren:

-

Maak een [Folder](/docs/nl-nl/reference/engine/classes/Folder)  instantie aan via een standaard [invoeg](#object-invoeging)  methode, en sleep vervolgens bestaande objecten erin.

-

Selecteer meerdere objecten, klik met de rechtermuisknop op ze en selecteer Groep Als Een Map  in het contextmenu (sneltoets van Alt Ctrl G  op Windows of ⌥ ⌘ G  op Mac).

## [Zoekmethoden](#zoekmethoden)[](#zoekmethoden)

Via de zoek  invoer nabij de bovenkant van het venster kun je instanties vinden op basis van [naam](#naamzoektocht) , [eigenschap](#eigenschapszoektocht) , klasse/subklasse/tag [op maat](#op-maat-gemaakte-zoekopdracht)  queries, en [afstamming](#afstammingszoektocht)  queries. Je kunt ook [parameters combineren](#gecombineerd)  voor geavanceerde logische zoekopdrachten. Toegang tot deze invoer krijg je snel door Ctrl Shift X  (Windows) of ⌘ Shift X  (Mac) in te drukken.

 ![Voorbeeld zoekopdracht en zoekopties](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Search-Diagram.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Navigeer omhoog en omlaag door zoekresultaten

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Selecteer alle zoekresultaten (Ctrl A  op Windows of ⌘ A  op Mac)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Vernieuw zoekresultaten

Een naam is een reeks tekens die alfanumeriek, _ , - , of .  zijn. In al deze zoekmethoden, wees voorzichtig bij het zoeken naar instanties waarvan de namen spaties bevatten, aangezien de zoeklogica spaties kan verwarren voor een [samengevoegde zoekopdracht](#gecombineerd) . Bij het zoeken naar namen met spaties, moet je de volledige naam omringen met dubbele aanhalingstekens, bijvoorbeeld tag:"Light Source"  om te zoeken op de volledige [tag](/docs/nl-nl/studio/properties#instantie-tags)  naam van Light Source .

### [Naamzoektocht](#naamzoektocht)[](#naamzoektocht)

Het typen van een basisreeks levert naam  overeenkomende instanties op, hoofdletterongevoelig. Bijvoorbeeld, zoeken op het trefwoord script  vindt alle instanties die het bevatten, zoals ServerScriptService  en LocalScript .

 ![Objecten gefilterd op zoekopdracht van 'script'](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Search-By-Name.png)

### [Eigenschapszoektocht](#eigenschapszoektocht)[](#eigenschapszoektocht)

Je kunt filteren op eigenschap gelijkheid of waarde vergelijkingen. De meeste eigenschappen worden ondersteund, het werkt met gedeeltelijke overeenkomsten, negeert spaties en is hoofdletterongevoelig.

Gelijkheid Waarde vergelijkingen Individuele Velden Volledige Eenheden

Eigenschap gelijkheid  wordt doorzocht via de operatoren =  of == .

| Voorbeeld | | Resultaat |
| ClassName = Decal | | Alle instanties van klasse [Decal](/docs/nl-nl/reference/engine/classes/Decal) . |
| Locked = true | | [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  met [Locked](/docs/nl-nl/reference/engine/classes/BasePart#Locked)  ingesteld op true . |
| Material == plas | | [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  met [Material](/docs/nl-nl/reference/engine/classes/BasePart#Material)  van ofwel [Plastic](/docs/nl-nl/reference/engine/enums/Material)  of [SmoothPlastic](/docs/nl-nl/reference/engine/enums/Material) . |

### [Op maat gemaakte zoekopdracht](#op-maat-gemaakte-zoekopdracht)[](#op-maat-gemaakte-zoekopdracht)

Klassen, en subklassen, en tags worden doorzocht via verschillende op maat  queries, waaronder:

-

is:[Class]  vindt alles dat van klasse  [Class]  is. Bijvoorbeeld, is:Part  vindt alles dat een [Part](/docs/nl-nl/reference/engine/classes/Part)  is.

-

is:[SubClass]  vindt alles dat een subklasse  van [SubClass]  is. Bijvoorbeeld, is:BasePart  vindt alles dat een subklasse van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  is, zoals [Part](/docs/nl-nl/reference/engine/classes/Part)  en [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) .

-

tag:[TagName]  vindt alles met een [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  tag van [TagName] . Bijvoorbeeld, tag:LightSource  vindt alles dat getagd is met LightSource . Je kunt tags toevoegen via de [Tags](/docs/nl-nl/studio/properties#instantie-tags)  sectie van de eigenschappen van een instantie en tag namen zullen automatisch aanvullen.

### [Afstammingszoektocht](#afstammingszoektocht)[](#afstammingszoektocht)

Je kunt binnen een specifieke scope zoeken met de .  operator, operatoren aan elkaar koppelen voor zeer specifieke zoekopdrachten, of *  gebruiken als een wildcard.

-

[Parent].[Child]  vindt genaamde kinderen binnen een genaamde ouder. Bijvoorbeeld, workspace.Model  vindt instanties genaamd Model  binnen instanties genaamd workspace , vergelijkbaar met scripting.

-

Het aan elkaar koppelen van .  operatoren voegt specificiteit toe. Bijvoorbeeld, Animals.Dog.Tail  vindt objecten genaamd Tail  binnen Dog  binnen Animals .

-

*  fungeert als een wildcard, bijvoorbeeld:

| Voorbeeld | | Resultaat |
| Cart.* | | Alle kinderen van een object genaamd Cart . |
| Cart.Barrier.* | | Alle kinderen van Barrier , zelf een kind van Cart . |
| Cart.*.* | | Alle kleinkinderen van Cart , exclusief directe kinderen van Cart . |
| Cart.*.Trim | | Alle kleinkinderen van Cart  die Trim  heten. |

-

[Parent].**  vindt alle afstammelingen van een ouder. Bijvoorbeeld, CarModel.**  vindt alle afstammelingen van CarModel .

### [Gecombineerd](#gecombineerd)[](#gecombineerd)

Voor geavanceerde logische zoekopdrachten kun je queries combineren door middel van unies en groepering.

-

Meerdere queries gescheiden door spaties of and  werken op alle  voorwaarden.

| Voorbeeld | | Resultaat |
| Anchored=true CanCollide=true | | Elke [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die verankerd is en kan botsen. |
| Cart.*.* Transparency < 1 | | Alle kleinkinderen van Cart  die niet volledig transparant zijn. |
| Anchored=false and CanCollide=false | | Elke [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die niet verankerd is en niet kan botsen. |

-

De or  conjunctie werkt net als de or  operator in code. Groepen binnen haakjes, samengevoegd door or , vinden alles binnen meerdere gecombineerde queries.

| Voorbeeld | | Resultaat |
| Cat or Dog | | Alles dat Cat  of Dog  in zijn naam heeft. |
| (Anchored=true CanCollide=true) or (Anchored=false CanCollide=false) | | Elke [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die ofwel verankerd is en kan botsen, of  niet verankerd is en niet kan botsen. |

## [Selectiemethoden](#selectiemethoden)[](#selectiemethoden)

Binnen een [gezochte](#zoekmethoden)  hiërarchie, gedragen bepaalde sneltoetsen en muisoperaties zich anders dan binnen een niet-gezochte hiërarchie.

### [Selecteer alles](#selecteer-alles)[](#selecteer-alles)

Binnen een niet-gezochte hiërarchie selecteert het indrukken van Ctrl A  op Windows of ⌘ A  op Mac alle instanties. Binnen een [gezochte](#zoekmethoden)  hiërarchie selecteert dezelfde sneltoets of de selecteer alles  knop alleen de objecten die overeenkomen met de query, bijvoorbeeld alle objecten die overeenkomen met Board  in een hiërarchie die is doorzocht naar board .

 ![Afbeelding die toont hoe alleen overeenkomende objecten worden geselecteerd in een gezochte hiërarchie met behulp van de Select All sneltoets](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Select-All-Searched.png)

### [Shift-selectie](#shift-selectie)[](#shift-selectie)

Klikken op een object en Shift -klikken op een ander object gedraagt zich anders binnen een niet-gezochte hiërarchie versus een [gezochte](#zoekmethoden)  hiërarchie.

Niet-gezochte Hiërarchie Gezochte Hiërarchie

Binnen een niet-gezochte hiërarchie selecteert Shift -klikken op twee objecten op hetzelfde hiërarchische niveau beide en elk object ertussen dat ook op hetzelfde hiërarchische niveau is, zoals weergegeven in afbeelding 🅰  waar LeftFoot  aanvankelijk is aangeklikt, LeftLowerArm  is Shift -geklikt, en LeftHand  op hetzelfde hiërarchische niveau is ook geselecteerd. Het dupliceren, kopiëren of plakken van de geselecteerde objecten resulteert in een diepe kopie van die objecten en  alle kinderen.

Als het eerste Shift -geklikte object en het tweede Shift -geklikte object zich op verschillende  hiërarchische niveaus bevinden, worden alle objecten ertussen geselecteerd, zoals weergegeven in afbeelding 🅱  waar LeftFoot  aanvankelijk is aangeklikt, LeftHand  is Shift -geklikt, en alles ertussen is ook geselecteerd.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Shift-Click-Non-Searched-A.png) Shift -klik op hetzelfde hiërarchische niveau

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Shift-Click-Non-Searched-B.png) Shift -klik op een ander hiërarchisch niveau

### [Sleepselectie](#sleepselectie)[](#sleepselectie)

Klikken en slepen vanuit een leeg gebied van het venster initieert een selectiekader. Binnen een niet-gezochte hiërarchie wordt alles binnen het kader geselecteerd. Binnen een [gezochte](#zoekmethoden)  hiërarchie worden alleen de objecten die overeenkomen met de query binnen het kader geselecteerd.

![Afbeelding die toont hoe alleen overeenkomende objecten binnen het selectiekader worden geselecteerd binnen een gezochte hiërarchie](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Drag-Select-Searched.png)

## [Sneltoetsen](#sneltoetsen)[](#sneltoetsen)

| Sneltoets | | Beschrijving |
| → | | Met een ingeklapte tak geselecteerd, vouwt die tak uit. Wanneer opnieuw ingedrukt, selecteert het de eerste kind  direct onder de ouderknoop. |
| ← | | Met een kind van een tak geselecteerd, verplaatst de selectie terug naar de ouderknoop. Wanneer opnieuw ingedrukt, klapt de hele tak in. |
| Home | | Selecteert het bovenste object in de hiërarchie ([Workspace](/docs/nl-nl/reference/engine/classes/Workspace) ). |
| Einde | | Selecteert het onderste object in de hiërarchie. |
| PageUp | | Selecteert het object in de hiërarchie dat boven het bovenste zichtbare  hiërarchische item staat. |
| PageDown | | Selecteert het object in de hiërarchie dat onder het onderste zichtbare  hiërarchische item staat. |
| Ctrl Shift X
⌘ Shift X | | Spring naar de [zoekinvoer](#zoekmethoden)  nabij de bovenkant van het venster. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
