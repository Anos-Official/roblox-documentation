<!-- Source: https://create.roblox.com/docs/nl-nl/input -->

Invoer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Input](/docs/nl-nl/input)

# Invoer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Elke game moet gebruikersinvoer ontvangen zodat spelers kunnen interageren en hun omgeving kunnen bekijken. Roblox ondersteunt bijna alle vormen van invoer, waaronder [muisklik/toetsenbord](/docs/nl-nl/input/mouse-and-keyboard) , [aanraking](/docs/nl-nl/input/mobile) , [gamepads](/docs/nl-nl/input/gamepad)  en VR.

## [Cross-platform invoer](#cross-platform-invoer)[](#cross-platform-invoer)

Roblox is van nature [cross‑platform](/docs/nl-nl/projects/cross-platform) , omdat spelers games kunnen ontdekken en zich kunnen aansluiten op hun telefoon of tablet, en later kunnen doorgaan waar ze waren gebleven op hun pc of console. Invoer is vooral belangrijk als onderdeel van je cross‑platform ontwikkelingsplan.

Om dit proces te vereenvoudigen, biedt Roblox het [Input Action System](/docs/nl-nl/input/input-action-system)  om acties  zoals "springen", "rennen" of "schieten" te definiëren en bindingen  voor meerdere hardware-invoeren in te stellen om die acties aan te sturen. Dit bevrijdt je van het nadenken over alle technische aspecten van hardware-invoeren en stelt je in staat om eenvoudig te definiëren welke invoeren welke acties uitvoeren.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Input-Actions-Jump.png)

## [Invoertype detectie](#invoertype-detectie)[](#invoertype-detectie)

In cross‑platform ontwikkeling is het belangrijk dat je het primaire  invoertype bepaalt en hierop reageert dat een speler gebruikt, normaal gesproken om ervoor te zorgen dat [UI-elementen](/docs/nl-nl/ui#ui-objecten)  zoals knoppen en menu's op het scherm elegant werken op verschillende apparaten.

Bijvoorbeeld, een apparaat met aanraakfunctionaliteit gaat ervan uit dat aanraking de standaardinvoer is en dat aanraakknoppen kunnen verschijnen voor acties, maar als een speler een extra bluetooth toetsenbord/muis of gamepad aansluit, kun je aannemen dat ze willen overschakelen naar dat als het primaire  invoertype en mogelijk aanraking als een back-upinvoer voor de UI op het scherm willen gebruiken. De alleen-lezen [UserInputService.PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  eigenschap is een handige manier om te testen op en aan te passen aan meerdere invoertypes op verschillende apparaattype, gebaseerd op verwacht spelersgedrag.

Gedrag Voordelen

De waarde van [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  verandert op basis van ingebouwde apparaatinvoeren en de meest recente interactie van de speler met een aangesloten gamepad of toetsenbord/muis. Voorbeelden zijn:

| Reële Scenario | | PreferredInput |
| --- | --- |
| Speler gebruikt een telefoon zonder andere aangesloten invoerapparaten; geen mogelijkheid tot verandering van invoertype. | | [Touch](/docs/nl-nl/reference/engine/enums/PreferredInput) |
| Speler gebruikt een mobiel apparaat met een bluetooth toetsenbord & muis aangesloten, maar geen gamepad is aangesloten. | | [KeyboardAndMouse](/docs/nl-nl/reference/engine/enums/PreferredInput) |
| Speler gebruikt een tablet met een bluetooth gamepad aangesloten, maar geen toetsenbord of muis is aangesloten. | | [Gamepad](/docs/nl-nl/reference/engine/enums/PreferredInput) |
| Speler is op een Xbox of PlayStation met een bluetooth toetsenbord & muis aangesloten en heeft het laatst interactie gehad met het toetsenbord of de muis. | | [KeyboardAndMouse](/docs/nl-nl/reference/engine/enums/PreferredInput) |
| Speler is op een Windows of Mac PC met een gamepad aangesloten en heeft het laatst interactie gehad met de gamepad. | | [Gamepad](/docs/nl-nl/reference/engine/enums/PreferredInput) |

De volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  is een sjabloon voor het aanvankelijk detecteren van de voorkeurinvoer en reageren op veranderingen tijdens het spel.

Detectie van voorkeurinvoer

```

local UserInputService = game:GetService("UserInputService")

local function preferredInputChanged()

	local preferredInput = UserInputService.PreferredInput

	if preferredInput == Enum.PreferredInput.Touch then

		-- Speler is op een apparaat met aanraakfunctionaliteit zonder andere invoertypes beschikbaar/aangesloten

		print("Aanraking")

	elseif preferredInput == Enum.PreferredInput.Gamepad then

		-- Speler heeft een gamepad aangesloten of heeft het laatst interactie gehad met een gamepad

		print("Gamepad")

	elseif preferredInput == Enum.PreferredInput.KeyboardAndMouse then

		-- Speler heeft een toetsenbord of muis aangesloten of heeft het laatst interactie gehad met een toetsenbord of muis

		print("Toetsenbord en Muis")

	end

end

preferredInputChanged()

UserInputService:GetPropertyChangedSignal("PreferredInput"):Connect(function()

	preferredInputChanged()

end)

```

## [Standaard bindingen](#standaard-bindingen)[](#standaard-bindingen)

Roblox biedt standaard invoerbindingen voor beweging, camerabesturing en basisinteractie met de omgeving — Roblox-spelers zijn vertrouwd met deze bedieningselementen, dus je zou ze alleen in specifieke gevallen moeten overschrijven. Houd er ook rekening mee dat de gereserveerde  invoer niet kan worden overschreven en altijd zal functioneren met hun bedoelde doel.

Roblox Gereserveerd Personage Interface / Inventaris Camera

| Actie | | Muis/Toetsenbord | | Gamepad | | Aanraken |
| Open Roblox-menu | | Esc | | Start  knop ([ButtonStart](/docs/nl-nl/reference/engine/enums/KeyCode) ) | | N.v.t. |
| [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console) | | F9 | | N.v.t. | | N.v.t. |
| Volledig scherm modus (Windows)
Toon bureaublad (Mac) | | F11 | | N.v.t. | | N.v.t. |
| Video opnemen (Windows) | | F12 | | N.v.t. | | N.v.t. |
| Screenshot maken | | PrintScreen | | N.v.t. | | N.v.t. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
