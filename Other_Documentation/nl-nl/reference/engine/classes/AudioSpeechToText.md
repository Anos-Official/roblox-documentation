<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioSpeechToText -->

AudioSpeechToText | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioSpeechToText](/docs/nl-nl/reference/engine/classes/AudioSpeechToText)

Nederlands

Feedback

Engine-klasse

AudioSpeechToText

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioSpeechToText)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Text](#Text) :[string](/docs/nl-nl/luau/strings)

 |
|

[VoiceDetected](#VoiceDetected) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Evenementen

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Spraak om tekst converteren

```

local players = game:GetService("Players")

local function connect(src: Instance, dst: Instance)

	local wire = Instance.new("Wire", dst)

	wire.SourceInstance = src

	wire.TargetInstance = dst

end

local textLabel = nil

local stt = nil

local function onCharacterSpawned(player: Player, character: Model)

	local input = Instance.new("AudioDeviceInput", player)

	input.Player = player

	local audioSpeechToText = Instance.new("AudioSpeechToText", character)

	audioSpeechToText.Enabled = true

	connect(player.AudioDeviceInput, audioSpeechToText)

	local screenGui = Instance.new("ScreenGui", player.PlayerGui)

	textLabel = Instance.new("TextLabel", screenGui)

	textLabel.Text = "Hallo!"

	textLabel.Size = UDim2.fromOffset(160,90)

	textLabel.Position = UDim2.fromOffset(20,20)

	textLabel.BackgroundTransparency = 0

	textLabel.FontFace.Weight = Enum.FontWeight.Bold

	textLabel.TextColor3 = Color3.new(1,1,1)

	textLabel.TextStrokeColor3 = Color3.new(0,0,0)

	textLabel.TextStrokeTransparency = 0.5

	audioSpeechToText:GetPropertyChangedSignal("Text"):Connect(function()

		if audioSpeechToText.Text ~= '' then

			print(audioSpeechToText.Text)

			textLabel.Text = audioSpeechToText.Text

			audioSpeechToText.Text = ''

		end

	end)

	stt = audioSpeechToText

end

local function onPlayerAdded(player: Player)

	if player.Character then

		onCharacterSpawned(player, player.Character)

	end

	player.CharacterAdded:Connect(function()

		onCharacterSpawned(player, player.Character)

	end)

end

players.PlayerAdded:Connect(onPlayerAdded)

for _, player in players:GetPlayers() do

	onPlayerAdded(player)

end

local vad = false

while true do

	wait(0.1)

	if stt and textLabel then

		if(stt.VoiceDetected ~= vad) then

			vad = stt.VoiceDetected

			print(vad)

			if(vad) then

				textLabel.BackgroundColor3 = Color3.new(0.7,0,0)

			else

				textLabel.BackgroundColor3 = Color3.new(0,0,0)

			end

		end

	end

end

```

---

API-referentie

Eigenschappen

Enabled

Parallel lezen

Mogelijkheden: Audio

AudioSpeechToText.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Text

Parallel lezen

Mogelijkheden: Audio

AudioSpeechToText.Text :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

VoiceDetected

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioSpeechToText.VoiceDetected :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioSpeechToText:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetInputPins

Mogelijkheden: Audio

AudioSpeechToText:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioSpeechToText:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioSpeechToText.WiringChanged (

connected :[boolean](/docs/nl-nl/luau/booleans) , pin :[string](/docs/nl-nl/luau/strings) , wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/nl-nl/luau/booleans)

 |
|

pin :[string](/docs/nl-nl/luau/strings)

 |
|

wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

Ga naar

▼

AudioSpeechToText

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Enabled](#Enabled)

[Text](#Text)

[VoiceDetected](#VoiceDetected)

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[Evenementen](#events)

[WiringChanged](#WiringChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
