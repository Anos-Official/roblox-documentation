<!-- Source: https://create.roblox.com/docs/nl-nl/resources/the-mystery-of-duvall-drive/materialize-the-world -->

Materialiseer de wereld | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Het mysterie van Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)

# Materialiseer de wereld

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

We gebruiken [materialen](/docs/nl-nl/parts/materials)  en [oppervlakteverschijning](/docs/nl-nl/art/modeling/surface-appearance)  objecten om een meeslepende en realistische binnen- en buitenomgeving te creëren. Zonder materialen zou deze scène nog steeds enige interessante diepte, silhouetten en verlichting kunnen hebben, maar met onze materialen en textuursystemen kunnen we de kamer echt tot leven brengen en een dimensie van realisme aan de wereld toevoegen.

Deze [fysiek-gebaseerde rendering](/docs/nl-nl/art/modeling/surface-appearance)  (PBR) materialen zijn wat oppervlakken zoals hout doet lijken, reageren en reflecteren zoals hout dat in de echte wereld doet. In deze sectie zullen we enkele van de beslissingen en processen doornemen die we hebben doorlopen om het palet van materialen te creëren dat in de demo is gebruikt. Zoals in de [Beyond the Dark](/docs/nl-nl/resources/beyond-the-dark)  demo, wilden we een realistische uitstraling en gevoel voor onze materialen en dat hebben we bereikt door een paar verschillende benaderingen.

Je kunt het proces van het bouwen van al onze texturen en materialen opdelen in drie gebieden:

-

Oppervlakteverschijningsobjecten voor 1:1 of unieke materialen voor meshes, zoals een marmeren standbeeld.

-

Oppervlakteverschijningsobjecten voor gedeelde trimkaarten voor [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) , zoals herhaalbare houttrimdetails op meubels.

-

[Materiaalvarianten](/docs/nl-nl/parts/materials#aangepaste-materialen)  voor gedeelde materialen op Parts of terrein, zoals flagstone die cobblestone vervangt voor zowel open haarden als de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/overview.png)

## [Plannen, hergebruiken en budgetten](#plannen-hergebruiken-en-budgetten)[](#plannen-hergebruiken-en-budgetten)

Bij het starten van een project, denk na over de artistieke richting van materialen voor consistentie en hergebruik. Elk platform en apparaat heeft een limiet op de hoeveelheid geheugen die je kunt gebruiken voor texturen, dus enige voorafgaande planning helpt om het aantal texturen in je spel onder controle te houden.

Bij het overwegen van de uitstraling en het gevoel van het spel, hebben we bewust gekozen voor een ambachtelijke stijl huis om ervoor te zorgen dat we een handvol materialen konden hergebruiken over een breed scala aan activa, van kleine fotolijsten en meubels tot grote architectonische elementen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/craftsman-reference-images.png) Hier zijn enkele van de referentieafbeeldingen die we hebben verzameld voor de Craftsman-stijl.

In zijn basisvorm omvatten de kenmerken van [American Craftsman](https://en.wikipedia.org/wiki/American_Craftsman)  eenvoudige, schone lijnen en natuurlijke houttinten, waardoor het hout en de kunstzinnigheid van de timmerman centraal staan. Deze kenmerken stellen ons in staat om één set houttrimtextuurkaarten te gebruiken voor meubels en architectonische elementen in het huis en stellen ons ook in staat om onze modellen vrij laag poly te houden. Met dit in gedachten, gingen we aan de slag om de trimkaarttextuurset te creëren die je hieronder ziet.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/wood-trim-texture-set.png) Hout Trim Textuur Set

## [Oppervlakteverschijning en trimkaarten](#oppervlakteverschijning-en-trimkaarten)[](#oppervlakteverschijning-en-trimkaarten)

Trimkaarten zijn eenvoudige herhaalbare texturen die op een breed scala aan activa kunnen worden toegepast. Trimkaarten doen veel zwaar werk in games en vullen de kloof tussen volledig tegeltexturen en het creëren van een 1:1 textuurset die je zou krijgen door een object te schilderen in een programma zoals [Substance Painter](https://www.adobe.com/products/substance3d-painter)  of door gebruik te maken van [fotogrammetrie](/docs/nl-nl/resources/the-mystery-of-duvall-drive/construct-the-house#fotogrammetrie) . Het houtmateriaal dat eerder werd getoond, was ingesteld als een trimkaart, wat betekent dat het op veel verschillende meshes kon worden hergebruikt, waarbij elke mesh profiteert van dezelfde trimtexturen door zijn UV's creatief uit te leggen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/tiling-texture.png) Tiling Textuur

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/trim-texture.png) Trim Textuur

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/1-1-texture.png) 1-1 Textuur

Bij het gebruik van trimkaarttextuursets voor gebruik over een breed scala aan schalen en objecten, probeer je je texturen redelijk schoon en vrij van details te houden die gemakkelijk herkenbaar zouden zijn als herhalend.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/too-much-detail-texture.png) Voorbeeld van te veel detail

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/cleaner-texture.png) Schonere texturen werken het beste

Voor een voorbeeld van over-detail, stel dat we wat vuil aan onze BaseColor-kaart wilden toevoegen. Kijk hoe snel je de onrealistische richting van texturen en uitgerekte UV's begint op te merken.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/furniture-set-stain.png) Let op hoe het extra detail van vlekken op het meubel aan de linkerkant opvalt door herhaling en onjuiste richting in vergelijking met de schonere set aan de rechterkant.

Als een activum echt zware vlekken, slijtage en/of vuilophoping nodig heeft, is het beter om een 1:1 kaart te gebruiken die uniek is voor die specifieke mesh. Voor aanvullende informatie over het werken met trimkaarten, zie de sectie [Maak trimbladen](/docs/nl-nl/resources/beyond-the-dark/building-architecture#maak-trim-sheets)  in de Beyond the Dark-documentatie.

Je kunt een enkele Oppervlakteverschijningsnode met deze trimkaarten verpakken en de trim toepassen op al de activa die hieronder worden getoond.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/wood-trim-asset-place.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/wood-trim-assets-in-place.png)

Slechts enkele van de vele activa die dezelfde Hout Trim Oppervlakteverschijningsnode hebben gebruikt.

Tinting is een andere manier om je Oppervlakteverschijningsnodes en Materiaalvarianten verder te laten gaan. Door een alpha-masker toe te voegen aan je [SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  en de [SurfaceAppearance.AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  in te stellen op Overlay , kun je [BrickColor](/docs/nl-nl/reference/engine/datatypes/BrickColor)  of [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  gebruiken om je objecten te tinten voor visuele variatie.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/couch-surface-appearance-set.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/leather-couch-settings.png)

Deze 4 kleurvariaties maken allemaal gebruik van dezelfde Verpakte Oppervlakteverschijningsnode.

Alpha-maskers, ongeacht hoe ze zijn gemaakt, worden samengevoegd in je [SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap) , waardoor het verandert van een standaard RGB-textuur naar een RGBA. Je kunt spelen met waarden en niveaus in je alpha-masker om het gewenste niveau van tinting te krijgen, maar met een beetje finesse kun je geweldige resultaten behalen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/basecolor-rgb.png) BaseColor RGB

In dit leervoorbeeld hebben we gewoon de hoogtekaart gemengd met wat krassen en slijtage om ons alpha-masker te creëren.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/height-map.png) Hoogtekaart

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/scratches-and-wear-mask.png) Krassen en slijtage

Deze twee kaarten werden vervolgens naar een Alpha Merge Node gestuurd om de uiteindelijke RGBA te creëren die in de Overlay Oppervlakteverschijningsnode wordt gebruikt.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/final-alpha.png) Eind Alpha textuur. Witte pixels passen geen tint toe en tonen alleen de Base Color RGB-kaart. Zwarte pixels tinten en tonen alleen de platte BrickColor/Color met een verloop tussen de twee.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/alpha-merge-substance-designer.png) Voorbeeld van de BaseColor en Alpha die worden samengevoegd via de Alpha Merge Node in Substance Designer.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/rgba-in-combination.png) Voorbeelden van de RGBA in combinatie met Mesh Color op witte, bruine, rode en blauwe meshes.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/only-colormap-and-mesh-color.png) Zelfde voorbeeld dat alleen de ColorMap en Mesh Color toont.

## [Textuurgroottes](#textuurgroottes)[](#textuurgroottes)

Naast het veelvuldig hergebruiken van texturen, kun je andere technieken toepassen om je textuurgeheugengebruik laag te houden. Je kunt textuurgroottes verminderen op basis van gebruik. Bijvoorbeeld, je kunt vaak de resolutie van de [SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap) , [SurfaceAppearance.RoughnessMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#RoughnessMap) , en [SurfaceAppearance.MetalnessMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#MetalnessMap)  van je Oppervlakteverschijningsobject met 1 of 2 keer verlagen zonder visuele kwaliteit te verliezen. Vaak kan de [SurfaceAppearance.MetalnessMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#MetalnessMap)  leeg worden gelaten, wat resulteert in een puur zwart/niet-metaal oppervlak.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/leather-trim-texture-set.png) Deze leer trim textuurset bestaat uit een normale kaart op 1024, een basiskleurkaart op 512, een ruwheidskaart op 256, en geen metalness kaart.

In [Substance Designer](https://www.adobe.com/products/substance3d-designer)  is de gemakkelijkste manier om uitvoer te verkleinen het toevoegen van een [Transformation 2D node](https://substance3d.adobe.com/documentation/sddoc/transformation-2d-172825332.html)  net voor je uiteindelijke uitvoernode en de Output Size  binnen de Basisparameters sectie voor die node aan te passen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/transform-2d-node.png) Transform 2D Node met aangepaste Output Size.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/final-surface-on-couch.png) Eindoppervlak op bank meshes.

Het kost over het algemeen verschillende iteraties van het verkleinen van de verschillende kaarten in je textuurset en het visueel inspecteren van het activum in Studio om ze op een plek te krijgen waar ze goed genoeg standhouden over de verschillende groottes van activa. Met dit proces kun je de kleinste textuurgroottes vaststellen waarvan je denkt dat je ermee weg kunt zonder de visuele kwaliteit te verliezen die nodig is voor de artistieke richting van je spel.

Met deze paar technieken kun je je textuurbudget onder controle houden en toch een prachtige ervaring hebben.

Bij het importeren van aangepaste meshes in Studio, kunnen basistexturen die bij je model zijn inbegrepen, samen met je mesh worden geïmporteerd en automatisch worden toegepast als een textureID. Dit kan een probleem worden bij het importeren van meerdere meshes met dezelfde basistextuur. Elke import kan een nieuwe versie van dezelfde textuurkaart creëren en je textuurgeheugen opblazen.

Wanneer een verpakte Oppervlakteverschijningsnode wordt toegepast voor hergebruik, zorg er dan voor dat je het textureID binnen de eigenschappen van de mesh verwijdert om dit probleem te voorkomen. Dit is een bekend gedrag en Roblox kijkt naar het verbeteren van deze stroom.

## [Basis materialen](#basis-materialen)[](#basis-materialen)

Aangezien we [onderdelen](/docs/nl-nl/parts) , [terrein](/docs/nl-nl/parts/terrain) , en [meshes](/docs/nl-nl/parts/meshes)  naast elkaar hebben gebruikt in deze demo, hebben we ervoor gekozen om de standaard [ingebouwde materialen](/docs/nl-nl/parts/materials#asset-ids-for-built-in-materials) , [Materiaalvarianten](/docs/nl-nl/parts/materials#aangepaste-materialen) , en de nieuw vrijgegeven [Materiaalbeheerder](/docs/nl-nl/parts/materials#materiaalbeheerder)  tool te gebruiken om ervoor te zorgen dat onze verschillende onderdelen en terreinoppervlakken overeenkomen met de uitstraling en het gevoel van onze PBR-geconfigureerde meshes.

Basis materialen zijn beschikbaar voor gebruik zoals ze zijn of om te wijzigen als een nieuwe variant. In veel gevallen dienen de houten basismaterialen ons zeer goed en vereisen ze alleen aanpassing van de kleur om overeen te komen met onze geconfigureerde meshes.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/mesh-in-foreground.png) Voorbeeld van een mesh op de voorgrond die een Oppervlakteverschijningsnode en CSG (constructieve solide geometrie) objecten gebruikt die in Studio zijn gebouwd met Onderdelen en de standaard Hout materiaal gekleurd om overeen te komen.

## [Materiaalvarianten](#materiaalvarianten)[](#materiaalvarianten)

Aangezien het spel een buitenomgeving tijdens een stortbui omvat, wisten we dat we wilden dat onze grond nat en modderig aanvoelde om overeen te komen met onze stormachtige pacific northwest artistieke richting. We hebben dit bereikt door een handvol nieuwe [Aangepaste Materialen](/docs/nl-nl/parts/materials#aangepaste-materialen)  te creëren met behulp van [Materiaalvarianten](/docs/nl-nl/parts/materials#create-a-custom-material-in-the-explorer)  die we konden gebruiken om de basismaterialen te overschrijven. We gebruiken ze om dingen zoals mulch, grote en kleine grind, modder, evenals een ondiepe plassenversie van elk te schilderen.

Materiaalvarianten stellen de gebruiker in staat om texturen te herdefiniëren die worden gebruikt voor een gegeven standaardmateriaal, wat veel mogelijkheden biedt om materialen die in terrein en onderdelen worden gebruikt aan te passen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/backyard-wet-material-variants.png) Afbeelding van de achtertuin en het gebruik van natte Materiaalvarianten.

Materiaalvarianten worden ook gebruikt om natte en droge versies van onze materialen te creëren. Dit is nuttig voor oppervlakken zoals beton en onze flagstone hardscape die droog zou zijn onder de overkapping van het porchdak en nat wanneer blootgesteld aan de regen in de tuin.

Het creëren van een Materiaalvariant kan worden gedaan binnen de [Materiaalbeheerder](/docs/nl-nl/parts/materials#materiaalbeheerder) . Zoals de naam al aangeeft, stelt de Materiaalbeheerder je ook in staat om zowel standaard- als materiaalvarianten op één plek te beheren.

Zodra de Materiaalbeheerder is geopend, klik je op de Cirkel Plus-knop in de linkerbovenhoek van het venster om een nieuwe Variant te bewerken en toe te voegen. Bij het toevoegen van een naam is het een goed idee om een suffix van _MV achter je naam toe te voegen, zodat je de nieuwe materiaalvariant gemakkelijk kunt onderscheiden van de standaardmaterialen.

Kies een Basis Materiaal  dat het dichtst bij je nieuwe materiaal staat. Je kunt het Basis Materiaal veld beschouwen als de Fysieke Eigenschappen  van het materiaal, wat invloed heeft op dingen zoals wrijving, dichtheid, gewicht, impacteffecten en voetstapgeluiden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/edit-variant-dialog.png) Let op dat de Metalness-kaart leeg is gelaten omdat deze niet nodig was.

Waarom een Materiaalvariant creëren? Materiaalvarianten die een Basis Materiaal overschrijven, erven alle eigenschappen van dat materiaal, behalve de visuals. Dit betekent dat je materiaalvariant de fysieke gedragingen van het standaardmateriaal erft, zoals dichtheid. Het betekent ook dat toekomstige toevoegingen, zoals het toevoegen van unieke akoestiek aan beton, automatisch worden geërfd. In dit geval willen we een nieuwe natte betonvariant creëren die bijna alle eigenschappen van het betonmateriaal erft.

Als het Basis Materiaal betrekking heeft op de Fysieke Eigenschappen , dan zijn de Textuurkaarten onze Visuele Eigenschappen . Textuurkaarten  vertellen de renderer hoe licht met het materiaal moet interageren via onze PBR-renderingpipeline. Het Basis Materiaal veld definieert ook welk standaardmateriaal wordt overschreven met de nieuwe visuele eigenschappen. In dit geval gaan we verder met het overschrijven van het Beton  basismateriaal.

Nu we onze nieuwe "Concrete_Wet_MV" hebben gemaakt, moeten we het standaard betonmateriaal ermee overschrijven zodat we het in onze scène kunnen gebruiken. Om dat te doen, klik je gewoon op je nieuwe MV en klik je op de Set Override  schakelaar.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/set-override.png) Let op dat het standaard betonmateriaal verandert in de nieuwe Concrete_Wet_MV wanneer de Set Override wordt ingeschakeld.

Materiaalvarianten kunnen per onderdeel/meshpart worden toegepast, zodat je een onbeperkt aantal aangepaste materialen tegelijkertijd op onderdelen kunt gebruiken. Terrein vereist het gebruik van overschrijvingen voor aanpassing, en je bent beperkt tot het overschrijven van de 22 ingebouwde materialen.

Nu zal alles wat beton in je scène gebruikt nu de nieuwe overschrijving gebruiken, inclusief elk beton dat je misschien op je terrein hebt geschilderd. De enige uitzondering hierop zijn onderdelen die een specifiek vermelde "materiaalvariant" op dat object hebben.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/material-variant-overrides.png) Voorbeeld van Materiaalvariant Overschrijvingen die worden gebruikt op terrein en onderdelen.

Om ons terrein een verscheidenheid aan oppervlakken te geven, inclusief zowel nat als met plassen, hebben we ongeveer 10 van de standaardmaterialen overschreven. Dit was noodzakelijk voor de door regen doordrenkte uitstraling die we voor ons uiteindelijke terrein wilden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/before-override.png) Voor Materiaalvariant Overschrijving.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/after-override.png) Na Materiaalvariant Overschrijving.

Met al deze materiaalopties en tools binnen handbereik zijn de mogelijkheden van wat je kunt creëren onbeperkt. Met een beetje vooruitdenken en planning kun je inspirerende materialen creëren, terwijl je de texturen van je spel binnen budget houdt.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/backyard-terrain-materials.png) Shot van de achtertuin die de variatie in de terreinmaterialen toont.

[Volgende](/docs/nl-nl/resources/the-mystery-of-duvall-drive/immersive-narrative)[Vorige](/docs/nl-nl/resources/the-mystery-of-duvall-drive/construct-the-house)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
