<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/audio/speech-to-text -->

Voeg spraak-naar-tekst toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Audio

# Voeg spraak-naar-tekst toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Spraak-naar-tekst  (STT) is een vorm van technologie die automatisch tekst genereert uit spraakgeluiden. Met STT kun je meer meeslepende werelden creëren door spelers in staat te stellen te praten met NPC's, tekst te genereren zonder dat specifieke audio vooraf hoeft te worden opgenomen, de toegankelijkheid voor spelers met motorische of visuele beperkingen te verbeteren en spelers handsfree bediening te bieden via spraakopdrachten voor acties zoals het openen van hun inventaris of het uitspreken van een spreuk.

Met het [Gingerbread House - Start](https://www.roblox.com/games/134812596370919/Gingerbread-House-Start)  .rbxl  bestand als startpunt, laat deze tutorial je zien hoe je tekst die dynamisch uit spraak wordt gegenereerd aan je game toevoegt, inclusief richtlijnen over hoe je STT implementeert zodat de speler kan interageren met objecten in jouw 3D-wereld.

Voor meer algemene richtlijnen over het toevoegen van audio aan je game, zie de [Voeg 2D-audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-2D-audio)  en [Voeg 3D-audio toe](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-3D-audio)  tutorials.

Voor betrouwbaardere spraakdetectie, gebruik [druk om te chatten](/docs/nl-nl/tutorials/use-case-tutorials/audio/add-voice-chat#voeg-push-to-chat-toe)  naast STT. Dit zorgt ervoor dat de microfoons van spelers alleen actief zijn terwijl ze een specifieke knop op hun apparaat ingedrukt houden.

## [Audio-objecten](#audio-objecten)[](#audio-objecten)

Om STT-audio te creëren, is het belangrijk om de audio-objecten te begrijpen waarmee je gedurende deze tutorial zult werken. Er zijn drie soorten audio-objecten voor STT:

-

Het [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object is een fysiek hardwareapparaat in de echte wereld, zoals een microfoon in een laptop, telefoon of headset.

-

Het [AudioSpeechToText](/docs/nl-nl/reference/engine/classes/AudioSpeechToText)  object converteert spraakgeluiden naar tekststrings.

-

[Wires](/docs/nl-nl/reference/engine/classes/Wire)  dragen audiostreams van het ene object naar het andere.

Al deze audio-objecten werken samen om STT-tekst te genereren als reactie op spelersacties. Bijvoorbeeld, als de speler een headset draagt terwijl hij een game speelt met zijn laptop:

-

De AudioDeviceInput  vangt de spraak van de speler op, zoals gesproken in hun microfoon en als een audiostream.

-

Een Wire  draagt de audiostream van de AudioDeviceInput  naar de AudioSpeechToText .

-

De AudioSpeechToText  converteert de spraak van de speler naar tekst.

-

De game leest deze tekst en voert een actie uit, zoals het weergeven van de gesproken tekst op het scherm of het openen van een deur op commando van de speler.

## [Microfoongebruik inschakelen](#microfoongebruik-inschakelen)[](#microfoongebruik-inschakelen)

Voordat je STT aan een game toevoegt, moet je eerst het gebruik van de microfoon inschakelen en de game publiceren.

1.

Open het [Gingerbread House - Start](https://www.roblox.com/games/134812596370919/Gingerbread-House-Start)  bestand in Studio.

2.

Maak een lokale kopie.

3.

Publiceer je lokale kopie van de game.

4.

Ga terug naar Studio, ga naar Bestand  ⟩ Ervaringsinstellingen  ⟩ Communicatie .

5.

Zet Microfoon inschakelen  aan.

6.

Sla je wijzigingen op.

## [Voeg eenvoudige spraakopname toe](#voeg-eenvoudige-spraakopname-toe)[](#voeg-eenvoudige-spraakopname-toe)

Om eenvoudige spraakopname aan je lokale kopie van het [Gingerbread House - Start](https://www.roblox.com/games/134812596370919/Gingerbread-House-Start)  bestand toe te voegen:

1.

Schakel het gebruik van de nieuwste API voor spraak in.

1.

In het Explorer  venster, selecteer de VoiceChatService .

2.

In het Eigenschappen  venster, stel UseAudioApi  in op Ingeschakeld .

2.

Maak de basis audio-objecten die je in staat stellen gesproken woorden op te nemen.

1.

In het Explorer  venster, ga naar Workspace  > DialogueVolume .

2.

Verwijder alle objecten in de DialogueVolume  map.

3.

Voeg de volgende objecten toe aan de DialogueVolume  map:

-

Een AudioDeviceInput  om spraak op te nemen.

-

Een AudioSpeechToText  om de spraak naar tekst te converteren.

-

Een Wire  om de stream van de audio-invoerapparaat naar de STT-instantie te dragen.

4.

In het Eigenschappen  venster van het AudioSpeechToText  object, stel de Ingeschakeld  status in op aan.

5.

In het Eigenschappen  venster van het Wire  object:

1.

Stel SourceInstance  in op je nieuwe AudioDeviceInput  om aan te geven dat je wilt dat de draad audio van deze specifieke audio-instantie draagt.

2.

Stel TargetInstance  in op je nieuwe AudioSpeechToText  om aan te geven dat je wilt dat de draad audio naar deze specifieke audio-instantie draagt.

3.

Stel de Speler  eigenschap van het audio-invoerapparaat in op de lokale speler tijdens runtime. Dit vertelt Roblox van welke gebruiker de microfoon audio moet opnemen.

1.

In het Explorer  venster, ga naar StarterPlayer  > StarterCharacterScripts .

2.

Voeg een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe en noem het ListenForMagicWord .

3.

Plak de volgende code in het nieuwe lokale script:

```

local audioDeviceInput = workspace:WaitForChild('DialogueVolume'):WaitForChild('AudioDeviceInput')

  -- Koppelt de microfoon aan de lokale speler

  audioDeviceInput.Player = game.Players.LocalPlayer

```

### [Test je spraakopname](#test-je-spraakopname)[](#test-je-spraakopname)

Nadat je eenvoudige spraakopname hebt toegevoegd, kun je de game testen om ervoor te zorgen dat je STT-implementatie goed werkt. Spreken in je microfoon zou de AudioSpeechToText  eigenschap moeten vullen met de tekstversie van je spraak.

Om je spraakopname te testen:

1.

Onder Test  > Klanten en Servers , selecteer Team Test .

2.

Klik op Start  om de testserver te starten.

3.

In de nieuwe testserver, demuteer je microfoon en spreek een paar woorden.

4.

In het Explorer  venster, ga naar Workspace  > DialogueVolume  > AudioSpeechToText .

5.

In het Eigenschappen  venster van AudioSpeechToText , bevestig dat de woorden die je in je microfoon sprak zijn verschenen als de waarde van de Text  eigenschap.

## [Gebruik STT met gameplay](#gebruik-stt-met-gameplay)[](#gebruik-stt-met-gameplay)

Om STT te verbinden met gameplay en de deur van het peperkoekhuis te openen wanneer de speler "Open Sesame" in hun microfoon zegt:

1.

Maak een remote event om de client met de server te verbinden.

1.

In het Explorer  venster, voeg een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  toe onder ReplicatedStorage .

2.

Noem het OpenDoor .

2.

Voeg een nieuw script toe om de opening van de deur van het peperkoekhuis te animeren.

1.

Onder ServerScriptService , voeg een server-side [Script](/docs/nl-nl/reference/engine/classes/Script)  toe.

2.

Noem het DoorService .

3.

Plak de volgende code in het nieuwe script:

```

-- Krijgt de ReplicatedStorage service voor gedeelde opslag tussen server en client

  -- Krijgt de TweenService voor het tweening systeem

  local ReplicatedStorage = game:GetService("ReplicatedStorage")

  local TweenService = game:GetService("TweenService")

  -- Laat de client de server vragen om de deur te openen

  local remoteEvent = ReplicatedStorage:WaitForChild("OpenDoor")

  -- Functie die de deur animeert om naar beneden te bewegen en te openen

  local function openDoor()

    local doorPart = workspace:WaitForChild("Door")

    local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Linear)

    local tween = TweenService:Create(doorPart, tweenInfo, {Position = doorPart.Position + Vector3.new(0, -15, 0)})

    tween:Play()

  end

  -- Verbindt de functie met het evenement

  remoteEvent.OnServerEvent:Connect(openDoor)

```

3.

Verbind de deur met spraak-naar-tekst zodat er een actie plaatsvindt wanneer de speler in hun microfoon spreekt.

1.

Ga naar StarterPlayer  > StarterCharacterScripts .

2.

Open het ListenForMagicWord  script dat je eerder hebt gemaakt.

3.

Voeg de volgende regels toe:

```

-- Krijgt de ReplicatedStorage service voor gedeelde opslag tussen server en client

  local ReplicatedStorage = game:GetService("ReplicatedStorage")

  -- Krijgt de RemoveEvent die de client naar de server zal afvuren

  local remoteEvent = ReplicatedStorage:WaitForChild("OpenDoor")

  -- Vindt de STT-knoop in de scène-grafiek

  -- De Text-eigenschap van de knoop wordt bijgewerkt terwijl deze spraak herkent

  local speechToText = workspace:WaitForChild('DialogueVolume'):WaitForChild('AudioSpeechToText')

  -- Functie die de server vertelt de deur te openen als STT de speler "Open Sesame" laat zeggen

  speechToText:GetPropertyChangedSignal('Text'):Connect(function()

    local text = speechToText.Text

    if text == '' then

      return

    end

    print(text)

    if (text.find(text, 'open sesame') ~= nil)  then

      remoteEvent:FireServer()

    end

    speechToText.Text = ''

  end)

```

4.

Test je STT-implementatie.

1.

Onder Test  > Klanten en Servers , selecteer Team Test .

2.

Klik op Start  om de testserver te starten.

3.

In de nieuwe testserver, loop naar de deur, demuteer je microfoon en zeg "Open Sesame". De deur zou moeten openen en je binnenlaten in het peperkoekhuis.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
