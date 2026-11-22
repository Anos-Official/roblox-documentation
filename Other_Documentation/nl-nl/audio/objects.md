<!-- Source: https://create.roblox.com/docs/nl-nl/audio/objects -->

Audio-objecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Audio](/docs/nl-nl/audio)

# Audio-objecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De modulaire audio-objecten van Roblox stellen je in staat om dynamische controle te hebben over geluid en spraakchat in je ervaringen. Bijna elk audio-object komt overeen met een echt audio-apparaat, en ze functioneren allemaal samen om audio vast te leggen en af te spelen zoals hun fysieke tegenhangers.

Bijvoorbeeld, elk audio-object valt conceptueel in de volgende categorieën:

-

Objecten die audio  streams produceren , zoals audio-spelers.

-

Objecten die audio  streams consumeren , zoals audio-emitters.

-

Objecten die audio  streams wijzigen , zoals audio-effecten.

-

Objecten die audio  streams van het ene audio-object naar het andere dragen , zoals draden.

Terwijl je deze gids doorleest en leert hoe al deze audio-objecten samenwerken om geluid uit te zenden, zul je leren hoe je muziek, geluidseffecten en de menselijke stem nauwkeurig kunt vastleggen en doorgeven van de ervaring naar de speler en vice versa.

[Sound](/docs/nl-nl/reference/engine/classes/Sound) , [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  en [SoundEffect](/docs/nl-nl/reference/engine/classes/SoundEffect)  objecten worden nu afgeraden ten gunste van de robuustere functionaliteit van audio-objecten.

## [Audio afspelen](#audio-afspelen)[](#audio-afspelen)

Om audio binnen je ervaring af te spelen, is het belangrijk om de rol van elk beschikbaar audio-object te begrijpen:

-

Een [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  laadt en speelt het audio-bestand  met behulp van een vast audio-assets ID.

-

Een [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  is een virtuele luidspreker  die audio in de 3D-omgeving uitzendt.

-

Een [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  is een virtuele microfoon  die audio uit de 3D-omgeving oppikt.

-

Een [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  is een fysiek hardware-apparaat  in de echte wereld, zoals een luidspreker of hoofdtelefoon.

-

Een [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  is een fysieke microfoon  in de echte wereld.

-

Het [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  object converteert tekst naar audio  met behulp van een kunstmatige menselijke stem.

-

Het [AudioSpeechToText](/docs/nl-nl/reference/engine/classes/AudioSpeechToText)  object converteert gesproken audio naar tekst .

-

Een [Wire](/docs/nl-nl/reference/engine/classes/Wire)  draagt audio-streams  van het ene audio-object naar het andere.

Hoe je deze audio-objecten samenvoegt, hangt af van of je audio rechtstreeks naar de luidspreker of hoofdtelefoon van de speler wilt uitzenden of vanuit objecten in de 3D-ruimte. De volgende secties beschrijven beide scenario's.

### [2D audio](#2d-audio)[](#2d-audio)

2D audio  is niet-directioneel geluid dat vanuit geen specifieke locatie speelt, en blijft op hetzelfde volume ongeacht de positie of oriëntatie van de speler in de 3D-ruimte. Dit type audio vereist drie audio-objecten:

-

Een audio-speler om een audio-stream te produceren.

-

Een fysiek hardware-apparaat om de audio-stream in de echte wereld af te spelen.

-

Een draad om de audio-stream van de audio-speler naar het uitvoerapparaat te dragen.

Om te demonstreren hoe je deze audio-objecten in Studio configureert voor 2D audio, vergelijkt het volgende diagram elk object met hun echte wereld audio-apparaat tegenhanger. Samengevat:

-

De [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  laadt en speelt je audio-assets met gespecificeerde instellingen.

-

De [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  stelt de speler in staat om de audio via hun luidspreker of hoofdtelefoon te horen.

-

De [Wire](/docs/nl-nl/reference/engine/classes/Wire)  verbindt met de audio-speler via zijn [SourceInstance](/docs/nl-nl/reference/engine/classes/Wire#SourceInstance)  eigenschap, en met het fysieke hardware-apparaat via zijn [TargetInstance](/docs/nl-nl/reference/engine/classes/Wire#TargetInstance)  eigenschap. Het fungeert dan als een brug om de audio-stream van de audio-speler naar het uitvoerapparaat van de speler te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/2D-Audio-Diagram.png)

Om niet-directionele audio af te spelen:

1.

In het Explorer  venster, ga naar SoundService  en voeg het volgende toe:

1.

Een AudioPlayer  object om een audio-bron te creëren.

2.

Een AudioDeviceOutput  object om een luidspreker te creëren die door de ervaring heen speelt.

3.

Een Wire  object om de stream van de audio-speler naar de luidspreker te verbinden.

2.

In het Properties  venster van het AudioPlayer  object:

1.

Stel AssetID  in op een geldig audio-assets ID. Als je geen eigen aangepaste audio hebt, kun je gratis te gebruiken audio-assets vinden in de Creator Store.

2.

Schakel Looping  in als je wilt dat je audio continu herhaald wordt.

3.

Stel Volume  in op de eenheid van amplitude die je wilt gebruiken om je audio af te spelen.

3.

In het Properties  venster van het Wire  object:

1.

Stel SourceInstance  in op de AudioPlayer  om aan te geven dat je de audio binnen deze specifieke audio-speler wilt afspelen.

2.

Stel TargetInstance  in op de AudioDeviceOutput  om aan te geven dat je de audio van deze specifieke luidspreker wilt afspelen.

Van hieruit kun je je niet-directionele audio activeren met scripts om het af te spelen wanneer spelers de ervaring betreden of als gevolg van een gameplay-evenement of UI-interactie. Voor codevoorbeeldreferenties voor deze gebruikssituaties, zie de [Voeg 2D audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-2D-audio)  tutorial.

### [3D audio](#3d-audio)[](#3d-audio)

3D audio  is directioneel geluid dat vanuit een specifieke locatie in de 3D-ruimte speelt, en dat in volume toeneemt of afneemt afhankelijk van de positie en oriëntatie van de speler ten opzichte van het geluid. Dit type audio vereist zes audio-objecten:

-

Een audio-speler om een audio-stream te produceren.

-

Een audio-emitter om de audio-stream binnen de omgeving uit te zenden.

-

Een luisteraar om de audio-stream uit de omgeving op te pikken.

-

Een fysiek hardware-apparaat om de audio-stream in de echte wereld af te spelen.

-

Twee draden: één om de audio-stream van de audio-speler naar de emitter te dragen, en een andere om deze van de luisteraar naar het uitvoerapparaat te dragen.

Om te demonstreren hoe je deze audio-objecten in Studio configureert voor 3D audio, vergelijkt het volgende diagram elk object met hun echte wereld audio-apparaat tegenhanger. Samengevat:

-

De [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  laadt en speelt je audio-assets met gespecificeerde instellingen.

-

De positie van de ouder van de [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  in de 3D-ruimte bepaalt waar dat audio binnen de omgeving uitzendt.

-

De [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  pikt audio op van de emitter vanuit de lokale camera of binnen het [Humanoid.RootPart](/docs/nl-nl/reference/engine/classes/Humanoid#RootPart)  van het speler-personage, afhankelijk van waar je de standaard luisteraarpositie instelt.

-

De [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  stelt de speler in staat om de audio via hun luidspreker of hoofdtelefoon te horen.

-

De eerste [Wire](/docs/nl-nl/reference/engine/classes/Wire)  verbindt met de audio-speler via zijn [SourceInstance](/docs/nl-nl/reference/engine/classes/Wire#SourceInstance)  eigenschap, en met de emitter via zijn [TargetInstance](/docs/nl-nl/reference/engine/classes/Wire#TargetInstance)  eigenschap. Het fungeert dan als een brug om de audio-stream van de audio-speler naar de emitter te dragen.

-

De tweede [Wire](/docs/nl-nl/reference/engine/classes/Wire)  verbindt met de luisteraar via zijn [SourceInstance](/docs/nl-nl/reference/engine/classes/Wire#SourceInstance)  eigenschap, en met het fysieke hardware-apparaat via zijn [TargetInstance](/docs/nl-nl/reference/engine/classes/Wire#TargetInstance)  eigenschap. Het fungeert dan als een brug om de audio-stream van de luisteraar naar het uitvoerapparaat van de speler te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/3D-Audio-Diagram.png)

Om positionele audio af te spelen:

1.

Kies waar je een AudioListener  wilt creëren wanneer spelers in de ervaring spawnen.

1.

In het Explorer  venster, selecteer SoundService .

2.

In het Properties  venster, stel ListenerLocation  in op een van de volgende opties:

-

Default  - Creëert en plaatst de luisteraar onder [Workspace.CurrentCamera](/docs/nl-nl/reference/engine/classes/Workspace#CurrentCamera)  in ervaringen die spraakchat inschakelen.

-

None  - Creëert geen luisteraar. Deze optie is nuttig als je een luisteraar via een script wilt creëren.

-

Character  - Creëert en plaatst een luisteraar onder het lokale speler-personage.

-

Camera  - Creëert en plaatst de luisteraar onder [Workspace.CurrentCamera](/docs/nl-nl/reference/engine/classes/Workspace#CurrentCamera) .

Wanneer je ListenerLocation  instelt op Character  of Camera , creëert de engine automatisch een [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object onder [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  tijdens runtime.

2.

In het Explorer  venster, ga naar het 3D-object waarvan je audio wilt uitzenden en voeg het volgende toe:

1.

Een AudioPlayer  object om een audio-bron te creëren.

2.

Een AudioEmitter  object om een positionele stream van het 3D-object uit te zenden.

3.

Een Wire  object om de stream van de audio-speler naar de audio-emitter te verbinden.

3.

In het Properties  venster van het AudioPlayer  object:

1.

Stel AssetID  in op een geldig audio-assets ID. Als je geen eigen aangepaste audio hebt, kun je gratis te gebruiken audio-assets vinden in de Creator Store.

2.

Schakel Looping  in als je wilt dat je audio continu herhaald wordt.

3.

Stel Volume  in op de eenheid van amplitude die je wilt gebruiken om je audio af te spelen.

4.

In het Properties  venster van het AudioEmitter  object, stel DistanceAttenuation  in op een volume-over-afstand curve die bepaalt hoe luid de luisteraar de emitter hoort afhankelijk van de afstand tussen hen.

Bijvoorbeeld, de volgende curve vermindert het volume van de audio met de helft wanneer de luisteraar 50 studs van de emitter verwijderd is, en vermindert dan scherp het volume tot nul wanneer de luisteraar 70 studs verwijderd is.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/DistanceAttenuation.png)

5.

In het Properties  venster van het Wire  object:

1.

Stel SourceInstance  in op de AudioPlayer  om aan te geven dat je de audio binnen deze specifieke audio-speler wilt afspelen.

2.

Stel TargetInstance  in op de AudioEmitter  om aan te geven dat je de audio van deze specifieke audio-emitter wilt afspelen.

Van hieruit kun je je directionele audio activeren met scripts om het af te spelen wanneer spelers de ervaring betreden of als gevolg van een gameplay-evenement of UI-interactie. Voor codevoorbeeldreferenties voor deze gebruikssituaties, zie de [Voeg 3D audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-3D-audio)  tutorial.

### [Tekst-naar-spraak](#tekst-naar-spraak)[](#tekst-naar-spraak)

Alle tekst voor [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  objecten moet voldoen aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) .

Tekst-naar-spraak  (TTS ) is een vorm van assistieve technologie die tekststrings omzet in spraakgeluiden met behulp van een kunstmatige stem. Dit type audio vereist vijf audio-objecten:

-

Een audio-spraakgenerator om tekst te laden en om te zetten in audio.

-

Een audio-emitter om de audio-stream binnen de omgeving uit te zenden.

-

Een luisteraar om de audio-stream uit de omgeving op te pikken.

-

Een fysiek hardware-apparaat om de audio-stream in de echte wereld af te spelen.

-

Voor 2D audio - Een draad om de audio-stream van de audio-spraakgenerator naar het uitvoerapparaat te dragen.

-

Voor 3D audio - Twee draden: één om de audio-stream van de audio-spraakgenerator naar de emitter te dragen, en een andere om deze van de luisteraar naar het uitvoerapparaat te dragen.

Hoe je deze objecten configureert, hangt af van of je 2D TTS-audio of 3D TTS-audio wilt creëren. Voor meer details over elk proces, klik tussen de volgende tabbladen.

2D Tekst-naar-Spraak 3D Tekst-naar-Spraak

Om te demonstreren hoe je deze audio-objecten in Studio configureert voor 2D TTS-audio, vergelijkt het volgende diagram elk object met hun echte wereld audio-apparaat tegenhanger. Samengevat:

-

Het [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  object laadt en zet tekststrings om in spraakgeluiden.

-

De [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  stelt de speler in staat om de audio via hun luidspreker of hoofdtelefoon te horen.

-

De [Wire](/docs/nl-nl/reference/engine/classes/Wire)  verbindt met de audio-spraakgenerator via zijn [SourceInstance](/docs/nl-nl/reference/engine/classes/Wire#SourceInstance)  eigenschap, en met het fysieke hardware-apparaat via zijn [TargetInstance](/docs/nl-nl/reference/engine/classes/Wire#TargetInstance)  eigenschap. Het fungeert dan als een brug om de audio-stream van de audio-spraakgenerator naar het uitvoerapparaat van de speler te dragen.

![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/TTS2D-Audio-Diagram.png)

Om 2D tekst-naar-spraak audio af te spelen:

1.

In het Explorer  venster, ga naar SoundService  en voeg het volgende toe:

1.

Een AudioTextToSpeech  object om een audio-spraakgenerator te creëren.

2.

Een AudioDeviceOutput  object om een luidspreker te creëren die door de ervaring heen speelt.

3.

Een Wire  object om de stream van de audio-spraakgenerator naar de luidspreker te verbinden.

2.

In het Properties  venster van het AudioTextToSpeech  object:

1.

Stel Text  in op alles wat je wilt dat de stem zegt. Er is een limiet van 300 tekens per verzoek.

2.

Stel VoiceId  in op het nummer van de kunstmatige stem die je wilt gebruiken. Voor een volledige lijst van beschikbare stemmen, zie de [lijst van kunstmatige stemmen](#lijst-van-kunstmatige-stemmen) .

3.

Stel Volume  in op de eenheid van amplitude die je wilt gebruiken om je audio af te spelen.

3.

In het Properties  venster van het Wire  object:

1.

Stel SourceInstance  in op de AudioTextToSpeech  om aan te geven dat je de audio binnen deze specifieke audio-spraakgenerator wilt afspelen.

2.

Stel TargetInstance  in op de AudioDeviceOutput  om aan te geven dat je de audio van deze specifieke luidspreker wilt afspelen.

Van hieruit kun je je TTS-audio activeren met scripts. Voor codevoorbeeldreferenties voor TTS-audio, inclusief hoe je contextbewuste TTS configureert die zich aanpast aan de speler, de staat van hun omgeving of gameplay-status, zie de [Voeg tekst-naar-spraak toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-text-to-speech)  tutorial.

#### [Het creëren van tekst-naar-spraak-assets](#het-creëren-van-tekst-naar-spraak-assets)[](#het-creëren-van-tekst-naar-spraak-assets)

In sommige gevallen wil je misschien dezelfde spraak meerdere keren hergebruiken. In plaats van de API elke keer aan te roepen, kun je een tekst-naar-spraak audio-assets genereren om in je spel te gebruiken met [AssetService:CreateAssetAsync()](/docs/nl-nl/reference/engine/classes/AssetService#CreateAssetAsync) .

#### [Lijst van kunstmatige stemmen](#lijst-van-kunstmatige-stemmen)[](#lijst-van-kunstmatige-stemmen)

| VoiceID | | Stem Beschrijving | | Audio Voorbeeld |
| --- | --- |
| 1 | | Britse man | |  |
| 2 | | Britse vrouw | |  |
| 3 | | Verenigde Staten man #1 | |  |
| 4 | | Verenigde Staten vrouw #1 | |  |
| 5 | | Verenigde Staten man #2 | |  |
| 6 | | Verenigde Staten vrouw #2 | |  |
| 7 | | Australische man | |  |
| 8 | | Australische vrouw | |  |
| 9 | | Retro stem #1 | |  |
| 10 | | Retro stem #2 | |  |
| 11 | | Verteller stem | |  |
| 101 | | Spaanse man | |  |
| 102 | | Spaanse vrouw | |  |
| 201 | | Duitse man | |  |
| 202 | | Duitse vrouw | |  |
| 301 | | Italiaanse man | |  |
| 302 | | Italiaanse vrouw | |  |
| 401 | | Franse man | |  |
| 402 | | Franse vrouw | |  |
| 501 | | Chinees (Mandarijn) man | |  |
| 502 | | Chinees (Mandarijn) vrouw | |  |
| 601 | | Hindi man | |  |
| 602 | | Hindi vrouw | |  |
| 701 | | Japanse man | |  |
| 702 | | Japanse vrouw | |  |
| 801 | | Arabische man | |  |
| 802 | | Arabische vrouw | |  |
| 901 | | Koreaanse man | |  |
| 902 | | Koreaanse vrouw | |  |
| 1001 | | Portugese man | |  |
| 1002 | | Portugese vrouw | |  |

#### [Ondersteunde talen](#ondersteunde-talen)[](#ondersteunde-talen)

Standaard vertaalt Roblox automatisch tekstinvoer naar de taal van de speler en leidt de vertaalde tekst naar de juiste stem-ID. Leer meer over hoe dit werkt in [AudioTextToSpeech.AutoLocalize](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#AutoLocalize) .

### [Spraak-naar-tekst](#spraak-naar-tekst)[](#spraak-naar-tekst)

Alle audio voor [AudioSpeechToText](/docs/nl-nl/reference/engine/classes/AudioSpeechToText)  objecten moet voldoen aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) .

Spraak-naar-tekst  (STT ) is een vorm van technologie die automatisch tekststrings genereert uit spraakgeluiden. Dit type audio vereist drie audio-objecten:

-

Een tekstgenerator om audio te laden en om te zetten in tekst.

-

Een fysiek hardware-apparaat zoals een microfoon om de audio-invoer vast te leggen.

-

Een draad om de audio-stream van het invoerapparaat naar de tekstgenerator te dragen.

Al deze audio-objecten werken samen om STT-tekst te genereren als reactie op acties van de speler. Bijvoorbeeld, als de speler een headset draagt terwijl hij speelt met hun laptop:

-

De [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  legt de spraak van de speler vast, zoals gesproken in hun microfoon en als een audio-stream.

-

Een [Wire](/docs/nl-nl/reference/engine/classes/Wire)  draagt de audio-stream van de [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  naar de [AudioSpeechToText](/docs/nl-nl/reference/engine/classes/AudioSpeechToText) .

-

De [AudioSpeechToText](/docs/nl-nl/reference/engine/classes/AudioSpeechToText)  zet de spraak van de speler om in tekst.

-

De ervaring leest deze tekst en voert een actie uit, zoals het weergeven van de gesproken tekst op het scherm of het openen van een deur op commando van de speler.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/STT-Audio-Diagram.png)

Om spraak-naar-tekst in je ervaring te implementeren:

1.

Schakel het gebruik van de nieuwste API voor spraak in.

1.

In het Explorer  venster, selecteer de VoiceChatService .

2.

In het Properties  venster, stel UseAudioApi  in op Enabled .

2.

In het Explorer  venster, ga naar SoundService  en voeg het volgende toe:

1.

Een AudioDeviceInput  om spraak vast te leggen.

2.

Een AudioSpeechToText  om de spraak om te zetten in tekst.

3.

Een Wire  om de stream van het audio-apparaatinvoer naar de STT-instantie te dragen.

3.

In het Properties  venster van het AudioSpeechToText  object, stel de Enabled  status in op aan.

4.

In het Properties  venster van het Wire  object:

1.

Stel SourceInstance  in op je nieuwe AudioDeviceInput  om aan te geven dat je wilt dat de draad audio van deze specifieke audio-instantie draagt.

2.

Stel TargetInstance  in op je nieuwe AudioSpeechToText  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio-instantie draagt.

5.

Stel de Player  eigenschap van het audio-apparaatinvoer in op de lokale speler tijdens runtime met audioDeviceInput.Player = game.Players.LocalPlayer . Dit vertelt Roblox van welke gebruiker de microfoon audio moet vastleggen.

Standaard schakelt het inschakelen van de microfoon ook spatiële spraakchat in je ervaring in. Als je wilt dat spelers spraak-naar-tekst gebruiken zonder hun stem naar andere spelers uit te zenden, schakel dan de EnableDefaultVoice  eigenschap onder VoiceChatService  uit.

Na het instellen van STT in je ervaring, kun je het activeren met scripts. Voor codevoorbeeldreferenties, zie de [Voeg spraak-naar-tekst toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/speech-to-text)  tutorial.

#### [Ondersteunde talen](#ondersteunde-talen-1)[](#ondersteunde-talen-1)

Er is geen configuratie vereist om ondersteunde talen in te schakelen. Roblox detecteert automatisch de gesproken taal uit de audio en transcribeert deze.

STT ondersteunt de volgende talen:

-

Arabisch

-

Chinees (Vereenvoudigd)

-

Chinees (Traditioneel)

-

Engels

-

Frans

-

Duits

-

Indonesisch

-

Italiaans

-

Japans

-

Koreaans

-

Pools

-

Portugees

-

Spaans

-

Russisch

-

Turks

-

Thais

-

Vietnamees

#### [Filteren op vergelijkbare woorden](#filteren-op-vergelijkbare-woorden)[](#filteren-op-vergelijkbare-woorden)

Wanneer je STT in je ervaring implementeert, wil je misschien de nauwkeurigheid van de matching verbeteren door te filteren op woorden die vergelijkbaar klinken met de woorden die je daadwerkelijk wilt dat de speler zegt. Om dit te doen, kun je de woorden die door AudioSpeechToText  worden herkend vergelijken met bekende woordenlijsten:

1.

Sanitize en tokenize de Text  output van AudioSpeechToText  om een tabel van kleine letters strings te creëren die kunnen worden geparsed en vergeleken.

1.

Verwijder leestekens.

2.

Zet de hele string om naar kleine letters.

3.

Splits de string op witruimtes om een tabel van woorden te produceren.

2.

Genereer kandidaat-tabellen om je strings voor vergelijking voor te bereiden.

1.

Sanitize en tokenize elke referentiestring.

2.

Sla deze verwerkte woorden op in een aparte tabel.

3.

Vergelijk en match de woorden in beide tabellen om de spraakinputs te herkennen die dicht bij je doelzinnen liggen, zelfs als ze kleine variaties bevatten.

-

Voor eenvoudige controles, controleer of de strings exact hetzelfde zijn.

-

Voor meer flexibele matching kun je aangepaste logica schrijven om vervangingen te accepteren (zoals "kleur" in plaats van "color") of een subset van woorden te matchen en een gelijkenisscore te berekenen.

## [Audio aanpassen](#audio-aanpassen)[](#audio-aanpassen)

Audio-effecten stellen je in staat om audio-streams niet-destructief te wijzigen of te verbeteren voordat ze de oren van een speler bereiken. Je kunt deze effecten toepassen om je audio meeslepender te maken binnen ervaringen, zoals het gebruik van een [AudioEqualizer](/docs/nl-nl/reference/engine/classes/AudioEqualizer)  object om regen gedempt te laten klinken, een [AudioCompressor](/docs/nl-nl/reference/engine/classes/AudioCompressor)  object om het maximale volume van een geluid te regelen, of [AudioReverb](/docs/nl-nl/reference/engine/classes/AudioReverb)  om realistischere geluidsecho's in binnenruimtes toe te voegen.

Voor instructies over hoe je audio-effecten configureert, evenals zij-aan-zij vergelijkingen van voor en na je audio aan te passen, zie [Audio-effecten](/docs/nl-nl/audio/effects) .

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Single.png)  ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Multiple.png)

## [Audio activeren](#audio-activeren)[](#audio-activeren)

Je kunt audio contextueel activeren vanuit een script door [Play()](/docs/nl-nl/reference/engine/classes/AudioPlayer#Play)  aan te roepen op een [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  object dat correct is aangesloten. Bijvoorbeeld, als je een script aan een audio-speler plaatst, kun je de audio-assets activeren via iets als dit:

```

local audio = script.Parent

local something = ...

something.SomeEvent:Connect(function()

    audio:Play()

end)

```

Voor meer complexe codevoorbeelden om audio te activeren, zoals voor gameplay-feedback, UI-interacties en herhalend achtergrondgeluid, zie de [Voeg 2D audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-2D-audio) , [Voeg 3D audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-3D-audio) , en [Voeg tekst-naar-spraak toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-text-to-speech)  tutorials.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
