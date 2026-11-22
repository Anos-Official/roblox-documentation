<!-- Source: https://create.roblox.com/docs/nl-nl/players/disable-ui -->

Standaard UI uitschakelen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)
6. /
7. UI voor spelers

# Standaard UI uitschakelen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Alle Roblox-spellen bevatten verschillende UI-elementen die standaard zijn ingeschakeld. Als je een van deze elementen niet nodig hebt of als je ze wilt vervangen door je eigen creaties, kun je de [SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled) -methode gebruiken in een client-side script met de bijbehorende [Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType) -optie.

| Standaard UI | | Bijbehorende enum |
| --- | --- |
| Dynamisch bijgewerkte [Players](/docs/nl-nl/reference/engine/classes/Players) -lijst, vaak gebruikt als een [leaderboard](/docs/nl-nl/players/leaderboards) . | | [Enum.CoreGuiType.PlayerList](/docs/nl-nl/reference/engine/enums/CoreGuiType#PlayerList) |
| De [Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health) -balk van het personage. Verschijnt niet als de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  van het personage op volle gezondheid is. | | [Enum.CoreGuiType.Health](/docs/nl-nl/reference/engine/enums/CoreGuiType#Health) |
| De [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  van het personage die [in-game tools](/docs/nl-nl/players/tools)  bevat. Verschijnt niet als er geen [Tools](/docs/nl-nl/reference/engine/classes/Tool)  in de rugzak zijn. | | [Enum.CoreGuiType.Backpack](/docs/nl-nl/reference/engine/enums/CoreGuiType#Backpack) |
| Het [tekstchat](/docs/nl-nl/chat/in-experience-text-chat)  venster. | | [Enum.CoreGuiType.Chat](/docs/nl-nl/reference/engine/enums/CoreGuiType#Chat) |
| Pop-upmenu van karakter [emotes](/docs/nl-nl/characters/emotes) . | | [Enum.CoreGuiType.EmotesMenu](/docs/nl-nl/reference/engine/enums/CoreGuiType#EmotesMenu) |
| Een venster dat het perspectief of het uitzicht van een speler op hun eigen personage weergeeft. Verschijnt niet tenzij de speler Zelf Weergave  heeft ingeschakeld vanuit het Roblox-menu. | | [Enum.CoreGuiType.SelfView](/docs/nl-nl/reference/engine/enums/CoreGuiType#SelfView) |
| Een screenshot maken -knop aan de rechterkant van het scherm. Verschijnt niet tenzij de speler Captures  heeft ingeschakeld vanuit het Roblox-menu. | | [Enum.CoreGuiType.Captures](/docs/nl-nl/reference/engine/enums/CoreGuiType#Captures) |
| De Avatar Switcher  stelt gebruikers in staat om hun platformavatar te wijzigen. | | [Enum.CoreGuiType.AvatarSwitcher](/docs/nl-nl/reference/engine/enums/CoreGuiType#AvatarSwitcher) |

 ![Kern UI-elementen in elk Roblox-spel.](https://prod.docsiteassets.roblox.com/assets/ui/misc/CoreGui-Elements.jpg)

Client Script - Standaard UI-elementen uitschakelen

```

local StarterGui = game:GetService("StarterGui")

-- Standaard gezondheidsbalk en rugzak uitschakelen

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Backpack, false)

```

Bovendien bevatten apparaten met aanraakmogelijkheden standaard een virtuele thumbstick en een springknop. Indien gewenst, kun je deze elementen verbergen door [GuiService.TouchControlsEnabled](/docs/nl-nl/reference/engine/classes/GuiService#TouchControlsEnabled)  op false  in te stellen in een client-side script.

 ![UI-elementen voor aanraakgevoelige apparaten in elk Roblox-spel.](https://prod.docsiteassets.roblox.com/assets/ui/misc/TouchGui-Elements.png)

Client Script - Uitschakelen van aanraakbediening

```

local GuiService = game:GetService("GuiService")

GuiService.TouchControlsEnabled = false

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
