<!-- Source: https://create.roblox.com/docs/nl-nl/input/input-action-system -->

Invoeren Actiesysteem | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Input](/docs/nl-nl/input)

# Invoeren Actiesysteem

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het cross-platform Invoeren Actiesysteem  stelt je in staat om [acties](#invoeracties)  te verbinden en [bindings](#invoerbindings)  te rangschikken over verschillende hardware-invoeren tijdens de bewerkingstijd. In combinatie met [contexten](#invoercontexten)  kun je eenvoudig een modulair invoersysteem configureren en bewerken dat op elk apparaat werkt in elke fase van het spel. Voorbeelden van gebruik zijn:

-

Een first-person shooter systeem waarbij acties dynamisch in- en uitgeschakeld worden, afhankelijk van of de speler in de gevechtsmodus of de toeschouwersmodus is.

-

Een uitgebreid rijdend systeem uitgerust met acceleratie/vertraging, autoboosters en tankstations.

-

Sneltoetsen voor een vaardigheden systeem in een vechtspel om bewegingen naadloos te verwisselen zonder dat spelers een klap missen.

## [Invoercontexten](#invoercontexten)[](#invoercontexten)

Een [InputContext](/docs/nl-nl/reference/engine/classes/InputContext)  is een verzameling van acties die gerelateerde [invoeren acties](#invoeracties)  bevat, bijvoorbeeld PlayContext  voor in-game karakterbesturing en NavContext  voor besturing om door UI-menu's te navigeren. Je kunt [contexten in-/uitschakelen](#contextwijzigingen)  (en hun bijbehorende acties) via hun [Enabled](/docs/nl-nl/reference/engine/classes/InputContext#Enabled)  eigenschap, zoals om de NavContext  in te schakelen wanneer een inventaris menu open is en vervolgens te schakelen naar de PlayContext  wanneer de speler het menu sluit en terugkeert naar de primaire gameplay.

Zelfs als een spel aanvankelijk geen meerdere invoercontexten gebruikt, is het aan te raden om een primaire context op het hoogste niveau van elk invoersysteem te creëren, bijvoorbeeld de PlayContext  instantie voor invoer die plaatsvindt tijdens de gameplay.

1.

AANBEVOLEN

 Maak een [Folder](/docs/nl-nl/reference/engine/classes/Folder)  genaamd Inputs  binnen [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  om verschillende invoercontexten te bevatten.

 ![Nieuwe map binnen ReplicatedStorage, hernoemd naar Inputs](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Folder-Inputs.png)

2.

Voeg een nieuwe [InputContext](/docs/nl-nl/reference/engine/classes/InputContext)  toe aan de map en hernoem deze naar PlayContext .

 ![Nieuwe InputContext instantie binnen ReplicatedStorage, hernoemd naar PlayContext](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext.png)

3.

OPTIONEEL

 Stel in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster de [Priority](/docs/nl-nl/reference/engine/classes/InputContext#Priority)  in op 2000  en schakel [Sink](/docs/nl-nl/reference/engine/classes/InputContext#Sink)  in. Een context met [Sink](/docs/nl-nl/reference/engine/classes/InputContext#Sink)  ingeschakeld verbruikt invoerevenementen voor zijn gebonden [KeyCodes](/docs/nl-nl/reference/engine/enums/KeyCode)  op zijn prioriteitsniveau, waardoor die invoeren worden geblokkeerd voor contexten met een lagere prioriteit. Dit is praktisch voor gebruiksgevallen zoals een inventaris scherm dat specifieke gameplay-invoeren moet onderdrukken terwijl het open is. In dit voorbeeld krijgt PlayContext  een hoge genoeg [Priority](/docs/nl-nl/reference/engine/classes/InputContext#Priority)  om zijn gebonden invoeren te sinken voordat de standaard [PlayerScripts](/docs/nl-nl/reference/engine/classes/PlayerScripts)  contexten ze verwerken.

 ![InputContext met Prioriteit ingesteld op 2000 en Sink ingeschakeld](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputContext-Priority-Sink.png)

## [Invoeracties](#invoeracties)[](#invoeracties)

Een [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  definieert een gameplay actie mechaniek zoals "Springen," "Sprinten," of "Schieten." Deze acties worden vervolgens gekoppeld aan hardware-invoeren met behulp van [invoerbindings](#invoerbindings) .

Een [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  kan verschillende variaties hebben, afhankelijk van zijn [Type](/docs/nl-nl/reference/engine/classes/InputAction#Type)  eigenschap ([Enum.InputActionType](/docs/nl-nl/reference/engine/enums/InputActionType) ). De standaard is [Bool](/docs/nl-nl/reference/engine/enums/InputActionType) , ontworpen om true / false  waarden te ontvangen van drukken/loslaten van invoeren zoals [ButtonA](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonA) , [E](/docs/nl-nl/reference/engine/enums/KeyCode#E) , of [MouseLeftButton](/docs/nl-nl/reference/engine/enums/KeyCode#MouseLeftButton) .

[InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  biedt ook een alleen-lezen [PreferredBinding](/docs/nl-nl/reference/engine/classes/InputAction#PreferredBinding)  eigenschap die de kind [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  retourneert die het beste overeenkomt met het huidige invoerapparaat van de speler (toetsenbord/muis, gamepad of aanraak). Het wordt dynamisch bijgewerkt naarmate de apparaatconfiguratie van de speler verandert en is de basis voor [het weergeven van bindings](#weergeven-van-bindings)  aan spelers.

| Invoer Actie Type | | Voorbeeld Gebruik |
| --- | --- |
| [Bool](/docs/nl-nl/reference/engine/enums/InputActionType) | | Geactiveerde acties zoals springen, schieten, sprinten, enz. met ondersteuning voor ingedrukte/losgelaten drempels op analoge invoeren. |
| [Direction1D](/docs/nl-nl/reference/engine/enums/InputActionType) | | Variabele nul-tot-vol acties zoals het gaspedaal van een auto of het zoomniveau van een kijker. |
| [Direction2D](/docs/nl-nl/reference/engine/enums/InputActionType) | | 2D directionele beweging zoals camerabeweging, of de standaard Roblox karakterbeweging. |
| [Direction3D](/docs/nl-nl/reference/engine/enums/InputActionType) | | 3D directionele beweging zoals een luchtvoertuig dat omhoog/omlaag kan zweven, versnellen/vertragen, en naar links/rechts kan afdrijven. |
| [ViewportPosition](/docs/nl-nl/reference/engine/enums/InputActionType) | | 2D viewport coördinaten zoals muisinvoer, bijvoorbeeld voor aangepaste cursors of raycasting om wereldobjecten te selecteren. |

Karakter Sprinten Camera Rotatie

Om een [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  voor eenvoudig karakter sprinten te testen:

1.

AANBEVOLEN

 Selecteer het top-level [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  object in de [Explorer](/docs/nl-nl/studio/explorer)  en stel vervolgens in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster de [PlayerScriptsUseInputActionSystem](/docs/nl-nl/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  eigenschap in op [Enabled](/docs/nl-nl/reference/engine/enums/RolloutState) .

2.

Maak een nieuwe [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  binnen de PlayContext  context binnen [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Hernoem deze naar CharacterSprint  om de specifieke actie aan te geven.

 ![Nieuwe InputAction instantie binnen een InputContext, hernoemd naar CharacterSprint](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction.png)

3.

In het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, merk op dat het type van de actie [Type](/docs/nl-nl/reference/engine/classes/InputAction#Type)  is [Bool](/docs/nl-nl/reference/engine/enums/InputActionType)  (standaard). Dit is een logisch type voor eenvoudig karakter sprinten als een boolean true / false  actie (het karakter sprint of sprint niet).

 ![Type eigenschap van een InputAction ingesteld op Bool](https://prod.docsiteassets.roblox.com/assets/studio/properties/SprintAction-Type-Bool.png)

## [Invoerbindings](#invoerbindings)[](#invoerbindings)

Een [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  definieert welke hardwarebinding de bovenliggende [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  moet activeren, bijvoorbeeld een toetsdruk, gamepadknop of tik op een aanraakapparaat. Voor [cross-platform](/docs/nl-nl/projects/cross-platform)  compatibiliteit, moet elke [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  een [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  hebben voor gamepad , toetsenbord/muis , en aanraak  zoals hier geïllustreerd.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-InputBinding-All.png)

Standaard Bindings

Roblox biedt standaard invoerbindingen voor beweging, camerabesturing en basisinteractie met de omgeving — Roblox-spelers zijn vertrouwd met deze bedieningselementen, dus je zou ze alleen in specifieke gevallen moeten overschrijven. Houd er ook rekening mee dat de gereserveerde  invoer niet kan worden overschreven en altijd zal functioneren met hun bedoelde doel.

Roblox Gereserveerd Personage Interface / Inventaris Camera

| Actie | | Muis/Toetsenbord | | Gamepad | | Aanraken |
| Open Roblox-menu | | Esc | | Start  knop ([ButtonStart](/docs/nl-nl/reference/engine/enums/KeyCode) ) | | N.v.t. |
| [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console) | | F9 | | N.v.t. | | N.v.t. |
| Volledig scherm modus (Windows)
Toon bureaublad (Mac) | | F11 | | N.v.t. | | N.v.t. |
| Video opnemen (Windows) | | F12 | | N.v.t. | | N.v.t. |
| Screenshot maken | | PrintScreen | | N.v.t. | | N.v.t. |

De [Type](/docs/nl-nl/reference/engine/classes/InputAction#Type)  die aan de bovenliggende [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  is toegewezen, beïnvloedt direct welke algemene invoertypes (toets/button/tik, analoge trigger, thumbstick, enz.) geldig zijn voor kind [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  instanties. Op hun beurt hangen de waarden die naar de verbonden evenementen van de bovenliggende actie worden verzonden af van het gekozen invoertype van een binding. Zie [invoerevenementen](#invoerevenementen)  voor details over de correlatie tussen actie types, bindings, en retourwaarden.

Karakter Sprinten Camera Rotatie

Om bindings voor eenvoudig karakter sprinten aan te sluiten:

1.

Voeg een nieuwe [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  toe aan de CharacterSprint  actie en hernoem deze naar KeyboardBinding . Stel vervolgens de [KeyCode](/docs/nl-nl/reference/engine/classes/InputBinding#KeyCode)  eigenschap van de binding in op [LeftShift](/docs/nl-nl/reference/engine/enums/KeyCode#LeftShift) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-InputBinding-KeyboardBinding.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputBinding-KeyCode-LeftShift.png)

2.

Voeg een tweede [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  toe aan de CharacterSprint  actie en hernoem deze naar GamepadBinding . Stel vervolgens de [KeyCode](/docs/nl-nl/reference/engine/classes/InputBinding#KeyCode)  eigenschap van de binding in op [ButtonY](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonY) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-InputBinding-GamepadBinding.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputBinding-KeyCode-ButtonY.png)

3.

Maak binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  een [knop op het scherm](/docs/nl-nl/ui/buttons) , hernoem deze naar SprintButton , en [positioneer/resize](/docs/nl-nl/ui/position-and-size)  deze zoals gewenst.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-SprintButton.png)  ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/Sprint-Button.png)

4.

Voeg een derde [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  toe aan de CharacterSprint  actie en hernoem deze naar TouchBinding . Stel vervolgens in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster de [UIButton](/docs/nl-nl/reference/engine/classes/InputBinding#UIButton)  eigenschap van de binding in op de SprintButton  knop die je eerder hebt gemaakt binnen [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-InputBinding-TouchBinding.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/InputBinding-UIButton-SprintButton.png)

## [Invoerevenementen](#invoerevenementen)[](#invoerevenementen)

De [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  instantie heeft drie ingebouwde evenementen  om spelersinvoer te verwerken die afkomstig is van [InputBindings](/docs/nl-nl/reference/engine/classes/InputBinding) .

-

[Pressed](/docs/nl-nl/reference/engine/classes/InputAction#Pressed)  — Dit evenement wordt alleen geactiveerd wanneer het invoeractie type [Type](/docs/nl-nl/reference/engine/classes/InputAction#Type)  is ingesteld op [Bool](/docs/nl-nl/reference/engine/enums/InputActionType) , en alleen wanneer de status overgaat van false  naar true .

-

[Released](/docs/nl-nl/reference/engine/classes/InputAction#Released)  — Dit evenement wordt alleen geactiveerd wanneer het invoeractie type [Type](/docs/nl-nl/reference/engine/classes/InputAction#Type)  is ingesteld op [Bool](/docs/nl-nl/reference/engine/enums/InputActionType) , en alleen wanneer de status overgaat van true  naar false .

-

[StateChanged](/docs/nl-nl/reference/engine/classes/InputAction#StateChanged)  — Dit evenement wordt geactiveerd voor alle invoeractie types wanneer de status verandert, behalve als de status probeert over te gaan naar dezelfde status.

Afhankelijk van het invoeractie type [Type](/docs/nl-nl/reference/engine/classes/InputAction#Type)  ([Bool](/docs/nl-nl/reference/engine/enums/InputActionType) , [Direction1D](/docs/nl-nl/reference/engine/enums/InputActionType) , [Direction2D](/docs/nl-nl/reference/engine/enums/InputActionType) , [Direction3D](/docs/nl-nl/reference/engine/enums/InputActionType) , of [ViewportPosition](/docs/nl-nl/reference/engine/enums/InputActionType) ) en het algemene invoertype dat afkomstig is van een kind [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  (toets/button/tik, analoge trigger, thumbstick, enz.), worden verschillende waarden geretourneerd aan de [Pressed](/docs/nl-nl/reference/engine/classes/InputAction#Pressed) , [Released](/docs/nl-nl/reference/engine/classes/InputAction#Released) , en [StateChanged](/docs/nl-nl/reference/engine/classes/InputAction#StateChanged)  evenement handlers. Bekijk de volgende tabellen om de correlatie beter te begrijpen.

Bool Direction1D Direction2D Direction3D ViewportPosition

Het [Bool](/docs/nl-nl/reference/engine/enums/InputActionType)  type is het beste voor geactiveerde acties zoals springen, schieten, sprinten, enz. met ondersteuning voor ingedrukte/losgelaten drempels op analoge invoeren.

| Geldige Invoer Types op [InputBindings](/docs/nl-nl/reference/engine/classes/InputBinding) | | Geretourneerd aan de [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  Evenement(en) |
| Boolean invoeren van toetsenbordtoetsen of basis muis/gamepad knoppen via de binding's [KeyCode](/docs/nl-nl/reference/engine/classes/InputBinding#KeyCode)  eigenschap, of een [GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton)  druk/loslaten via de binding's [UIButton](/docs/nl-nl/reference/engine/classes/InputBinding#UIButton)  eigenschap. | |
-

[Pressed](/docs/nl-nl/reference/engine/classes/InputAction#Pressed)  evenement:
-

true  wanneer ingedrukt

-

[Released](/docs/nl-nl/reference/engine/classes/InputAction#Released)  evenement:
-

true  wanneer losgelaten

-

[StateChanged](/docs/nl-nl/reference/engine/classes/InputAction#StateChanged)  evenement:
-

true  (ingedrukt) of false  (losgelaten)

 |
| Variabele invoerhoeveelheden van analoge invoeren zoals gamepad triggers ([ButtonL2](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonL2) /[ButtonR2](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonR2) ) via de binding's [KeyCode](/docs/nl-nl/reference/engine/classes/InputBinding#KeyCode)  eigenschap. | |
-

[Pressed](/docs/nl-nl/reference/engine/classes/InputAction#Pressed)  evenement:
-

true  wanneer triggerdruk >=  [PressedThreshold](/docs/nl-nl/reference/engine/classes/InputBinding#PressedThreshold)  is

-

[Released](/docs/nl-nl/reference/engine/classes/InputAction#Released)  evenement:
-

true  wanneer triggerdruk <=  [ReleasedThreshold](/docs/nl-nl/reference/engine/classes/InputBinding#ReleasedThreshold)  is

-

[StateChanged](/docs/nl-nl/reference/engine/classes/InputAction#StateChanged)  evenement:
-

true  wanneer triggerdruk >=  [PressedThreshold](/docs/nl-nl/reference/engine/classes/InputBinding#PressedThreshold)  is

-

false  wanneer triggerdruk <=  [ReleasedThreshold](/docs/nl-nl/reference/engine/classes/InputBinding#ReleasedThreshold)  is

 |

Karakter Sprinten Camera Rotatie

Om evenementen voor eenvoudig karakter sprinten aan te sluiten:

1.

Voeg een nieuwe [Script](/docs/nl-nl/reference/engine/classes/Script)  toe aan de CharacterSprint  boom, naast de verschillende invoerbindings. Stel vervolgens de [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  in op [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client)  en hernoem deze naar OnActivate .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-Script.png)

2.

Plak de volgende code in het OnActivate  script. Let op de [Pressed](/docs/nl-nl/reference/engine/classes/InputAction#Pressed)  evenementverbinding op regels 13 ‑ 15  die de loopsnelheid van het karakter verdubbelt wanneer een sprintinvoerbinding wordt ingedrukt, en de overeenkomstige [Released](/docs/nl-nl/reference/engine/classes/InputAction#Released)  evenementverbinding op regels 16 ‑ 18  die de loopsnelheid terugzet naar de standaardwaarde wanneer een sprintinvoerbinding wordt losgelaten.

OnActivate (Client Script)

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character

if not character or character.Parent == nil then

	character = player.CharacterAdded:Wait()

end

local humanoid = character:WaitForChild("Humanoid")

local defaultWalkSpeed = humanoid.WalkSpeed

local inputAction = script.Parent

inputAction.Pressed:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed * 2

end)

inputAction.Released:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed

end)

```

3.

Speel je spel en test de karakter sprintactie met de [bindings](#invoerbindings)  die je eerder hebt gekozen: [LeftShift](/docs/nl-nl/reference/engine/enums/KeyCode#LeftShift)  voor toetsenbord, [ButtonY](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonY)  voor gamepad, en de op het scherm weergegeven SprintButton  voor aanraakapparaten. Vergeet niet dat je de [Controller Emulator](/docs/nl-nl/studio/testing-modes#controller-emulation)  kunt gebruiken om gamepadinvoeren direct in Roblox Studio te testen.

## [Contextwijzigingen](#contextwijzigingen)[](#contextwijzigingen)

Zodra je een [invoercontext](#invoercontexten)  zoals PlayContext  hebt, kun je deze tijdens de gameplay in-/uitschakelen via scripting, de [Priority](/docs/nl-nl/reference/engine/classes/InputContext#Priority)  wijzigen om te bepalen welke acties voorrang hebben boven andere, en [Sink](/docs/nl-nl/reference/engine/classes/InputContext#Sink)  invoeren om te voorkomen dat ze worden verwerkt binnen contexten van lagere prioriteit.

1.

Om het gemakkelijker te maken om contexten vanuit andere scripts te wisselen, voeg een nieuwe [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  toe aan je invoermap binnen [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  en hernoem deze naar ContextEvent .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-BindableEvent-ContextEvent.png)

2.

Maak een nieuw [Script](/docs/nl-nl/reference/engine/classes/Script)  op hetzelfde niveau, stel de [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  in op [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) , en hernoem deze naar UpdateContext .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Script-UpdateContext.png)

3.

Plak de volgende code in het UpdateContext  script:

UpdateContext (Client Script)

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local inputsFolder = ReplicatedStorage:WaitForChild("Inputs")

local contextEvent = inputsFolder:WaitForChild("ContextEvent")

-- Verbind bindbare gebeurtenis

contextEvent.Event:Connect(function(targetContext, enabled)

	local context = inputsFolder:FindFirstChild(targetContext)

	if context then

		context.Enabled = enabled

		print(context.Name .. ": " .. tostring(context.Enabled))

	else

		warn("InputContext niet gevonden!")

	end

end)

```

4.

Met het UpdateContext  script op zijn plaats, kun je nu een genaamde [InputContext](/docs/nl-nl/reference/engine/classes/InputContext)  bijwerken door de bindbare gebeurtenis te activeren, bijvoorbeeld vanuit een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  die een [GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton)  aanstuurt binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-TextButton.png)

Button Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local inputsFolder = ReplicatedStorage:WaitForChild("Inputs")

local contextEvent = inputsFolder:WaitForChild("ContextEvent")

local button = script.Parent

button.Activated:Connect(function()

	-- Activeer bindbare gebeurtenis met doel invoercontext en ingeschakelde status

	contextEvent:Fire("PlayContext", true)

end)

```

## [Weergeven van bindings](#weergeven-van-bindings)[](#weergeven-van-bindings)

Zodra je [acties](#invoeracties)  en [bindings](#invoerbindings)  hebt ingesteld, moet je doorgaans spelers laten zien, via op het scherm weergegeven [ondersteunende hints](/docs/nl-nl/projects/cross-platform#ondersteunende-hints) , welke toets of knop elke actie activeert:

Toetsenbord Invoer Gamepad Invoer

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Inventory-Selection-Keyboard.jpg)

Het Invoeren Actiesysteem biedt twee benaderingen:

-

AANBEVOLEN

 [InputActionLabel](/docs/nl-nl/reference/engine/classes/InputActionLabel)  — Een no-code, drag-and-drop [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  dat automatisch de juiste invoer per platform weergeeft.

-

INTERMEDIAIR

 [PreferredBinding](/docs/nl-nl/reference/engine/classes/InputAction#PreferredBinding)  — Een alleen-lezen [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  eigenschap voor makers die volledige controle willen over hoe bindings in aangepaste UI worden weergegeven.

InputActionLabel PreferredBinding

Deze klasse/object is momenteel in beta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ InputActionLabel .

[InputActionLabel](/docs/nl-nl/reference/engine/classes/InputActionLabel)  is een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  dat je kunt invoegen in elke [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  of [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui) . Zodra de [InputAction](/docs/nl-nl/reference/engine/classes/InputActionLabel#InputAction)  eigenschap is ingesteld om te verwijzen naar een bestaande [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  instantie, lost het automatisch de juiste toetsbinding op voor het huidige invoerapparaat van de speler — geen scripting vereist. Wanneer de speler van apparaat wisselt (bijvoorbeeld, een gamepad oppakken na het gebruik van een toetsenbord) of een bediening opnieuw toewijst, wordt het label onmiddellijk bijgewerkt.

Om een [InputActionLabel](/docs/nl-nl/reference/engine/classes/InputActionLabel)  toe te voegen:

1.

Binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) , voeg een [InputActionLabel](/docs/nl-nl/reference/engine/classes/InputActionLabel)  toe zoals elke andere [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) .

2.

Stel in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster de [InputAction](/docs/nl-nl/reference/engine/classes/InputActionLabel#InputAction)  eigenschap in op de [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  instantie die je wilt weergeven (bijvoorbeeld, je "Sprint" actie onder [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) ) en [positioneer/resize](/docs/nl-nl/ui/position-and-size)  het zoals gewenst.

3.

Wanneer het label oplost wat het moet weergeven, controleert het het volgende in volgorde:

1.

Aangepaste Afbeeldingen  — Als kind [InputBindings](/docs/nl-nl/reference/engine/classes/InputBinding)  hun [DisplayImage](/docs/nl-nl/reference/engine/classes/InputBinding#DisplayImage)  eigenschap hebben ingesteld, rendert het label die afbeeldingen direct.

2.

Platform Toets Afbeeldingen  — Bij gebrek aan aangepaste afbeeldingen, rendert het label platform-geleverde afbeeldingen voor kind [InputBindings](/docs/nl-nl/reference/engine/classes/InputBinding)  via [UserInputService:GetImageForKeyCode()](/docs/nl-nl/reference/engine/classes/UserInputService#GetImageForKeyCode) , als dergelijke afbeeldingen beschikbaar zijn. Samengestelde bindings met modifiers tonen meerdere pictogrammen met +  scheidingstekens.

3.

Aangepaste Namen  — Bij gebrek aan beschikbare afbeeldingen, als kind [InputBindings](/docs/nl-nl/reference/engine/classes/InputBinding)  hun [DisplayName](/docs/nl-nl/reference/engine/classes/InputBinding#DisplayName)  eigenschap hebben ingesteld, rendert het label die tekst met behulp van de stijl eigenschappen van het label.

4.

Platform Toets Strings  — Bij gebrek aan al het bovenstaande, rendert het label platform-geleverde strings via [UserInputService:GetStringForKeyCode()](/docs/nl-nl/reference/engine/classes/UserInputService#GetStringForKeyCode) .

5.

Als er geen [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  is toegewezen of er geen kind [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  bestaat, rendert het label een placeholder pictogram.

## [Invoeren Actie Manager](#invoeren-actie-manager)[](#invoeren-actie-manager)

Deze tool is momenteel in beta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ Invoeren Actie Manager .

De Invoeren Actie Manager  tool is een uniforme, matrix-achtige interface om je invoerarchitectuur te ontwerpen, te controleren en op te schalen.

Om toegang te krijgen, navigeer naar het Venster  menu in Studio en selecteer Invoer  ⟩ Invoeren Actie Manager . Als je spel al invoer [contexten](#invoercontexten) , [acties](#invoeracties) , of [bindings](#invoerbindings)  gebruikt, zal de manager automatisch het [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  scannen en die bestaande instanties in de editor grid extraheren. Nieuwe invoer-gerelateerde instanties worden automatisch toegevoegd aan een Inputs  map binnen [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

 ![Map binnen ReplicatedStorage genaamd Inputs](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Folder-Inputs.png)

Om een invoeropstelling voor karakter sprint  te configureren zoals beschreven in de bovenstaande secties:

1.

AANBEVOLEN

 Selecteer het top-level [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  object in de [Explorer](/docs/nl-nl/studio/explorer)  en stel vervolgens in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster de [PlayerScriptsUseInputActionSystem](/docs/nl-nl/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  eigenschap in op [Enabled](/docs/nl-nl/reference/engine/enums/RolloutState) .

2.

Maak binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  een [knop op het scherm](/docs/nl-nl/ui/buttons) , hernoem deze naar SprintButton , en [positioneer/resize](/docs/nl-nl/ui/position-and-size)  deze zoals gewenst.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-SprintButton.png)

3.

In de Invoeren Actie Manager , beweeg over de Context  kolomkop en klik op de ＋  knop. Voer een geschikte naam in voor de nieuwe context zoals PlayContext  en druk op Enter . Een [InputContext](/docs/nl-nl/reference/engine/classes/InputContext)  van de bijpassende naam verschijnt in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

![](https://prod.docsiteassets.roblox.com/assets/studio/input-action-manager/Add-Context.png)

![Nieuwe InputContext instantie binnen ReplicatedStorage genaamd PlayContext](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext.png)

4.

Beweeg over de nieuwe context en klik op de ＋  knop. Selecteer uit het pop-upmenu [Bool](/docs/nl-nl/reference/engine/enums/InputActionType) , voer CharacterSprint  in voor de naam van de actie, en druk op Enter . Een [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  van de bijpassende naam verschijnt onder de context.

![](https://prod.docsiteassets.roblox.com/assets/studio/input-action-manager/Add-Action.png)

![Nieuwe InputAction instantie binnen een InputContext genaamd CharacterSprint](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction.png)

5.

Wijs in de nieuwe CharacterSprint  rij bindings toe voor elk invoertype:

1.

Toetsenbord en Muis  — Klik op de pijlknop en selecteer [LeftShift](/docs/nl-nl/reference/engine/enums/KeyCode)  uit het keuzemenu.

2.

Aanraak  — Klik op de cel en klik vervolgens in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie op het SprintButton  object dat je eerder in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  hebt ingevoegd.

3.

Gamepad  — Klik op de pijlknop en selecteer [ButtonY](/docs/nl-nl/reference/engine/enums/KeyCode)  uit het keuzemenu.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/input-action-manager/Add-Bindings-Sprint.png)

Terwijl je bindings toewijst, let op waarschuwing/fout pictogrammen in de UI. Gele waarschuwingen (** ⚠** ) geven een ontbrekende  binding aan voor [cross-platform](/docs/nl-nl/projects/cross-platform)  compatibiliteit, terwijl rode waarschuwingen (** ⚠** ) een dubbele  binding aangeven voor acties binnen dezelfde context.

6.

Voeg een nieuwe [Script](/docs/nl-nl/reference/engine/classes/Script)  toe aan de CharacterSprint  boom, naast de verschillende invoerbindings. Stel vervolgens de [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  in op [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client)  en hernoem deze naar OnActivate .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext-SprintAction-Script-IAM.png)

7.

Plak de volgende code in het OnActivate  script. Let op de [Pressed](/docs/nl-nl/reference/engine/classes/InputAction#Pressed)  evenementverbinding op regels 13 ‑ 15  die de loopsnelheid van het karakter verdubbelt wanneer een sprintinvoerbinding wordt ingedrukt, en de overeenkomstige [Released](/docs/nl-nl/reference/engine/classes/InputAction#Released)  evenementverbinding op regels 16 ‑ 18  die de loopsnelheid terugzet naar de standaardwaarde wanneer een sprintinvoerbinding wordt losgelaten.

OnActivate (Client Script)

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character

if not character or character.Parent == nil then

	character = player.CharacterAdded:Wait()

end

local humanoid = character:WaitForChild("Humanoid")

local defaultWalkSpeed = humanoid.WalkSpeed

local inputAction = script.Parent

inputAction.Pressed:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed * 2

end)

inputAction.Released:Connect(function()

	humanoid.WalkSpeed = defaultWalkSpeed

end)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
