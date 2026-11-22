<!-- Source: https://create.roblox.com/docs/nl-nl/studio/script-editor -->

Scripteditor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Scripteditor

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Scripteditor  in Studio is het primaire hulpmiddel voor scripting op Roblox. Het is een zelfverbeterende omgeving die je kan helpen om impactvolle code te schrijven, je ontwikkelingstijd te verkorten en je games te itereren. Het kan je scriptingervaring verbeteren door:

-

De syntaxis in je code te formatteren en te markeren.

-

Manieren aan te bieden om [autocompletion](#autocomplete-functies)  van zinnen in je code te krijgen terwijl je typt.

-

Je te helpen [navigeren in code](#code-navigatie)  door naar variabele- en functiedeclaraties te springen.

-

Je te helpen [zoeken en vervangen](#zoeken-en-vervangen)  van code in open scripts of alle scripts.

-

[Realtime feedback](#realtime-feedback)  te geven over de kwaliteit en prestaties van je code.

De Scripteditor ondersteunt alle soorten [scripts](/docs/nl-nl/scripting)  en opent automatisch wanneer je een nieuw script aanmaakt of dubbelklikt op een bestaand script in het [Explorer](/docs/nl-nl/studio/explorer)  venster.

Je kunt de [Scripteditor](#editor-instellingen)  aanpassen aan je voorkeuren en workflows, inclusief lettertype/familie/grootte, formatteringsgedrag en kleuren voor syntaxismarkering. Je kunt ook functies zoals [autocompletion](#autocomplete-functies)  en [scriptanalyse](#scriptanalyse)  in- of uitschakelen.

## [Autocomplete-functies](#autocomplete-functies)[](#autocomplete-functies)

De autocompletion-functies van de Scripteditor genereren codegerelateerde informatie die je programmeerefficiëntie kan verbeteren, zoals:

-

Informatieve suggesties  over hoe je zinnen kunt voltooien terwijl je ze typt, die contextueel zijn voor het [datamodel](/docs/nl-nl/projects/data-model)  van het spel. Bijvoorbeeld, als je een [Model](/docs/nl-nl/reference/engine/classes/Model)  in [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  hebt genaamd RocketShip , suggereert autocompletion RocketShip  wanneer je workspace.roc  typt en geeft aan dat het een [Model](/docs/nl-nl/reference/engine/classes/Model)  is.

 ![Autocompletion toont suggesties op basis van het datamodel van het spel](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Autocomplete-Data-Model.png)

Gebruik de ↑  en ↓  toetsen om door de suggesties te bladeren, druk vervolgens op Tab  of Enter  om een suggestie te accepteren en de volledige zin in te voegen.

-

Autofill-namen  voor variabelen en functies die je declareert, waardoor je vervelende typfouten kunt vermijden.

 ![Autocompletion toont suggesties op basis van een eerder gedeclareerde variabele.](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Autocomplete-Variable.png)

-

Documentatie-pop-ups met codevoorbeelden  die vergelijkbaar zijn met die op de [Engine API Reference](/docs/nl-nl/reference/engine) , die je context geven over het gebruik van de API.

 ![Autocompletion toont suggesties op basis van een Roblox Engine API.](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Autocomplete-API.png)

-

On-hover tooltips  die je kunt aanpassen met je eigen gedefinieerde documentatie. Plaats een [blockcommentaar](/docs/nl-nl/luau/comments#blok-opmerkingen)  direct voor een functie, variabele of andere declaratie, en de Scripteditor toont die opmerking als een tooltip wanneer je later over de naam zweeft. Dit werkt ook wanneer de declaratie binnen een type-expressie verschijnt, zoals typeof() :

```

export type Icon = {

	new: typeof(--[[Construeert een leeg pictogram.]] function(): Icon

		return (nil :: any) :: Icon

	end),

}

```

 ![Autocompletion toont aangepaste documentatie.](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Autocomplete-CustomDocs.png)

-

On-hover scriptanalyse-diagnostiek  met informatie die je kunt gebruiken om fouten op te lossen.

 ![Autocompletion toont diagnostische informatie.](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Autocomplete-Diagnostics.png)

-

Functiesignaturen  wanneer je een argument typt, waardoor je een referentie krijgt voor de parameters en retourwaarden.

 ![Autocompletion toont functiesignatuur](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Autocomplete-Signature.png)

## [Code-navigatie](#code-navigatie)[](#code-navigatie)

### [Ga naar declaratie](#ga-naar-declaratie)[](#ga-naar-declaratie)

Je kunt naar de declaratie van een functie of variabele springen door Ctrl  op Windows of ⌘  op Mac ingedrukt te houden terwijl je op de aanroep klikt, of door met de rechtermuisknop op de aanroep te klikken en Ga naar Declaratie  te selecteren.

 ![Ga naar Declaratie workflow op een gedeclareerde functie](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Go-To-Declaration.png)

### [Scriptfunctiefilter](#scriptfunctiefilter)[](#scriptfunctiefilter)

Het Scriptfunctiefilter  toont een lijst van alle functies die in een script zijn gedeclareerd. Om het te openen, druk je op Alt F  op Windows of ⌥ F  op Mac. Met de lijst open kun je door de handtekeningen van elke functie bladeren, ze filteren op naam en dubbelklikken op een functie om naar de declaratie te springen.

 ![Scriptfunctiefilter toont alle functies binnen een script](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Script-Functions-Filter.png)

## [Zoeken en vervangen](#zoeken-en-vervangen)[](#zoeken-en-vervangen)

De Zoeken/Vervangen  widget stelt je in staat om code in een open script te vinden en te vervangen. De widget ondersteunt het matchen van hoofdletters, het matchen van het hele woord en zoeken met reguliere expressies. Om het te openen, druk je op Ctrl F  op Windows of ⌘ F  op Mac.

 ![Zoeken/Vervangen widget gelabeld](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Find-Replace-Widget-Labeled.png)

Voor bredere zoekopdrachten laat het Zoek Alles / Vervang Alles  venster je toe om code te vinden/vervangen in meerdere scripts in het spel. Om het te openen, druk je op Ctrl Shift F  op Windows of ⌘ Shift F  op Mac.

## [Realtime feedback](#realtime-feedback)[](#realtime-feedback)

### [Scriptanalyse](#scriptanalyse)[](#scriptanalyse)

Het Scriptanalyse  venster, toegankelijk via de Analyse  knop in de werkbalk van het Script  tabblad van Studio, voert statische analyse uit op je scripts en toont actieve fouten en waarschuwingen. Voor meer informatie over de fouten en waarschuwingen, zie de [Luau linting](https://luau.org/lint)  documentatie.

![Script met verschillende gemarkeerde fouten](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Script-Analysis-1.png) Scriptfouten onderstreept in de Scripteditor

![Scriptanalyse venster met details over gemarkeerde fouten uit script](https://prod.docsiteassets.roblox.com/assets/studio/script-editor/Script-Analysis-2.png) Fouten uitgelegd in het Scriptanalyse venster

### [Output](#output)[](#output)

Het [Output](/docs/nl-nl/studio/output)  venster toont fouten die zijn vastgelegd tijdens het uitvoeren van scripts, berichten van de Roblox-engine, berichten van aanroepen naar print() , en fouten van aanroepen naar warn() .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Output-Window.png)

## [Code-assistent](#code-assistent)[](#code-assistent)

Code-assistent  is een functie die lijnen of functies van code suggereert terwijl je typt, waardoor je efficiënter kunt coderen en gefocust kunt blijven. Op basis van contexten uit je commentaar en code, worden suggesties op twee manieren geactiveerd:

-

Automatisch  wanneer je een paar seconden op een regel pauzeert en het AI-model voldoende context heeft voor een suggestie.

-

Handmatig  met de sneltoets Alt ∖  op Windows of ⌥ ∖  op Mac.

Druk op Tab  om een suggestie te accepteren, of negeer het door door te typen. Momenteel moet je script ten minste een paar regels code bevatten om een suggestie te activeren.

Code-assistent  helpt bij het automatiseren van basis codetaken, zodat je je kunt concentreren op creatief werk, maar het suggereert niet altijd perfecte code (zie [Beperkingen](#beperkingen) ). Het blijft jouw verantwoordelijkheid om de suggestie te beoordelen, te testen en te bepalen of de codesuggestie contextueel geschikt is.

### [Verbeter suggesties](#verbeter-suggesties)[](#verbeter-suggesties)

Om nauwkeurigere en relevantere suggesties te krijgen, is het aan te raden dat je schone coderingspraktijken volgt, ongeacht de assistentie, en:

-

Breek je code op in kleinere functies.

-

Gebruik beschrijvende scriptnamen die de algemene intentie van wat elk script doet vastleggen. Noem een script bijvoorbeeld SyncCustomSounds  in plaats van alleen Sounds .

-

Ken beschrijvende namen toe voor parameters, functies en scripts. Noem een onderdeel bijvoorbeeld GreenSphere  in plaats van simpelweg grs , of noem een functie generateSphere()  in plaats van gen() . Het gebruik van benoemde functies in plaats van anonieme functies kan ook betere hints opleveren.

-

Neem consequent goed geschreven [commentaar](/docs/nl-nl/luau/comments)  op dat de taak beschrijft die je implementeert en wat de invoer/uitvoer zou moeten zijn.

-

Overweeg om enkele voorbeeldaanroepen met verwachte resultaten in commentaar op te nemen.

-

Stel voor hoe je een probleem kunt oplossen, bijvoorbeeld -- Gebruik raycast .

-

Gebruik de exacte functie- of variabelenaam die je hebt gedefinieerd, bijvoorbeeld -- Maak 10 greenSphere-objecten  in plaats van -- Maak 10 sferen .

-

Als je een novice scripter bent, begin dan met basisprojecten zoals "maak de speler aan het springen wanneer ze het onderdeel aanraken" of gebruik de tool om kleine codesnippets te genereren die je kunt uitbreiden naarmate je kennis groeit.

### [Beperkingen](#beperkingen)[](#beperkingen)

De tool helpt bij het automatiseren van basis codetaken, maar het suggereert niet altijd perfecte code. Bekende beperkingen zijn:

-

Handmatig activeren genereert niet altijd  een suggestie.

-

Suggesties zijn machinaal geleerd uit een corpus van code en kunnen dus enkele beperkingen van de code weerspiegelen waarop ze zijn getraind. Bijvoorbeeld, suggesties gebruiken mogelijk geen nieuwere API's ten gunste van oudere API's, of ze kunnen Lua gebruiken in plaats van [Luau](/docs/nl-nl/luau) .

-

De tool kan onjuiste of misleidende informatie genereren die niet nuttig is voor jouw doel.

-

Interne filters proberen kwetsende taal te blokkeren, maar ze zijn niet allesomvattend en er is een mogelijkheid dat de tool kwetsende of bevooroordeelde informatie genereert.

-

De suggesties kunnen hetzelfde, vergelijkbaar of verschillend zijn tussen gebruikers, zelfs met dezelfde prompts. Jouw code zal echter nooit met anderen worden gedeeld.

-

De suggestie kan onvolledig zijn vanwege de beperkte lengte van de output van de leermodellen.

-

Er is een dagelijkse limiet voor het aantal suggesties en, zodra de limiet is bereikt, ontvang je geen suggesties totdat de volgende dag.

### [Codeprivacy](#codeprivacy)[](#codeprivacy)

Momenteel gebruikt Roblox geen niet-publieke gegevens om de leermodellen te trainen. De tool gebruikt alleen een klein subset van gratis marktplaatsactiva voor het afstemmen van grote taalmodellen en de subset heeft verschillende controles voor kwaliteit en veiligheidsfilters doorstaan.

Bovendien worden alle suggesties door  het AI-model gegenereerd en worden ze niet overgedragen van de ene gebruiker naar de andere. Aangezien jouw code niet wordt gebruikt voor modeltraining, zal deze niet worden voorgesteld aan andere gebruikers van Code Assist , met de enige uitzondering van code die wordt gepost naar gratis marktplaatsitems.

## [Multi-cursor](#multi-cursor)[](#multi-cursor)

De Scripteditor ondersteunt het gebruik van meerdere cursors om gelijktijdig bewerkingen uit te voeren. Je kunt cursors toevoegen op basis van je behoeften met een muisklik of sneltoets. De initiële cursor wordt de primaire cursor  genoemd en extra cursors worden secundaire cursors  genoemd.

-

Bewerking die je maakt bij de primaire cursor wordt gekopieerd naar de secundaire cursors. Elke bewerking telt als één actie, dus ongedaan maken/terugzetten van een bewerking geldt voor alle cursors.

-

Widgets zoals [autocompletion](#autocomplete-functies)  verschijnen op de primaire cursor maar niet op de secundaire cursors.

-

Alle standaard [sneltoetsen](#sneltoetsen)  voor scriptbewerking werken met multi-cursorbewerking, inclusief code-inspringen, opmerkingen in- en uitschakelen, en regels verwijderen.

De volgende tabel geeft een samenvatting van multi-cursor workflows en hun sneltoetsen.

| Opdracht | | Windows | | Mac |
| --- | --- |
| Voeg cursor toe/verwijder cursor op muislocatie | | Alt  + klik | | ⌥  + klik |
| Verwijder meest recent toegevoegde cursor | | Ctrl U | | ⌘ U |
| Voeg/wijzig cursor bij muisversleep | | Alt  + versleep | | ⌥  + versleep |
| Voeg cursor boven/beneden toe | | Ctrl Alt ↑  / Ctrl Alt ↓ | | ⌘ ⌥ ↑  / ⌘ ⌥ ↓ |
| Voeg cursor toe aan volgende overeenkomende selectie | | Ctrl D | | ⌘ D |
| Voeg cursor toe aan elke overeenkomende selectie | | Shift Alt L | | Shift ⌥ L |
| Kolom/blok selecteren | | Shift Alt  + versleep | | Shift ⌥  + versleep |
| Splits selecties in regels | | Shift Alt I | | Shift ⌥ I |

Om alle secundaire cursors te verwijderen, verlaat je de multi-cursorbewerking en keer je terug naar de primaire cursor door op Esc  te drukken.

### [Cursors toevoegen](#cursors-toevoegen)[](#cursors-toevoegen)

Je kunt cursors toevoegen met een combinatie van sneltoetsen en muisbewegingen. Cursors versmelten als ze dezelfde ruimte innemen, bijvoorbeeld als je cursors toevoegt met de pijltoetsen of alle tekens tussen cursors verwijdert.

#### [Op muislocatie](#op-muislocatie)[](#op-muislocatie)

Om een cursor op de locatie van je muispointer toe te voegen:

1.

Houd Alt  op Windows of ⌥  op Mac ingedrukt.

2.

Klik waar je de cursor wilt toevoegen.

#### [Met muisversleep](#met-muisversleep)[](#met-muisversleep)

Je kunt de muis verslepen om een cursor aan een selectie toe te voegen, een multi-regel selectie in regels te splitsen, of kolommen en blokken code/witruimte te selecteren.

Versleep selecteren Splits in regels Kolom/blok selecteren

Om een cursor aan een selectie van code toe te voegen door te verslepen:

1.

Houd Alt  op Windows of ⌥  op Mac ingedrukt.

2.

Klik en versleep je muis over de selectie van code.

#### [Boven en onder de primaire cursor](#boven-en-onder-de-primaire-cursor)[](#boven-en-onder-de-primaire-cursor)

Om een cursor direct boven of onder de primaire cursor toe te voegen:

1.

Druk en houd Ctrl Alt  op Windows of ⌘ ⌥  op Mac ingedrukt.

2.

Druk op de ↑  of ↓  pijlen.

#### [Aan overeenkomende selecties](#aan-overeenkomende-selecties)[](#aan-overeenkomende-selecties)

Je kunt cursors toevoegen aan alle overeenkomsten van een selectie of aan de volgende/vorige overeenkomst, en optioneel schakelen of overeenkomsten hoofdlettergevoelig zijn en/of alleen het hele woord matchen.

Alle overeenkomende Volgende/vorige overeenkomst Hoofdlettergevoelig of hele woord match

Om een cursor toe te voegen aan alle overeenkomsten van een geselecteerd gedeelte:

1.

Selecteer de code waarvan je overeenkomsten wilt zoeken.

2.

Druk op Shift Alt L  op Windows of Shift ⌥ L  op Mac.

### [Cursors verwijderen](#cursors-verwijderen)[](#cursors-verwijderen)

Je kunt cursors verwijderen met de volgende sneltoetsen en muisbewegingen. Alternatief kun je de multi-cursorbewerking verlaten door op Esc  te drukken.

#### [Op muislocatie](#op-muislocatie-1)[](#op-muislocatie-1)

Om een cursor te verwijderen:

1.

Druk en houd Alt  op Windows of ⌥  op Mac ingedrukt.

2.

Klik op de cursor die je wilt verwijderen.

#### [Meest recent toegevoegde](#meest-recent-toegevoegde)[](#meest-recent-toegevoegde)

Om de meest recent toegevoegde cursor te verwijderen, druk je op Ctrl U  op Windows of ⌘ U  op Mac.

### [Cursors kopiëren en plakken](#cursors-kopiëren-en-plakken)[](#cursors-kopiëren-en-plakken)

Het kopiëren van een selectie code omvat de cursors daarin. Het gedrag van de plakken hangt af van het aantal cursors bij de bron en het aantal cursors bij de bestemming:

-

Als het aantal cursors hetzelfde is, dan plakt elke gekopieerde cursor naar elke overeenkomstige bestemmingscursor.

-

Als het aantal cursors verschillend is, ontvangt elke cursor op de bestemming de gehele plak met elke gekopieerde cursor als een nieuwe regel.

### [Op-type formattering](#op-type-formattering)[](#op-type-formattering)

Drukken op enter/return zal elke cursor automatisch inspringen op de nieuwe regel ten opzichte van de vorige regel. Als de vorige regel begint met een onvolledig blok, zal de formatter proberen het te voltooien.

## [Editor-instellingen](#editor-instellingen)[](#editor-instellingen)

Veel aanpassingsopties zijn toegankelijk via het Scripteditor  tabblad van [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) . Veelvoorkomende gewijzigde opties zijn:

| Optie | | Beschrijving |
| Lettertype | | Lettertype en grootte voor code in de editor. |
| Tabbreedte | | Aantal spaties dat een Tab  inspringing vertegenwoordigt. |
| Inspringen met spaties | | Als ingeschakeld, worden spaties gelijk aan Tab Breedte  ingevoegd met een Tab  druk. |
| Tekstomsluiting | | Als ingeschakeld, worden langere regels code omgevouwen naar de volgende regel. |
| Kleurpreset voor Scripteditor | | Kleurpreset voor code-elementen, selectiekleuren en meer. Na het kiezen van een preset, kun je specifieke kleuren instellen voor opties zoals Selectiekleur  en Commentaarkleur . |

## [Sneltoetsen](#sneltoetsen)[](#sneltoetsen)

De Scripteditor heeft de volgende sneltoetsen.

Bestand en weergave Basisbewerking Multi-Cursor

| Opdracht | | Windows | | Mac |
| Sluit script | | Ctrl W | | ⌘ W |
| Heropen laatst gesloten script | | Ctrl Shift T | | ⌘ Shift T |
| Snelle open | | Ctrl P | | ⌘ P |
| Toon script in Explorer | | Ctrl Alt K | | ⌘ ⌥ K |
| Inzoomen | | Ctrl = | | ⌘ = |
| Uitzoomen | | Ctrl - | | ⌘ - |
| Reset scriptzoom | | Ctrl 0 | | ⌘ 0 |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
