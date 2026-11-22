<!-- Source: https://create.roblox.com/docs/nl-nl/learn/more/rounded-corners -->

Wat er nodig is om een hoek rond te maken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

Meer informatie

![Een scheef zwaard winkellmenu met afgeronde hoeken, een zachte schaduw, en een oranje-naar-paarse verloopkoptekst, zwevend boven een vervaagde gamewereld.](https://prod.docsiteassets.roblox.com/assets/resources/rounded-corners/cover-finale.jpg)

# Wat er nodig is om een hoek rond te maken

Een schaduw, een afgerond menu, een verloop over een koptekst. Dit zijn de soorten details waar niemand twee keer over nadenkt... totdat iemand een game-engine moet leren hoe ze deze moeten tekenen.

[

Speel op Roblox](https://www.roblox.com/games/start?placeId=107426260461768)[

Bekijk de code](https://github.com/Roblox/resources/tree/main/experiences/rounded-corners)

## In dit artikel

1. [Chapter 01 · Schaduwen Een native drop shadow bouwen](#shadows)
2. [Chapter 02 · Verlopen Verlopen voorbij de rechte lijn](#gradients)
3. [Chapter 03 · Knippen Knippen naar een curve](#clipping)

Stel je dit voor: je maakt een winkellmenu voor je Roblox-spel. Er is een zwaard te koop. Je schetst een paneel dat boven de actie zweeft, geeft het afgeronde hoeken en een zachte schaduw, en laat de itemkaarten netjes onder de gebogen randen scrollen. Een verloop geeft de koptekst een beetje persoonlijkheid.

Het is een volkomen gewoon menu, het soort dat je in Figma kunt opzetten voor de lunch of op het web kunt samenstellen met een handvol CSS-eigenschappen. Roblox moet het echter tekenen terwijl je vrienden erachter rondrennen en dingen in brand steken, en het moet werken op alles, van een gaming-pc tot een telefoon met een gebroken scherm.

De afgeronde hoeken zelf zijn eenvoudig genoeg om te tekenen, maar het binnenhouden van die scrollende itemkaarten is moeilijker dan het lijkt. De eenvoudigste kniptool van de GPU kan alles buiten een rechthoek afsnijden, maar begrijpt geen afgeronde hoeken. De schaduw moet de rand volgen telkens wanneer je de vorm verandert, en het verloop moet zich gedragen wanneer je het draait.

Dit zijn de soorten problemen die de Capabilities-pod bezig hebben gehouden. Het kleine team, geleid door engineering manager Chase Ruppert ([@DrRanchDressing](https://www.roblox.com/users/1298953044/profile) ), maakt deel uit van de Digital Matter-groep van Roblox. In augustus 2025 stelde hoofdingenieur Jonah Williams ([@jaydubs808](https://www.roblox.com/users/8302270184/profile) ) een voorstel op om enkele van de ontbrekende onderdelen van Roblox's UI-toolkit in te vullen, van native schaduwen en nieuwe verlopen tot meer flexibele vormen en betere kniptechnieken. Dat voorstel heeft geholpen om het werk van het team het afgelopen jaar te begeleiden.

Jonah beschouwt deze effecten als onderdeel van de "grammatica" van 2D UI. Zodra je hebt geleerd om afgeronde hoeken, schaduwen en verlopen op één plek te gebruiken, verwacht je dat diezelfde bouwstenen elders beschikbaar zijn. En wanneer er één ontbreekt, merk je het.

Chapter 01  · Schaduwen

## Een native drop shadow bouwen

Een schaduw gebouwd vanuit het frame, in plaats van een afbeelding erachter.

Roblox-makers vragen al meer dan een decennium om native drop shadows. In een DevForum-bericht uit 2015 beschreef een ontwikkelaar dat hij aangepaste schaduwafbeeldingen moest uploaden of negen-slice frames moest gebruiken om het gewenste effect te krijgen. De klassieke oplossing was om een schaduw in Photoshop te schilderen, deze als PNG te exporteren en de afbeelding achter een frame te plaatsen. Een andere optie was om doorzichtige [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke) -contouren te stapelen, elk iets groter en vager dan de vorige, totdat de hele stapel eruitzag als een schaduw, zolang je er maar niet te hard naar keek.

Beide konden overtuigend lijken, hoewel ze enkele vervelende beperkingen met zich meebrachten. Een PNG van 800 bij 800 pixels kan bijvoorbeeld ongeveer 2,5 megabyte ongecomprimeerd geheugen in gebruik nemen, wat behoorlijk veel is voor een grijze vlek. Het schalen of comprimeren van de afbeelding om ruimte te besparen, kon banding of artefacten introduceren. In tegenstelling tot het frame zelf, kon de afbeelding ook niet automatisch aanpassen aan veranderingen in zijn vorm. Animeren van de hoekradius van het frame, en de schaduw zou zijn oorspronkelijke omtrek behouden, als een sticker. Gestapelde strokes deden het iets beter, omdat ze mee konden groeien met het frame, maar ze behielden de hoekradius waarmee ze waren getekend.

De engine was niet wijzer. Voor zover de renderer kon zien, was die vlek gewoon een andere afbeelding, niet anders dan een pictogram of een foto van iemands hond. Het had geen manier om te weten dat de afbeelding een schaduw moest zijn, dus het kon geen gebruik maken van rendertechnieken die specifiek voor dat effect zijn ontworpen.

Wat het team wilde, en wat senior software engineer [@luigiburger333](https://www.roblox.com/users/4541804944/profile)  hielp bouwen, was een schaduw die daadwerkelijk bij het frame hoorde, eentje die kon veranderen telkens wanneer het frame veranderde zonder dat de grafische kaart overuren moest draaien om bij te blijven.

De conventionele manier om een zachte schaduw te produceren, is door de vorm die deze werpt te vervagen. Een * Gaussian blur*  verspreidt de opaciteit over de omliggende pixels volgens een klokvormige curve: hoe verder je van de vorm afkomt, hoe vager de schaduw wordt. Maak de curve breder en de schaduw wordt zachter. De resultaten zien er geweldig uit, maar een volledige afbeeldingsvervaging houdt in dat je naburige pixels moet bemonsteren, wat kostbaar kan worden wanneer je veel UI-elementen tekent die bewegen en veranderen.

Er is ook een vreemde detail verborgen in de Gaussian-curve. Wiskundig gezien bereikt het nooit echt nul. Het komt gewoon steeds dichterbij, voor altijd. Dus de schaduw onder je zwaardwinkeltje is, strikt genomen, nog steeds op weg naar de rand van het universum, en je grafische kaart zou het waarschijnlijk liever niet daarheen volgen.

In de praktijk snijden renderers de vervaging af zodra deze te vaag wordt om er toe te doen, maar het team had een ambitieuzere vraag in gedachten: konden ze de vervaging helemaal overslaan?

### Een afgeronde rechthoek vervagen

Het antwoord van het team was om de schaduw te behandelen als een Gaussian blur van een afgeronde rechthoek en het uit te werken vanuit de vorm zelf. De algoritmische aanpak was al getest in Skia, de open-source grafische bibliotheek die door Chrome, Flutter en Android wordt gebruikt, en het team paste het aan voor de renderer van Roblox. In plaats van te beginnen met een afbeelding, begint het met iets dat Roblox al kent: de vorm van het frame dat de schaduw werpt. De meeste UI-frames zijn rechthoeken of afgeronde rechthoeken, dus de renderer kent al hun afmetingen en hoekstralen.

Om de schaduw te tekenen, creëert de renderer twee nieuwe contouren rond het frame, één iets groter en een andere naar binnen getrokken. Beide buigen rond dezelfde hoeken, waardoor er een band tussen hen ontstaat die een beetje lijkt op een zeer rechthoekige donut.

De contouren worden niet willekeurig geplaatst. Elke zit anderhalf keer de vervagingsradius van de schaduw van de rand van het frame, een afstand die gelijk is aan drie standaarddeviaties langs de Gaussian-curve. Buiten de buitenste contour is de schaduw vervaagd tot bijna niets, zodat de renderer veilig kan stoppen met tekenen.

De band wordt verdeeld in driehoeken via een proces dat * tessellatie*  wordt genoemd. Elke vertex, of hoek van een driehoek, krijgt een waarde die zijn positie langs de vervaging van de schaduw beschrijft. De GPU interpoleert vervolgens die waarden over de driehoeken, waardoor elke pixel een positie tussen de binnenste en buitenste randen krijgt.

Dat vertelt de renderer * waar*  de schaduw moet vervagen, maar het laat nog steeds de vraag open hoe donker elke pixel moet zijn. Het uitwerken van de Gaussian-curve voor elke pixel zou betekenen dat je hetzelfde wiskundige werk keer op keer moet doen, dus het team berekende de curve van tevoren en slaagde het antwoord op in een kleine textuur. Terwijl de GPU de schaduw tekent, kijkt hij de opaciteit voor elke pixel op in plaats van deze vanaf nul te berekenen.

### Probeer de schaduw speelplaats

De bijbehorende plaats heeft een schaduw speelplaats, met een frame dat een echte UIShadow gebruikt en een paneel met knoppen voor elk van zijn eigenschappen. Open het vanuit de rechterbovenhoek van de ervaring en kijk wat elke eigenschap doet.

Het werkt op een computer, telefoon of tablet. Elke controle is een echte UIShadow-eigenschap, dus alles wat je daar bouwt, werkt op dezelfde manier in Studio.

[

Speel op Roblox](https://www.roblox.com/games/start?placeId=107426260461768)

Expand video

1. 01** Vervaging, offset en transparantie**

Verander de [BlurRadius](/docs/nl-nl/reference/engine/classes/UIShadow#BlurRadius) , [Offset](/docs/nl-nl/reference/engine/classes/UIShadow#Offset) , [Transparency](/docs/nl-nl/reference/engine/classes/UIShadow#Transparency) , en [Spread](/docs/nl-nl/reference/engine/classes/UIShadow#Spread)  van een enkele schaduw, beginnend vanaf de standaardinstellingen van een nieuwe [UIShadow](/docs/nl-nl/reference/engine/classes/UIShadow) .

2. 02** Een tweede laag**

Voeg een tweede, zachtere [UIShadow](/docs/nl-nl/reference/engine/classes/UIShadow)  achter de eerste toe, zoals de twee lagen onder het winkellmenu. De [ZIndex](/docs/nl-nl/reference/engine/classes/UIShadow#ZIndex)  van -2 tekent het achter de eerste schaduw. Laad de zwaardwinkelschaduwen om de exacte waarden van het menu in te vullen.

3. 03** Het frame zelf**

Verander de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius) , [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size) , en [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  van het frame zonder een van beide schaduwen aan te raken, en zie beide schaduwen zich aanpassen. Voor meer informatie over elke eigenschap, zie [Schaduw](/docs/nl-nl/ui/appearance-modifiers#schaduw)  in de gids voor UI-verschijningmodifiers.

### Acht segmenten per hoek

De eerste versie benaderde elke afgeronde hoek met slechts acht segmenten, wat betekende dat de hele schaduw kon worden getekend met slechts 73 vertices en 108 driehoeken - nauwelijks genoeg geometrie om een GPU te verontrusten. Het team dacht dat eventuele imperfecties zouden verdwijnen in de zachte buitenrand van de schaduw, en voor grote, vage schaduwen deden ze dat. Maar maak de schaduw strak genoeg, en plotseling waren die segmenten niet zo moeilijk te zien.

Het team wilde ook ruimte maken voor meer dan één schaduw op een frame, een techniek die vaak door ontwerpers wordt gebruikt. Combineer een kleine, donkere schaduw met een grotere, zachtere, en plotseling heeft het paneel meer natuurlijke diepte. Het ondersteunen van die lagen betekende uitzoeken welke schaduw bovenop moest worden getekend, iets dat het waard was om vroeg uit te zoeken in plaats van de renderer later opnieuw te moeten bewerken.

Omdat de schaduw is opgebouwd uit het frame, gaat het waar het frame gaat. Geef elke hoek een andere straal? Geen probleem. Draai het frame of wijzig de hele grootte? De schaduw volgt mee. Als je ooit met CSS hebt geknutseld, herken je die controles. Je kunt met je ontwerp spelen en tien keer van gedachten veranderen zonder ooit Photoshop te openen.

Spelers zullen ondertussen niet weten of de schaduw onder je winkellmenu afkomstig is van een PNG of een mesh van driehoeken, en ze zullen het waarschijnlijk niet uitmaken. Ze zien gewoon een winkel die eruitziet alsof hij boven het spel zweeft... en dan kopen ze het zwaard.

Chapter 02  · Verlopen

## Verlopen voorbij de rechte lijn

Radiale en conische verlopen, getekend door een shader in plaats van meer geometrie.

Verlopen hadden het tegenovergestelde probleem. Voor schaduwen was het toevoegen van geometrie het slimme deel. Verlopen verdrinken al in geometrie.

Roblox ondersteunt al jaren lineaire UI-verlopen. Je kiest een richting en een paar kleuren, en de engine mengt ze. Onder de motorkap deed de oude renderer veel van het voorbereidende werk op de CPU, waarbij de vorm in stroken werd verdeeld op de kleur- en transparantiestops van het verloop, wat goed genoeg werkte wanneer de kleuren in een rechte lijn over een rechthoek reisden.

Het wordt rommeliger wanneer de kleuren niet meer in een rechte lijn reizen. Een radiaal verloop verspreidt zich naar buiten vanuit een centraal punt, zoals een gloed, terwijl een conisch verloop (soms een sweep-verloop genoemd) van kleur verandert terwijl je rond een punt beweegt, zoals de wijzer van een klok. Nu zijn de kleurbanden ringen en wiggen, en proberen ze deze uit rechte stroken op te bouwen zou betekenen dat je de vorm in een verschrikkelijk aantal kleine stukjes moet snijden.

### Probeer de verloop speelplaats

De bijbehorende plaats heeft ook een verloop speelplaats, met een frame dat een echte UIGradient gebruikt en knoppen voor elk van zijn eigenschappen. Open het vanuit de rechterbovenhoek van de ervaring en experimenteer.

Het werkt op een computer, telefoon of tablet. Elke controle is een echte UIGradient-eigenschap, dus alles wat je daar bouwt, werkt op dezelfde manier in Studio.

[

Speel op Roblox](https://www.roblox.com/games/start?placeId=107426260461768)

Expand video

1. 01** Drie verloop types**

Wissel [Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  tussen [Lineair](/docs/nl-nl/reference/engine/enums/GradientType#Linear) , [Radiaal](/docs/nl-nl/reference/engine/enums/GradientType#Radial) , en [Conisch](/docs/nl-nl/reference/engine/enums/GradientType#Conical) , en probeer ze met een paar sets van [Kleur](/docs/nl-nl/reference/engine/classes/UIGradient#Color)  en een vervaging van een [Transparantie](/docs/nl-nl/reference/engine/classes/UIGradient#Transparency)  van 0 naar 1.

2. 02** Rotatie, offset en schaal**

Draai het verloop met [Rotatie](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation) , verplaats het centrum met [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset) , en rek de kleuren uit met [Schaal](/docs/nl-nl/reference/engine/classes/UIGradient#Scale) . Op een breed frame dat naar 45 graden is gedraaid, is [Schaal](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  hoe je de menging helemaal in de hoeken krijgt.

3. 03** Het frame zelf**

Verander de [HoekRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  en [Grootte](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  van het frame. Laad de waarden van de zwaardwinkelkop in die achter de koptekst van het winkellmenu staan. Voor meer informatie over elke eigenschap, zie [Verloop](/docs/nl-nl/ui/appearance-modifiers#verloop)  in de gids voor UI-verschijningmodifiers.

### Shader-verlopen

In plaats van de vorm steeds te snijden, verkende het team de mogelijkheid om deze intact te laten en een shader de kleur van elke pixel rechtstreeks te laten berekenen. Voor een lineair verloop betekent dat begrijpen hoe ver een pixel langs een lijn zit. Voor een radiaal verloop is het de afstand tot het centrum. En voor een conisch verloop is het hoe ver je rond de cirkel hebt gereisd.

Elke berekening geeft de shader een positie langs het verloop, die hij kan gebruiken om uit te werken welke kleur daar hoort.

De juiste kleuren vinden, kost echter moeite. Roblox-verlopen slaan kleur en transparantie op als twee aparte lijsten, en elke kan tot twintig stops hebben. De stops hoeven niet noodzakelijkerwijs op elkaar te zijn afgestemd: een kleur kan op het ene punt veranderen terwijl de transparantie ergens anders verandert. Aangezien de lijsten hun start- en eindpunten delen, kan het combineren ervan je met wel 38 verschillende posities achterlaten om te overwegen.

De shader moest nog steeds de twee stops vinden die elke pixelpositie omringen, zodat hij kon uitzoeken welke waarden hij moest mengen. In een vroege prototype probeerde het team een algoritme genaamd * binaire zoekopdracht* . Denk eraan als een spelletje hoger-of-lager: de shader controleert het midden van de lijst, ontdekt welke helft de positie bevat waar hij naar op zoek is, en gooit de andere helft weg. Het blijft dingen verfijnen totdat het het juiste paar vindt, zonder elke stop onderweg te hoeven controleren.

Het was een slim idee, maar het hield geen stand op echte hardware. De prototype draaide langzaam en crashte op low-end apparaten, dus het team verliet het.

In plaats daarvan gingen ze met iets veel eenvoudigers. De renderer maakt een miniatuurversie van elk verloop, slechts één pixel hoog, met al zijn kleuren in een rij. Die stroken worden samengevoegd in een gedeelde textuur die een * atlas*  wordt genoemd. De shader werkt nog steeds uit waar elke pixel zich langs het verloop bevindt, maar nu kan hij in plaats van door een lijst van stops te zoeken, de kleur rechtstreeks uit de strook kiezen. Dat geeft de shader veel minder te doen, wat vooral belangrijk was voor de low-end Android-apparaten die het team moest ondersteunen.

Aangezien de renderer de onderliggende geometrie niet langer hoeft te snijden, kan dezelfde aanpak ook worden gebruikt op allerlei vormen, inclusief gebogen paden en zelfs de schaduwen waar we het eerder over hadden.

### Bestaande verlopen

Er was nog steeds de vraag wat te doen met alle verlopen die Roblox al jaren aan het tekenen was. Neem een lange, brede menu-kop met een diagonale verloop. Onder de oudere berekening kon het draaien van het verloop de verre hoeken buiten het deel laten waar kleuren overgaan, waardoor die gebieden met een vaste kleur werden gevuld. CSS en Figma behandelen de geometrie anders, dus dezelfde instellingen produceren niet altijd hetzelfde resultaat.

** Laat de oude verlopen met rust**

Je zou denken dat het voor de hand liggende antwoord zou zijn om de berekening te veranderen om overeen te komen met die veelgebruikte ontwerptools. Behalve dat iemand, ergens, al een hele interface heeft gebouwd rond het oude gedrag, quirks en al. Verander de wiskunde, en hun UI kan er morgen anders uitzien, ook al hebben ze niets aangeraakt.

Dus het team hield de oude berekening in plaats van het risico te lopen interfaces te veranderen die makers al hadden gebouwd. Dat betekende echter niet dat makers er vast mee zaten: door de [Schaal](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  van een verloop aan te passen, konden ze de kleuren naar de hoeken van een gedraaid hoofdmenu rekken, waardoor ze iets dichter bij de verwachtingen van CSS of Figma kregen. Ondertussen kon het menu dat iemand drie jaar geleden had afgesteld precies zo blijven als het was.

Chapter 03  · Knippen

## Knippen naar een curve

Scrollende kaarten binnen een curve houden, zonder een extra textuur voor elk paneel.

Terug in je winkellmenu zouden de itemkaarten moeten verdwijnen terwijl ze onder de afgeronde hoeken van het paneel scrollen. Het klinkt eenvoudig genoeg, behalve dat de meest eenvoudige manier van knippen in Roblox niet weet wat het met een curve moet doen.

Tot dit jaar knipte Roblox UI volledig op de CPU, waarbij werd uitgewerkt welke delen van elk element binnen zijn container vielen voordat iets de grafische kaart bereikte, en het verplaatsen van dat werk naar de GPU maakte het eindelijk mogelijk om gedraaide vormen te knippen. De eenvoudigste kniptool van de GPU is een * schaarrechthoek* , die al een tijdje bestaat: je geeft de GPU een rechthoekige grens, en hij stopt met tekenen van alles wat daarbuiten valt. Het is snel en betrouwbaar, maar een rechthoek is de enige vorm die hij begrijpt.

Makers omzeilen dit door een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  te combineren met een [UICorner](/docs/nl-nl/reference/engine/classes/UICorner) , hoewel [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  voor veel meer is gebouwd dan knippen.

Stel dat je een heel menu uit het zicht wilt vervagen. Je zou geleidelijk elke knop, label en afbeelding transparanter kunnen maken, maar de overlappende elementen kunnen nog steeds door elkaar heen zichtbaar zijn als een stapel overheadprojector-dia's. Om dat te voorkomen, tekent een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  het hele menu eerst in een aparte afbeelding, en vervaagt vervolgens die afbeelding als één geheel.

Het is een techniek die * render-to-texture*  wordt genoemd, en het is nuttig wanneer je een verzameling UI-elementen als één wilt behandelen. Het nadeel is dat het maken en opslaan van die afbeelding geheugen en extra renderwerk vereist.

** De meeste makers gebruiken CanvasGroup voor knippen**

Toen senior software engineer Emily Ma ([@ThunderBolt5140](https://www.roblox.com/users/1726941628/profile) ) onderzocht hoe makers [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  gebruikten, deed ze meer dan alleen rondvragen. Ze sprak met makers op het DevForum en op RDC, en voegde vervolgens telemetrie toe aan de engine om te zien hoe vaak [CanvasGroups](/docs/nl-nl/reference/engine/classes/CanvasGroup)  daadwerkelijk render-to-texture nodig hadden. Het bleek dat ongeveer 60 procent alleen voor afgeronde of gedraaide kniptechnieken werd gebruikt. Die makers probeerden niet een hele interface te vervagen of te tinten; ze wilden gewoon hun inhoud op de juiste plek houden, maar de engine deed al dat extra werk toch.

Op apparaten met beperkte grafische geheugen konden die extra texturen duur worden. Onder bepaalde omstandigheden kon een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  er zelfs vaag uitzien of veranderen in een solide zwarte rechthoek. Niet precies wat je wilt van een functie die je menu er mooier uit moet laten zien.

### Stencilbuffers

** Stencil knippen is nog niet uitgebracht**

De aanpak in deze sectie is nog in ontwikkeling, dus sommige details kunnen veranderen voordat het wordt uitgebracht.

Voor alleen knippen vond het team een eenvoudigere optie: een * stencilbuffer* .

Stel je voor dat je een afgeronde rechthoek uit een stuk karton snijdt en deze als een sjabloon gebruikt. Je kunt er overal overheen schilderen, maar alleen de verf die door de opening gaat, bereikt het oppervlak eronder. Een stencilbuffer doet hetzelfde, behalve dat het karton wordt vervangen door een verborgen laag cijfers die de GPU vertelt waar hij mag tekenen.

Voor je winkellmenu markeert de renderer eerst de afgeronde vorm van het paneel in die verborgen laag. Vervolgens, terwijl de itemkaarten scrollen, tekent de GPU alleen de delen die binnen die markeringen vallen. Alles wat buiten het frame valt, verschijnt gewoon niet. Je kunt zelfs een geknipt paneel in een ander paneel plaatsen, en de stencilbuffer houdt bij waar hun grenzen elkaar overlappen.

Met stencil knippen ingeschakeld, kan een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  die alleen knippen nodig heeft, zijn inhoud rechtstreeks tekenen, zonder door render-to-texture te gaan. Het komt allemaal neer op een paar instellingen. Zolang [GroepTransparantie](/docs/nl-nl/reference/engine/classes/CanvasGroup#GroupTransparency)  op 0 blijft, [GroepKleur3](/docs/nl-nl/reference/engine/classes/CanvasGroup#GroupColor3)  wit (255, 255, 255) blijft, en er geen [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  aan de groep is gekoppeld, kan de stencil het knippen zelf afhandelen. Verander een van die dingen, en de renderer gaat terug naar het tekenen van een aparte textuur zodat hij het effect op de groep als geheel kan toepassen.

Die besparingen kunnen zich opstapelen. In een voorbeeld dat Emily doorwerkte, kon een scherm met twintig knip-only [CanvasGroups](/docs/nl-nl/reference/engine/classes/CanvasGroup)  van twintig offscreen texturen naar geen enkele gaan.

### Wat er nog te oplossen valt

Er was echter een addertje onder het gras. Een stencilbuffer slaat gehele getallen op, dus elke pixel is ofwel binnen de knipgrens of erbuiten, met niets ertussen. Op zichzelf kan dat afgeronde randen er gekarteld uit laten zien naast de gladde hoeken die Roblox al tekent met een techniek die * signed distance fields*  wordt genoemd. Emily werkt aan een manier om een vage, vervagende rand rond die geknipte randen toe te voegen om ze gladder te maken.

Het werkend krijgen van stencil knippen op alle grafische platforms van Roblox was een andere uitdaging. Ondersteuning toevoegen betekende wijzigingen aan de grafische backends die op iOS, Android, Mac, Windows, PlayStation, Xbox en VR worden gebruikt. Emily zegt dat dat het moeilijkste deel van het project was: ervoor zorgen dat de nieuwe aanpak overal waar Roblox draait, kan werken.

Totdat stencil knippen wordt uitgebracht, is een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  nog steeds de manier om inhoud binnen een curve te houden, maar zodra dat gebeurt, gaat de opbrengst verder dan alleen geheugen besparen. De textuur achter een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  is momenteel beperkt tot 1024 bij 1024 pixels, en aangezien een knip-only groep zijn inhoud rechtstreeks kan tekenen, kan het team die limiet opheffen en een groot geknipt paneel zoals je winkellmenu in volledige resolutie laten renderen.

Makers gaan deze functies niet één voor één gebruiken. Ze zullen een schaduw op een afgerond paneel plaatsen, een verloop aan de koptekst toevoegen, het vullen met scrollende kaarten, en dan besluiten dat het geheel twee keer zo breed moet zijn. Of ietsjes gekanteld. Of samengedrukt op een telefoonscherm.

Misschien geef je je zwaardwinkeltje een slank, elegant menu. Iemand anders kan diezelfde tools gebruiken om een ingewikkeld ruimteschipdashboard te bouwen, terwijl een andere maker een interface maakt die eruitziet alsof deze om twee uur 's nachts met een krijtje is getekend.

De renderer hoeft geen goede smaak te hebben. Het moet makers gewoon de vrijheid geven om de hunne uit te oefenen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
