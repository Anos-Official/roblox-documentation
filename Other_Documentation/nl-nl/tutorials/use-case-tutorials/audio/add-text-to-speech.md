<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/audio/add-text-to-speech -->

Voeg tekst-naar-spraak toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Audio

# Voeg tekst-naar-spraak toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Tekst-naar-spraak  is een vorm van assistieve technologie die tekststrings omzet in spraakgeluiden met behulp van een kunstmatige stem. Naast het verbeteren van de toegankelijkheid van je games voor spelers met visuele, motorische of cognitieve beperkingen, stelt TTS je in staat om spraak dynamisch te genereren, zodat je geen audio voor alle mogelijke verhaalscenario's van tevoren hoeft op te nemen.

Met het [Gingerbread House - Start](https://www.roblox.com/games/134812596370919/Gingerbread-House-Start)  .rbxl  bestand als startpunt en [Gingerbread House - Tekst-naar-spraak](https://www.roblox.com/games/129041658365712/Gingerbread-House-Text-to-Speech)  als referentie, laat deze tutorial je zien hoe je zowel basis- als contextbewuste TTS-audio aan je games toevoegt, inclusief richtlijnen over:

-

Het activeren van TTS voor veelvoorkomende gameplay-scenario's die nooit veranderen, zoals UI-interacties en tutorials.

-

Het configureren van TTS zodat het zich aanpast aan spelersacties, omgevingsstatus of flexibele doelstellingen.

Als je op enig moment vastloopt in het proces, kun je Gingerbread House - Tekst-naar-spraak  als referentie gebruiken om je voortgang te vergelijken.

## [Audio-objecten](#audio-objecten)[](#audio-objecten)

Om TTS-audio te creëren, is het belangrijk om de audio-objecten te begrijpen waarmee je gedurende deze tutorial zult werken. Er zijn vijf hoofdtypen audio-objecten voor TTS:

-

Het [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  object zet tekststrings om in spraakgeluiden.

-

Het [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  object is een virtuele luidspreker  die audio in de 3D-omgeving uitzendt.

-

Het [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  object is een virtuele microfoon  die audio uit de 3D-omgeving opvangt.

-

Het [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object is een fysiek hardware-apparaat  in de echte wereld, zoals een luidspreker of hoofdtelefoon.

-

[Wires](/docs/nl-nl/reference/engine/classes/Wire)  dragen audiostreams van het ene object naar het andere.

Al deze audio-objecten werken samen om TTS-geluid uit te zenden als reactie op spelersacties. Laten we eens kijken hoe dit in de praktijk werkt voor 3D-audio met een voorbeeld van een speler die een headset draagt terwijl hij een game speelt met zijn laptop:

-

Het [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  laadt en zet tekst om in audio telkens wanneer een speler een deel aanraakt in de buurt van een niet-speelbaar personage (NPC).

-

Het [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  zendt een stroom van de TTS-audio van de NPC uit in de 3D-omgeving.

-

Een [Wire](/docs/nl-nl/reference/engine/classes/Wire)  draagt de stroom van de [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  naar de [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) , zodat de stroom uit de NPC komt.

-

Het kind [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  object van het personage luistert naar dat geluid binnen de 3D-omgeving en geeft het terug aan hun headset.

-

Het [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  object draagt het geluid van de [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  naar de fysieke luidspreker van de speler, of in dit geval, hun hoofdtelefoon.

De volgende secties gaan dieper in op deze objecten terwijl je leert hoe je zowel basis- als contextbewuste audio afspeelt. Terwijl je deze objecten met de komende technieken bekijkt, kun je nauwkeuriger voorspellen hoe je geluid uit het spel naar de speler kunt vastleggen en doorgeven.

## [Basis TTS](#basis-tts)[](#basis-tts)

Basis TTS is de meest voorkomende vorm van tekst-naar-spraak waarin de kunstmatige stem een tekststring voorleest, ongeacht de context van de speler of de omgeving. Dit betekent dat telkens wanneer de speler de TTS-audio activeert, de woorden en de manier waarop de kunstmatige stem de woorden voorleest consistent blijven, ongeacht de staat van de speler, hun acties of de omgevingsstatus.

Deze vorm van TTS is nuttig in de meeste gameplay-scenario's, zoals spelers die interactie hebben met UI-menu's, tutorials of routinematige NPC-interacties zoals aanbiedingen van verkopers of vijandelijke kreten. Roblox biedt een scala aan kunstmatige stemmen waarmee je kunt experimenteren voor een van deze interacties. Voor de volledige lijst van beschikbare stemmen en audiofragmenten van elk, zie de [lijst van kunstmatige stemmen](/docs/nl-nl/audio/objects#lijst-van-kunstmatige-stemmen) .

Om de basis 3D TTS-audio in het voorbeeld [Gingerbread House - Tekst-naar-spraak](https://www.roblox.com/games/129041658365712/Gingerbread-House-Text-to-Speech)  plaatsbestand te recreëren:

1.

Schakel een standaard luisteraar in die aan je speler karakter is gekoppeld.

1.

Selecteer in het Explorer  venster de SoundService .

2.

Stel in het Properties  venster DefaultListenerLocation  in op Character . Wanneer je het spel uitvoert, maakt de engine automatisch:

-

Een [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  onder elk [Humanoid.RootPart](/docs/nl-nl/reference/engine/classes/Humanoid#RootPart)  van de speler karakters, zodat je geluiden kunt horen verschuiven in je echte luidsprekers volgens de positie en schaal van geluidsbronnen binnen het spel.

-

Een [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput)  onder SoundService .

2.

Navigeer in het Explorer  venster naar Workspace  ⟩ DialogueVolume , dan:

1.

Voeg een AudioTextToSpeech  object toe om een audio spraakgenerator voor het volume rond de sneeuwman te creëren.

2.

Voeg een AudioEmitter  object toe om een positionele stroom van DialogueVolume  uit te zenden.

3.

Voeg een Wire  object toe om de stroom van de audio spraakgenerator naar de audio emitter te dragen.

3.

Selecteer het AudioTextToSpeech  object, en stel in het Properties  venster:

1.

Stel Text  in op "Verzamel elke laatste gumpdrop om mijn huis te openen!"

2.

Stel VoiceId  in op 2  om de kunstmatige stem in te stellen op een Britse vrouwelijke stem.

3.

Stel het Volume  in op 3  om de audio op een hoog volume af te spelen, zodat je het TTS-geluid boven andere audiobronnen binnen het spel hoort.

4.

Selecteer de Wire , en stel in het Properties  venster:

1.

Stel SourceInstance  in op je nieuwe AudioTextToSpeech  om aan te geven dat je wilt dat de draad audio van deze specifieke audio spraakgenerator draagt.

2.

Stel TargetInstance  in op je nieuwe AudioEmitter  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio emitter binnen het volume draagt.

5.

Navigeer in het Explorer  venster naar StarterPlayer  ⟩ StarterCharacterScripts , voeg een LocalScript  toe, hernoem het naar PlayBasicTTSAudioWhenInVolume , en plak de volgende code in het lokale script:

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

  local audioTextToSpeech = Workspace.DialogueVolume.AudioTextToSpeech

  audioTextToSpeech:Play()

  audioTextToSpeech.Ended:Wait()

  debounce = false

end)

```

Code uitleg

Dit script begint met het verkrijgen van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  en [Players](/docs/nl-nl/reference/engine/classes/Players)  services, zodat het hun kinderen en functionaliteit kan refereren. Voor elk speler karakter dat in het spel laadt of opnieuw spawnt, wacht het script op:

-

De [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en [Animator](/docs/nl-nl/reference/engine/classes/Animator)  objecten van het karakter.

-

Het volume-object in de workspace genaamd DialogueVolume .

Wanneer iets met het volume botst, krijgt de Touched  event handler functie de eerste voorouder die een [Model](/docs/nl-nl/reference/engine/classes/Model)  is, wat het karakter zou moeten zijn als de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die met het volume botste een afgeleide is van een karaktermodel. Als dat zo is, dan:

-

Zet debounce op true .

-

Speelt en wacht op het eindigen van de TTS-audio.

-

Zet debounce terug op false .

Het instellen van debounce van false  naar true  en weer naar false  nadat de basis TTS-audio is afgelopen met afspelen is een debounce-patroon dat voorkomt dat de audio herhaaldelijk wordt geactiveerd terwijl spelers continu met het volume botsen. Voor meer informatie over dit debounce-patroon, zie [Debounce - Detecteer botsingen](/docs/nl-nl/scripting/debounce#detecteer-botsingen) .

1.

Speel het spel om de instructieve dialoog van het personage te horen wanneer je speler karakter het volume rond de sneeuwman aanraakt.

Je kunt verder experimenteren met deze audio door de [Text](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Text) , [VoiceID](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#VoiceID) , [Pitch](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Pitch) , en [Speed](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Speed)  eigenschappen naar nieuwe waarden te wijzigen. De gegenereerde spraak wordt volledig anders zonder dat je een nieuw audiobestand voor elk scenario hoeft op te nemen en te uploaden.

|  | |  | |  |
| --- | --- |
|

-

[VoiceID](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#VoiceID)  = 2

-

[Pitch](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Pitch)  = -12

-

[Speed](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Speed)  = 2

 | |

-

[VoiceID](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#VoiceID)  = 7

-

[Pitch](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Pitch)  = 7

-

[Speed](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Speed)  = 0.8

 | |

-

[VoiceID](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#VoiceID)  = 9

-

[Pitch](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Pitch)  = 12

-

[Speed](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech#Speed)  = 1.2

 |

## [Contextbewuste TTS](#contextbewuste-tts)[](#contextbewuste-tts)

Contextbewuste TTS is een geavanceerdere vorm van tekst-naar-spraak waarin de kunstmatige stem een tekststring leest in relatie tot de speler, de staat van hun omgeving of de gameplay-status. Dit betekent dat telkens wanneer de speler de TTS-audio activeert, de woorden en de manier waarop de kunstmatige stem de woorden leest zich dienovereenkomstig aanpast.

Deze vorm van TTS is nuttig voor gameplay-scenario's die voortdurend veranderen, zoals directionele audiocues, doelstatus of unieke NPC-interacties. Daarom, omdat contextbewuste TTS moet transformeren om nauwkeurig te zijn, moet je gameplay-elementen configureren zodat je hun status kunt volgen terwijl spelers door de omgeving navigeren en gameplay-doelstellingen voltooien.

Hoewel er veel manieren zijn om deze taak te volbrengen, gebruikt het voorbeeld aangepaste attributen om de kleur  en locatie  van elke gumpdrop die de speler moet verzamelen om het peperkoekhuis binnen te gaan, bij te houden. Voor meer informatie over attributen, zie [Eigenschappen en attributen](/docs/nl-nl/scripting/attributes) .

** Elk gumpdrop-object heeft attributen die hun kleur en locatie in de omgeving beschrijven.**

![Een close-up van de gele gumpdrop](https://prod.docsiteassets.roblox.com/assets/tutorials/add-text-to-speech/YellowGumdrop.png)

![Een close-up van de groene gumpdrop](https://prod.docsiteassets.roblox.com/assets/tutorials/add-text-to-speech/GreenGumdrop.png)

![Een close-up van de rode gumpdrop](https://prod.docsiteassets.roblox.com/assets/tutorials/add-text-to-speech/RedGumdrop.png)

Om de contextbewuste 3D TTS-audio in het voorbeeld [Gingerbread House - Tekst-naar-spraak](https://www.roblox.com/games/129041658365712/Gingerbread-House-Text-to-Speech)  plaatsbestand te recreëren:

1.

Navigeer in het Explorer  venster naar Workspace  ⟩ GumDrops .

2.

Configureer drie aangepaste attributen om de gele gumpdrop bij te houden.

1.

Selecteer de gele gumpdrop, en ga in het Properties  venster naar de sectie Attributes , klik dan op het pluspictogram. Een pop-updialoog verschijnt.

2.

Vul in het Name  veld ColorDescription  in.

3.

Selecteer in het Type  dropdownmenu string .

4.

Klik op de Opslaan  knop.

5.

Stel het nieuwe ColorDescription  attribuut in op geel .

6.

Gebruik dit proces om nog twee attributen te maken met de volgende waarden.

| Naam | | Type | | Waarde |
| HintOrder | | nummer | | 0 |
| LocationDescription | | string | | bij de waterval |

3.

Configureer drie aangepaste attributen om de groene gumpdrop bij te houden.

1.

Selecteer in het Explorer  venster de groene gumpdrop.

2.

Maak in het Properties  venster drie attributen met de volgende waarden.

| Naam | | Type | | Waarde |
| ColorDescription | | string | | groen |
| HintOrder | | nummer | | 1 |
| LocationDescription | | string | | op de rand |

4.

Configureer drie aangepaste attributen om de rode gumpdrop bij te houden.

1.

Selecteer in het Explorer  venster de rode gumpdrop.

2.

Maak in het Properties  venster drie attributen met de volgende waarden.

| Naam | | Type | | Waarde |
| ColorDescription | | string | | rood |
| HintOrder | | nummer | | 2 |
| LocationDescription | | string | | achter het hek |

5.

Navigeer in het Explorer  venster naar Workspace  ⟩ HintVolume , dan:

1.

Voeg een AudioTextToSpeech  object toe om een audio spraakgenerator voor het volume rond de rendier te creëren.

2.

Voeg een AudioEmitter  object toe om een positionele stroom van HintVolume  uit te zenden.

3.

Voeg een Wire  object toe om de stroom van de audio spraakgenerator naar de audio emitter te dragen.

6.

Selecteer de Wire , en stel in het Properties  venster:

1.

Stel SourceInstance  in op je nieuwe AudioTextToSpeech  om aan te geven dat je wilt dat de draad audio van deze specifieke audio spraakgenerator draagt.

2.

Stel TargetInstance  in op je nieuwe AudioEmitter  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio emitter binnen het volume draagt.

7.

Navigeer in het Explorer  venster naar StarterPlayer  ⟩ StarterCharacterScripts , voeg een LocalScript  toe, hernoem het naar PlayContextTTSAudioWhenInVolume , en plak de volgende code in het lokale script:

```

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local humanoid = script.Parent:WaitForChild("Humanoid")

local volumeDetector = Workspace.HintVolume

local trigger = humanoid:WaitForChild("Animator")

local debounce = false

local localPlayer = Players.LocalPlayer

function getRemainingGumdrops(): {Part}

  local gumdropsFolder = Workspace.Gumdrops

  local gumdrops = gumdropsFolder:GetChildren()

  local remainingGumdrops = {};

  for _, gumdrop in gumdrops do

    if gumdrop:GetAttribute("Active") then

      remainingGumdrops[#remainingGumdrops + 1] = gumdrop

    end

  end

  table.sort(remainingGumdrops, function(a, b)

    return a:GetAttribute("HintOrder") < b:GetAttribute("HintOrder")

  end)

  return remainingGumdrops

end

function getReindeerHint(remainingGumdrops: {Part}): string

  local remainingGumdrops = getRemainingGumdrops()

  if (#remainingGumdrops == 0) then

    return "Er zijn geen gumpdrops meer. Kijk binnen in het huis."

  end

  local nextGumdrop = remainingGumdrops[1]

  local colorDescription = nextGumdrop:GetAttribute("ColorDescription")

  local locationDescription = nextGumdrop:GetAttribute("LocationDescription")

  local message = #remainingGumdrops > 1

    and  "Er zijn " .. #remainingGumdrops .. " gumpdrops over. Zoek de " .. colorDescription  .. " een " .. locationDescription  .. "."

    or "Er is één gumpdrop over. Het is " .. colorDescription .. " en het is " .. locationDescription .. "."

  return message

end

volumeDetector.Touched:Connect(function(hit)

  if debounce then

    return

  end

  local hitCharacter = hit:FindFirstAncestorWhichIsA("Model")

  local hitPlayer = Players:GetPlayerFromCharacter(hitCharacter)

  if hitPlayer ~= localPlayer then

    return

  end

    print("Speler raakte volume aan.")

    debounce = true

    local remainingGumdrops = getRemainingGumdrops()

    local message = getReindeerHint(remainingGumdrops)

    local audioTextToSpeech = Workspace.HintVolume.AudioTextToSpeech

    audioTextToSpeech.Text = message

    audioTextToSpeech:Play()

    audioTextToSpeech.Ended:Wait()

    debounce = false

end)

```

Code uitleg

Dit script begint met het verkrijgen van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  en [Players](/docs/nl-nl/reference/engine/classes/Players)  services, zodat het hun kinderen en functionaliteit kan refereren. Voor elk speler karakter dat in het spel laadt of opnieuw spawnt, wacht het script op:

-

De [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en [Animator](/docs/nl-nl/reference/engine/classes/Animator)  objecten van het karakter.

-

Het volume-object in de workspace genaamd HintVolume .

De functie getRemainingGumdrops()  van het script retourneert een lijst van gumpdrop [Part](/docs/nl-nl/reference/engine/classes/Part)  objecten binnen de Gumdrops  map en filtert alle delen die de speler heeft verzameld. De resterende gumpdrops worden gesorteerd in een specifieke volgorde volgens het HintOrder  attribuut van elke gumpdrop.

De functie getReindeerHint(remainingGumdrops)  van het script neemt die lijst van getRemainingGumdrops()  en retourneert een stringbericht dat beschrijft waar de speler de resterende gumpdrops kan vinden, inclusief zowel de kleur- als locatiebeschrijving van de volgende gumpdrop die de speler moet verzamelen. Als de speler echter alle gumpdrops in de omgeving heeft verzameld, beschrijft het stringbericht waar ze naartoe moeten gaan nadat ze alle gumpdrops in de omgeving hebben verzameld.

Wanneer iets met het volume botst, krijgt de Touched  event handler functie de eerste voorouder die een [Model](/docs/nl-nl/reference/engine/classes/Model)  is, wat het karakter zou moeten zijn als de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die met het volume botste een afgeleide is van een karaktermodel. Als dat zo is, dan:

-

Zet debounce op true .

-

Krijgt de lijst van resterende gumpdrops en het stringbericht dat de volgende gumpdrop beschrijft die de speler moet vinden.

-

Zet de string om in audio met behulp van het [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)  object, speelt de audio af en wacht tot de audio is afgelopen.

-

Zet debounce terug op false .

Het instellen van debounce van false  naar true  en weer naar false  nadat de contextbewuste TTS-audio is afgelopen met afspelen is een debounce-patroon dat voorkomt dat de audio herhaaldelijk wordt geactiveerd terwijl spelers continu met het volume botsen. Voor meer informatie over dit debounce-patroon, zie [Debounce - Detecteer botsingen](/docs/nl-nl/scripting/debounce#detecteer-botsingen) .

1.

Speel het spel om contextuele hints te horen wanneer je speler karakter het volume rond de rendier aanraakt. De TTS-audio verandert op basis van het aantal en de kleur van gumpdrops die de speler karakter al in de omgeving heeft gevonden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
