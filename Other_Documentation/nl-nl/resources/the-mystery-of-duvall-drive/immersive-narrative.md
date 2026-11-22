<!-- Source: https://create.roblox.com/docs/nl-nl/resources/the-mystery-of-duvall-drive/immersive-narrative -->

Indringend verhaal | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Het mysterie van Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)

# Indringend verhaal

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Net als de [Beyond the Dark](/docs/nl-nl/resources/beyond-the-dark)  demo, was een van onze vroegste beslissingen om zoveel mogelijk van de gameplay en het verhaal diegetisch binnen de wereld zelf te vertellen. Dit kan een moeilijk proces zijn wanneer je zowel de voortgang aan de speler wilt communiceren via de gebruikersinterface, terwijl je ze ook het gevoel wilt geven dat ze echt binnen de wereld zijn die je hebt gebouwd. Om deze doelen voor onze game te bereiken, hebben we de manier waarop we informatie aan spelers communiceren opgedeeld in vier technieken:

1.

Visuele aanwijzingen  - Objecten, afbeeldingen of de rangschikking van middelen die passief het verhaal versterken of hints geven aan de speler wanneer het logisch is voor de wereld.

2.

Verhaal  - Wanneer een speler op specifieke items in het huis klikt/tikt, wordt belangrijke informatie over het verhaal op het hele scherm  weergegeven. Dit verhaal is alleen zichtbaar voor de speler die op het object heeft geklikt/getikt. De toon is altijd informatief in toon en formulering.

3.

Denkballonnen  - Wanneer een speler op specifieke items in het huis klikt/tikt, wordt een tekstdialoog "reactie" dichtbij het object  weergegeven. Dit verhaal is alleen zichtbaar voor de speler die op het object heeft geklikt/getikt. De toon is altijd eerste persoon en observerend.

4.

Aankondigingen  - Wanneer een speler op een gecorrumpeerd item in het huis klikt/tikt, wordt derde persoon dialoog op elk spelersscherm tegelijk  weergegeven. Dit verhaal brengt soms alle spelers over naar de gecorrumpeerde staat van de kamer waarin ze zich bevinden.

In deze sectie zullen we demonstreren hoe we deze technieken en specifieke functies hebben gebruikt om spelers in ons verhaal onder te dompelen, terwijl we tegelijkertijd verkenning aanmoedigen, voortgang communiceren en de gameplay zowel intiem voor de individuele speler als eerlijk in een multiplayer game houden.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overview-visual-cues.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overview-announcement.png) Een aankondiging op het schermoverlay van de interne gedachten van het personage.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overview-thought-bubble.png) Een denkballon, of object-specifieke dialoog, die wordt weergegeven wanneer je bepaalde objecten selecteert.

## [Visuele aanwijzingen](#visuele-aanwijzingen)[](#visuele-aanwijzingen)

Een visuele aanwijzing is een belangrijk hulpmiddel om zowel het verhaal te versterken als spelers te vertellen wat ze moeten weten over hun doel zonder woorden te gebruiken . Door een rangschikking van middelen, zoals schoolborden, standbeelden en behang, waren we in staat om passief een diepte van informatie over de hoofdpersonages van Duvall Drive te bieden, evenals begeleiding over hoe puzzels op te lossen zonder dat we invasieve UI-elementen hoefden op te nemen. We begonnen dit proces door eerst uit te zoeken wat we de speler wilden communiceren, en vervolgens hoe het logisch zou zijn om dat binnen de wereld van onze game te communiceren. Bijvoorbeeld, we wilden dat spelers begrepen hoe geobsedeerd de grootvader was in zijn missie om de dood te tarten, dus lieten we zijn kamer in wanorde achter met veel van zijn onderzoek en verschillende muren met zijn gekrabbelde gedachten.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/grandfather-room.png) Krabbelingen door de kamer van de grootvader communiceren de compulsieve aard van de grootvader.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/dog-statue.png) Een overvloed aan sculpturen en referentiefoto's toont aan hoe de dochter een kunstenaar is.

Onze eerste regel was dat als we een visuele aanwijzing wilden gebruiken om spelers iets te leren, deze een reden moet hebben om te bestaan, zelfs als er geen spelers aanwezig zijn. Als we een gigantisch bord met duidelijke instructies over wat te doen voor een puzzel zouden plaatsen, zou dit misplaatst lijken binnen het huis. Als we echter een grootvader vaststelden die geconsumeerd was door het tekenen op alles, inclusief de muren van zijn slaapkamer, is het veel geloofwaardiger om een schoolbord te hebben met zijn plan dat is gekrabd voor de speler om te volgen.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/chalkboard.png)

Onze tweede regel was dat we spelers niet altijd hoeven te vertellen wat ze moeten doen of hoe ze puzzels moeten oplossen, omdat ze inzicht hebben in hun omgeving. Soms is een gevallen elektriciteitslijn in een plas water voldoende als visuele aanwijzing om te communiceren dat spelers in gevaar zijn om geëlektrificeerd te worden als ze in die richting blijven bewegen.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/power-line.png)

## [Verhaal](#verhaal)[](#verhaal)

Naast het gebruik van visuele aanwijzingen om spelers passief te begeleiden, kozen we er ook voor om belangrijke informatie over het verhaal van de familie op het hele scherm  weer te geven als een voorloper om de puzzel van de kamer te starten telkens wanneer een speler op specifieke items in het huis klikte of tikte. Om spelers naar de objecten te leiden die ze moesten selecteren om het verhaal weer te geven, gebruikten we het nieuwe highlight visuele effect om specifieke objecten te laten opvallen ten opzichte van hun omgeving. Dit effect stelt je in staat om objecten te omtrekken en/of te overlappen met een specifieke kleur die past bij de vorm van het object zelf, en te kiezen of andere objecten de highlight kunnen verbergen als ze dichter bij de camera zijn.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-4.png)

We initially used [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  for every object a player could interact with, but the visual noise was overwhelming and players wouldn't clearly know what to interact with to read the lore. We decided to only use it to highlight items that were either corrupted or dangerous, and this visual feedback allowed players to easily drive the story forward.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/dog-statue-lore.png) Leuke feit: we hadden oorspronkelijk verhaal op alles wat je kon klikken! Dit was niet nuttig omdat spelers niet zeker wisten welke informatie belangrijk was en wat alleen voor de sfeer was. Uiteindelijk hebben we veel van het verhaal verwijderd en visuele aanwijzingen gebruikt om de rest van het verhaal aan de verbeelding van de speler over te laten.

Nadat de speler op het object met het verhaal had geklikt, hadden we een manier nodig om de informatie bovenaan het scherm weer te geven. We besloten een overlay te maken door een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  te gebruiken als onze on-screen UI-container met een kind [Frame](/docs/nl-nl/reference/engine/classes/Frame)  om de grootte en herverdeling van zijn kinderen [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  en [ImageLabels](/docs/nl-nl/reference/engine/classes/ImageLabel)  te regelen. We stelden de posities en schalen van de [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  en [ImageLabels](/docs/nl-nl/reference/engine/classes/ImageLabel)  eigenschappen in zodat ze visueel bij elkaar pasten en zouden schalen voor verschillende apparaten die spelers gebruiken om toegang te krijgen tot de game.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/jacob-photo-album.png)

[TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  en [ImageLabels](/docs/nl-nl/reference/engine/classes/ImageLabel)  beïnvloeden visuele elementen van hun respectieve tekst en afbeeldingen, inclusief hun kleur, transparantie, grootte en rangschikking. Voor [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  specifiek, kun je hun [TextLabel.TextScaled](/docs/nl-nl/reference/engine/classes/TextLabel#TextScaled)  en [TextLabel.RichText](/docs/nl-nl/reference/engine/classes/TextLabel#RichText)  eigenschappen aanpassen om de lay-out en visuele styling van tekst te regelen. [TextLabel.TextScaled](/docs/nl-nl/reference/engine/classes/TextLabel#TextScaled)  stelt je in staat om tekst te schalen om de hele ruimte van het bovenliggende UI-element in te vullen, en [TextLabel.RichText](/docs/nl-nl/reference/engine/classes/TextLabel#RichText)  stelt je in staat om eenvoudige opmaak-tags te gebruiken om secties van tekst in vet, cursief, kleur of zelfs verschillende lettertypen te stylen.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/lore-template.png)

We wisten dat spelers deze game vanaf verschillende apparaten zouden benaderen, waaronder pc, console en mobiele apparaten, en ze moesten in staat zijn om ofwel te klikken of het scherm aan te tikken om met de game te interageren. We wilden geen hoop knoppen op het scherm die afleiden van het verhaal, dus maakten we een onzichtbare terugknop ter grootte van het hele scherm, zodat spelers overal op de lore-overlay konden klikken of tikken om de inhoud te sluiten en terug te keren naar de gameplay.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/overlay-back-button.png)

## [Denkballonnen](#denkballonnen)[](#denkballonnen)

We hadden een manier nodig voor het personage van de speler om ideeën aan de speler te communiceren, zoals het bieden van extra narratieve smaak of het versterken van wat ze moesten doen. Onze oplossing was om denkballonnen, of tekstreacties van het personage van de speler , weer te geven nabij niet-verhaalobjecten telkens wanneer de speler deze selecteerde. Dit verhaal wordt alleen weergegeven aan de speler die op het object heeft geklikt of getikt, en de toon is altijd eerste persoon en observerend.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/barn-owl-thought-bubbles.png) Een relatief eenvoudig maar krachtig systeem om de wereld te laten reageren op de interacties van de speler!

Om denkballonnen te creëren, hebben we een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  met een kind [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  aan niet-verhaalobjecten gekoppeld. Dit stelde ons in staat om dialoog in de 3D-ruimte nabij het object weer te geven zonder dat de tekst de hele schermruimte in beslag nam. Vergelijkbaar met ons proces bij het creëren van verhaal, gebruikten we de [TextLabel.RichText](/docs/nl-nl/reference/engine/classes/TextLabel#RichText)  eigenschap om de tekst te stylen en visuele effecten toe te voegen, zoals een ander buitenaards wezen dat de gedachten van de speler onderbrak. Het volgende is een voorbeeld van RichText HTML die is gebruikt om de afbeelding hieronder te maken.

"Wat is…dit…<br/><stroke color="#dcc7ff" joins="miter" thickness="2" transparency="0.5"><font size="60"><font color="rgb(10,8,11)"><i>....honger….leegte….trek…</i></font></font></stroke>

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/richtext-thought-bubble.png)

Door [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  in plaats van afbeeldingen te gebruiken, hielden we de tekst leesbaar door Roblox, en konden we deze inhoud automatisch lokaliseren en toegankelijk maken voor veel meer spelers zonder iets te hoeven doen! Voor meer informatie over dit proces, zie [automatische vertalingen](/docs/nl-nl/production/localization/automatic-translations) .

## [Aankondigingen](#aankondigingen)[](#aankondigingen)

Hoewel we wilden dat het personage van de speler reacties had op de wereld, wilden we ook dat de wereld zelf reageerde op hun aanwezigheid. Om dit doel te bereiken, hebben we aankondigingen opgenomen, of derde persoon dialoog, die op elk spelersscherm tegelijk  wordt weergegeven. Vergelijkbaar met het verhaal, hebben we aankondigingen gemaakt door een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  te gebruiken als onze on-screen UI-container met een kind [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) . We gebruikten ook de [TextLabel.RichText](/docs/nl-nl/reference/engine/classes/TextLabel#RichText)  eigenschap om de kleur, het lettertype en de grootte van de dialoog te veranderen om verschillende "entiteiten" die met de spelers in het huis spraken over te brengen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-white.png) Aankondigingen met gewone witte tekst waren de reactie van het personage van de speler die algemeen was voor een gebied, niet een object zoals de verhaal narratieve techniek.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-purple.png) Aankondigingen met paarse tekst waren de reactie van een corrupte entiteit.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-yellow.png) Aankondigingen met gele tekst waren de reactie van een herstelde entiteit.

Door de [TextLabel.RichText](/docs/nl-nl/reference/engine/classes/TextLabel#RichText)  eigenschap te gebruiken en enkele HTML-commando's erin te geven om veranderingen aan te drijven, konden we ook wijzigingen halverwege de zin aanbrengen! Bijvoorbeeld, de volgende rich text markup stelde ons in staat om de reactie van het personage van de speler te onderbreken door de gedachten van de corrupte entiteit:

Wat is…dit…<br/><stroke color="#dcc7ff" joins="miter" thickness="2" transparency="0.5"><font size="60"><font color="rgb(10,8,11)"><i>....honger….leegte….trek…</i></font></font></stroke>

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/announcements-interrupt.png)

We hadden verschillende van dit soort aankondigingen, die ofwel werden geactiveerd door onzichtbare deelvolumes waar spelers in liepen, of door bepaalde doelen te voltooien. Om tientallen individuele [ScreenGuis](/docs/nl-nl/reference/engine/classes/ScreenGui)  te vermijden, gebruikten we een apart script in de demo dat ons in staat stelde om de tekst te bieden die het script vervolgens aan een enkel object toevoegde dat we StoryNote  noemden in onze [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  map. Dit object was een enkele [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  met een kind [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) . Met behulp van scripting konden we elke zin die we wilden rechtstreeks in de enkele [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  injecteren, wat het veel gemakkelijker maakte om wijzigingen aan te brengen terwijl we uitvonden hoe en wat we aan de speler wilden communiceren!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/storynote-object.png) StoryNote was een object dat we aanriepen voor alle instanties die het via script activeerden. Diezelfde scripts boden de tekst en opmaak die we voor elk evenement wilden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/example-script.png) Voorbeeld van een script dat dat object aanroept en de tekst definieert, per evenement.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/immersive-narrative/blank-textlabel.png) De TextLabel was eigenlijk leeg, en met behulp van scripts injecteerden we de RichText zoals nodig in hetzelfde object.

[Volgende](/docs/nl-nl/resources/the-mystery-of-duvall-drive/stream-in-immersion)[Vorige](/docs/nl-nl/resources/the-mystery-of-duvall-drive/materialize-the-world)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
