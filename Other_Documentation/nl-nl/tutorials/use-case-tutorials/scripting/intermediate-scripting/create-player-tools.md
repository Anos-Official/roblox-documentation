<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-player-tools -->

Maak spelerstools | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Scripting
6. /
7. Spel voor gemiddeld niveau

# Maak spelerstools

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Tools zijn een eenvoudige manier om items te beheren die de speler in zijn hand kan houden en in het spel kan gebruiken. Ze kunnen variëren van wapens zoals zwaarden tot voedselitems.

In deze tutorial leer je hoe je een tool in de vorm van een laserblaster kunt maken die geluidseffecten afspeelt wanneer deze wordt uitgerust of geactiveerd.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/title-image.jpg)

## [Maak de tool](#maak-de-tool)[](#maak-de-tool)

Het [Tool](/docs/nl-nl/reference/engine/classes/Tool)  object is de basis van elke tool in Roblox, dus je moet er een maken. Het is gemakkelijker om te veranderen hoe tools eruitzien door objecten zoals Parts en MeshParts aan de tool in de workspace toe te voegen, waar ze zichtbaar zijn.

1.

Voeg een Tool  toe aan de workspace en noem het Blaster .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-blaster.png)

2.

Voeg een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  toe aan de tool.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-MeshPart.png)

3.

Stel de MeshId  eigenschap in op rbxassetid://92656610 .

4.

Stel de TextureId  eigenschap in op rbxassetid://92658105 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/properties-MeshPart.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-mesh.jpg)

5.

De tool heeft een onderdeel genaamd Handle  nodig voor de speler om vast te houden. Verander de naam van de MeshPart in Handle .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-handle.png)

Als je geen onderdeel met de naam ** Handle**  in de tool opneemt, zal het op de grond vallen wanneer een speler probeert het uit te rusten.

## [Bewaar de tool](#bewaar-de-tool)[](#bewaar-de-tool)

Tools kunnen in de 3D-wereld worden bewaard als verzamelbare tools  of aan alle spelers worden gegeven als starter tools .

### [Verzamelbare tool](#verzamelbare-tool)[](#verzamelbare-tool)

De blaster is momenteel een kind van Workspace , dus het zal verzamelbaar zijn. Een speler kan de tool oppakken door deze aan te raken, waardoor het een kind van het karaktermodel wordt; de tool zal dan worden uitgerust en in hun hotbar worden geplaatst.

Tijdens het spel worden niet-uitgeruste tools opgeslagen binnen de hiërarchie van de speler in de Backpack en vervolgens verplaatst naar hun karaktermodel wanneer ze worden uitgerust. Elke tool die een kind van een karakter wordt, zal automatisch worden uitgerust.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-unequipped.png) Tripmine Niet-uitgerust

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-equipped-character.png) Tripmine Uitgerust

### [Starter tool](#starter-tool)[](#starter-tool)

Een tool opslaan in [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  plaatst deze in de [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  van een speler wanneer ze zich aanmelden of opnieuw verschijnen.

1.

Verplaats de Blaster  naar StarterPack  in de Explorer .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-starterpack.png)

2.

Speel het spel om de tool te testen. Klik op de hotbar onderaan het scherm of druk op 1  op het toetsenbord om de tool uit te rusten.

## [Tool eigenschappen](#tool-eigenschappen)[](#tool-eigenschappen)

### [Positie / oriëntatie](#positie--oriëntatie)[](#positie--oriëntatie)

De positie en oriëntatie van een tool kunnen worden gewijzigd met behulp van de grip  eigenschappen. GripPos  verandert de positie van de grip, terwijl GripForward , GripRight  en GripUp  de rotatie beïnvloeden.

Momenteel houdt de speler het midden van de blaster vast in plaats van de grip.

1.

Stel de GripPos  eigenschap van de tool in op 0, -0.4, 1.1 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/property-grippos.png)

2.

[Start een playtest](/docs/nl-nl/studio/testing-modes#spelen-testen)  om de tool te testen. Let op hoe de tool nu op een andere positie wordt vastgehouden.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-weapon-pos-2.jpg) Voor

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-weapon-pos-1.jpg) Na

### [Hotbar-icoon](#hotbar-icoon)[](#hotbar-icoon)

Standaard wordt de naam  van de tool weergegeven op het hotbar-icoon. Het is een goede gewoonte om het icoon te veranderen in een afbeelding van de tool. Stel de TextureId  eigenschap van de tool in op rbxassetid://92628145 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-blaster-icon-2.png) Voor

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-blaster-icon.png) Na

### [Tooltip](#tooltip)[](#tooltip)

Een tooltip  is een kleine tekstbeschrijving die verschijnt wanneer de muis boven een tool in de hotbar zweeft. Ze bevatten meestal de naam van de tool en/of een korte beschrijving van de functie. Verander de ToolTip  eigenschap in Blaster .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-tooltip.png)

## [Gebruik scripts met tools](#gebruik-scripts-met-tools)[](#gebruik-scripts-met-tools)

Een tool heeft drie belangrijke gebeurtenissen waaraan je kunt verbinden: [Equipped](/docs/nl-nl/reference/engine/classes/Tool#Equipped) , [Unequipped](/docs/nl-nl/reference/engine/classes/Tool#Unequipped)  en [Activated](/docs/nl-nl/reference/engine/classes/Tool#Activated) .

| Evenement | | Beschrijving |
| --- | --- |
| **[Equipped](/docs/nl-nl/reference/engine/classes/Tool#Equipped)** | | Wordt geactiveerd wanneer een tool door de speler wordt uitgerust, bijvoorbeeld wanneer een tool in de hotbar is geselecteerd. |
| **[Unequipped](/docs/nl-nl/reference/engine/classes/Tool#Unequipped)** | | Wordt geactiveerd wanneer een tool door de speler wordt uitgetrokken, bijvoorbeeld wanneer een tool in de hotbar wordt gedeselecteerd. |
| **[Activated](/docs/nl-nl/reference/engine/classes/Tool#Activated)** | | Wordt geactiveerd wanneer een tool door de speler wordt geactiveerd, bijvoorbeeld wanneer een speler met de linkermuisknop klikt. |

Deze methoden werken alleen in [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  omdat alleen het apparaat van de speler weet wanneer er invoer plaatsvindt, zoals een muisklik of een aanraking van het scherm.

## [Voeg de geluiden toe](#voeg-de-geluiden-toe)[](#voeg-de-geluiden-toe)

Om deze gebeurtenissen in actie te zien, kun je een geluid afspelen wanneer ze worden geactiveerd. Eerst moet je Sound-objecten maken om hiervoor te gebruiken.

1.

Voeg twee [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten toe aan de Handle .

2.

Hernoem één geluid naar Equip  en stel de SoundId-eigenschap in op rbxassetid://282906960 .

3.

Hernoem het andere geluid naar Activate  en stel de SoundId-eigenschap in op rbxassetid://130113322 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-sounds.png)

## [Voeg de code toe](#voeg-de-code-toe)[](#voeg-de-code-toe)

De voorbeeldcode hieronder speelt het Equip  geluid af wanneer de tool wordt uitgerust en het Fire  geluid wanneer deze wordt geactiveerd.

1.

Voeg een LocalScript  toe aan de tool en noem het ToolController .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-toolcontroller.png)

2.

Voeg de volgende regels code toe aan het script.

```

local tool = script.Parent

local function toolEquipped()

	tool.Handle.Equip:Play()

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Activated:Connect(toolActivated)

```

3.

Test de blaster geluidseffecten door de tool uit te rusten en te klikken om deze te activeren.

Nu weet je hoe je een basis tool kunt maken en script, probeer andere eenvoudige tools te maken zoals een zaklamp of luidspreker.

[Volgende](/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/hit-detection-with-lasers)[Vorige](/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-a-health-pickup)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
