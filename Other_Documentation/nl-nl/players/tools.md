<!-- Source: https://create.roblox.com/docs/nl-nl/players/tools -->

In-game tools | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# In-game tools

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In-game [Tools](/docs/nl-nl/reference/engine/classes/Tool)  zijn interactieve tools die spelers kunnen uitrusten in sessies, zoals wapens, toverstokken, zaklampen, sleutels en meer. Je kunt tools ontwerpen en ze opnemen in de inventaris van een speler of ze in de wereld plaatsen als pickups.

## [Maak een in-game tool](#maak-een-in-game-tool)[](#maak-een-in-game-tool)

Het [Tool](/docs/nl-nl/reference/engine/classes/Tool)  object is de basis van elke tool in Roblox, dus je moet er een maken. Het is gemakkelijker om een tool te previewen door deze te ontwerpen in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , en later kun je het een [inventaris](#speler-inventaris)  item of een [verdiend/aangekocht](#verdiendeaangekochte-tool)  item maken.

1.

In de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie, beweeg je de muis over [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , klik op de ⊕  knop en voeg een [Tool](/docs/nl-nl/reference/engine/classes/Tool)  toe.

 ![Tool object gemaakt in de workspace](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Tool.png)

2.

Met de nieuwe [Tool](/docs/nl-nl/reference/engine/classes/Tool)  geselecteerd, open je het [Properties](/docs/nl-nl/studio/properties)  venster en pas je aan hoe de tool eruit zal zien in de inventaris van de speler:

-

[TextureId](/docs/nl-nl/reference/engine/classes/Tool#TextureId)  — Specificeert de afbeelding asset ID voor de tool in de inventaris van een speler.

-

[ToolTip](/docs/nl-nl/reference/engine/classes/Tool#ToolTip)  — De tooltip naam bij hover voor de tool in de inventaris van een speler.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Inventory.jpg)

3.

Bepaal of de tool een [fysieke tool in de 3D omgeving](#fysieke-tool)  (meest gebruikelijk) of een [niet-fysieke](#niet-fysieke-tool)  tool zal zijn die simpelweg de inventaris van een speler bezet en reageert op hun input.

### [Fysieke tool](#fysieke-tool)[](#fysieke-tool)

Nadat je de [Tool](/docs/nl-nl/reference/engine/classes/Tool)  instantie voor een fysieke tool hebt gemaakt, moet je [onderdelen/mesh](#voeg-onderdelenmesh-toe)  toevoegen om het uiterlijk in de 3D wereld samen te stellen. Je moet ook een [handvat](#stel-het-handvat-in)  opnemen dat door de spelerspersonages [vastgegrepen](#pas-de-grippositieorientatie-aan)  kan worden.

#### [Voeg onderdelen/mesh toe](#voeg-onderdelenmesh-toe)[](#voeg-onderdelenmesh-toe)

In-game tools kunnen bestaan uit een of meer [Parts](/docs/nl-nl/reference/engine/classes/Part)  en/of [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) . Als je de tool uit meerdere stukken bouwt, vergeet dan niet om ze allemaal met elkaar te verbinden met [WeldConstraints](/docs/nl-nl/reference/engine/classes/WeldConstraint)  of andere [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  zodat de tool intact blijft als een eenheid terwijl de speler deze meedraagt.

 ![Constraint pickers aangegeven in de toolbar van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Constraint-Pickers.png)

Bij het construeren van tools, zorg ervoor dat geen enkele onderdelen [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  zijn. Als je de tool in 3D ruimte verankert, zullen spelerspersonages vast komen te zitten wanneer ze de tool oppakken of uitrusten.

Als je verzamelbare tools als pickups rond de 3D wereld wilt plaatsen en ze op specifieke plaatsen wilt verankeren, zoals iets boven de grond zwevend, kun je ze verankeren, maar je moet een [Script](/docs/nl-nl/reference/engine/classes/Script)  aan elke tool toevoegen die zijn onderdelen ontankert bij verzameling. Zie [verzamelbare tools](#verzamelbare-tool)  voor details.

#### [Stel het handvat in](#stel-het-handvat-in)[](#stel-het-handvat-in)

Om spelers in staat te stellen tools mee te nemen, moet een onderdeel van de tool Handle  worden genoemd. Dit is waar de tool aan het RightHand  [lichaamsdeel](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen)  (R15) of Rechter Arm  deel (R6) van het karaktermodel wordt bevestigd.

Als de tool uit slechts één [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  bestaat, noem dat onderdeel dan eenvoudig Handle . Anders kun je een apart onderdeel met de naam Handle  opnemen als een direct kind  van de bovenliggende [Tool](/docs/nl-nl/reference/engine/classes/Tool)  en het vervolgens aan een ander onderdeel bevestigen met een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  of [mechanische beperking](/docs/nl-nl/physics/mechanical-constraints) .

Het volgende voorbeeld toont een tool met drie instanties: de Handle  mesh, een [RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint) , en een lantaarn mesh die aan het touw hangt.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Handle-Example.jpg)

Zorg ervoor dat je slechts één  onderdeel met de naam Handle  opneemt. Als je meerdere onderdelen met de naam Handle  opneemt, wordt er willekeurig één gekozen als het bevestigingspunt voor de hand van het karakter, wat mogelijk problemen kan veroorzaken, zoals dat het karakter de kling van een zwaard vasthoudt in plaats van de greep.

#### [Pas de grippositie/orientatie aan](#pas-de-grippositieorientatie-aan)[](#pas-de-grippositieorientatie-aan)

De [Grip](/docs/nl-nl/reference/engine/classes/Tool#Grip)  eigenschap van de tool is een [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  die specificeert hoe de tool is gepositioneerd en georiënteerd ten opzichte van het karakter dat deze vasthoudt.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Tool-Grip.png)

Aangezien de ideale grippositie/orientatie voor elke tool anders is, moet je experimenteren met de waarden totdat de grip van je tool er correct uitziet. Het volgende voorbeeld toont mogelijke onjuiste en correcte [Grip](/docs/nl-nl/reference/engine/classes/Tool#Grip)  instellingen voor de hangende lantaarn:

![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Grip-Incorrect.jpg) Lantaarn sleept over de grond met [Grip.Position](/docs/nl-nl/reference/engine/classes/Tool#Grip)  van (0, -2, 0)  en [Grip.Orientation](/docs/nl-nl/reference/engine/classes/Tool#Grip)  van (-90, 0, 0)

![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Grip-Correct.jpg) Lantaarn voor het karakter met [Grip.Position](/docs/nl-nl/reference/engine/classes/Tool#Grip)  van (0, -1.5, 0)  en [Grip.Orientation](/docs/nl-nl/reference/engine/classes/Tool#Grip)  van (25, 0, 0)

### [Niet-fysieke tool](#niet-fysieke-tool)[](#niet-fysieke-tool)

Een niet-fysieke [Tool](/docs/nl-nl/reference/engine/classes/Tool)  bezet simpelweg de [inventaris](#speler-inventaris)  van een speler en reageert op hun input. Bijvoorbeeld, een rollenspel kan een reeks magische spreuken bevatten die spelers kunnen "uitvoeren" via hun inventaris.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Inventory-Non-Physical.jpg)

Niet-fysieke tools vereisen geen 3D samenstelling en maken geen gebruik van een Handle  onderdeel, dus je moet de [RequiresHandle](/docs/nl-nl/reference/engine/classes/Tool#RequiresHandle)  eigenschap van de tool deactiveren :

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Tool-RequiresHandle.png)

## [Voeg tools toe aan een spel](#voeg-tools-toe-aan-een-spel)[](#voeg-tools-toe-aan-een-spel)

Zodra je klaar bent met het [maken](#maak-een-in-game-tool)  van je in-game tool, moet je deze op de juiste plaats in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie plaatsen. Waar je de tool in de hiërarchie plaatst, hangt af van het beoogde gebruik.

### [Speler inventaris](#speler-inventaris)[](#speler-inventaris)

Als je wilt dat alle spelers met een tool in hun inventaris beginnen, plaats deze dan in de [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  container. Wanneer een speler spawnt, kopieert het systeem de tool naar hun [Backpack](/docs/nl-nl/reference/engine/classes/Backpack) . Van daaruit kan de speler de tool uitrusten door op het inventaricon te klikken of door de bijbehorende sneltoets te drukken, zoals 1  of 2 .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterPack-Tools.png)

Let op dat tools in de inventaris van de speler ([Backpack](/docs/nl-nl/reference/engine/classes/Backpack) ) worden gekopieerd in de volgorde waarin ze aan [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  zijn toegevoegd. Voor een meer gecontroleerde ordening kun je een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  aan [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  toevoegen die tijdelijk de tools naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  verplaatst en ze vervolgens opnieuw aan [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  plaatst in de volgorde die is opgegeven in de order  tabel.

Herschik Inventaris

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local order = {"WaterSpell", "FireSpell", "AirSpell", "EarthSpell"}

local backpack = script.Parent

for _, item in backpack:GetChildren() do

	if item:IsA("Tool") then

		item.Parent = ReplicatedStorage

	end

end

-- Herplaats tools naar de rugzak in de opgegeven volgorde

for i = 1, #order do

	local tool = ReplicatedStorage:FindFirstChild(order[i])

	if tool then

		tool.Parent = backpack

	end

end

```

Zoals hierboven opgemerkt, worden tools die in [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  zijn geplaatst gekloond naar alle  spelers. Om specifieker te controleren welke tools naar welke spelers worden gekloond, zie [StarterGear](/docs/nl-nl/reference/engine/classes/StarterGear) .

### [Verzamelbare tool](#verzamelbare-tool)[](#verzamelbare-tool)

Als je spelers wilt toestaan om fysieke tools te verzamelen terwijl ze de 3D wereld verkennen, plaats de tools dan in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  zoals normale 3D objecten. Verzamelde tools worden automatisch uitgerust en toegevoegd aan de inventaris van de speler (je hoeft geen extra botsingsdetectie toe te voegen voor personages om de tool op te pakken).

Zoals opgemerkt in de [voeg onderdelen/mesh toe](#voeg-onderdelenmesh-toe)  sectie, moeten toolonderdelen doorgaans niet [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  zijn, aangezien spelerspersonages vast komen te zitten wanneer ze een verankerde tool oppakken of uitrusten. Als je echter een verzamelbare tool op een specifieke plaats in de 3D wereld wilt verankeren, zoals iets boven de grond zwevend, kun je de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  aan de tool toevoegen om zijn onderdelen te ontankeren bij verzameling.

Ontank Tool bij Uitrusting/Verzameling

```

local tool = script.Parent

tool.Equipped:Connect(function()

	for _, part in tool:GetDescendants() do

		if part:IsA("BasePart") and part.Anchored then

			part.Anchored = false

		end

	end

end)

```

### [Verdiende/aangekochte tool](#verdiendeaangekochte-tool)[](#verdiendeaangekochte-tool)

Als je tools wilt instellen als beloningen voor wanneer spelers taken voltooien, of tools wilt aanbieden te koop in een in-game winkel, plaats die tools dan in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Van daaruit kun je [Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone)  een tool naar de [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  van de speler op het juiste moment.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Tools.png)

Kloon Tool naar Inventaris van de Speler

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer

local backpack = player:WaitForChild("Backpack")

-- Maak een kloon van de tool

local tool = ReplicatedStorage:FindFirstChild("WaterSpell")

if tool then

	local clone = tool:Clone()

	clone.Parent = backpack  -- Voegt kloon toe aan de rugzak van de speler

end

```

## [Implementeer tool effecten](#implementeer-tool-effecten)[](#implementeer-tool-effecten)

Nadat je [tools aan je spel hebt toegevoegd](#voeg-tools-toe-aan-een-spel) , kun je scripts implementeren om spelers in staat te stellen hun tools te gebruiken en de gewenste acties uit te voeren. De volgende tool-specifieke evenementen geven de status van de tool en de input van de speler ermee aan.

-

[Equipped()](/docs/nl-nl/reference/engine/classes/Tool#Equipped)  — Vindt plaats wanneer de speler de tool selecteert uit hun rugzak.

-

[Unequipped()](/docs/nl-nl/reference/engine/classes/Tool#Unequipped)  — Vindt plaats wanneer de speler van tool wisselt of de tool laat vallen.

-

[Activated()](/docs/nl-nl/reference/engine/classes/Tool#Activated)  — Vindt plaats wanneer de speler begint de tool te activeren (klikt, tikt of drukt op de achter-rechter trigger op een gamepad).

-

[Deactivated()](/docs/nl-nl/reference/engine/classes/Tool#Deactivated)  — Vindt plaats wanneer de speler stopt met de activatie-input (laat de knop of aanraking los).

Tool Evenementen Sjabloon

```

local tool = script.Parent

local function onEquip()

	print(tool.Name, "tool uitgerust")

end

local function onUnequip()

	print(tool.Name, "tool niet meer uitgerust")

end

local function onActivate()

	print(tool.Name, "tool geactiveerd")

end

local function onDeactivate()

	print(tool.Name, "tool gedeactiveerd")

end

tool.Equipped:Connect(onEquip)

tool.Unequipped:Connect(onUnequip)

tool.Activated:Connect(onActivate)

tool.Deactivated:Connect(onDeactivate)

```

Toegepaste tool evenementen worden alleen geactiveerd in client-side [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  omdat alleen het apparaat van de speler weet wanneer [input](/docs/nl-nl/input)  plaatsvindt. Als gevolg hiervan vereisen de meeste tools zowel een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  als een server-side [Script](/docs/nl-nl/reference/engine/classes/Script)  waar elk bepaalde aspecten van het gedrag van de tool afhandelt en een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  informatie van de client naar de server doorgeeft (zie [remote events and callbacks](/docs/nl-nl/scripting/events/remote)  voor meer informatie).

Hieronder volgen voorbeeldtools en hun gedragingen beheerd door ofwel een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  of een [Script](/docs/nl-nl/reference/engine/classes/Script) :

| Tool | | [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) | | [Script](/docs/nl-nl/reference/engine/classes/Script) |
| --- | --- |
| Creator's Wand | | Detecteert waar de speler de tool activeert ([Activated()](/docs/nl-nl/reference/engine/classes/Tool#Activated) ). | | Maakt een nieuw onderdeel op de locatie binnen de 3D wereld waar de speler aanraakte of klikte. |
| Invisibility Cloak | | Detecteert wanneer de speler de tool uitrust ([Equipped()](/docs/nl-nl/reference/engine/classes/Tool#Equipped) ) of de tool niet meer uitrust ([Unequipped()](/docs/nl-nl/reference/engine/classes/Tool#Unequipped) ). | | Maakt de speler onzichtbaar voor alle andere spelers terwijl de cloak is uitgerust en herstelt de speler naar volledige zichtbaarheid wanneer de cloak niet meer is uitgerust. |
| Mega‑Bow | | Detecteert hoe lang de speler de tool activeert (tijd tussen [Activated()](/docs/nl-nl/reference/engine/classes/Tool#Activated)  en [Deactivated()](/docs/nl-nl/reference/engine/classes/Tool#Deactivated) ). | | Schoot een magische pijl met grotere of kleinere kracht, afhankelijk van de gedetecteerde activatietijd. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
