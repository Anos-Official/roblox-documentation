<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Backpack -->

Backpack | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)

Nederlands

Feedback

Engine-klasse

Backpack

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Backpack)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Rugzak Geef Gereedschap

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

	local player = Players:GetPlayerFromCharacter(character)

	local tool = Instance.new("Tool")

	local backpack = player:FindFirstChildOfClass("Backpack")

	tool.Parent = backpack

end

local function onPlayerAdded(player)

	if player.Character then

		onCharacterAdded(player.Character)

	end

	player.CharacterAdded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Rugzak Overzicht

```

local Players = game:GetService("Players")

-- Toegang tot Rugzak vanuit een server script

local backpack = Players.PlayerName.Backpack

-- Toegang tot Rugzak vanuit een client script

local backpack = Players.LocalPlayer.Backpack

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
