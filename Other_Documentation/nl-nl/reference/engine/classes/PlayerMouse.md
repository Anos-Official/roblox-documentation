<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PlayerMouse -->

PlayerMouse | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Mouse](/docs/nl-nl/reference/engine/classes/Mouse)
8. /
9. [PlayerMouse](/docs/nl-nl/reference/engine/classes/PlayerMouse)

Nederlands

Feedback

Engine-klasse

PlayerMouse

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PlayerMouse)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Overgenomen leden

25  overgenomen van [Mouse](/docs/nl-nl/reference/engine/classes/Mouse)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

PlayerMouse

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local mouse = player:GetMouse()

local function onMouseMove()

	print("muisklik positie op het scherm: ", mouse.X, mouse.Y)

end

mouse.Move:Connect(onMouseMove)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
