<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/input-and-camera/detect-user-input -->

Detecteer gebruikersinvoer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Input en camera

# Detecteer gebruikersinvoer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het verbinden van gebruikersinvoer met acties geeft gebruikers veel betere en intuïtieve controle over de functies van je spel. In deze tutorial koppel je een herlaadactie aan een specifieke toets.

## [Aan de slag](#aan-de-slag)[](#aan-de-slag)

Deze tutorial maakt gebruik van de Blaster  tool die is gemaakt in [Create Player Tools](/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-player-tools) . Je kunt die instructies volgen om de tool te maken of je kunt het [Blaster](https://www.roblox.com/library/6571559694/Blaster)  model downloaden en in StarterPack  invoegen.

Modellen kunnen aan je Inventaris worden toegevoegd om tussen verschillende spellen te worden gebruikt. Om een model aan je spel toe te voegen:

1.

Open in een browser de [model](https://www.roblox.com/library/6571559694/Blaster)  pagina en klik op de Krijg  knop. Dit voegt het model aan je inventaris toe.

2.

Open vanuit het Venster  menu of de Start  tabbalk de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  en selecteer de Inventaris  tab.

3.

Zorg ervoor dat de dropdown op Mijn Modellen  staat.

4.

Selecteer het Blaster  model om het aan het spel toe te voegen.

## [Maak een actiehandler](#maak-een-actiehandler)[](#maak-een-actiehandler)

Eerst heb je een functie nodig om te handelen wanneer gebruikersinvoer wordt gedetecteerd.

1.

Open de ToolController  [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  binnen de Blaster.

![Weergave van de Explorer waar het ToolController-script binnen de Blaster-tool is geselecteerd](https://prod.docsiteassets.roblox.com/assets/tutorials/detecting-user-input/ToolControllerExplorer.png)

2.

Maak een variabele om een naam voor de actie op te slaan.

```

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

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

Maak een functie genaamd onAction die drie argumenten ontvangt: actionName , inputState  en inputObject . Dit zal de functie zijn die wordt uitgevoerd wanneer gebruikersinvoer wordt gedetecteerd.

```

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

local function onAction(actionName, inputState, inputObject)

end

local function toolEquipped()

	tool.Handle.Equip:Play()

end

```

4.

Controleer binnen de functie of de gegeven actionName  overeenkomt met de naam van de herlaadactie en zorg ervoor dat inputState  gelijk is aan [UserInputState.Begin](/docs/nl-nl/reference/engine/enums/UserInputState)  (de beginstatus). Dit is belangrijk omdat de functie elke keer wordt uitgevoerd wanneer de inputState  verandert, maar de herlaadactie slechts één keer hoeft te gebeuren.

```

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

	end

end

```

5.

Om het voor de gebruiker duidelijk te maken wanneer deze herlaadt, verander je de [TextureId](/docs/nl-nl/reference/engine/classes/BackpackItem#TextureId)  van de tool tijdelijk naar "rbxassetid://6593020923"  en verander je het daarna terug naar de oorspronkelijke waarde van "rbxassetid://92628145" .

```

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

		tool.TextureId = "rbxassetid://6593020923"

		task.wait(2)

		tool.TextureId = "rbxassetid://92628145"

	end

end

```

## [Koppel de actie](#koppel-de-actie)[](#koppel-de-actie)

[ContextActionService](/docs/nl-nl/reference/engine/classes/ContextActionService)  kan worden gebruikt om een functie te koppelen  aan een specifieke invoer door gebruik te maken van de [BindAction](/docs/nl-nl/reference/engine/classes/ContextActionService#BindAction)  functie, die verschillende argumenten accepteert:

-

De naam van de actie.

-

De functie om de actie te verwerken (ook wel een "callback" genoemd).

-

Of er een touchscreenknop moet worden weergegeven.

-

Een aantal Enum.KeyCodes  om te detecteren en te associëren met de actie.

KeyCodes zijn waarden die verschillende invoertoetsen vertegenwoordigen, zoals toetsen op het toetsenbord of knoppen op een controller. Een volledige lijst van codes is beschikbaar [hier](/docs/nl-nl/reference/engine/enums/KeyCode) .

1.

Verkrijg [ContextActionService](/docs/nl-nl/reference/engine/classes/ContextActionService)  aan het begin van het script.

```

local ContextActionService = game:GetService("ContextActionService")

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

```

2.

Roep binnen de toolEquipped  functie BindAction  aan en geef de volgende argumenten door:

-

De naam van de actie (RELOAD_ACTION )

-

De actiehandler (onAction )

-

Een waarde om een aanraakknop te maken (true )

-

Een toetsdruk om te detecteren ([Enum.KeyCode.R](/docs/nl-nl/reference/engine/enums/KeyCode#R) )

```

local RELOAD_ACTION = "reloadWeapon"

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

		tool.TextureId = "rbxassetid://6593020923"

		task.wait(2)

		tool.TextureId = "rbxassetid://92628145"

	end

end

local function toolEquipped()

	ContextActionService:BindAction(RELOAD_ACTION, onAction, true, Enum.KeyCode.R)

	tool.Handle.Equip:Play()

end

```

3.

Test het spel door de tool uit te rusten en op de R  toets op je toetsenbord te drukken. Het rugzakpictogram zou tijdelijk moeten veranderen in een wacht symbool om aan te geven dat het wapen aan het herladen is:

## [Ontkoppel de actie](#ontkoppel-de-actie)[](#ontkoppel-de-actie)

Wanneer de gebruiker de tool uittrekt, moet de actie worden ontkoppeld  zodat ze niet kunnen herladen zonder dat de tool is uitgerust.

1.

Maak een nieuwe functie genaamd toolUnequipped  en roep [UnbindAction](/docs/nl-nl/reference/engine/classes/ContextActionService#UnbindAction)  aan, waarbij je de actienaam doorgeeft.

```

local function toolEquipped()

	ContextActionService:BindAction(RELOAD_ACTION, onAction, true, Enum.KeyCode.R)

	tool.Handle.Equip:Play()

end

local function toolUnequipped()

	ContextActionService:UnbindAction(RELOAD_ACTION)

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Activated:Connect(toolActivated)

```

2.

Verbind de toolUnequipped  functie met de [Unequipped](/docs/nl-nl/reference/engine/classes/Tool#Unequipped)  gebeurtenis zodat de functie wordt uitgevoerd wanneer de gebeurtenis wordt geactiveerd.

```

local ContextActionService = game:GetService("ContextActionService")

local tool = script.Parent

local RELOAD_ACTION = "reloadWeapon"

local function onAction(actionName, inputState, inputObject)

	if actionName == RELOAD_ACTION and inputState == Enum.UserInputState.Begin then

		tool.TextureId = "rbxassetid://6593020923"

		task.wait(2)

		tool.TextureId = "rbxassetid://92628145"

	end

end

local function toolEquipped()

	ContextActionService:BindAction(RELOAD_ACTION, onAction, true, Enum.KeyCode.R)

	tool.Handle.Equip:Play()

end

local function toolUnequipped()

	ContextActionService:UnbindAction(RELOAD_ACTION)

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Unequipped:Connect(toolUnequipped)

tool.Activated:Connect(toolActivated)

```

3.

Test het spel om te bevestigen dat alles correct werkt. Je zou moeten kunnen herladen wanneer de tool is uitgerust, maar niet wanneer deze is uitgetrokken.

Je herlaadanimatie is nu compleet - voor een extra uitdaging, probeer een munitieteller te tellen elke keer dat de blaster wordt afgevuurd. Je kunt dan de toolActivated  functie deactiveren wanneer het wapen geen munitie meer heeft, en deze opnieuw activeren zodra de herlaadanimatie is voltooid.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
