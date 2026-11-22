<!-- Source: https://create.roblox.com/docs/nl-nl/input/mouse-and-keyboard -->

Muis- en toetsenbordinvoer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Input](/docs/nl-nl/input)

# Muis- en toetsenbordinvoer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een groot percentage van de Roblox-sessies wordt gespeeld op apparaten met een muis en toetsenbord, dus het is belangrijk om deze invoer te ondersteunen bij het ontwerpen van een game voor een breed publiek.

Om [cross-platform](/docs/nl-nl/projects/cross-platform)  invoer, inclusief muis/toetsenbord, te vereenvoudigen, biedt Roblox het [Input Action System](/docs/nl-nl/input/input-action-system)  om acties  zoals "springen", "rennen" of "schieten" te definiëren en bindingen  voor meerdere hardware-invoeren in te stellen om die acties aan te sturen.

Roblox ondersteunt ook algemene muis/toetsenbordinvoer via [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService) -evenementen zoals [InputBegan](/docs/nl-nl/reference/engine/classes/UserInputService#InputBegan)  en [InputEnded](/docs/nl-nl/reference/engine/classes/UserInputService#InputEnded)  en methoden zoals [IsKeyDown()](/docs/nl-nl/reference/engine/classes/UserInputService#IsKeyDown)  om te controleren of een bepaalde toets op een toetsenbord is ingedrukt.

## [Invoertype-detectie](#invoertype-detectie)[](#invoertype-detectie)

Bij cross-platform ontwikkeling is het belangrijk dat je het [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  type bepaalt en hierop reageert dat een speler gebruikt, normaal gesproken om ervoor te zorgen dat [UI elementen](/docs/nl-nl/ui#ui-objecten)  zoals knoppen en menu's op het scherm elegant werken en interactie tussen apparaten ondersteunen.

Bijvoorbeeld, een pc of laptop gaat ervan uit dat muis/toetsenbord de standaardinvoer is, maar een speler kan ervoor kiezen om een bluetooth-gamepad aan te sluiten. In dit geval blijft muis/toetsenbord een geldige invoer, maar je kunt aannemen dat de speler wil overschakelen naar de aangesloten gamepad als het primaire  invoertype.

Zie [invoertype-detectie](/docs/nl-nl/input#invoertype-detectie)  voor meer informatie.

## [Algemene muis/toetsinvoer](#algemene-muistoetsinvoer)[](#algemene-muistoetsinvoer)

Naast het [Input Action System](/docs/nl-nl/input/input-action-system)  kun je muis- en toetsenbordinvoer vastleggen met [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService) . De volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , wanneer geplaatst in [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) , legt de begonnen en beëindigde fasen van toets- en muisklikken vast en print het resultaat naar het [Output](/docs/nl-nl/studio/output)  venster.

LocalScript - Output Toets/Muis Begon en Eindigde

```

local UserInputService = game:GetService("UserInputService")

local function onInputBegan(inputObject, processedEvent)

	-- Retourneer als een ander script de invoer al heeft verwerkt

	if processedEvent then return end

	print(inputObject.KeyCode.Name, "begon!", inputObject.Position)

end

local function onInputEnded(inputObject, processedEvent)

	-- Retourneer als een ander script de invoer al heeft verwerkt

	if processedEvent then return end

	print(inputObject.KeyCode.Name, "eindigde!", inputObject.Position)

end

UserInputService.InputBegan:Connect(onInputBegan)

UserInputService.InputEnded:Connect(onInputEnded)

```

## [Muispictogram](#muispictogram)[](#muispictogram)

Je kunt het uiterlijk en gedrag van het muispictogram van een speler binnen je game aanpassen om een samenhangende stijl te creëren over al je UI-elementen. Dit omvat het tijdelijk veranderen van het muispictogram van de speler in specifieke omstandigheden, zoals wanneer je over een knop zweeft.

Pictogram Wijzigen Pictogram Verbergen Pictogram Vergrendelen

Je kunt het muispictogram van de speler in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  wijzigen door de [MouseIcon](/docs/nl-nl/reference/engine/classes/UserInputService#MouseIcon)  eigenschap in [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService)  in te stellen op een aangepaste Roblox asset ID. Bijvoorbeeld, de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  verandert het standaard muispictogram van de speler in een cirkel met een blauwe stip in het midden.

```

local UserInputService = game:GetService("UserInputService")

UserInputService.MouseIcon = "rbxassetid://3400146391"

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
