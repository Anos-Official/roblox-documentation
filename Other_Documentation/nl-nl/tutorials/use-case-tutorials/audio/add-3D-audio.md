<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/audio/add-3D-audio -->

Voeg 3D-audio toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Audio

# Voeg 3D-audio toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

3D-audio  is directioneel geluid dat uit een bepaalde locatie in de 3D-ruimte komt, waarbij het volume toeneemt of afneemt afhankelijk van de afstand en oriëntatie tussen de audio-emitter en de luisteraar. Dit betekent dat terwijl luisteraars of emitters zich door de omgeving bewegen, spelers dat geluid dynamisch vanuit verschillende richtingen en volume-niveaus kunnen horen.

Met het [Gingerbread House - Start](https://www.roblox.com/games/134812596370919/Gingerbread-House-Start)  .rbxl  bestand als startpunt en [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  als referentie, laat deze tutorial je zien hoe je zowel herhalende als eenmalige 3D-audio aan je games toevoegt, inclusief richtlijnen over:

-

Herhalende omgevingsgeluiden die afspelen zodra spelers verbinding maken met de server.

-

Audio activeren om spelers te informeren over belangrijke situationele gebeurtenissen die belangrijk zijn voor hun gameplay.

-

Audio activeren om spelers auditieve feedback te geven wanneer ze interactie hebben met 3D-objecten.

-

Geluidssnippets van personages afspelen die spelers betrekken en begeleiden naar interessante punten binnen hun omgeving.

Als je op enig moment vastloopt in het proces, kun je Gingerbread House - Complete Audio  als referentie gebruiken om je voortgang te vergelijken.

Als je niet-positionele audio aan je game wilt toevoegen, zoals achtergrondmuziek, geluiden van UI-interacties of voice-over dialoog in cutscenes, zie [Voeg 2D-audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-2D-audio) .

## [Audio-objecten](#audio-objecten)[](#audio-objecten)

Om directionele audio te creëren, is het belangrijk om de audio-objecten te begrijpen waarmee je gedurende deze tutorial zult werken. Er zijn zes hoofdtypen audio-objecten voor 3D-audio:

-

Het [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  object laadt en speelt het audio bestand  af.

-

Het [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  object is een virtuele luidspreker  die audio in de 3D-omgeving uitzendt.

-

Het [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  object is een virtuele microfoon  die audio uit de 3D-omgeving opvangt.

-

Het [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object is een fysiek hardware-apparaat  in de echte wereld, zoals een luidspreker of hoofdtelefoon.

-

Het [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object is een fysieke microfoon  in de echte wereld.

-

[Wires](/docs/nl-nl/reference/engine/classes/Wire)  dragen audiostreams van het ene object naar het andere.

Al deze audio-objecten werken samen om geluid uit te zenden, net als hun tegenhangers in de echte wereld. Laten we eens kijken hoe dit in de praktijk werkt met een voorbeeld van een speler die een headset draagt terwijl hij een game speelt met zijn laptop:

-

Het [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  laadt de 1516791621  audio asset ID in de game voor een regentrack.

-

Het [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  zendt een stroom van de regentrack audio uit in de 3D-omgeving.

-

Een [Wire](/docs/nl-nl/reference/engine/classes/Wire)  draagt de stroom van de [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  naar de [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) , zodat de stroom uit de 3D-luidspreker komt.

-

Het kind [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  object van het personage luistert naar dat geluid binnen de 3D-omgeving en geeft het terug aan hun headset.

-

Het [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object draagt het geluid van de [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  naar de fysieke luidspreker van de speler, of in dit geval, hun hoofdtelefoon.

-

Het [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object vangt geluid uit de echte wereld op en geeft het terug in de game voor spraakchat.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Experience-Object-Representations.png) Objectrepresentaties binnen de game

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Realworld-Object-Representations.png) Objectrepresentaties in de echte wereld

De volgende secties gaan dieper in op deze objecten terwijl je leert hoe je zowel herhalende als eenmalige 3D-audio kunt afspelen. Terwijl je deze objecten met de komende technieken bekijkt, kun je nauwkeuriger voorspellen hoe je geluid uit de game naar de speler en vice versa kunt vastleggen en doorgeven.

## [Herhalende audio](#herhalende-audio)[](#herhalende-audio)

Herhalende 3D-audio , of directionele audio die naadloos herhaalt zodra spelers verbinding maken met de server, is een veelgebruikte geluidsontwerptechniek om de sfeer van de 3D-ruimte te verbeteren door deze levendig en dynamisch te laten aanvoelen. Bovendien houdt herhalende 3D-audio je omgevingsgeluidsbronnen consistent, zoals het statische geluid van een televisie of het gebrul van een waterval; als deze geluiden plotseling zouden stoppen, zou de omgeving onrealistisch aanvoelen.

Om dit concept te demonstreren, bekijk hoe de volgende 3D-audio voor twee grote watervallen stopt zodra de niet-herhalende audiotrack is voltooid. Terwijl de watergeluiden aanvankelijk spelers onderdompelen in de buitenomgeving, is de plotselinge auditieve verandering schokkend en onnatuurlijk voor hoe een waterval zich in de echte wereld gedraagt.

Om een naadloze loop te creëren, moet je de eind- en startpunten van je audiotrack precies op elkaar afstemmen, zodat spelers de herhaling niet kunnen detecteren. Dit proces vereist software voor audio-bewerking van derden zoals [Reaper](https://www.reaper.fm/)  of [Audacity](https://www.audacityteam.org/) , zodat je een nuldoorgang kunt vinden en een zorgvuldig getimede snede kunt maken. Voor stap-voor-stap instructies over deze methoden, zie [Perfecte Audio Loops Creëren](https://devforum.roblox.com/t/creating-perfect-audio-loops/2849057) .

Evenzo gebruikt het voorbeeld deze techniek voor de stromende chocolade waterval en past het volume aan op basis van de afstand van de speler tot de audio-emitter. Wanneer de speler minder dan 20 studs weg is, zendt de emitter het geluid op vol volume uit. Terwijl de speler verder weg beweegt, neemt het geluid van het klotsen af in volume elke 20 studs van de audio-emitter. Dit emuleert geluid in de echte wereld dat afneemt in volume naarmate je verder van de bron verwijderd bent.

Om de herhalende 3D-audio in het voorbeeld [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

Schakel een standaard luisteraar in die aan je spelerspersonage is gekoppeld.

1.

In het Explorer  venster, selecteer de SoundService .

2.

In het Properties  venster, stel DefaultListenerLocation  in op Character . Wanneer je de game uitvoert, maakt de engine automatisch:

-

Een [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  aan onder elk [Humanoid.RootPart](/docs/nl-nl/reference/engine/classes/Humanoid#RootPart)  van de speler, zodat je geluiden kunt horen verschuiven in je echte luidsprekers volgens de positie en schaal van geluidsbronnen binnen de game.

-

Een [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  onder SoundService .

2.

In het Explorer  venster, navigeer naar Workspace  ⟩ WaterfallAudioObject , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron voor de waterval te creëren.

2.

Voeg een AudioEmitter  object toe om een positionele stroom van WaterfallAudioObject  uit te zenden.

3.

Voeg een Wire  object toe om de stroom van de audio speler naar de audio emitter te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Looping-DataModel.png)

3.

Selecteer de AudioPlayer , en stel in het Properties  venster,

1.

AssetID  in op rbxassetid://1516791621  om een regenachtige audiotrack af te spelen.

2.

Schakel Looping  in zodat de audio naadloos herhaalt.

4.

Selecteer de AudioEmitter , en stel in het Properties  venster DistanceAttenuation  in op {0: 1}, {20: 0.8}, {40: 0.4}, {80: 0}  zodat het geluid geleidelijk in volume afneemt elke 20 studs van de audio-emitter.

5.

Selecteer de Wire , en stel in het Properties  venster,

1.

SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

TargetInstance  in op je nieuwe AudioEmitter  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio emitter binnen de waterval draagt.

6.

Terug in het Explorer  venster, voeg een Script  toe aan WaterfallAudioObject , hernoem het naar LoopWaterfallMusic , stel de RunContext  eigenschap in op Client , en plak de volgende code in het script:

```

local audioPlayer = script.Parent

audioPlayer:Play()

```

Code uitleg

Het script begint met het declareren van een variabele om de ouder van het script [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  weer te geven. Het script stelt vervolgens de audio bron in om af te spelen vanaf het moment dat de speler de game binnenkomt tot het moment dat ze de game verlaten.

7.

Speel de game om het herhalende chocolade regen geluid te horen wanneer je avatar zich dicht bij de waterval bevindt. Wanneer je het hoofd van je personage draait om in een andere richting te kijken, verschuift het geluid dynamisch in je echte luidsprekers volgens de positie van de emitter in de 3D-ruimte.

## [Eenmalige audio](#eenmalige-audio)[](#eenmalige-audio)

Eenmalige 3D-audio , of directionele audio die eenmaal op een specifieke tijd en positie afspeelt, tenzij een speler het opnieuw activeert, biedt spelers context over hun acties, de omgeving en eventuele personages om hen heen. Het gebruik van dit type auditieve feedback in je games is essentieel omdat het spelers in staat stelt strategische beslissingen te nemen, zoals het vermijden van binnenkomende vijanden of het oppakken van nuttige items.

De volgende secties bieden implementatiedetails voor veelvoorkomende gameplay-scenario's waarin spelers tijdige, directionele feedback nodig hebben, inclusief situationele gameplay-evenementen, objectinteractie en dialoog van niet-speelbare personages.

### [Evenementfeedback](#evenementfeedback)[](#evenementfeedback)

Wanneer spelers belangrijke situationele evenementen binnen hun omgeving activeren, zoals het ontgrendelen van nieuwe gameplay-gebieden of het uitlokken van vijandelijk vuur, is het essentieel dat ze begrijpen waar in de 3D-ruimte ze hun focus en aandacht moeten richten. Als ze geen onmiddellijke auditieve feedback ontvangen, kunnen ze informatie missen die belangrijk is voor hun gameplay, wat leidt tot frustratie omdat ze niet weten waar ze heen moeten of wat ze vervolgens moeten doen.

Om te demonstreren waarom dit belangrijk is, laten we de eenmalige 3D-audio van de [Laser Tag](/docs/nl-nl/resources/templates#laser-tag)  template bekijken die vanuit elke speler zijn blaster afspeelt:

-

Een diepe popgeluid speelt voor elke schot die de speler vanuit zijn blaster afvuurt.

-

Een klik- en robotachtige piepgeluid speelt elke keer wanneer de speler zijn blaster herlaadt met een nieuw rondje.

Beide geluiden bieden situationele bewustwording door alle nabijgelegen spelers te waarschuwen over de richting waaruit de schoten komen, zodat ze geïnformeerde beslissingen kunnen nemen om ofwel mee te doen aan het plezier of potentiële gevaren te vermijden.

Het voorbeeld gebruikt dezezelfde techniek om spelers situationele bewustwording te bieden over hun beloning voor het voltooien van het hoofdobjectief binnen de game. Nadat ze alle drie de gumdrops hebben verzameld, opent de deur naar het peperkoekenhuis om spelers toegang te geven tot het cadeau binnenin.

Omdat er geen specifieke volgorde is waarin spelers de gumdrops moeten verzamelen, is het belangrijk dat spelers zich bewust zijn van de opening van de deur, ongeacht welke gumdrop ze als laatste verzamelen. Positioneel geluid maakt dit mogelijk, zodat spelers zich bewust zijn van hun succes en waar ze vervolgens heen moeten, ongeacht hun relatieve afstand en richting van de deur.

Om de eenmalige evenementfeedback 3D-audio in het voorbeeld [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

In het Explorer  venster, navigeer naar Workspace  ⟩ Door , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron voor de volumeklep te creëren.

2.

Voeg een AudioEmitter  object toe om een positionele stroom van Door  uit te zenden.

3.

Voeg een Wire  object toe om de stroom van de audio speler naar de audio emitter te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Feedback-DataModel.jpg)

2.

Selecteer de AudioPlayer , en stel in het Properties  venster AssetID  in op rbxassetid://5930776613  om een geluidstrack van een schuivende metalen poort af te spelen.

3.

Selecteer de Wire , en stel in het Properties  venster,

1.

SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

TargetInstance  in op je nieuwe AudioEmitter  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio emitter binnen het volume draagt.

4.

Terug in het Explorer  venster, navigeer naar ServerScriptService , voeg een Script  toe, hernoem het naar GumdropService , stel de RunContext  eigenschap in op Server , en plak de volgende code in het script:

```

-- Initialiseren van variabelen

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local ServerStorage = game:GetService("ServerStorage")

local TweenService = game:GetService("TweenService")

-- Modules

local Leaderboard = require(ServerStorage.Leaderboard)

local PlayerData = require(ServerStorage.PlayerData)

-- Variabelen

local gumdropsFolder = Workspace.Gumdrops

local gumdrops = gumdropsFolder:GetChildren()

local GUMDROP_KEY_NAME = PlayerData.GUMDROP_KEY_NAME

local GUMDROP_AMOUNT_TO_ADD = 1

local function updatePlayerGumdrops(player, updateFunction)

   -- Update de gumdrop tabel

   local newGumdropAmount = PlayerData.updateValue(player, GUMDROP_KEY_NAME, updateFunction)

   -- Update de gumdrop leaderboard

   Leaderboard.setStat(player, GUMDROP_KEY_NAME, newGumdropAmount)

   -- Controleer of de speler drie gumdrops heeft verzameld

   if newGumdropAmount >= 3 then

      -- Speel de deur evenement audio af wanneer de speler drie gumdrops verzamelt

      local audioPlayer = Workspace.Door.AudioPlayer

      audioPlayer:Play()

      -- Animeer de deur om naar beneden te bewegen

      local doorPart = Workspace.Door

      local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Linear)

      local tween = TweenService:Create(doorPart, tweenInfo, {Position = doorPart.Position + Vector3.new(0, -15, 0)})

      tween:Play()

   end

end

-- Definiëren van de gebeurtenis handler

local function onGumdropTouched(otherPart, gumdrop)

   if gumdrop:GetAttribute("Enabled") then

      local character = otherPart.Parent

      local player = Players:GetPlayerFromCharacter(character)

      if player then

         -- Speler heeft een gumdrop aangeraakt

         local audioPlayer = gumdrop.AudioPlayer

         audioPlayer:Play()

         gumdrop.Transparency = 1

         gumdrop:SetAttribute("Enabled", false)

         updatePlayerGumdrops(player, function(oldGumdropAmount)

            oldGumdropAmount = oldGumdropAmount or 0

            return oldGumdropAmount + GUMDROP_AMOUNT_TO_ADD

         end)

         print("Speler heeft gumdrop verzameld")

      end

   end

end

-- Instellen van gebeurtenisluisteraars

for _, gumdrop in gumdrops do

   gumdrop:SetAttribute("Enabled", true)

   gumdrop.Touched:Connect(function(otherPart)

      onGumdropTouched(otherPart, gumdrop)

   end)

end

```

Code uitleg

Dit script behandelt aanvullende functionaliteit buiten het activeren van de positionele audio, zoals het bijwerken van de leaderboard en het activeren van een niet-positioneel geluid elke keer dat een speler een gumdrop verzamelt. Dit is belangrijk voor de gameplay van het voorbeeld, maar het is niet belangrijk voor het begrijpen van hoe je 2D-audio implementeert, dus deze uitleg zal die secties op een hoog niveau houden.

Dit script begint met het initialiseren van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , [Players](/docs/nl-nl/reference/engine/classes/Players) , [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) , en [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  services, zodat het hun kinderen en functionaliteit kan refereren. Vervolgens vereist het de Leaderboard  en PlayerData  modules in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) ; deze modules zijn verantwoordelijk voor het creëren en bijwerken van een leaderboard in de rechterbovenhoek van het scherm dat het aantal gumballs bijhoudt dat een speler in de omgeving verzamelt.

De updatePlayerGumdrops  functie van het script is waar het grootste deel van het werk plaatsvindt voor het activeren van 3D-audio voor evenementfeedback, en het neemt twee argumenten:

-

player  - Een speler die een gumdrop verzamelt.

-

updateFunction  - Een callbackfunctie die het verzamelde gumdrop aantal van de speler bijwerkt.

Wanneer een speler met een gumdrop botst, doet het script het volgende:

-

Krijgt de nieuwe gumdrop verzameling hoeveelheid waarde van de speler door de PlayerData.updateValue  functie aan te roepen.

-

Update de leaderboard met dit nieuwe bedrag door de Leaderboard.setStat  functie aan te roepen.

-

Controleert of de hoeveelheid groter is dan of gelijk aan 3 .

Wanneer deze waarde groter is dan of gelijk aan 3 , doet het script het volgende:

-

Speelt de 3D-audio track van de audio speler naar de audio emitter af.

-

Beweegt de deur lineair 15  studs onder zijn huidige positie.

De rest van het script is grotendeels verantwoordelijk voor het detecteren dat alles wat met de gumdrop botst een speler is, zodat het een niet-positioneel geluid voor verzamelfeedback kan activeren. Voor meer informatie over dit deel van het script, zie [Voeg 2D-audio toe - Gameplay feedback](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-2D-audio) .

5.

Speel de game om het geluid van de schuifpoort te horen nadat je alle drie de gumdrops in de omgeving hebt verzameld. Wanneer je de camera draait, verschuift het geluid dynamisch in je echte luidsprekers, zodat je het hoort volgens de positie van de emitter in de 3D-ruimte.

### [Objectinteractie](#objectinteractie)[](#objectinteractie)

Wanneer spelers interactie hebben met 3D-objecten binnen hun omgeving, zoals het aanzetten van een lichtschakelaar of het oppakken van een wapen, is het belangrijk om onmiddellijke feedback te geven, zodat ze intuïtief begrijpen hoe  ze met het object interageren. De combinatie van zowel visuele als auditieve feedback versterkt de oorzaak-en-gevolgrelatie tussen de acties van de speler en de reactie van de omgeving.

Om dit concept verder uit te breiden, laten we de volgende eenmalige 3D-audio van het [Plant](https://www.roblox.com/games/18221564209/Plant-Complete-Audio)  voorbeeld bekijken voor de gebruikersstroom van het tuinieren van een kool:

-

Een zachte klikgeluid speelt wanneer de speler een zaadje plant.

-

Een nat, spetterend geluid speelt wanneer de speler hun groeiende plant water geeft.

-

Een knipgeluid speelt wanneer de speler de volgroeide plant verzamelt.

-

Een zachte thud-geluid speelt wanneer de speler de kool in de wagen plaatst.

Al deze geluiden versterken de [proximity prompt](/docs/nl-nl/ui/proximity-prompts)  belangrijke interacties van de speler met het object dat van vorm verandert in de 3D-ruimte. Voor spelers met visuele beperkingen waarbij kleurveranderingen of animaties moeilijker te onderscheiden zijn, helpen deze meerdere vormen van sensorische feedback om je 3D-objectinteracties toegankelijk en intuïtief te houden voor zoveel mogelijk spelers.

Om een ander voorbeeld te geven van hoe je objectinteractie kunt configureren met meerdere vormen van sensorische feedback, biedt het voorbeeld zowel visuele als auditieve feedback telkens wanneer spelers op de 3D-pepermuntknop binnen het peperkoekenhuis stappen. Wanneer spelers niet met de knop interageren, lijkt het op een typische pepermunt, maar wanneer ze op de knop stappen, doet het voorbeeld het volgende:

-

Speelt een feestelijke jingle audio track af.

-

Tint de zijkanten van de knop met een groene tint.

-

Beweegt de knop in de grond.

Van hieruit kun je deze interactie verbinden met allerlei unieke gameplay-acties, zoals het ontgrendelen van een item of het activeren van een speciale vaardigheid.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Button-Default.jpg) Standaardweergave

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Button-Pressed.jpg) Ingedrukte staat

Om de eenmalige objectinteractie 3D-audio in het voorbeeld [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

In het Explorer  venster, navigeer naar Workspace  ⟩ 3DAudioButton , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron voor de knop te creëren.

2.

Voeg een AudioEmitter  object toe om een positionele stroom van 3DAudioButton  uit te zenden.

3.

Voeg een Wire  object toe om de stroom van de audio speler naar de audio emitter te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Looping-DataModel.png)

2.

Selecteer de AudioPlayer , en stel in het Properties  venster AssetID  in op rbxassetid://1846248593  om een vrolijke, feestelijke audio track af te spelen.

3.

Selecteer de Wire , en stel in het Properties  venster,

1.

SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

TargetInstance  in op je nieuwe AudioEmitter  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio emitter binnen de knop draagt.

4.

Terug in het Explorer  venster, voeg een Script  toe aan 3DAudioButton , hernoem het naar PlayAudioWhenPressed , en plak de volgende code in het script:

```

local TweenService = game:GetService("TweenService")

local buttonModel = script.Parent.Parent

local buttonPart = buttonModel.ButtonPart

local buttonPressedAudioPlayer = buttonModel.ButtonPressedAudioPlayer

local tweenInfo = TweenInfo.new(.2, Enum.EasingStyle.Exponential)

local buttonTweenByIsPressed = {

   -- Ingedrukt

   [true] = TweenService:Create(buttonPart, tweenInfo, {

      Size = buttonPart.Size / Vector3.new(2, 1, 1),

      Color = Color3.fromRGB(75, 151, 75),

   }),

   -- Standaard

   [false] = TweenService:Create(buttonPart, tweenInfo, {

      Size = buttonPart.Size,

      Color = Color3.fromRGB(196, 40, 28),

   }),

}

local function onIsPlayingChanged()

   local isPlaying = buttonPressedAudioPlayer.IsPlaying

   local tween = buttonTweenByIsPressed[isPlaying]

   tween:Play()

   end

onIsPlayingChanged()

buttonPressedAudioPlayer:GetPropertyChangedSignal("IsPlaying"):Connect(onIsPlayingChanged)

buttonPressedAudioPlayer.Ended:Connect(onIsPlayingChanged)

buttonPart.Touched:Connect(function(_hit)

buttonPressedAudioPlayer:Play()

end)

```

Code uitleg

Dit script behandelt aanvullende functionaliteit buiten alleen het afspelen van 3D-audio voor objectinteracties, zoals het tweenen van de kleur en positie van de knop. Dit is belangrijk voor het bieden van meerdere bronnen van sensorische feedback, maar de ontwerpeisen voor jouw gebruiksgeval vereisen mogelijk alleen auditieve feedback. Als je alleen audio wilt afspelen wanneer spelers het model aanraken, kun je de tween-functionaliteit verwijderen.

Het script begint met het verkrijgen van:

-

De [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  zodat het de knop kan animeren die uit de grond steekt.

-

Het ouder 3DAudioButton  model van het script.

-

Het deel van de knop dat uit de grond steekt.

-

De relevante audio speler met je feestgeluid audio track.

Het script definieert vervolgens:

-

Een TweenInfo  object dat specificeert dat de animatie van de knop met een exponentiële animatiestijl zal afspelen.

-

Twee tweens die de ingedrukte of niet-ingedrukte staat van de knop vertegenwoordigen.

-

De true  ingedrukte staat beweegt de knop iets naar beneden in de grond en tint de zijkanten van het deel met een groene tint.

-

De false  niet-ingedrukte staat beweegt de knop terug naar zijn oorspronkelijke positie en verwijdert de vorige tint.

De rest van het script is waar het grootste deel van het werk plaatsvindt voor objectinteractie feedback, dus laten we bekijken hoe de onIsPlayingChanged  functie en gebeurtenisluisteraars samenwerken:

1.

buttonPart.Touched  luistert naar een speler die de knop aanraakt, en roept vervolgens de Play()  functie aan om de bijbehorende audio van de audio speler te starten. Dit proces schakelt de [AudioPlayer.IsPlaying](/docs/nl-nl/reference/engine/classes/AudioPlayer#IsPlaying)  eigenschap van false  naar true .

2.

buttonPressedAudioPlayer:GetPropertyChangedSignal("IsPlaying")  luistert naar de IsPlaying  eigenschap van de audio speler om te veranderen, en roept vervolgens de onIsPlayingChanged  functie aan.

3.

De onIsPlayingChanged  functie gebruikt deze informatie om de tween te activeren die de visuele verschijning in de 3D-ruimte verandert.

4.

Om te voorkomen dat de speler per ongeluk de audio opnieuw start als ze snel op de knop springen, luistert buttonPressedAudioPlayer.Ended  naar de audio speler om te eindigen met afspelen voordat de onIsPlayingChanged  functie opnieuw wordt aangeroepen.

Het is belangrijk op te merken dat de onIsPlayingChanged  gebeurtenis alleen wordt geactiveerd wanneer deze verandert van false  naar true , wat betekent dat deze niet wordt geactiveerd wanneer deze verandert van true  naar false . Dit is de bedoelde werking vanwege complicaties met de timing van het repliceren van eigenschappen van server naar client. Daarom wordt de Ended  gebeurtenis in dit voorbeeld geboden en beluisterd om beide gevallen te dekken.

5.

Speel de game om het feestgeluid te horen wanneer je spelerspersonage de 3D-knop in het peperkoekenhuis aanraakt. Wanneer je wegloopt van de knop, neemt het volume van het geluid af.

### [Dialoog van personages](#dialoog-van-personages)[](#dialoog-van-personages)

Het bieden van directionele audio van je niet-speelbare personages (NPC) is nuttig om spelers te begeleiden naar interessante punten binnen hun omgeving en voegt diepte toe aan hun interacties met andere personages. In feite gebruiken veel ontwerpers in narratief gedreven games strategisch personagedialoog om spelers indirect te leren over hun personage, bondgenoten en vijandige personages, of de wereld zelf.

Veelvoorkomende voorbeelden van deze techniek zijn onder andere:

-

Dialoogstijl  om de toon van je game te zetten.

-

Banter  om spelers te leren over de relaties tussen personages.

-

Vijandige gesprekken  om motivaties of hun positie ten opzichte van de speler te onthullen.

-

Spelerpersonages die hun gedachten hardop uitspreken  om de speler zachtjes te begeleiden naar wat ze vervolgens moeten doen, zoals zichzelf genezen, naar een andere locatie verplaatsen of een item vinden.

-

Bondgenoten die met het spelerspersonage praten  om details over de in-game wereld zoals geschiedenis, cultuur en sociale kwesties te onthullen.

Om te demonstreren hoe dit eruit kan zien in de praktijk, laten we de volgende eenmalige 3D-audio van [Beyond the Dark](https://www.roblox.com/games/7208091524/Beyond-the-Dark-Vistech-Showcase)  showcase bekijken die periodiek afspeelt wanneer spelers zich in het hoofd lobbygebied van het ruimtestation bevinden.

Met het ruimtestation als personage biedt deze dialoogclip spelers belangrijke context en lore over de algehele setting. Bijvoorbeeld, uit deze enkele zin leren spelers:

-

Ze zijn in de ruimte, specifiek op een ruimtestation genaamd Kerr-Newman Deep Space Relay 14.

-

Hun omgeving is futuristisch en gastvrij.

-

Ze zijn een bezoeker en zullen waarschijnlijk snel vertrekken.

Deze details samen onderdompelen spelers in hun omgeving en voegen een gevoel van urgentie toe aan hun missie. Als spelers echter niet weten wat hun belangrijkste missie is, kun je ook personagedialoog gebruiken om spelers te informeren over wat je wilt dat ze doen binnen je game.

Om dit te illustreren, gebruikt het voorbeeld een volume , of onzichtbaar gebied binnen de 3D-ruimte, om personagedialoog van de sneeuwman te activeren om spelers te begeleiden om drie gumdrops te verzamelen om de deur naar zijn huis te openen. Aangezien dit een van de eerste dingen is die spelers zien wanneer ze de game binnenkomen, is de kans groter dat spelers de dialoog activeren en weten wat ze moeten doen om succesvol te zijn.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Volume-Example.jpg) Het volume rond de sneeuwman gebruikt botsingfeedback om audio af te spelen wanneer spelers het 3D-gebied binnenkomen.

Om de eenmalige personagedialoog 3D-audio in het voorbeeld [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

In het Explorer  venster, navigeer naar Workspace  ⟩ DialogueVolume , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron voor het volume te creëren.

2.

Voeg een AudioEmitter  object toe om een positionele stroom van DialogueVolume  uit te zenden.

3.

Voeg een Wire  object toe om de stroom van de audio speler naar de audio emitter te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-3D-audio/Looping-DataModel.png)

2.

Selecteer de AudioPlayer , en stel in het Properties  venster AssetID  in op rbxassetid://92917410841704  om een instructieve audio track voor het doel van de game af te spelen.

3.

Selecteer de Wire , en stel in het Properties  venster,

1.

SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

TargetInstance  in op je nieuwe AudioEmitter  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio emitter binnen het volume draagt.

4.

Terug in het Explorer  venster, navigeer naar StarterPlayer  ⟩ StarterCharacterScripts , voeg een LocalScript  toe, hernoem het naar PlayAudioWhenInVolume , en plak de volgende code in het lokale script:

```

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local humanoid = script.Parent:WaitForChild("Humanoid")

local volumeDetector = Workspace.DialogueVolume

local trigger = humanoid:WaitForChild("Animator")

local debounce = false

local localPlayer = Players.LocalPlayer

volumeDetector.Touched:Connect(function(hit)

   if debounce then

      return

   end

   local hitCharacter = hit:FindFirstAncestorWhichIsA("Model")

   local hitPlayer = Players:GetPlayerFromCharacter(hitCharacter)

   if hitPlayer ~= localPlayer then

      return

   end

   debounce = true

   local audioPlayer = Workspace.DialogueVolume.AudioPlayer

   audioPlayer:Play()

   audioPlayer.Ended:Wait()

   debounce = false

end)

```

Code uitleg

Dit script begint met het verkrijgen van de Workspace en Players services, zodat het hun kinderen en functionaliteit kan refereren. Voor elk spelerspersonage dat in de game laadt of opnieuw spawnt, wacht het script op:

-

De [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en [Animator](/docs/nl-nl/reference/engine/classes/Animator)  objecten van het personage.

-

Het volume-object in de workspace genaamd DialogueVolume .

Wanneer iets met het volume botst, krijgt de Touched  gebeurtenis handler functie de eerste voorouder die een [Model](/docs/nl-nl/reference/engine/classes/Model)  is, wat het personage zou moeten zijn als de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die met het volume botste een afgeleide is van een personagemodel. Als dat zo is, doet de functie het volgende:

-

Stelt debounce in op true .

-

Speelt de audio af en wacht tot deze eindigt.

-

Stelt debounce weer in op false .

Het instellen van debounce van false  naar true  naar false  weer na het afspelen van de audio is een debounce-patroon dat voorkomt dat de audio herhaaldelijk wordt geactiveerd terwijl spelers continu met het volume botsen. Voor meer informatie over dit debounce-patroon, zie [Debounce - Detecteer botsingen](/docs/nl-nl/scripting/debounce#detecteer-botsingen) .

5.

Speel de game om de instructieve personagedialoog te horen wanneer je spelerspersonage het volume rond de sneeuwman aanraakt.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
