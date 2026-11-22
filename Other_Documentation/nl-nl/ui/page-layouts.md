<!-- Source: https://create.roblox.com/docs/nl-nl/ui/page-layouts -->

Pagina-indelingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. Lay-outstructuren

# Pagina-indelingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je een [UIPageLayout](/docs/nl-nl/reference/engine/classes/UIPageLayout)  aan een UI-container koppelt, wordt elke sibling [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  een unieke pagina waar je via scripting naartoe kunt schakelen. Deze indeling is nuttig wanneer je gebruikersinterfaces wilt maken zoals tabbladenmodals, tutorials of schermen voor karakteraanpassing.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIPageLayout.png)

Nadat je meerdere pagina's binnen de [UIPageLayout](/docs/nl-nl/reference/engine/classes/UIPageLayout)  hebt gemaakt, moet je scripting gebruiken om van pagina naar pagina te schakelen. Bijvoorbeeld, de volgende code, geplakt in een client-side sibling [Script](/docs/nl-nl/reference/engine/classes/Script)  van de indeling, schakelt elke twee seconden vooruit en vervolgens achteruit tussen de pagina's.

```

local frame = script.Parent

local pageLayout = frame:FindFirstChildWhichIsA("UIPageLayout")

task.wait(2)

pageLayout:Next()

task.wait(2)

pageLayout:Next()

task.wait(2)

pageLayout:Previous()

task.wait(2)

pageLayout:Previous()

```

Als je pagina's wilt bekijken terwijl je in Studio aan het bewerken bent, kun je de [Opdrachtbalk](/docs/nl-nl/studio/overview#command-bar)  gebruiken om van de ene pagina naar de andere te navigeren, zodat je kunt bekijken waar je wijzigingen moet aanbrengen zonder telkens je spel te hoeven spelen.

1.

Selecteer het [UIPageLayout](/docs/nl-nl/reference/engine/classes/UIPageLayout)  object in de hiërarchie van het [Explorer](/docs/nl-nl/studio/explorer)  venster.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIPageLayout.png)

2.

Open de [Opdrachtbalk](/docs/nl-nl/studio/overview#command-bar) .

3.

Voer een van de volgende opdrachten in en druk op Enter .

| Actie | | Opdracht |
| --- | --- |
| Volgende Pagina | | game:GetService("Selection"):Get()[1]:Next() |
| Vorige Pagina | | game:GetService("Selection"):Get()[1]:Previous() |
| Eerste Pagina | | game:GetService("Selection"):Get()[1]:JumpToIndex(0) |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
