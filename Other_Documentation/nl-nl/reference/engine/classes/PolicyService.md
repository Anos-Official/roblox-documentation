<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PolicyService -->

PolicyService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PolicyService](/docs/nl-nl/reference/engine/classes/PolicyService)

Nederlands

Feedback

Engine-klasse

PolicyService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PolicyService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CanViewBrandProjectAsync](#CanViewBrandProjectAsync) (player :  [Player](/docs/nl-nl/reference/engine/classes/Player) , brandProjectId :  [string](/docs/nl-nl/luau/strings) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[GetPolicyInfoForPlayerAsync](#GetPolicyInfoForPlayerAsync) (player :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

CanViewBrandProjectAsync

Opbrengst

Mogelijkheden: Basic

PolicyService:CanViewBrandProjectAsync (

player :[Player](/docs/nl-nl/reference/engine/classes/Player) , brandProjectId :[string](/docs/nl-nl/luau/strings)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

player :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |
|

brandProjectId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Server-side code voorbeeld

```

-- In ServerScriptService

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local PolicyService = game:GetService("PolicyService")

-- Vooraf gemaakte RemoteEvent in ReplicatedStorage

local RemoteEvent = ReplicatedStorage:WaitForChild("RemoteEvent")

local brandedAsset = ReplicatedStorage:WaitForChild("BrandedAsset")

local defaultAsset = Instance.new("Part")

Players.PlayerAdded:Connect(function(player)

	-- PolicyService:CanViewBrandProjectAsync kan alleen vanaf de Server worden aangeroepen

	local success, canView = pcall(function()

		return PolicyService:CanViewBrandProjectAsync(player, "BRP-0123456789")

	end)

	if success and canView then

		RemoteEvent:FireClient(player, brandedAsset)

	else

		RemoteEvent:FireClient(player, defaultAsset)

	end

end)

```

Voorbeeld van client-side code

```

-- In StarterPlayerScripts

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Vooraf gemaakte RemoteEvent in ReplicatedStorage

local RemoteEvent = ReplicatedStorage:WaitForChild("RemoteEvent")

RemoteEvent.OnClientEvent:Connect(function(partToLoad)

	local clonedPart = partToLoad:Clone()

	clonedPart.Parent = workspace

end)

```

Feedback geven

---

GetPolicyInfoForPlayerAsync

Opbrengst

Mogelijkheden: Basic

PolicyService:GetPolicyInfoForPlayerAsync (player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Beleid Informatie Verkrijgen voor een Speler

```

local PolicyService = game:GetService("PolicyService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local success, result = pcall(function()

	return PolicyService:GetPolicyInfoForPlayerAsync(player)

end)

if not success then

	warn("PolicyService fout: " .. result)

elseif result.ArePaidRandomItemsRestricted then

	warn("Speler kan niet interageren met betaalde willekeurige itemgeneratoren")

end

```

Beleidsinformatie voor een Speler Opvragen

```

local PolicyService = game:GetService("PolicyService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local success, result = pcall(function()

	return PolicyService:GetPolicyInfoForPlayerAsync(player)

end)

if not success then

	warn("PolicyService fout: " .. result)

elseif not result.IsEligibleToPurchaseCommerceProduct then

	warn("Speler is niet in aanmerking om commerciële producten te kopen")

end

```

Feedback geven

---

Ga naar

▼

PolicyService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[CanViewBrandProjectAsync()](#CanViewBrandProjectAsync)

[GetPolicyInfoForPlayerAsync()](#GetPolicyInfoForPlayerAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
