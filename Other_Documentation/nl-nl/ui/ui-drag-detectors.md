<!-- Source: https://create.roblox.com/docs/nl-nl/ui/ui-drag-detectors -->

UI-sleepdetectie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# UI-sleepdetectie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  instantie vergemakkelijkt en moedigt interactie aan met 2D-gebruikersinterface-elementen in een spel, zoals schuifregelaars, draaiwielen en meer. Belangrijke kenmerken zijn:

-

Plaats een [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  onder elke [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  instantie om deze versleepbaar te maken via alle gebruikersinvoeren zonder een enkele regel code.

-

Kies uit verschillende [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  opties, definieer hoe het object reageert op beweging via [ResponseStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#ResponseStyle) , en pas optioneel assen, bewegingslimieten of sleepgrenzen toe.

-

Scripts kunnen reageren op manipulatie van versleepbare objecten om logische reacties aan te sturen, zoals het aanpassen van instellingen.

-

[UIDragDetectors](/docs/nl-nl/reference/engine/classes/UIDragDetector)  werken in de bewerkings- en speelmodus van Studio zolang je niet  de Selecteer , Verplaats , Schaal , of Draai  tools gebruikt, noch bepaalde plugins of de UI  editor tools van Studio.

Voor sleepdetectie die 3D-objecten in een spel manipuleert, zoals het openen van deuren en lades of het verslepen van een onderdeel, zie [3D Sleepdetectie](/docs/nl-nl/ui/3D-drag-detectors) .

## [Maak UI-elementen versleepbaar](#maak-ui-elementen-versleepbaar)[](#maak-ui-elementen-versleepbaar)

Om elke [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  instantie versleepbaar te maken, voeg je eenvoudig een [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  toe als directe afstammeling.

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, beweeg de muis over de [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  instantie en klik op de ⊕ knop. Een contextmenu wordt weergegeven.

2.

Kies in het menu voor UIDragDetector .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-UIDragDetector.png)

3.

Standaard zal het object nu versleepbaar zijn in de [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector)  interface.

Vergeet niet dat [UIDragDetectors](/docs/nl-nl/reference/engine/classes/UIDragDetector)  alleen in Studio werken als je niet  de Selecteer , Verplaats , Schaal , of Draai  tools gebruikt, noch bepaalde plugins of de UI  editor tools van Studio.

## [Pas UI-sleepdetectie aan](#pas-ui-sleepdetectie-aan)[](#pas-ui-sleepdetectie-aan)

### [Sleepstijl](#sleepstijl)[](#sleepstijl)

[UIDragDetectors](/docs/nl-nl/reference/engine/classes/UIDragDetector)  koppelen cursorbeweging aan om voorgestelde 2D-beweging en/of rotatie te berekenen. Via de [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  eigenschap kun je kiezen uit verschillende koppelingen die aan jouw behoeften voldoen. Bijvoorbeeld, [Enum.UIDragDetectorDragStyle.TranslatePlane](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#TranslatePlane)  produceert vertaling in het 2D-vlak van de [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector) , terwijl [Enum.UIDragDetectorDragStyle.Rotate](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#Rotate)  normaal gesproken een rotatie produceert in plaats van vertaling.

| Instelling | | Beschrijving |
| --- | --- |
| [TranslateLine](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#TranslateLine) | | 1D-beweging langs de [DragAxis](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragAxis)  van de detector. |
| [TranslatePlane](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#TranslatePlane) | | 2D-beweging in het vlak van de [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector) . |
| [Rotate](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#Rotate) | | Standaard, rotatie rond de absolute middelpuntpositie van de ouder [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  van de detector. Als [ReferenceUIInstance](/docs/nl-nl/reference/engine/classes/UIDragDetector#ReferenceUIInstance)  is ingesteld, vindt de rotatie plaats rond de absolute middelpuntpositie van die instantie. |
| [Scriptable](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#Scriptable) | | Berekeningen van de gewenste beweging via een aangepaste functie die wordt geleverd via [SetDragStyleFunction()](/docs/nl-nl/reference/engine/classes/UIDragDetector#SetDragStyleFunction) . |

### [Sleeprichting](#sleeprichting)[](#sleeprichting)

Standaard zijn 2D-beweging en de bijbehorende [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  gekoppeld aan de ruimte van de voorouder [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector) . Je wilt misschien de [ReferenceUIInstance](/docs/nl-nl/reference/engine/classes/UIDragDetector#ReferenceUIInstance)  of de [DragAxis](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragAxis)  wijzigen bij het bouwen van verschillende UI-componenten.

| Instelling | | Beschrijving | | Standaard |
| [ReferenceUIInstance](/docs/nl-nl/reference/engine/classes/UIDragDetector#ReferenceUIInstance) | | Een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  instantie wiens lokale ruimte en absolute middelpuntpositie de referentieruimte en oorsprong voor de detector is. Het instellen van deze referentie beïnvloedt eigenschappen zoals [DragUDim2](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragUDim2) , [DragRotation](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragRotation) , en het gedrag van [DragAxis](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragAxis) . | | nil |
| [DragAxis](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragAxis) | | [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  waarde die de as van beweging voor het versleepbare object definieert wanneer [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  is ingesteld op [Enum.UIDragDetectorDragStyle.TranslateLine](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#TranslateLine) . De as is gedefinieerd in de lokale ruimte van de [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  tenzij [ReferenceUIInstance](/docs/nl-nl/reference/engine/classes/UIDragDetector#ReferenceUIInstance)  is gedefinieerd, in welk geval de as is gedefinieerd in de lokale ruimte van die instantie. | | (1, 0) |

### [Reactie op beweging](#reactie-op-beweging)[](#reactie-op-beweging)

De [UIDragDetector.ResponseStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#ResponseStyle)  eigenschap specificeert hoe de positiewaarde van een object wordt gewijzigd door de voorgestelde beweging. De aangepaste responsstijlen laten je de resulterende [UIDragDetector.DragUDim2](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragUDim2)  en [UIDragDetector.DragRotation](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragRotation)  waarden gebruiken zoals gewenst, zonder dat de ouder van de detector de voorgestelde beweging uitvoert.

| Instelling | | Beschrijving |
| [Offset](/docs/nl-nl/reference/engine/enums/UIDragDetectorResponseStyle#Offset) | | Verplaats met de [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden van de positie van de ouder [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  van de detector. Dit is de standaardinstelling. |
| [Scale](/docs/nl-nl/reference/engine/enums/UIDragDetectorResponseStyle#Scale) | | Verplaats met de [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  waarden van de positie van de ouder [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  van de detector. |
| [CustomOffset](/docs/nl-nl/reference/engine/enums/UIDragDetectorResponseStyle#CustomOffset) | | Het UI-element zal helemaal niet bewegen, maar de [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden van de [DragUDim2](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragUDim2)  van de detector zullen nog steeds worden bijgewerkt en de evenementen van de detector zullen nog steeds worden geactiveerd, zodat je kunt reageren op sleepmanipulatie zoals je wilt. |
| [CustomScale](/docs/nl-nl/reference/engine/enums/UIDragDetectorResponseStyle#CustomScale) | | Het UI-element zal helemaal niet bewegen, maar de [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  waarden van de [DragUDim2](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragUDim2)  van de detector zullen nog steeds worden bijgewerkt en de evenementen van de detector zullen nog steeds worden geactiveerd, zodat je kunt reageren op sleepmanipulatie zoals je wilt. |

### [Vertalings- en rotatielimieten](#vertalings--en-rotatielimieten)[](#vertalings--en-rotatielimieten)

Standaard zijn er geen limieten voor 2D-beweging achter de inherente beperkingen van de [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle) . Limieten voor zowel minimale als maximale vertalingen en rotaties kunnen worden verklaard met de volgende eigenschappen indien gewenst. Bovendien kun je definiëren hoe het versleepbare object wordt beperkt binnen de grenzen van een opgegeven [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) , zoals een [Frame](/docs/nl-nl/reference/engine/classes/Frame) .

| Eigenschappen | | Beschrijving | | Standaard |
| [MinDragTranslation](/docs/nl-nl/reference/engine/classes/UIDragDetector#MinDragTranslation)
 [MaxDragTranslation](/docs/nl-nl/reference/engine/classes/UIDragDetector#MaxDragTranslation) | | Limieten voor sleepvertaling in elke dimensie, gedefinieerd door een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  waarde. Als [MaxDragTranslation](/docs/nl-nl/reference/engine/classes/UIDragDetector#MaxDragTranslation)  groter is dan [MinDragTranslation](/docs/nl-nl/reference/engine/classes/UIDragDetector#MinDragTranslation) , zal de vertaling binnen dat bereik worden beperkt. | | {0, 0}, {0, 0} |
| [MinDragAngle](/docs/nl-nl/reference/engine/classes/UIDragDetector#MinDragAngle)
 [MaxDragAngle](/docs/nl-nl/reference/engine/classes/UIDragDetector#MaxDragAngle) | | Alleen relevant als [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  is ingesteld op [Enum.UIDragDetectorDragStyle.Rotate](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#Rotate) , of als de functies die zijn ingesteld via [SetDragStyleFunction()](/docs/nl-nl/reference/engine/classes/UIDragDetector#SetDragStyleFunction)  of [AddConstraintFunction()](/docs/nl-nl/reference/engine/classes/UIDragDetector#AddConstraintFunction)  een rotatiewaarde definiëren. Als [MaxDragAngle](/docs/nl-nl/reference/engine/classes/UIDragDetector#MaxDragAngle)  groter is dan [MinDragAngle](/docs/nl-nl/reference/engine/classes/UIDragDetector#MinDragAngle) , zal de rotatie binnen dat bereik worden beperkt. | | 0 |
| [BoundingBehavior](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingBehavior) | | Bepaalt het begrenzingsgedrag van de [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  instantie wanneer de [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  is ingesteld. Dit instellen op [EntireObject](/docs/nl-nl/reference/engine/enums/UIDragDetectorBoundingBehavior#EntireObject)  beperkt de gehele versleepbare UI binnen de [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI) , terwijl het instellen op [HitPoint](/docs/nl-nl/reference/engine/enums/UIDragDetectorBoundingBehavior#HitPoint)  de versleepbare UI alleen beperkt door het exacte hit/grab punt en de respectieve positie na vertaling/rotatie. Als gemak is de standaardinstelling van [Automatic](/docs/nl-nl/reference/engine/enums/UIDragDetectorBoundingBehavior#Automatic)  gelijk aan het gedrag van [EntireObject](/docs/nl-nl/reference/engine/enums/UIDragDetectorBoundingBehavior#EntireObject)  voor een UI-object dat volledig is opgenomen door de [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI) , of anders [HitPoint](/docs/nl-nl/reference/engine/enums/UIDragDetectorBoundingBehavior#HitPoint)  voor een UI-object dat gedeeltelijk buiten de [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  ligt. | | [Automatic](/docs/nl-nl/reference/engine/enums/UIDragDetectorBoundingBehavior#Automatic) |

### [Snelheidsaanpassingen](#snelheidsaanpassingen)[](#snelheidsaanpassingen)

Via [SelectionModeDragSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed)  en [SelectionModeRotateSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeRotateSpeed)  kun je de maximale sleep-/rotatiesnelheden voor een detector fijn afstemmen. Bovendien kun je via [UIDragSpeedAxisMapping](/docs/nl-nl/reference/engine/classes/UIDragDetector#UIDragSpeedAxisMapping)  de X / Y  dimensie sleep snelheden fijn afstemmen, op basis van de [SelectionModeDragSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed) .

| Eigenschap | | Beschrijving |
| [SelectionModeDragSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed) | | Definieert de maximale sleep snelheid voor vertaling als een combinatie van [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  en [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  van de eerste voorouder [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  of [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  waartoe de [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  behoort. |
| [SelectionModeRotateSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeRotateSpeed) | | Definieert de maximale hoek per seconde waarmee de [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  kan draaien. |
| [UIDragSpeedAxisMapping](/docs/nl-nl/reference/engine/classes/UIDragDetector#UIDragSpeedAxisMapping) | | Bepaalt de X / Y  dimensie sleep snelheden, op basis van de [SelectionModeDragSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed) . De standaard is [XY](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping#XY) , wat betekent dat de X  en Y  as snelheden zijn gebaseerd op de X  en Y  [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale) /[Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden respectievelijk.
Alternatieven zijn [XX](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping)  en [YY](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping) , wat betekent dat zowel de X  als Y  as snelheden zijn gebaseerd op de X  ([XX](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping) ) of Y  ([YY](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping) ) as voor [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale) , terwijl de [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden nog steeds van toepassing zijn op hun respectieve assen. Bijvoorbeeld, als de eerste voorouder [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  is ingesteld op 800×600 en [SelectionModeDragSpeed](/docs/nl-nl/reference/engine/classes/UIDragDetector#SelectionModeDragSpeed)  is {0.1, 10}, {0.1, 20} , resulteert een instelling van [XX](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping)  in een X / Y  sleep snelheid van 80+10 / 80+20 , terwijl [YY](/docs/nl-nl/reference/engine/enums/UIDragSpeedAxisMapping)  resulteert in 60+10 / 60+20  (let op dat de [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden in beide gevallen hetzelfde blijven). |

## [Scriptreacties op klikken en slepen](#scriptreacties-op-klikken-en-slepen)[](#scriptreacties-op-klikken-en-slepen)

Via [evenement signalen](#evenement-signalen) , eigenschapswijzigingen, [Scriptable](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#Scriptable)  sleepstijl, en aangepaste functies kunnen scripts reageren op de manipulatie van versleepbare UI-elementen om verschillende instellingen aan te sturen of logische beslissingen te nemen, zoals schuifregelaars die het volume van muziek en geluidseffecten afzonderlijk aanpassen.

Voor door de gebruiker geïnitieerde scriptreacties zoals [Evenement Signalen](#evenement-signalen)  en [Scripted Sleepstijl](#aangepaste-sleepstijl) , moet je je scriptcode meestal binnen een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  plaatsen, of een [Script](/docs/nl-nl/reference/engine/classes/Script)  met [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) .

### [Evenement signalen](#evenement-signalen)[](#evenement-signalen)

Via de volgende evenement signalen kun je detecteren wanneer een gebruiker begint, doorgaat en stopt met het slepen van een object.

| Evenement | | Beschrijving |
| [DragStart](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStart) | | Wordt geactiveerd wanneer een gebruiker begint met het slepen van het object. |
| [DragContinue](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragContinue) | | Wordt geactiveerd wanneer een gebruiker doorgaat met het slepen van het object nadat [DragStart](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStart)  is geïnitieerd. |
| [DragEnd](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragEnd) | | Wordt geactiveerd wanneer een gebruiker stopt met het slepen van het object. |

De volgende schuifregelaar wijst zijn container aan als de [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  om zijn beweging binnen het containergebied te beperken, waardoor de schaalgebaseerde [TranslateLine](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle)  sleep wordt beperkt tot de volledige breedte van de container zonder extra scripting.

Om dit voorbeeld te testen, download het [TransparencySlider.rbxm](https://prod.docsiteassets.roblox.com/assets/ui/ui-drag-detectors/TransparencySlider.rbxm)  bestand, klik met de rechtermuisknop op [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  in het [Explorer](/docs/nl-nl/studio/explorer)  venster, selecteer Invoegen  ⟩ Importeer Roblox Model , en kies het gedownloade bestand.

UIDragDetector - Evenement Signaal Transparantie Verandering

```

-- Hiërarchie is SliderContainer ⟩ Handle ⟩ UIDragDetector ⟩ (dit script)

local sliderContainer = script.Parent.Parent.Parent

local handle = sliderContainer:FindFirstChild("Handle")

local uiDragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.ResponseStyle = Enum.UIDragDetectorResponseStyle.Scale  -- Stel slepen in op schaal

uiDragDetector.DragStyle = Enum.UIDragDetectorDragStyle.TranslateLine  -- Beperk slepen tot lijn

uiDragDetector.BoundingUI = sliderContainer

-- Stel aanvankelijk de transparantie van de container in op de X-schaalwaarde van de handgreep

sliderContainer.BackgroundTransparency = 1 - handle.Position.X.Scale

-- Breid de rand van de handgreep uit om het begin van het grijpen aan te geven

uiDragDetector.DragStart:Connect(function(inputPosition)

	handle:FindFirstChildWhichIsA("UIStroke").Thickness = 6

end)

-- Verander de transparantie op basis van hoeveel het in schaal is versleept

uiDragDetector.DragContinue:Connect(function(inputPosition)

	sliderContainer.BackgroundTransparency = 1 - handle.Position.X.Scale

end)

-- Herstel de rand van de handgreep om het einde van het grijpen aan te geven

uiDragDetector.DragEnd:Connect(function(inputPosition)

	handle:FindFirstChildWhichIsA("UIStroke").Thickness = 4

end)

```

### [Positie- en rotatiewijzigingen](#positie--en-rotatiewijzigingen)[](#positie--en-rotatiewijzigingen)

Naast [evenement signalen](#evenement-signalen)  kun je wijzigingen in de [DragUDim2](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragUDim2)  en/of [DragRotation](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragRotation)  eigenschappen van de detector direct volgen.

De volgende detector heeft zijn [DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  ingesteld op [Rotate](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle) , waardoor gebruikers de handgreep rond de kleurrotatorring kunnen slepen, terwijl wijzigingen in de sleeprotatie worden gedetecteerd via [Instance:GetPropertyChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetPropertyChangedSignal) .

Om dit voorbeeld te testen, download het [HueRotator.rbxm](https://prod.docsiteassets.roblox.com/assets/ui/ui-drag-detectors/HueRotator.rbxm)  bestand, klik met de rechtermuisknop op [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  in het [Explorer](/docs/nl-nl/studio/explorer)  venster, selecteer Invoegen  ⟩ Importeer Roblox Model , en kies het gedownloade bestand.

UIDragDetector - DragRotation Verandering

```

local handle = script.Parent.Parent  -- UI-element om te slepen

local uiDragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.DragStyle = Enum.UIDragDetectorDragStyle.Rotate  -- Stel sleepstijl in op draaien

local function changeHue()

	local currAngle = (math.fmod(handle.Rotation, 360)) / 360

	if currAngle < 0 then

		currAngle += 1

	end

	handle.BackgroundColor3 = Color3.fromHSV(currAngle, 1, 1)

end

-- Stel aanvankelijk de kleur in op de rotatie van de handgreep

changeHue()

-- Verbind functie met GetPropertyChangedSignal() van de dragrotatie van de detector

uiDragDetector:GetPropertyChangedSignal("DragRotation"):Connect(changeHue)

```

### [Aangepaste sleepstijl](#aangepaste-sleepstijl)[](#aangepaste-sleepstijl)

Als je de [UIDragDetector.DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  van een detector instelt op [Enum.UIDragDetectorDragStyle.Scriptable](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#Scriptable) , kun je je eigen functie opgeven die een [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  van de invoerpositie accepteert en een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  (positie) en een float (rotatie) retourneert. De detector zal het object bijwerken naar de berekende positie/rotatie op basis van de retourwaarden, de [DragSpace](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragSpace)  eigenschap, en de [DragRelativity](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragRelativity)  eigenschap.

Standaard zullen de geretourneerde [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  en float de eind  gewenste positie/rotatie zijn in de lokale ruimte van de ouder van de detector. Bestaande vertalings-/rotatielimieten blijven van toepassing, evenals grenslimieten opgelegd door een opgegeven [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  instantie.

Het volgende voorbeeld sleept een UI-element dat een sinusgolf volgt, berekend door de verandering in X  coördinaat invoer. Let op dat de [DragRelativity](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragRelativity)  van de detector is ingesteld op [Enum.UIDragDetectorDragRelativity.Relative](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragRelativity#Relative) .

UIDragDetector - Slepen Volgen Sinusgolf

```

local frame = script.Parent  -- UI-element om te slepen

local uiDragDetector = frame:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.DragStyle = Enum.UIDragDetectorDragStyle.Scriptable

uiDragDetector.DragRelativity = Enum.UIDragDetectorDragRelativity.Relative

local initialXValue = 0

local maxHeightChange = 200

local pixelsPerRadian = 75  -- Verlaag deze waarde om de frequentie te verhogen

uiDragDetector.DragStart:Connect(function(inputPosition)

	initialXValue = inputPosition.X

end)

local function computeSinWaveCoordinate(inputPosition)

	local deltaX = inputPosition.X - initialXValue

	-- Negatieve Y delta zodat het "omhoog" op het scherm gaat met positieve Y verandering

	local deltaY = -math.sin(deltaX / pixelsPerRadian) * maxHeightChange

	return UDim2.fromOffset(deltaX, deltaY)

end

uiDragDetector:SetDragStyleFunction(computeSinWaveCoordinate)

```

### [Aangepaste beperkingsfunctie](#aangepaste-beperkingsfunctie)[](#aangepaste-beperkingsfunctie)

[UIDragDetectors](/docs/nl-nl/reference/engine/classes/UIDragDetector)  hebben geen ingebouwde bewegingsregels over grids en vastklikken, maar je kunt aangepaste beperkingsfuncties registreren om de [UIDragDetector.DragUDim2](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragUDim2)  en [UIDragDetector.DragRotation](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragRotation)  van de detector te bewerken voordat ze worden toegepast. Bijvoorbeeld, je kunt de beweging op een grid houden door posities naar specifieke stappen te ronden, of toegestane bewegingsgebieden te definiëren. Let op dat dit voorafgaand aan  bestaande vertalings-/rotatielimieten wordt toegepast.

Meerdere beperkingsfuncties kunnen worden geregistreerd en ze zullen worden aangeroepen in de volgorde van hun prioriteitswaarde die bij registratie is doorgegeven, van laag naar hoog.

Het volgende voorbeeld maakt gebruik van een beperkingsfunctie die de vlakke sleep in een X / Y  grid beperkt op basis van het aantal rijen en kolommen. Let op dat de [ResponseStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#ResponseStyle)  van de detector is ingesteld op [Enum.UIDragDetectorResponseStyle.Scale](/docs/nl-nl/reference/engine/enums/UIDragDetectorResponseStyle#Scale)  en zijn [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  is ingesteld op de gridcontainer.

Om dit voorbeeld te testen, download het [GridDrag.rbxm](https://prod.docsiteassets.roblox.com/assets/ui/ui-drag-detectors/GridDrag.rbxm)  bestand, klik met de rechtermuisknop op [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  in het [Explorer](/docs/nl-nl/studio/explorer)  venster, selecteer Invoegen  ⟩ Importeer Roblox Model , en kies het gedownloade bestand.

UIDragDetector - Slepen in Grid, Vastklikken op Tegels

```

-- Hiërarchie is GridContainer ⟩ Handle ⟩ UIDragDetector ⟩ (dit script)

local gridContainer = script.Parent.Parent.Parent

local handle = gridContainer:FindFirstChild("Handle")  -- UI-element om te slepen

local uiDragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

uiDragDetector.ResponseStyle = Enum.UIDragDetectorResponseStyle.Scale  -- Stel slepen in op schaal

uiDragDetector.DragRelativity = Enum.UIDragDetectorDragRelativity.Relative

uiDragDetector.BoundingUI = gridContainer

local NUM_COLUMNS = 10

local NUM_ROWS = 5

local xScaleIncrement = 1 / NUM_COLUMNS

local yScaleIncrement = 1 / NUM_ROWS

local initialParentPosition = uiDragDetector.Parent.Position

uiDragDetector.DragStart:Connect(function()

	initialParentPosition = uiDragDetector.Parent.Position

end)

local function dragToGridOnly(proposedPosition, proposedRotation)

	local griddedXScale = math.round(proposedPosition.X.Scale / xScaleIncrement) * xScaleIncrement

	local griddedYScale = math.round(proposedPosition.Y.Scale / yScaleIncrement) * yScaleIncrement

	return UDim2.fromScale(griddedXScale, griddedYScale), proposedRotation

end

uiDragDetector:AddConstraintFunction(1, dragToGridOnly)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
