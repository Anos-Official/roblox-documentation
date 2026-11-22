<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PluginMouse -->

PluginMouse | Documentatie - Roblox Creator Hub

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
9. [PluginMouse](/docs/nl-nl/reference/engine/classes/PluginMouse)

Nederlands

Feedback

Engine-klasse

PluginMouse

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PluginMouse)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Evenementen

|

[DragEnter](#DragEnter) (instances :  Instances ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
| --- | --- |

Overgenomen leden

25  overgenomen van [Mouse](/docs/nl-nl/reference/engine/classes/Mouse)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

PluginMouse Verkrijgen

```

plugin:Activate(false) -- verkrijg niet-exclusieve toegang tot de muis

local mouse = plugin:GetMouse()

local function button1Down()

	print("Linker muisklik")

end

mouse.Button1Down:Connect(button1Down)

```

---

API-referentie

Evenementen

DragEnter

Plugin-beveiliging

Mogelijkheden: Input

PluginMouse.DragEnter (instances : Instances ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

instances : Instances

 |

Feedback geven

---

Ga naar

▼

PluginMouse

[Samenvatting](#summary)

[Evenementen](#summary-events)

[Evenementen](#events)

[DragEnter](#DragEnter)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
