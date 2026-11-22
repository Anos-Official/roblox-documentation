<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TextChannelWindow -->

TextChannelWindow | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/nl-nl/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)
10. /
11. [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)
12. /
13. [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)

Nederlands

Feedback

Engine-klasse

TextChannelWindow

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TextChannelWindow)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Target](#Target) :[TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)

 |
| --- | --- |
|

[FontFace](#FontFace) :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

 |
|

[UseDefaultFont](#UseDefaultFont) :[boolean](/docs/nl-nl/luau/booleans)

 |

Overgenomen leden

51  overgenomen van [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)

12  overgenomen van [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Target

Parallel lezen

Mogelijkheden: UI, Chat

TextChannelWindow.Target :[TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)

Feedback geven

---

FontFace

Parallel lezen

Mogelijkheden: UI, Chat

TextChannelWindow.FontFace :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

Codevoorbeelden

Aangepaste TextChannelWindow Lettertype

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = Players.LocalPlayer:WaitForChild("PlayerGui")

local window = Instance.new("TextChannelWindow")

window.Size = UDim2.fromOffset(400, 300)

window.Target = TextChatService:WaitForChild("TextChannels"):WaitForChild("RBXGeneral")

-- FontFace wordt alleen toegepast wanneer UseDefaultFont false is

window.UseDefaultFont = false

window.FontFace = Font.fromName("FredokaOne")

window.Parent = screenGui

```

Feedback geven

---

UseDefaultFont

Parallel lezen

Mogelijkheden: UI, Chat

TextChannelWindow.UseDefaultFont :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Aangepaste TextChannelWindow Lettertype

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = Players.LocalPlayer:WaitForChild("PlayerGui")

local window = Instance.new("TextChannelWindow")

window.Size = UDim2.fromOffset(400, 300)

window.Target = TextChatService:WaitForChild("TextChannels"):WaitForChild("RBXGeneral")

-- FontFace wordt alleen toegepast wanneer UseDefaultFont false is

window.UseDefaultFont = false

window.FontFace = Font.fromName("FredokaOne")

window.Parent = screenGui

```

Feedback geven

---

Ga naar

▼

TextChannelWindow

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Target](#Target)

[FontFace](#FontFace)

[UseDefaultFont](#UseDefaultFont)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
