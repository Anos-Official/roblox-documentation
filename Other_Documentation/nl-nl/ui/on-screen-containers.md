<!-- Source: https://create.roblox.com/docs/nl-nl/ui/on-screen-containers -->

Scherm UI-containers | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# Scherm UI-containers

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container houdt [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  vast om weer te geven op het scherm van een speler, inclusief [frames](/docs/nl-nl/ui/frames) , [labels](/docs/nl-nl/ui/labels) , [knoppen](/docs/nl-nl/ui/buttons)  en meer. Alle UI-objecten op het scherm en de code worden opgeslagen en gewijzigd op de client.

![Voorbeeld van ScreenGui met verschillende GuiObject-kinderen, waaronder een Frame, TextLabel, TextBox en ImageButton.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGui-Example.jpg)

Voor UI-containers die [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  bevatten die je binnen  de 3D-wereld wilt weergeven, zoals op het oppervlak van een onderdeel, zie [In-game UI Containers](/docs/nl-nl/ui/in-experience-containers) .

Om een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en zijn kind [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  weer te geven aan elke speler die het spel betreedt, plaats je het binnen de [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  container. Wanneer een speler een spel betreedt en hun karakter voor het eerst verschijnt, worden de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en de inhoud ervan gekloond naar de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  container voor die speler, die zich binnen de [Players](/docs/nl-nl/reference/engine/classes/Players)  container bevindt.

 ![Diagram van hoe een ScreenGui kloont van StarterGui naar de PlayerGui van een speler](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/StarterGui-To-PlayerGui.png)

Standaard verschijnen [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  binnen [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  als een overlay van de [3D viewport](/docs/nl-nl/studio/overview#3d-viewport) , wat hun uiterlijk en positie in een draaiend spel simuleert. Om alle dergelijke schermoverlays te verbergen, schakel je GUI overlay  uit in de [Visualisatie opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van de 3D-viewport.

Als [Players.CharacterAutoLoads](/docs/nl-nl/reference/engine/classes/Players#CharacterAutoLoads)  is uitgeschakeld, worden de inhoud van [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  niet gekloond totdat [Player:LoadCharacterAsync()](/docs/nl-nl/reference/engine/classes/Player#LoadCharacterAsync)  wordt aangeroepen.

Naarmate een spel in omvang toeneemt, heb je mogelijk meerdere scherminterfaces nodig, zoals een titel scherm, instellingenmenu, winkelinterface en meer. In dergelijke gevallen kun je meerdere unieke [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  containers binnen [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  plaatsen en de [Enabled](/docs/nl-nl/reference/engine/classes/ScreenGui#Enabled)  eigenschap van elke container in- of uitschakelen, afhankelijk van of deze zichtbaar en actief moet zijn (terwijl false , worden de inhoud niet weergegeven, verwerkt gebruikersinvoer of bijgewerkt in reactie op wijzigingen).

 ![Explorer-hiërarchie die meerdere ScreenGui-containers toont, waarvan er één is ingeschakeld en de anderen zijn uitgeschakeld, om te controleren welke op een bepaald moment zichtbaar zijn.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGuis-Enabled.png)

De [Enabled](/docs/nl-nl/reference/engine/classes/ScreenGui#Enabled)  eigenschap kan aanvankelijk worden in- of uitgeschakeld via het [Eigenschappen](/docs/nl-nl/studio/properties)  venster en/of je kunt het tijdens de speeltijd instellen vanuit een client-side script door de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  van de speler te [benaderen](#toegang-tot-speler-ui)  en het in te stellen op true  of false  voor de gewenste container(s).

Bij het gebruik van meerdere [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  interfaces, kun je ze stapelen op basis van Z-index via hun [DisplayOrder](/docs/nl-nl/reference/engine/classes/ScreenGui#DisplayOrder)  eigenschap. Zie [Weergavevolgorde](#weergavevolgorde)  voor meer informatie.

## [Container eigenschappen](#container-eigenschappen)[](#container-eigenschappen)

De volgende eigenschappen stellen je in staat om de [scherminzetten](#scherminzetten)  over meerdere apparaten, de [weergavevolgorde](#weergavevolgorde)  bij het gebruik van meerdere schermcontainers en meer aan te passen.

### [Scherminzetten](#scherminzetten)[](#scherminzetten)

Moderne telefoons maken gebruik van het volledige scherm, maar bevatten doorgaans inkepingen, uitsparingen en andere elementen die schermruimte innemen. Elke Roblox-game bevat ook de bovenbalkbedieningselementen  voor snelle toegang tot het hoofdmenu, [chat](/docs/nl-nl/chat/in-experience-text-chat) , [leaderboard](/docs/nl-nl/players/leaderboards)  en meer.

 ![Mobiel apparaat dat de Roblox bovenbalkknoppen en de uitsparing van het apparaat toont.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/Top-Bar-Cutout.png)

Om ervoor te zorgen dat spelers alle UI gemakkelijk kunnen zien en benaderen zonder obstructie, biedt Roblox de [ScreenInsets](/docs/nl-nl/reference/engine/classes/ScreenGui#ScreenInsets)  eigenschap die de veilige gebied  insets voor de inhoud van een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  beheert.

CoreUISafeInsets DeviceSafeInsets TopbarSafeInsets None

De standaardinstelling van [CoreUISafeInsets](/docs/nl-nl/reference/engine/enums/ScreenInsets)  houdt alle afgeleide [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  binnen het veilige gebied van de kern UI, vrij van de bovenbalkknoppen en andere schermuitsparingen. Deze instelling wordt aanbevolen als de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  interactieve UI-elementen bevat.

![Mobiel apparaat dat het veilige gebied van de kern UI toont.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/CoreUISafeInsets.png)

### [Weergavevolgorde](#weergavevolgorde)[](#weergavevolgorde)

Bij het gebruik van meerdere [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  interfaces, kun je ze stapelen op basis van Z-index via hun [DisplayOrder](/docs/nl-nl/reference/engine/classes/ScreenGui#DisplayOrder)  eigenschap. Bijvoorbeeld, om een modaal instellingenmenu op één [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  voor de hoofdgebruikersinterface van het spel op een andere [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  weer te geven, wijs je een hogere [DisplayOrder](/docs/nl-nl/reference/engine/classes/ScreenGui#DisplayOrder)  toe aan het modale dan aan de onderliggende interface.

### [Reset bij spawnen](#reset-bij-spawnen)[](#reset-bij-spawnen)

De [ResetOnSpawn](/docs/nl-nl/reference/engine/classes/ScreenGui#ResetOnSpawn)  boolean eigenschap bepaalt of de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  reset (verwijdert zichzelf en kloont opnieuw naar de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  van de speler) elke keer dat het karakter van de speler opnieuw spawnt.

| Voorwaarde | | Reset |
| --- | --- |
| [ResetOnSpawn](/docs/nl-nl/reference/engine/classes/ScreenGui#ResetOnSpawn)  is true  (standaard). | |

JA

 |
| De [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  is een indirecte  afstammeling van [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) ; bijvoorbeeld, het is geplaatst binnen een [Folder](/docs/nl-nl/reference/engine/classes/Folder)  die zich binnen [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  bevindt. | |

JA

 |
| [ResetOnSpawn](/docs/nl-nl/reference/engine/classes/ScreenGui#ResetOnSpawn)  is false  en  de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  is een directe  afstammeling van [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) . | |

NEE

 |

## [Toegang tot speler UI](#toegang-tot-speler-ui)[](#toegang-tot-speler-ui)

Zoals opgemerkt, kloont het ouderschap van een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  naar [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  het en zijn kind [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  naar de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  container van een speler wanneer ze het spel betreden en hun karakter voor het eerst verschijnt.

Als je de UI-container van een speler tijdens de speeltijd wilt bedienen, bijvoorbeeld om een specifieke [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  of een van zijn kinderen te tonen/verbergen, benader je het als volgt vanuit een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) :

LocalScript - Toegang tot de UI van een Speler

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local titleScreen = playerGui:WaitForChild("TitleScreen")

local settingsMenu = playerGui:WaitForChild("SettingsMenu")

titleScreen.Enabled = false  -- Verberg titel scherm

settingsMenu.Enabled = true  -- Toon instellingenmenu

```

## [Standaard UI uitschakelen](#standaard-ui-uitschakelen)[](#standaard-ui-uitschakelen)

Alle Roblox-spellen bevatten verschillende UI-elementen die standaard zijn ingeschakeld. Als je een van deze elementen niet nodig hebt of als je ze wilt vervangen door je eigen creaties, kun je de [SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled) -methode gebruiken in een client-side script met de bijbehorende [Enum.CoreGuiType](/docs/nl-nl/reference/engine/enums/CoreGuiType) -optie.

| Standaard UI | | Bijbehorende enum |
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
