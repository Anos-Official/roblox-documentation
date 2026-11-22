<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Pants -->

Pants | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [CharacterAppearance](/docs/nl-nl/reference/engine/classes/CharacterAppearance)
8. /
9. [Clothing](/docs/nl-nl/reference/engine/classes/Clothing)
10. /
11. [Pants](/docs/nl-nl/reference/engine/classes/Pants)

Nederlands

Feedback

Engine-klasse

Pants

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Pants)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[PantsTemplate](#PantsTemplate) : ContentId

 |
| --- | --- |
|

[PantsTemplateContent](#PantsTemplateContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |

Overgenomen leden

1  overgenomen van [Clothing](/docs/nl-nl/reference/engine/classes/Clothing)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Verander Shirt / Broek

```

local Players = game:GetService("Players")

local function replaceClothes(player)

	local character = player.Character

	if character then

		-- zoek naar shirts / broeken

		local shirt = character:FindFirstChildOfClass("Shirt")

		local pants = character:FindFirstChildOfClass("Pants")

		-- maak shirts / broeken aan als ze niet bestaan

		if not shirt then

			shirt = Instance.new("Shirt")

			shirt.Parent = character

		end

		if not pants then

			pants = Instance.new("Pants")

			pants.Parent = character

		end

		-- reset shirt / broek content ids

		shirt.ShirtTemplate = "http://www.roblox.com/asset/?id=83326831"

		pants.PantsTemplate = "http://www.roblox.com/asset/?id=10045638"

	end

end

for _index, player in ipairs(Players:GetPlayers()) do

	replaceClothes(player)

end

```

---

API-referentie

Eigenschappen

PantsTemplate

Parallel lezen

Mogelijkheden: AvatarAppearance

Pants.PantsTemplate : ContentId

Codevoorbeelden

Verander Shirt / Broek

```

local Players = game:GetService("Players")

local function replaceClothes(player)

	local character = player.Character

	if character then

		-- zoek naar shirts / broeken

		local shirt = character:FindFirstChildOfClass("Shirt")

		local pants = character:FindFirstChildOfClass("Pants")

		-- maak shirts / broeken aan als ze niet bestaan

		if not shirt then

			shirt = Instance.new("Shirt")

			shirt.Parent = character

		end

		if not pants then

			pants = Instance.new("Pants")

			pants.Parent = character

		end

		-- reset shirt / broek content ids

		shirt.ShirtTemplate = "http://www.roblox.com/asset/?id=83326831"

		pants.PantsTemplate = "http://www.roblox.com/asset/?id=10045638"

	end

end

for _index, player in ipairs(Players:GetPlayers()) do

	replaceClothes(player)

end

```

Feedback geven

---

PantsTemplateContent

Parallel lezen

Mogelijkheden: AvatarAppearance

Pants.PantsTemplateContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

Ga naar

▼

Pants

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[PantsTemplate](#PantsTemplate)

[PantsTemplateContent](#PantsTemplateContent)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
