<!-- Source: https://create.roblox.com/docs/nl-nl/studio/properties -->

Eigenschappenvenster | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Eigenschappenvenster

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Eigenschappen  venster, toegankelijk vanuit het Venster  menu of de Start  tabblad werkbalk van Studio, stelt je in staat om bepaalde eigenschappen van een geselecteerd object aan te passen om te veranderen hoe het object eruitziet en zich gedraagt. Daarnaast kun je [tags](#instantie-tags)  beheren en instantie [attributen](#instantie-attributen)  configureren onderaan het venster.

 ![Eigenschappen gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Properties.png)

Wanneer je een object selecteert, verandert de bovenbalk van het venster om de klasse en naam van het object weer te geven, en zijn eigenschappen zijn verdeeld in secties. Bijvoorbeeld, een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  bevat secties zoals Uiterlijk  en Transformatie  die respectievelijk toestaan om het uiterlijk te veranderen en de [Grootte](/docs/nl-nl/reference/engine/classes/BasePart#Size) , [CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame) , en oorsprong te transformeren.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sections-Example.png)

Je kunt elke sectie of subsectie in- of uitklappen door op de kleine pijl links van de naam te klikken. Nadat je een sectie hebt uitgebreid of ingeklapt, blijft deze uitgebreid of ingeklapt voor andere objecten van dezelfde klasse, evenals gerelateerde objecten die dezelfde eigenschapsgroepering delen.

Sommige eigenschappen zijn standaard ingeklapt, maar je kunt ze uitbreiden door op de kleine pijl naast de naam te klikken. Bijvoorbeeld, [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  bevat een [Positie](/docs/nl-nl/reference/engine/classes/BasePart#Position)  eigenschap die een X , Y , Z  coördinaat in de 3D-wereld vertegenwoordigt. In Studio kunnen deze coördinaten op twee manieren worden ingevoerd:

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Input-Combined.png) Alle drie de coördinaten getypt in het bovenliggende Grootte  veld, gescheiden door komma's

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Input-Expanded.png) Eigenschap uitgebreid en een individuele groottevector getypt in de X , Y , en Z  velden

Nadat je een eigenschap hebt uitgebreid of ingeklapt, blijft deze uitgebreid of ingeklapt voor andere objecten van dezelfde klasse, evenals gerelateerde objecten die dezelfde eigenschap delen.

## [Eigenschap filter](#eigenschap-filter)[](#eigenschap-filter)

Je kunt eigenschappen filteren door een zoekopdracht in te voeren in het Filter Eigenschappen  invoerveld nabij de bovenkant van het venster. Bijvoorbeeld, filteren op de letters "velo" vindt alle eigenschappen die ze bevatten, zoals AssemblyLinear Velo city  en AssemblyAngular Velo city . Toegang tot deze invoer krijg je snel door Ctrl Shift P  (Windows) of ⌘ Shift P  (Mac) in te drukken.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Instance-Filtered.png)

## [Instantie tags](#instantie-tags)[](#instantie-tags)

De Tags  sectie stelt je in staat om specifieke tags toe te passen voor gebruik met [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) . Tags zijn sets van strings die worden toegepast op instanties die repliceren van de server naar de client. Ze worden ook geserialiseerd wanneer plaatsen worden opgeslagen.

Om tags aan een instantie toe te voegen via het Eigenschappen  venster:

1.

Selecteer de instantie, scroll naar de Tags  sectie en klik op de +  knop.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Add-Tag-Button.png)

2.

Voer in het pop-upvenster een nieuwe tagnaam in of  selecteer een tag die je al voor een andere instantie hebt gemaakt uit de lijst onder het invoerveld. De tag verschijnt binnen de Tags  sectie.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Set-Tag.png)

3.

Indien nodig kun je een bestaande tag verwijderen door op het ×  pictogram te klikken.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Remove-Tag-Button.png)

## [Instantie attributen](#instantie-attributen)[](#instantie-attributen)

Attributen  stellen je in staat om instanties te personaliseren met je eigen gegevens. Ze zijn vergelijkbaar met ingebouwde objecteigenschappen, maar je kunt je eigen attributen voor elke instantie maken en wijzigen. Belangrijke kenmerken zijn:

-

Attributen kunnen direct binnen Studio of via scripting worden gemaakt, bewerkt en verwijderd (zie [eigenschappen en attributen](/docs/nl-nl/scripting/attributes)  voor scriptcommando's om attributen te maken, in te stellen, op te halen en te verwijderen).

-

Attributen en hun waarden worden opgeslagen met je plaats en activa.

-

Waarde wijzigingen kunnen in realtime worden bekeken en worden gerepliceerd  zodat clients er onmiddellijk toegang toe hebben.

Je kunt de volgende types/waarden in attributen opslaan:

-

[string](/docs/nl-nl/luau/strings)

-

[boolean](/docs/nl-nl/luau/booleans)

-

[number](/docs/nl-nl/luau/numbers)

-

[UDim](/docs/nl-nl/reference/engine/datatypes/UDim)

-

[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

-

[BrickColor](/docs/nl-nl/reference/engine/datatypes/BrickColor)

-

[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

-

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

-

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

-

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

-

[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

-

[ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)

-

[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

-

[Rect](/docs/nl-nl/reference/engine/datatypes/Rect)

-

[Font](/docs/nl-nl/reference/engine/datatypes/Font)

Nieuwe attributen kunnen in Studio worden gemaakt en gewijzigd als volgt:

1.

Selecteer de instantie, scroll naar de Attributen  sectie en klik op de +  knop.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Add-Attribute-Button.png)

2.

Voer in het pop-upvenster de Naam  van het attribuut in, selecteer het Type , en klik op Opslaan .

3.

Het nieuwe attribuut verschijnt met een standaardwaarde die je kunt wijzigen zoals elke andere eigenschap.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Set-Attribute.png)

4.

Indien nodig kun je een attribuut hernoemen of verwijderen door op het tandwielpictogram te klikken.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Rename-Delete-Attribute-Button.png)

## [Configureerbare standaardinstellingen](#configureerbare-standaardinstellingen)[](#configureerbare-standaardinstellingen)

De functie configureerbare standaardinstellingen  stelt je in staat om eigenschappen van een geselecteerde [Instance](/docs/nl-nl/reference/engine/classes/Instance)  op te slaan als de nieuwe standaard voor dat type, ze indien nodig opnieuw in te stellen, en ze te delen vanuit een lokaal bestand indien gewenst. Gebruiksscenario's zijn onder andere:

-

Een standaard [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  instantie waarbij [Verankerd](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  waar  is, zodat elke nieuwe [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  die in de 3D-werkruimte wordt ingevoegd, verankerd is.

-

Een set standaard [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  met fysieke gedragingen die overeenkomen met het type mechanismen dat je momenteel aan het bouwen bent, zoals massieve voertuigen versus kleinere machines met minder massa.

-

Een set standaard [licht](/docs/nl-nl/effects/light-sources)  bronnen ([PointLight](/docs/nl-nl/reference/engine/classes/PointLight) , [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) , [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight) ), elk met [Helderheid](/docs/nl-nl/reference/engine/classes/Light#Brightness)  die past bij de omgeving die je ontwerpt.

Om een specifieke instantie als de standaard in te stellen:

1.

Selecteer de instantie in de 3D-weergave of [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie.

2.

Selecteer vanuit het hoofdmenu Bewerken  van Studio Opslaan als Standaard [Instantie] . Een toastmelding geeft aan dat de standaard is bijgewerkt, en nieuw ingevoegde instanties van dat type zullen overeenkomen met de standaard eigenschappen.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Default-Properties-Toast.jpg)

Instantie standaardinstellingen worden lokaal  op elke machine opgeslagen in een DefaultInstances.rbxm  bestand, niet op je Roblox of groepsaccount. De locatie van deze map kan worden gewijzigd in de instellingen van Studio (Alt S  of ⌥ S ) onder het Studio  tabblad ⟩ Instantie Standaardinstellingen Dir .

Om een configureerbare standaardinstantie te resetten :

1.

Selecteer een instantie van dat type in de 3D-weergave of [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie.

2.

Selecteer vanuit het hoofdmenu Bewerken  van Studio Reset Standaard [Instantie] . Bestaande instanties van dat type behouden hun eigenschappen, maar nieuw ingevoegde instanties zullen de standaard eigenschappen van Studio gebruiken.

Let op de volgende uitzonderingen en gedragsregels voor standaardinstanties:

-

De positionele  instantie eigenschappen [BasePart.Position](/docs/nl-nl/reference/engine/classes/BasePart#Position) , [BasePart.CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame) , [PVInstance.Origin](/docs/nl-nl/reference/engine/classes/PVInstance#Origin) , en [Model.WorldPivot](/docs/nl-nl/reference/engine/classes/Model#WorldPivot)  worden niet  beïnvloed door standaard eigenschappen, maar worden in plaats daarvan overschreven door de invoeringsregels en workflows van Studio. Echter, [GuiObject.Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position)  en positionele eigenschappen voor [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  ([Positie](/docs/nl-nl/reference/engine/classes/Attachment#Position) , [WorldCFrame](/docs/nl-nl/reference/engine/classes/Attachment#WorldCFrame) , [Wereldpositie](/docs/nl-nl/reference/engine/classes/Attachment#WorldPosition) ) worden opgeslagen/onderhouden in geconfigureerde standaardinstellingen van die instantietypen.

-

De acties Groeperen als Model  (Ctrl G  of ⌘ G ) en Groeperen als Map  (Ctrl Alt G  of ⌘ ⌥ G ) van Studio gebruiken geen  de standaardinstellingen voor [Model](/docs/nl-nl/reference/engine/classes/Model)  of [Folder](/docs/nl-nl/reference/engine/classes/Folder) , respectievelijk.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
