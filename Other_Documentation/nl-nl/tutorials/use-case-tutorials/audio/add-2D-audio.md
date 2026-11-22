<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/audio/add-2D-audio -->

Voeg 2D-audio toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Audio

# Voeg 2D-audio toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

2D-audio  is niet-directioneel geluid dat niet uit een specifieke locatie komt en hetzelfde blijft, ongeacht de positie of oriëntatie van de luisteraar in de 3D-ruimte. Dit betekent dat terwijl spelers hun luisteraars door de omgeving bewegen, ze 2D-audio consistent kunnen horen vanuit elke richting waarin ze zich omdraaien.

Met het [Gingerbread House - Start](https://www.roblox.com/games/134812596370919/Gingerbread-House-Start)  .rbxl  bestand als startpunt en [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  als referentie, laat deze tutorial je zien hoe je zowel herhalende als eenmalige 2D-audio aan je games toevoegt, inclusief richtlijnen over:

-

Herhalende achtergrondmuziek die afspeelt zodra spelers verbinding maken met de server.

-

Audio activeren om spelers onmiddellijke feedback te geven volgens hun gameplay-doelen.

-

Verschillende geluiden activeren om verschillende interacties met de gebruikersinterface aan te geven.

Als je op enig moment vastloopt in het proces, kun je Gingerbread House - Complete Audio  als referentie gebruiken om je voortgang te vergelijken.

Als je positionele audio aan je game wilt toevoegen, zoals omgevingsgeluiden binnen de omgeving, geluiden van objectinteracties of dialogen van niet-speelbare personages, zie [Voeg 3D-audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-3D-audio) .

## [2D-audio-objecten](#2d-audio-objecten)[](#2d-audio-objecten)

Om niet-directionele audio te creëren, is het belangrijk om de audio-objecten te begrijpen waarmee je gedurende deze tutorial zult werken. Er zijn drie hoofdtypen audio-objecten voor 2D-audio:

-

Het [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  object laadt en speelt het audio bestand  af.

-

Het [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object is een fysiek hardware-apparaat  in de echte wereld, zoals een luidspreker of hoofdtelefoon.

-

[Wires](/docs/nl-nl/reference/engine/classes/Wire)  dragen audiostreams van het ene object naar het andere.

Al deze audio-objecten werken samen om geluid van bestandafspelen naar de hardware van elke speler te dragen. Laten we eens kijken hoe dit in de praktijk werkt met een voorbeeld van een speler die een headset draagt terwijl hij een game speelt met zijn laptop:

-

De [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  laadt de 127645268874265  audio asset ID in de game voor een geluid bij de aankoop van valuta.

-

Een [Wire](/docs/nl-nl/reference/engine/classes/Wire)  draagt de stream van de [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  naar de [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput) , zodat de stream uit de headset van de speler komt.

-

Het [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object draagt het geluid naar de fysieke luidspreker van de speler, of in dit geval, hun hoofdtelefoon.

De volgende secties gaan dieper in op deze objecten terwijl je leert hoe je zowel herhalende als eenmalige 2D-audio kunt afspelen. Terwijl je deze objecten met de komende technieken bekijkt, kun je nauwkeuriger voorspellen hoe je geluid van de game naar de speler kunt vastleggen en doorgeven.

## [Herhalende audio](#herhalende-audio)[](#herhalende-audio)

Herhalende 2D-audio , of niet-directionele audio die naadloos herhaalt zodra spelers verbinding maken met de server, is een veelgebruikte geluidsontwerpmethode om een samenhangende auditieve achtergrond te bieden, ongeacht wat spelers doen of waar ze zich bevinden binnen de 3D-ruimte. Bovendien zorgt herhalende 2D-audio ervoor dat je game nooit volledig stil is, wat spelers kan desoriënteren en afleiden van hun doelen.

Om dit concept te demonstreren, bekijk hoe de volgende 2D-audio de kwaliteit van de [Hazardous Space Station](https://www.roblox.com/games/99416825187098/Hazardous-Space-Station)  sample aanzienlijk verbetert. Zonder achtergrondmuziek voelt het ruimtevaartuig hol en levenloos aan. Echter, wanneer het ruimtevaartuig achtergrondmuziek bevat, voelt het zowel onheilspellend als gevaarlijk aan, wat bijdraagt aan de algehele griezelige sfeer.

Zonder herhalende 2D-audio

Met herhalende 2D-audio

Om een naadloze loop te creëren, moet je de eind- en startpunten van je audiotrack precies op elkaar afstemmen, zodat spelers de herhaling niet kunnen detecteren. Dit proces vereist software voor audio-bewerking van derden zoals [Reaper](https://www.reaper.fm/)  of [Audacity](https://www.audacityteam.org/) , zodat je een nuldoorgang kunt vinden en een zorgvuldig getimede snede kunt maken. Voor stap-voor-stap instructies over deze methoden, zie [Perfecte Audio Loops Creëren](https://devforum.roblox.com/t/creating-perfect-audio-loops/2849057) .

Herhalende audio is bijzonder nuttig om vast te stellen hoe je wilt dat spelers zich voelen zodra ze je game betreden. Bijvoorbeeld, de sample is bedoeld om spelers een vrolijk avontuur in een winterwonderland te bieden, dus het gebruikt een opgewekt audiotrack om hun humeur positief te beïnvloeden op het moment dat ze de omgeving binnenkomen. Om te zien hoe invloedrijk deze techniek kan zijn, overweeg hoe de ervaring van de speler zou veranderen als je de herhalende audio zou vervangen door een metaltrack.

Om de herhalende 2D-audio in de sample [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

Schakel een standaard luisteraar in die aan je speler karakter is gekoppeld.

1.

In het Explorer  venster, selecteer de SoundService .

2.

In het Properties  venster, stel DefaultListenerLocation  in op Character . Wanneer je de game uitvoert, maakt de engine automatisch een [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  aan onder SoundService .

2.

In het Explorer  venster, navigeer naar SoundService , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron te creëren.

2.

Voeg een AudioDeviceOutput  object toe om een luidspreker te creëren die door de game heen speelt.

3.

Voeg een Wire  object toe om de stream van de audio speler naar de luidspreker te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/Looping-DataModel.png)

3.

Selecteer de AudioPlayer , dan in het Properties  venster,

1.

Stel AssetID  in op rbxassetid://1841461968  om een opgewekt audiotrack af te spelen.

2.

Schakel Looping  in zodat de audio naadloos herhaalt.

3.

Stel Volume  in op 0.2  om de audio op een laag volume af te spelen, zodat je de andere audio bronnen binnen de game nog steeds kunt horen.

4.

Selecteer de Wire , dan in het Properties  venster,

1.

Stel SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

Stel TargetInstance  in op je nieuwe AudioDeviceOutput  om aan te geven dat je wilt dat de draad audio naar deze specifieke luidspreker draagt.

5.

Terug in het Explorer  venster, voeg een Script  toe aan AudioPlayer , hernoem het naar LoopBackgroundMusic , stel de RunContext  eigenschap in op Client , en plak de volgende code in het script:

```

local audioPlayer = script.Parent

audioPlayer:Play()

```

Code uitleg

Het script begint met het declareren van een variabele om de ouder van het script [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  weer te geven. Het script stelt vervolgens de audio bron in om af te spelen vanaf het moment dat de speler de game binnenkomt tot het moment dat ze de game verlaten.

6.

Speel de game om de herhalende achtergrondmuziek te horen.

## [Eenmalige audio](#eenmalige-audio)[](#eenmalige-audio)

Eenmalige 2D-audio , of niet-directionele audio die eenmaal op een specifieke tijd en plaats afspeelt, tenzij een speler het opnieuw activeert, biedt spelers belangrijke context over alles wat je niet wilt dat ze missen. Het gebruik van dit type auditieve feedback in je games is essentieel omdat het een onmiddellijke, duidelijke reactie biedt op cruciale gameplay-functies en spelersacties, zoals het starten van een baasgevecht of het verliezen van een aanzienlijke hoeveelheid gezondheid.

De volgende secties bieden implementatiedetails voor veelvoorkomende gameplay-scenario's waarin spelers tijdige, niet-directionele feedback nodig hebben, inclusief gameplay-feedback, interacties met UI-elementen en voice-over-narratie voor tutorials.

### [Gameplay-feedback](#gameplay-feedback)[](#gameplay-feedback)

Naarmate spelers door je game vorderen, is het belangrijk dat ze onmiddellijke auditieve feedback ontvangen over de status van alles wat hun gameplay beïnvloedt, zoals hun score, gezondheid of voortgang in het niveau. Omdat dit type audio direct verband houdt met de doelstellingen van de speler, is het belangrijk dat deze geluiden duidelijk, hoorbaar zijn en nuttige en nauwkeurige informatie overbrengen.

Om dit concept te demonstreren, laten we de volgende eenmalige 2D-audio bekijken van de [Platformer](/docs/nl-nl/resources/templates#platformer)  template die afspeelt wanneer spelers springen en munten verzamelen:

-

Een luchtige whoosh-geluid speelt af zodra de speler de springtoets op hun apparaat indrukt.

-

Een hoge piep en het geluid van munten die schudden spelen af zodra het personage van de speler een munt aanraakt.

Beide geluiden zijn onmiddellijk herkenbaar binnen de context van de 3D-ruimte, en ze helpen spelers te begrijpen hoe succesvol hun acties zijn zonder alleen op visuele aanwijzingen te vertrouwen.

Wanneer je meerdere geluiden tegelijk afspeelt, kunnen bepaalde geluiden belangrijker zijn voor spelers om te horen dan andere. In dit geval geeft het geluid van het verzamelen van munten meer waardevolle gameplay-informatie door dan het springgeluid, dus de game speelt het op een iets hoger volume af. Er zijn echter geen standaarden of regels om een geweldige mix te bereiken, dus stem de geluiden in je game af op wat jij het belangrijkst vindt.

Bijvoorbeeld, de sample bevat verschillende audiotriggers door de game, maar ze zijn niet allemaal op hetzelfde niveau van belang voor het begrijpen van het belangrijkste doel van de game: verzamel gumdrops om het peperkoekenhuis te openen. Om ervoor te zorgen dat spelers zich bewust zijn van wat ze moeten doen, verdrievoudigt de sample de amplitude van de auditieve feedback telkens wanneer de speler een gumdrop verzamelt.

Om de eenmalige statusfeedback-audio in de sample [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

In het Explorer  venster, navigeer naar Workspace  ⟩ Gumdrops  ⟩ Gumdrop , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron te creëren.

2.

Voeg een AudioDeviceOutput  object toe om een luidspreker te creëren die door de game heen speelt.

3.

Voeg een Wire  object toe om de stream van de audio speler naar de luidspreker te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/Feedback-DataModel.jpg)

2.

Selecteer de AudioPlayer , dan in het Properties  venster,

1.

Stel AssetID  in op rbxassetid://9113723699  om een zacht kauwgeluid af te spelen.

2.

Stel TimePosition  in op 0.15  om de audiotrack dichter bij het daadwerkelijke kauwgeluid te starten.

3.

Stel Volume  in op 3  om de audio op een hoog volume af te spelen, zodat je het gumdrop-geluid boven andere audio bronnen binnen de game hoort.

3.

Selecteer de Wire , dan in het Properties  venster,

1.

Stel SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

Stel TargetInstance  in op je nieuwe AudioDeviceOutput  om aan te geven dat je wilt dat de draad audio naar deze specifieke luidspreker draagt.

4.

Dupliceer Gumdrop  totdat je drie gumdrops hebt, en verspreid ze dan door de omgeving.

5.

Terug in het Explorer  venster, navigeer naar ServerScriptService , voeg een Script  toe, hernoem het naar GumdropService , stel de RunContext  eigenschap in op Server , en plak de volgende code in het script:

```

-- Initializing services

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local ServerStorage = game:GetService("ServerStorage")

local TweenService = game:GetService("TweenService")

-- Modules

local Leaderboard = require(ServerStorage.Leaderboard)

local PlayerData = require(ServerStorage.PlayerData)

-- Variables

local gumdropsFolder = Workspace.Gumdrops

local gumdrops = gumdropsFolder:GetChildren()

local GUMDROP_KEY_NAME = PlayerData.GUMDROP_KEY_NAME

local GUMDROP_AMOUNT_TO_ADD = 1

local function updatePlayerGumdrops(player, updateFunction)

   -- Update the gumdrop table

   local newGumdropAmount = PlayerData.updateValue(player, GUMDROP_KEY_NAME, updateFunction)

   -- Update the gumdrop leaderboard

   Leaderboard.setStat(player, GUMDROP_KEY_NAME, newGumdropAmount)

   -- Check if the player has collected three gumdrops

   if newGumdropAmount >= 3 then

      -- Play the door event audio when the player collects three gumdrops

      local audioPlayer = Workspace.Door.AudioPlayer

      audioPlayer:Play()

      -- Animate the door to move downward

      local doorPart = Workspace.Door

      local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Linear)

      local tween = TweenService:Create(doorPart, tweenInfo, {Position = doorPart.Position + Vector3.new(0, -15, 0)})

      tween:Play()

   end

end

-- Defining the event handler

local function onGumdropTouched(otherPart, gumdrop)

   if gumdrop:GetAttribute("Active") then

      local character = otherPart.Parent

      local player = Players:GetPlayerFromCharacter(character)

      if player then

         -- Player touched a gumdrop

         local audioPlayer = gumdrop.AudioPlayer

         audioPlayer:Play()

         gumdrop.Transparency = 1

         gumdrop:SetAttribute("Active", false)

         updatePlayerGumdrops(player, function(oldGumdropAmount)

         oldGumdropAmount = oldGumdropAmount or 0

         return oldGumdropAmount + GUMDROP_AMOUNT_TO_ADD

         end)

      end

   end

end

-- Setting up event listeners

for _, gumdrop in gumdrops do

   gumdrop:SetAttribute("Active", true)

   gumdrop.Touched:Connect(function(otherPart)

   onGumdropTouched(otherPart, gumdrop)

   end)

end

```

Code uitleg

Dit script behandelt aanvullende functionaliteit buiten het activeren van de niet-positionele audio, zoals het bijwerken van de leaderboard elke keer dat een speler een gumdrop verzamelt en het activeren van een positioneel geluid en animatie voor de deur van het peperkoekenhuis wanneer een speler alle drie de gumdrops verzamelt. Dit is belangrijk voor de gameplay van de sample, maar het is niet belangrijk voor het begrijpen van hoe je 2D-audio implementeert, dus deze uitleg houdt die secties op een hoog niveau.

Dit script begint met het initialiseren van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , [Players](/docs/nl-nl/reference/engine/classes/Players) , [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) , en [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  services, zodat het hun kinderen en functionaliteit kan refereren. Vervolgens vereist het de Leaderboard  en PlayerData  modules in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) ; deze modules zijn verantwoordelijk voor het creëren en bijwerken van een leaderboard in de rechterbovenhoek van het scherm dat het aantal gumdrops bijhoudt dat een speler in de omgeving verzamelt.

De updatePlayerGumdrops  functie van het script is grotendeels verantwoordelijk voor zowel het bijwerken van de leaderboard elke keer dat een speler een gumdrop verzamelt, als het wachten op het moment dat ze alle drie de gumdrops verzamelen, zodat het een positioneel geluid en animatie voor de deur van het peperkoekenhuis kan activeren. Voor meer informatie over dit deel van het script, zie [Voeg 3D-audio toe - Evenementfeedback](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-3D-audio#evenementfeedback) .

De onGumdropTouched  functie van het script is waar het grootste deel van het werk plaatsvindt voor het activeren van 2D-audio voor gameplay-feedback, en het neemt twee argumenten:

-

otherPart  - Een deel dat in botsing komt met de gumdrop.

-

gumdrop  - Een sferisch deel dat een gumdrop vertegenwoordigt.

Wanneer iets in botsing komt met het gumdrop-deel, controleert het script eerst of de gumdrop actief is. Als dat zo is, controleert het of het botsende object een speler is. Als dat zo is, dan:

-

Speelt het de 2D-audio track van de audio speler af.

-

Maakt het de gumdrop onzichtbaar.

-

Deactiveert het de gumdrop zodat spelers niet met de onzichtbare gumdrop kunnen interageren.

-

Werkt het de leaderboard bij voor de speler die de gumdrop aanraakte.

Ten slotte stelt het script evenementlisteners in, zodat voor elke gumdrop een functie wordt verbonden met het [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement, dat de onGumdropTouched  functie aanroept wanneer een speler de gumdrop aanraakt.

6.

Speel de game om het kauwgeluid te horen nadat je een gumdrop hebt verzameld.

### [UI-interactie](#ui-interactie)[](#ui-interactie)

Wanneer spelers interageren met je gebruikersinterface (UI) elementen, zoals het zweven boven een selectievakje of het selecteren van een aankoopknop, is het belangrijk om onmiddellijke feedback te geven, zodat ze intuïtief begrijpen hoe  ze met je UI interageren. Veel ontwerpers veranderen bijvoorbeeld de visuele kenmerken van de UI wanneer spelers instellingen in- of uitschakelen om de status van de instelling te communiceren.

Echter, voor spelers met visuele beperkingen waarbij kleurveranderingen of animaties moeilijker te onderscheiden zijn, is het nuttig om meerdere vormen van sensorische feedback voor je UI-interacties te bieden, zodat ze toegankelijk en intuïtief blijven voor zoveel mogelijk spelers. Om dit concept verder uit te breiden, laten we de volgende UI-toestanden overwegen die belangrijk zijn voor de aankoopknoppen van de [UGC Homestore](/docs/nl-nl/resources/templates#ugc-homestore)  template:

-

In focus  - Geeft aan dat de speler een UI-element markeert ter voorbereiding op selectie.

-

Bij hover  - Geeft aan dat de speler met de cursor boven een UI-element zweeft.

-

Geselecteerd  - Geeft aan dat de speler een UI-element heeft geselecteerd via hun invoer.

Al deze drie interacties zijn essentieel voor de belangrijkste gebruikersstroom van de template waarbij spelers browsen, selecteren en kleding en accessoires voor hun avatar kopen, dus het is van het grootste belang dat niemand in de war is over hoe ze met de UI moeten interageren. Om spelers voor succes op te zetten, biedt de template zowel visuele als auditieve feedback voor elke UI-interactie.

** Visuele Feedback**

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/Default.jpg) Standaardweergave

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/In-Focus-State.jpg) In focus staat

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/On-Hover-State.jpg) Bij hover staat

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/Selected-State.jpg) Geselecteerde staat

Om een voorbeeld te geven van hoe je meerdere vormen van sensorische feedback kunt configureren, biedt de sample zowel visuele als auditieve feedback telkens wanneer spelers op de on-screen pepermuntknop drukken. Wanneer spelers niet met de knop interageren, lijkt het op een typische pepermunt, maar wanneer ze op de knop drukken, doet de sample het volgende:

-

Speelt een heerlijke jingle audiotrack af.

-

Tint de knop met een teal tint.

-

Beweegt de knop iets naar beneden op het scherm.

Van hieruit kun je deze interactie verbinden met allerlei nuttige gameplay-acties, zoals het openen van een menu of het kopen van een item.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/Button-Default.jpg) Standaardweergave

![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/Button-Pressed.jpg) Ingedrukte staat

Om de eenmalige UI-interactie audio in de sample [Gingerbread House - Complete Audio](https://www.roblox.com/games/94670255584609/Gingerbread-House-Complete-Audio)  plaatsbestand te recreëren:

1.

In het Explorer  venster, navigeer naar StarterGui  ⟩ 2DAudioButton , dan:

1.

Voeg een AudioPlayer  object toe om een audio bron te creëren.

2.

Voeg een AudioDeviceOutput  object toe om een luidspreker te creëren die door de game heen speelt.

3.

Voeg een Wire  object toe om de stream van de audio speler naar de luidspreker te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/add-2D-audio/UI-DataModel.png)

2.

Selecteer de AudioPlayer , dan in het Properties  venster, stel AssetID  in op rbxassetid://3422389728  om een retro jingle audiotrack af te spelen.

3.

Selecteer de Wire , dan in het Properties  venster,

1.

Stel SourceInstance  in op je nieuwe AudioPlayer  om aan te geven dat je wilt dat de draad audio van deze specifieke audio speler draagt.

2.

Stel TargetInstance  in op je nieuwe AudioDeviceOutput  om aan te geven dat je wilt dat de draad audio naar deze specifieke luidspreker draagt.

4.

Terug in het Explorer  venster, voeg een LocalScript  toe aan 2DAudioButton , hernoem het naar PlayAudioWhenPressed , en plak de volgende code in het script:

```

local TweenService = game:GetService("TweenService")

local buttonGui = script.Parent

local buttonImageButton = buttonGui.ButtonFrame.ButtonImageButton

local buttonAudioPlayer = buttonGui.AudioPlayer

local tweenInfo = TweenInfo.new(.2, Enum.EasingStyle.Exponential)

local buttonTweenByIsPressed = {

   -- Ingedrukt

   [true] = TweenService:Create(buttonImageButton, tweenInfo, {

      Position = buttonImageButton.Position + UDim2.fromScale(0, .1),

      ImageColor3 = Color3.fromRGB(117, 255, 255),

   }),

   -- Standaard

   [false] = TweenService:Create(buttonImageButton, tweenInfo, {

      Position = buttonImageButton.Position,

      ImageColor3 = Color3.fromRGB(255, 255, 255),

   }),

}

local function onIsPlayingChanged()

   local isPlaying = buttonAudioPlayer.IsPlaying

   local tween = buttonTweenByIsPressed[isPlaying]

   tween:Play()

end

onIsPlayingChanged()

buttonAudioPlayer:GetPropertyChangedSignal("IsPlaying"):Connect(onIsPlayingChanged)

buttonAudioPlayer.Ended:Connect(onIsPlayingChanged)

buttonImageButton.Activated:Connect(function(_hit)

   buttonAudioPlayer:Play()

end)

```

Code uitleg

Dit script behandelt aanvullende functionaliteit buiten alleen het afspelen van 2D-audio voor UI-interacties, zoals het tweenen van de kleur en positie van de knop. Dit is belangrijk voor het bieden van meerdere bronnen van sensorische feedback, maar de ontwerpeisen voor jouw gebruiksgeval vereisen mogelijk alleen auditieve feedback. Als je alleen audio wilt afspelen wanneer spelers UI-elementen aanraken, kun je de tween-functionaliteit verwijderen.

Het script begint met het verkrijgen van:

-

De [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  zodat het UI-elementen kan animeren.

-

De ouder van het script 2DAudioButton  [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  object.

-

De pepermunt [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton) .

-

De relevante audio speler met je jingle audiotrack.

Het script definieert vervolgens:

-

Een TweenInfo  object dat specificeert dat de animatie van de knop met een exponentiële animatiestijl zal afspelen.

-

Twee tweens die de ingedrukte of niet-ingedrukte staat van de knop vertegenwoordigen.

-

De true  ingedrukte staat beweegt de knop iets naar beneden op het scherm en tint het met een teal tint.

-

De false  niet-ingedrukte staat beweegt de knop terug naar zijn oorspronkelijke positie op het scherm en verwijdert de vorige tint.

De rest van het script is waar het grootste deel van het werk plaatsvindt voor het activeren van 2D UI-interactie feedback, dus laten we bekijken hoe de onIsPlayingChanged  functie en evenementlisteners samenwerken voor de UI-gebruikersstroom:

1.

buttonImageButton.Activated  luistert naar een speler die op de knop klikt, en roept vervolgens de Play()  functie aan om de bijbehorende audio van de audio speler te starten. Dit proces schakelt de [AudioPlayer.IsPlaying](/docs/nl-nl/reference/engine/classes/AudioPlayer#IsPlaying)  eigenschap van false  naar true .

2.

buttonAudioPlayer:GetPropertyChangedSignal("IsPlaying")  luistert naar de wijziging van de IsPlaying  eigenschap van de audio speler, en roept vervolgens de onIsPlayingChanged  functie aan.

3.

De onIsPlayingChanged  functie gebruikt deze informatie om de tween te activeren die de visuele verschijning op het scherm verandert.

4.

Om te voorkomen dat de speler per ongeluk de audio opnieuw start als ze snel achter elkaar op de knop klikken, luistert buttonAudioPlayer.Ended  naar de audio speler om te eindigen met afspelen voordat de onIsPlayingChanged  functie opnieuw wordt aangeroepen.

Het is belangrijk op te merken dat het onIsPlayingChanged  evenement alleen wordt geactiveerd wanneer het verandert van false  naar true , wat betekent dat het niet wordt geactiveerd wanneer het verandert van true  naar false . Dit is de bedoelde werking vanwege complicaties met de timing van het repliceren van eigenschappen van server naar client. Daarom wordt het Ended  evenement in dit voorbeeld geboden en beluisterd om beide gevallen te dekken.

5.

Speel de game om de jingle te horen elke keer dat je op de on-screen knop drukt.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
