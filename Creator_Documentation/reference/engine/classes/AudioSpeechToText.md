<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioSpeechToText -->

AudioSpeechToText | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioSpeechToText.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioSpeechToText](/docs/en-us/reference/engine/classes/AudioSpeechToText)

English

Feedback

Engine Class

AudioSpeechToText

---

## Summary

Properties

|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[Text](#Text) :[string](/docs/en-us/luau/strings)

 |
|

[VoiceDetected](#VoiceDetected) :[boolean](/docs/en-us/luau/booleans)

 |

Methods

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Convert speech to text

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

	textLabel.Text = "Hello!"

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

API Reference

Properties

Enabled

Read Parallel

Capabilities: Audio

AudioSpeechToText.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Text

Read Parallel

Capabilities: Audio

AudioSpeechToText.Text :[string](/docs/en-us/luau/strings)

Provide feedback

---

VoiceDetected

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioSpeechToText.VoiceDetected :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioSpeechToText:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/en-us/luau/strings)

 |

Returns

{[Wire](/docs/en-us/reference/engine/classes/Wire) }

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioSpeechToText:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioSpeechToText:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioSpeechToText.WiringChanged (

connected :[boolean](/docs/en-us/luau/booleans) , pin :[string](/docs/en-us/luau/strings) , wire :[Wire](/docs/en-us/reference/engine/classes/Wire) , instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/en-us/luau/booleans)

 |
|

pin :[string](/docs/en-us/luau/strings)

 |
|

wire :[Wire](/docs/en-us/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

AudioSpeechToText

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Enabled](#Enabled)

[Text](#Text)

[VoiceDetected](#VoiceDetected)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[Events](#events)

[WiringChanged](#WiringChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
