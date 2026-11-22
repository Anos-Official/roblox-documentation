<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/KeyframeMarker -->

KeyframeMarker | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [KeyframeMarker](/docs/nl-nl/reference/engine/classes/KeyframeMarker)

Nederlands

Feedback

Engine-klasse

KeyframeMarker

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/KeyframeMarker)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Value](#Value) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Krijg Keyframe Markers Bevestigd aan een Keyframe

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker1 = Instance.new("KeyframeMarker")

marker1.Name = "FootStep"

marker1.Value = 100

local marker2 = Instance.new("KeyframeMarker")

marker2.Name = "Wave"

marker2.Value = 100

keyframe:AddMarker(marker1) --marker.Parent = keyframe

keyframe:AddMarker(marker2) --marker.Parent = keyframe

local markers = keyframe:GetMarkers()

for _, marker in pairs(markers) do

	print(marker.Name)

end

```

Luisteren naar Keyframe Markers

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.Character:Wait()

local humanoid = character:WaitForChild("Humanoid")

-- Maak een nieuwe "Animation" instantie aan

local kickAnimation = Instance.new("Animation")

-- Stel de "AnimationId" in op de bijbehorende animatie asset ID

kickAnimation.AnimationId = "rbxassetid://2515090838"

-- Laad animatie op de humanoïde

local kickAnimationTrack = humanoid:LoadAnimation(kickAnimation)

-- Speel animatie track af

kickAnimationTrack:Play()

-- Als er een benoemde gebeurtenis was gedefinieerd voor de animatie, verbind deze met "GetMarkerReachedSignal()"

kickAnimationTrack:GetMarkerReachedSignal("KickEnd"):Connect(function(paramString)

	print(paramString)

end)

```

---

API-referentie

Eigenschappen

Value

Parallel lezen

Mogelijkheden: Animation

KeyframeMarker.Value :[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Krijg Keyframe Markers Bevestigd aan een Keyframe

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker1 = Instance.new("KeyframeMarker")

marker1.Name = "FootStep"

marker1.Value = 100

local marker2 = Instance.new("KeyframeMarker")

marker2.Name = "Wave"

marker2.Value = 100

keyframe:AddMarker(marker1) --marker.Parent = keyframe

keyframe:AddMarker(marker2) --marker.Parent = keyframe

local markers = keyframe:GetMarkers()

for _, marker in pairs(markers) do

	print(marker.Name)

end

```

Marker Toevoegen/Marker Verwijderen

```

local keyframe = Instance.new("Keyframe")

keyframe.Parent = workspace

local marker = Instance.new("KeyframeMarker")

marker.Name = "FootStep"

marker.Value = 100

keyframe:AddMarker(marker) --marker.Parent = keyframe

task.wait(2)

keyframe:RemoveMarker(marker) --marker.Parent = nil

```

Feedback geven

---

Ga naar

▼

KeyframeMarker

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Value](#Value)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
