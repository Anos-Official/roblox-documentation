<!-- Source: https://create.roblox.com/docs/nl-nl/sound/objects -->

Geluidsobjecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Geluidsobjecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Er is een nieuwere set van [audio-objecten](/docs/nl-nl/audio/objects)  die meer controle bieden en robuuste gebruiksscenario's aanpakken. Voor meer informatie, zie [Audio](/docs/nl-nl/audio) .

Audio-afspeel gebeurt via [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten die audio binnen een spel uitzenden. Roblox kent elk [audio-asset](/docs/nl-nl/audio/assets)  een unieke ID toe die je kunt toewijzen aan [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten om een specifiek geluidseffect of muzieknummer af te spelen. Je kunt deze audio automatisch laten afspelen tijdens runtime, of het laten [afspelen vanuit scripts](#script-geluidsobjecten) .

Om de afspeel van meerdere [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten te wijzigen, kun je ze toewijzen aan een [geluidsgroep](/docs/nl-nl/sound/groups)  en het volume van de hele groep regelen, evenals [dynamische effecten](/docs/nl-nl/sound/dynamic-effects)  toepassen.

## [Geluidsobjecten maken](#geluidsobjecten-maken)[](#geluidsobjecten-maken)

Er zijn drie locaties waar je een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object kunt maken, en elke locatie bepaalt hoe audio uitzendt en hoe het volume verandert in relatie tot de positie van de gebruiker binnen het spel.

| Locatie | | Hoe audio uitzendt | | Hoe volume verandert |
| --- | --- |
| Kind van een blok, bol of cilinder [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) . | | Audio zendt naar buiten uit vanaf het gehele oppervlak van het onderdeel. | | Volume verandert afhankelijk van de afstand tussen de geluidsluisteraar van de gebruiker en de positie van het onderdeel, evenals de grootte ervan. |
| Kind van een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , [TrussPart](/docs/nl-nl/reference/engine/classes/TrussPart) , [WedgePart](/docs/nl-nl/reference/engine/classes/WedgePart) , of [CornerWedgePart](/docs/nl-nl/reference/engine/classes/CornerWedgePart) . | | Audio zendt naar buiten uit vanaf het enkele bevestigingspunt of het middelpunt van het onderdeel. | | Volume verandert afhankelijk van de afstand tussen de geluidsluisteraar van de gebruiker en de bevestiging/onderdeel positie. |
| Binnen [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  of [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . | | Audio zendt uit door het hele spel. | | Volume en panpositie blijven hetzelfde, ongeacht de positie of rotatie van de geluidsluisteraar van de gebruiker. |

### [Positional audio](#positional-audio)[](#positional-audio)

Positional audio is audio die gebruikers alleen kunnen horen nabij een specifieke positie binnen het spel. Er zijn twee soorten positional audio die je kunt gebruiken: volumetrisch en puntbron.

#### [Volumetrisch](#volumetrisch)[](#volumetrisch)

Volumetrische audio is de meest realistische audio-optie, omdat het dynamisch verandert afhankelijk van de positie van de gebruiker ten opzichte van de audio-bron. Bijvoorbeeld, als de gebruiker zich binnen een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  met een kind [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object bevindt, speelt de audio rondom de gebruiker, vergelijkbaar met muziek in hoofdtelefoons die op hetzelfde volume in elke luidspreker speelt. Wanneer de gebruiker het onderdeel verlaat, neemt de audio geleidelijk in volume af en wordt het meer directioneel per luidspreker, terwijl het rond het hoofd van de gebruiker beweegt wanneer hun luisteraar draait. Voor informatie over de eigenschappen die bepalen hoe luid je audio is op verschillende afstanden van het onderdeel, zie [RollOffMinDistance en RollOffMaxDistance](#rolloffmindistance-en-rolloffmaxdistance) .

De grootte van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  beïnvloedt ook het volume van de audio, aangezien grotere [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  een groter gebied produceren waarin gebruikers de audio kunnen horen en wanneer een gebruiker zich van een grote [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  verwijdert, neemt het volume langzamer af. Het volgende voorbeeld toont een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die de grootte van een stad heeft met een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object dat ambient audio afspeelt. Gebruikers A en B ervaren de audio anders: gebruiker B is dichter bij de grote [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , en zij horen de audio meestal rond dezelfde luidheid in beide luidsprekers. Omgekeerd is gebruiker A verder weg van de stad, dus de audio die zij horen is stiller en meer directioneel dan die van gebruiker B, die op verschillende luidheid in elk van hun luidsprekers speelt.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/Volumetric-Sound-Diagram.jpg)

Volumetrische audio is nuttig voor elke audio die meeslepend moet zijn rondom een gebruiker en dynamisch moet veranderen afhankelijk van de positie van de gebruiker, zoals een concertpodium of ambiancezones zoals regenval. Wanneer je experimenteert met het plaatsen van een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object op [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  van verschillende groottes en posities ten opzichte van gebruikers, kun je horen hoe meeslepend volumetrische audio kan zijn.

Om een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object voor volumetrische audio te maken:

1.

In het Explorer  venster, selecteer SoundService .

2.

In het Properties  venster, navigeer naar de VolumetricAudio  eigenschap, en stel deze in op Enabled .

3.

In het Explorer  venster, zweef over een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , en klik dan op de ⊕ knop. Een contextmenu verschijnt.

4.

Kies in het menu voor Sound .

5.

In het Properties  venster, navigeer naar de SoundId  eigenschap en voer een geldige [audio asset ID](/docs/nl-nl/audio/assets)  in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sound-SoundId.png)

6.

OPTIONEEL

 Als je wilt dat de audio begint te spelen wanneer het spel begint, schakel dan de Playing  eigenschap in.

#### [Puntbron](#puntbron)[](#puntbron)

In tegenstelling tot volumetrische audio, zendt puntbron audio alleen uit vanaf een enkel punt. Dit type audio is nuttig voor explosies, impactgeluiden, elektronische apparaten en dialoog.

Om een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object voor puntbron audio te maken:

1.

In het Explorer  venster, zweef over een bevestiging, truss, wig of hoekwig, en klik dan op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor Sound .

3.

In het Properties  venster, navigeer naar de SoundId  eigenschap en voer een geldige [audio asset ID](/docs/nl-nl/audio/assets)  in.

4.

OPTIONEEL

 Als je wilt dat de audio begint te spelen wanneer het spel begint, schakel dan de Playing  eigenschap in.

### [Achtergrondaudio](#achtergrondaudio)[](#achtergrondaudio)

Achtergrondaudio speelt op hetzelfde volume, ongeacht waar de gebruiker zich binnen je spel bevindt. Dit type audio is nuttig voor muziek die je voor gebruikers wilt afspelen, vooral wanneer je een soundtrack van meerdere audio-bestanden wilt creëren.

Het is het beste om alle [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten voor achtergrondaudio op één locatie in de Workspace te houden voor organisatorische doeleinden terwijl je blijft toevoegen en bewerken van audio binnen je spel. Het volgende voorbeeld slaat het nieuwe [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object op onder de [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  container, aangezien deze service bepaalt hoe [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten in spellen afspelen.

Om een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object voor achtergrondaudio te maken:

1.

In het Explorer  venster, zweef over SoundService , en klik dan op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor Sound .

3.

In het Properties  venster, navigeer naar de SoundId  eigenschap en voer een geldige [audio asset ID](/docs/nl-nl/audio/assets)  in.

4.

OPTIONEEL

 Als je wilt dat de audio begint te spelen wanneer het spel begint, schakel dan de Playing  eigenschap in.

5.

OPTIONEEL

 Als dit [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object het enige nummer is dat je in de plaats wilt afspelen, schakel dan de Looped  eigenschap in.

## [Geluidsobjecten aanpassen](#geluidsobjecten-aanpassen)[](#geluidsobjecten-aanpassen)

De eigenschappen van [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten werken samen om te beïnvloeden hoe gebruikers je audio ervaren, zoals:

-

Hoe luid ze specifieke audio individueel en in relatie tot elkaar horen ([Volume](#volume) ).

-

Hoe ze volume waarnemen wanneer ze zich van de audio-bron verwijderen ([RollOffMinDistance](#rolloffmindistance-en-rolloffmaxdistance) , [RollOffMaxDistance](#rolloffmindistance-en-rolloffmaxdistance) , en [RollOffMode](#rolloffmode) )

-

Welk deel van de audio ze kunnen beluisteren ([TimePosition](#timeposition) ).

-

Hoe snel en met welke toonhoogte ze het horen ([PlaybackSpeed](#playbackspeed) ).

-

Of de audio automatisch opnieuw afspeelt na voltooiing ([Looped](#looped) ).

### [Volume](#volume)[](#volume)

De [Volume](/docs/nl-nl/reference/engine/classes/Sound#Volume)  eigenschap stelt je in staat om het volume van je audio in te stellen van 0  (stilte) tot 10  (donker). Als je het volume van meerdere [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten tegelijk wilt wijzigen, plaats ze dan onder een [geluidsgroep](/docs/nl-nl/sound/groups) .

Als je bronaudio voldoende luid is, hoef je het volume waarschijnlijk niet hoger dan 2  te verhogen, aangezien deze eigenschap multiplicatief is. Bijvoorbeeld: een [Volume](/docs/nl-nl/reference/engine/classes/Sound#Volume)  waarde van 4  is vier keer zo luid als een [Volume](/docs/nl-nl/reference/engine/classes/Sound#Volume)  waarde van 1 , dus als je bronaudio al luid was, kan de audio overweldigend worden voor gebruikers.

### [RollOffMinDistance en RollOffMaxDistance](#rolloffmindistance-en-rolloffmaxdistance)[](#rolloffmindistance-en-rolloffmaxdistance)

[RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  en [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  bepalen het bereik van hoe een gebruiker volume waarneemt van positional audio. Voor volumetrische audio is [RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  de minimale afstand in studs waar audio begint te verminderen in volume wanneer de luisteraar van de client zich verwijdert  van de ouder [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , en de [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  eigenschap is de maximale afstand in studs waar een luisteraar van de client audio kan horen van het oppervlak van het object.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/Sound-Volumetric-RollOff.jpg)

Voor puntbron audio werken [RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  en [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  op een vergelijkbare manier als volumetrische audio, maar de roll-off afstand die deze eigenschappen regelen omringt het object niet, het beïnvloedt alleen de afstand naar buiten vanaf de puntbron.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/Sound-Point-RollOff.jpg)

### [RollOffMode](#rolloffmode)[](#rolloffmode)

De [RollOffMode](/docs/nl-nl/reference/engine/classes/Sound#RollOffMode)  eigenschap stelt je in staat om te beslissen hoe audio vervaagt naarmate de afstand tussen de luisteraar van de gebruiker en de ouder van het [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object toeneemt. Je kunt deze eigenschap instellen op een van de vier waarden van de [Enum.RollOffMode](/docs/nl-nl/reference/engine/enums/RollOffMode)  enum.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-objects/RollOffMode-Chart.png)

| RollOffMode | | Beschrijving |
| Inverse  (standaard) | | Volume vervaagt aanvankelijk abrupt vanaf [RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance) , maar het volume vervagen wordt geleidelijker naarmate een gebruiker dichter bij de [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  komt. Zodra ze de [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  bereiken, valt de audio stil. |
| Linear | | Volume vervaagt lineair tussen [RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  en [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance) . Zodra een gebruiker de [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  bereikt, valt de audio stil. |
| InverseTapered | | Volume volgt het inverse model wanneer dicht bij [RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  en het lineaire vierkante model wanneer een gebruiker dicht bij [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  is. Audio benadert stilte op het maximale afstandspunt. |
| LinearSquare | | Volume vervaagt tussen [RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  en [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  met een lineair vierkante relatie. Audio benadert stilte op het maximale afstandspunt. |

Voor de meeste Inverse  en Linear  [RollOffMode](/docs/nl-nl/reference/engine/classes/Sound#RollOffMode)  types, veroorzaken lage [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  waarden dat audio abrupt afsnijdt wanneer de luisteraar de [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  bereikt. Als je wilt dat je audio geleidelijk in volume afneemt, stel dan een hogere [RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  waarde in.

### [PlaybackSpeed](#playbackspeed)[](#playbackspeed)

De [PlaybackSpeed](/docs/nl-nl/reference/engine/classes/Sound#PlaybackSpeed)  eigenschap stelt je in staat om de snelheid te bepalen waarmee je audio afspeelt. Bijvoorbeeld, als je de [PlaybackSpeed](/docs/nl-nl/reference/engine/classes/Sound#PlaybackSpeed)  instelt op een waarde van 2 , speelt je audio twee keer zo snel en één octaaf hoger in toonhoogte. Evenzo, als je het instelt op een waarde van 0.5 , speelt je audio twee keer zo langzaam en één octaaf lager in toonhoogte.

|  | |  | |  |
| [PlaybackSpeed](/docs/nl-nl/reference/engine/classes/Sound#PlaybackSpeed)  = 0.5 | | [PlaybackSpeed](/docs/nl-nl/reference/engine/classes/Sound#PlaybackSpeed)  = 1.0 | | [PlaybackSpeed](/docs/nl-nl/reference/engine/classes/Sound#PlaybackSpeed)  = 2.0 |

### [TimePosition](#timeposition)[](#timeposition)

De [TimePosition](/docs/nl-nl/reference/engine/classes/Sound#TimePosition)  eigenschap toont, in seconden, welke positie binnen de audio-sample een gebruiker momenteel hoort. Deze eigenschap is nuttig voor het alleen afspelen van een sectie van de audio-sample, of het triggeren van een gebeurtenis die plaatsvindt zodra de audio een specifieke positie bereikt. Bijvoorbeeld, de volgende code-sample zorgt ervoor dat een deeltjesemitter een witte ringdeeltje boven een onderdeel uitzendt binnen een beperkte tijdsrange van een audiotrack.

```

local RunService = game:GetService("RunService")

local Workspace = game:GetService("Workspace")

-- Maak een nieuw onderdeel

local part = Instance.new("Part")

part.Anchored = true

part.Color = Color3.new(0.75, 0.2, 0.5)

part.Size = Vector3.new(2, 1, 2)

part.Material = Enum.Material.Neon

part.Position = Vector3.new(0, 4, 0)

part.Parent = Workspace

-- Maak een bevestiging op het onderdeel

local attachment = Instance.new("Attachment")

attachment.Position = Vector3.new(0, 0.5, 0)

attachment.Parent = part

-- Maak een deeltjesemitter op de bevestiging

local emitter = Instance.new("ParticleEmitter")

emitter.Rate = 5

emitter.Lifetime = NumberRange.new(1.5, 1.5)

emitter.Texture = "rbxassetid://1266170131"

emitter.Speed = NumberRange.new(1, 1)

emitter.Size = NumberSequence.new{NumberSequenceKeypoint.new(0, 1), NumberSequenceKeypoint.new(1, 6)}

emitter.Transparency = NumberSequence.new{NumberSequenceKeypoint.new(0, 1), NumberSequenceKeypoint.new(0.25, 0), NumberSequenceKeypoint.new(1, 1)}

emitter.Orientation = Enum.ParticleOrientation.VelocityPerpendicular

emitter.Parent = attachment

-- Maak een geluid op de bevestiging

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://1835405646"

sound.Parent = attachment

-- Speel het geluid af

sound:Play()

-- Begin met controleren of de emitter moet worden ingeschakeld

RunService.Heartbeat:Connect(function()

	-- Schakel de emitter in binnen een tijdsrange van de audio; anders schakel het uit

	emitter.Enabled = sound.TimePosition >= 5 and sound.TimePosition < 20

end)

```

### [Looped](#looped)[](#looped)

De [Looped](/docs/nl-nl/reference/engine/classes/Sound#Looped)  eigenschap stelt je in staat om audio te herhalen nadat deze is afgelopen met afspelen. Wanneer ingesteld op true , speelt de audio van het [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object opnieuw af. Dit is nuttig om toe te passen op [achtergrondaudio](#achtergrondaudio)  om ervoor te zorgen dat je spel nooit abrupt stil is.

## [Script geluidsobjecten](#script-geluidsobjecten)[](#script-geluidsobjecten)

### [Audio contextueel afspelen](#audio-contextueel-afspelen)[](#audio-contextueel-afspelen)

Afgezien van het automatisch afspelen van audio via de [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object's [Playing](/docs/nl-nl/reference/engine/classes/Sound#Playing)  eigenschap, kun je audio contextueel afspelen vanuit een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  door [Play()](/docs/nl-nl/reference/engine/classes/Sound#Play)  aan te roepen op het overeenkomstige [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object. Bijvoorbeeld:

```

local Workspace = game:GetService("Workspace")

local sound = Instance.new("Sound")

sound.SoundId = "rbxassetid://9120386436"

sound.Looped = true

sound.Parent = Workspace

sound:Play()

```

Alternatief, als de plaats meerdere nummers zal bevatten, kun je een specifiek nummer afspelen vanuit een clientscript:

```

local SoundService = game:GetService("SoundService")

local musicTrack = SoundService:FindFirstChild("LucidDream")

if musicTrack and not musicTrack.IsPlaying then

	musicTrack:Play()

end

```

### [Interface audio afspelen](#interface-audio-afspelen)[](#interface-audio-afspelen)

Je kunt interface audio afspelen voor [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  zoals [knoppen](/docs/nl-nl/ui/buttons)  door een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object aan te sluiten op de [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  gebeurtenislistener. Dit stelt je in staat om auditieve feedback aan gebruikers te geven, zoals wanneer ze eroverheen bewegen of deze indrukken.

Om de audio van een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object af te spelen wanneer een gebruiker een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  of [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  activeert:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, zweef over de [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  of [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton) , en klik dan op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  of een [Script](/docs/nl-nl/reference/engine/classes/Script)  met [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Enum.RunContext.Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) .

3.

Plak de volgende code in het script, en vervang SOUND_NAME  door de naam van een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object dat zich binnen de [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  container bevindt.

```

local SoundService = game:GetService("SoundService")

local button = script.Parent

local sound = SoundService:FindFirstChild("SOUND_NAME")

if not sound.isLoaded then

	sound.Loaded:Wait()

end

local function onButtonActivated()

	if sound and not sound.IsPlaying then

		sound:Play()

	end

end

button.Activated:Connect(onButtonActivated)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
