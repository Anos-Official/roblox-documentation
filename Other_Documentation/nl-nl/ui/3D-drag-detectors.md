<!-- Source: https://create.roblox.com/docs/nl-nl/ui/3D-drag-detectors -->

3D sleepdetectie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# 3D sleepdetectie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector)  instantie vergemakkelijkt en moedigt interactie aan met 3D-objecten in een spel, zoals het openen van deuren en lades, het verschuiven van een onderdeel, het oppakken en gooien van een bowlingbal, het terugtrekken en afvuren van een katapult, en nog veel meer. Belangrijke kenmerken zijn:

-

Plaats een [DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector)  onder elk [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Model](/docs/nl-nl/reference/engine/classes/Model)  om het [sleepbaar te maken](#maak-objecten-sleepbaar)  via alle invoer (muis, aanraking, gamepad en VR), alles zonder een enkele regel code.

-

Kies uit verschillende [sleepstijlen](#sleepstijl) , definieer hoe het object [reageert op beweging](#reactie-op-beweging) , en pas optioneel [as- of bewegingslimieten](#as--en-bewegingslimieten)  toe.

-

Scripts kunnen [reageren op manipulatie van gesleepte objecten](#scriptreacties-op-klikken-en-slepen)  om UI aan te sturen of logische beslissingen te nemen, zoals het aanpassen van het lichtniveau in een kamer op basis van een schuifwandschakelaar dimmer.

-

Spelers kunnen verankerde onderdelen of modellen manipuleren en ze blijven precies waar je ze plaatst bij het loslaten.

-

[DragDetectors](/docs/nl-nl/reference/engine/classes/DragDetector)  werken in Studio zolang je niet  de Selecteer , Verplaats , Schaal , of Draai  tools gebruikt, waardoor het gemakkelijker wordt om sleepbare objecten te testen en aan te passen tijdens het bewerken.

## [Maak objecten sleepbaar](#maak-objecten-sleepbaar)[](#maak-objecten-sleepbaar)

Om elk onderdeel of model sleepbaar te maken, voeg je eenvoudig een [DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector)  toe als directe afstammeling.

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, beweeg de muis over de [Part](/docs/nl-nl/reference/engine/classes/Part) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , of [Model](/docs/nl-nl/reference/engine/classes/Model)  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een DragDetector  in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-DragDetector.png)

3.

Standaard zal het object nu sleepbaar zijn in het grondvlak, maar je kunt de [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  aanpassen, definiëren hoe het [reageert op beweging](#reactie-op-beweging) , en optioneel [as- of bewegingslimieten](#as--en-bewegingslimieten)  toepassen.

Vergeet niet dat [DragDetectors](/docs/nl-nl/reference/engine/classes/DragDetector)  alleen in Studio werken als je niet  de Selecteer , Verplaats , Schaal , of Draai  tools gebruikt.

## [Pas sleepdetectie aan](#pas-sleepdetectie-aan)[](#pas-sleepdetectie-aan)

### [Sleepstijl](#sleepstijl)[](#sleepstijl)

[DragDetectors](/docs/nl-nl/reference/engine/classes/DragDetector)  koppelen cursorbeweging aan virtuele lijnen en vlakken om voorgestelde 3D-beweging te berekenen. Via de [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  eigenschap kun je kiezen uit verschillende mappings die aan jouw behoeften voldoen. Bijvoorbeeld, TranslatePlane  produceert vertaling in een virtueel vlak, terwijl RotateAxis  rotatie rond een virtuele as produceert.

| Instelling | | Beschrijving |
| --- | --- |
| [TranslateLine](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#TranslateLine) | | 1D beweging langs de as van de detector, standaard de wereld Y  as. |
| [TranslatePlane](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#TranslatePlane) | | 2D beweging in het vlak dat loodrecht staat op de as van de detector, standaard het wereld XZ  vlak. |
| [TranslatePlaneOrLine](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#TranslatePlaneOrLine) | | 2D beweging in het vlak dat loodrecht staat op de as van de detector en, wanneer de [modifier](#modifier-invoer)  actief is, 1D beweging langs de as van de detector. |
| [TranslateLineOrPlane](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#TranslateLineOrPlane) | | 1D beweging langs de as van de detector en, wanneer de [modifier](#modifier-invoer)  actief is, 2D beweging in het vlak dat loodrecht staat op de as van de detector. |
| [TranslateViewPlane](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#TranslateViewPlane) | | 2D beweging in het vlak dat loodrecht staat op het zicht van de camera. In deze modus wordt het vlak constant bijgewerkt, zelfs tijdens het slepen, en zal het altijd naar het huidige zicht van de camera gericht zijn. |
| [RotateAxis](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#RotateAxis) | | Rotatie rond de as van de detector, standaard de wereld Y  as. |
| [RotateTrackball](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#RotateTrackball) | | Trackball-rotatie, verder aangepast via de [TrackballRadialPullFactor](/docs/nl-nl/reference/engine/classes/DragDetector#TrackballRadialPullFactor)  en [TrackballRollFactor](/docs/nl-nl/reference/engine/classes/DragDetector#TrackballRollFactor)  eigenschappen. |
| [BestForDevice](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#BestForDevice) | | TranslatePlaneOrLine  voor muis en gamepad; TranslatePlane  voor aanraking; 6DOF  voor VR. |
| [Scriptable](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#Scriptable) | | Berekeningen van gewenste beweging via een aangepaste functie die wordt geleverd via [SetDragStyleFunction()](/docs/nl-nl/reference/engine/classes/DragDetector#SetDragStyleFunction) . |

### [Sleeprichting](#sleeprichting)[](#sleeprichting)

Standaard worden 3D-beweging en de bijbehorende [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  gekoppeld aan de wereldruimte. Je wilt misschien de [ReferenceInstance](/docs/nl-nl/reference/engine/classes/DragDetector#ReferenceInstance) , [Orientation](/docs/nl-nl/reference/engine/classes/DragDetector#Orientation) , of [Axis](/docs/nl-nl/reference/engine/classes/DragDetector#Axis)  wijzigen, bijvoorbeeld bij het bouwen van sleepdetectie in [modellen met verstelbare onderdelen](#verankerde-modellen-met-verstelbare-onderdelen) .

| Eigenschap | | Beschrijving | | Standaard |
| [ReferenceInstance](/docs/nl-nl/reference/engine/classes/DragDetector#ReferenceInstance) | | Een instantie waarvan de pivot het referentiekader  voor de sleepdetectie biedt. Het [DragFrame](/docs/nl-nl/reference/engine/classes/DragDetector#DragFrame)  wordt uitgedrukt ten opzichte van dit referentiekader, dat kan worden opgehaald via [GetReferenceFrame()](/docs/nl-nl/reference/engine/classes/DragDetector#GetReferenceFrame) . Als het referentiekader nil  is, zal de vertaling in de richting van (of in het vlak dat loodrecht staat op) de [Axis](/docs/nl-nl/reference/engine/classes/DragDetector#Axis)  eigenschap in wereldruimte zijn. | | nil |
| [Orientation](/docs/nl-nl/reference/engine/classes/DragDetector#Orientation) | | Geeft de YXZ  rotatie van de bewegingsassen ten opzichte van het referentiekader aan (verandert de oriëntatie van het referentiekader zelf niet). Lineaire vertaling en axiale rotatie zullen op deze opnieuw georiënteerde Y  as zijn, en vlakke vertaling in het XZ  vlak. Het wijzigen van deze waarde werkt automatisch [Axis](/docs/nl-nl/reference/engine/classes/DragDetector#Axis)  bij en vice versa. | | (0, 0, 0) |
| [Axis](/docs/nl-nl/reference/engine/classes/DragDetector#Axis) | | De primaire as van beweging, uitgedrukt ten opzichte van het referentiekader. Het wijzigen van deze waarde werkt automatisch [Orientation](/docs/nl-nl/reference/engine/classes/DragDetector#Orientation)  bij en vice versa. | | (0, 1, 0) |

### [Reactie op beweging](#reactie-op-beweging)[](#reactie-op-beweging)

De [ResponseStyle](/docs/nl-nl/reference/engine/classes/DragDetector#ResponseStyle)  eigenschap specificeert hoe een object reageert op de voorgestelde beweging, afhankelijk van of het object [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  is of niet.

| Instelling | | Verankerd gedrag | | Onverankerd gedrag |
| [Geometric](/docs/nl-nl/reference/engine/enums/DragDetectorResponseStyle#Geometric) | | Zowel binnen het draaiende spel als in de Studio bewerkingsmodus, zal de positie/oriëntatie van een verankerd object worden bijgewerkt om exact de voorgestelde beweging weer te geven. | | Voor een onverankerd object is het gedrag hetzelfde als voor een verankerd object. Echter, in een draaiend spel zal het object aan het begin van de sleep worden verankerd en weer onverankerd worden bij het loslaten van de sleep. |
| [Physical](/docs/nl-nl/reference/engine/enums/DragDetectorResponseStyle#Physical) | | Een verankerd object zal standaard Geometric  gedrag hebben, omdat het niet door krachten wordt beïnvloed. | | Een onverankerd object zal worden verplaatst door [constraint forces](#fysieke-reactie)  die proberen het naar de gewenste positie en/of oriëntatie te brengen zoals gegeven door de voorgestelde beweging. |
| [Custom](/docs/nl-nl/reference/engine/enums/DragDetectorResponseStyle#Custom) | | Het object zal helemaal niet bewegen, maar [DragFrame](/docs/nl-nl/reference/engine/classes/DragDetector#DragFrame)  zal nog steeds worden bijgewerkt en je kunt [reageren op sleepmanipulatie](#scriptreacties-op-klikken-en-slepen)  zoals je wilt. | | (zelfde als verankerd) |

Vergeet niet dat [DragDetectors](/docs/nl-nl/reference/engine/classes/DragDetector)  alleen in Studio werken als je niet  de Selecteer , Verplaats , Schaal , of Draai  tools gebruikt.

### [As- en bewegingslimieten](#as--en-bewegingslimieten)[](#as--en-bewegingslimieten)

Standaard zijn er geen limieten aan 3D-beweging behalve de inherente beperkingen van de [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle) . Indien nodig kun je minimum- en maximumlimieten toepassen op zowel vertaling als rotatie. Let echter op dat dit geen  beperkingen zijn; ze belemmeren slechts de pogingen van de sleepdetectie om beweging te genereren om binnen de limieten te blijven.

| Eigenschappen | | Beschrijving | | Standaard |
| [MinDragTranslation](/docs/nl-nl/reference/engine/classes/DragDetector#MinDragTranslation)
 [MaxDragTranslation](/docs/nl-nl/reference/engine/classes/DragDetector#MaxDragTranslation) | | Beperkingen voor sleepvertaling in elke dimensie. Als MaxDragTranslation groter is dan MinDragTranslation, zal de vertaling binnen dat bereik worden geklemd. | | (0, 0, 0) |
| [MinDragAngle](/docs/nl-nl/reference/engine/classes/DragDetector#MinDragAngle)
 [MaxDragAngle](/docs/nl-nl/reference/engine/classes/DragDetector#MaxDragAngle) | | Alleen relevant als [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  is ingesteld op RotateAxis . Als [MaxDragAngle](/docs/nl-nl/reference/engine/classes/DragDetector#MaxDragAngle)  groter is dan [MinDragAngle](/docs/nl-nl/reference/engine/classes/DragDetector#MinDragAngle) , zal de rotatie binnen dat bereik worden geklemd. | | 0 |

Bij het gebruik van as-/bewegingslimieten, moet je altijd de [ReferenceInstance](/docs/nl-nl/reference/engine/classes/DragDetector#ReferenceInstance)  van de detector instellen zodat de limieten relatief zijn aan een specifiek referentiekader. Als je er niet in slaagt het referentiekader vast te stellen, zal elke sleep van het object zijn limieten resetten naar zijn huidige wereldruimte positie/oriëntatie.

### [Sleeprechten](#sleeprechten)[](#sleeprechten)

De toestemming van spelers om met een gegeven sleepdetectie-instantie te interageren kan worden gespecificeerd door de [PermissionPolicy](/docs/nl-nl/reference/engine/classes/DragDetector#PermissionPolicy)  eigenschap. Dit is standaard ingesteld op [Enum.DragDetectorPermissionPolicy.Everybody](/docs/nl-nl/reference/engine/enums/DragDetectorPermissionPolicy#Everybody) , en het kan ook worden gewijzigd om gescripte toestemmingscontroles te ondersteunen zoals weergegeven in het codevoorbeeld.

| Instelling | | Beschrijving |
| [Nobody](/docs/nl-nl/reference/engine/enums/DragDetectorPermissionPolicy#Nobody) | | Geen spelers kunnen interageren met de [DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector) . |
| [Everybody](/docs/nl-nl/reference/engine/enums/DragDetectorPermissionPolicy#Everybody) | | Alle spelers kunnen interageren met de [DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector) . |
| [Scriptable](/docs/nl-nl/reference/engine/enums/DragDetectorPermissionPolicy#Scriptable) | | De sleeprechten van spelers worden bepaald door een functie die is geregistreerd via [SetPermissionPolicyFunction()](/docs/nl-nl/reference/engine/classes/DragDetector#SetPermissionPolicyFunction) . Onder deze instelling zal het niet registreren van een functie of het retourneren van een ongeldig resultaat voorkomen dat alle spelers kunnen slepen. |

DragDetector - Gescripte Sleeprechten

```

local dragDetector = script.Parent.DragDetector

dragDetector.PermissionPolicy = Enum.DragDetectorPermissionPolicy.Scriptable

dragDetector:SetPermissionPolicyFunction(function(player, part)

	if player and player:GetAttribute("IsInTurn") then

		return true

	elseif part and not part:GetAttribute("IsDraggable") then

		return false

	else

		return true

	end

end)

```

### [Fysieke reactie](#fysieke-reactie)[](#fysieke-reactie)

Als de [reactiestijl](#reactie-op-beweging)  van een sleepdetectie is ingesteld op Physical  en deze wordt toegepast op een onverankerd object, zal dat object worden verplaatst door constraint forces die proberen het naar de positie/oriëntatie te brengen die gegeven is door de voorgestelde beweging. Je kunt de fysieke reactie verder aanpassen via de volgende eigenschappen:

| Eigenschap | | Beschrijving | | Standaard |
| [ApplyAtCenterOfMass](/docs/nl-nl/reference/engine/classes/DragDetector#ApplyAtCenterOfMass) | | Wanneer false, wordt de sleepkracht toegepast op het punt waar de gebruiker klikt. Wanneer true, wordt de kracht toegepast op het zwaartepunt van het object. | | false |
| [MaxForce](/docs/nl-nl/reference/engine/classes/DragDetector#MaxForce) | | Maximale kracht die wordt toegepast om het object zijn doel te laten bereiken. | | 10000000 |
| [MaxTorque](/docs/nl-nl/reference/engine/classes/DragDetector#MaxTorque) | | Maximale koppel dat wordt toegepast om het object zijn doel te laten bereiken. | | 10000 |
| [Responsiveness](/docs/nl-nl/reference/engine/classes/DragDetector#Responsiveness) | | Hogere waarden zorgen ervoor dat het object zijn doel sneller bereikt. | | 10 |

### [Modifier invoer](#modifier-invoer)[](#modifier-invoer)

Sommige [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  modi staan gebruikers toe om een modifier  toets/knop ingedrukt te houden om het gesleepte object op verschillende manieren te manipuleren. Standaard is de modifier [LeftControl](/docs/nl-nl/reference/engine/enums/KeyCode)  op PC, [ButtonR1](/docs/nl-nl/reference/engine/enums/KeyCode)  op gamepad, of [ButtonL2](/docs/nl-nl/reference/engine/enums/KeyCode)  op VR. Je kunt deze modifiers aanpassen via de [KeyboardModeSwitchKeyCode](/docs/nl-nl/reference/engine/classes/DragDetector#KeyboardModeSwitchKeyCode) , [GamepadModeSwitchKeyCode](/docs/nl-nl/reference/engine/classes/DragDetector#GamepadModeSwitchKeyCode) , of [VRSwitchKeyCode](/docs/nl-nl/reference/engine/classes/DragDetector#VRSwitchKeyCode)  eigenschappen van de sleepdetectie-instantie.

### [Replicatie](#replicatie)[](#replicatie)

Wanneer de [RunLocally](/docs/nl-nl/reference/engine/classes/DragDetector#RunLocally)  eigenschap false is (standaard), interpreteert de client alle invoer om gegevens te produceren die naar de server worden verzonden om de sleep uit te voeren. In deze modus moeten alle aangepaste gebeurtenissignalen en geregistreerde functies zich in server [Scripts](/docs/nl-nl/reference/engine/classes/Script)  bevinden.

Wanneer de [RunLocally](/docs/nl-nl/reference/engine/classes/DragDetector#RunLocally)  eigenschap true is, worden er geen gebeurtenissen naar de server gerepliceerd. Alle aangepaste gebeurtenissignalen en geregistreerde functies moeten zich in client scripts bevinden, en je moet [remote events](/docs/nl-nl/scripting/events/remote)  gebruiken om noodzakelijke wijzigingen naar de server te propagateren.

## [Scriptreacties op klikken en slepen](#scriptreacties-op-klikken-en-slepen)[](#scriptreacties-op-klikken-en-slepen)

Via [gebeurtenissignalen](#gebeurtenissignalen) , eigenschapswijzigingen, [Scriptable](/docs/nl-nl/reference/engine/enums/DragDetectorDragStyle#Scriptable)  sleepstijl, en aangepaste functies kunnen scripts reageren op de manipulatie van gesleepte objecten om UI aan te sturen of logische beslissingen te nemen, zoals het aanpassen van het lichtniveau in een kamer op basis van een schuifwandschakelaar dimmer.

### [Gebeurtenissignalen](#gebeurtenissignalen)[](#gebeurtenissignalen)

Via de volgende gebeurtenissignalen kun je detecteren wanneer een gebruiker begint, doorgaat en stopt met het slepen van een object.

| Evenement | | Beschrijving |
| [DragStart](/docs/nl-nl/reference/engine/classes/DragDetector#DragStart) | | Wordt geactiveerd wanneer een gebruiker begint met het slepen van het object. |
| [DragContinue](/docs/nl-nl/reference/engine/classes/DragDetector#DragContinue) | | Wordt geactiveerd wanneer een gebruiker doorgaat met het slepen van het object nadat [DragStart](/docs/nl-nl/reference/engine/classes/DragDetector#DragStart)  is gestart. |
| [DragEnd](/docs/nl-nl/reference/engine/classes/DragDetector#DragEnd) | | Wordt geactiveerd wanneer een gebruiker stopt met het slepen van het object. |

DragDetector - Gebeurtenissignalen

```

local dragDetector = script.Parent.DragDetector

local highlight = Instance.new("Highlight")

highlight.Enabled = false

highlight.Parent = script.Parent

dragDetector.DragStart:Connect(function()

	highlight.Enabled = true

end)

dragDetector.DragContinue:Connect(function()

end)

dragDetector.DragEnd:Connect(function()

	highlight.Enabled = false

end)

```

### [Wijzigingen in het sleepframe](#wijzigingen-in-het-sleepframe)[](#wijzigingen-in-het-sleepframe)

Naast [gebeurtenissignalen](#gebeurtenissignalen)  kun je wijzigingen in het [DragFrame](/docs/nl-nl/reference/engine/classes/DragDetector#DragFrame)  van de detector direct volgen.

DragDetector - Wijzigingen in DragFrame

```

local dragDetector = script.Parent.DragDetector

dragDetector:GetPropertyChangedSignal("DragFrame"):Connect(function()

	local currentDragTranslation = dragDetector.DragFrame.Position

	print(currentDragTranslation)

end)

```

### [Gescripte sleepstijl](#gescripte-sleepstijl)[](#gescripte-sleepstijl)

Als je de [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  van een detector instelt op Scriptable , kun je je eigen functie bieden die een [Ray](/docs/nl-nl/reference/engine/datatypes/Ray)  accepteert en een wereldruimte [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  retourneert. De detector zal de beweging verplaatsen zodat het gesleepte object naar die aangepaste locatie/oriëntatie gaat.

DragDetector - Gescripte DragStyle

```

local Workspace = game:GetService("Workspace")

local dragDetector = script.Parent.DragDetector

dragDetector.DragStyle = Enum.DragDetectorDragStyle.Scriptable

local cachedHitPoint = Vector3.zero

local cachedHitNormal = Vector3.yAxis

local function followTheCursor(cursorRay)

	-- Exclude dragged object from raycast detection

	local raycastParams = RaycastParams.new()

	raycastParams.FilterDescendantsInstances = {dragDetector.Parent}

	raycastParams.FilterType = Enum.RaycastFilterType.Exclude

	local hitPoint = Vector3.zero

	local hitNormal = Vector3.yAxis

	local raycastResult = Workspace:Raycast(cursorRay.Origin, cursorRay.Direction, raycastParams)

	if raycastResult then

		hitPoint = raycastResult.Position

		hitNormal = raycastResult.Normal.Unit

	else

		hitPoint = cachedHitPoint

		hitNormal = cachedHitNormal

	end

	cachedHitPoint = hitPoint

	cachedHitNormal = hitNormal

	local lookDir1 = hitNormal:Cross(Vector3.xAxis)

	local lookDir2 = hitNormal:Cross(Vector3.yAxis)

	local lookDir = if lookDir1.Magnitude > lookDir2.Magnitude then lookDir1.Unit else lookDir2.Unit

	return CFrame.lookAt(hitPoint, hitPoint + lookDir, hitNormal)

end

dragDetector:SetDragStyleFunction(followTheCursor)

```

### [Aangepaste constraint functie](#aangepaste-constraint-functie)[](#aangepaste-constraint-functie)

Sleepdetectie heeft geen ingebouwde bewegingsregels over grids en vastklikken, maar je kunt aangepaste constraint functies registreren om het [DragFrame](/docs/nl-nl/reference/engine/classes/DragDetector#DragFrame)  van de detector te bewerken voordat het wordt toegepast. Bijvoorbeeld, je kunt de beweging op een grid houden door posities af te ronden op veelvouden van de gridverhoging, of een schaakspel simuleren met bewegingsregels die legaal zijn voor elk stuk.

DragDetector - Aangepaste Constraint Functie

```

local dragDetector = script.Parent.DragDetector

local startPartPosition = nil

local SNAP_INCREMENT = 4

dragDetector.DragStart:Connect(function()

	startPartPosition = script.Parent.Position

end)

dragDetector.DragEnd:Connect(function()

	startPartPosition = nil

end)

local function snapToWorldGrid(proposedMotion)

	if startPartPosition == nil then

		return proposedMotion

	end

	local snapIncrement = SNAP_INCREMENT // 1

	if snapIncrement < 1 then

		return proposedMotion

	end

	local newWorldPosition = startPartPosition + proposedMotion.Position

	local roundedX = ((newWorldPosition.X / snapIncrement + 0.5) // 1) * snapIncrement

	local roundedY = ((newWorldPosition.Y / snapIncrement + 0.5) // 1) * snapIncrement

	local roundedZ = ((newWorldPosition.Z / snapIncrement + 0.5) // 1) * snapIncrement

	local newRoundedWorldPosition = Vector3.new(roundedX, roundedY, roundedZ)

	return proposedMotion.Rotation + (newRoundedWorldPosition - startPartPosition)

end

local connection = dragDetector:AddConstraintFunction(2, snapToWorldGrid)

-- Wanneer van toepassing, verwijder de constraint functie door connection:Disconnect() aan te roepen

```

## [Voorbeeldgebruik](#voorbeeldgebruik)[](#voorbeeldgebruik)

### [Onverankerde fysieke objecten](#onverankerde-fysieke-objecten)[](#onverankerde-fysieke-objecten)

Een basisimplementatie van sleepdetectie is een torenbalansspel waarbij spelers voorzichtig stukken moeten verwijderen en proberen de toren rechtop te houden. In de volgende torenstructuur heeft elk stuk een kind [DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector)  met een standaard [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  van TranslatePlane  zodat spelers de stukken naar buiten kunnen trekken maar niet omhoog of omlaag.

### [Verankerde modellen met verstelbare onderdelen](#verankerde-modellen-met-verstelbare-onderdelen)[](#verankerde-modellen-met-verstelbare-onderdelen)

Je kunt eenvoudig modellen maken en delen die voornamelijk verankerd zijn, maar die een of meer kindonderdelen/modellen hebben die spelers kunnen slepen. Bijvoorbeeld, het volgende bureau heeft twee lades die spelers kunnen openen om te inspecteren wat erin zit.

Bij het maken van kinderen van modellen die sleepbaar zijn, moet je de [ReferenceInstance](/docs/nl-nl/reference/engine/classes/DragDetector#ReferenceInstance)  van de sleepdetectie instellen op een object binnen het model dat kan dienen als een specifiek referentiekader, bijvoorbeeld het bovenste oppervlak van het bureau. Dit stelt een consistent referentiekader [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  in voor de stijl/richting van het slepen, zelfs als het model is gedraaid.

### [Sleepdetectie en beperkingen](#sleepdetectie-en-beperkingen)[](#sleepdetectie-en-beperkingen)

Je kunt sleepdetectie combineren met [Constraints](/docs/nl-nl/reference/engine/classes/Constraint) , bijvoorbeeld een marionettepop. In de volgende opstelling zijn de controlehandvatten verankerd, zijn de lichaamsdelen onverankerd, en houden beperkingen de marionette bij elkaar. Het verplaatsen van de handvatten met de TranslateViewPlane  [DragStyle](/docs/nl-nl/reference/engine/classes/DragDetector#DragStyle)  laat de marionette dansen, en de individuele lichaamsdelen kunnen ook worden verplaatst met sleepdetectie, terwijl het model zijn integriteit behoudt.

### [3D gebruikersinterfaces](#3d-gebruikersinterfaces)[](#3d-gebruikersinterfaces)

3D gebruikersinterfaces zijn gemakkelijk te bereiken via sleepdetectie, zoals het aanpassen van de helderheid van een [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight)  op basis van een schuifschakelaar dimmer. Je kunt ook de X  en Z  assen afzonderlijk detecteren om twee verschillende aspecten van een 3D gebruikersinterface te controleren, zoals de [Size](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Size) , [Speed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Speed) , en [Color](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Color)  van een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter) .

DragDetector - 3D Gebruikersinterface

```

local model = script.Parent

local slider = model.SliderPart

local originPart = model.OriginPart

local emitter = script.Parent.EmitterPart.ParticleEmitter

local dragDetector = slider.DragDetector

dragDetector.ReferenceInstance = originPart

dragDetector.MinDragTranslation = Vector3.zero

dragDetector.MaxDragTranslation = Vector3.new(10, 0, 10)

local dragRangeX = dragDetector.MaxDragTranslation.X - dragDetector.MinDragTranslation.X

local dragRangeZ = dragDetector.MaxDragTranslation.Z - dragDetector.MinDragTranslation.Z

local MIN_PARTICLE_SIZE = 1

local MAX_PARTICLE_SIZE = 1.5

local MIN_PARTICLE_SPEED = 2.5

local MAX_PARTICLE_SPEED = 5

local COLOR1 = Color3.fromRGB(255, 150, 0)

local COLOR2 = Color3.fromRGB(255, 0, 50)

local function updateParticles(emitter)

	local dragFactorX = (dragDetector.DragFrame.Position.X - dragDetector.MinDragTranslation.X) / dragRangeX

	local dragFactorZ = (dragDetector.DragFrame.Position.Z - dragDetector.MinDragTranslation.Z) / dragRangeZ

	-- Pas de deeltjesgrootte en snelheid aan op basis van de sleepdetectie X-factor

	emitter.Size = NumberSequence.new{

		NumberSequenceKeypoint.new(0, 0),

		NumberSequenceKeypoint.new(0.1, MIN_PARTICLE_SIZE + ((MAX_PARTICLE_SIZE - MIN_PARTICLE_SIZE) * dragFactorX)),

		NumberSequenceKeypoint.new(1, 0)

	}

	local speed = MIN_PARTICLE_SPEED + ((MAX_PARTICLE_SPEED - MIN_PARTICLE_SPEED) * dragFactorX)

	emitter.Speed = NumberRange.new(speed, speed * 1.2)

	-- Pas de deeltjeskleur aan op basis van de sleepdetectie Z-factor

	local color = COLOR2:Lerp(COLOR1, dragFactorZ)

	emitter.Color = ColorSequence.new{

		ColorSequenceKeypoint.new(0, color),

		ColorSequenceKeypoint.new(1, color)

	}

end

dragDetector:GetPropertyChangedSignal("DragFrame"):Connect(function()

	updateParticles(emitter)

end)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
