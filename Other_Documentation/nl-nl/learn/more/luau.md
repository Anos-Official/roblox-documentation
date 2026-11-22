<!-- Source: https://create.roblox.com/docs/nl-nl/learn/more/luau -->

Hoe Lua Luau werd | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

Meer informatie

![Een collage van snapshots op een disco dansvloer, inclusief Roblox Studio en vlaggenstands uit 2007, Dave Baszucki op een banenbeurs in 2007, de Roblox homepage van 2019, sleutelkunst voor Remedy's Alan Wake 2, twee Luau codefragmenten uit het artikel, en Hina, de Luau mascotte.](https://prod.docsiteassets.roblox.com/assets/resources/luau/cover-collage.jpg)

# Hoe Lua Luau werd

Roblox koos Lua omdat het klein, snel en gemakkelijk te leren was. Twintig jaar later is het behouden van die eigenschappen een verrassend gecompliceerde engineeringtaak geworden.

[

Probeer Luau](https://play.luau.org/)[

Bekijk op GitHub](https://github.com/luau-lang/luau)

## In dit artikel

1. [Chapter 01 · Waarom Lua Waarom Roblox Lua koos](#small-language)
2. [Chapter 02 · Hoe scripts draaien Herbouwen hoe scripts draaien](#new-engine)
3. [Chapter 03 · Fouten spotten Studio leren om fouten te spotten](#type-checker)
4. [Chapter 04 · Buiten Roblox Luau buiten Roblox](#beyond-roblox)

Je bouwt een disco-thema obby in Studio. Je hebt zwevende platforms boven een lavaput uitgelijnd, een paar draaiende spiegelbollen verspreid en het beste deel voor de finishlijn bewaard: een dansvloer. Elke tegel moet van kleur veranderen wanneer iemand erop stapt.

Elke tegel op de dansvloer voert dezelfde vier regels code uit.

Je begint met één tegel en vier regels code:

```

local tile = script.Parent

tile.Touched:Connect(function()

    tile.BrickColor = BrickColor.random()

end)

```

Je drukt op Play , maakt het over de lava en springt op de tegel. Het wordt blauw. Je springt eraf en landt weer, en deze keer is het geel. Dan roze. Er is nog niet veel van een spel hier, maar het is verrassend bevredigend om iets te zien gebeuren gewoon omdat je het hebt gezegd.

Je hebt niet verklaard wat voor soort waarde tile  is, geen geheugen beheerd, of veel nagedacht over hoe het script daadwerkelijk draait — je was te druk bezig om niet in de lava te vallen. Roblox moet ondertussen al die dingen in de gaten houden terwijl de rest van het spel doorgaat, of de code nu toebehoort aan een beginnersdansvloer of een uitgestrekte ervaring gebouwd door een professioneel team.

De taal die het werk doet is Luau, de afstammeling van Lua van Roblox. Wat begon als een manier om gedrag te geven aan een wereld van onderdelen, de blokken waarmee makers bouwen, draait nu alles van gameplay tot gebruikersinterfaces. Het helpt ook de eigen app en Studio-tools van Roblox aan te drijven, en heeft zelfs zijn weg gevonden in games gemaakt door andere studio's, waaronder * Alan Wake 2*  en, meer recent, * Control Resonant* . De taal is in de loop der jaren aanzienlijk geavanceerder geworden, ook al is het schrijven van die eerste vier regels niet moeilijker geworden.

Chapter 01  · Waarom Lua

## Waarom Roblox Lua koos

Roblox had een manier nodig voor makers om hun eigen spelregels te schrijven, en een kleine taal uit Brazilië paste perfect.

Lua begon in Rio de Janeiro in 1993, toen drie onderzoekers van een computergraphicsgroep — Roberto Ierusalimschy, Luiz Henrique de Figueiredo en Waldemar Celes — een programmeertaal nodig hadden die ze in andere programma's konden stoppen. Ze noemden het Lua, Portugees voor maan.

Het was ontworpen om een goede gast te zijn. Lua leverde de taal, terwijl het programma dat het hostte de interessante dingen leverde om mee te werken. Stop het bijvoorbeeld in een game-engine, en scripts konden interageren met personages, geluiden en fysica zonder de engine zelf te hoeven draaien. Tegen het begin van de jaren 2000 hadden game-ontwikkelaars veel toepassingen gevonden voor iets dat klein, snel en relatief gemakkelijk te leren was.

Roblox had een bijzonder goede reden om geïnteresseerd te zijn. De vroege werelden bestonden uit onderdelen en fysica: je kon een toren bouwen en deze omverwerpen of een auto in elkaar zetten en kijken of deze de rit naar beneden overleefde. Fysica alleen was echter niet genoeg om elk soort spel te maken.

![Dave Baszucki staat naast een Roblox-stand op een banenbeurs aan Stanford, naast een poster die zegt "We zijn op zoek naar geweldige softwareontwikkelaars."](https://prod.docsiteassets.roblox.com/assets/resources/luau/stanford-job-fair-2007.jpg) Roblox mede-oprichter en CEO Dave Baszucki werft op een Stanford startup banenbeurs in maart 2007.

Neem Capture the Flag, waar iemand moet opmerken wanneer een speler de vlag oppakt, punten moet toekennen en de vlag terug moet plaatsen. Roblox leverde aanvankelijk dat gedrag als een engine-functie, een klasse genaamd FlagStand , die perfect werkte voor Capture the Flag maar niet veel zou helpen met een huisdier-simulator, een winkel, of een spel waarvan het hele concept inhield dat mensen in bananen werden veranderd.

![Vier vlaggenstands in rood, blauw, geel en groen, elk met een vlag met het Roblox-logo.](https://prod.docsiteassets.roblox.com/assets/resources/luau/flag-stands-2007.png) Vlaggenstands van Roblox's Capture the Flag-release in juni 2007, waarmee makers een CTF-spel konden bouwen zonder "scripting vereist."

Rond 2006 adopteerde Roblox Lua 5.1, waardoor makers hun eigen regels konden uitvinden in plaats van te wachten tot het engine-team ze bouwde. Als iemand een spel over bananen wilde maken, kon dat gewoon.

![Roblox Studio in februari 2007, met een speler die bij een deur staat in de game-weergave en het Output-venster dat herhaaldelijk "Mens heeft deur aangeraakt" afdrukt vanuit een script van een maker.](https://prod.docsiteassets.roblox.com/assets/resources/luau/studio-door-script-2007.png) Roblox Studio in februari 2007, van een scriptingtutorial op de Roblox-blog. Een script van een maker drukt "Mens heeft deur aangeraakt" af elke keer dat een speler het aanraakt.

Chapter 02  · Hoe scripts draaien

## Herbouwen hoe scripts draaien

Grotere, ambitieuzere games betekenden dat scripts meer van elke frame in beslag namen. In 2019 verving Roblox de code die ze uitvoert en probeerde niet één daarvan onderweg te breken.

Makers maakten goed gebruik van die vrijheid, en naarmate Roblox-ervaringen groeiden in games met uitgebreide inventarissen, economieën en allerlei systemen die op de achtergrond draaiden, vond de oude Lua-interpreter zichzelf met aanzienlijk meer werk te doen. De ingenieurs van Roblox waren ook andere delen van de engine aan het versnellen, wat betekende dat de tijd die aan het draaien van scripts werd besteed steeds moeilijker te negeren werd.

![Vier in-game weergaven van het Bloxy Theater, vol avatars die aan ronde tafels zitten, met een gouden Bloxy-standbeeld op het podium.](https://prod.docsiteassets.roblox.com/assets/resources/luau/bloxy-awards-2019.jpg) Spelers gepakt in het Bloxy Theater voor Roblox's 6e jaarlijkse Bloxy Awards in 2019.

In juni 2019 kondigde Arseny Kapoulkine, een ingenieur die hielp bij de ontwikkeling van Luau, aan dat Roblox een snellere implementatie van Lua aan het testen was. Het team had verschillende opties overwogen en besloot uiteindelijk om een nieuwe te bouwen omdat, schreef hij, "we gek zijn."

Er waren alternatieven, waaronder LuaJIT, een uitzonderlijk snelle implementatie van Lua, maar het aannemen van een van hen was niet zo eenvoudig als het verwisselen van een component en het er bij laten. Roblox had zijn eigen wijzigingen aangebracht in Lua 5.1, zoals striktere beveiliging en een uitgebreidere globale omgeving. Het moest ook een breed scala aan apparaten ondersteunen en wilde voldoende controle over de implementatie om deze te blijven verbeteren. Overstappen naar een nieuwere versie van gewone Lua was ook geen gemakkelijke uitweg — Roblox had al jaren scripts geschreven tegen Lua 5.1, en nieuwere versies gedroegen zich niet altijd op dezelfde manier.

Arseny begon met een prototype van een nieuwe compiler en interpreter, leende ideeën van andere snelle taal-runtime's en experimenteerde met een paar benaderingen die geschikt waren voor Lua zelf. Het begreep slechts een klein subset van de taal, maar op de code die het kon draaien, was het aanzienlijk sneller dan de bestaande implementatie van Roblox. Het bemoedigende deel was dat het idee leek te werken. Het minder bemoedigende deel was dat het team nu de rest van Lua moest ondersteunen, jaren van obscure gedragingen moest reproduceren en de vervanging over een live platform moest uitrollen — een taak die Arseny beschreef als "ontzettend, maar meer of minder 'gewoon' engineering."

>

"Ontzettend, maar meer of minder 'gewoon' engineering."

Arseny Kapoulkine

In plaats van de hele runtime in één keer opnieuw op te bouwen, concentreerde het team zich op de delen die verantwoordelijk waren voor het omzetten van scripts in instructies en het uitvoeren ervan: de compiler, bytecode-indeling en interpreter. Veel van de bestaande machines, inclusief de bibliotheken en garbage collector, bleven voorlopig waar ze waren. Er zouden later genoeg kansen zijn om die te verbeteren, ervan uitgaande dat ze eerst de nieuwe implementatie konden laten draaien zonder iets te breken.

![Een script gaat door de compiler naar bytecode en vervolgens naar de runtime op het apparaat van de speler. De typechecker zit naast het script in Studio, en de garbage collector draait op de achtergrond.](https://prod.docsiteassets.roblox.com/assets/resources/luau/life-of-a-script.svg) Het pad dat een script volgt van Studio naar het apparaat van de speler. De typechecker helpt terwijl je bewerkt, maar verandert nooit hoe het script draait.

En dat was het moeilijke deel. Lua's flexibiliteit was een van de redenen waarom Roblox het in de eerste plaats had gekozen, maar het betekende ook dat ontwikkelaars perfect geldige code konden schrijven die bepaalde optimalisaties verrassend ongemakkelijk maakte.

### Fastcall

Een van Arseny's favoriete voorbeelden is * fastcall* , een optimalisatie voor het aanroepen van bekende functies zoals math.sqrt . Je zou denken dat het berekenen van een vierkantswortel een eenvoudige zaak zou zijn om sneller te maken, behalve dat Lua scripts toestaat om ingebouwde functies te vervangen door hun eigen versies, zodat math.sqrt  niet noodzakelijkerwijs betekent wat de naam suggereert. Luau omzeilt dit door te controleren of de functie nog steeds de originele is voordat het een snellere route door de interpreter neemt. Als iemand het heeft vervangen, draait de aanroep normaal in plaats daarvan, waardoor het gedrag behouden blijft waar ontwikkelaars mogelijk al op vertrouwden.

![Een math.sqrt-aanroep bereikt een controle die vraagt of math.sqrt nog de originele is. Als dat zo is, neemt het het snelle pad; als dat niet zo is, maakt het een gewone aanroep.](https://prod.docsiteassets.roblox.com/assets/resources/luau/fastcall.svg) Zelfde resultaat op beide manieren. De snelkoppeling geldt alleen wanneer het niet kan veranderen wat het script betekent.

#### Probeer het: vergelijk de bytecode

Hier is hoe die snelkoppeling eruitziet vanuit de kant van de compiler. De twee functies hieronder berekenen beide de afstand tussen twee punten. De ene vindt de vierkantswortel met math.sqrt , en de andere gebruikt customSqrt , een functie die hetzelfde antwoord op een andere manier krijgt. Beide drukken hetzelfde nummer af, maar ze compileren niet naar dezelfde instructies.

Luau markeert de snelkoppeling met een speciale instructie genaamd FASTCALL , die de interpreter vertelt dat het mogelijk is om het gebruikelijke werk van functie-aanroepen over te slaan.

Beide functies drukken 5  af. Vergelijk hun bytecode. Welke gebruikt FASTCALL , en waarom kan Luau dezelfde snelkoppeling niet nemen voor customSqrt ?

Iets verderop kreeg het project ook een naam. Luau begon als een interne codenaam voorgesteld door de vrouw van ingenieur Andy Friesen, die blijkbaar een talent heeft voor woordspellen. Hij herinnert zich Luau als haar iets belachelijke kijk op "Lua, maar een beetje extra," wat bleek te kloppen voor een taal die nog steeds herkenbaar Lua was maar geleidelijk iets van zichzelf aan het worden was. Het team vond het ook leuk dat de naam het project niet permanent aan Roblox verbond, en tegen de tijd dat ze iets officieels moesten vaststellen, was iedereen al gewend geraakt om het Luau te noemen. Tijdens RDC 2019 grapte Arseny dat het verhaal achter de naam "gecompliceerd" was.

### De uitrol

De uitrol, aan de andere kant, was echt gecompliceerd.

Roblox kon de oude en nieuwe virtuele machines niet naast elkaar in hetzelfde proces draaien, en het uitschakelen van de nieuwe zou niets doen voor servers die deze al draaiden. Een volledige terugrol zou een grid-reset kunnen betekenen, waardoor spelers over het platform werden losgekoppeld, terwijl het testen van elk script van elke maker van tevoren ook niet realistisch was. Scripts waren vaak afhankelijk van de ervaringen om hen heen, en Roblox was begrijpelijkerwijs terughoudend om de ongepubliceerde code van makers te inspecteren zonder hun toestemming.

Tijdens de eerste uitrol onthulde een buitengewoon lange keten van methode-aanroepen een limiet die niemand in het team had voorzien. Arseny herinnert zich een script, mogelijk gegenereerd door een aangepaste animatie-editor, dat iets als duizend keyframes in één enorme expressie opsloeg. Het was in wezen animation:AddKeyframe(...)  dat keer op keer werd herhaald, waarbij elke aanroep in de volgende voedde totdat het geheel een enkele, zeer lange regel code werd.

Er was niets bijzonder ongewoons aan een individuele aanroep, maar de nieuwe compiler reserveerde een tijdelijke register voor elke aanroep, en de virtuele machine had een limiet van 256 registers. Uiteindelijk raakte de compiler zonder ruimte, waardoor het script niet kon compileren en de animaties die ervan afhankelijk waren niet konden werken.

![Een keten van animation:AddKeyframe-aanroepen die in een 16 bij 16 grid van 256 registers voeden die één register per aanroep vullen, met de laatste rij in het rood.](https://prod.docsiteassets.roblox.com/assets/resources/luau/rollout-register-limit.svg) Elke aanroep in de keten reserveerde een ander tijdelijk register totdat de compiler opraakte bij 256.

Niemand had ondersteuning beloofd voor duizend aaneengeschakelde methode-aanroepen, maar ontwikkelaars schrijven geen software alleen op basis van wat de documentatie belooft. Ze schrijven tegen wat daadwerkelijk werkt, en soms is wat werkt een duizend methode-aanroepen die aan elkaar zijn geregen op een manier die niemand had gedacht te testen.

Het team repareerde de compiler en probeerde het opnieuw. Andere randgevallen zouden naar voren komen terwijl ontwikkelaars de grenzen van de nieuwe implementatie verkenden, maar op 28 augustus 2019 was de nieuwe Luau virtuele machine live op de client- en serverplatforms van Roblox, met de overgrote meerderheid van bestaande scripts die bleven werken zoals ze altijd hadden gedaan.

Voor al de moeite die gemoeid was met het vervangen van de machines achter elk Roblox-script, herinnerde Arseny zich later dat de meeste makers de overgang nauwelijks opmerkte. Roblox mede-oprichter Dave Baszucki noemde het "de ultieme soort contactloze functie."

>

"Luau, net als Lua voor het, is een relatief eenvoudige, imperatieve, dynamisch getypeerde programmeertaal."

Andy Friesen

Chapter 03  · Fouten spotten

## Studio leren om fouten te spotten

Luau's typechecker kan sommige bugs opvangen terwijl je nog code schrijft. Het moeilijke deel was leren wanneer niet te waarschuwen.

Scripts sneller maken was één probleem. Ontwikkelaars helpen om te begrijpen wat er mis was met hun code was een ander.

Naarmate de grootste games van Roblox groeiden van hobbyprojecten naar producties die werden onderhouden door teams van fulltime ontwikkelaars, werden zowel die games als de eigen app van Roblox moeilijker te onderhouden. "We hadden allemaal een probleem met bugs die gemakkelijk te spotten hadden moeten zijn voordat ze bij klanten kwamen," zegt Andy ([@fun_enthusiast](https://www.roblox.com/users/671461758/profile) ), die in 2018 bij Roblox kwam. Lua's flexibiliteit had het geweldig gemakkelijk gemaakt om te beginnen, maar de script-editor was niet altijd veel hulp zodra een project ingewikkeld werd — autocompleteren kon onbetrouwbaar zijn, en ontwikkelaars moesten vaak zelf uitzoeken wat voor soort waarde een variabele zou moeten bevatten.

Een typechecker kon daarbij helpen. Als je per ongeluk scroe  in plaats van score  typt, kan Studio de fout aanwijzen terwijl je aan het bewerken bent in plaats van je te laten ontdekken wanneer het spel draait. Beter nog, het kon vaak uitzoeken wat voor soort waarde je aan het behandelen was zonder je eerst om een type te vragen, wat betekende dat beginners door konden gaan met het schrijven van gewone Lua-stijl scripts terwijl ontwikkelaars die grotere projecten onderhouden konden kiezen voor striktere controles.

>

"We hadden allemaal een probleem met bugs die gemakkelijk te spotten hadden moeten zijn voordat ze bij klanten kwamen."

Andy Friesen

#### Probeer het: vind de bug

Hier is een bug die je zelf kunt proberen op te sporen. Een danser begint met 10 punten en verdient een bonus van 5 punten met een vermenigvuldiger van 2, dus ze zouden moeten eindigen met 20. Voer het script uit, werk uit waar het probleem is, en kijk dan wat de typechecker te zeggen heeft.

De danser zou moeten eindigen met 20 punten. Is het probleem in de score, de vermenigvuldiger, of de regel die het resultaat afdrukt? Voordat je het oplost, verwijder de -⁠-!strict  regel bovenaan en voer het script opnieuw uit om te zien wat de typechecker zegt zonder strikte modus. Zet de regel dan terug, vind de bug en los het op.

Een gewone tabel retourneert nil  wanneer je probeert een veld te lezen dat niet bestaat, dus het script crasht niet — het geeft je gewoon het verkeerde antwoord. De checker kan ondertussen zien dat dancer  een points -veld heeft en geen poins -veld, ook al heb je het niet verteld wat voor soort waarde dancer  zou moeten zijn.

Een typefout zoals dat opvangen is relatief eenvoudig. Weten wanneer je iemand niet moet waarschuwen bleek een veel moeilijker probleem te zijn.

Stel dat een script de score van een speler opzoekt, die een nummer kan zijn of nil  als de speler nog niets heeft verdiend. Het script controleert of de score bestaat voordat het enige wiskunde doet, zodat iemand die de code leest kan zien dat het gevaarlijke geval al is afgehandeld. Een typechecker die de logica van het programma niet nauwkeurig genoeg kan volgen, kan echter nog steeds volhouden dat de score mogelijk ontbreekt, waardoor de ontwikkelaar naar een waarschuwing kijkt voor een probleem dat ze al hebben opgelost.

Volgens Andy was de oorspronkelijke type-oplosser van Luau gebouwd rond een grotendeels top-down, single-pass ontwerp dat redelijk goed werkte voor eenvoudigere gevallen, maar steeds moeilijker te verlengen werd naarmate ontwikkelaars vroegen om meer gecompliceerde code te begrijpen. De beperkingen beïnvloedden ook autocompleteren, omdat als de checker niet kon uitzoeken wat een variabele op een bepaald moment in een script was, Studio niet betrouwbaar zijn eigenschappen of methoden kon voorstellen. Andy herinnert zich dat hij herhaaldelijk probeerde de inferentie voor veelvoorkomende Lua object-georiënteerde patronen te verbeteren zonder ontwikkelaars te dwingen om casts of annotaties toe te voegen, alleen om te ontdekken dat de resultaten niet nauwkeurig of betrouwbaar genoeg waren.

### De Nieuwe Type Oplosser

Uiteindelijk besloot het team de oplosser opnieuw op te bouwen in plaats van te blijven werken rond de beperkingen. De nieuwe aanpak kon volgen hoe een script de mogelijke types van een waarde verfijnde, een proces dat * type verfijning*  wordt genoemd, zodat iets dat eerder nil  had kunnen zijn, niet noodzakelijkerwijs onzeker bleef na een if -controle of een standaardtoewijzing. Het verschil klinkt misschien niet bijzonder dramatisch, maar voor een ontwikkelaar die probeert te begrijpen waarom Studio voortdurend perfect geldige code onderstreept, is het behoorlijk belangrijk.

#### Probeer het: volg de ontbrekende score

Hier is een voorbeeld. Een functie berekent de uiteindelijke score van een danser, maar hun bestaande score kan ontbreken, en een combo-vermenigvuldiger kan deze verhogen voordat een bonus van 5 punten wordt gegeven. Het script levert eerst een standaardwaarde, en Luau volgt die wijziging: tegen de tijd dat er enige wiskunde plaatsvindt, is de score een nummer.

Verwijder score = score or 0 . Welke regels markeert de checker? Probeer dan de ontbrekende score af te handelen met if score == nil then score = 0 end , of verplaats de standaardwaarde naar de return -regel in plaats daarvan.

Het team moest ook beslissen hoe veeleisend de checker moest zijn. Hunter Goldstein ([@MercuryBromine0](https://www.roblox.com/users/7329002687/profile) ), een ingenieur in het type-systeemteam, beschrijft nonstrict als gericht op fouten die de checker kan bepalen dat ze tijdens runtime zullen gebeuren, terwijl strict een ambitieuzer belofte maakt: "types liegen niet." Dat kan betekenen dat code wordt afgewezen die mogelijk succesvol kan draaien als de checker niet kan bewijzen dat het veilig is, wat een redelijke afweging is voor een ontwikkelaar die sterkere garanties wil, maar potentieel frustrerend voor iemand die net heeft uitgevonden hoe een blok van kleur te laten veranderen.

>

"Types liegen niet."

Hunter Goldstein

In november 2025 bereikte de Nieuwe Type Oplosser de algemene release, en werd de standaard voor scripts die nocheck en nonstrict-modus gebruikten, terwijl projecten in strikte modus op dat moment konden kiezen om in te stappen.

Chapter 04  · Buiten Roblox

## Luau buiten Roblox

Nadat Roblox Luau open source maakte, begonnen andere studio's het in hun eigen games te gebruiken.

Luau was aanvankelijk niet gebouwd met andere game-studio's in gedachten. Arseny wilde simpelweg vermijden dat de aangepaste versie van Lua van Roblox verstrikt raakte met de rest van de engine, tot het punt waarop zelfs het bouwen van de taal op zichzelf betekende dat Roblox-code die er niets mee te maken had, moest worden meegesleept. Toen hij begon met het werk aan Luau, maakte hij er een punt van om de taal gescheiden te houden, vooral omdat het het project gemakkelijker maakte om te ontwikkelen en te onderhouden.

Die beslissing bleek een onverwacht voordeel te hebben. Terwijl het team functies toevoegde zoals continue  en een typesysteem, begon Arseny te denken dat het zonde zou zijn als niemand buiten Roblox het resultaat kon gebruiken. In november 2021 werd Luau [open source](https://github.com/luau-lang/luau)  onder de MIT-licentie, waardoor andere ontwikkelaars de kans kregen om het in hun eigen software te plaatsen.

![Hina, een blauwe cartoon Hawaiiaanse monniksrob.](https://prod.docsiteassets.roblox.com/assets/resources/luau/hina.png) Hina, een Hawaiiaanse monniksrob en de officiële mascotte van de Luau-taal.

#### Probeer het: sla de gebroken tegels over

Sommige van Luau's toevoegingen zijn gemakkelijker te waarderen dan andere. Neem continue , waarmee een script de rest van één doorgang door een lus kan overslaan en doorgaan naar de volgende. In het onderstaande voorbeeld verdient een danser punten van elke tegel waarop ze stappen, maar gebroken tegels tellen niet mee.

De danser eindigt met 25 punten. Repareer de roze tegel door broken  op false  te zetten, voeg een tegel van je eigen toe, of verander de voorwaarde zodat het tegels met minder dan 10 punten overslaat.

### Andere studio's

Remedy Entertainment vond een gebruik voor Luau in * Alan Wake 2* , waarbij een propriëtaire scripttaal in de Northlight-engine werd vervangen door Luau, zodat gameplay- en visuele-effectenteams konden experimenteren zonder elke wijziging aan een engine-programmeur te hoeven vragen om deze te implementeren. Een voorbeeld was een weersysteem dat kon worden aangepast via een debugpaneel, waardoor kunstenaars en ontwerpers konden spelen met de sfeer van een scène zonder de onderliggende engine aan te raken. Remedy zei dat de stap hen ook in staat stelde om ongeveer 80.000 regels code te beëindigen die ze niet langer hoefden te onderhouden.

![Alan Wake 2 sleutelkunst: het gezicht van schrijver Alan Wake doemt op boven een rood verlichte bos, waar FBI-agent Saga Anderson staat met een zaklamp.](https://prod.docsiteassets.roblox.com/assets/resources/luau/alan-wake-2.jpg)

![Control Resonant sleutelkunst: een man in een versleten jas zwaait met een grote hamer boven een rode, verwoeste stadsgezicht.](https://prod.docsiteassets.roblox.com/assets/resources/luau/control-resonant.jpg)

Linden Lab had een ander probleem: Second Life had een runtime nodig voor door gebruikers geschreven scripts die veilig konden worden gesandboxed, gepauzeerd en tussen servers konden worden verplaatst, en na het overwegen van andere opties kozen de ontwikkelaars Luau als de basis voor hun SLua-werk.

De relatie begint ook in beide richtingen te werken. Volgens Andy droeg een ontwikkelaar bij Remedy een paar kleine taalfeatures bij terwijl hij aan * Alan Wake 2*  werkte, wat betekent dat sommige van de beslissingen die Luau nu vormgeven komen van mensen die games buiten Roblox maken.

Terug in Studio is de eerste tegel op je disco-vloer roze geworden. Er zijn meer tegels om aan te sluiten, een scoreteller om af te maken, en een behoorlijk goede kans dat iemand een manier vindt om over alle platforms te springen die je net de middag hebt besteed aan het rangschikken.

Je opent de script-editor opnieuw.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
